---
title: Dateistatus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- restoring file state [SQL Server]
- verifying file states
- current file states
- verifying filegroup states
- file states [SQL Server]
- online file state
- offline file state [SQL Server]
- viewing filegroup states
- viewing file states
- suspect file state
- recovering file state [SQL Server]
- current filegroup state
- recovery pending file state [SQL Server]
- displaying file states
- states [SQL Server], files
- displaying filegroup states
- defunct file state
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7cad94527d9191609a6920b5dfa200a98cd8bbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620985"
---
# <a name="file-states"></a>Dateistatus
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wird der Status einer Datenbankdatei unabhängig vom Status der Datenbank verwaltet. Eine Datei befindet sich immer in einem bestimmten Status, wie ONLINE oder OFFLINE. Um den aktuellen Status einer Datei anzuzeigen, verwenden Sie die Katalogsicht [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) oder [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) . Wenn die Datenbank offline ist, kann der Status der Dateien über die [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) -Katalogsicht angezeigt werden.  
  
 Der Status der Dateien in einer Dateigruppe legt die Verfügbarkeit der gesamten Dateigruppe fest. Damit eine Dateigruppe verfügbar ist, müssen alle Dateien in der Dateigruppe online sein. Wenn Sie den aktuellen Status einer Dateigruppe anzeigen möchten, verwenden Sie die [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) -Katalogsicht. Wenn eine Dateigruppe offline ist und Sie versuchen, mit einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung auf die Dateigruppe zuzugreifen, führt dies zu einem Fehler. Wenn der Abfrageoptimierer Abfragepläne für SELECT-Anweisungen erstellt, vermeidet er nicht gruppierte Indizes und indizierte Sichten, die in Offlinedateigruppen gespeichert sind, damit die Anweisungen erfolgreich ausgeführt werden. Enthält die Offlinedateigruppe jedoch den Heap oder gruppierten Index der Zieltabelle, schlagen die SELECT-Anweisungen fehl. Auch alle INSERT-, UPDATE- oder DELETE-Anweisungen, die eine Tabelle mit einem Index in einer Offlinedateigruppe ändern, schlagen fehl.  
  
## <a name="file-state-definitions"></a>Dateistatusdefinitionen  
 Die folgende Tabelle definiert den Dateistatus.  
  
|State|Definition|  
|-----------|----------------|  
|ONLINE|Die Datei ist für alle Vorgänge verfügbar. Dateien in der primären Dateigruppe sind immer online, wenn die Datenbank selbst online ist. Wenn eine Datei in der primären Dateigruppe nicht online ist, ist die Datenbank nicht online, und der Status der sekundären Dateien ist nicht definiert.|  
|OFFLINE|Die Datei ist nicht für den Zugriff verfügbar und ist möglicherweise nicht auf dem Datenträger vorhanden. Dateien werden durch explizite Benutzeraktionen offline geschaltet und bleiben offline, bis weitere Benutzeraktionen durchgeführt werden.<br /><br /> Vorsicht eine Datei sollte nur offline geschaltet werden, wenn die Datei beschädigt ist, jedoch wieder hergestellt werden kann. ** \* \* \* \* ** Eine offline geschaltete Datei kann nur durch Wiederherstellen der Datei aus der Sicherung erneut online geschaltet werden. Weitere Informationen zum Wiederherstellen einer einzelnen Datei finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).|  
|RESTORING|Die Datei wird wiederhergestellt. Dateien gehen aufgrund eines Wiederherstellungsbefehls in den Wiederherstellungsstatus über, der sich auf die gesamte Datei und nicht nur auf eine Seitenwiederherstellung bezieht; sie verbleiben in diesem Status, bis die Wiederherstellung abgeschlossen ist und die Datei wiederhergestellt wurde.|  
|RECOVERY PENDING|Die Wiederherstellung der Datei wurde verschoben. Eine Datei geht automatisch in diesen Status über, weil ein schrittweiser Wiederherstellungsvorgang durchgeführt wird, bei dem die Datei nicht wiederhergestellt wird. Es sind weitere Aktionen durch den Benutzer erforderlich, um den Fehler zu beheben und den Wiederherstellungsvorgang erfolgreich abzuschließen. Weitere Informationen finden Sie unter [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).|  
|SUSPECT|Die Wiederherstellung der Datei ist während eines Onlinewiederherstellungsvorgangs fehlgeschlagen. Wenn sich die Datei in der primären Dateigruppe befindet, wird die Datenbank ebenfalls als fehlerverdächtig markiert. Anderenfalls gilt nur für die Datei der Status Fehlerverdächtig, und die Datenbank besitzt auch weiterhin den Status online.<br /><br /> Die Datei behält den Status Fehlerverdächtig, bis sie durch eine der folgenden Methoden bereitgestellt wird:<br /><br /> Wiederherstellung<br /><br /> DBCC CHECKDB mit REPAIR_ALLOW_DATA_LOSS|  
|DEFUNCT|Die Datei wurde gelöscht, während sie nicht online war. Alle Dateien in einer Dateigruppe erhalten den Status "defunct", wenn eine Offlinedateigruppe entfernt wird.|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [Datenbankstatus](database-states.md)  
  
 [Spiegelungsstatus &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [Datenbankdateien und Dateigruppen](database-files-and-filegroups.md)  
  
  
