---
title: "Filtern von Werten mit ' SQL: limit-field ' und ' SQL: limit-value ' (SQLXML 4,0) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7886a9a6f51c76ed693576ca6f4659f4051d1f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725354"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a>Filtern von Werten mit 'sql:limit-field' und 'sql:limit-value' (SQLXML 4.0)
  Sie können Zeilen, die von einer Datenbankabfrage zurückgegeben werden, mit einem Grenzwert beschränken. Mithilfe der `sql:limit-field`- und der `sql:limit-value`-Anmerkung können Sie die Datenbankspalte, die die Grenzwerte enthält, identifizieren und einen bestimmten Grenzwert angeben, der zum Filtern der zurückgegebenen Daten verwendet werden soll.  
  
 Mithilfe der `sql:limit-field`-Anmerkung können Sie eine Spalte identifizieren, die einen Grenzwert enthält. Dies ist für alle zugeordneten Elemente oder Attribute zulässig.  
  
 Die-Anmerkung `sql:limit-value` wird verwendet, um den begrenzten Wert in der Spalte anzugeben, die in der-Anmerkung angegeben wird `sql:limit-field` . Die `sql:limit-value`-Anmerkung ist optional. Wenn `sql:limit-value` nicht angegeben wird, wird ein NULL-Wert angenommen.  
  
> [!NOTE]  
>  Bei Verwendung einer `sql:limit-field`-Anmerkung, bei der die zugeordnete SQL-Spalte eine Spalte vom Typ `real` ist, konvertiert SQLXML 4.0 die `sql:limit-value`-Anmerkung wie in XML-Schemas angegeben in einen angegebenen `nvarchar`-Wert. Hierzu müssen Dezimalgrenzwerte mithilfe der vollständigen wissenschaftlichen Schreibweise angegeben werden. Weitere Informationen finden Sie im Folgenden unter Beispiel B.  
  
## <a name="examples"></a>Beispiele  
 Um mithilfe dieser Daten funktionstüchtige Beispiele zu erstellen, muss Folgendes installiert sein:  
  
-   Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   MDAC 2.6 oder höher  
  
 In diesen Beispielen werden mithilfe der Vorlagen XPath-Abfragen für das XSD-Zuordnungsschema angegeben.  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a>A. Beschränken der zurückgegebenen Kundenadressen auf einen bestimmten Adresstyp  
 In diesem Beispiel enthält eine Datenbank zwei Tabellen:  
  
-   Customer (CustomerID, CompanyName)  
  
-   Addresses (CustomerID, AddressType, StreetAddress)  
  
 Ein Kunde kann eine Liefer- und/oder eine Rechnungsadresse haben. Die AddressType-Spaltenwerte sind Shipping (Lieferadresse) und Billing (Rechnungsadresse).  
  
 Dies ist das Zuordnungs Schema, in dem das **ShipTo** -Schema Attribut der Spalte "StreetAddress" in der Beziehung "Adressen" zugeordnet wird. Die Werte, die für dieses Attribut zurückgegeben werden, sind nur durch Angabe der `sql:limit-field` -und-Anmerkungen auf das Versenden von Adressen beschränkt `sql:limit-value` . Ebenso gibt das Attribut " **BillTo** Schema" nur die Abrechnungsadresse eines Kunden zurück.  
  
 Das ist das Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Erstellen Sie zwei Tabellen in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  Fügen Sie die Beispieldaten hinzu:  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constituci??n 2222 M??xico D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen LimitFieldValue.xml.  
  
4.  Erstellen Sie die folgende Vorlage (LimitFieldValueT.xml), und speichern Sie sie dort, wo Sie im vorherigen Schritt auch das Schema (LimitFieldValue.xml) gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (LimitFieldValue.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constituci??n 2222 M??xico D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a>B. Beschränken von Ergebnissen anhand eines Rabattwerts vom Datentyp "real"  
 In diesem Beispiel enthält eine Datenbank zwei Tabellen:  
  
-   Orders (OrderID)  
  
-   OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)  
  
 Dies ist das Zuordnungs Schema, in dem das **OrderID** -Attribut in den Bestelldetails der OrderID-Spalte in der Orders-Beziehung zugeordnet wird. Die Werte, die für dieses Attribut zurückgegeben werden, sind auf die Werte beschränkt, die den Wert 0000000e e-001 (0,2) aufweisen, wie für das **Discount** -Attribut mithilfe der `sql:limit-field` -und-Anmerkungen angegeben `sql:limit-value` .  
  
 Das ist das Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Erstellen Sie zwei Tabellen in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  Fügen Sie die Beispieldaten hinzu:  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  Speichern Sie das Schema (LimitFieldValue.xml) in einem Verzeichnis.  
  
4.  Erstellen Sie das folgende Testskript (TestQuery.vbs), geben Sie anstelle von MyServer den Namen des SQL Server-Computers ein, und speichern Sie das Skript in dem Verzeichnis, in dem Sie im vorherigen Schritt das Schema gespeichert haben:  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  Führen Sie die Datei TestQuery.vbs aus, indem Sie in Windows Explorer auf die Datei klicken.  
  
     Dies ist das Ergebnis:  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [float und Real &#40;Transact-SQL-&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)   
 [nchar und nvarchar &#40;Transact-SQL-&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)   
 [Installieren von SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [Verwenden von XSD-Schemas mit Anmerkungen in Abfragen &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  
