---
title: 'Beispiel: Angeben der HIDE-Direktive | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- HIDE directive
ms.assetid: 87504d87-1cbd-412a-9041-47884b6efcec
author: rothja
ms.author: jroth
ms.openlocfilehash: 423ee36f679467c07a604b9754172f6e261971b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621394"
---
# <a name="example-specifying-the-hide-directive"></a>Beispiel: Angeben der HIDE-Direktive
  In diesem Beispiel wird die Verwendung der **HIDE** -Direktive veranschaulicht. Diese Direktive erweist sich als hilfreich, wenn die Abfrage ein Attribut zum Sortieren der Zeilen in der Universaltabelle zurückgeben soll, das Attribut jedoch nicht im endgültigen XML-Dokument enthalten sein soll.  
  
 Diese Abfrage konstruiert diese XML-Ausgabe:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
           <Summary> element from XML stored in CatalogDescription column  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Diese Abfrage generiert die gewünschte XML-Ausgabe. Die Abfrage identifiziert zwei Spaltengruppen, deren Spaltennamen die Tagwerte 1 und 2 aufweisen.  
  
 Diese Abfrage verwendet die [query()-Methode (xml-Datentyp)](/sql/t-sql/xml/query-method-xml-data-type) vom Datentyp **xml** , um die CatalogDescription-Spalte vom Typ **xml** abzufragen und daraus die Zusammenfassungsbeschreibung abzurufen. Die Abfrage verwendet auch die [value()-Methode (xml-Datentyp)](/sql/t-sql/xml/value-method-xml-data-type) vom Datentyp **xml** , um den ProductModelID-Wert aus der CatalogDescription-Spalte abzurufen. Dieser Wert wird benötigt, um die Rowsets des Ergebnisses zu sortieren, ist im XML-Ergebnis jedoch nicht erforderlich. Deshalb beinhaltet der Spaltenname `[Summary!2!ProductModelID!HIDE]`die **HIDE** -Direktive. Wenn diese Spalte nicht in der SELECT-Anweisung enthalten ist, müssen Sie das Rowset nach `[ProductModel!1!ProdModelID]` und `[Summary!2!SummaryDescription]` vom Datentyp **xml** sortieren und können die Spalte vom Typ **xml** in ORDER BY nicht verwenden. Daher wird die zusätzliche Spalte `[Summary!2!ProductModelID!HIDE]` hinzugefügt und in der ORDER BY-Klausel angegeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID     as [ProductModel!1!ProdModelID],  
        Name               as [ProductModel!1!Name],  
        NULL               as [Summary!2!ProductModelID!hide],  
        NULL               as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
        CatalogDescription.value('  
         declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       (/PD:ProductDescription/@ProductModelID)[1]', 'int'),  
        CatalogDescription.query('  
         declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /pd:ProductDescription/pd:Summary')  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],[Summary!2!ProductModelID!hide]  
FOR XML EXPLICIT  
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription" xmlns="">  
        <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike. Performance-enhancing options include the innovative HL Frame, super-smooth front suspension, and traction for all terrain. </p1:p>  
      </pd:Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
