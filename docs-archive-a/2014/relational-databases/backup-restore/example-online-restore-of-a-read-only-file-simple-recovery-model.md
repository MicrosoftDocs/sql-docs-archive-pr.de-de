---
title: 'Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei (einfaches Wiederherstellungsmodell) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d84c920a2cb40866ba106b4d30d8e24c4caea611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726005"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a>Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei (einfaches Wiederherstellungsmodell)
  Dieses Thema ist nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken relevant, für die ein einfaches Wiederherstellungsmodell mit einer schreibgeschützten Dateigruppe verwendet wird. Bei einem einfachen Wiederherstellungsmodell kann eine schreibgeschützte Datei online wiederhergestellt werden, wenn eine Dateisicherung vorhanden ist, die erstellt wurde, nachdem der Schreibschutz letztmalig festgelegt wurde.  
  
 In diesem Beispiel sind in der Datenbank `adb` drei Dateigruppen enthalten. Die Dateigruppe `A` weist Lese-/Schreibzugriff auf, die Dateigruppen `B` und `C` sind schreibgeschützt. Zu Beginn sind alle Dateigruppen online. Eine schreibgeschützte Datei in Dateigruppe `B`, `b1`, muss wiederhergestellt werden. Der Datenbankadministrator kann sie mithilfe einer Sicherung wiederherstellen, die erstellt wurde, nachdem der Schreibschutz für die Datei festgelegt wurde. Für die Dauer der Wiederherstellung ist die Dateigruppe `B` offline, der Rest der Datenbank bleibt jedoch online.  
  
## <a name="restore-sequence"></a>Wiederherstellungssequenz  
  
> [!NOTE]  
>  Die Syntax für eine Onlinewiederherstellungssequenz ist dieselbe wie bei einer Offlinewiederherstellungssequenz.  
  
 Zum Wiederherstellen der Datei befolgt der Datenbankadministrator die folgende Wiederherstellungssequenz:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 Die Datei ist zurzeit online.  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Vollständiges Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;vollständiges Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer Datei mit Lese-/Schreibzugriff &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Beispiel: Onlinewiederherstellung einer schreibgeschützten Datei &#40;vollständiges Wiederherstellungsmodell&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Onlinewiederherstellungen &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)   
 [Dateiwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](file-restores-simple-recovery-model.md)   
 [Übersicht über Wiederherstellungsvorgänge &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
