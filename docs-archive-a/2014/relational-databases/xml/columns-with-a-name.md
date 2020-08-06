---
title: Spalten mit Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
author: rothja
ms.author: jroth
ms.openlocfilehash: 32cfe617b80ed216374249961b85eae401011a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696529"
---
# <a name="columns-with-a-name"></a>Spalten mit Namen
  Im Folgenden werden die spezifischen Bedingungen aufgeführt, unter denen dem XML-Ergebnis mit Unterscheidung nach Groß-/Kleinschreibung Rowsetspalten mit Namen zugeordnet werden:  
  
-   Der Spaltenname beginnt mit einem At-Zeichen (\@).  
  
-   Der Spaltenname beginnt nicht mit einem At-Zeichen (\@).  
  
-   Der Spaltenname beginnt nicht mit einem At-Zeichen (\@) und enthält einen Schrägstrich (/).  
  
-   Mehrere Spalten verwenden dasselbe Präfix.  
  
-   Eine Spalte hat einen unterschiedlichen Namen.  
  
## <a name="column-name-starts-with-an-at-sign-"></a>Spaltenname beginnt mit einem At-Zeichen (\@)  
 Wenn der Spaltenname mit einem @-Zeichen ( \@ ) beginnt und keinen Schrägstrich (/) enthält, wird ein Attribut des <`row`> Elements erstellt, das über den entsprechenden Spaltenwert verfügt. Die folgende Abfrage gibt beispielsweise ein Rowset mit zwei Spalten (\@PmId, Name) zurück. Im resultierenden XML-Code wird dem entsprechenden <`row`>-Element ein **PmId**-Attribut hinzugefügt und diesem der Wert ProductModelID zugewiesen.  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 Beachten Sie, dass Attribute allen anderen Knotentypen, wie z. B. Elementknoten und Textknoten, auf derselben Ebene vorangestellt sein müssen. Die folgende Abfrage gibt einen Fehler zurück:  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a>Spaltenname beginnt nicht mit einem At-Zeichen (\@)  
 Wenn der Spaltenname nicht mit einem at-Zeichen ( \@ ) beginnt, keiner der XPath-Knoten Tests ist und keinen Schrägstrich (/) enthält, wird ein XML-Element erstellt, das ein untergeordnetes Element des Row-Elements ist, <`row` standardmäßig>.  
  
 Die folgende Abfrage gibt den Spaltennamen result an. Folglich wird dem <`row`>-Element das untergeordnete <`result`>-Element hinzugefügt.  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 Die folgende Abfrage gibt den Spaltennamen ManuWorkCenterInformation für den XML-Code an, der von der für die Instructions-Spalte vom **xml** -Typ angegebenen XQuery zurückgegeben wurde. Folglich wird dem <`row`>-Element das untergeordnete <`ManuWorkCenterInformation`>-Element hinzugefügt.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a>Spaltenname beginnt nicht mit einem At-Zeichen (\@) und enthält einen Schrägstrich (/)  
 Wenn der Spaltenname nicht mit einem At-Zeichen (\@) beginnt, jedoch einen Schrägstrich (/) enthält, zeigt der Spaltenname eine XML-Hierarchie an. Wenn der Spaltenname z.B. „Name1/Name2/Name3.../Name***n*** “ lautet, stellt „Name***i*** “ jeweils einen Elementnamen dar, der im aktuellen Zeilenelement geschachtelt ist (für i=1), oder der dem Element mit dem Namen „Name***i-1***“ untergeordnet ist. Wenn „Namen***n***“ mit „\@“ beginnt, wird er einem Attribut des „Namen***n-1***“-Elements zugeordnet.  
  
 Die folgende Abfrage gibt beispielsweise die ID und den Namen eines Mitarbeiters als komplexes Element EmpName zurück, welches zwei Vornamen und einen Nachnamen enthält (FirstName, MiddleName, LastName).  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 Die Spaltennamen werden als Pfad für die Konstruktion des XML-Codes im PATH-Modus verwendet. Der Spaltenname, der Mitarbeiter-ID-Werte enthält, beginnt mit " \@ ". Daher wird das Attribut " **EmpID**" dem <>-Element hinzugefügt `row` . Alle anderen Spalten enthalten einen eine Hierarchie aufzeigenden Schrägstrich (/) im Spaltennamen. Im resultierenden XML-Code befindet sich das untergeordnete <`EmpName`>-Element unter dem <`row`>-Element, und das untergeordnete <`EmpName`>-Element verfügt über die untergeordneten Elemente <`First`>, <`Middle`> und <`Last`>.  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 Der zweite Vorname des Mitarbeiters ist ein NULL-Wert, welcher standardmäßig der Abwesenheit eines Elements oder Attributs zugeordnet ist. Wenn Sie jedoch möchten, dass für NULL-Werte Elemente generiert werden, können Sie die ELEMENTS-Direktive mit XSINIL angeben, wie in der folgenden Abfrage gezeigt.  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 Standardmäßig generiert der PATH-Modus elementzentrierten XML-Code. Daher hat die Angabe der ELEMENTS-Direktive in einer Abfrage im PATH-Modus keine Wirkung. Die ELEMENTS-Direktive erweist sich jedoch in Verbindung mit XSINIL als nützlich, um Elemente für NULL-Werte zu generieren.  
  
 Die folgende Abfrage ruft außer der ID und dem Namen die Adresse eines Mitarbeiters ab. Entsprechend dem Pfad in den Spaltennamen für Adressspalten wird dem <`row`>-Element ein untergeordnetes <`Address`>-Element hinzugefügt, und die Adressdetails werden als untergeordnete Elemente des <`Address`>-Elements hinzugefügt.  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a>Mehrere Spalten verwenden dasselbe Pfadpräfix  
 Wenn mehrere aufeinander folgende Spalten dasselbe Pfadpräfix gemeinsam haben, werden sie unter demselben Namen gruppiert. Werden verschiedene Namespacepräfixe verwendet, wird ein Pfad als verschieden betrachtet, auch wenn die Präfixe an denselben Namespace gebunden sind. In der vorherigen Abfrage verfügen die Spalten FirstName, MiddleName und LastName über das gleiche EmpName-Präfix. Daher werden sie als untergeordnete Elemente des <`EmpName`>-Elements hinzugefügt. Dies war auch der Fall, als Sie das <`Address`>-Element im vorherigen Beispiel erstellt haben.  
  
## <a name="one-column-has-a-different-name"></a>Eine Spalte hat einen unterschiedlichen Namen  
 Wenn eine Spalte in einer Reihe von Spalten einen anderen Namen aufweist, wird die Gruppierung unterbrochen, wie in der folgenden, geänderten Abfrage gezeigt. Die Abfrage unterbricht die Gruppierung von FirstName, MiddleName und LastName, die in der vorherigen Abfrage angegeben waren, durch Hinzufügen der Adressspalten zwischen der FirstName- und der MiddleName-Spalte.  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 Daher erstellt die Abfrage zwei <`EmpName`>-Elemente. Das erste <`EmpName`>-Element verfügt über das untergeordnete <`FirstName`>-Element, und das zweite <`EmpName`>-Element verfügt über die untergeordneten Elemente <`MiddleName`> und <`LastName`>.  
  
 Dies ist das Ergebnis:  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)  
  
  
