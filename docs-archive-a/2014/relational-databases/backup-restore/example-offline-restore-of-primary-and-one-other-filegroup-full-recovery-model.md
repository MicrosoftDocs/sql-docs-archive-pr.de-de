---
title: 'Beispiel: Offline Wiederherstellung der primären und einer anderen Datei Gruppe (vollständiges Wiederherstellungs Modell) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f845927fdd74fba476139fccbf9a5fa112d434e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621520"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a>Beispiel: Offlinewiederherstellung der primären Dateigruppe und einer weiteren Dateigruppe (vollständiges Wiederherstellungsmodell)
  Dieses Thema ist nur für Datenbanken relevant, in denen mehrere Dateigruppen enthalten sind und für die das vollständige Wiederherstellungsmodell verwendet wird.  
  
 In diesem Beispiel sind in der Datenbank `adb` drei Dateigruppen enthalten. Die Dateigruppen `A` und `C` weisen Lese-/Schreibzugriff auf, und die Dateigruppe `B` ist schreibgeschützt. Die primäre Dateigruppe und die Dateigruppe `B` sind beschädigt, die Dateigruppen `A` und `C` sind jedoch intakt. Vor dem Notfall waren alle Dateigruppen online.  
  
 Der Datenbankadministrator entscheidet sich, die primäre Dateigruppe und Dateigruppe `B`wiederherzustellen. Für die Datenbank wird das vollständige Wiederherstellungsmodell verwendet, weshalb vor dem Beginn der Wiederherstellung eine Protokollfragmentsicherung der Datenbank erstellt werden muss. Wenn die Datenbank online geschaltet wird, werden die Dateigruppen `A` und `C` automatisch online geschaltet.  
  
> [!NOTE]  
>  Die Offlinewiederherstellungssequenz verfügt über weniger Schritte als die Onlinewiederherstellung einer schreibgeschützten Datei. Ein Beispiel finden Sie unter [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;Vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md). Die gesamte Datenbank ist jedoch für die Dauer der Wiederherstellungssequenz offline.  
  
## <a name="tail-log-backup"></a>Sicherung des Protokollfragments  
 Vor dem Wiederherstellen der Datenbank muss der Datenbankadministrator das Protokollfragment sichern. Weil die Datenbank beschädigt ist, muss zum Erstellen der Sicherung des Protokollfragments die NO_TRUNCATE-Option verwendet werden:  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 Bei der Sicherung des Protokollfragments handelt es sich um die letzte Sicherung im Rahmen der folgenden Wiederherstellungssequenzen.  
  
## <a name="restore-sequence"></a>Wiederherstellungssequenz  
 Zum Wiederherstellen der primären Dateigruppe und der Dateigruppe `B`verwendet der Datenbankadministrator die Wiederherstellungssequenz ohne die Option PARTIAL folgendermaßen:  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 Die nicht wiederhergestellten Dateien werden automatisch online geschaltet. Alle Dateigruppen sind jetzt online.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Onlinewiederherstellungen &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)   
 [Dateiwiederherstellungen &#40;vollständiges Wiederherstellungsmodell&#41;](file-restores-full-recovery-model.md)   
 [Anwenden von Transaktionsprotokollsicherungen &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
