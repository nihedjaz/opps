<?xml version="1.0" encoding="UTF-8"?>
<!-- Created with Jaspersoft Studio version last-->
<jasperReport xmlns="http://jasperreports.sourceforge.net/jasperreports" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports http://jasperreports.sourceforge.net/xsd/jasperreport.xsd" name="Blank_A4_2" pageWidth="595" pageHeight="842" columnWidth="555" leftMargin="20" rightMargin="20" topMargin="20" bottomMargin="20" uuid="3e817595-70fc-4f32-b3bd-657278376565">
    <property name="com.jaspersoft.studio.data.defaultdataadapter" value="One Empty Record"/>
    <style name="Table_TH" mode="Opaque" backcolor="#FFFFFF">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <style name="Table_CH" mode="Opaque" backcolor="#EDEDED">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <style name="Table_TD" mode="Opaque" backcolor="#FFFFFF">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <style name="Table 1_TH" mode="Opaque" backcolor="#FFFFFF">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <style name="Table 1_CH" mode="Opaque" backcolor="#FFFFFF">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <style name="Table 1_TD" mode="Opaque" backcolor="#FFFFFF">
        <box>
            <pen lineWidth="0.5" lineColor="#000000"/>
            <topPen lineWidth="0.5" lineColor="#000000"/>
            <leftPen lineWidth="0.5" lineColor="#000000"/>
            <bottomPen lineWidth="0.5" lineColor="#000000"/>
            <rightPen lineWidth="0.5" lineColor="#000000"/>
        </box>
    </style>
    <subDataset name="Dataset1" uuid="4ace9ecd-388c-4a8f-90ed-974433f2dbab">
        <queryString>
            <![CDATA[]]>
        </queryString>
        <field name="ancien_solde" class="java.math.BigDecimal"/>
        <field name="date_val" class="java.time.LocalDate"/>
        <field name="capitaux" class="java.math.BigDecimal"/>
        <field name="solde" class="java.math.BigDecimal"/>
        <field name="jour" class="java.lang.Number"/>
        <field name="nombres" class="java.math.BigDecimal"/>
        <field name="taux_debit" class="java.math.BigDecimal"/>
        <field name="taux_credit" class="java.math.BigDecimal"/>
        <field name="interet_debit" class="java.math.BigDecimal"/>
        <field name="interet_credit" class="java.math.BigDecimal"/>
        <field name="pay" class="java.lang.String"/>
        <field name="ville" class="java.lang.String"/>
        <field name="adr1" class="java.lang.String"/>
        <field name="adr2" class="java.lang.String"/>
        <field name="sub_name" class="java.lang.String"/>
        <field name="pivot" class="java.lang.String"/>
        <field name="first_date" class="java.time.LocalDate"/>
        <field name="last_date" class="java.time.LocalDate"/>
        <field name="devise" class="java.lang.String"/>
        <field name="num_compte" class="java.lang.String"/>
        <field name="soc_name" class="java.lang.String"/>
        <field name="total_cap" class="java.math.BigDecimal"/>
        <field name="total_jrs" class="java.math.BigDecimal"/>
        <field name="total_numbrs" class="java.math.BigDecimal"/>
        <field name="total_id" class="java.math.BigDecimal"/>
        <field name="total_ic" class="java.math.BigDecimal"/>
    </subDataset>
    <parameter name="tableDataSource" class="net.sf.jasperreports.engine.data.JRBeanCollectionDataSource"/>
    <field name="pay" class="java.lang.String"/>
    <field name="ville" class="java.lang.String"/>
    <field name="adr1" class="java.lang.String"/>
    <field name="adr2" class="java.lang.String"/>
    <field name="adr3" class="java.lang.String"/>
    <field name="ref" class="java.lang.String"/>
    <field name="rattach" class="java.lang.String"/>
    <field name="sub_name" class="java.lang.String"/>
    <field name="pivot" class="java.lang.String"/>
    <field name="first_date" class="java.time.LocalDate"/>
    <field name="last_date" class="java.time.LocalDate"/>
    <field name="devise" class="java.lang.String"/>
    <field name="num_compte" class="java.lang.String"/>
    <field name="soc_name" class="java.lang.String"/>
    <field name="taux" class="java.math.BigDecimal"/>
    <field name="montant_b_d" class="java.math.BigDecimal"/>
    <field name="montant_b_c" class="java.math.BigDecimal"/>
    <field name="montant_n_d" class="java.math.BigDecimal"/>
    <field name="montant_n_c" class="java.math.BigDecimal"/>
    <field name="mon_rsa_c" class="java.math.BigDecimal"/>
    <field name="mon_rsa_d" class="java.math.BigDecimal"/>
    <field name="montant_in_d" class="java.math.BigDecimal"/>
    <field name="montant_in_c" class="java.math.BigDecimal"/>
    <pageHeader>
        <band height="86" splitType="Stretch">
            <staticText>
                <reportElement x="-11" y="49" width="40" height="18" forecolor="#000000" uuid="693a41de-a9a8-46ac-a340-9b58ee801549"/>
                <textElement>
                    <font fontName="Arial" size="10" isBold="false"/>
                </textElement>
                <text><![CDATA[PAYS : ]]></text>
            </staticText>
            <image>
                <reportElement x="40" y="-6" width="40" height="40" uuid="1c4e3760-1f78-42b0-9f5a-d7e906fa7661"/>
                <imageExpression><![CDATA["C:\\Users\\JAZZARN\\Downloads\\unnamed.png"]]></imageExpression>
            </image>
            <staticText>
                <reportElement x="212" y="18" width="350" height="29" forecolor="#000000" uuid="daf95bcb-1ff6-4f82-88cc-27e1da4c9cbf"/>
                <textElement textAlignment="Right">
                    <font fontName="Arial" size="16"/>
                </textElement>
                <text><![CDATA[ÉTAT DÉTAIL DES INTÉRÊTS INTRA-GROUPE]]></text>
            </staticText>
            <staticText>
                <reportElement x="209" y="-15" width="355" height="40" uuid="02d3a236-43c8-4245-9aee-a3e3e5e8b229"/>
                <textElement textAlignment="Right" verticalAlignment="Middle">
                    <font fontName="Arial" size="18" isBold="true" pdfFontName="Helvetica"/>
                </textElement>
                <text><![CDATA[SOGECASH INTERNATIONAL POOLING ]]></text>
            </staticText>
            <staticText>
                <reportElement x="-15" y="-5" width="49" height="38" uuid="fc47d53e-60ed-4cb4-955a-41ed663d9be2"/>
                <textElement>
                    <font fontName="Arial" size="28" isBold="true"/>
                </textElement>
                <text><![CDATA[SG]]></text>
            </staticText>
            <staticText>
                <reportElement x="-11" y="65" width="40" height="17" uuid="c9e1053c-f0ef-4510-af2a-e3d595694bd8"/>
                <textElement>
                    <font fontName="Arial" size="10"/>
                </textElement>
                <text><![CDATA[VILLE : ]]></text>
            </staticText>
            <line>
                <reportElement x="-11" y="45" width="572" height="1" uuid="b98f64fc-d8c8-4628-83d1-788651fa0f6c"/>
                <graphicElement>
                    <pen lineWidth="2.0"/>
                </graphicElement>
            </line>
            <textField>
                <reportElement x="34" y="49" width="100" height="15" uuid="e8dc8e22-8cd4-4923-822e-6297303a35ff"/>
                <textFieldExpression><![CDATA[$F{pay}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="34" y="63" width="100" height="19" uuid="fa586764-5ac2-41f4-be95-8af88e6c3746"/>
                <textFieldExpression><![CDATA[$F{ville}]]></textFieldExpression>
            </textField>
        </band>
    </pageHeader>
    <detail>
        <band height="677" splitType="Stretch">
            <textField>
                <reportElement x="394" y="7" width="100" height="13" uuid="8bfbcea5-abc6-4063-bb72-247ed0e6e607"/>
                <textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="394" y="24" width="100" height="13" uuid="ef51ed4c-c210-4fa3-956c-92d7cce020de"/>
                <textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="394" y="37" width="86" height="20" uuid="22183458-96a1-4698-b257-80d6e7aff874"/>
                <textFieldExpression><![CDATA[$F{adr1}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="480" y="37" width="62" height="20" uuid="6b767f8d-f538-4d50-b565-0bab5e5ff8c7"/>
                <textFieldExpression><![CDATA[$F{adr2}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="-10" y="228" width="350" height="30" uuid="1836b038-192f-4478-a096-badc1aff9ffd"/>
                <textElement>
                    <font fontName="Arial" size="18" isBold="true"/>
                </textElement>
                <text><![CDATA[DÉTAIL DES INTÉRÊTS INTRA-GROUPE]]></text>
            </staticText>
            <staticText>
                <reportElement x="-12" y="189" width="110" height="20" uuid="509e9e9c-58f9-4cfa-a4a5-05c7ac3de916"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Entité de rattachement :]]></text>
            </staticText>
            <staticText>
                <reportElement x="-10" y="140" width="57" height="20" uuid="62892f0c-2742-4fd5-b63d-9ccb803cbae0"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Période du ]]></text>
            </staticText>
            <staticText>
                <reportElement x="-11" y="111" width="90" height="20" uuid="0177a056-45bd-4347-90b7-393519beb4bc"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Nom de la société :]]></text>
            </staticText>
            <staticText>
                <reportElement x="-10" y="170" width="39" height="20" uuid="22a12ec8-2c93-456c-853f-cc42703f1d1d"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Devise :]]></text>
            </staticText>
            <line>
                <reportElement x="-10" y="250" width="575" height="1" uuid="3c050b20-e2ac-44c5-b75b-940b1dafc76e"/>
                <graphicElement>
                    <pen lineWidth="1.3"/>
                </graphicElement>
            </line>
            <staticText>
                <reportElement x="99" y="140" width="16" height="20" uuid="adb20794-ef78-47e6-ac22-39c18dc89d3c"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[au]]></text>
            </staticText>
            <staticText>
                <reportElement x="-12" y="94" width="81" height="20" uuid="355c883e-271d-4db8-808b-e3607eec7871"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Nom du groupe :]]></text>
            </staticText>
            <staticText>
                <reportElement x="-10" y="253" width="500" height="19" uuid="a28bb339-286b-450f-90e4-33f4957ddf7b"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Vous trouverez dans le tableau ci-dessous le détail des intérêts reçus ou payés par la société pour la période du ]]></text>
            </staticText>
            <staticText>
                <reportElement x="-10" y="267" width="18" height="17" uuid="343025bf-5835-4434-9ceb-193434478f83"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[au ]]></text>
            </staticText>
            <staticText>
                <reportElement x="-11" y="79" width="61" height="20" uuid="945444d4-2be3-4553-81a4-bd301b51a022"/>
                <textElement>
                    <font fontName="Arial"/>
                </textElement>
                <text><![CDATA[Référence :]]></text>
            </staticText>
            <textField>
                <reportElement x="53" y="80" width="100" height="16" uuid="76804318-236c-4363-8905-d7a1460d0fc2"/>
                <textFieldExpression><![CDATA[$F{ref}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="70" y="97" width="100" height="14" uuid="46267e4e-0542-4ce3-96ae-58138fe74184"/>
                <textFieldExpression><![CDATA[$F{pivot}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="79" y="111" width="100" height="20" uuid="1ff05992-5462-470d-a503-387d482207d1"/>
                <textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="44" y="140" width="57" height="20" uuid="45f3470e-2cc5-4365-a807-ee31afb19357"/>
                <textFieldExpression><![CDATA[$F{first_date}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="115" y="140" width="100" height="20" uuid="6f827afd-e453-4704-a375-39acf26c7f52"/>
                <textFieldExpression><![CDATA[$F{last_date}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="490" y="252" width="57" height="20" uuid="89106ea9-4e13-400c-bb60-92ab89e9883c"/>
                <textFieldExpression><![CDATA[$F{first_date}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="10" y="265" width="100" height="20" uuid="0949e8ee-2a85-456e-98d4-edc63c0053c7"/>
                <textFieldExpression><![CDATA[$F{last_date}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="40" y="170" width="100" height="20" uuid="4f6074ef-3d00-4b0d-af7d-39722cea8f6f"/>
                <textFieldExpression><![CDATA[$F{devise}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="100" y="190" width="100" height="20" uuid="80065a90-4b21-4044-b8be-0b812b5df0e4"/>
                <textFieldExpression><![CDATA[$F{rattach}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="1" y="630" width="548" height="43" uuid="1933146e-8abb-420b-8608-64af4f046c40"/>
                <textElement>
                    <font fontName="Arial" size="7"/>
                </textElement>
                <text><![CDATA[Position du compte :
+ signifie que le compte est créditeur par rapport à la société centralisatrice;
- signifie que le compte est débiteur par rapport à la société centralisatrice.
Les soldes ci-dessus comprennent les nivellements propres au présent service et, le cas échéant, les prêts/emprunts antérieurs à celui-ci et éventuellement toute modification ultérieure,
communiqués à la banque par le pivot de trésorerie.]]></text>
            </staticText>
            <componentElement>
<!--                <reportElement positionType="Float" x="-1" y="428" width="555" height="132" uuid="fd403e9d-1dd1-4157-a3e5-3787b3b2ea50"/>-->
<!--                <jr:table xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd">-->
<!--                    <datasetRun subDataset="Dataset1" uuid="8d006b1f-27a7-459f-8cee-4aa5fd6c2024">-->
<!--                        <dataSourceExpression><![CDATA[new net.sf.jasperreports.engine.JREmptyDataSource()]]></dataSourceExpression>-->
<!--&lt;!&ndash;                        <dataSourceExpression><![CDATA[$P{tableDataSource}]]></dataSourceExpression>&ndash;&gt;-->

<!--                    </datasetRun>-->
                <reportElement positionType="Float" x="-1" y="428" width="555" height="132" uuid="fd403e9d-1dd1-4157-a3e5-3787b3b2ea50"/>
                <jr:table xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" whenNoDataType="AllSectionsNoDetail">
                    <datasetRun subDataset="Dataset1" uuid="c21dff75-8a26-4267-a515-cc0a6e02f5f5">
                        <connectionExpression><![CDATA[$P{tableDataSource} ]]></connectionExpression>
                    </datasetRun>
                    <jr:columnGroup width="240" uuid="bb0e1153-4923-4612-a24d-cc7c3f335597">
                        <jr:columnGroup width="150" uuid="8f1a7c09-6585-4829-af2e-662b942f9319">
                            <jr:column width="60" uuid="c7370fcf-193b-4512-88b8-8d6b65e9a45a">
                                <property name="Date de valeur" value="NEW_VALUE"/>
                                <jr:tableHeader style="Table_TH" height="40">
                                    <property name="com.jaspersoft.studio.layout" value="com.jaspersoft.studio.editor.layout.VerticalRowLayout"/>
                                    <box>
                                        <topPen lineWidth="0.9"/>
                                        <leftPen lineWidth="0.9"/>
                                        <bottomPen lineWidth="0.9"/>
                                        <rightPen lineWidth="0.9"/>
                                    </box>
                                    <staticText>
                                        <reportElement x="0" y="0" width="60" height="40" uuid="e3d1a20d-b0bf-4b65-acc8-fbe5891ec125"/>
                                        <textElement textAlignment="Center" verticalAlignment="Middle">
                                            <font fontName="Arial" isBold="true"/>
                                        </textElement>
                                        <text><![CDATA[Date de valeur]]></text>
                                    </staticText>
                                </jr:tableHeader>
                                <jr:tableFooter style="Table_TH" height="30">
                                    <box>
                                        <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                </jr:tableFooter>
                                <jr:columnHeader style="Table_CH" height="30">
                                    <box>
                                        <topPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <staticText>
                                        <reportElement x="1" y="0" width="59" height="30" uuid="79dfe6b5-a007-42e6-98de-6a6c50151fb3"/>
                                        <textElement textAlignment="Right" verticalAlignment="Middle">
                                            <font fontName="Arial" isBold="true"/>
                                        </textElement>
                                        <text><![CDATA[Report ]]></text>
                                    </staticText>
                                </jr:columnHeader>
                                <jr:detailCell style="Table_TD" height="30">
                                    <box>
                                        <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <textField>
                                        <reportElement x="2" y="7" width="58" height="20" uuid="765159d5-6179-4a31-825d-d98697c6fa9f"/>
                                        <textFieldExpression><![CDATA[$F{date_val}]]></textFieldExpression>
                                    </textField>
                                </jr:detailCell>
                            </jr:column>
                            <jr:column width="90" uuid="3e7d21f2-7b16-4521-a354-82d100ddae85">
                                <property name="capitaux" value="NEW_VALUE"/>
                                <jr:tableHeader style="Table_TH" height="40">
                                    <box>
                                        <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <staticText>
                                        <reportElement x="2" y="0" width="78" height="39" uuid="f21404b4-171e-414d-9c7d-33b9928a1619"/>
                                        <textElement textAlignment="Center" verticalAlignment="Middle">
                                            <font fontName="Arial" isBold="true"/>
                                        </textElement>
                                        <text><![CDATA[Capitaux]]></text>
                                    </staticText>
                                </jr:tableHeader>
                                <jr:tableFooter style="Table_TH" height="30">
                                    <box>
                                        <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <textField>
                                        <reportElement x="3" y="4" width="77" height="20" uuid="fe81ff5e-c6af-4966-a5dc-1d2ed8818b93"/>
                                        <textFieldExpression><![CDATA[$F{total_cap}]]></textFieldExpression>
                                    </textField>
                                </jr:tableFooter>
                                <jr:columnHeader style="Table_CH" height="30">
                                    <property name="com.jaspersoft.studio.layout" value="com.jaspersoft.studio.editor.layout.VerticalRowLayout"/>
                                    <box>
                                        <topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <staticText>
                                        <reportElement x="0" y="0" width="90" height="30" uuid="96320cd6-4358-4719-a431-fc7b5aa8b74a"/>
                                        <textElement verticalAlignment="Middle">
                                            <font fontName="Arial" isBold="true"/>
                                        </textElement>
                                        <text><![CDATA[solde précédent :]]></text>
                                    </staticText>
                                </jr:columnHeader>
                                <jr:detailCell style="Table_TD" height="30">
                                    <box>
                                        <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                        <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    </box>
                                    <textField>
                                        <reportElement x="12" y="6" width="60" height="20" uuid="e14b3f59-4113-4272-8c25-f4249f06edfc"/>
                                        <textFieldExpression><![CDATA[$F{capitaux}]]></textFieldExpression>
                                    </textField>
                                </jr:detailCell>
                            </jr:column>
                        </jr:columnGroup>
                        <jr:column width="90" uuid="21299fc6-ad0b-44d6-991b-e1b71e4ad5c7">
                            <jr:tableHeader style="Table_TH" height="40">
                                <box>
                                    <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                </box>
                                <staticText>
                                    <reportElement x="10" y="0" width="70" height="40" uuid="c332f633-7d9f-4903-83c5-bcb0169ebfa0"/>
                                    <textElement textAlignment="Center" verticalAlignment="Middle">
                                        <font fontName="Arial" isBold="true"/>
                                    </textElement>
                                    <text><![CDATA[Solde]]></text>
                                </staticText>
                            </jr:tableHeader>
                            <jr:tableFooter style="Table_TH" height="30">
                                <box>
                                    <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                </box>
                            </jr:tableFooter>
                            <jr:columnHeader style="Table_CH" height="30">
                                <box>
                                    <topPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                    <leftPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                                    <bottomPen lineWidth="0.9" lineStyle="Solid" lineColor="#000000"/>
                                    <rightPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                                </box>
                                <textField>
                                    <reportElement x="0" y="0" width="90" height="30" uuid="d09023d0-762b-4cd7-9b81-618845a7726d"/>
                                    <textElement textAlignment="Right" verticalAlignment="Middle">
                                        <font fontName="Arial" isBold="true"/>
                                    </textElement>
                                    <textFieldExpression><![CDATA[$F{ancien_solde}]]></textFieldExpression>
                                </textField>
                            </jr:columnHeader>
                            <jr:detailCell style="Table_TD" height="30">
                                <box>
                                    <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                    <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                </box>
                                <textField>
                                    <reportElement x="1" y="6" width="79" height="20" uuid="265ef99a-53b7-4763-92aa-4571054b638e"/>
                                    <textFieldExpression><![CDATA[$F{solde}]]></textFieldExpression>
                                </textField>
                            </jr:detailCell>
                        </jr:column>
                    </jr:columnGroup>
                    <jr:column width="30" uuid="d69c17fc-7a6c-4ec2-9dfa-15396067b134">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="0" y="0" width="30" height="39" uuid="09584a1b-e975-4a57-9609-e834932df6e8"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Jours]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="4" y="6" width="24" height="20" uuid="17b99e7d-6696-4833-9459-1bbf31ade63a"/>
                                <textFieldExpression><![CDATA[$F{total_jrs}]]></textFieldExpression>
                            </textField>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="4" y="8" width="24" height="20" uuid="921d95db-d92d-4119-8108-baf458777542"/>
                                <textFieldExpression><![CDATA[$F{jour}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                    <jr:column width="80" uuid="2cda10f0-3915-4747-9afd-4ec76eb279b4">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="10" y="1" width="56" height="39" uuid="9fc85a00-8abc-4a9d-8ece-4ee70b7a4a61"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Nombres]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="1" y="5" width="59" height="20" uuid="8cf7d6c8-ebcd-4ff5-84bb-2c84ce7342ca"/>
                                <textFieldExpression><![CDATA[$F{total_numbrs}]]></textFieldExpression>
                            </textField>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="4" y="8" width="71" height="20" uuid="c468f080-2f4e-41b0-ade2-7ad74e3138a9"/>
                                <textFieldExpression><![CDATA[$F{nombres}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                    <jr:column width="50" uuid="67c918e0-b430-4c95-9ffc-f3438698cf9e">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="0" y="0" width="50" height="40" uuid="8f9c74bb-2682-4f3e-9291-4b2e8607b24a"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Taux
débiteurs]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="5" y="9" width="42" height="20" uuid="d1ff4cc5-a134-4168-bd25-5201cf3bf97c"/>
                                <textFieldExpression><![CDATA[$F{taux_debit}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                    <jr:column width="50" uuid="efdb9f33-1aee-474c-9e5c-654deee3b9be">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="0" y="0" width="50" height="39" uuid="799d1d51-b858-4366-bfcb-a051adc2e498"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Taux
créditeurs]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="1" y="8" width="34" height="20" uuid="3a39d73b-03c7-4c02-b304-74ac29845c3a"/>
                                <textFieldExpression><![CDATA[$F{taux_credit}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                    <jr:column width="50" uuid="6d79fa1c-7709-404e-854a-f4939477a343">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="0" y="0" width="50" height="39" uuid="e58b75da-e973-4b3c-a439-1ae035277a0d"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Intérêts
débiteurs]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="6" y="5" width="40" height="20" uuid="6928774b-5dba-4693-a02e-b3da26a7939d"/>
                                <textFieldExpression><![CDATA[$F{total_id}]]></textFieldExpression>
                            </textField>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="1" y="9" width="49" height="20" uuid="6d144e8d-7da0-4277-851c-3acc6a2018f6"/>
                                <textFieldExpression><![CDATA[$F{interet_debit}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                    <jr:column width="50" uuid="fdca2d7a-a6e1-4199-9cc9-7e55f3439e41">
                        <jr:tableHeader style="Table_TH" height="40">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <staticText>
                                <reportElement x="0" y="0" width="50" height="40" uuid="dc4465f9-5f53-4035-8f43-6a9bb228c122"/>
                                <textElement textAlignment="Center" verticalAlignment="Middle">
                                    <font fontName="Arial" isBold="true"/>
                                </textElement>
                                <text><![CDATA[Intérêts
créditeurs]]></text>
                            </staticText>
                        </jr:tableHeader>
                        <jr:tableFooter style="Table_TH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="11" y="5" width="30" height="20" uuid="c16c42f5-b47e-4875-81ea-92f33a098d0b"/>
                                <textFieldExpression><![CDATA[$F{total_ic}]]></textFieldExpression>
                            </textField>
                        </jr:tableFooter>
                        <jr:columnHeader style="Table_CH" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                        </jr:columnHeader>
                        <jr:detailCell style="Table_TD" height="30">
                            <box>
                                <topPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <leftPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <bottomPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                                <rightPen lineWidth="0.8" lineStyle="Solid" lineColor="#000000"/>
                            </box>
                            <textField>
                                <reportElement x="0" y="10" width="50" height="20" uuid="5a6d5839-a9e5-4e33-aeee-6e58aec495b8"/>
                                <textFieldExpression><![CDATA[$F{interet_credit}]]></textFieldExpression>
                            </textField>
                        </jr:detailCell>
                    </jr:column>
                </jr:table>
            </componentElement>
            <staticText>
                <reportElement x="-1" y="290" width="116" height="40" uuid="15902c6a-d42c-4cbe-84c1-e87d134737f8"/>
                <box>
                    <topPen lineWidth="1.2"/>
                    <leftPen lineWidth="1.2"/>
                    <bottomPen lineWidth="1.2"/>
                    <rightPen lineWidth="1.2"/>
                </box>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Nom de la société et
N° de compte pour la
comptabilisation des intérêts]]></text>
            </staticText>
            <staticText>
                <reportElement x="115" y="290" width="66" height="40" uuid="31f0daf0-4028-4fcc-b3da-84a79fbd2635"/>
                <box>
                    <topPen lineWidth="1.2"/>
                    <leftPen lineWidth="1.2"/>
                    <bottomPen lineWidth="1.2"/>
                    <rightPen lineWidth="1.2"/>
                </box>
                <text><![CDATA[]]></text>
            </staticText>
            <staticText>
                <reportElement x="181" y="290" width="99" height="40" uuid="511afa0c-73bb-411c-ae5e-9d9f04ed0d52"/>
                <box>
                    <topPen lineWidth="1.2"/>
                    <leftPen lineWidth="1.2"/>
                    <bottomPen lineWidth="1.2"/>
                    <rightPen lineWidth="1.2"/>
                </box>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font size="11" isBold="true"/>
                </textElement>
                <text><![CDATA[Montant brut]]></text>
            </staticText>
            <staticText>
                <reportElement x="280" y="290" width="160" height="40" uuid="3164a45a-0a57-487d-ae84-53026bb86ffe"/>
                <box>
                    <topPen lineWidth="1.2"/>
                    <leftPen lineWidth="1.2"/>
                    <bottomPen lineWidth="1.2"/>
                    <rightPen lineWidth="1.2"/>
                </box>
                <text><![CDATA[]]></text>
            </staticText>
            <staticText>
                <reportElement x="440" y="290" width="115" height="40" uuid="98e6655f-14de-4ee9-8952-64faec05f546"/>
                <box>
                    <topPen lineWidth="1.2"/>
                    <leftPen lineWidth="1.2"/>
                    <bottomPen lineWidth="1.2"/>
                    <rightPen lineWidth="1.2"/>
                </box>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Montant net]]></text>
            </staticText>
            <textField>
                <reportElement x="-1" y="330" width="116" height="64" uuid="d03600ef-5e20-4d83-854f-23b702da2abf"/>
                <box>
                    <topPen lineWidth="1.1"/>
                    <leftPen lineWidth="1.1"/>
                    <bottomPen lineWidth="1.1"/>
                    <rightPen lineWidth="1.1"/>
                </box>
                <textFieldExpression><![CDATA[$F{sub_name}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="190" y="330" width="80" height="20" uuid="1966a774-9e99-467c-841c-f8feae756daa"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{montant_b_d}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="190" y="350" width="80" height="20" uuid="d7fd1b01-2175-40d3-8e01-c73e3e7e55e9"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{montant_n_c}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="440" y="330" width="109" height="20" uuid="8e2e733d-a04a-459d-b066-50dfa7dc71b0"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{montant_n_d}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement stretchType="RelativeToTallestObject" x="289" y="330" width="31" height="20" uuid="437f43e8-5ea8-4723-85d1-f84a16ada092"/>
                <box>
                    <topPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                    <leftPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                    <bottomPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                    <rightPen lineWidth="0.0" lineStyle="Solid" lineColor="#000000"/>
                </box>
                <textFieldExpression><![CDATA[$F{taux}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="115" y="330" width="66" height="40" uuid="2a516128-7309-45cf-819d-219abb59f390"/>
                <box>
                    <topPen lineWidth="1.1"/>
                    <leftPen lineWidth="1.1"/>
                    <bottomPen lineWidth="1.1"/>
                    <rightPen lineWidth="1.1"/>
                </box>
                <textElement textAlignment="Center" verticalAlignment="Top"/>
                <text><![CDATA[Débit

Crédit]]></text>
            </staticText>
            <staticText>
                <reportElement x="349" y="370" width="206" height="24" uuid="3f4d51a5-5e58-491f-8908-2ba4b7be6cc5"/>
                <box>
                    <topPen lineWidth="1.1"/>
                    <leftPen lineWidth="1.1"/>
                    <bottomPen lineWidth="1.1"/>
                    <rightPen lineWidth="1.1"/>
                </box>
                <textElement textAlignment="Left" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Montant à imputer au crédit :]]></text>
            </staticText>
            <textField>
                <reportElement x="440" y="350" width="107" height="20" uuid="cd2f74e5-fcde-4882-883c-bd44cb9d2d04"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{montant_n_c}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="237" y="372" width="80" height="20" uuid="17e6fdaa-1d0c-43b2-9996-e77ee8f96813"/>
                <textElement textAlignment="Right" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <textFieldExpression><![CDATA[$F{montant_in_d}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="115" y="370" width="234" height="24" uuid="a1c70d97-b426-45b2-9653-4b45a022f06a"/>
                <box>
                    <topPen lineWidth="1.1"/>
                    <leftPen lineWidth="1.1"/>
                    <bottomPen lineWidth="1.1"/>
                    <rightPen lineWidth="1.1"/>
                </box>
                <textElement verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Montant à imputer au débit :]]></text>
            </staticText>
            <textField>
                <reportElement x="452" y="370" width="68" height="24" uuid="b3573dd9-1e41-4abc-96d4-b2e79e4803f0"/>
                <textElement textAlignment="Right" verticalAlignment="Middle">
                    <font fontName="Arial" isBold="true"/>
                </textElement>
                <textFieldExpression><![CDATA[$F{montant_in_c}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="440" y="330" width="115" height="40" uuid="3304dc1e-57c9-48dc-be71-c82ea54864b1"/>
                <box>
                    <topPen lineWidth="1.0"/>
                    <leftPen lineWidth="1.0"/>
                    <bottomPen lineWidth="1.0"/>
                    <rightPen lineWidth="1.0"/>
                </box>
                <text><![CDATA[]]></text>
            </staticText>
            <staticText>
                <reportElement x="280" y="330" width="160" height="40" uuid="572073a8-9b79-4477-adaf-fd4fdeccc718"/>
                <box>
                    <topPen lineWidth="1.1"/>
                    <leftPen lineWidth="1.1"/>
                    <bottomPen lineWidth="1.1"/>
                    <rightPen lineWidth="1.1"/>
                </box>
                <text><![CDATA[]]></text>
            </staticText>
            <textField>
                <reportElement x="289" y="350" width="31" height="20" uuid="35891d75-ebe5-40dd-b371-8fea79e51faf"/>
                <textFieldExpression><![CDATA[$F{taux}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="349" y="350" width="81" height="20" uuid="2b9e5a28-2a12-4abf-9073-678308a013b2"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{mon_rsa_c}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="349" y="330" width="81" height="20" uuid="7d81b7fd-3df4-4181-9f31-d22aa31d7d4c"/>
                <textElement textAlignment="Right"/>
                <textFieldExpression><![CDATA[$F{mon_rsa_d}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="310" y="290" width="100" height="20" uuid="b76d0358-1a98-4949-b5fe-7ff43ae22165"/>
                <textElement textAlignment="Center">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Retenue à la source]]></text>
            </staticText>
            <staticText>
                <reportElement x="280" y="310" width="69" height="20" uuid="a65b3938-9930-4e93-8c28-fa1c769f1f3e"/>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Taux]]></text>
            </staticText>
            <staticText>
                <reportElement x="350" y="310" width="90" height="20" uuid="013cd360-4a75-482f-afd3-5690826fb640"/>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Montant]]></text>
            </staticText>
            <staticText>
                <reportElement x="-1" y="575" width="555" height="15" uuid="eebd1b04-c806-4208-89c2-14b37a6da029"/>
                <box>
                    <topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                </box>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[LISTE DES COMPTES INCLUS  DANS L'ARRETE]]></text>
            </staticText>
            <staticText>
                <reportElement x="-1" y="590" width="281" height="20" uuid="edf184bb-2c8c-4b86-8c64-1fb2b10ba6ca"/>
                <box>
                    <topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                </box>
                <textElement verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Compte]]></text>
            </staticText>
            <staticText>
                <reportElement x="280" y="590" width="274" height="20" uuid="da85b086-080f-4f5f-8964-92f34c43e680"/>
                <box>
                    <topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                </box>
                <textElement verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[Agence]]></text>
            </staticText>
            <staticText>
                <reportElement x="-1" y="610" width="555" height="20" uuid="b84e58a7-6a0a-4b27-ae65-83b68512ed78"/>
                <box>
                    <topPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <leftPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <bottomPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                    <rightPen lineWidth="1.1" lineStyle="Solid" lineColor="#000000"/>
                </box>
                <text><![CDATA[]]></text>
            </staticText>
            <textField>
                <reportElement x="0" y="612" width="181" height="16" uuid="0a669a8a-6f28-4068-9ee8-1baf3c65c108"/>
                <textElement verticalAlignment="Middle"/>
                <textFieldExpression><![CDATA[$F{num_compte}]]></textFieldExpression>
            </textField>
            <textField>
                <reportElement x="289" y="612" width="258" height="13" uuid="70b8b41a-6e8d-4e2c-85c9-7fdc659caf94"/>
                <textElement verticalAlignment="Middle"/>
                <textFieldExpression><![CDATA[$F{soc_name}]]></textFieldExpression>
            </textField>
            <staticText>
                <reportElement x="320" y="330" width="17" height="20" uuid="28b51819-6ea9-40c2-b195-481448624b28"/>
                <text><![CDATA[%]]></text>
            </staticText>
            <staticText>
                <reportElement x="321" y="350" width="17" height="20" uuid="06c37d05-d2ec-42fb-b06b-74a131ee080d"/>
                <text><![CDATA[%]]></text>
            </staticText>
            <staticText>
                <reportElement x="522" y="372" width="30" height="20" uuid="af668228-6179-4e8e-9b07-f0adf3209946"/>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[MAD]]></text>
            </staticText>
            <staticText>
                <reportElement x="318" y="372" width="29" height="20" uuid="a5a1f006-a9a8-4c92-99a7-6cc06942a898"/>
                <textElement textAlignment="Center" verticalAlignment="Middle">
                    <font isBold="true"/>
                </textElement>
                <text><![CDATA[MAD]]></text>
            </staticText>
            <textField>
                <reportElement x="394" y="57" width="131" height="22" uuid="4f8fc329-caa6-4e67-af52-cc3db67b4ccc"/>
                <textFieldExpression><![CDATA[$F{ville}]]></textFieldExpression>
            </textField>
        </band>
    </detail>
    <pageFooter>
        <band height="38" splitType="Stretch">
            <staticText>
                <reportElement x="0" y="5" width="549" height="15" uuid="024ad315-c294-4c23-acbb-f03f6725c003"/>
                <textElement>
                    <font fontName="Arial" size="9"/>
                </textElement>
                <text><![CDATA[Ce relevé vous est communiqué à titre indicatif. Pour toute information complémentaire, veuillez vous adresser à vos contacts habituels.]]></text>
            </staticText>
            <textField evaluationTime="Report">
                <reportElement x="528" y="24" width="40" height="14" uuid="1f394408-c79e-4ad9-8c62-b3020e173f8f"/>
                <textElement>
                    <font fontName="Arial" size="9" isBold="false"/>
                </textElement>
                <textFieldExpression><![CDATA[" " + $V{PAGE_NUMBER}]]></textFieldExpression>
            </textField>
            <line>
                <reportElement x="-11" y="20" width="572" height="1" uuid="5c24126d-31ba-4eb9-a910-57eb998f18f3"/>
                <graphicElement>
                    <pen lineWidth="2.0"/>
                </graphicElement>
            </line>
            <staticText>
                <reportElement x="-16" y="24" width="486" height="14" uuid="bc2513ab-98e1-48b3-9382-d455bc5ac3eb"/>
                <textElement textAlignment="Center">
                    <font fontName="Arial" size="7"/>
                </textElement>
                <text><![CDATA[SOCIETE GENERALE SA AU CAPITAL DE 1 066 714 367,50 EUR. SIEGE SOCIAL A PARIS, 29 BD HAUSMANN - 552.120.222 R.C.S. PARIS.]]></text>
            </staticText>
            <textField>
                <reportElement x="480" y="24" width="48" height="14" uuid="effad8d2-c98a-4423-a2a3-e4a34b41e306"/>
                <textElement textAlignment="Right">
                    <font fontName="Arial" size="9" isBold="false"/>
                </textElement>
                <textFieldExpression><![CDATA["Page "+$V{PAGE_NUMBER}+" /"]]></textFieldExpression>
            </textField>
        </band>
    </pageFooter>
</jasperReport>
////////////////////////////////////////
/*********************/

package com.sgma.cashpool.engineservice.controller;

//import com.sgma.cashpool.engineservice.entity.interest.InterestCalculationRow;
import com.sgma.cashpool.engineservice.entity.interest.InterestCalculationRow2;
import com.sgma.cashpool.engineservice.entity.interest.InterstTest;
import net.sf.jasperreports.engine.*;
import net.sf.jasperreports.engine.data.JRBeanCollectionDataSource;
import org.springframework.core.io.InputStreamResource;
import org.springframework.http.HttpHeaders;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
import java.io.File;
import java.io.InputStream;
import java.math.BigDecimal;
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.util.*;

@RestController
@RequestMapping("/api/reports")
public class ReportController {

    @GetMapping("/account-interest")
    public ResponseEntity<InputStreamResource> generateAccountInterestReport() {
        try {
            // Création d'exemples de données

            List<MyTableData> tableData = Arrays.asList(
                    new MyTableData(new BigDecimal("25833.07"),new BigDecimal("25833.07")),
                    new MyTableData(new BigDecimal("25833.07"),new BigDecimal("25833.07")),
                    new MyTableData(new BigDecimal("25833.07"),new BigDecimal("25833.07"))
                    );
            DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");

            List<InterestCalculationRow2> calculationRows = new ArrayList<>();
            List<InterstTest> interstTests = new ArrayList<>();
            InterstTest interstTest = new InterstTest();
            interstTest.setCompName("eeee");
            interstTest.setNomCompte("eeeedddddd");
            interstTests.add(interstTest);
            calculationRows.add(new InterestCalculationRow2("MAROC","CASABLANCA","2 RUE AL ABTAL"," , HAY ERRAHA","CASABLANCA","03340 - 30796 - 00000 - AIG - IS","OCP (N° de compte : )","EMAPHOS","OCP",
                    LocalDate.parse("01/06/2024", formatter), LocalDate.parse("30/06/2024", formatter),"MAD","022780000140002797376074","SGMBMAMC SOCIETE GENERALE MAROCAINE DE BANQUE",new BigDecimal(10),
                    new BigDecimal("140998.19"),new BigDecimal("25833.07"),new BigDecimal("126898.37") ,
                    new BigDecimal("23249.76") ,new BigDecimal("2583.31"),new BigDecimal("14099.82"),new BigDecimal("126898.37") ,new BigDecimal("126898.37"), interstTests));

            // Remplir les paramètres du rapport
            JRBeanCollectionDataSource dataSource = new JRBeanCollectionDataSource(calculationRows);
            JRBeanCollectionDataSource dataSource2 = new JRBeanCollectionDataSource(interstTests);
            Map<String, Object> parameters = new HashMap<>();
            calculationRows.forEach(interestCalculationRow2 -> {
                parameters.put("pay",interestCalculationRow2.getPay());
                parameters.put("ville", interestCalculationRow2.getVille());
                parameters.put("adr1", interestCalculationRow2.getAdr1());
                parameters.put("adr2", interestCalculationRow2.getAdr2());
                parameters.put("adr3", interestCalculationRow2.getAdr3());
                parameters.put("ref", interestCalculationRow2.getRef());
                parameters.put("rattach", interestCalculationRow2.getRattach());
                parameters.put("sub_name", interestCalculationRow2.getSub_name());
                parameters.put("pivot", interestCalculationRow2.getPivot());
                parameters.put("first_date", interestCalculationRow2.getFirst_date());
                parameters.put("last_date", interestCalculationRow2.getLast_date());
                parameters.put("devise", interestCalculationRow2.getDevise());
                parameters.put("taux", interestCalculationRow2.getTaux());
                parameters.put("montant_b_d", interestCalculationRow2.getMontant_b_d());
                parameters.put("montant_b_c", interestCalculationRow2.getMontant_b_c());
                parameters.put("montant_n_d", interestCalculationRow2.getMontant_n_d());
                parameters.put("montant_n_c", interestCalculationRow2.getMontant_n_c());
                parameters.put("mon_rsa_c", interestCalculationRow2.getMon_rsa_c());
                parameters.put("mon_rsa_d", interestCalculationRow2.getMon_rsa_d());
                parameters.put("montant_in_d", interestCalculationRow2.getMontant_in_d());
                parameters.put("montant_in_c", interestCalculationRow2.getMontant_in_c());
                interstTests.forEach(interstTest1 -> {
                    parameters.put("num_compte",interstTest1.getCompName());
                    parameters.put("soc_name",interstTest1.getNomCompte());
                });

            });

            // Passez le JRBeanCollectionDataSource des comptes comme un paramètre spécifique

            // Utiliser JREmptyDataSource pour remplir le rapport sans changer JRXML
            JRBeanCollectionDataSource tableDataSource = new JRBeanCollectionDataSource(tableData);
            parameters.put("TABLE_DATA", tableData);

            // Chargement du fichier Jasper
            InputStream jasperStream = this.getClass().getResourceAsStream("/IntertsIntraGroupe.jrxml");
            JasperReport jasperReport = JasperCompileManager.compileReport(jasperStream);
            JasperPrint jasperPrint = JasperFillManager.fillReport(jasperReport, parameters, dataSource);

            // Génération du fichier PDF
            ByteArrayOutputStream pdfOutputStream = new ByteArrayOutputStream();
            JasperExportManager.exportReportToPdfStream(jasperPrint, pdfOutputStream);
            ByteArrayInputStream bis = new ByteArrayInputStream(pdfOutputStream.toByteArray());

            // Retourner le fichier PDF en réponse HTTP
            HttpHeaders headers = new HttpHeaders();
            headers.add("Content-Disposition", "inline; filename=account-interest-report.pdf");
            // Chemin du fichier de destination
            // Créer le répertoire si nécessaire
            File outputDir = new File("C:/Users/JAZZARN/Documents/projets/backend/engine-service/src/main/resources/reports/");
            if (!outputDir.exists()) {
                outputDir.mkdirs();
            }

//            String outputFilePath = "C:/Users/JAZZARN/Documents/projets/backend/engine-service/src/main/resources/reports/EtatDetaileInteretIG.pdf";
//            JasperExportManager.exportReportToPdfFile(jasperPrint, outputFilePath);
            return ResponseEntity
                    .ok()
                    .headers(headers)
                    .contentType(MediaType.APPLICATION_PDF)
                    .body(new InputStreamResource(bis));

        } catch (Exception e) {
            e.printStackTrace();
            return ResponseEntity.status(500).build();
        }
    }
}
class MyTableData{
    private BigDecimal total_numbrs;
    private BigDecimal total_cap;
    public MyTableData(BigDecimal total_numbrs,BigDecimal total_cap){
        this.total_cap=total_cap;
        this.total_numbrs=total_numbrs;
    }
    public BigDecimal getTotal_numbrs(){return total_numbrs;}
    public BigDecimal getTotal_cap(){return total_cap;}
}
