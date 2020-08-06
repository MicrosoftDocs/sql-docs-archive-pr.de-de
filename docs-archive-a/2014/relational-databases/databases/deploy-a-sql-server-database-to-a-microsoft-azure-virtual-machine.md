---
title: Bereitstellen einer SQL Server-Datenbank auf einem virtuellen Microsoft Azure-Computer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: d48c06db038a775811cba6705fbaf1d97a960f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721486"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Bereitstellen einer SQL Server-Datenbank auf einem virtuellen Microsoft Azure-Computer
  Verwenden Sie den Assistenten zum Bereitstellen **einer SQL Server Datenbank in einer Azure-VM** , um eine Datenbank von einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] in auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem virtuellen Azure-Computer (VM) bereitzustellen. Der Assistent führt eine vollständige Datenbanksicherung durch und kopiert somit immer das vollständige Datenbankschema und alle Daten einer SQL Server-Benutzerdatenbank. Der Assistent übernimmt außerdem die gesamte Azure-VM-Konfiguration, sodass keine Vorkonfiguration der VM erforderlich ist.  
  
 Sie können den Assistenten nicht für differenzielle Sicherungen verwenden, da der Assistent keine vorhandene Datenbank überschreibt, die denselben Datenbanknamen hat. Um eine vorhandene Datenbank auf der VM zu ersetzen, müssen Sie zuerst die vorhandene Datenbank löschen oder den Datenbanknamen ändern. Falls ein Namenskonflikt zwischen dem Datenbanknamen eines aktiven Bereitstellungsvorgangs und dem einer vorhandenen Datenbank auf der VM auftritt, schlägt der Assistent ein Namenssuffix für den Namen der bereitzustellenden Datenbank vor, sodass der Vorgang erfolgreich abgeschlossen werden kann.  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> Vorbereitungen  
 Für diesen Assistenten sind die folgenden Informationen und Konfigurationseinstellungen verfügbar sein:  
  
-   Die Microsoft-Konto Details, die Ihrem Azure-Abonnement zugeordnet sind.  
  
