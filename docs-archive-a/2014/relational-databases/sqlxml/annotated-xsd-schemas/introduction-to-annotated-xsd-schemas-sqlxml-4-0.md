---
title: Einführung in XSD-Schemas mit Anmerkungen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: rothja
ms.author: jroth
ms.openlocfilehash: b91be71569daa9e5bf4143be9f652617ba7c5b01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619720"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Einführung in XSD-Schemas mit Anmerkungen (SQLXML 4.0)
  Sie können mit der XML-Schemadefinitionssprache (XSD) XML-Sichten von relationalen Daten erstellen. Diese Sichten können dann mit XPath (XML Path)-Abfragen abgefragt werden. Dieser Vorgang gleicht prinzipiell dem Erstellen von Sichten mit CREATE VIEW-Anweisungen und dem Definieren von SQL-Abfragen für diese Sichten.  
  
 Ein XML-Schema beschreibt die Struktur eines XML-Dokuments und beschreibt außerdem die verschiedenen Einschränkungen der Daten im Dokument. Wenn XQuery-Abfragen mit dem XSD-Schema angegeben werden, wird die Struktur des resultierenden XML-Dokuments durch das Schema bestimmt, mit dem die Abfrage ausgeführt wird.  
  
 In einem XSD-Schema **\<xsd:schema>** umschließt das-Element das gesamte Schema; alle Element Deklarationen müssen im- **\<xsd:schema>** Element enthalten sein. Sie können Attribute beschreiben, die den Namespace definieren, in dem sich das Schema befindet, und die Namespaces, die im Schema als Eigenschaften des Elements verwendet werden **\<xsd:schema>** .  
  
 Ein gültiges XSD-Schema muss das-Element enthalten, das **\<xsd:schema>** wie folgt definiert ist:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 Das- **\<xsd:schema>** Element wird von der XML-Schema-Namespace Spezifikation unter abgeleitet http://www.w3.org/2001/XMLSchema .  
  
## <a name="annotations-to-the-xsd-schema"></a>Anmerkungen zum XSD-Schema  
 Sie können ein XSD-Schema mit Anmerkungen angeben, welche die Zuordnung zu einer Datenbank beschreiben, die Datenbank abfragen und die Ergebnisse in Form eines XML-Dokuments zurückgeben. Anmerkungen werden bereitgestellt, um ein XSD-Schema Datenbanktabellen und -spalten zuzuordnen. XPath-Abfragen können für die XML-Sicht, die durch das XSD-Schema erstellt wird, angegeben werden, um die Datenbank abzufragen und die Ergebnisse als XML-Dokument zu erhalten.  
  
> [!NOTE]  
>  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt die XSD-Schemasprache die Anmerkungen, die in der XDR-Schemasprache (XML-Data Reduced) mit Anmerkungen in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] eingeführt wurden. XDR-Anmerkungen sind in SQLXML 4.0 veraltet.  
  
 Im Kontext relationaler Datenbanken ist es nützlich, das beliebige XSD-Schema einem relationalen Datenspeicher zuzuordnen. Dies lässt sich beispielsweise erreichen, indem das XSD-Schema mit Anmerkungen versehen wird. Ein XSD-Schema mit Anmerkungen wird als Zuordnungsschema *mapping schema*bezeichnet, das Informationen dazu bereitstellt, wie XML-Daten dem relationalen Speicher zugeordnet werden. Ein Zuordnungsschema ist im Grunde eine XML-Sicht der relationalen Daten. Diese Zuordnungen können verwendet werden, um relationale Daten als XML-Dokument abzurufen.  
  
## <a name="namespace-for-annotations"></a>Namespace für Anmerkungen  
 In einem XSD-Schema werden Anmerkungen mithilfe des Namespace **urn: Schemas-Microsoft-com: Mapping-Schema**angegeben. Wie im folgenden Beispiel gezeigt, ist die einfachste Möglichkeit, den Namespace anzugeben, im- **\<xsd:schema>** Tag anzugeben.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Es kann ein beliebiges Namespacepräfix verwendet werden. In dieser Dokumentation wird das **SQL** -Präfix verwendet, um den Namespace der Anmerkung anzugeben und Anmerkungen in diesem Namespace von denjenigen in anderen Namespaces zu unterscheiden.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Beispiel eines XSD-Schemas mit Anmerkungen  
 Im folgenden Beispiel besteht das XSD-Schema aus einem- **\<Person.Contact>** Element. Das- **\<Employee>** Element verfügt über ein **ContactID** -Attribut und untergeordnete **\<FirstName>** - **\<LastName>** Elemente:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Diesem XSD-Schema werden Anmerkungen hinzugefügt, um die darin enthaltenen Elemente und Attribute den entsprechenden Datenbanktabellen und –spalten zuzuordnen.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Im Zuordnungs Schema wird das- **\<Contact>** Element mithilfe der-Anmerkung der Person. Contact-Tabelle in der AdventureWorks-Beispieldatenbank zugeordnet `sql:relation` . Die Attribute ConID, FName und LName werden mithilfe der `sql:field`-Anmerkungen den Spalten ContactID, FirstName und LastName in der Person.Contact-Tabelle zugeordnet.  
  
 Dieses XSD-Schema mit Anmerkungen stellt die XML-Sicht der relationalen Daten bereit. Diese XML-Sicht kann mit der XPath-Sprache abgefragt werden. Xpath-Abfragen geben als Ergebnis ein XML-Dokument zurück statt eines Rowsets, das von SQL-Abfragen zurückgegeben wird.  
  
> [!NOTE]  
>  Ob im Zuordnungsschema bei relationalen Werten, z. B. Tabellenname und Spaltenname, zwischen Groß-und Kleinschreibung unterschieden wird, hängt davon ab, ob in den Sortiereinstellungen auf dem SQL Server die Groß-/Kleinschreibung beachtet wird. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Weitere Ressourcen  
 Weitere Informationen zu XSD (XML Schema Definition Language), XPath (XML Path Language) und XSLT (Extensible Stylesheet Language Transformations) finden Sie auf den folgenden Websites:  
  
-   XML Schema Part 0: Primer, W3C-Empfehlung (http://www.w3.org/TR/xmlschema-0/)  
  
-   XML-Schema Teil 1: Strukturen, W3C-Empfehlung (http://www.w3.org/TR/xmlschema-1/)  
  
-   XML Schema Part 2: Datatypes, W3C-Empfehlung (http://www.w3.org/TR/xmlschema-2/)  
  
-   XML Path Language (XPath) (http://www.w3.org/TR/xpath)  
  
-   XSL-Transformationen (XSLT) (http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überlegungen zur Schema Sicherheit mit Anmerkungen &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [XDR-Schemas mit Anmerkungen &#40;in SQLXML 4,0 als veraltet markiert&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
