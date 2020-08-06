---
title: Konfigurieren der Serverkonfigurationsoption „Startprozeduren suchen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbf46fc7476e6e879991cfe3f649fd5617f3275e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616167"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Startprozeduren suchen
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Startprozeduren suchen** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Sie können mithilfe der Option **Startprozeduren suchen** nach der automatischen Ausführung gespeicherter Prozeduren zum Startzeitpunkt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suchen. Wenn diese Option auf 1 festgelegt ist, sucht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nach allen automatisch ausgeführten gespeicherten Prozeduren, die auf dem Server definiert sind, und führt diese aus. Der Standardwert für **Startprozeduren suchen** ist „0“ (kein Scannen).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Startprozeduren suchen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Startprozeduren suchen“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Der Wert für diese Option kann mithilfe von **sp_configure**festgelegt werden. Er wird jedoch automatisch festgelegt, wenn Sie die gespeicherte Systemprozedur **sp_procoption**verwenden. Diese Prozedur wird verwendet, um gespeicherte Prozeduren als automatisch ausgeführte Prozeduren zu kennzeichnen oder die Kennzeichnung aufzuheben. Wird **sp_procoption** zum Kennzeichnen der ersten gespeicherten Prozedur als autoproc verwendet, wird für diese Option automatisch der Wert „1“ festgelegt. Wenn **sp_procoption** verwendet wird, um die Kennzeichnung der letzten gespeicherten Prozedur als autoproc aufzuheben, wird der Wert für diese Option automatisch auf „0“ festgelegt. Wenn Sie **sp_procoption** zum Kennzeichnen bzw. zum Aufheben von Kennzeichnungen verwenden und die Kennzeichnungen von autoprocs vor dem Löschen immer aufheben, ist es nicht notwendig, diese Option manuell festzulegen.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a>So konfigurieren Sie die Option "Startprozeduren suchen"  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Ändern Sie unter **Sonstiges**die Option **Startprozeduren suchen** in TRUE oder FALSE, indem Sie im Dropdown-Listenfeld den gewünschten Wert auswählen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a>So konfigurieren Sie die Option "Startprozeduren suchen"  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `scan for startup procs` auf `1`festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-scan-for-startup-procs-option"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Startprozeduren suchen“  
 Der Server muss neu gestartet werden, bevor die Einstellung wirksam werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [sp_procoption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
