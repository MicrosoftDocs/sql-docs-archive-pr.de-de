---
title: 'SQL: limit-field und SQL: limit-value (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: 402c21cf-9566-463f-a928-f94270c11db3
author: rothja
ms.author: jroth
ms.openlocfilehash: a6d0383aece7a2bafa5d21b76d0c4da9cb057984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617884"
---
# <a name="sqllimit-field-and-sqllimit-value-sqlxml-40"></a>'sql:limit-field' und 'sql:limit-value' (SQLXML 4.0)
  Beim XML-Massenladen werden `sql:limit-field`- und `sql:limit-value`-Anmerkungen nach der jeweiligen Definition verarbeitet. Weitere Informationen finden Sie unter [Filtern von Werten mithilfe von SQL: limit-field und SQL: limit-value &#40;SQLXML 4,0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md).  
  
 Nehmen Sie z. B. an, dass eine Datenbank die folgenden Tabellen enthält:  
  
-   Customer (CustomerID, CompanyName)  
  
-   Addresses (CustomerID, StreetAddress, AddressType)  
  
 Ein Kunde kann viele Adressen haben, und jede Adresse hat einen verknüpften Adresstyp (z. B. eine Versandadresse oder Rechnungsadresse).  
  
 Betrachten Sie jetzt die im folgenden XSD-Schema mit Anmerkungen angegebene XML-Sicht dieser Tabellen.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Address"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
        <xsd:attribute name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
        <xsd:attribute name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Address"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Nach Empfang dieses Schemas und der XML-Daten fügt XML-Massenladen den Wert, der für das BillTo-Attribut angegeben ist, in die StreetAddress-Spalte der CustAddress-Tabelle zusammen mit dem "billing"-Wert für die AddressType-Spalte ein.  
  
 Entsprechend fügt XML-Massenladen den Wert, der für das ShipTo-Attribut angegeben ist, in die StreetAddress-Spalte zusammen mit dem "shipping"-Wert für die AddressType-Spalte ein.  
  
### <a name="to-test-a-working-sample"></a>So testen Sie ein funktionstüchtiges Beispiel  
  
1.  Speichern Sie das in diesem Beispiel bereitgestellte Schema unter dem Dateinamen SampleSchema.xml.  
  
2.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    CREATE TABLE Customer(  
                     CustomerID     int         PRIMARY KEY,  
                     CompanyName    varchar(20) NOT NULL)  
    GO  
    CREATE TABLE Address(  
                      CustomerID     int        FOREIGN KEY REFERENCES   
                                                 Customer(CustomerID),   
                      StreetAddress  varchar(50),  
                      AddressType    varchar(10))  
    GO  
    ```  
  
3.  Speichern Sie die folgenden Beispieldaten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <Customer CustomerID="1111" CompanyName="Sean Chai" City="NY"   
                 BillTo="111 Maple (Billing) "   
                 ShipTo="111 Maple (Shipping)" />  
    <Customer CustomerID="1112" CompanyName="Dont Know" City="LA"   
                 BillTo="222 Spruce (Billing)"   
                 ShipTo="222 Spruce (Shipping)" />  
    ```  
  
4.  Speichern Sie dieses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition-Beispiel (VBScript) unter dem Dateinamen Sample.vbs, und führen Sie es aus, um das XML-Massenladen auszuführen:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.XMLFragment = True  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="CompanyName" />  
    <AttributeType name="BillTo" />  
    <AttributeType name="ShipTo" />  
  
    <attribute type="CustomerID" />  
    <attribute type="CompanyName" />  
    <attribute type="BillTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="billing"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                        key="CustomerID"  
                        key-relation="Customer"  
                        foreign-relation="Address"  
                        foreign-key="CustomerID" />  
    </attribute>  
    <attribute type="ShipTo"   
                sql:limit-field="AddressType"  
                sql:limit-value="shipping"  
                sql:field="StreetAddress"  
                sql:relation="Address" >  
                <sql:relationship   
                     key="CustomerID"  
                     key-relation="Customer"  
                     foreign-relation="Address"  
                     foreign-key="CustomerID" />  
    </attribute>  
</ElementType>  
</Schema>  
```  
  
  
