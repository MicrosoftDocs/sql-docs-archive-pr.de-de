---
title: 'Beispiel: Angeben der ELEMENT-Anweisung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
ms.assetid: 80dd5d1f-fa90-4f97-a186-8fa3f460a7f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a03d1049fa9df23eff759634bcd74f88f842a8e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695462"
---
# <a name="example-specifying-the-element-directive"></a>Beispiel: Angeben der ELEMENT-Direktive
  Dadurch werden Mitarbeiterinformationen abgerufen und wird elementzentriertes XML generiert, wie nachfolgend zu sehen ist:  
  
```  
<Employee EmpID=...>  
  <Name>  
    <FName>...</FName>  
    <LName>...</LName>  
  </Name>  
</Employee>  
```  
  
 Die Abfrage bleibt dieselbe, mit der Ausnahme, dass Sie nun den Spaltennamen die `ELEMENT`-Direktive hinzufügen. Folglich werden dem <`Name`>-Element anstelle von Attributen die untergeordneten Elemente <`FName`> und <`LName`> hinzugefügt. Die `Employee!1!EmpID`-Spalte gibt keine `ELEMENT`-Direktive an; daher wird `EmpID` als Attribut des <`Employee`>-Elements hinzugefügt.  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName!ELEMENT],  
       NULL       as [Name!2!LName!ELEMENT]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
ORDER BY [Employee!1!EmpID],[Name!2!FName!ELEMENT]  
FOR XML EXPLICIT;  
```  
  
 Dies ist das Teilergebnis.  
  
 `<Employee EmpID="1">`  
  
 `<Name>`  
  
 `<FName>Ken</FName>`  
  
 `<LName>S??nchez</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name>`  
  
 `<FName>Terri</FName>`  
  
 `<LName>Duffy</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `...`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
