@Service
public class StatesScheduler {
    @Autowired
    private AttachmentServiceImpl attachmentServiceImpl;
    @Autowired
    private ClientServiceFeign clientServiceFeign;
    @Autowired
    private PPTStateCalculator PPTStateCalculator;
    @Autowired
    private CumulativeLevelingsService cumulativeLevelingsServiceImpl;
    @Autowired
    private AttachmentRepository attachmentRepository;
    @Autowired
    InterestCalculationService interestCalculationServiceImpl;
    @Autowired
    private SubsidiaryServiceFeign subsidiaryServiceFeign;
    @Autowired
    private StateDispatcherServiceImpl stateDispatcherService;
    @Value("${states.output.directory}")
    private String reportDirectory;
    @Value("${seed.pdfFile.fileLocation}")
    public String pathPiecesJointes;
    public UUID generateUniqueUUID() {
        UUID uuid;
        do {
            uuid = UUID.randomUUID();
        } while (attachmentRepository.existsById(uuid));
        return uuid;
    }
    public static LocalDate[] extractDates(String calculationPeriod) {
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        Pattern pattern = Pattern.compile("\\d{2}/\\d{2}/\\d{4}");
        Matcher matcher = pattern.matcher(calculationPeriod);
        LocalDate[] result = new LocalDate[2];
        int index = 0;
        while (matcher.find() && index < 2) {
            String dateStr = matcher.group();
            result[index] = LocalDate.parse(dateStr, formatter);
            index++;
        }
        if (result[0] == null || result[1] == null) {
            throw new IllegalArgumentException("Impossible d'extraire les deux dates du texte fourni.");
        }
        return result;
    }
 @Scheduled(cron = "0 0 23 * * ?")
    public void generateLoanBorrowingReports() {
        try {
            List<ClientDTO> clients = clientServiceFeign.getAllClients();
            LocalDate referenceDate = LocalDate.now();
            for (ClientDTO client : clients) {
                for (SubsidiaryDTO subsidiary : client.getSubsidiaries()) {
                    CompletableFuture<PPTStateCalculator.PositionReport> reportFuture =
                            PPTStateCalculator.calculateLastNWorkingDayPositions(referenceDate, subsidiary, client);
                    PPTStateCalculator.PositionReport report = reportFuture.get();
                    if (report != null) {
                        String subsidiaryName = subsidiary.getName().replaceAll("\\s+", "_");
                        String formattedDate = referenceDate.format(DateTimeFormatter.ofPattern("yyyyMMdd"));
                        String fileName = "pretEmprunt-indiv-report_" + subsidiaryName + "_" + formattedDate + ".pdf";
                        String outputFilePath = reportDirectory + "/" + fileName;
                        JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(Collections.singletonList(report));
                        JRBeanCollectionDataSource subReportDataSource = new JRBeanCollectionDataSource(report.getPositions());
                        Map<String, Object> parameters = new HashMap<>();
                        parameters.put("tableDataSource", subReportDataSource);
                        parameters.put("address", report.getAddress());
                        parameters.put("stateReference", report.getStateReference());
                        parameters.put("clientName", report.getClientName());
                        parameters.put("subsidiaryName", report.getSubsidiaryName());
                        parameters.put("clientAccountNumber", report.getClientAccountNumber());
                        parameters.put("referenceDate", report.getReferenceDate());
                        parameters.put("stateAttach", report.getStateAttach());
                        parameters.put("devise", report.getCurrency());
                        InputStream jasperStream = this.getClass().getResourceAsStream("/LoanBorrowingPosition.jrxml");
                        JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
                        JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);
                        JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
                        ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
                        JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
                        byte[] pdfBytes = pdfOutputStream.toByteArray();
                        Attachment attachment = new Attachment();
                        attachment.setId(UUID.randomUUID());
                        attachment.setDateUpload(new Date());
                        attachment.setTitle("Rapport Prêt Emprunt");
                        attachment.setName(fileName);
                        attachmentRepository.save(attachment);
                        CustomMultipartFile customFile = new CustomMultipartFile(pdfBytes, pathPiecesJointes + "/" + fileName);
                        attachmentServiceImpl.save(customFile, attachment, false);
                        System.out.println("✅ Fichier PDF envoyé et enregistré avec succès !");
                    }
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
            System.err.println("❌ Erreur lors de la génération automatique du rapport PDF !");
        }
    }
    @Scheduled(cron = "0 32 15 * * ?")
    public void generateCumulativeLevelingsGroupReport() {
        try {
            YearMonth reportMonth = YearMonth.now().minusMonths(1);
            List<ClientDTO> clients = clientServiceFeign.getAllClients();
            List<CumulativeLevelingsReport> listReport = new ArrayList<>();
            for (ClientDTO client : clients) {
                for (SubsidiaryDTO subsidiary : client.getSubsidiaries()) {
                    CumulativeLevelingsReport report = cumulativeLevelingsServiceImpl.calculateMonthlyCumulativeLevelingsReport(client.getId(), subsidiary.getId(), reportMonth);
                    if (report != null) {
                        listReport.add(report);
                    }
                }
            }
            final BigDecimal[] lastTotalCumulativeCredit = {BigDecimal.ZERO};
            final BigDecimal[] lastTotalCumulativeDebit = {BigDecimal.ZERO};
            final BigDecimal[] lastTotalCumulativeNet = {BigDecimal.ZERO};
            final BigDecimal[] totalCumulativeDebit = {BigDecimal.ZERO};
            final BigDecimal[] totalCumulativeCredit = {BigDecimal.ZERO};
            final BigDecimal[] totalCumulativeNet = {BigDecimal.ZERO};
            final BigDecimal[] totalGeneral = {BigDecimal.ZERO};
            final String[] currency = {""};
            final String[] reportReference = {""};
            final String[] groupName = {""};
            final String[] companyName = {""};
            final String[] pivotAddress = {""};
            final String[] pivotAccountNumber = {""};
            final LocalDate[] dates = {null, null};
            List<CumulativeLevelingsReport> cumulativeReport = new ArrayList<>();
            List<AccountCumulativeLevelingDetails> cumulatives = new ArrayList<>();
            listReport.forEach(rep -> {
                        currency[0] = rep.getCurrency();
                        reportReference[0] = rep.getReportReference();
                        groupName[0] = rep.getGroupName();
                        companyName[0] = rep.getCompanyName();
                        pivotAddress[0] = rep.getPivotAddress();
                        dates[0] = rep.getFirstDate();
                        dates[1] = rep.getLastDate();
                        pivotAccountNumber[0] = rep.getPivotAccountNumber();
                        rep.getAccountDetails()
                                .forEach((s, accountCumulativeLevelingDetails) -> {
                                    if (accountCumulativeLevelingDetails != null) {
                                        AccountCumulativeLevelingDetails cumulative = new AccountCumulativeLevelingDetails();
                                        cumulative.setCumulativeLevelingDebit(accountCumulativeLevelingDetails.getCumulativeLevelingDebit());
                                        cumulative.setCumulativeLevelingCredit(accountCumulativeLevelingDetails.getCumulativeLevelingCredit());
                                        cumulative.setCumulativeLevelingNet(accountCumulativeLevelingDetails.getCumulativeLevelingNet());
                                        cumulative.setLastCumulativeLevelingCredit(accountCumulativeLevelingDetails.getLastCumulativeLevelingCredit());
                                        cumulative.setLastCumulativeLevelingDebit(accountCumulativeLevelingDetails.getLastCumulativeLevelingDebit());
                                        cumulative.setLastCumulativeLevelingNet(accountCumulativeLevelingDetails.getLastCumulativeLevelingNet());
                                        cumulative.setCompanyName(accountCumulativeLevelingDetails.getCompanyName());
                                        cumulative.setAccountNumber(accountCumulativeLevelingDetails.getAccountNumber());
                                        cumulatives.add(cumulative);
                                        lastTotalCumulativeCredit[0] = lastTotalCumulativeCredit[0].add(accountCumulativeLevelingDetails.getLastCumulativeLevelingDebit());
                                        lastTotalCumulativeDebit[0] = lastTotalCumulativeDebit[0].add(accountCumulativeLevelingDetails.getLastCumulativeLevelingCredit());
                                        lastTotalCumulativeNet[0] = lastTotalCumulativeNet[0].add(accountCumulativeLevelingDetails.getLastCumulativeLevelingNet());
                                        totalCumulativeDebit[0] = totalCumulativeDebit[0].add(accountCumulativeLevelingDetails.getCumulativeLevelingCredit());
                                        totalCumulativeCredit[0] = totalCumulativeCredit[0].add(accountCumulativeLevelingDetails.getCumulativeLevelingDebit());
                                        totalCumulativeNet[0] = totalCumulativeNet[0].add(accountCumulativeLevelingDetails.getCumulativeLevelingNet());
                                        totalGeneral[0] = totalGeneral[0]
                                                .add(accountCumulativeLevelingDetails.getCumulativeLevelingDebit() != null
                                                        ? accountCumulativeLevelingDetails.getCumulativeLevelingDebit()
                                                        : BigDecimal.ZERO)
                                                .add(accountCumulativeLevelingDetails.getCumulativeLevelingCredit() != null
                                                        ? accountCumulativeLevelingDetails.getCumulativeLevelingCredit()
                                                        : BigDecimal.ZERO);
                                    }
                                });
                    }
            );
            Map<String, AccountCumulativeLevelingDetails> cumulativeMap = cumulatives.stream()
                    .collect(Collectors.toMap(
                            AccountCumulativeLevelingDetails::getAccountNumber,
                            account -> account,
                            (existing, replacement) -> existing
                    ));
            cumulativeReport.add(new CumulativeLevelingsReport(currency[0], groupName[0], "02992 - 21807 - 04488 - NCU - RG", "",
                    pivotAddress[0], pivotAccountNumber[0], dates[0], dates[1], companyName[0], lastTotalCumulativeCredit[0], lastTotalCumulativeDebit[0], lastTotalCumulativeNet[0], totalCumulativeDebit[0], totalCumulativeCredit[0], totalCumulativeNet[0], totalGeneral[0], cumulativeMap));
            JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(cumulativeReport);
            JRBeanCollectionDataSource subReportDataSource = new JRBeanCollectionDataSource(cumulatives);
            Map<String, Object> parameters = new HashMap<>();
            parameters.put("tableDataSource", subReportDataSource);
            parameters.put("pivotAddress", cumulativeReport.get(0)
                    .getPivotAddress());
            parameters.put("reportReference", cumulativeReport.get(0)
                    .getReportReference());
            parameters.put("groupName", cumulativeReport.get(0)
                    .getGroupName());
            parameters.put("pivotAccountNumber", cumulativeReport.get(0)
                    .getPivotAccountNumber());
            parameters.put("companyName", cumulativeReport.get(0)
                    .getCompanyName());
            parameters.put("firstDate", cumulativeReport.get(0)
                    .getFirstDate());
            parameters.put("lastDate", cumulativeReport.get(0)
                    .getLastDate());
            parameters.put("devise", cumulativeReport.get(0)
                    .getCurrency());
            InputStream jasperStream = this.getClass().getResourceAsStream("/CumulativeLevelingsGroup.jrxml");
            JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
            JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);
            String fileName = "EtatCumuleGroup_" + cumulativeReport.get(0)
                    .getGroupName() + "_" + reportMonth + ".pdf";
            String outputFilePath = reportDirectory + "/" +fileName;
            JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
            // ✅ Export du PDF en mémoire
            ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
            JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
            byte[] pdfBytes = pdfOutputStream.toByteArray();
            Attachment attachment = new Attachment();
            attachment.setId(UUID.randomUUID());
            attachment.setDateUpload(new Date());
            attachment.setTitle("Rapport Cumulative Levelings Groupe");
            attachment.setName(fileName);
            attachmentRepository.save(attachment);
            CustomMultipartFile customFile = new CustomMultipartFile(pdfBytes, pathPiecesJointes + "/" + fileName);
            attachmentServiceImpl.save(customFile, attachment, false);
            System.out.println("✅ Fichier PDF envoyé et enregistré avec succès !");
        } catch (Exception e) {
            System.err.println("❌ Erreur lors de la génération du fichier PDF : " + e.getMessage());
            e.printStackTrace();
        }
    }
    @Scheduled(cron = "0 0 1 * * ?")
    public void generateCumulativeLevelingsReport() {
        try {
            LocalDate currentDate = LocalDate.now();
            YearMonth reportMonth = YearMonth.now().minusMonths(1);
            System.out.println("📌 Début de la génération du rapport cumulatif pour le mois : " + reportMonth);
            List<ClientDTO> clients = clientServiceFeign.getAllClients();
            for (ClientDTO client : clients) {
                for (SubsidiaryDTO subsidiary : client.getSubsidiaries()) {
                    CumulativeLevelingsReport report = cumulativeLevelingsServiceImpl.calculateMonthlyCumulativeLevelingsReport(client.getId(), subsidiary.getId(), reportMonth);
                    if (report != null && report.getAccountDetails() != null) {
                        List<AccountCumulativeLevelingDetails> cumulatives = new ArrayList<>();
                        for (AccountCumulativeLevelingDetails accountDetails : report.getAccountDetails().values()) {
                            if (accountDetails != null) {
                                AccountCumulativeLevelingDetails cumulative = new AccountCumulativeLevelingDetails();
                                cumulative.setCompanyName(accountDetails.getCompanyName());
                                cumulative.setAccountNumber(accountDetails.getAccountNumber());
                                if (accountDetails.getCumulativeLevelingDebit().add(accountDetails.getCumulativeLevelingCredit()).compareTo(BigDecimal.ZERO) != 0) {
                                    cumulatives.add(cumulative);
                                }
                            }
                        }
                        String fileName = "EtatCumuleIndiv_" + report.getGroupName() + "_" + subsidiary.getName().replaceAll("\\s+", "_") + "_" + reportMonth + ".pdf";
                        String outputFilePath = reportDirectory+"/" + fileName;
                        JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(Collections.singletonList(report));
                        JRBeanCollectionDataSource subReportDataSource = new JRBeanCollectionDataSource(cumulatives);
                        Map<String, Object> parameters = new HashMap<>();
                        parameters.put("tableDataSource", subReportDataSource);
                        parameters.put("pivotAddress", report.getPivotAddress());
                        parameters.put("groupName", report.getGroupName());
                        parameters.put("companyName", report.getCompanyName());
                        InputStream jasperStream = this.getClass().getResourceAsStream("/CumulativeLevelings.jrxml");
                        JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
                        JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);
                        JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
                        System.out.println("✅ Fichier PDF généré avec succès : " + outputFilePath);
                        ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
                        JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
                        byte[] pdfBytes = pdfOutputStream.toByteArray();
                        Attachment attachment = new Attachment();
                        attachment.setId(UUID.randomUUID());
                        attachment.setDateUpload(new Date());
                        attachment.setTitle("Rapport Cumulative Levelings");
                        attachment.setName(fileName);
                        attachmentRepository.save(attachment);
                        CustomMultipartFile customFile = new CustomMultipartFile(pdfBytes, pathPiecesJointes + "/" + fileName);
                        attachmentServiceImpl.save(customFile, attachment, false);
                        System.out.println("✅ Fichier PDF envoyé et enregistré avec succès !");
                    }
                }
            }
        } catch (Exception e) {
            System.err.println("❌ Erreur lors de la génération des fichiers PDF : " + e.getMessage());
            e.printStackTrace();
        }
    }
    @Scheduled(cron = "0 0 1 * * ?")
    public void generateArreteIntraGroupeReport() {
        try {
            System.out.println("📌 Début de la génération du rapport Arrete Intra-Groupe...");
            final BigDecimal[] netInterstDebit = {BigDecimal.ZERO};
            final BigDecimal[] netInterstCredit = {BigDecimal.ZERO};
            List<InterestReport> listReport = new ArrayList<>();
            YearMonth reportMonth = YearMonth.now().minusMonths(1);
            List<ClientDTO> clients = clientServiceFeign.getAllClients();
            for (ClientDTO client : clients) {
                for (SubsidiaryDTO subsidiary : client.getSubsidiaries()) {
                    InterestReport reportx = interestCalculationServiceImpl.calculateMonthlyInterestReport(client.getId(), subsidiary.getId(), reportMonth);
                    if (reportx != null) {
                        listReport.add(reportx);
                    }
                }
            }
            List<InterestReport> intrestReport = new ArrayList<>();
            List<AccountInterestDetails> interests = new ArrayList<>();
            final String[] currency = {""};
            final String[] reportReference = {""};
            final String[] groupName = {""};
            final String[] pivotAddress = {""};
            final String[] pivotAccountNumber = {""};
            final LocalDate[] dates = {null, null};
            listReport.forEach(rep -> {
                currency[0] = rep.getCurrency();
                reportReference[0] = rep.getReportReference();
                groupName[0] = rep.getGroupName();
                pivotAddress[0] = rep.getPivotAddress();
                LocalDate[] extractedDates = extractDates(rep.getCalculationPeriod());
                dates[0] = extractedDates[0];
                dates[1] = extractedDates[1];
                pivotAccountNumber[0] = rep.getPivotAccountNumber();
                rep.getAccountDetails().forEach((s, accountInterestDetails) -> {
                    if (accountInterestDetails != null) {
                        AccountInterestDetails interest = new AccountInterestDetails();
                        interest.setAccountName(accountInterestDetails.getAccountName());
                        interest.setAccountNumber(accountInterestDetails.getAccountNumber());
                        interest.setAmountToBeChargedCredit(accountInterestDetails.getAmountToBeChargedCredit());
                        interest.setAmountToBeChargedDebit(accountInterestDetails.getAmountToBeChargedDebit());
                        interest.setGrossCreditAmount(accountInterestDetails.getGrossCreditAmount());
                        interest.setGrossDebitAmount(accountInterestDetails.getGrossDebitAmount());
                        interest.setRetainedCreditAmount(accountInterestDetails.getRetainedCreditAmount());
                        interest.setRetainedDebitAmount(accountInterestDetails.getRetainedDebitAmount());
                        interest.setWithholdingTax(accountInterestDetails.getWithholdingTax());
                        interests.add(interest);
                        netInterstDebit[0] = netInterstDebit[0].add(accountInterestDetails.getGrossCreditAmount());
                        netInterstCredit[0] = netInterstCredit[0].add(accountInterestDetails.getGrossDebitAmount());
                    }
                });
            });
            Map<String, AccountInterestDetails> interestMap = interests.stream()
                    .collect(Collectors.toMap(AccountInterestDetails::getAccountNumber, account -> account));
            intrestReport.add(new InterestReport(currency[0], "", groupName[0], "03340 - 26449 - 00000 - AIG - RG", "", "",
                    netInterstDebit[0], netInterstCredit[0], pivotAddress[0], pivotAccountNumber[0], dates[0], dates[1], interestMap));
            JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(intrestReport);
            JRBeanCollectionDataSource subReportDataSource = new JRBeanCollectionDataSource(interests);
            Map<String, Object> parameters = new HashMap<>();
            parameters.put("tableDataSource", subReportDataSource);
            parameters.put("pivotAddress", intrestReport.get(0).getPivotAddress());
            parameters.put("reportReference", intrestReport.get(0).getReportReference());
            parameters.put("pivot", intrestReport.get(0).getGroupName());
            parameters.put("pivotAccountNumber", intrestReport.get(0).getPivotAccountNumber());
            parameters.put("firstDate", dates[0]);
            parameters.put("lastDate", dates[1]);
            parameters.put("devise", intrestReport.get(0).getCurrency());
            parameters.put("netInterstDebit", netInterstDebit[0]);
            parameters.put("netInterstCredit", netInterstCredit[0]);
            InputStream jasperStream = this.getClass().getResourceAsStream("/intra-groupOrders.jrxml");
            JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
            JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);
            File outputDir = new File("engine-service/src/main/resources/reports");
            if (!outputDir.exists()) {
                boolean created = outputDir.mkdirs();
                System.out.println("✅ Répertoire créé : " + created);
            }
            String fileName = "EtatArretesIntraGroupe_" + intrestReport.get(0).getGroupName() + "_" + reportMonth + ".pdf";
            String outputFilePath = reportDirectory+"/" + fileName;
            JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
            System.out.println("✅ Fichier PDF généré avec succès : " + outputFilePath);
            ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
            JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
            byte[] pdfBytes = pdfOutputStream.toByteArray();
            Attachment attachment = new Attachment();
            attachment.setId(UUID.randomUUID());
            attachment.setDateUpload(new Date());
            attachment.setTitle("Rapport Arrete Intra-Groupe");
            attachment.setName(fileName);
            attachmentRepository.save(attachment);
            CustomMultipartFile customFile = new CustomMultipartFile(pdfBytes, pathPiecesJointes + "/" + fileName);
            attachmentServiceImpl.save(customFile, attachment, false);
            System.out.println("✅ Fichier PDF envoyé et enregistré avec succès !");
        } catch (Exception e) {
            System.err.println("❌ Erreur lors de la génération du fichier PDF : " + e.getMessage());
            e.printStackTrace();
        }
    }
    @Scheduled(cron = "0 0 1 * * ?")
    public void generateAccountInterestReport() {
        try {
            YearMonth reportMonth = YearMonth.now().minusMonths(1);
            List<ClientDTO> clients = clientServiceFeign.getAllClients();
            for (ClientDTO client : clients) {
                for (SubsidiaryDTO subsidiary : client.getSubsidiaries()) {
                    InterestReport report = interestCalculationServiceImpl.calculateMonthlyInterestReport(client.getId(), subsidiary.getId(), reportMonth);
                    if (report != null && report.getAccountDetails() != null) {
                        List<AccountInterestDetailsState> calculationRows = new ArrayList<>();
                        List<InterestCalculationRowState> interestCalculationRowEtats = new ArrayList<>();
                        final BigDecimal[] taux = {BigDecimal.ZERO};
                        final BigDecimal[] montant_b_d = {BigDecimal.ZERO};
                        final BigDecimal[] montant_b_c = {BigDecimal.ZERO};
                        final BigDecimal[] montant_n_d = {BigDecimal.ZERO};
                        final BigDecimal[] montant_n_c = {BigDecimal.ZERO};
                        final BigDecimal[] mon_rsa_c = {BigDecimal.ZERO};
                        final BigDecimal[] mon_rsa_d = {BigDecimal.ZERO};
                        final BigDecimal[] montant_in_d = {BigDecimal.ZERO};
                        final BigDecimal[] montant_in_c = {BigDecimal.ZERO};
                        final LocalDate[] dates = {null, null};
                        LocalDate[] extractedDates = extractDates(report.getCalculationPeriod());
                        dates[0] = extractedDates[0];
                        dates[1] = extractedDates[1];
                        report.getAccountDetails()
                                .forEach((s, accountInterestDetails) -> {
                                    if (accountInterestDetails != null) {
                                        taux[0] = accountInterestDetails.getWithholdingTax();
                                        montant_b_d[0] = accountInterestDetails.getGrossDebitAmount();
                                        montant_b_c[0] = accountInterestDetails.getGrossCreditAmount();
                                        montant_n_d[0] = accountInterestDetails.getAmountToBeChargedDebit();
                                        montant_n_c[0] = accountInterestDetails.getAmountToBeChargedCredit();
                                        mon_rsa_d[0] = accountInterestDetails.getRetainedDebitAmount();
                                        mon_rsa_c[0] = accountInterestDetails.getRetainedCreditAmount();
                                        montant_in_d[0] = accountInterestDetails.getAmountToBeChargedDebit();
                                        montant_in_c[0] = accountInterestDetails.getAmountToBeChargedCredit();
                                        if (accountInterestDetails.getCalculationRows() != null) {
                                            accountInterestDetails.getCalculationRows()
                                                    .forEach(cal -> {
                                                        if (cal != null) {
                                                            InterestCalculationRowState interestCalculationRowEtat = new InterestCalculationRowState();
                                                            interestCalculationRowEtat.setAncien_solde(accountInterestDetails.getInitialBalance());
                                                            interestCalculationRowEtat.setDate_val(cal.getValueDate());
                                                            interestCalculationRowEtat.setCapitaux(cal.getCapital());
                                                            interestCalculationRowEtat.setSolde(cal.getBalance());
                                                            interestCalculationRowEtat.setJour(cal.getDays());
                                                            interestCalculationRowEtat.setNombres(cal.getNumbers());
                                                            interestCalculationRowEtat.setTaux_debit(cal.getDebitInterest()
                                                                    .compareTo(BigDecimal.ZERO) != 0 ? cal.getDebitRate() : null);
                                                            interestCalculationRowEtat.setTaux_credit(cal.getCreditInterest()
                                                                    .compareTo(BigDecimal.ZERO) != 0 ? cal.getCreditRate() : null);
                                                            interestCalculationRowEtat.setInteret_debit(cal.getDebitInterest()
                                                                    .compareTo(BigDecimal.ZERO) != 0 ? cal.getDebitInterest() : null);
                                                            interestCalculationRowEtat.setInteret_credit(cal.getCreditInterest()
                                                                    .compareTo(BigDecimal.ZERO) != 0 ? cal.getCreditInterest() : null);
                                                            interestCalculationRowEtats.add(interestCalculationRowEtat);
                                                        }
                                                    });
                                        }
                                    }
                                });
                        calculationRows.add(new AccountInterestDetailsState(report.getPivotAddress(), report.getReportReference(), report.getAttachedEntityGroupName(), subsidiary.getName(), report.getGroupName(),
                                dates[0], dates[1], report.getCurrency(), report.getPivotAccountNumber(), report.getGroupName(), taux[0],
                                montant_b_d[0], montant_b_c[0], montant_n_d[0],
                                montant_n_c[0], mon_rsa_c[0], mon_rsa_d[0], montant_in_d[0], montant_in_c[0], interestCalculationRowEtats));
                        JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(calculationRows);
                        JRBeanCollectionDataSource subReportDataSource = new JRBeanCollectionDataSource(interestCalculationRowEtats);
                        Map<String, Object> parameters = new HashMap<>();
                        parameters.put("tableDataSource", subReportDataSource);
                        parameters.put("adr1", calculationRows.get(0)
                                .getAdr1());
                        parameters.put("ref", calculationRows.get(0)
                                .getRef());
                        parameters.put("rattach", calculationRows.get(0)
                                .getRattach());
                        parameters.put("sub_name", calculationRows.get(0)
                                .getSub_name());
                        parameters.put("pivot", calculationRows.get(0)
                                .getPivot());
                        parameters.put("first_date", calculationRows.get(0)
                                .getFirst_date());
                        parameters.put("last_date", calculationRows.get(0)
                                .getLast_date());
                        parameters.put("devise", calculationRows.get(0)
                                .getDevise());
                        report.getAccountDetails()
                                .forEach((s, accountInterestDetails) -> {
                                    if (accountInterestDetails != null) {
                                        parameters.put("taux", accountInterestDetails.getWithholdingTax());
                                        parameters.put("montant_b_d", accountInterestDetails.getGrossDebitAmount());
                                        parameters.put("montant_b_c", accountInterestDetails.getGrossCreditAmount());
                                        parameters.put("montant_n_d", accountInterestDetails.getNetDebitAmount());
                                        parameters.put("montant_n_c", accountInterestDetails.getNetCreditAmount());
                                        parameters.put("mon_rsa_c", accountInterestDetails.getRetainedCreditAmount());
                                        parameters.put("mon_rsa_d", accountInterestDetails.getRetainedDebitAmount());
                                        parameters.put("montant_in_d", accountInterestDetails.getAmountToBeChargedDebit());
                                        parameters.put("montant_in_c", accountInterestDetails.getAmountToBeChargedCredit());
                                    }
                                });
                        parameters.put("taux", calculationRows.get(0)
                                .getTaux());
                        parameters.put("montant_b_d", calculationRows.get(0)
                                .getMontant_b_d());
                        parameters.put("montant_b_c", calculationRows.get(0)
                                .getMontant_b_c());
                        parameters.put("montant_n_d", calculationRows.get(0)
                                .getMontant_n_d());
                        parameters.put("montant_n_c", calculationRows.get(0)
                                .getMontant_n_c());
                        parameters.put("mon_rsa_c", calculationRows.get(0)
                                .getMon_rsa_c());
                        parameters.put("mon_rsa_d", calculationRows.get(0)
                                .getMon_rsa_d());
                        parameters.put("montant_in_d", calculationRows.get(0)
                                .getMontant_in_d());
                        parameters.put("montant_in_c", calculationRows.get(0)
                                .getMontant_in_c());
                        InputStream jasperStream = this.getClass().getResourceAsStream("/IntertsIntraGroupe.jrxml");
                        JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
                        JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);
                        String fileName = String.format("EtatDetaileInteretIG_%s_%s_%s.pdf",
                                report.getGroupName(), subsidiary.getName().replaceAll("\\s+", "_"), reportMonth);
                        String outputFilePath = reportDirectory+"/" + fileName;
                        JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
                        System.out.println("✅ Fichier PDF généré avec succès : " + outputFilePath);
                    ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
                    JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
                    byte[] pdfBytes = pdfOutputStream.toByteArray();
                    Attachment attachment = new Attachment();
                    attachment.setId(UUID.randomUUID());
                    attachment.setDateUpload(new Date());
                    attachment.setTitle("Rapport Arrete Intra-Groupe");
                    attachment.setName(fileName);
                    attachmentRepository.save(attachment);
                    CustomMultipartFile customFile = new CustomMultipartFile(pdfBytes, pathPiecesJointes + "/" + fileName);
                    attachmentServiceImpl.save(customFile, attachment, false);
                    System.out.println("✅ Fichier PDF envoyé et enregistré avec succès !");
                }}
            }
        } catch (Exception e) {
            System.err.println("❌ Erreur lors de la génération des fichiers PDF : " + e.getMessage());
            e.printStackTrace();
        }
    }
}
