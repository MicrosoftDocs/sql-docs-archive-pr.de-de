---
title: FOR XML (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, about FOR XML clause
- PATH FOR XML mode, construction
- EXPLICIT FOR XML mode
- RAW FOR XML mode
- retrieving XML data
- XML [SQL Server], FOR XML clause
- AUTO FOR XML mode
- XML [SQL Server], construction
ms.assetid: 2b6b5c61-c5bd-49d2-8c0c-b7cf15857906
author: rothja
ms.author: jroth
ms.openlocfilehash: 6fe55186e89020f57ae1eb078625d1cdce262864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726778"
---
# <a name="for-xml-sql-server"></a>FOR XML (SQL Server)
  Eine SELECT-Abfrage gibt Ergebnisse als Rowset zurück. Sie können optional die formalen Ergebnisse einer SQL-Abfrage als XML abrufen, indem Sie die FOR XML-Klausel in der Abfrage angeben. Die FOR XML-Klausel kann in Abfragen der obersten Ebene sowie in Unterabfragen verwendet werden. Die FOR XML-Klausel der obersten Ebene kann nur in der SELECT-Anweisung verwendet werden. In Unterabfragen kann FOR XML in den INSERT-, UPDATE- und DELETE-Anweisungen verwendet werden. Die Klausel kann auch in Zuweisungsanweisungen verwendet werden.  
  
 In einer FOR XML-Klausel geben Sie einen der folgenden Modi an:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
-   PATH  
  
 Der RAW-Modus generiert ein einzelnes \<row>-Element pro Zeile im Rowset, das von der SELECT-Anweisung zurückgegeben wird. Sie können eine XML-Hierarchie erstellen, indem Sie geschachtelte FOR XML-Abfragen schreiben.  
  
 Der AUTO-Modus generiert mithilfe von Heuristik, basierend auf der Art der Angabe der SELECT-Anweisung, Schachtelung in dem sich ergebenden XML. Sie besitzen nur minimale Kontrolle über die Form des generierten XML. Die geschachtelten FOR XML-Abfragen können geschrieben werden, um eine XML-Hierarchie zu erstellen, die über die XML-Form hinausgeht, die von der Heuristik des AUTO-Modus generiert wird.  
  
 Der EXPLICIT-Modus lässt eine größere Kontrolle über die Form des XML zu. Sie können Attribute und Elemente beliebig mischen, um die Form des XML zu bestimmen. Aufgrund der Abfrageausführung ist ein bestimmtes Format für das sich ergebende Rowset erforderlich, das generiert wird. Dieses Rowsetformat wird anschließend der XML-Form zugeordnet. Die Leistungsfähigkeit des EXPLICIT-Modus beruht auf der Möglichkeit, Attribute und Elemente beliebig zu mischen, Wrapper und verschachtelte komplexe Eigenschaften, durch Leerzeichen getrennte Werte (das OrderID-Attribut kann z. B. eine Liste von Bestellungs-ID-Werten besitzen) und gemischte Inhalte erstellen zu können.  
  
 Das Schreiben von Abfragen für den EXPLICIT-Modus kann jedoch aufwendig sein. Sie können einige der neuen FOR XML-Funktionen verwenden; Sie können z. B. verschachtelte Abfragen für den FOR XML RAW/AUTO/PATH-Modus und die TYPE-Direktive schreiben, statt den EXPLICIT-Modus zum Generieren der Hierarchien zu verwenden. Die geschachtelten FOR XML-Abfragen können beliebiges XML erstellen, das mithilfe des EXPLICIT-Modus generiert werden kann. Weitere Informationen finden Sie unter [Verwenden von geschachtelten FOR XML-Abfragen](use-nested-for-xml-queries.md) und [TYPE-Direktive in FOR XML-Abfragen](type-directive-in-for-xml-queries.md).  
  
 Der PATH-Modus stellt zusammen mit der Möglichkeit geschachtelter FOR XML-Abfragen die Flexibilität des EXPLICIT-Modus auf einfachere Weise bereit.  
  
 Diese Modi gelten ausschließlich für die Ausführung der Abfrage, für die sie festgelegt wurden. Sie wirken sich nicht auf die Ergebnisse nachfolgender Abfragen aus.  
  
 FOR XML ist für keine Auswahl gültig, die mit einer FOR BROWSE-Klausel verwendet wird.  
  
## <a name="example"></a>Beispiel  
 So ruft die folgende `SELECT` -Anweisung Informationen aus den `Sales.Customer` - und `Sales.SalesOrderHeader` -Tabellen der `AdventureWorks2012` -Datenbank ab. Diese Abfrage gibt den `AUTO` -Modus in der `FOR XML` -Klausel an:  
  
```  
USE AdventureWorks2012  
GO  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status  
FROM Sales.Customer Cust   
INNER JOIN Sales.SalesOrderHeader OrderHeader  
ON Cust.CustomerID = OrderHeader.CustomerID  
FOR XML AUTO  
```  
  
## <a name="the-for-xml-clause-and-server-names"></a>Die FOR XML-Klausel und Servernamen  
 Wenn eine SELECT-Anweisung mit einer FOR XML-Klausel einen vierteiligen Namen in der Abfrage angibt, wird der Servername im sich ergebenden XML-Dokument nicht zurückgegeben, wenn die Abfrage auf dem lokalen Computer ausgeführt wird. Wenn die Abfrage jedoch auf einem Netzwerkserver ausgeführt wird, wird der Servername als vierteiliger Name zurückgegeben.  
  
 Angenommen, Sie haben die folgende Abfrage vorliegen:  
  
```  
SELECT TOP 1 LastName  
FROM ServerName.AdventureWorks2012.Person.Person  
FOR XML AUTO  
```  
  
 Wenn `ServerName` ein lokaler Server ist, gibt die Abfrage Folgendes zurück:  
  
```  
<AdventureWorks2012.Person.Person LastName="Achong" />  
```  
  
 Wenn `ServerName` ein Netzwerkserver ist, gibt die Abfrage Folgendes zurück:  
  
```  
<ServerName.AdventureWorks2012.Person.Person LastName="Achong" />  
```  
  
 Diese potenzielle Mehrdeutigkeit kann vermieden werden, indem Sie den folgenden Alias angeben:  
  
```  
SELECT TOP 1 LastName  
FROM ServerName.AdventureWorks2012.Person.Person x  
FOR XML AUTO   
```  
  
 Diese Abfrage gibt Folgendes zurück:  
  
```  
<x LastName="Achong"/>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegende Syntax der for XML-Klausel](basic-syntax-of-the-for-xml-clause.md)   
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)   
 [Verwenden des AUTO-Modus mit FOR XML](use-auto-mode-with-for-xml.md)   
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)   
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)   
 [OPENXML-&#40;SQL Server&#41;](openxml-sql-server.md)   
 [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
