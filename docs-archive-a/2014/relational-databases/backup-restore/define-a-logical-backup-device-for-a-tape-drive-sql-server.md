---
title: Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8728df2cc0b5907e51da84ed9e77d897a1718d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726014"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a>Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk (SQL Server)
  In diesem Thema wird beschrieben, wie Sie ein logisches Sicherungsmedium für ein Bandlaufwerk in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]definieren. Ein logisches Medium ist ein benutzerdefinierter Name, der auf ein bestimmtes, physisches Sicherungsmedium (Datenträgerdatei oder Bandlaufwerk) verweist.  Die Initialisierung des physischen Mediums erfolgt später, wenn eine Sicherung auf das Sicherungsmedium geschrieben wird.  
  
> [!NOTE]  
>  Die Unterstützung für Bandsicherungsgeräte wird in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So definieren Sie ein logisches Sicherungsmedium für ein Bandlaufwerk mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Das Bandlaufwerk bzw. die -laufwerke müssen vom Betriebssystem Microsoft Windows unterstützt werden.  
  
-   Das Bandmedium muss physisch mit dem Computer verbunden sein, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird. Das Sichern auf Remotebandmedien wird nicht unterstützt.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **diskadmin** .  
  
 Erfordert die Berechtigung zum Schreiben auf den Datenträger.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>So definieren Sie ein logisches Sicherungsmedium für ein Bandlaufwerk  
  
1.  Klicken Sie nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Serverobjekte**, und klicken Sie dann mit der rechten Maustaste auf **Sicherungsmedien**.  
  
3.  Klicken Sie auf **Neues Sicherungsmedium**, um das Dialogfeld **Sicherungsmedium** zu öffnen.  
  
4.  Geben Sie einen Mediennamen ein.  
  
5.  Klicken Sie für das Ziel auf **Band** , und wählen Sie ein Bandlaufwerk aus, das noch keinem anderen Sicherungsmedium zugeordnet ist. Falls keine Bandlaufwerke verfügbar sind, ist die Option **Band** deaktiviert.  
  
6.  Klicken Sie auf **OK**, um das neue Medium zu definieren.  
  
 Damit eine Sicherung auf dieses neue Medium erstellt werden kann, fügen Sie es dem Feld **Sichern auf:** im Dialogfeld **Datenbank sichern** (Seite **Allgemein**) hinzu. Weitere Informationen finden Sie unter [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>So definieren Sie ein logisches Sicherungsmedium für ein Bandlaufwerk  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie Sie [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) verwenden müssen, um ein logisches Sicherungsmedium für ein Band zu definieren. Im folgenden Beispiel wird das Bandsicherungsmedium `tapedump1`mit dem physischen Namen `\\.\tape0`hinzugefügt.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)   
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
