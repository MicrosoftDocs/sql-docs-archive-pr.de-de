---
title: Schnelle Vorwärts Cursor (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: rothja
ms.author: jroth
ms.openlocfilehash: de8d82a0c72ad51741a3785fba2910f691028cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620347"
---
# <a name="fast-forward-only-cursors-odbc"></a>Schnelle Vorwärtscursor (ODBC)
  Wenn eine Verbindung mit einer Instanz von besteht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt der Native Client-ODBC-Treiber Leistungsoptimierungen für schreibgeschützte Vorwärts Cursor. Schnelle Vorwärtscursor werden vom Treiber und Server intern auf ganz ähnliche Weise implementiert wie Standardresultsets. Neben einer hohen Leistungsfähigkeit besitzen schnelle Vorwärtscursor auch folgende Eigenschaften:  
  
-   [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt. Die Resultsetspalten müssen an Programmvariablen gebunden sein.  
  
-   Wenn der Server auf das Ende des Cursors stößt, wird der Cursor automatisch geschlossen. Die Anwendung muss weiterhin [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE) aufzurufen, aber der Treiber muss nicht die Anforderung zum Schließen an den Server senden. Damit wird ein Roundtrip durch das Netzwerk zum Server eingespart.  
  
 Anwendungen fordern mit dem treiberspezifischen Anweisungsattribut SQL_SOPT_SS_CURSOR_OPTIONS schnelle Vorwärtscursor an. Wenn dieses auf SQL_CO_FFO festgelegt wird, werden schnelle Vorwärtscursor ohne die automatische Abrufoption aktiviert. Wenn es auf SQL_CO_FFO_AF festgelegt wird, wird auch die automatische Abrufoption aktiviert. Weitere Informationen zu Autofetch finden Sie unter [Verwenden von Autofetch mit ODBC-Cursorn](using-autofetch-with-odbc-cursors.md).  
  
 Schnelle Vorwärtscursor mit automatischer Abrufoption können eingesetzt werden, um kleine Resultsets mit nur einem Roundtrip zum Server abzurufen. In den folgenden Schritten ist *n* die Anzahl der zurück zugegenden Zeilen:  
  
1.  Legen Sie SQL_SOPT_SS_CURSOR_OPTIONS auf SQL_CO_FFO_AF fest.  
  
2.  Legen Sie SQL_ATTR_ROW_ARRAY_SIZE auf *n* + 1 fest.  
  
3.  Binden Sie die Ergebnis Spalten an Arrays von *n* + 1 Elementen (um sicher zu sein, wenn *n* + 1 Zeilen tatsächlich abgerufen werden).  
  
4.  Öffnen Sie den Cursor entweder mit **SQLExecDirect** oder **SQLExecute**.  
  
5.  Wenn der Rückgabestatus SQL_SUCCESS ist, dann wird **SQLFreeStmt** oder **SQLCloseCursor** aufgerufen, um den Cursor zu schließen. Alle Daten für die Zeilen sind in den gebundenen Programmvariablen enthalten.  
  
 Mit diesen Schritten sendet **SQLExecDirect** oder **SQLExecute** eine Anforderung zum Öffnen eines Cursors mit aktivierter Autofetch-Option. Auf diese einzelne Anforderung vom Client, führt der Server Folgendes aus:  
  
-   Er öffnet den Cursor.  
  
-   Er erstellt das Resultset und sendet die Zeilen an den Client.  
  
-   Weil die Rowsetgröße auf einen Wert festgelegt wurde, der um 1 größer als die Anzahl der Resultsetzeilen ist, erkennt der Server das Ende des Cursors und schließt den Cursor.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursor Programmierung &#40;ODBC-&#41;](cursor-programming-details-odbc.md)  
  
  
