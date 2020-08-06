---
title: Starten, anhalten, anhalten, fortsetzen, Neustarten des Datenbank-Engine, SQL Server-Agent oder SQL Server-Browser Dienstanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723026"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a>Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers
  In diesem Thema wird beschrieben- und wie [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]- und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent oder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager- und der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]- und **net** commands from a command prompt- und [!INCLUDE[tsql](../../includes/tsql-md.md)]- und or PowerShell.  
  
-   **Vorbereitungen:**  
  
    -   [Was ist die Funktion dieser Dienste?](#Services)  
  
    -   [Weitere Informationen](#MoreInformation)  
  
    -   [Security](#Security)  
  
-   **Anweisungen mit:**  
  
    -   [SQL Server-Konfigurations-Manager](#SSCMProcedure)  
  
    -   [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [Net-Befehle von einem Eingabeaufforderungsfenster](#CommandPrompt)  
  
    -   [Transact-SQL](#TsqlProcedure)  
  
    -   [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a>Was sind der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Dienst, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst und der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten sind ausführbare Programme, die als Windows-Dienst ausgeführt werden. Programme, die als Windows-Dienst ausgeführt werden, lassen sich ohne Anzeige von Aktivitäten auf dem Computerbildschirm weiterhin ausführen.  
  
 **[!INCLUDE[ssDE](../../includes/ssde-md.md)]Leistungs**  
 Der ausführbare Prozess, der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]entspricht. [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann der Standardinstanz (eine pro Computer) oder einer von vielen benannten Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]entsprechen. Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um zu bestimmen, welche Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf dem Computer installiert werden. Die Standard Instanz (bei der Installation) wird als ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)** aufgelistet. Benannte Instanzen (bei der Installation) werden als ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)** aufgeführt. Standardmäßig [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird Express als ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLExpress)** installiert.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst**  
 Entspricht einem Windows-Dienst, der geplante administrative Tasks ausführt, die als Aufträge und Warnungen bezeichnet werden. Weitere Informationen finden Sie unter [SQL Server Agent](../../ssms/agent/sql-server-agent.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser Dienst**  
 Ein Windows-Dienst, der auf eingehende Anforderungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen lauscht und Clientinformationen zu den auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen bereitstellt. Eine einzelne Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdiensts wird für alle auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen verwendet.  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a>Weitere Informationen  
  
-   Durch das Anhalten des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensts wird verhindert, dass neue Benutzer eine Verbindung mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]herstellen. Benutzer, die bereits verbunden sind, können jedoch ihre Arbeit fortsetzen, bis die jeweilige Verbindung unterbrochen wird. Halten Sie den Dienst an, wenn Benutzer zuerst ihre Arbeit abschließen sollen, bevor Sie den Dienst beenden. Dadurch können sie Transaktionen abschließen, die gerade verarbeitet werden. Mit der Funktion zum Fortsetzen kann [!INCLUDE[ssDE](../../includes/ssde-md.md)] neue Verbindungen wieder zulassen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst kann nicht angehalten oder fortgesetzt werden.  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zeigen den aktuellen Dienststatus an. Dazu werden folgende Symbole verwendet.  
  
     **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**  
  
    -   Ein grüner Pfeil im Symbol neben dem Dienstnamen gibt an, dass der Dienst gestartet wurde.  
  
    -   Ein rotes Quadrat im Symbol neben dem Dienstnamen gibt an, dass der Dienst beendet wurde.  
  
    -   Zwei vertikale blaue Linien im Symbol neben dem Dienstnamen geben an, dass der Dienst angehalten wurde.  
  
    -   Beim Neustart von [!INCLUDE[ssDE](../../includes/ssde-md.md)]weist ein rotes Quadrat darauf hin, dass der Dienst beendet wurde. Ein grüner Pfeil gibt daraufhin an, dass der Dienst erfolgreich gestartet wurde.  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   Ein weißer Pfeil in einem grünen Kreis neben dem Dienstnamen gibt an, dass der Dienst gestartet wurde.  
  
    -   Ein weißes Quadrat in einem roten Kreis neben dem Dienstnamen gibt an, dass der Dienst beendet wurde.  
  
    -   Zwei vertikale weiße Linien in einem blauen Kreis neben dem Dienstnamen geben an, dass der Dienst angehalten wurde.  
  
-   Bei Verwendung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers oder bei Verwendung von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]sind nur mögliche Optionen verfügbar. Wurde der Dienst beispielsweise bereits gestartet, ist die Option **Start** nicht verfügbar.  
  
-   Im Fall der Ausführung auf einem Cluster lässt sich der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Dienst am besten mittels Clusterverwaltung verwalten.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der lokalen Administratorgruppe einen Dienst starten, beenden, anhalten, fortsetzen oder neu starten. Informationen dazu, wie Sie es Nichtadministratoren ermöglichen, Dienste zu verwalten, finden Sie unter [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349)(So erteilen Sie Benutzern die Berechtigung zum Verwalten von Diensten in Windows Server 2003). (Dieser Vorgang ist bei anderen Versionen von Windows ähnlich.)  
  
 Das Beenden [!INCLUDE[ssDE](../../includes/ssde-md.md)] von mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` Befehl erfordert die Mitgliedschaft in den festen Server Rollen **sysadmin** oder **serveradmin** und ist nicht übertragbar.  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a>Verwenden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>So wird eine [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Wenn das Dialogfeld **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Ja**.  
  
3.  Klicken Sie im linken Bereich des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers auf **SQL Server-Dienste**.  
  
4.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **SQL Server (MSSQLServer)** oder auf eine benannte Instanz, und klicken Sie anschließend auf **Starten**, **Beenden**, **Anhalten**, **Fortsetzen**oder **Neu starten**.  
  
5.  Klicken Sie auf **OK** , um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager zu schließen.  
  
> [!NOTE]  
>  Weitere Informationen zum Starten einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz mit Startoptionen finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](scm-services-configure-server-startup-options.md).  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a>So wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Instanz gestartet, beendet, angehalten, fortgesetzt oder neu gestartet  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Wenn das Dialogfeld **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Ja**.  
  
3.  Klicken Sie im linken Bereich des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers auf **SQL Server-Dienste**.  
  
4.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**oder ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLSERVER)** oder ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** für eine benannte Instanz, und klicken Sie dann auf **starten**, anhalten **Resume**, **Anhalten** **, fort**setzen oder **neu starten**.  
  
5.  Klicken Sie auf **OK** , um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager zu schließen.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent kann nicht angehalten werden.  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a>Verwenden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a>So wird eine [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her, klicken Sie mit der rechten Maustaste auf die zu startende [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz und anschließend auf **Starten**, **Beenden**, **Anhalten**, **Fortsetzen**oder **Neu starten**.  
  
     Klicken Sie alternativ im Bereich „Registrierte Server“ mit der rechten Maustaste auf die zu startende [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, zeigen Sie auf die Option **Dienstkontrolle**, und klicken Sie anschließend auf **Starten**, **Beenden**, **Anhalten**, **Fortsetzen**oder **Neu starten**.  
  
2.  Wenn das Dialogfeld **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Ja**.  
  
3.  Klicken Sie bei der Frage, ob die Aktion ausgeführt werden soll, auf **Ja**.  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a>So wird eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Instanz gestartet, beendet oder neu gestartet  
  
1.  Stellen Sie in Objekt-Explorer eine Verbindung mit der Instanz von her [!INCLUDE[ssDE](../../includes/ssde-md.md)] , klicken Sie mit der rechten Maustaste auf ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**, und klicken Sie dann auf **starten, starten**oder **neu starten**. **Stop**  
  
2.  Wenn das Dialogfeld **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Ja**.  
  
3.  Klicken Sie bei der Frage, ob die Aktion ausgeführt werden soll, auf **Ja**.  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a> Über das Eingabeaufforderungsfenster mit Net-Befehlen  
 Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste können mithilfe von **net**-Befehlen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows gestartet, beendet oder pausiert werden.  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a> So starten Sie die Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein:  
  
     **net start "SQL Server (MSSQLSERVER)"**  
  
     Oder  
  
     **net start MSSQLSERVER**  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> So starten Sie eine benannte Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein. Ersetzen Sie *\<instancename>* durch den Namen der Instanz, die Sie verwalten möchten.  
  
     **net start "SQL Server (** *Instanzname* **)"**  
  
     Oder  
  
     **net start MSSQL$** *Instanzname*  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a>So starten Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] mit Startoptionen  
  
-   Fügen Sie Startoptionen am Ende der Anweisung **net start "SQL Server (MSSQLSERVER)"** hinzu (durch ein Leerzeichen getrennt). Beim Starten mithilfe von **net start**wird ein Schrägstrich (/) anstelle eines Bindestriches (-) für die Startoptionen verwendet.  
  
     **net start "SQL Server (MSSQLSERVER)" /f /m**  
  
     Oder  
  
     **net start MSSQLSERVER /f /m**  
  
    > [!NOTE]  
    >  Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md).  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a>So starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent auf der Standard Instanz von[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein:  
  
     **net start "SQL Server-Agent (MSSQLSERVER)"**  
  
     Oder  
  
     **net start SQLSERVERAGENT**  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> So starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf einer benannten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein. Ersetzen Sie *Instanzname* durch den Namen der Instanz, die Sie verwalten möchten.  
  
     **net start "SQL Server Agent(** *Instanzname* **)"**  
  
     Oder  
  
     **net start SQLAgent$** *Instanzname*  
  
 Informationen zum Ausführen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents im ausführlichen Modus zur Problembehandlung finden Sie unter [sqlagent90 (Anwendung)](../../tools/sqlagent90-application.md).  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a> So starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser  
  
-   Geben Sie an einer Eingabeaufforderung einen der folgenden Befehle ein:  
  
     **net start "SQL Server Browser"**  
  
     Oder  
  
     **net start SQLBrowser**  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> So werden Dienste über das Eingabeaufforderungsfenster angehalten oder beendet  
  
-   Ändern Sie zum Anhalten oder Beenden von Diensten die Befehle wie folgt.  
  
    -   Um einen Dienst anzuhalten, ersetzen Sie **net start** durch **net pause**.  
  
    -   Um einen Dienst zu beenden, ersetzen Sie **net start** durch **net stop**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] lässt sich mit der `SHUTDOWN`-Anweisung beenden.  
  
#### <a name="to-stop-the-ssde-using-tsql"></a>So beenden Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   Um nach der vollständigen Ausführung von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen und gespeicherten Prozeduren [!INCLUDE[ssDE](../../includes/ssde-md.md)]zu beenden, führen Sie die folgende Anweisung aus.  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   Um [!INCLUDE[ssDE](../../includes/ssde-md.md)] sofort zu beenden, führen Sie die folgende Anweisung aus.  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 Weitere Informationen zur- `SHUTDOWN` Anweisung finden Sie unter [Shutdown &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Verwenden von PowerShell  
  
#### <a name="to-start-and-stop-ssde-services"></a>So starten und beenden Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienste  
  
1.  Starten Sie in einem Eingabeaufforderungsfenster [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell durch das Ausführen des folgenden Befehls.  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  Führen Sie an einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Eingabeaufforderung den folgenden Befehl aus. Ersetzen Sie `computername` durch den Namen des Computers.  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  Identifizieren Sie den Dienst, den Sie beenden oder starten möchten. Wählen Sie eine der folgenden Zeilen aus. Ersetzen Sie `instancename` durch den Namen der benannten Instanz.  
  
    -   Abrufen eines Verweises auf die Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   Abrufen eines Verweises auf die benannte Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   Abrufen eines Verweises auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf der Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   Abrufen eines Verweises auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf einer benannten Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   Abrufen eines Verweises auf den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst.  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  Starten Sie anhand des Beispiels den ausgewählten Dienst, und beenden Sie ihn anschließend.  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server mit minimaler Konfiguration starten](start-sql-server-with-minimal-configuration.md)   
 [Von den Editionen von SQL Server 2014 unterstützte Features](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
