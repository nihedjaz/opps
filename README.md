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
            .f





<?xml version="1.0" encoding="UTF-8"?>
<jasperReport xmlns="http://jasperreports.sourceforge.net/jasperreports"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports
        http://jasperreports.sourceforge.net/xsd/jasperreport.xsd"
    name="etat_interets"
    pageWidth="595" pageHeight="842" columnWidth="555" leftMargin="20" rightMargin="20"
    topMargin="20" bottomMargin="20" uuid="12345678-ABCD-1234-ABCD-123456789ABC">

    <!-- Définition des Champs (récupérés depuis la base de données) -->
    <field name="societe" class="java.lang.String"/>
    <field name="montant_brut" class="java.lang.Double"/>
    <field name="taux" class="java.lang.Double"/>
    <field name="retenue" class="java.lang.Double"/>
    <field name="montant_net" class="java.lang.Double"/>

    <!-- Titre du Rapport -->
    <title>
        <band height="80">
            <staticText>
                <reportElement x="0" y="0" width="500" height="30"/>
                <text><![CDATA[SOGECASH INTERNATIONAL POOLING]]></text>
            </staticText>
            <textField>
                <reportElement x="0" y="40" width="300" height="20"/>
                <textFieldExpression><![CDATA[$F{societe}]]></textFieldExpression>
            </textField>
        </band>
    </title>

    <!-- En-têtes des Colonnes -->
    <columnHeader>
        <band height="30">
            <staticText>
                <reportElement x="0" y="0" width="100" height="30" />
                <text><![CDATA[Nom de la Société]]></text>
            </staticText>
            <staticText>
                <reportElement x="120" y="0" width="80" height="30" />
                <text><![CDATA[Montant Brut]]></text>
            </staticText>
            <staticText>
                <reportElement x="220" y="0" width="60" height="30" />
                <text><![CDATA[Taux]]></text>
            </staticText>
            <staticText>
                <reportElement x="300" y="0" width="80" height="30" />
                <text><![CDATA[Retenue]]></text>
            </staticText>
            <staticText>
                <reportElement x="400" y="0" width="100" height="30" />
                <text><![CDATA[Montant Net]]></text>
            </staticText>
        </band>
    </columnHeader>

    <!-- Détails des Données -->
    <detail>
        <band height="20">
            <textField>
                <reportElement x="0" y="0" width="100" height="20"/>
                <textFieldExpression><![CDATA[$F{societe}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="120" y="0" width="80" height="20"/>
                <textFieldExpression><![CDATA[$F{montant_brut}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="220" y="0" width="60" height="20"/>
                <textFieldExpression><![CDATA[$F{taux}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="300" y="0" width="80" height="20"/>
                <textFieldExpression><![CDATA[$F{retenue}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="400" y="0" width="100" height="20"/>
                <textFieldExpression><![CDATA[$F{montant_net}]]></textFieldExpression>
            </textField>
        </band>
    </detail>

    <!-- Pied de Page -->
    <pageFooter>
        <band height="20">
            <staticText>
                <reportElement x="0" y="0" width="555" height="20"/>
                <text><![CDATA[Ce relevé est communiqué à titre indicatif.]]></text>
            </staticText>
        </band>
    </pageFooter>

</jasperReport>

import net.sf.jasperreports.engine.*;
import net.sf.jasperreports.engine.data.JRBeanCollectionDataSource;
import org.springframework.core.io.ClassPathResource;
import org.springframework.stereotype.Service;

import java.io.File;
import java.io.FileOutputStream;
import java.util.*;

@Service
public class JasperReportService {

    public void generateReport() throws Exception {
        // Charger le fichier .jrxml
        File reportFile = new ClassPathResource("etat_interets.jrxml").getFile();
        JasperReport jasperReport = JasperCompileManager.compileReport(reportFile.getAbsolutePath());

        // Création des données dynamiques (SANS dataset)
        List<Map<String, Object>> data = new ArrayList<>();
        
        Map<String, Object> row1 = new HashMap<>();
        row1.put("societe", "EMAPHOS");
        row1.put("montant_brut", 140_968.19);
        row1.put("taux", 10.0);
        row1.put("retenue", 14_089.82);
        row1.put("montant_net", 126_898.37);
        data.add(row1);

        Map<String, Object> row2 = new HashMap<>();
        row2.put("societe", "EMAPHOS");
        row2.put("montant_brut", 25_833.07);
        row2.put("taux", 10.0);
        row2.put("retenue", 2_583.31);
        row2.put("montant_net", 23_249.76);
        data.add(row2);

        // Passer les données au rapport
        JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(data);
        JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, null, dataSource);

        // Exporter en PDF
        FileOutputStream outputStream = new FileOutputStream("etat_interets.pdf");
        JasperExportManager.exportReportToPdfStream(jasperPrint, outputStream);

        System.out.println("Rapport généré : etat_interets.pdf");
    }
}


<field name="societe" class="java.lang.String"/>
<field name="montantBrut" class="java.lang.Double"/>
<field name="taux" class="java.lang.Double"/>
<field name="retenue" class="java.lang.Double"/>
<field name="montantNet" class="java.lang.Double"/>


            
