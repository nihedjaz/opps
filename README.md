# opps
@Transactional
public void checkAndAlertForBalanceMismatch(ClientDTO client, LocalDate today) {
    List<SubsidiaryDTO> subsidiaries = subsidiaryService.getSubsidiariesByClientId(client.getId());

    for (SubsidiaryDTO subsidiary : subsidiaries) {
        List<AccountDTO> accounts = accountService.getAccountsBySubsidiaryId(subsidiary.getId());

        for (AccountDTO account : accounts) {
            String accountId = account.getAccountNumber();
            
            // Récupérer la transaction du jour J
            Optional<TransactionInDTO> todayTransactionOpt = getTransactionForDate(accountId, today);
            
            if (todayTransactionOpt.isEmpty()) {
                continue; // Pas de transaction aujourd'hui, on passe au compte suivant
            }

            TransactionInDTO todayTransaction = todayTransactionOpt.get();
            BigDecimal todayOpeningBalance = todayTransaction.getOpeningBalance().getAmount();
            
            // Rechercher la dernière transaction avec une opération en remontant dans le temps
            LocalDate previousDate = today.minusDays(1);
            Optional<TransactionInDTO> lastTransactionOpt = Optional.empty();
            
            while (previousDate.isAfter(today.minusDays(30))) { // On ne remonte pas plus de 30 jours
                lastTransactionOpt = getTransactionForDate(accountId, previousDate);
                
                if (lastTransactionOpt.isPresent()) {
                    break; // On a trouvé une transaction, on s'arrête ici
                }

                previousDate = previousDate.minusDays(1);
            }

            if (lastTransactionOpt.isEmpty()) {
                continue; // Aucune transaction trouvée dans les derniers jours
            }

            TransactionInDTO lastTransaction = lastTransactionOpt.get();
            BigDecimal lastClosingBalance = lastTransaction.getClosingBalance().getAmount();

            // Vérifier si les soldes correspondent
            if (todayOpeningBalance.compareTo(lastClosingBalance) != 0) {
                String alertMessage = String.format(
                    "Mismatch de solde détecté pour le compte %s : " +
                    "Solde de fermeture (%s) du %s ne correspond pas au solde d'ouverture (%s) du %s.",
                    accountId, lastClosingBalance, previousDate, todayOpeningBalance, today
                );

                Alert alert = Alert.builder()
                        .transactionReference(todayTransaction.getTransactionReference())
                        .message(alertMessage)
                        .clientId(client.getId())
                        .build();
                
                alertRepository.save(alert);
                logger.warn(alertMessage);
            }
        }
    }
}






private Optional<TransactionInDTO> getTransactionForDate(String accountId, LocalDate date) {
    List<TransactionInDTO> transactions = transactionInService.getTransactionsByAccountId(accountId);
    
    return transactions.stream()
            .filter(t -> t.getCreatedAt().toLocalDate().equals(date))
            .findFirst();
}

