---
title: Client seitige XML-Formatierung (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619709"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a>Clientseitige XML-Formatierung (SQLXML 4.0)
  Dieses Thema enthält Informationen zur clientseitigen XML-Formatierung. Als clientseitige Formatierung wird die Formatierung von XML-Code auf der mittleren Ebene bezeichnet.  
  
> [!NOTE]  
>  Dieses Thema enthält zusätzliche Informationen zur clientseitigen Verwendung der FOR XML-Klausel und setzt voraus, dass Sie bereits mit der FOR XML-Klausel vertraut sind. Weitere Informationen zu for XML finden Sie unter [Erstellen von XML mithilfe von for XML](../../xml/for-xml-sql-server.md).  
  
 **Wichtig** Zur Verwendung der Client seitigen for XML-Funktionalität mit dem neuen- `xml` Datentyp sollten Clients immer den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11)-Datenanbieter anstelle des SQLOLEDB-Anbieters verwenden. SQLNCLI11 ist die neueste Version des SQLmServer-Anbieters und erkennt die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Datentypen vollständig. Das Verhalten für clientseitiges FOR XML mit dem SQLOLEDB-Anbieter behandelt `xml`-Datentypen als Zeichenfolgen.  
  
## <a name="formatting-xml-documents-on-the-client-side"></a>Clientseitige Formatierung von XML-Dokumenten  
 Wenn eine Clientanwendung die folgende Abfrage ausführt:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 Wird nur dieser Teil der Abfrage an den Server gesendet:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Der Server führt die Abfrage aus und gibt ein Rowset (das FirstName und lastnamecolumschlag enthält) an den Client zurück. Die mittlere Ebene wendet dann die FOR XML-Transformation auf das Rowset an und gibt die XML-Formatierung an den Client zurück.  
  
 Entsprechend gibt der Server beim Ausführen einer XPath-Abfrage das Rowset an den Client zurück und die FOR XML EXPLICIT-Transformation wird auf das Rowset auf dem Client angewendet. Somit wird die gewünschte XML-Formatierung erzeugt.  
  
 Die folgende Tabelle zeigt die Modi, die Sie mit clientseitigem FOR XML angeben können.  
  
|Clientseitiger FOR XML-Modus|Comment|  
|-------------------------------|-------------|  
|RAW|Erzeugt bei Festlegung in clientseitigem oder serverseitigem FOR XML identische Ergebnisse.|  
|NESTED|Ist dem serverseitigen FOR XML AUTO-Modus ähnlich.|  
|EXPLICIT|Ist dem serverseitigen FOR XML EXPLICIT-Modus ähnlich.|  
  
> [!NOTE]  
>  Wenn Sie den AUTO-Modus angeben und clientseitige XML-Formatierung anfordern, wird die gesamte Abfrage an den Server gesendet, d. h. die XML-Formatierung findet auf dem Server statt. Dies ist praktisch, aber beachten Sie, dass der NESTED-Modus Basistabellennamen als Elementnamen in dem generierten XML-Dokument zurückgibt. Einige der von Ihnen erstellten Anwendungen erfordern möglicherweise Basistabellennamen. Angenommen, Sie führen eine gespeicherte Prozedur aus, laden die Ergebnisdaten in ein Dataset (im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework) und erstellen dann später ein DiffGram, um die Daten in den Tabellen zu aktualisieren. In einem solchen Fall benötigen Sie die Basistabelleninformationen und müssen den NESTED-Modus verwenden.  
  
## <a name="benefits-of-client-side-xml-formatting"></a>Vorteile der clientseitigen XML-Formatierung  
 Im Folgenden werden einige Vorteile der Formatierung von XML auf dem Client aufgezeigt.  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a>Wenn auf dem Server gespeicherte Prozeduren gespeichert sind, die ein einzelnes Rowset zurückgeben, können Sie zur Erstellung des XML-Code die clientseitige FOR XML-Transformation anfordern.  
 Nehmen Sie die folgende gespeicherte Prozedur als Beispiel: Diese Prozedur gibt den Vor- und Nachnamen der Mitarbeiter aus der Person.Contact-Tabelle in der AdventureWorks-Datenbank zurück:  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 Die folgende XML-Beispielvorlage führt die gespeicherte Prozedur aus. Die FOR XML-Klausel wird nach dem Namen der gespeicherten Prozedur festgelegt.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Da das **Client seitige XML-** Attribut in der Vorlage auf 1 (true) festgelegt ist, wird die gespeicherte Prozedur auf dem Server ausgeführt, und das zweispaltige Rowset, das vom Server zurückgegeben wird, wird auf der mittleren Ebene in XML transformiert und an den Client zurückgegeben. (Hier wird nur ein Teilergebnis angezeigt.)  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  Wenn Sie den SQLXMLOLEDB-Anbieter oder verwaltete SQLXML-Klassen verwenden, können Sie mithilfe der `ClientSideXml`-Eigenschaft clientseitige XML-Formatierung anfordern.  
  
### <a name="the-workload-is-more-balanced"></a>Die Arbeitsauslastung wird besser verteilt.  
 Da der Client die XML-Formatierung ausführt, wird die Arbeitsauslastung zwischen Server und Client besser verteilt. Der Server verfügt über mehr Kapazität für andere Aufgaben.  
  
## <a name="supporting-client-side-xml-formatting"></a>Unterstützung clientseitiger XML-Formatierung  
 Zur Unterstützung der clientseitigen XML-Formatierung bietet SQLXML:  
  
-   SQLXMLOLEDB-Anbieter  
  
-   SQLXML, verwaltete Klassen  
  
-   Verbesserte Unterstützung für XML-Vorlagen  
  
-   SqlXmlCommand. ClientSideXML (Eigenschaft)  
  
     Sie können die clientseitige Formatierung festlegen, indem Sie diese Eigenschaft der verwalteten SQLXML-Klassen auf true festlegen.  
  
## <a name="enhanced-xml-template-support"></a>Erweiterte XML-Vorlagen Unterstützung  
 Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde die XML-Vorlage in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] durch das Hinzufügen des **Client seitigen XML-** Attributs erweitert. Wenn dieses Attribut auf true festgelegt wird, wird der XML-Code auf dem Client formatiert. Beachten Sie, dass dieses Vorlagen Attribut in der Funktionalität mit der anbieterspezifischen SQLXMLOLEDB-Eigenschaft "ClientSideXML" identisch ist.  
  
> [!NOTE]  
>  Wenn Sie in einer ADO-Anwendung, die den SQLXMLOLEDB-Anbieter verwendet, eine XML-Vorlage ausführen und sowohl das **Client-Side-XML-** Attribut in der Vorlage als auch die ClientSideXML-Eigenschaft des Anbieters angeben, hat der in der Vorlage angegebene Wert Vorrang.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Architektur der Client seitigen und Server seitigen XML-Formatierung &#40;SQLXML 4,0&#41;](server-side-xml-formatting-sqlxml-4-0.md)   
 [Für XML-&#40;SQL Server&#41;](../../xml/for-xml-sql-server.md)   
 [Informationen zu den XML-Sicherheitsüberlegungen &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [XML-Datentyp Unterstützung in SQLXML 4,0](../xml-data-type-support-in-sqlxml-4-0.md)   
 [Verwaltete SQLXML-Klassen](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Client seitige und Server seitige XML-Formatierung &#40;SQLXML 4,0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md)   
 [SqlXmlCommand-Objekt &#40;verwalteten SQLXML-Klassen&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [XML-Daten &#40;SQL Server&#41;](../../xml/xml-data-sql-server.md)  
  
  