-   Ihr Azure-Veröffentlichungs Profil.  
  
    > [!CAUTION]  
    >  SQL Server unterstützt derzeit die Version 2.0 des Veröffentlichungsprofils. Weitere Informationen zum Herunterladen der unterstützten Version des Veröffentlichungsprofils finden Sie unter [Herunterladen des Veröffentlichungsprofils 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
-   Das Verwaltungs Zertifikat, das in Ihr Azure-Abonnement hochgeladen wurde.  
  
-   Das Verwaltungszertifikat wurde im persönlichen Zertifikatspeicher auf dem Computer gespeichert, auf dem der Assistent ausgeführt wird.  
  
-   Ein temporärer Speicherort muss für den Computer verfügbar sein, auf dem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank gehostet wird. Der temporäre Speicherort muss zudem auch für den Computer verfügbar sein, auf der der Assistent ausgeführt wird.  
  
-   Wenn Sie die Datenbank auf einer vorhandenen virtuellen Maschine bereitstellen, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das Abhören eines TCP/IP-Ports konfiguriert werden.  
  
-   Entweder für eine Azure-VM oder ein Katalog Image, das Sie für die Erstellung der VM verwenden möchten, muss die SQL Server konfiguriert Cloudadapter und ausgeführt werden.  
  
-   Sie müssen einen geöffneten Endpunkt für Ihre SQL Server Cloudadapter auf dem Azure-Gateway mit dem privaten Port 11435 konfigurieren.  
  
 Wenn Sie Ihre Datenbank in einer vorhandenen Azure-VM bereitstellen möchten, müssen Sie außerdem Folgendes bereitstellen:  
  
-   Der DNS-Name des Cloud-Diensts, der die VM hostet.  
  
-   Administrator-Anmeldeinformationen für die VM.  
  
-   Anmeldeinformationen mit Sicherungsoperatorprivilegien für die bereitzustellende Datenbank, aus der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Weitere Informationen zum Ausführen von SQL Server auf virtuellen Azure-Computern finden Sie unter [Vorbereiten der Migration zu SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx).  
  
 Auf Computern, auf denen ein Windows Server-Betriebssystem ausgeführt wird, müssen Sie zur Ausführung dieses Assistenten die folgenden Konfigurationseinstellungen vornehmen:  
  
-   Deaktivieren Sie die verstärkte Sicherheitskonfiguration: Wählen Sie „Server-Manager > Lokaler Server“, und geben Sie für „Verstärkte Sicherheitskonfiguration für Internet Explorer“ den Wert **AUS** an.  
  
-   Aktivieren Sie JavaScript: Internet Explorer > Internetoptionen > Sicherheit > Stufe anpassen > Skripting > Active Scripting: **Aktivieren**.  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> Einschränkungen  
 Die Datenbankgröße für diesen Vorgang ist auf 1 TB beschränkt.  
  
 Diese Bereitstellungsfunktion ist in SQL Server Management Studio für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]verfügbar.  
  
 Diese Bereitstellungsfunktion ist nur für die Verwendung mit Benutzerdatenbanken vorgesehen. Das Bereitstellen von Systemdatenbanken wird nicht unterstützt.  
  
 Die Bereitstellungsfunktion unterstützt keine gehosteten Dienste, die einer Affinitätsgruppe zugeordnet sind. Beispielsweise können Speicherkonten, die einer Affinitätsgruppe zugeordnet sind, nicht auf der Seite **Bereitstellungseinstellungen** dieses Assistenten nicht zur Verwendung ausgewählt werden.  
  
 Die SQL Server-Version auf dem virtuellen Computer muss gleich oder höher sein als die SQL Server-Version des Quellservers. SQL Server von Daten Bank Versionen, die mithilfe dieses Assistenten auf einer Azure-VM bereitgestellt werden können:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 SQL Server Daten Bank Versionen, die in einer Azure-VM ausgeführt werden, können bereitgestellt werden für:  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 Falls ein Namenskonflikt zwischen dem Datenbanknamen eines aktiven Bereitstellungsvorgangs und dem einer vorhandenen Datenbank auf der VM auftritt, schlägt der Assistent ein Namenssuffix für den Namen der bereitzustellenden Datenbank vor, sodass der Vorgang erfolgreich abgeschlossen werden kann.  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> Überlegungen zur Bereitstellung einer FILESTREAM-aktivierten Datenbank in einer Azure-VM  
 Beachten Sie die folgenden Richtlinien und Einschränkungen, wenn Sie Datenbanken bereitstellen, in denen BLOBs in FILESTREAM-Objekten gespeichert sind:  
  
-   Die Bereitstellungsfunktion kann eine FILESTREAM-aktivierte Datenbank nicht in einer neuen VM bereitstellen. Wenn FILESTREAM vor dem Ausführen des Assistenten in der VM nicht aktiviert wurde, schlägt der Vorgang zur Datenbankwiederherstellung fehl, und der Assistentenvorgang kann nicht erfolgreich abgeschlossen werden. Um eine Datenbank, die FILESTREAM verwendet, erfolgreich bereitzustellen, aktivieren Sie FILESTREAM in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf der Host-VM, bevor Sie den Assistenten starten. Weitere Informationen finden Sie unter [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).  
  
-   Wenn die Datenbank In-Memory OLTP verwendet, können Sie die Datenbank ohne Änderungen an der Datenbank in einer Azure-VM bereitstellen. Weitere Informationen finden Sie unter [In-Memory OLTP (Speicheroptimierung)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a>Überlegungen zur geografischen Verteilung von Assets  
 Beachten Sie, dass sich die folgenden Ressourcen in der gleichen geografischen Region befinden müssen:  
  
-   Clouddienst  
  
-   VM-Speicherort  
  
-   Datenträgerspeicherdienst  
  
 Wenn sich die oben genannten Ressourcen nicht in derselben Region befinden, kann der Assistent nicht erfolgreich abgeschlossen werden.  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a> Konfigurationseinstellungen des Assistenten  
 Verwenden Sie die folgenden Konfigurationsdetails, um die Einstellungen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankbereitstellung in einer Azure-VM zu ändern.  
  
-   **Standardpfad für die Konfigurationsdatei** – %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **Struktur der Konfigurationsdatei**  
  
    -   \<DeploymentSettings>  
  
        -   <OtherSettings  
  
            -   TraceLevel = "Debug"\<!-- Logging level -->  
  
            -   Backuppath = " \\ \\ [Servername] \\ [Volume] \\ "\<!-- The last used path for backup. Used as default in the wizard. -->  
  
            -   Cleanupdeaktiviert = false/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). -->  
  
        -   <publishprofile\<!-- The last used publish profile information. -->  
  
            -   Certificate = "12a34b567890123abcd4ef567a8"\<!-- The certificate for use in the wizard. -->  
  
            -   Abonnement = "1a2b34c5-67d8-90EF-ab12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. -->  
  
            -   Name = "mein Abonnement"\<!-- The name of the subscription. -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **Konfigurationsdateiwerte**  
  
