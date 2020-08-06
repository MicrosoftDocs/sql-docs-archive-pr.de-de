---
title: Ändern des Dienst Start Kontos für SQL Server (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c14c1756ac66c4a377271a13e61a307e53ac1ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697153"
---
# <a name="change-the-service-startup-account-for-sql-server-sql-server-configuration-manager"></a>Ändern des Dienststartkontos für SQL Server (SQL Server-Konfigurations-Manager)
  In diesem Thema wird die Verwendung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Managers zum Ändern der Startoptionen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste und zum Ändern der von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendeten Dienstkonten beschrieben. in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder PowerShell beschrieben. Weitere Informationen zum Auswählen eines geeigneten Dienstkontos finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](configure-windows-service-accounts-and-permissions.md).  
  
> [!IMPORTANT]  
>  Wenn Sie das Dienststartkonto für den [!INCLUDE[ssDE](../../includes/ssde-md.md)] - und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ändern, muss der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]) neu gestartet werden, damit die Änderung wirksam wird. Beim Neustart des Diensts stehen sämtliche dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zugeordneten Datenbanken erst dann wieder zur Verfügung, wenn der Dienst erfolgreich neu gestartet wird. Wenn Sie das Dienststartkonto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ändern müssen, sollten Sie dies während regelmäßig geplanter Wartungen vornehmen oder wenn die Datenbank offline geschaltet werden kann, ohne dass dabei die Ausführung täglicher Vorgänge unterbrochen wird.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Gruppierte Server  
  
     Die Änderung des Dienstkontos für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss über den aktiven Knoten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clusters ausgeführt werden.  
  
     Bei Ausführung unter Windows Server 2008 (in einer nicht dem Standard entsprechenden Konfiguration mit Domänengruppen) ist zum Ändern des Dienstkontos für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager erforderlich, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuhalten, indem die Ressourcengruppen offline geschaltet werden.  
  
-   SKU-Upgrade ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] auf andere SKU als Express)  
  
     Während der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] -Installation wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst für die Verwendung des Netzwerkdienstkontos konfiguriert. Dieser wird jedoch deaktiviert. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager kann das dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst zugewiesene Konto ändern, jedoch kann der Dienst nicht aktiviert oder gestartet werden. Nach einem SKU-Upgrade von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] auf eine andere SKU als Express wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst nicht automatisch aktiviert. Dieser kann stattdessen bei Bedarf aktiviert werden, indem im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager der Dienststartmodus auf "Manuell" oder "Automatisch" festgelegt wird.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a>So ändern Sie das Dienststartkonto für SQL Server  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          Um Configuration Manager zu öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , geben Sie auf der **Start Seite**SQLServerManager12. msc (für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ) ein. Ersetzen Sie für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl. Durch Klicken auf SQLServerManager12.msc wird der Konfigurations-Manager geöffnet. Um die Configuration Manager an die Start Seite oder Task Leiste anzuheften, klicken Sie mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf **Datei Speicherort öffnen**. Klicken Sie im Windows-Datei-Explorer mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf am **Anfang anheften** oder **an Taskleiste**anheften  
    > -   **Windows 8**:  
    >          Um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager im Charm **Suchen** unter **apps**zu öffnen, geben Sie **SQLServerManager \<version> . msc** ein, z `SQLServerManager12.msc` . b., und drücken Sie dann die **Eingabe**Taste.  
  
2.  Klicken Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf **SQL Server-Dienste**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, dessen Dienststartkonto Sie ändern möchten, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Eigenschaften von SQL Server \<***instancename***>** auf die Registerkarte **Anmelden**, und wählen Sie einen Kontotyp mit **Anmelden als** aus.  
  
5.  Klicken Sie nach Auswahl des neuen Dienststartkontos auf **OK**.  
  
     In einem Meldungsfenster werden Sie gefragt, ob Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst neu starten möchten.  
  
6.  Klicken Sie auf **Ja**, und schließen Sie dann den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](start-stop-pause-resume-restart-sql-server-services.md)   
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
