<?xml version="1.0" encoding="UTF-8"?>
<!-- Created with Jaspersoft Studio version last-->
<jasperReport xmlns="http://jasperreports.sourceforge.net/jasperreports" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports http://jasperreports.sourceforge.net/xsd/jasperreport.xsd" name="Arrêtés-intra-groupe" pageWidth="595" pageHeight="842" columnWidth="555" leftMargin="20" rightMargin="20" topMargin="20" bottomMargin="20" uuid="9b052309-5517-4ffe-bf31-5e7ea5240878">
	<property name="com.jaspersoft.studio.data.defaultdataadapter" value="One Empty Record"/>
	<queryString>
		<![CDATA[]]>
	</queryString>
	<field name="adr1" class="java.lang.String"/>
	<field name="adr2" class="java.lang.String"/>
	<field name="adr3" class="java.lang.String"/>
	<field name="ref" class="java.lang.String"/>
	<field name="rattach" class="java.lang.String"/>
	<field name="sub_name" class="java.lang.String"/>
	<field name="pivot" class="java.lang.String"/>
	<field name="first_date" class="sun.util.resources.LocaleData"/>
	<field name="last_date" class="sun.util.resources.LocaleData"/>
	<field name="devise" class="java.lang.String"/>
	<field name="num_compte" class="java.lang.String"/>
	<field name="total_pivot_debit" class="java.math.BigDecimal"/>
	<field name="total_pivot_credit" class="java.math.BigDecimal"/>
	<pageHeader>
		<band height="86" splitType="Stretch">
			<line>
				<reportElement x="-11" y="45" width="572" height="1" uuid="1f1e5445-5263-4944-bdaf-ba8565d59bb4"/>
				<graphicElement>
					<pen lineWidth="2.0"/>
				</graphicElement>
			</line>
			<staticText>
				<reportElement x="212" y="18" width="350" height="29" forecolor="#000000" uuid="e2cebf24-75b5-429b-a546-20ccce80e7b8"/>
				<textElement textAlignment="Right">
					<font fontName="Serif" size="16"/>
				</textElement>
				<text><![CDATA[ÉTAT DES INTÉRÊTS INTRA-GROUPE]]></text>
			</staticText>
			<image>
				<reportElement x="40" y="-6" width="40" height="40" uuid="18d82036-0529-4760-a2bd-12cfe188530a"/>
				<imageExpression><![CDATA["C:\\Users\\JAZZARN\\Downloads\\societeGeneral.png"]]></imageExpression>
			</image>
			<staticText>
				<reportElement x="-15" y="-5" width="49" height="38" uuid="061fb447-960f-4763-9cf1-038fb48e6a67"/>
				<textElement>
					<font fontName="Serif" size="28" isBold="true"/>
				</textElement>
				<text><![CDATA[SG]]></text>
			</staticText>
			<staticText>
				<reportElement x="209" y="-15" width="355" height="40" uuid="cb04004d-e714-4875-b718-b0239352b48d"/>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font fontName="Serif" size="18" isBold="true" pdfFontName="Helvetica"/>
				</textElement>
				<text><![CDATA[SOGECASH INTERNATIONAL POOLING ]]></text>
			</staticText>
			<staticText>
				<reportElement x="-11" y="49" width="81" height="18" forecolor="#000000" uuid="385f5a30-09ef-46b4-8303-dd9fd0a88010"/>
				<textElement>
					<font fontName="Serif" size="10" isBold="false"/>
				</textElement>
				<text><![CDATA[PAYS : MAROC]]></text>
			</staticText>
			<staticText>
				<reportElement x="-11" y="65" width="111" height="17" uuid="88a5eabe-8fdb-4e7f-ba81-47b0b5b496c3"/>
				<textElement>
					<font fontName="Serif" size="10"/>
				</textElement>
				<text><![CDATA[VILLE : CASABLANCA]]></text>
			</staticText>
		</band>
	</pageHeader>
	<detail>
		<band height="630" splitType="Stretch">
			<textField>
				<reportElement x="391" y="57" width="131" height="22" uuid="ae9551e4-5912-48af-8734-4d4bd6cb2483"/>
				<textFieldExpression><![CDATA[$F{adr3}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-10" y="170" width="39" height="20" uuid="f99890f2-7b23-4325-9beb-7c297bf97807"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Devise :]]></text>
			</staticText>
			<textField>
				<reportElement x="44" y="140" width="57" height="20" uuid="6e749dc9-6ac3-41fb-abe5-4d6ac69f96c5"/>
				<textFieldExpression><![CDATA[$F{first_date}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-11" y="79" width="61" height="20" uuid="fe76598a-db9b-4a45-95ba-d3e5d3fb662e"/>
				<textElement>
					<font fontName="Serif"/>
				</textElement>
				<text><![CDATA[Référence :]]></text>
			</staticText>
			<staticText>
				<reportElement x="-10" y="140" width="57" height="20" uuid="4f770ee9-0537-4caa-8c69-52b153f12056"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Période du ]]></text>
			</staticText>
			<staticText>
				<reportElement x="99" y="140" width="16" height="20" uuid="4a163406-449c-4fa2-973a-3aea8624a640"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[au]]></text>
			</staticText>
			<textField>
				<reportElement x="470" y="37" width="77" height="20" uuid="cea35f39-3355-4186-afcc-86147f1ee643"/>
				<textFieldExpression><![CDATA[$F{adr2}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="390" y="37" width="80" height="20" uuid="e1b14707-6677-468a-8aec-abfe3a3d348e"/>
				<textFieldExpression><![CDATA[$F{adr1}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="70" y="97" width="100" height="14" uuid="9d69134d-075b-4474-982b-1586d0c5bbf2"/>
				<textFieldExpression><![CDATA[$F{pivot}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-12" y="94" width="81" height="20" uuid="2a70b3ee-f21d-4cee-b68a-8861390b54a1"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Nom du groupe :]]></text>
			</staticText>
			<textField>
				<reportElement x="79" y="111" width="100" height="20" uuid="12b1e6ce-4f54-4284-a48a-80afb7e051af"/>
				<textFieldExpression><![CDATA[$F{pivot}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="53" y="80" width="162" height="16" uuid="bf6dbfca-2890-41a0-9a44-adde1f46cdd0"/>
				<textFieldExpression><![CDATA[$F{ref}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-11" y="111" width="90" height="20" uuid="c6fcc6ac-e92d-474b-975e-31bf8e30bd54"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Nom de la société :]]></text>
			</staticText>
			<textField>
				<reportElement x="40" y="170" width="100" height="20" uuid="b13d6396-00af-4471-a3c1-0d34617cfb5e"/>
				<textFieldExpression><![CDATA[$F{devise}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="390" y="24" width="104" height="13" uuid="fc3b3da0-8372-46db-aba3-bc93391e4c90"/>
				<textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="390" y="7" width="104" height="13" uuid="478883c6-86a8-44f5-81b3-80ef5390b892"/>
				<textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="115" y="140" width="100" height="20" uuid="ab6f3314-5282-4f51-8fa6-bd96582a8884"/>
				<textFieldExpression><![CDATA[$F{last_date}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="10" y="238" width="100" height="20" uuid="f88f716c-b35b-47c6-9e5e-220ccdeb0ff1"/>
				<textFieldExpression><![CDATA[$F{last_date}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="505" y="225" width="57" height="20" uuid="6c6130c0-0acb-4a75-9ae6-bcdeb42a1a93"/>
				<textFieldExpression><![CDATA[$F{first_date}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-10" y="201" width="504" height="30" uuid="4d950bb5-a123-4871-84b3-2b768f4fa7a7"/>
				<textElement>
					<font fontName="Arial" size="18" isBold="true"/>
				</textElement>
				<text><![CDATA[RÉCAPITULATIF DES INTÉRÊTS INTRA-GROUPE]]></text>
			</staticText>
			<staticText>
				<reportElement x="-10" y="240" width="18" height="17" uuid="036baa40-a335-4f8b-879d-7051d65e88ee"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[au ]]></text>
			</staticText>
			<staticText>
				<reportElement x="-10" y="226" width="520" height="19" uuid="05b9c21f-a6df-448f-8769-62fffb30a5cb"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Vous trouverez dans le tableau ci-dessous le montant des intérêts reçus ou payés par la société pour la période du ]]></text>
			</staticText>
			<line>
				<reportElement x="-10" y="223" width="575" height="1" uuid="08de203f-08a8-4937-a0d4-682e0f9adefc"/>
				<graphicElement>
					<pen lineWidth="1.3"/>
				</graphicElement>
			</line>
			<staticText>
				<reportElement x="-10" y="268" width="180" height="30" uuid="eef27b8f-6a2b-49f5-b0e5-1cbf0e277ff2"/>
				<box>
					<topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font fontName="Serif" isBold="true"/>
				</textElement>
				<text><![CDATA[Nom de la société et N° de compte
pour la comptabilisation des intérêts]]></text>
			</staticText>
			<staticText>
				<reportElement x="-10" y="298" width="180" height="35" uuid="df01319d-2186-4ecd-bd57-82d30f517831"/>
				<box>
					<topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<text><![CDATA[]]></text>
			</staticText>
			<staticText>
				<reportElement x="170" y="268" width="385" height="30" uuid="21db64ac-e373-47f9-a0ac-d2490d58d420"/>
				<box>
					<topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font fontName="Serif" isBold="true"/>
				</textElement>
				<text><![CDATA[Intérêts nets reçus ou payés par la société]]></text>
			</staticText>
			<staticText>
				<reportElement x="170" y="298" width="70" height="35" uuid="6bfaae99-17b7-4d07-9a5b-e8d7bbaa9277"/>
				<box>
					<topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font fontName="Serif"/>
				</textElement>
				<text><![CDATA[Débit
Crédit]]></text>
			</staticText>
			<staticText>
				<reportElement x="240" y="298" width="315" height="35" uuid="195c3b60-23ef-4377-9879-c10d3cdb86ad"/>
				<box>
					<topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<text><![CDATA[]]></text>
			</staticText>
			<textField>
				<reportElement x="0" y="300" width="160" height="14" uuid="306f681e-033a-4d86-9569-c3825e06b751"/>
				<textElement verticalAlignment="Middle">
					<font fontName="Serif"/>
				</textElement>
				<textFieldExpression><![CDATA[$F{pivot}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="314" width="160" height="17" uuid="482d6188-ec42-4379-97e9-6388b1cda17d"/>
				<textElement verticalAlignment="Middle">
					<font fontName="Serif"/>
				</textElement>
				<textFieldExpression><![CDATA[$F{num_compte}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="391" y="300" width="156" height="14" uuid="d9c304b1-9061-4807-bb3b-cc52ae984678"/>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font fontName="Serif"/>
				</textElement>
				<textFieldExpression><![CDATA[$F{total_pivot_debit}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="390" y="317" width="157" height="14" uuid="35524469-769c-4660-9277-3e6dbf432c86"/>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font fontName="Serif"/>
				</textElement>
				<textFieldExpression><![CDATA[$F{total_pivot_credit}]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="77" y="355" width="100" height="20" uuid="f3ffa45f-6f0c-418b-9a6d-03d86339ebcd"/>
				<textFieldExpression><![CDATA[$F{last_date}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="57" y="356" width="18" height="17" uuid="ca627289-def8-4ef2-a13d-875a89b11685"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[au ]]></text>
			</staticText>
			<textField>
				<reportElement x="-9" y="355" width="57" height="20" uuid="5fcb2779-b2bf-4a32-bc62-f476421c0c4b"/>
				<textFieldExpression><![CDATA[$F{first_date}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-5" y="343" width="570" height="19" uuid="aec2ed44-b1b3-4bbe-85a9-4ad3a5877f18"/>
				<textElement>
					<font fontName="Arial"/>
				</textElement>
				<text><![CDATA[Vous trouverez dans le tableau ci-dessous le montant des intérêts reçus ou payés par les entités nivelées pour la période du]]></text>
			</staticText>
		</band>
	</detail>
	<pageFooter>
		<band height="38" splitType="Stretch">
			<staticText>
				<reportElement x="0" y="5" width="549" height="15" uuid="fae483a0-1a41-4b43-95ef-ef20502f9848"/>
				<textElement>
					<font fontName="Arial" size="9"/>
				</textElement>
				<text><![CDATA[Ce relevé vous est communiqué à titre indicatif. Pour toute information complémentaire, veuillez vous adresser à vos contacts habituels.]]></text>
			</staticText>
			<textField evaluationTime="Report">
				<reportElement x="528" y="24" width="40" height="14" uuid="ab1acabc-43df-4ebc-95be-5b911f3289bf"/>
				<textElement>
					<font fontName="Arial" size="9" isBold="false"/>
				</textElement>
				<textFieldExpression><![CDATA[" " + $V{PAGE_NUMBER}]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="-16" y="24" width="486" height="14" uuid="85d958e1-1364-4030-a287-0724ca557649"/>
				<textElement textAlignment="Center">
					<font fontName="Arial" size="7"/>
				</textElement>
				<text><![CDATA[SOCIETE GENERALE SA AU CAPITAL DE 1 066 714 367,50 EUR. SIEGE SOCIAL A PARIS, 29 BD HAUSMANN - 552.120.222 R.C.S. PARIS.]]></text>
			</staticText>
			<line>
				<reportElement x="-11" y="20" width="572" height="1" uuid="675fb861-83d7-418a-904a-1c642a9f325e"/>
				<graphicElement>
					<pen lineWidth="2.0"/>
				</graphicElement>
			</line>
			<textField>
				<reportElement x="480" y="24" width="48" height="14" uuid="c19b3836-79c7-49c3-aa0d-bf52351efa2b"/>
				<textElement textAlignment="Right">
					<font fontName="Arial" size="9" isBold="false"/>
				</textElement>
				<textFieldExpression><![CDATA["Page "+$V{PAGE_NUMBER}+" /"]]></textFieldExpression>
			</textField>
		</band>
	</pageFooter>
</jasperReport>
