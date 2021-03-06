---
title: Schrittweise Wiederherstellung von Datenbanken mit speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 732c9721-8dd4-481d-8ff9-1feaaa63f84f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed23f08d40e23b1d43c1b642f4089fe77646b675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722813"
---
# <a name="piecemeal-restore-of-databases-with-memory-optimized-tables"></a>Schrittweise Wiederherstellung von Datenbanken mit speicheroptimierten Tabellen
  Die schrittweise Wiederherstellung wird für Datenbanken mit speicheroptimierten Tabellen unterstützt, allerdings mit der im Folgenden beschriebenen Einschränkung. Weitere Informationen zur schrittweisen Sicherung und Wiederherstellung finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) und [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).  
  
 Eine speicheroptimierte Dateigruppe muss zusammen mit der primären Dateigruppe gesichert und wiederhergestellt werden:  
  
-   Wenn Sie die primäre Dateigruppe sichern (oder wiederherstellen), müssen Sie die speicheroptimierte Dateigruppe angeben.  
  
-   Wenn Sie die speicheroptimierte Dateigruppe sichern (oder wiederherstellen), müssen Sie die primäre Dateigruppe angeben.  
  
 Wichtige Szenarien für die schrittweise Sicherung und Wiederherstellung  
  
-   Mithilfe der schrittweisen Sicherung lässt sich die Größe der Sicherung reduzieren. Einige Beispiele:  
  
    -   Konfigurieren Sie die Datenbanksicherung für unterschiedliche Uhrzeiten oder Tage, um die Auswirkungen auf die Arbeitsauslastung zu minimieren. Ein Beispiel hierfür ist eine sehr umfangreiche Datenbank (größer als 1 TB), bei der eine vollständige Datenbanksicherung nicht innerhalb des für die Datenbankwartung vorgesehenen Zeitraums abgeschlossen werden kann. In diesem Fall können Sie die schrittweise Sicherung verwenden, um die vollständige Datenbank in mehreren schrittweisen Sicherungen zu sichern.  
  
    -   Wenn eine Dateigruppe als schreibgeschützt gekennzeichnet ist, erfordert sie keine Transaktionsprotokollsicherung, nachdem sie als schreibgeschützt gekennzeichnet wurde. Nachdem Sie die Dateigruppe als schreibgeschützt gekennzeichnet haben, können Sie sie optional nur einmal sichern.  
  
-   Schrittweise Wiederherstellung.  
  
    -   Das Ziel einer schrittweisen Wiederherstellung besteht darin, die wichtigen Datenbankinhalte online zu schalten, ohne darauf zu warten, dass alle Daten wiederhergestellt sind. Ein Beispiel ist eine Datenbank mit partitionierten Daten, bei der ältere Partitionen nur selten verwendet werden. Diese Partitionen können dann jeweils nur bei Bedarf wiederhergestellt werden. Ähnliches gilt für Dateigruppen, die beispielsweise Vergangenheitsdaten enthalten.  
  
    -   Mithilfe der Seitenreparatur können Sie eine Seitenbeschädigung beheben, indem Sie die jeweilige Seite wiederherstellen. Weitere Informationen finden Sie unter [Wiederherstellung von Seiten &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md).  
  
## <a name="samples"></a>Beispiele  
 In den Beispielen wird das folgende Schema verwendet:  
  
```  
CREATE DATABASE imoltp  
ON PRIMARY (name = imoltp_primary1, filename = 'c:\data\imoltp_data1.mdf')  
LOG ON (name = imoltp_log, filename = 'c:\data\imoltp_log.ldf')  
GO  
  
ALTER DATABASE imoltp ADD FILE (name = imoltp_primary2, filename = 'c:\data\imoltp_data2.ndf')  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_secondary  
ALTER DATABASE imoltp ADD FILE (name = imoltp_secondary, filename = 'c:\data\imoltp_secondary.ndf') TO FILEGROUP imoltp_secondary  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod2', filename='c:\data\imoltp_mod2') TO FILEGROUP imoltp_mod   
GO  
```  
  
### <a name="backup"></a>Backup  
 Dieses Beispiel veranschaulicht, wie die primäre Dateigruppe und die speicheroptimierte Dateigruppe gesichert werden. Sie müssen die primäre und speicheroptimierte Dateigruppe zusammen angeben.  
  
```  
backup database imoltp filegroup='primary', filegroup='imoltp_mod' to disk='c:\data\imoltp.dmp' with init  
```  
  
 Das folgende Beispiel veranschaulicht, dass eine Dateigruppensicherung, die keine primäre und speicheroptimierte Dateigruppe umfasst, ähnlich wie bei Datenbanken ohne speicheroptimierte Tabellen funktioniert. Mit dem folgenden Befehl wird die sekundäre Dateigruppe gesichert.  
  
```  
backup database imoltp filegroup='imoltp_secondary' to disk='c:\data\imoltp_secondary.dmp' with init  
```  
  
### <a name="restore"></a>Restore  
 Im folgenden Beispiel wird gezeigt, wie die primäre Dateigruppe und speicheroptimierte Dateigruppe zusammen wiederhergestellt werden.  
  
```  
restore database imoltp filegroup = 'primary', filegroup = 'imoltp_mod'   
from disk='c:\data\imoltp.dmp' with partial, norecovery  
  
--restore the transaction log  
 RESTORE LOG [imoltp] FROM DISK = N'c:\data\imoltp_log.dmp' WITH  FILE = 1,  NOUNLOAD,  STATS = 10  
GO  
```  
  
 Das nächste Beispiel veranschaulicht, dass eine Dateigruppenwiederherstellung, die keine primäre und speicheroptimierte Dateigruppe umfasst, ähnlich wie bei Datenbanken ohne speicheroptimierte Tabellen funktioniert.  
  
```  
RESTORE DATABASE [imoltp] FILE = N'imoltp_secondary'   
FROM  DISK = N'c:\data\imoltp_secondary.dmp' WITH  FILE = 1,  RECOVERY,  NOUNLOAD,  STATS = 10  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen speicheroptimierter Tabellen](../../database-engine/backup-restore-and-recovery-of-memory-optimized-tables.md)  
  
  
