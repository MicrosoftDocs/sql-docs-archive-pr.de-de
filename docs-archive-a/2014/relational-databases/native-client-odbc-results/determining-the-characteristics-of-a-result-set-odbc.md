---
title: Bestimmen der Eigenschaften eines Resultsets (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5957092cdddfbcbce904d9a6483914672565d337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616041"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a>Bestimmen der Eigenschaften eines Resultsets (ODBC)
  Metadaten sind Daten, die andere Daten beschreiben. Resultsetmetadaten beschreiben beispielsweise die Merkmale eines Resultsets, wie die Spaltenanzahl im Resultset, die Datentypen in diesen Spalten, ihre Namen, Genauigkeit und NULL-Zulässigkeit.  
  
 ODBC liefert Metadaten an Anwendungen durch seine API-Katalogfunktionen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber implementiert viele der ODBC-API-Katalog Funktionen als Aufrufe einer entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Katalog Prozedur.  
  
 Anwendungen erfordern Metadaten für die meisten Resultsetvorgänge. Die Anwendung verwendet z. B. den Datentyp einer Spalte, um zu bestimmen, welche Art von Variable an diese Spalte gebunden werden soll. Sie verwendet die Bytelänge einer Zeichenspalte, um zu bestimmen, wie viel Platz zur Anzeige von Daten aus dieser Spalte erforderlich ist. Wie eine Anwendung die Metadaten für eine Spalte bestimmt, hängt vom Typ der Anwendung ab.  
  
 Vertikale Anwendungen funktionieren i. d. R. mit vordefinierten Tabellen und führen vordefinierte Vorgänge auf diese Tabellen aus. Da die Resultsetmetadaten für solche Anwendungen definiert werden, bevor die Anwendung überhaupt geschrieben wird, und vom Entwickler gesteuert werden, können sie in die Anwendung hartcodiert werden. Wenn beispielsweise eine OrderID-Spalte in der Datenquelle als 4-Byte-Ganzzahl definiert ist, kann die Anwendung stets eine 4-Byte-Ganzzahl an diese Spalte binden. Wenn Metadaten in der Anwendung hartcodiert sind, bedeutet eine Änderung an den von der Anwendung verwendeten Tabelle im Allgemeinen eine Änderung am Anwendungscode.  
  
 In generischen Anwendungen, vor allem Anwendungen, die Ad-Hoc-Abfragen unterstützen, sind die Metadaten des von ihnen erstellten Resultsets typischerweise bis zur Laufzeit unbekannt.  
  
 Ein Anwendung kann folgende Aufrufe durchführen, um die Eigenschaften eines Resultsets zu bestimmen:  
  
-   [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) , um zu bestimmen, wie viele Spalten eine Anforderung zurückgegeben hat.  
  
-   [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) oder [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) , um eine Spalte im Resultset zu beschreiben.  
  
 Eine wohlgeformte Anwendung wird ausgehend von der Annahme geschrieben, dass das Resultset unbekannt ist, und verwendet die von diesen Funktionen zurückgegebenen Informationen dazu, die Spalten im Resultset zu binden. Eine Anwendung kann diese Funktionen jederzeit aufrufen, nachdem eine Anweisung vorbereitet oder ausgeführt wurde. Um eine optimale Leistung zu erzielen, sollte eine Anwendung jedoch nach der Ausführung einer-Anweisung **SQLColAttribute**, **SQLDescribeCol**und **SQLNumResultCols** aufzurufen.  
  
 Sie können mehrere gleichzeitige Abrufe auf Metadaten durchführen. Die den ODBC-API-Implementierungen zugrunde liegenden Systemkatalogprozeduren können mit dem ODBC-Treiber aufgerufen werden, während dieser statische Servercursor verwendet. So können Anwendungen mehrere Aufrufe an ODBC-Katalogfunktionen gleichzeitig verarbeiten.  
  
 Wenn die Anwendung einen bestimmten Metadatensatz mehr als ein Mal verwendet, ist es möglicherweise von Vorteil, wenn die Informationen beim ersten Abrufen in privaten Variablen zwischengespeichert werden. Dadurch werden spätere Aufrufe an die ODBC-Katalogfunktionen für die gleichen Informationen vermieden, durch die der Treiber zu Roundtrips zum Server gezwungen wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC-&#41;](processing-results-odbc.md)  
  
  
