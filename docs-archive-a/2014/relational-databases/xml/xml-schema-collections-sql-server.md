---
title: XML-Schemaauflistungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- xml_schema_namespace function
- XML schema collections [SQL Server], about XML schema collections
- metadata [SQL Server], XML schema collections
- queries [XML in SQL Server], XML schema collections
- schema collections [SQL Server]
- schemas [SQL Server], XML
- XML [SQL Server], schema collections
- XML schema collections [SQL Server]
- schema collections [SQL Server], about XML schema collections
ms.assetid: 659d41aa-ccec-4554-804a-722a96ef25c2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ee4757f1353278447ee55e97c8d4ba23aa2d649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619674"
---
# <a name="xml-schema-collections-sql-server"></a>XML-Schemaauflistungen (SQL Server)
  Wie im Thema [XML &#40;Transact-SQL&#41;](/sql/t-sql/xml/xml-transact-sql)beschrieben, bietet SQL Server systemeigene Speicherung von XML-Daten durch den- `xml` Datentyp. Optional können Sie XSD-Schemas einer Variablen oder einer Spalte vom `xml` Typ über eine XML-Schema Auflistung zuordnen. Die XML-Schemaauflistung speichert die importierten XML-Schemas und wird dann für folgende Zwecke verwendet:  
  
-   Überprüfen von XML-Instanzen  
  
-   Typisierung der in der Datenbank gespeicherten XML-Daten  
  
 Beachten Sie, dass die XML-Schemaauflistung wie eine Tabelle in der Datenbank eine Metadatenentität ist. Sie können sie erstellen, ändern und löschen. In einer [CREATE XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) -Anweisung angegebene Schemas werden automatisch in das neu erstellte XML-Schemaauflistungsobjekt importiert. Mit der [ALTER XML SCHEMA COLLECTION (Transact-SQL)](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) -Anweisung können Sie zusätzliche Schemas oder Schemakomponenten in ein in der Datenbank vorhandenes Auflistungsobjekt importieren.  
  
 Wie im Thema [Vergleichen von typisiertem XML mit nicht typisiertem XML](../xml/compare-typed-xml-to-untyped-xml.md) beschrieben wird, wird der XML-Code, der in einer Spalte oder in einer Variablen mit zugeordnetem Schema gespeichert ist, als **typisiertes** XML bezeichnet, weil das Schema die für die Instanzendaten benötigten Datentypinformationen bereitstellt. SQL Server verwendet diese Typinformationen für die Optimierung des Datenspeichers.  
  
 Die Abfrageverarbeitungs-Engine verwendet das Schema außerdem zur Typüberprüfung sowie zur Optimierung der Abfragen und zur Datenänderung.  
  
 Außerdem verwendet SQL Server die zugeordnete XML-Schema Auflistung im Fall von typisiertem `xml` , um die XML-Instanz zu validieren. Wenn die XML-Instanz dem Schema entspricht, lässt die Datenbank das Speichern der Instanz und ihrer Typinformation im System zu. Anderenfalls wird die Instanz abgelehnt.  
  
 Um ein in der Datenbank gespeichertes Schema abzurufen, können Sie die systeminterne Funktion XML_SCHEMA_NAMESPACE verwenden. Weitere Informationen finden Sie unter [Anzeigen einer gespeicherten XML-Schemaauflistung](../xml/view-a-stored-xml-schema-collection.md).  
  
 Die XML-Schemaauflistung können Sie auch verwenden, um XML-Variablen, -Parameter und -Spalten zu typisieren.  
  
##  <a name="ddl-for-managing-schema-collections"></a><a name="ddl"></a> DDL zum Verwalten von Schemaauflistungen  
 Sie können XML-Schemaauflistungen in der Datenbank erstellen und Variablen und Spalten des `xml`-Typs zuordnen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet die folgenden DDL-Anweisungen zum Verwalten von Schemaauflistungen:  
  
-   [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql) Importiert die Schemakomponenten in eine Datenbank.  
  
-   [ALTER XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-xml-schema-collection-transact-sql) Ändert die Schemakomponenten in einer vorhandenen XML-Schemaauflistung.  
  
-   [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) Löscht eine gesamte XML-Schemaauflistung und alle zugehörigen Komponenten.  
  
 Um eine XML-Schemaauflistung und die darin enthaltenen Schemas zu verwenden, müssen Sie zuerst mit der CREATE XML SCHEMA COLLECTION-Anweisung die Auflistung und die Schemas erstellen. Nach dem Erstellen der Schemaauflistung können Sie Variablen und Spalten vom Typ `xml` erstellen und diese der Schemaauflistung zuordnen. Beachten Sie, dass nach dem Erstellen der Schemaauflistung verschiedene Schemakomponenten in den Metadaten gespeichert werden. Mit der Anweisung ALTER XML SCHEMA COLLECTION können Sie zu vorhandenen Schemas außerdem weitere Komponenten oder zu vorhandenen Auflistungen neue Schemas hinzufügen.  
  
 Zum Löschen der Schemaauflistung verwenden Sie die DROP XML SCHEMA COLLECTION-Anweisung. Diese Anweisung löscht alle in der Auflistung enthaltenen Schemas und entfernt das Auflistungsobjekt. Beachten Sie, dass zum Löschen einer Schemaauflistung zuerst die unter [DROP XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-xml-schema-collection-transact-sql) beschriebenen Bedingungen erfüllt sein müssen.  
  
##  <a name="understanding-schema-components"></a><a name="components"></a> Grundlegendes zu Schemakomponenten  
 Wenn Sie die CREATE XML SCHEMA COLLECTION-Anweisung verwenden, werden verschiedene Schemakomponenten in die Datenbank importiert. Zu den Schemakomponenten gehören Schemaelemente, -attribute und -typdefinitionen. Wenn Sie die DROP XML SCHEMA COLLECTION-Anweisung verwenden, wird die komplette Schemaauflistung entfernt.  
  
 CREATE XML SCHEMA COLLECTION speichert die Schemakomponenten in verschiedenen Systemtabellen.  
  
 Angenommen, das folgende Schema liegt vor:  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            targetNamespace="uri:Cust_Orders2"  
            xmlns="uri:Cust_Orders2" >  
  <xsd:attribute name="SomeAttribute" type="xsd:int" />  
  <xsd:complexType name="SomeType" />  
  <xsd:complexType name="OrderType" >  
    <xsd:sequence>  
      <xsd:element name="OrderDate" type="xsd:date" />  
      <xsd:element name="RequiredDate" type="xsd:date" />  
      <xsd:element name="ShippedDate" type="xsd:date" />  
    </xsd:sequence>  
    <xsd:attribute name="OrderID" type="xsd:ID" />  
    <xsd:attribute name="CustomerID"  />  
    <xsd:attribute name="EmployeeID"  />  
  </xsd:complexType>  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order" type="OrderType"  
                     maxOccurs="unbounded" />  
       </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
      <xsd:attribute name="OrderIDList" type="xsd:IDREFS" />  
  </xsd:complexType>  
  <xsd:element name="Customer" type="CustomerType" />  
</xsd:schema>  
```  
  
 Das obige Schema zeigt die verschiedenen Attributtypen von Komponenten, die in der Datenbank gespeichert werden können. Hierzu zählen `SomeAttribute`, `SomeType`, `OrderType`, `CustomerType`, `Customer`, `Order`, `CustomerID`, `OrderID`, `OrderDate`, `RequiredDate`und `ShippedDate`.  
  
### <a name="component-categories"></a>Komponentenkategorien  
 Die in der Datenbank gespeicherten Schemakomponenten fallen in folgende Kategorien:  
  
-   ELEMENT  
  
-   ATTRIBUTE  
  
-   TYPE (für einfache oder komplexe Typen)  
  
-   ATTRIBUTEGROUP  
  
-   MODELGROUP  
  
 Beispiel:  
  
-   **SomeAttribute** ist eine ATTRIBUTE-Komponente.  
  
-   **SomeType**, **OrderType**und **CustomerType** sind TYPE-Komponenten.  
  
-   **Customer** ist eine ELEMENT-Komponente.  
  
 Wenn Sie ein Schema in die Datenbank importieren, wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht das Schema als solches gespeichert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert stattdessen die verschiedenen Einzelkomponenten. Das \<Schema>-Tag wird demnach nicht gespeichert, es werden nur die darin definierten Komponenten aufbewahrt. Nicht alle Schemaelemente werden erhalten. Wenn das \<Schema>-Tag Attribute enthält, die das Standardverhalten seiner Komponenten definieren, werden diese Attribute während des Importvorgangs in die darin enthaltenen Komponenten verschoben. Die folgende Tabelle stellt dies dar.  
  
|Attributname|Verhalten|  
|--------------------|--------------|  
|**attributeFormDefault**|Das **form** -Attribut, das für alle im Schema enthaltenen Attributdeklarationen angewendet wird, die dieses Attribut noch nicht enthalten. Der Wert wird auf den Wert des **attributeFormDefault** -Attributs festgelegt.|  
|**elementFormDefault**|Das **form** -Attribut, das für alle im Schema enthaltenen Elementdeklarationen angewendet wird, die dieses Attribut noch nicht enthalten. Der Wert wird auf den Wert des **elementFormDefault** -Attributs festgelegt.|  
|**blockDefault**|Das **block** -Attribut, das für alle Elementdeklarationen und Typdefinitionen angewendet wird, die dieses Attribut noch nicht enthalten. Der Wert wird auf den Wert des **blockDefault** -Attributs festgelegt.|  
|**finalDefault**|Das **final** -Attribut, das für alle Elementdeklarationen und Typdefinitionen angewendet wird, die dieses Attribut noch nicht enthalten. Der Wert wird auf den Wert des **finalDefault** -Attributs festgelegt.|  
|**targetNamespace**|Zum Zielnamespace gehörende Informationen zu den Komponenten werden in den Metadaten gespeichert.|  
  
##  <a name="permissions-on-an-xml-schema-collection"></a><a name="perms"></a> Berechtigungen für eine XML-Schemaauflistung  
 Sie müssen über die entsprechenden Berechtigungen verfügen, um die folgenden Aufgaben durchführen zu können:  
  
-   Erstellen/Laden der XML-Schemaauflistung  
  
-   Ändern der XML-Schemaauflistung  
  
-   Löschen der XML-Schemaauflistung  
  
-   Verwenden Sie die XML-Schema Auflistung, um `xml` Typspalten, Variablen und Parameter einzugeben, oder verwenden Sie Sie in Tabellen-oder Spalten Einschränkungen.  
  
 Das SQL Server-Sicherheitsmodell lässt die CONTROL-Berechtigung für jedes Objekt zu. Der Empfänger dieser Berechtigung erhält alle anderen Berechtigungen für das Objekt. Der Besitzer des Objekts verfügt ebenfalls über alle Berechtigungen für das Objekt.  
  
 Der Besitzer und der Empfänger der CONTROL-Berechtigung für ein Objekt können beliebige Berechtigungen für das Objekt erteilen. Ein Benutzer, der nicht der Besitzer ist und keine CONTROL-Berechtigung besitzt, kann dennoch Berechtigungen für ein Objekt erteilen, wenn WITH GRANT OPTION angegeben wurde. Angenommen, Benutzer A verfügt über WITH GRANT OPTION z. B. über REFERENCES-Berechtigung für eine XML-Schemaauflistung S, besitzt jedoch keine weiteren Berechtigungen für S. Benutzer A kann Benutzer B die REFERENCES-Berechtigung für Schemaauflistung S erteilen.  
  
 Das Sicherheitsmodell ermöglicht außerdem Berechtigungen zum Erstellen oder Verwenden von XML-Schemaauflistungen oder zum Übertragen des Besitzes von einem auf einen anderen Benutzer. In den folgenden Themen werden die Berechtigungen für XML-Schemaauflistungen beschrieben.  
  
-   [Erteilen von Berechtigungen für eine XML-Schemaauflistung](../xml/grant-permissions-on-an-xml-schema-collection.md)  
  
     Dieses Thema erläutert das Erteilen von Berechtigungen zum Erstellen von XML-Schemaauflistungen sowie das Erteilen von Berechtigungen für ein XML-Schemaauflistungsobjekt.  
  
-   [Aufheben der Berechtigungen für eine XML-Schemaauflistung](../xml/revoke-permissions-on-an-xml-schema-collection.md)  
  
     Dieses Thema erläutert das Aufheben von Berechtigungen zum Verhindern der Erstellung einer XML-Schemaauflistung sowie das Aufheben von Berechtigungen für ein XML-Schemaauflistungsobjekt.  
  
-   [Verweigern von Berechtigungen für eine XML-Schemaauflistung](../xml/deny-permissions-on-an-xml-schema-collection.md)  
  
     Dieses Thema erläutert das Verweigern von Berechtigungen zum Erstellen einer XML-Schemaauflistung sowie das Verweigern von Berechtigungen für ein XML-Schemaauflistungsobjekt.  
  
##  <a name="getting-information-about-xml-schemas-and-schema-collections"></a><a name="info"></a> Abrufen von Informationen zu XML-Schemas und -Schemaauflistungen  
 XML-Schemaauflistungen sind in der Katalogsicht sys.xml_schema_collections aufgeführt. Die XML-Schemaauflistung "sys" wird durch das System definiert. Sie enthält die vordefinierten Namespaces, die in allen benutzerdefinierten XML-Schemaauflistungen verwendet werden können, ohne dass sie explizit geladen werden müssen. Diese Auflistung enthält die Namespaces für xml, xs, xsi, fn und xdt. Zwei weitere Katalogsichten sind sys.xml_schema_namespaces, die alle Namespaces innerhalb jeder Schemaauflistung aufführt, und sys.xml_components, die alle XML-Schemakomponenten innerhalb jedes XML-Schemas aufführt.  
  
 Die integrierte Funktion **XML_SCHEMA_NAMESPACE**, Schema *Name, XmlSchemaCollectionName, Namespace-URI*, ergibt eine Instanz des- `xml` Datentyps. Diese Instanz enthält XML-Schemafragmente für Schemas, die in einer XML-Schemaauflistung enthalten sind, mit Ausnahme der vordefinierten XML-Schemas.  
  
 Es gibt folgende Möglichkeiten, um den Inhalt einer XML-Schemaauflistung aufzuführen:  
  
-   Schreiben Sie Transact-SQL-Abfragen zur jeweiligen Katalogsicht für XML-Schemaauflistungen.  
  
-   Verwenden Sie die integrierte Funktion **XML_SCHEMA_NAMESPACE()** . Sie können `xml` Datentyp Methoden auf die Ausgabe dieser Funktion anwenden. Allerdings können Sie dabei die zugrunde liegenden XML-Schemas nicht ändern.  
  
 Diese Möglichkeiten werden in den folgenden Beispielen veranschaulicht.  
  
### <a name="example-enumerate-the-xml-namespaces-in-an-xml-schema-collection"></a>Beispiel: Enumeration der XML-Namespaces in einer XML-Schemaauflistung  
 Verwenden Sie die folgende Abfrage für die XML-Schemaauflistung "myCollection":  
  
```  
SELECT XSN.name  
FROM    sys.xml_schema_collections XSC JOIN sys.xml_schema_namespaces XSN  
    ON (XSC.xml_collection_id = XSN.xml_collection_id)  
WHERE    XSC.name = 'myCollection'     
```  
  
### <a name="example-enumerate-the-contents-of-an-xml-schema-collection"></a>Beispiel: Enumeration des Inhalts einer XML-Schemaauflistung  
 Mit der folgenden Anweisung wird der Inhalt der XML-Schemaauflistung "myCollection" innerhalb des relationalen Schemas dbo aufgeführt.  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection')  
```  
  
 Einzelne XML-Schemas innerhalb der Auflistung können als `xml` Datentyp Instanzen abgerufen werden, indem der Ziel Namespace als drittes Argument für **XML_SCHEMA_NAMESPACE ()** angegeben wird. Dies wird im folgenden Beispiel gezeigt.  
  
### <a name="example-output-a-specified-schema-from-an-xml-schema-collection"></a>Beispiel: Ausgeben eines angegebenen Schemas für eine XML-Schemaauflistung  
 Mit der folgenden Anweisung wird das XML-Schema mit dem Zielnamespace <https://www.microsoft.com/books> aus der XML-Schemaauflistung „myCollection“ innerhalb des relationalen Schemas „dbo“ ausgegeben.  
  
```  
SELECT XML_SCHEMA_NAMESPACE (N'dbo', N'myCollection',   
N'https://www.microsoft.com/books')  
```  
  
### <a name="querying-xml-schemas"></a>Abfragen von XML-Schemas  
 Es gibt folgende Möglichkeiten, um XML-Schemas, die Sie in XML-Schemaauflistungen geladen haben, abzufragen:  
  
-   Schreiben Sie Transact-SQL-Abfragen zu Katalogsichten für XML-Schemaauflistungen.  
  
-   Erstellen Sie eine Tabelle, die eine `xml`-Datentypspalte enthält, um die XML-Schemas zu speichern, und laden Sie diese auch in das XML-Typsystem. Sie können dann diese XML-Spalte abfragen, indem Sie `xml`-Datentypmethoden verwenden. Für diese Spalte können Sie auch einen XML-Index erstellen. Allerdings muss die Anwendung für diese Vorgehensweise die Konsistenz zwischen den in der XML-Spalte gespeicherten XML-Schemas und dem XML-Typsystem beibehalten. Wenn Sie z. B. den XML-Schemanamespace aus dem XML-Typsystem löschen, müssen Sie ihn auch aus der Tabelle löschen, damit die Konsistenz beibehalten wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen einer gespeicherten XML-Schemaauflistung](../xml/view-a-stored-xml-schema-collection.md)   
 [Vorverarbeiten eines Schemas zum Zusammenführen eingeschlossener Schemas](../xml/preprocess-a-schema-to-merge-included-schemas.md)   
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](../xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
