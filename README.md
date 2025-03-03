test


<?xml version="1.0" encoding="UTF-8"?>
<jasperReport xmlns="http://jasperreports.sourceforge.net/jasperreports"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports
    http://jasperreports.sourceforge.net/xsd/jasperreport.xsd"
    name="DetailInterets" pageWidth="595" pageHeight="842" columnWidth="555"
    leftMargin="20" rightMargin="20" topMargin="20" bottomMargin="20">

    <!-- Définition des Champs -->
    <field name="nomSociete" class="java.lang.String"/>
    <field name="type" class="java.lang.String"/>
    <field name="montantBrut" class="java.lang.Double"/>
    <field name="taux" class="java.lang.Double"/>
    <field name="retenue" class="java.lang.Double"/>
    <field name="montantNet" class="java.lang.Double"/>

    <detail>
        <band height="150">

            <!-- Titre -->
            <staticText>
                <reportElement x="0" y="0" width="555" height="20" backcolor="#DDDDDD"/>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font size="12" isBold="true"/>
                </textElement>
                <text><![CDATA[DÉTAIL DES INTÉRÊTS INTRA-GROUPE]]></text>
            </staticText>

            <!-- Tableau -->
            <frame>
                <reportElement x="0" y="30" width="555" height="100" backcolor="#FFFFFF"/>

                <!-- Ligne En-tête -->
                <staticText>
                    <reportElement x="0" y="0" width="100" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Nom de la société]]></text>
                </staticText>

                <staticText>
                    <reportElement x="100" y="0" width="80" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Type]]></text>
                </staticText>

                <staticText>
                    <reportElement x="180" y="0" width="90" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Montant Brut]]></text>
                </staticText>

                <staticText>
                    <reportElement x="270" y="0" width="80" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Taux]]></text>
                </staticText>

                <staticText>
                    <reportElement x="350" y="0" width="90" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Retenue]]></text>
                </staticText>

                <staticText>
                    <reportElement x="440" y="0" width="115" height="20" backcolor="#CCCCCC"/>
                    <textElement textAlignment="Center"/>
                    <text><![CDATA[Montant Net]]></text>
                </staticText>

                <!-- Ligne Données -->
                <textField>
                    <reportElement x="0" y="20" width="100" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Center"/>
                    <textFieldExpression><![CDATA[$F{nomSociete}]]></textFieldExpression>
                </textField>

                <textField>
                    <reportElement x="100" y="20" width="80" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Center"/>
                    <textFieldExpression><![CDATA[$F{type}]]></textFieldExpression>
                </textField>

                <textField>
                    <reportElement x="180" y="20" width="90" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Right"/>
                    <textFieldExpression><![CDATA[$F{montantBrut}]]></textFieldExpression>
                </textField>

                <textField>
                    <reportElement x="270" y="20" width="80" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Right"/>
                    <textFieldExpression><![CDATA[$F{taux}]]></textFieldExpression>
                </textField>

                <textField>
                    <reportElement x="350" y="20" width="90" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Right"/>
                    <textFieldExpression><![CDATA[$F{retenue}]]></textFieldExpression>
                </textField>

                <textField>
                    <reportElement x="440" y="20" width="115" height="20" backcolor="#FFFFFF" border="Bottom"/>
                    <textElement textAlignment="Right"/>
                    <textFieldExpression><![CDATA[$F{montantNet}]]></textFieldExpression>
                </textField>
            </frame>
        </band>
    </detail>
</jasperReport>
