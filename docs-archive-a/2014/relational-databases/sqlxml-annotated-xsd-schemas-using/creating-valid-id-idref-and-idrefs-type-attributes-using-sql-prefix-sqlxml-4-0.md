---
title: "Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mit ' SQL: Prefix ' (SQLXML 4,0) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9e63bebd0cebbfeed75ea5cbe2ea62683234fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617902"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a>Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mit 'sql:prefix' (SQLXML 4.0)
  Für ein Attribut kann der ID-Attributtyp angegeben werden. Attribute vom Typ IDREF oder IDRES können dann verwendet werden, um auf das ID-Attribut zu verweisen. Auf diese Weise werden Links zwischen Dokumenten gebildet.  
  
 ID, IDREF und IDREFS entsprechen, abgesehen von wenigen Unterschieden, Primärschlüssel/Fremdschlüssel-Beziehungen in der Datenbank. In einem XML-Dokument müssen die Werte von ID-Typattributen eindeutig sein. Wenn **CustomerID** -und **OrderID** -Attribute als ID-Typ in einem XML-Dokument angegeben werden, müssen diese Werte unterschiedlich sein. In einer Datenbank können die Spalten CustomerID und SalesOrderID allerdings die gleichen Werte haben. (Zum Beispiel sind die Einträge CustomerID = 1 und OrderID = 1 in der Datenbank gültig).  
  
 Für die Gültigkeit der Attribute ID, IDREF und IDREFS gelten folgende Voraussetzungen:  
  
-   Der Wert von ID muss innerhalb des XML-Dokuments eindeutig sein.  
  
-   Die ID-Werte, auf die jeweils in IDREF und IDREFS verwiesen wird, müssen im XML-Dokument enthalten sein.  
  
-   Der Wert eines Attributs vom Typ ID, IDREF und IDREFS muss ein benanntes Token sein. (Beispielsweise kann der ganzzahlige Wert 101 kein ID-Wert sein.)  
  
-   Die Attribute vom Typ ID, IDREF und IDREFS können keinen Spalten vom Typ `text`, `ntext` oder `image` bzw. einem anderen binären Datentyp (z. B. `timestamp`) zugeordnet werden.  
  
 Enthält ein XML-Dokument mehrere IDs, geben Sie die `sql:prefix`-Anmerkung an, um eindeutige Werte zu gewährleisten.  
  
 Beachten Sie, dass die `sql:prefix`-Anmerkung nicht mit dem XSD-Attribut fixed verwendet werden kann.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-id-and-idrefs-types"></a>A. Angeben von ID- und IDREFS-Typen  
 Im folgenden Schema besteht das-Element aus dem untergeordneten- **\<Customer>** **\<Order>** Element. Das-Element **\<Order>** verfügt auch über ein untergeordnetes-Element, das- **\<OrderDetail>** Element.  
  
 Das **OrderIDList** -Attribut von **\<Customer>** ist ein Attribut vom Typ IDREFS, das auf das **OrderID** -Attribut des- **\<Order>** Elements verweist.  
  
```  
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
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen sqlPrefix.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen sqlPrefixT.xml im gleichen Verzeichnis wie sqlPrefix.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (sqlPrefix.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert ist. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Teilergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
