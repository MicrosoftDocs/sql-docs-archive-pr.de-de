---
title: "Anfordern von URL-verweisen auf BLOB-Daten mithilfe von ' SQL: encode ' (SQLXML 4,0) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9f5edcfab4a9d7307327d97bc2099c78c666c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621426"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Anfordern von URL-Verweisen auf BLOB-Daten mit 'sql:encode' (SQLXML 4.0)
  Wenn in einem XSD-Schema mit Anmerkungen ein Attribut (oder Element) einer BLOB-Spalte in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist, werden die Daten im codierten Base-64-Format innerhalb von XML zurückgegeben.  
  
 Wenn ein Verweis auf die Daten (ein URI) zurückgegeben werden soll, der später zum Abrufen der BLOB-Daten in einem binären Format verwendet werden kann, geben Sie die `sql:encode`-Anmerkung an. Sie können `sql:encode` für ein Attribut oder Element des einfachen Typs angeben.  
  
 Geben Sie die `sql:encode`-Anmerkung an, um anzugeben, dass anstatt des Feldwerts eine URL zum Feld zurückgegeben werden soll. `sql:encode` verwendet den Primärschlüssel, um eine Singleton-Auswahl in der URL zu generieren. Der Primärschlüssel kann mithilfe der-Anmerkung angegeben werden `sql:key-fields` .  
  
 Der `sql:encode`-Anmerkung kann der Wert "url" oder "default" zugewiesen werden. Mit dem Wert "default" werden die Daten im codierten Base-64-Format zurückgegeben.  
  
 Die `sql:encode`Anmerkung kann nicht mit `sql:use-cdata` oder für die Attributtypen ID, IDREF, IDREFS, NMTOKEN und NMTOKENS verwendet werden. Sie kann auch nicht mit dem XSD-Attribut **Fixed** verwendet werden.  
  
> [!NOTE]  
>  BLOB-Spalten können nicht als Teil eines Schlüssels oder Fremdschlüssels verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Angeben von sql:encode zum Abrufen eines URL-Verweises auf BLOB-Daten  
 In diesem Beispiel gibt das `sql:encode` Zuordnungsschema für das **LargePhoto** -Attribut an, um den URI-Verweis auf ein bestimmtes Produktfoto abzurufen (anstatt die Binärdaten 64 im Base64-codierten Format abzurufen).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen sqlEncode.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen sqlEncodeT.xml im gleichen Verzeichnis, in dem Sie sqlEncode.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungschema (sqlEncode.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
