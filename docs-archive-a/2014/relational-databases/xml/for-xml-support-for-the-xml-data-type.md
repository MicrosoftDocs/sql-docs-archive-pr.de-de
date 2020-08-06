---
title: FOR XML-Unterstützung für den xml-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], XML
- xml data type [SQL Server], FOR XML clause
ms.assetid: 365de07d-694c-4c8b-b671-8825be27f87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 16b03d5f10ded40bb284c409f772ee8986060515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726765"
---
# <a name="for-xml-support-for-the-xml-data-type"></a>FOR XML-Unterstützung für den xml-Datentyp
  Wenn eine FOR XML-Abfrage eine Spalte vom `xml`-Typ in der SELECT-Klausel angibt, werden die Spaltenwerte unabhängig davon, ob die ELEMENTS-Direktive angegeben wird, im zurückgegebenen XML als Elemente zugeordnet. XML-Deklarationen in einer Spalte des `xml`-Typs werden nicht serialisiert.  
  
 Die folgende Abfrage ruft z. b. Kundenkontaktinformationen wie die `BusinessEntityID` Spalten, `FirstName` und und `LastName` die Telefonnummern aus der `AdditionalContactInfo` Spalte vom Typ ab `xml` .  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Da die Abfrage nicht die ELEMENTS-Direktive angibt, werden die Spaltenwerte als Attribute zurückgegeben. Eine Ausnahme sind die Werte für die zusätzlichen Kontaktinformationen, die aus der Spalte vom Typ `xml` abgerufen werden. Diese werden als Elemente zurückgegeben.  
  
 Dies ist das Teilergebnis:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</PhoneNumber>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<PhoneNumber>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</PhoneNumber>`  
  
```  
</Person.Person>  
...  
```  
  
 Wenn Sie einen Spaltenalias für die XML-Spalte angeben, die von der XQuery generiert wird, wird der Alias zum Hinzufügen eines Wrapperelements um das XML verwendet, das von der XQuery-Abfrage generiert wird. Die folgende Abfrage gibt z. B. `MorePhoneNumbers` als Spaltenalias an:  
  
```  
SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumber  
FROM Person.Person  
WHERE AdditionalContactInfo.query('  
declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
')IS NOT NULL  
FOR XML AUTO, TYPE;  
```  
  
 Das von der XQuery-Abfrage zurückgegebene XML wird vom <`MorePhoneNumbers`>-Element umschlossen, wie im folgenden Teilergebnis gezeigt wird:  
  
 `<Person.Person BusinessEntityID="291" FirstName="Gustavo" LastName="Achong">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1112</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">425-555-1111</act:number>`  
  
 `</MorePhoneNumbers>`  
  
 `</Person.Person>`  
  
 `<Person.Person BusinessEntityID="293" FirstName="Catherine" LastName="Abel">`  
  
 `<MorePhoneNumbers>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-2222</act:number>`  
  
 `<act:number xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">206-555-1234</act:number>`  
  
 `</MorePhoneNumbers>`  
  
```  
</Person.Person>  
...  
```  
  
 Wenn Sie die ELEMENTS-Direktive in der Abfrage angeben, werden BusinessEntityID, LastName und FirstName als Elemente im sich ergebenden XML zurückgegeben.  
  
 Das folgende Beispiel zeigt, dass die FOR XML-Verarbeitungslogik XML-Deklarationen in den XML-Daten aus einer Spalte des `xml`-Typs nicht serialisiert:  
  
```  
create table t(i int, x xml)  
go  
insert into t values(1, '<?xml version="1.0" encoding="UTF-8" ?>  
                             <Root SomeID="10" />')  
select i, x  
from   t  
for xml auto;  
```  
  
 Dies ist das Ergebnis. In diesem Ergebnis wird die XML-Deklaration <`?xml version="1.0" encoding="UTF-8" ?`> nicht serialisiert.  
  
```  
<root>  
  <t i="1">  
    <x>  
      <Root SomeID="10" />  
    </x>  
  </t>  
</root>  
```  
  
## <a name="returning-xml-from-a-user-defined-function"></a>Zurückgeben von XML aus einer benutzerdefinierten Funktion  
 FOR XML-Abfragen können zum Zurückgeben von XML aus einer benutzerdefinierten Funktion verwendet werden, die eines der folgenden Objekte zurückgibt:  
  
-   Eine Tabelle mit einer einzelnen Spalte des Typs `xml`.  
  
-   Eine Instanz vom `xml`-Typ.  
  
 Die folgende benutzerdefinierte Funktion gibt z. B. eine Tabelle mit einer einzelnen Spalte des `xm`-Typs zurück:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.MyUDF (@ProudctModelID int)  
RETURNS @T TABLE  
  (  
     ProductDescription xml  
  )  
AS  
BEGIN  
  INSERT @T  
     SELECT CatalogDescription.query('  
declare namespace PD="http://www.adventure-works.com/schemas/products/description";  
                    //PD:ProductDescription  ')  
     FROM Production.ProductModel  
     WHERE ProductModelID = @ProudctModelID  
  RETURN  
END;  
```  
  
 Sie können die benutzerdefinierte Funktion ausführen und die von dieser zurückgegebene Tabelle abfragen. In diesem Beispiel wird das durch Abfragen der Tabelle zurückgegebene XML einer Variablen vom Typ `xml` zugewiesen.  
  
```  
declare @x xml;  
set @x = (SELECT * FROM MyUDF(19));  
select @x;  
```  
  
 Das folgende Beispiel zeigt eine weitere benutzerdefinierte Funktion. Diese benutzerdefinierte Funktion gibt eine Instanz des `xml`-Typs zurück. In diesem Beispiel gibt die benutzerdefinierte Funktion eine typisierte XML-Instanz zurück, weil der Schemanamespace angegeben wird.  
  
```  
DROP FUNCTION dbo.MyUDF;  
GO  
CREATE FUNCTION MyUDF (@ProductModelID int)   
RETURNS xml ([Production].[ProductDescriptionSchemaCollection])  
AS  
BEGIN  
  declare @x xml  
  set @x =   ( SELECT CatalogDescription  
          FROM Production.ProductModel  
          WHERE ProductModelID = @ProductModelID )  
  return @x  
END;  
```  
  
 Das durch die benutzerdefinierte Funktion zurückgegebene XML kann einer Variablen vom Typ `xml` wie folgt zugewiesen werden:  
  
```  
declare @x xml;  
SELECT @x= dbo.MyUDF4 (19) ;  
select @x;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [FOR XML-Unterstützung für verschiedene SQL Server-Datentypen](for-xml-support-for-various-sql-server-data-types.md)  
  
  
