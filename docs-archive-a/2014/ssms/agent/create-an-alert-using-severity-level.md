---
title: Erstellen einer Warnung mithilfe von Schweregraden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ee353129d60fe7fc8bed0eff279920d8d4ba640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719399"
---
# <a name="create-an-alert-using-severity-level"></a>Create an Alert Using Severity Level
  In diesem Thema wird beschrieben, wie Sie eine- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Warnung erstellen, die ausgelöst wird, wenn ein Ereignis mit einem bestimmten Schweregrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder auftritt [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine Warnung mithilfe von Schweregraden mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lässt sich das gesamte Warnungssystem auf einfache Weise mit einer grafischen Oberfläche verwalten. Dies ist die empfohlene Vorgehensweise, um eine Warnungsinfrastruktur zu konfigurieren.  
  
-   Ereignisse, die mit **xp_logevent** generiert werden, treten in der master-Datenbank auf. Daher wird von **xp_logevent** erst dann eine Warnung ausgegeben, wenn der **@database_name** -Wert für die Warnung den Wert **'master'** oder NULL hat.  
  
-   Bei den Schweregraden 19 bis 25 wird eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Meldung an das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows gesendet und eine Warnung ausgelöst. Ereignisse mit einem Schweregrad unter 19 lösen nur dann Warnungen aus, wenn Sie **sp_altermessage**, RAISERROR WITH LOG oder **xp_logevent** verwendet haben, um zu erzwingen, dass die Warnungen in das Windows-Anwendungsprotokoll geschrieben werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** die Prozedur **sp_add_alert**ausführen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-an-alert-using-severity-level"></a>So erstellen Sie eine Warnung mithilfe von Schweregraden  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie eine Warnung mithilfe des Schweregrads erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um **SQL Server-Agent**zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Warnungen** , und wählen Sie **Neue Warnung**aus.  
  
4.  Geben Sie im Dialogfeld **Neue Warnung** einen **Namen** für diese Warnung ein.  
  
5.  Klicken Sie in der Liste **Typ** auf **SQL Server-Ereigniswarnung**.  
  
6.  Klicken Sie in der Liste **Datenbankname**auf den **Datenbanknamen**, um die Warnung auf eine bestimmte Datenbank zu beschränken.  
  
7.  Klicken Sie unter **Warnungen werden ausgelöst basierend auf**auf **Schweregrad** , und wählen Sie dann den bestimmten Schweregrad aus, womit die Warnung ausgelöst wird.  
  
8.  Aktivieren Sie das Kontrollkästchen neben **Warnung auslösen, wenn eine Meldung Folgendes enthält** , um die Warnung auf eine bestimmte Zeichenfolge zu beschränken, und geben Sie dann ein Schlüsselwort oder Zeichenfolge für den **Meldungstext**ein. Es können maximal 100 Zeichen eingegeben werden.  
  
9. Klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-an-alert-using-severity-level"></a>So erstellen Sie eine Warnung mithilfe von Schweregraden  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_add_alert &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).  
  
  
