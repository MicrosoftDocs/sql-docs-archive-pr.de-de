---
title: Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aa92296da81f984f260deace887c15f13443b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726021"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a>Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei (SQL Server)
  In diesem Thema wird beschrieben, wie Sie ein logisches Sicherungsmedium für eine Datenträgerdatei in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]definieren. Ein logisches Medium ist ein benutzerdefinierter Name, der auf ein bestimmtes, physisches Sicherungsmedium (Datenträgerdatei oder Bandlaufwerk) verweist.  Die Initialisierung des physischen Mediums erfolgt später, wenn eine Sicherung auf das Sicherungsmedium geschrieben wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So definieren Sie ein logisches Sicherungsmedium für eine Datenträgerdatei mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Der Name des logischen Mediums muss innerhalb der logischen Sicherungsmedien auf der Serverinstanz eindeutig sein. Sie können sich die vorhandenen logischen Mediennamen anzeigen lassen, indem Sie eine Abfrage für die [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) -Katalogsicht ausführen.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Als Sicherungsdatenträger sollte ein anderer Datenträger als für die Datenbankdaten und Protokolldatenträger verwendet werden. Nur so kann sichergestellt werden, dass Sie auch dann auf die Sicherungen zugreifen können, wenn die Daten- oder Protokolldatenträger ausfallen.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **diskadmin** .  
  
 Erfordert die Berechtigung zum Schreiben auf den Datenträger.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a>So definieren Sie ein logisches Sicherungsmedium für eine Datenträgerdatei  
  
1.  Klicken Sie nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Serverobjekte**, und klicken Sie dann mit der rechten Maustaste auf **Sicherungsmedien**.  
  
3.  Klicken Sie auf **Neues Sicherungsmedium**. Das Dialogfeld **Sicherungsmedium** wird geöffnet.  
  
4.  Geben Sie einen Mediennamen ein.  
  
5.  Klicken Sie zur Angabe des Ziels auf **Datei** , und geben Sie den vollständigen Dateipfad an.  
  
6.  Klicken Sie auf **OK**, um das neue Medium zu definieren.  
  
 Damit eine Sicherung auf dieses neue Medium erstellt werden kann, fügen Sie es dem Feld **Sichern auf:** im Dialogfeld **Datenbank sichern** (Seite **Allgemein**) hinzu. Weitere Informationen finden Sie unter [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a>So definieren Sie eine logische Sicherung für eine Datenträgerdatei  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie Sie [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) verwenden müssen, um ein logisches Sicherungsmedium für eine Datenträgerdatei zu definieren. Im folgenden Beispiel wird das Datenträgersicherungsmedium `mydiskdump`mit dem physischen Namen `c:\dump\dump1.bak`hinzugefügt.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)   
 [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