###  <a name="permissions"></a><a name="permissions"></a> Berechtigungen  
 Die bereitzustellende Datenbank muss sich in einem normalen Status befinden. Außerdem muss das Benutzerkonto, über das der Assistent ausgeführt wird, Zugriff auf die Datenbank haben und über die Berechtigung verfügen, einen Sicherungsvorgang auszuführen.  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a>Verwenden des Assistenten zum Bereitstellen einer Datenbank auf Azure-VMS  
 **Gehen Sie folgendermaßen vor, um den Assistenten zu starten:**  
  
1.  Verbinden Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von SQL Server Management Studio mit der bereitzustellenden Datenbank.  
  
2.  Erweitern Sie im **Objekt-Explorer**den Instanznamen und dann den Knoten **Datenbanken** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, die Sie bereitstellen möchten, und wählen Sie **Tasks**und dann **Datenbank in Azure-VM bereitstellen...**  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite wird der Assistent zum Bereitstellen **einer SQL Server Datenbank in einer Azure-VM** beschrieben.  
  
 **Optionen**  
  
-   **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Einführungsseite in Zukunft nicht mehr angezeigt wird.  
  
-   Durch**Weiter** gelangen Sie zur Seite **Quelleinstellungen** .  
  
-   **Abbrechen** : bricht den Vorgang ab und schließt den Assistenten.  
  
-   **Hilfe** : Hiermit wird das MSDN-Hilfethema für den Assistenten gestartet.  
  
##  <a name="source-settings"></a><a name="Source_settings"></a>Quell Einstellungen  
 Verwenden Sie diese Seite, um eine Verbindung mit der Instanz von herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Datenbank hostet, die Sie der Azure-VM bereitstellen möchten. Außerdem geben Sie einen temporären Speicherort für Dateien an, die auf dem lokalen Computer gespeichert werden sollen, bevor Sie an Azure übertragen werden. Dies kann ein freigegebener Netzwerkspeicherort sein.  
  
 **Optionen**  
  
-   Klicken Sie auf **verbinden...** , und geben Sie dann Verbindungsdetails für die Instanz von an, die die bereit zustellende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank hostet.  
  
-   Wählen Sie in der Dropdownliste **Datenbank auswählen** diejenige Datenbank aus, die bereitgestellt werden soll.  
  
-   Geben Sie im Feld **andere Einstellungen** einen freigegebenen Ordner an, auf den der Azure-VM-Dienst zugreifen kann.  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a>Azure-Anmeldung  
 Verwenden Sie diese Seite, um eine Verbindung mit Azure herzustellen und Verwaltungs Zertifikate bereitzustellen oder Profildetails zu veröffentlichen.  
  
 **Optionen**  
  
-   **Verwaltungs Zertifikat** : Verwenden Sie diese Option, um ein Zertifikat aus dem lokalen Zertifikat Speicher anzugeben, das mit dem Verwaltungs Zertifikat von Azure übereinstimmt.  
  
-   **Veröffentlichungs Profil** : Verwenden Sie diese Option, wenn Sie bereits ein Veröffentlichungs Profil auf Ihren Computer heruntergeladen haben.  
  
-   **Anmelden** : Verwenden Sie diese Option, um sich mit einer Microsoft-Konto, z. b. einer Live ID oder einem Hotmail-Konto, bei Azure anzumelden, um ein neues Verwaltungs Zertifikat zu generieren und herunterzuladen. Beachten Sie, dass die Anzahl von Zertifikaten pro Abonnement beschränkt ist.  
  
