---
title: Einrichten eines Masterservers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617356"
---
# <a name="make-a-master-server"></a>Make a Master Server
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Masterserver einrichten.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Einrichten eines Masterservers mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Verteilte Aufträge mit Schritten, die einem Proxy zugeordnet sind, werden im Kontext des Proxykontos auf dem Zielserver ausgeführt. Stellen Sie sicher, dass die folgenden Bedingungen erfüllt sind, da andernfalls einem Proxy zugeordnete Auftragsschritte nicht vom Masterserver auf den Zielserver heruntergeladen werden:  
  
-   Der Registrierungs Unterschlüssel für den Master Server **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \SQL Server agent\allowprotoadedjobstomatchproxyname** (REG_DWORD) ist auf 1 (true) festgelegt. Dieser Unterschlüssel ist standardmäßig auf 0 (false) festgelegt.  
  
-   Auf dem Zielserver ist ein Proxykonto vorhanden, das den gleichen Namen wie das Proxykonto des Masterservers hat, unter dem der Auftragsschritt ausgeführt wird.  
  
 Falls bei Auftragsschritten, die Proxykonten verwenden, beim Herunterladen vom Masterserver auf den Zielserver ein Fehler auftritt, können Sie die **error_message** -Spalte in der **sysdownloadlist** -Tabelle der **msdb** -Datenbank auf die folgenden Fehlermeldungen überprüfen:  
  
-   "Für den Auftragsschritt ist ein Proxykonto erforderlich, das Proxyabgleichen ist auf dem Zielserver aber deaktiviert."  
  
     Um diesen Fehler zu beheben, legen Sie den Registrierungsunterschlüssel **AllowDownloadedJobsToMatchProxyName** auf 1 fest.  
  
-   "Proxy nicht gefunden."  
  
     Um diesen Fehler zu beheben, stellen Sie sicher, dass auf dem Zielserver ein Proxykonto vorhanden ist, das den gleichen Namen wie das Proxykonto des Masterservers hat, unter dem der Auftragsschritt ausgeführt wird.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Berechtigungen zur Ausführung dieser Prozedur erhalten standardmäßig Mitglieder der festen Serverrolle `sysadmin`.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-make-a-master-server"></a>So richten Sie einen Masterserver ein  
  
1.  Stellen Sie in **Objekt-Explorer** eine Verbindung mit einer Instanz von her [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserveradministration**, und klicken Sie dann auf **Als Masterserver einrichten**. Der **Masterserver-Assistent** führt Sie durch die Schritte zum Einrichten eines Masterservers und Hinzufügen eines Zielservers.  
  
3.  Konfigurieren Sie auf der Seite **Masterserveroperator** einen Operator, damit der Masterserver Benachrichtigungen per E-Mail oder mittels Pager an Operatoren sendet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zum Senden von E-Mails konfiguriert werden. Um Operatoren die Benachrichtigungen mithilfe von **NET SEND**zu senden, muss auf dem Server mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent der Messenger-Dienst ausgeführt werden.  
  
     **E-Mail Adresse**  
     Legt die E-Mail-Adresse des Operators fest.  
  
     **Pageradresse**  
     Legt die Pager-E-Mail-Adresse des Operators fest.  
  
     **NET SEND-Adresse**  
     Legt die **NET SEND** -Adresse des Operators fest.  
  
4.  Wählen Sie auf der Seite **Zielserver** Zielserver für den Masterserver aus.  
  
     **Registrierte Server**  
     Listet die in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] registrierten Server auf, die noch nicht als Zielserver festgelegt wurden.  
  
     **Zielserver**  
     Listet die Server auf, die Zielserver sind.  
  
     **>**  
     Verschiebt den ausgewählten Server in die Liste mit den Zielservern.  
  
     **>>**  
     Verschiebt alle Server auf die Zielserverliste.  
  
     **<**  
     Entfernt den ausgewählten Server aus der Liste mit den Zielservern.  
  
     **<<**  
     Entfernt alle Server von der Zielserverliste.  
  
     **Verbindung hinzufügen**  
     Fügt der Zielserverliste einen Server hinzu, ohne diesen zu registrieren.  
  
     **Connection**  
     Ändert die Verbindungseigenschaften der ausgewählten Server.  
  
5.  Geben Sie auf der Seite **Masterserver-Anmeldeinformationen** an, ob für den Zielserver ein neuer Anmeldename erstellt werden soll, und weisen Sie ihm ggf. Rechte für den Masterserver zu.  
  
     **Bei Bedarf eine neue Anmeldung erstellen und ihr Rechte für MSX zuweisen**  
     Erstellt eine neue Anmeldung auf dem Zielserver, sofern die angegebene Anmeldung noch nicht vorhanden ist.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-make-a-master-server"></a>So richten Sie einen Masterserver ein  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel wird der aktuelle Server auf dem Masterserver "AdventureWorks1" eingetragen. Der Speicherort für den aktuellen Server ist "Building 21, Room 309, Rack 5".  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 Weitere Informationen finden Sie unter [sp_msx_enlist &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)   
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)  
  
  
