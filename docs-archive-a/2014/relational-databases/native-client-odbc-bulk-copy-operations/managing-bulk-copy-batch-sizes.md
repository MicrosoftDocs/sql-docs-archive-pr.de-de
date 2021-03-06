---
title: Verwalten von Batch Größen für das Massen kopieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f24ece176cbb834e4162f9e516ff23013fd256a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620349"
---
# <a name="managing-bulk-copy-batch-sizes"></a>Verwalten von Batchgrößen für das Massenkopieren
  Der Hauptzweck eines Batches in Massenkopiervorgängen besteht darin, den Umfang einer Transaktion zu definieren. Wenn keine Batchgröße festgelegt ist, wird der gesamte Massenkopiervorgang von den Massenkopierfunktionen als eine einzige Transaktion behandelt. Ist eine Batchgröße festgelegt, stellt jeder Batch eine Transaktion dar, für die nach Beendigung des Batches ein Commit ausgeführt wird.  
  
 Wenn ein Massenkopiervorgang ohne festgelegte Batchgröße ausgeführt wird und ein Fehler auftritt, wird für den gesamten Massenkopiervorgang ein Rollback durchgeführt. Das Wiederherstellen eines Massenkopiervorgangs mit langer Laufzeit kann einige Zeit in Anspruch nehmen. Wenn eine Batchgröße festgelegt wird, wird jeder Batch als Transaktion betrachtet und ein Commit für jeden Batch ausgeführt. Wenn ein Fehler auftritt, muss nur für den letzten ausstehenden Batch ein Rollback ausgeführt werden.  
  
 Die Batchgröße kann auch den Sperrenaufwand beeinflussen. Beim Ausführen eines Massen Kopiervorgangs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann der TABLOCK-Hinweis mithilfe [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) angegeben werden, um anstelle von Zeilen Sperren eine Tabellensperre zu erhalten. Die einzelne Tabellensperre kann mit minimalem Aufwand für einen ganzen Massenkopiervorgang aufrechterhalten werden. Wird TABLOCK nicht festgelegt, werden Sperren für einzelne Zeilen errichtet und der Aufwand zur Aufrechterhaltung aller Sperren für die Dauer des Massenkopiervorgangs kann die Leistung beeinträchtigen. Da die Sperren nur für die Dauer der Transaktion aufrechterhalten werden, wird dieses Problem durch Angabe einer Batchgröße behoben, indem ein Commit ausgeführt wird, mit dem die aktuellen Sperren freigegeben werden.  
  
 Die Anzahl der Zeilen, die zu einem Batch gehören, kann sich erheblich auf die Leistung auswirken, wenn die Zeilenzahl für das Massenkopieren groß ist. Die Empfehlungen für die Batchgröße hängen vom Typ des auszuführenden Massenkopiervorgangs ab.  
  
-   Bei einem Massenkopiervorgang in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geben Sie den TABLOCK-Massenkopierhinweis an und legen eine große Batchgröße fest.  
  
-   Wenn TABLOCK nicht angegeben wird, beschränken Sie Batchgrößen auf unter 1.000 Zeilen.  
  
 Beim Massen kopieren aus einer Datendatei wird die Batch Größe durch Aufrufen von **bcp_control** mit der BCPBATCH-Option angegeben, bevor [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)aufgerufen wird. Beim Massen Kopieren von Programmvariablen mithilfe von [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) und [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)wird die Batch Größe durch Aufrufen von [bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) nach dem Aufrufen [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* -Mal gesteuert, wobei *x* die Anzahl der Zeilen in einem Batch ist.  
  
 Batches sind nicht nur für das Festlegen der Größe einer Transaktion relevant, sondern wirken sich auch auf den Zeitpunkt aus, an dem Zeilen über das Netzwerk an den Server gesendet werden. Massen Kopierfunktionen speichern die Zeilen in der Regel **bcp_sendrow** zwischen, bis ein Netzwerk Paket ausgefüllt ist, und senden das vollständige Paket an den Server. Wenn eine Anwendung **bcp_batch**aufruft, wird das aktuelle Paket jedoch unabhängig davon, ob es ausgefüllt wurde, an den Server gesendet. Eine sehr niedrige Batchgröße kann die Leistung herabsetzen, wenn dadurch viele teilweise aufgefüllte Pakete an den Server gesendet werden. Wenn Sie z. b. nach jeder **bcp_sendrow** **bcp_batch** aufrufen, bewirkt dies, dass jede Zeile in einem separaten Paket gesendet wird. wenn die Zeilen sehr groß sind, verschwendet der Speicherplatz in jedem Paket. Die Standardgröße von Netzwerk Paketen für SQL Server beträgt 4 KB, obwohl eine Anwendung die Größe durch Aufrufen von [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) , die das SQL_ATTR_PACKET_SIZE Attribut angibt, ändern kann.  
  
 Ein weiterer Nebeneffekt von Batches besteht darin, dass jeder Batch als ausstehendes Resultset betrachtet wird, bis es mit **bcp_batch**abgeschlossen ist. Wenn bei einem Verbindungs Handle andere Vorgänge versucht werden, während ein Batch aussteht, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt der Native Client-ODBC-Treiber einen Fehler mit SQLSTATE = "HY000" und der folgenden Fehlermeldungs Zeichenfolge aus:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](performing-bulk-copy-operations-odbc.md)   
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
