---
title: Beispiel-XSD-Schema mit Anmerkungen für XPath-Beispiele (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], annotated XSD schemas in queries
- annotated XSD schemas, samples
- annotated XSD schemas, queries
ms.assetid: fefa2cc8-2d3c-4336-aeae-ce063a3a8df2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c7065bed89d867dda3ecffc7d80f2f729832e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608495"
---
# <a name="sample-annotated-xsd-schema-for-xpath-examples-sqlxml-40"></a>Beispiel-XSD-Schema mit Anmerkungen für XPath-Beispiele (SQLXML 4.0)
  Die Beispiel-XPath-Abfragen in diesem Abschnitt beziehen sich auf ein Zuordnungsschema. Das Zuordnungsschema ist eine XML-Schemadatei (XSD) mit Anmerkungen. Weitere Informationen zum Mapping von Schemas finden [Sie unter Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).  
  
 Die folgenden Bedingungen müssen erfüllt sein, um XPath-Abfragen eines XSD-Schemas mit Anmerkungen auszuführen:  
  
-   Erstellen Sie eine Vorlage mit einer XPath-Abfrage. Geben Sie in der Vorlage das Zuordnungsschema an, anhand dessen die XPath-Abfrage ausgeführt werden soll. In diesem Fall muss das Zuordnungsschema im Verzeichnis gespeichert werden (oder in einem der Unterverzeichnisse, wobei dann ein relativer Pfad als Wert des `mapping-schema`-Attributs in der Vorlage angegeben wird), das der Vorlagendatei zugeordnet ist.  
  
-   Erstellen Sie eine Testanwendung, die SQLXML-Erweiterungen für ADO verwendet, um Abfragen auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 In allen Beispielen in diesem Abschnitt werden zur Veranschaulichung die XPath-Abfragen in einer Vorlage angegeben, die mithilfe von ADO ausgeführt wird. Daher müssen Sie die folgende Zuordnungsschemadatei verwenden: SampleSchema1.xml. Speichern Sie diese Datei in dem Verzeichnis, in dem die Vorlagen gespeichert sind.  
  
## <a name="sample-annotated-xsd-schema-sampleschema1xml"></a>Beispiel-XSD-Schema mit Anmerkungen (SampleSchema1.xml)  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustOrders"  
                        parent="Sales.Customer"  
                        parent-key="CustomerID"  
                        child="Sales.SalesOrderHeader"  
                        child-key="CustomerID" />  
      <sql:relationship name="OrderOrderDetail"  
                        parent="Sales.SalesOrderHeader"  
                        parent-key="SalesOrderID"  
                        child="Sales.SalesOrderDetail"  
                        child-key="SalesOrderID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders" />  
     </xsd:sequence>  
     <xsd:attribute name="CustomerID" type="xsd:ID"/>  
     <xsd:attribute name="TerritoryID"/>  
     <xsd:attribute name="AccountNumber"/>  
     <xsd:attribute name="CustomerType"/>  
     <xsd:attribute name="Orders" type="xsd:IDREFS" sql:prefix="Ord-"/>  
  </xsd:complexType>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="OrderType"/>  
  
  <xsd:complexType name="OrderType">  
     <xsd:sequence>  
        <xsd:element name="OrderDetail"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOrderDetail" />  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:ID" sql:prefix="Ord-"/>  
     <xsd:attribute name="SalesPersonID"/>  
     <xsd:attribute name="OrderDate"/>  
     <xsd:attribute name="DueDate"/>  
     <xsd:attribute name="ShipDate"/>  
  </xsd:complexType>  
  
  <xsd:element name="OrderDetail" sql:relation="Sales.SalesOrderDetail" type="OrderDetailType"/>  
  
  <xsd:complexType name="OrderDetailType">  
    <xsd:attribute name="ProductID" type="xsd:IDREF"/>  
    <xsd:attribute name="UnitPrice"/>  
    <xsd:attribute name="OrderQty"/>  
    <xsd:attribute name="UnitPriceDiscount"/>  
  </xsd:complexType>  
  
  <xsd:element name="UnitPriceDiscount" sql:relation="Sales.SalesOrderDetail" type="DiscountType"/>  
  
  <xsd:complexType name="DiscountType">  
    <xsd:simpleContent>  
       <xsd:extension base="xsd:string">  
          <xsd:anyAttribute namespace="##other" processContents="lax"/>  
       </xsd:extension>  
    </xsd:simpleContent>  
  </xsd:complexType>  
  
  <xsd:element name="Contact" sql:relation="Person.Contact" type="ContactType"/>  
  
  <xsd:complexType name="ContactType">  
    <xsd:attribute name="ContactID"/>  
    <xsd:attribute name="LastName"/>  
    <xsd:attribute name="FirstName"/>  
    <xsd:attribute name="Title"/>  
  </xsd:complexType>  
  
</xsd:schema>  
```  
  
  
