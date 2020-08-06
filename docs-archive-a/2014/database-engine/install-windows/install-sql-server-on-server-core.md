---
title: Installieren von SQL Server 2014 auf Server Core | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2614c43bb763757db7db46b1c7a966221da96f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697145"
---
# <a name="install-sql-server-2014-on-server-core"></a>Installieren von SQL Server 2014 unter Server Core
  Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)]installieren. Dieses Thema enthält setupspezifische Details zum Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf Server Core.  
  
 Die Server Core-Installationsoption für das Betriebssystem [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)] stellt eine minimale Umgebung zum Ausführen von bestimmten Serverrollen bereit. Dies hilft, Wartung und Verwaltungsanforderungen und die Angriffsfläche für jene Serverrollen zu reduzieren. Weitere Informationen zu Server Core, wie unter implementiert [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] , finden Sie unter [Server Core für Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=202439) ( https://go.microsoft.com/fwlink/?LinkId=202439) . Weitere Informationen zur Implementierung von Server Core unter [!INCLUDE[win8srv](../../includes/win8srv-md.md)] finden Sie unter [Server Core für Windows Server 2012](https://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (https://msdn.microsoft.com/library/hh846323(VS.85).aspx) ).  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
|Anforderung|So führen Sie die Installation durch|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 2.0 SP2|In der Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 und [!INCLUDE[win8srv](../../includes/win8srv-md.md)]enthalten. Wenn nicht aktiviert, aktiviert Setup es standardmäßig.<br /><br /> Es ist nicht möglich, die Versionen 2.0, 3.0 und 3.5 parallel auf einem Computer auszuführen. Wenn Sie .NET Framework 3.5 SP1 installieren, erhalten Sie die 2.0- und 3.0-Ebenen automatisch.|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 3.5 SP1 Vollständiges Profil|In der Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 enthalten. Wenn nicht aktiviert, aktiviert Setup es standardmäßig.<br /><br /> Auf einem Computer mit einem Windows-Serverbetriebssystem müssen Sie .NET Framework 3.5 SP1 herunterladen und installieren, bevor Sie Setup ausführen, um von .NET 3.5 SP1 abhängige Komponenten installieren zu können.<br /><br /> Weitere Informationen zu den Empfehlungen und Anleitungen zum Abrufen und Aktivieren von .NET Framework 3,5 in finden Sie unter [!INCLUDE[win8srv](../../includes/win8srv-md.md)] [Überlegungen zur Bereitstellung von Microsoft .NET Framework 3,5](https://msdn.microsoft.com/library/windows/hardware/hh975396) ( https://msdn.microsoft.com/library/windows/hardware/hh975396) .|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core-Profil|Für alle Editionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] außer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]installiert Setup das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core-Profil als erforderliche Komponente.<br /><br /> Laden Sie für [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4 Server Core-Profil von [Microsoft .NET Framework 4 (eigenständiges Installationsprogramm) für Server Core ()](https://www.microsoft.com/download/details.aspx?id=17718) herunter, https://www.microsoft.com/download/details.aspx?id=17718) und installieren Sie es, bevor Sie mit dem Setup fortfahren.|  
|Windows Installer 4.5|Im Lieferumfang der Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 und [!INCLUDE[win8srv](../../includes/win8srv-md.md)]enthalten.|  
|Windows PowerShell 2.0|Im Lieferumfang der Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 und [!INCLUDE[win8srv](../../includes/win8srv-md.md)]enthalten.|  
  
##  <a name="supported-features"></a><a name="BK_SupportedFeatures"></a> Unterstützte Funktionen  
 In der folgenden Tabelle finden Sie die Funktionen, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] bei einer Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 und [!INCLUDE[win8srv](../../includes/win8srv-md.md)]unterstützt werden.  
  
|Funktion|Unterstützt|  
|-------------|---------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienste|Ja|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replikation|Ja|  
|Volltextsuche|Ja|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Ja|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Nein|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Tools (SSDT)|Nein|  
|Konnektivität der Clienttools|Ja|  
|Integration Services Server<sup>[1]</sup>|Ja|  
|Clienttools-Abwärtskompatibilität|Nein|  
|Clienttools SDK|Nein|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation|Nein|  
|Verwaltungstools - Einfach|Nur Remote<sup>[2]</sup>|  
|Verwaltungstools – Vollständig|Nur Remote<sup>[2]</sup>|  
|Distributed Replay Controller|Nein|  
|Distributed Replay Client|Nur Remote<sup>[2]</sup>|  
|SQL Client Connectivity SDK|Ja|  
|Microsoft Sync Framework|Ja<sup>[3]</sup>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|Nein|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|Nein|  
  
 <sup>[1]</sup> Weitere Informationen zum neuen Integration Services-Server und dessen Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] finden Sie unter [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).  
  
 <sup>[2]</sup> Die Installation dieser Funktionen unter Server Core wird nicht unterstützt. Diese Komponenten können auf einem anderen Server, der nicht [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core aufweist, installiert und mit den auf Server Core installierten [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Diensten verbunden werden.  
  
 <sup>[3]</sup> Microsoft Sync Framework ist nicht im [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installationspaket enthalten. Sie können die geeignete Sync Framework-Version von diesem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=221788) herunterladen ( https://go.microsoft.com/fwlink/?LinkId=221788) Seite und auf einem Computer installieren, auf dem die Server Core-Installation von SP1 oder ausgeführt wird) [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] [!INCLUDE[win8srv](../../includes/win8srv-md.md)] .  
  
## <a name="supported-scenario-matrix"></a>Matrix unterstützter Szenarien  
 In der folgenden Tabelle wird die Matrix unterstützter Szenarien zum Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf einer Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 und [!INCLUDE[win8srv](../../includes/win8srv-md.md)]angezeigt.  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Editionen|Alle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 64-Bit-Editionen<sup>[1]</sup>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sprache|Alle Sprachen|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sprache auf Betriebssystem Sprache/Gebietsschema (Kombination)|ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf JPN (Japanisch) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf GER (Deutsch) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf CHS (Chinesisch-China) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf ARA (Arabisch (SA)) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf THA (Thai) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf TRK (Türkisch) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf pt-PT (Portugiesisch Portugal) Windows<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf ENG (Englisch) Windows|  
|Windows-Edition|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64-Bit x64 Datacenter<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64-Bit x64 Standard<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Data Center Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-Bit x64 Enterprise Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Standard Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-Bit x64 Web Server Core|  
  
 <sup>[1]</sup> Die Installation der 32-Bit-Version von- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Editionen wird auf Server Core nicht unterstützt.  
  
## <a name="upgrading"></a>Wird aktualisiert  
 In Server Core-Installationen werden Upgrades von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt.  
  
## <a name="installation"></a>Installation  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt kein Setup mit dem Installations-Assistenten unter dem Server Core-Betriebssystem. Beim Installieren unter Server Core unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup mithilfe des /Q-Parameters den vollständigen stillen Modus oder mithilfe des /QS-Parameters den einfachen stillen Modus. Weitere Informationen finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](install-sql-server-from-the-command-prompt.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] kann nicht parallel mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer installiert werden, auf dem [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core ausgeführt wird.  
  
 Unabhängig von der Installationsmethode ist es erforderlich, dass Sie den Softwarelizenzbedingungen als Einzelperson oder im Auftrag einer juristischen Person zustimmen, sofern die Verwendung der Software in keiner separaten Vereinbarung geregelt ist, z. B. einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Volumenlizenzvertrag oder einem Vertrag eines Drittanbieters mit einem ISV oder OEM.  
  
 Die Lizenzbedingungen werden in der Setup-Benutzeroberfläche angezeigt, damit Sie diese lesen und akzeptieren können. Unbeaufsichtigte Installationen (mit dem /Q-Parameter oder /QS-Parameter) müssen den /IACCEPTSQLSERVERLICENSETERMS-Parameter enthalten. Sie können die Lizenzbedingungen unter [Microsoft-Software-Lizenzbedingungen](https://go.microsoft.com/fwlink/?LinkId=148209)in einer separaten Kopie lesen.  
  
> [!NOTE]  
>  Abhängig davon, wie Sie die Software erworben haben (z. B. durch [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Volumenlizenzierung), unterliegt die Verwendung der Software möglicherweise zusätzlichen Bestimmungen.  
  
 Um bestimmte Funktionen zu installieren, verwenden Sie den /FEATURES-Parameter, und geben Sie die übergeordnete Funktion oder die Funktionswerte an. Weitere Informationen zu Funktionsparametern und ihrer Verwendung finden Sie in den folgenden Abschnitten.  
  
### <a name="feature-parameters"></a>Funktionsparameter  
  
|Funktionsparameter|BESCHREIBUNG|  
|-----------------------|-----------------|  
|SQLENGINE|Installiert nur [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|REPLIKATION|Installiert die Replikationskomponente und das [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|FULLTEXT|Installiert die FullText-Komponente und das [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|AS|Installiert alle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Komponenten.|  
|IS|Installiert alle [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Komponenten.|  
|CONN|Installiert die Konnektivitätskomponenten.|  
  
 Vergleichen Sie die folgenden Beispiele für die Verwendung von Funktionsparametern:  
  
|Parameter und Werte|BESCHREIBUNG|  
|--------------------------|-----------------|  
|/FEATURES=SQLEngine|Installiert nur [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|/FEATURES=SQLEngine,FullText|Installiert das [!INCLUDE[ssDE](../../includes/ssde-md.md)] und Volltext.|  
|/FEATURES=SQLEngine,Conn|Installiert [!INCLUDE[ssDE](../../includes/ssde-md.md)] und die Konnektivitätskomponenten.|  
|/FEATURES=SQLEngine,AS,IS,Conn|Installiert [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]und die Konnektivitätskomponenten.|  
  
### <a name="installation-options"></a>Installationsoptionen  
 Beim Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unter einem Server Core-Betriebssystem unterstützt das Setup die folgenden Installationsoptionen:  
  
1.  **Installation über die Befehlszeile**  
  
     Um bestimmte Funktionen über die Befehlszeilen-Installationsoption zu installieren, verwenden Sie den /FEATURES-Parameter und geben die übergeordnete Funktion oder die Funktionswerte an. Nachfolgend wird gezeigt, wie die Parameter in der Befehlszeile verwendet werden:  
  
    ```cmd
    setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  **Installation über die Konfigurationsdatei**  
  
     Setup unterstützt die Verwendung der Konfigurationsdatei nur über die Eingabeaufforderung. Die Konfigurationsdatei ist eine Textdatei mit der grundlegenden Struktur eines Parameters (Name/Wert-Paar) und einem beschreibenden Kommentar. Die an der Eingabeaufforderung angegebene Konfigurationsdatei sollte die Dateinamenerweiterung .INI haben. Nachfolgend finden Sie einige Beispiele für ConfigurationFile.INI:  
  
    -   Installieren von [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
         Im folgenden Beispiel wird gezeigt, wie eine neue eigenständige Instanz, die das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]einschließt, installiert wird:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"
        ```  
  
    -   Installieren von Konnektivitätskomponenten  
  
         Im folgenden Beispiel wird gezeigt, wie die Konnektivitätskomponenten installiert werden:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True
        ```  
  
    -   Installieren aller unterstützten Funktionen  
  
         Im folgenden Beispiel wird gezeigt, wie alle unterstützten Funktionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unter Server Core installiert werden:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     Die folgenden Beispiele zeigen, wie Sie das Setup mithilfe einer Konfigurationsdatei starten können.  
  
    -   Konfigurationsdatei  
  
         Im Folgenden finden Sie einige Beispiele für das Verwenden der Konfigurationsdatei:  
  
        -   Angeben der Konfigurationsdatei an der Eingabeaufforderung:  
  
        ```cmd
        setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   Angeben von Kennwörtern an der Eingabeaufforderung und nicht in der Konfigurationsdatei:  
  
        ```cmd
        setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   DefaultSetup.ini  
  
         Wenn sich die Datei „DefaultSetup.ini“ in den Ordnern „\x86“ und „\x64“ auf der Stammebene der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellmedien befindet, öffnen Sie die Datei „DefaultSetup.ini“, und fügen Sie der Datei den Parameter *Features* hinzu.  
  
         Wenn die Datei DefaultSetup.ini nicht vorhanden ist, können Sie sie erstellen und sie in die Ordner \x86 und \x64 auf der Stammebene der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quellmedien kopieren.  
  
## <a name="configuring-remote-access-of-ssnoversion-running-on-server-core"></a>Konfigurieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Remotezugriff bei einer Server Core-Installation  
 Führen Sie die unten beschriebenen Aktionen aus, um den Remotezugriff auf eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Instanz zu konfigurieren, die auf einer Server Core-Installation von [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)]ausgeführt wird.  
  
### <a name="enable-remote-connections-on-the-instance-of-ssnoversion"></a>Aktivieren von Remoteverbindungen auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Um Remoteverbindungen zu aktivieren, verwenden Sie SQLCMD.exe lokal, und führen Sie die folgenden Anweisungen für die Server Core-Instanz aus:  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-ssnoversion-browser-service"></a>Aktivieren und Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdiensts  
 Standardmäßig ist der Browserdienst deaktiviert.  Wenn er auf einer auf Server Core ausgeführten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deaktiviert ist, führen Sie den folgenden Befehl von der Befehlszeile aus, um ihn zu aktivieren:  
  
 `sc config SQLBROWSER start= auto`  
  
 Nachdem er aktiviert wurde, führen Sie den folgenden Befehl von der Befehlszeile aus, um den Dienst zu starten:  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a>Erstellen von Ausnahmen von Windows-Firewall  
 Um Ausnahmen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zugriff in der Windows-Firewall zu erstellen, führen Sie die in [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)angegebenen Schritte aus.  
  
### <a name="enable-tcpip-on-the-instance-of-ssnoversion"></a>Aktivieren von TCP/IP auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Das TCP/IP-Protokoll kann durch Windows PowerShell für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz auf Server Core aktiviert werden. Folgen Sie diesen Schritten:  
  
1.  Starten Sie den Task-Manager auf dem Computer, auf dem [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core ausgeführt wird.  
  
2.  Klicken Sie auf der Registerkarte **Anwendungen** auf **Neuer Task**.  
  
3.  Geben Sie im Dialogfeld **Neuen Task erstellen** in das Feld **Öffnen** den Wert **sqlps.exe** ein, und klicken Sie auf **OK**. Dadurch wird das ** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell** -Fenster geöffnet.  
  
4.  Führen Sie im Fenster **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell** das folgende Skript aus, um das TCP/IP-Protokoll zu aktivieren:  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = New-Object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a>Deinstallation  
 Nachdem Sie sich an einem Computer angemeldet haben, auf dem [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 oder [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core ausgeführt wird, haben Sie eine beschränkte Desktopumgebung mit einer Administratoreingabeaufforderung. Sie können die Deinstallation einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]mithilfe dieser Eingabeaufforderung initiieren. Um eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]zu deinstallieren, starten Sie die Deinstallation im vollständigen stillen Modus mit dem /Q-Parameter oder im stillen einfachen Modus mit dem /QS-Parameter von der Eingabeaufforderung aus. Der /QS-Parameter zeigt den Status durch die Benutzeroberfläche an, akzeptiert jedoch keine Eingabe. /Q gibt an, dass Setup ohne Benutzeroberfläche in einem stillen Modus ausgeführt wird.  
  
 So deinstallieren Sie eine vorhandene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```cmd
setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 Um eine benannte Instanz zu entfernen, geben Sie den Namen der Instanz an und nicht wie im vorhergehenden Beispiel "MSSQLSERVER".  
  
> [!WARNING]
>  Wenn Sie die Eingabeaufforderung unbeabsichtigt schließen, können Sie eine neue Eingabeaufforderung starten, indem Sie folgende Schritte ausführen:  
> 
>  1.  Drücken Sie STRG+UMSCHALT+ESC, um Task-Manager anzuzeigen.  
> 2.  Klicken Sie auf der Registerkarte **Anwendungen** auf **Neuer Task**.  
> 3.  Geben Sie im Dialogfeld **Neuen Task erstellen** im Feld **Öffnen** den Wert **cmd** ein, und [!INCLUDE[clickOK](../../includes/clickok-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von SQL Server 2014 mithilfe einer Konfigurationsdatei](install-sql-server-using-a-configuration-file.md)   
 [Installieren von SQL Server 2014 von der Eingabeaufforderung](install-sql-server-from-the-command-prompt.md)   
 [Von den-Editionen unterstützte Funktionen SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Start Anleitung für die Server Core-Installations Option](https://go.microsoft.com/fwlink/?LinkId=221422)   
 [Konfigurieren einer Server Core-Installation: Übersicht](https://go.microsoft.com/fwlink/?LinkId=221423)   
 [Failovercluster-Cmdlets in Windows PowerShell, aufgelistet nach Aufgaben Fokus](https://go.microsoft.com/fwlink/?LinkId=221419)   
 [Zuordnen von Cluster.exe-Befehlen zu Windows PowerShell-Cmdlets für Failovercluster](https://go.microsoft.com/fwlink/?LinkId=221421)  