-   **Abonnement** : Wählen Sie Ihre Azure-Abonnement-ID aus dem lokalen Zertifikat Speicher oder einem Veröffentlichungs Profil aus, geben Sie Sie ein, oder fügen Sie Sie ein.  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a>Seite mit Bereitstellungs Einstellungen  
 Auf dieser Seite können Sie den Zielserver angeben sowie Details zur neuen Datenbank bereitstellen.  
  
 **Optionen**  
  
-   **Virtueller Azure-Computer** : Geben Sie Details für die VM an, die die SQL Server-Datenbank hostet:  
  
-   **Name des clouddiensts** : Geben Sie den Namen des Diensts an, der die VM hostet. Um einen neuen Clouddienst zu erstellen, geben Sie einen Namen für den neuen Clouddienst an.  
  
-   **Name des virtuellen** Computers: Geben Sie den Namen des virtuellen Computers an, auf dem die SQL Server Datenbank gehostet wird. Um einen neuen virtuellen Azure-Computer zu erstellen, geben Sie einen Namen für den neuen virtuellen Computer an.  
  
-   **Einstellungen** : Verwenden Sie die Schaltfläche Einstellungen, um einen neuen virtuellen Computer zum Hosten der SQL Server Datenbank zu erstellen. Wenn Sie eine vorhandene VM verwenden, werden die angegebenen Informationen verwendet, um Ihre Anmeldeinformationen zu authentifizieren.  
  
-   **Speicherkonto** : Wählen Sie in der Dropdown Liste das Speicherkonto aus. Um ein neues Speicherkonto zu erstellen, geben Sie einen Namen für das neue Konto an. Beachten Sie, dass Speicherkonten, die einer Affinitätsgruppe zugeordnet sind, nicht in der Dropdownliste verfügbar sind.  
  
-   **Zieldatenbank** : Geben Sie Details für die Zieldatenbank an.  
  
-   **Server Verbindung** : Verbindungsdetails für den Server.  
  
-   **Datenbank** : Geben Sie den Namen einer neuen Datenbank an, oder bestätigen Sie Sie. Wenn der Datenbankname auf der SQL Server-Zielinstanz bereits vorhanden ist, wird empfohlen, einen anderen Datenbanknamen anzugeben.  
  
##  <a name="summary-page"></a><a name="Summary"></a> Seite "Zusammenfassung"  
 Auf dieser Seite können Sie die für den Vorgang angegebenen Einstellungen überprüfen. Klicken Sie auf **Fertig stellen**, um den Bereitstellungsvorgang mithilfe der angegebenen Einstellungen abzuschließen. Klicken Sie auf **Abbrechen**, um den Bereitstellungsvorgang abzubrechen und den Assistenten zu beenden.  
  
 Möglicherweise sind manuelle Schritte erforderlich, um Daten Bank Details in der SQL Server-Datenbank auf der Azure-VM bereitzustellen. Diese Schritte werden detailliert für Sie beschriebenen.  
  
##  <a name="results-page"></a><a name="Results"></a>Seite "Ergebnisse"  
 Auf dieser Seite wird angegeben, ob der Bereitstellungsvorgang erfolgreich war oder ob dabei Fehler auftraten, dabei werden die Ergebnisse jeder Aktion angezeigt. Für alle Aktionen, die fehlerhaft waren, wird dies in der Spalte **Ergebnis** entsprechend angezeigt. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 Klicken Sie auf **Fertig stellen**, und beenden Sie den Assistenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cloudadapter für SQL Server](../../database-engine/cloud-adapter-for-sql-server.md)   
 [Datenbank-Lebenszyklus Verwaltung](../database-lifecycle-management.md)   
 [Exportieren einer Datenebenenanwendung](../data-tier-applications/export-a-data-tier-application.md)   
 [Importieren einer BacPac-Datei zum Erstellen einer neuen Benutzerdatenbank](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Sichern und Wiederherstellen von Azure SQL-Datenbanken](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [SQL Server Bereitstellung in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx)   
 [Bereit für die Migration zu SQL Server auf Azure-Virtuellen Computern](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
