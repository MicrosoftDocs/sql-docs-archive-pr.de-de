---
title: Bereitstellen einer Datenebenenanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploydacwizard.updateconfiguration.f1
- sql12.swb.deploydacwizard.selectdac.f1
- sql12.swb.deploydacwizard.deploydac.f1
- sql12.swb.deploydacwizard.introduction.f1
- sql12.swb.deploydacwizard.summary.f1
helpviewer_keywords:
- Deploy data-tier application
- deploy DAC
- data-tier application [SQL Server], deploy
- How to [DAC], deploy
- wizard [DAC], deploy
ms.assetid: c117af35-aa53-44a5-8034-fa8715dc735f
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd4a09eed946863064728fd8c62230121ad3d403
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723921"
---
# <a name="deploy-a-data-tier-application"></a>Bereitstellen einer Datenebenenanwendung
  Mithilfe eines Assistenten oder eines PowerShell-Skripts können Sie eine Datenebenenanwendung (DAC) von einem DAC-Paket für eine vorhandene [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz bereitstellen. Beim Bereitstellungsprozess wird eine DAC-Instanz registriert, indem die DAC-Definition in der **msdb** -Systemdatenbank (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]) gespeichert und eine Datenbank erstellt wird, die anschließend mit allen in der DAC definierten Datenbankobjekten aufgefüllt wird.  
  
-   **Vorbereitungen:**  [SQL Server-Hilfsprogramm](#SQLUtility), [Datenbankoptionen und -einstellungen](#DBOptSettings), [Einschränkungen](#LimitationsRestrictions), [Voraussetzungen](#Prerequisites), [Sicherheit](#Security), [Berechtigungen](#Permissions)  
  
-   **Bereitstellen einer DAC mit:**  [Assistent zum Bereitstellen von Datenebenenanwendungen](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> Vorbereitungen  
 Dasselbe DAC-Paket kann mehrmals für eine einzelne [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz bereitgestellt werden, die Bereitstellungen müssen jedoch einzeln ausgeführt werden. Der für die einzelnen Bereitstellungen angegebene DAC-Instanzname muss innerhalb der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]eindeutig sein.  
  
###  <a name="sql-server-utility"></a><a name="SQLUtility"></a>SQL Server-Hilfsprogramm  
 Beim Bereitstellen einer DAC in einer verwalteten Instanz der Datenbank-Engine wird die bereitgestellte DAC in das SQL Server-Hilfsprogramm integriert, wenn der Hilfsprogramm-Sammlungssatz das nächste Mal von der Instanz an den Steuerungspunkt für das Hilfsprogramm gesendet wird. Die DAC ist dann im Knoten **Bereitgestellte Datenebenenanwendungen** im [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Hilfsprogramm-Explorer**von** vorhanden und wird auf der Detailseite **Bereitgestellte Datenebenenanwendungen** aufgeführt.  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a>Daten Bankoptionen und-Einstellungen  
 Die während der Bereitstellung erstellte Datenbank verfügt standardmäßig über alle Standardeinstellungen der CREATE DATABASE-Anweisung mit folgenden Ausnahmen:  
  
-   Für Datenbanksortierung und Kompatibilitätsgrad werden die im DAC-Paket definierten Werte festgelegt. Ein aus einem Datenbankprojekt in SQL Server Developer Tools erstelltes DAC-Paket verwendet die im Datenbankprojekt festgelegten Werte. Ein aus einer vorhandenen Datenbank extrahiertes Paket verwendet die Werte aus der ursprünglichen Datenbank.  
  
-   Sie können einige der Datenbankeinstellungen, z. B. Datenbanknamen und Dateipfade, auf der Seite **Konfiguration aktualisieren** anpassen. Beim Bereitstellen auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]können Sie die Dateipfade nicht festlegen.  
  
 Einige Datenbankoptionen, z. B. TRUSTWORTHY, DB_CHAINING und HONOR_BROKER_PRIORITY, können nicht im Rahmen des Bereitstellungsprozesses angepasst werden. Physische Eigenschaften, z. B. die Anzahl der Dateigruppen oder die Anzahl und Größe der Dateien, können nicht im Rahmen des Bereitstellungsprozesses geändert werden. Nachdem die Bereitstellung abgeschlossen wurde, können Sie die ALTER DATABASE-Anweisung, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]oder PowerShell für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, um die Datenbank individuell anzupassen.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Eine DAC kann für [!INCLUDE[ssSDS](../../includes/sssds-md.md)]bereitgestellt werden, oder für eine Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] , die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 oder höher ausführt. Wenn Sie eine DAC mit einer späteren Version erstellen, enthält die DAC möglicherweise Objekte, die von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]nicht unterstützt werden. Sie können diese DACs nicht auf Instanzen von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]bereitstellen.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Das Bereitstellen eines DAC-Pakets aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche Pakete können schädlichen Code enthalten, der möglicherweise unbeabsichtigten Transact-SQL-Code ausführt oder Fehler verursacht, indem er das Schema ändert. Bevor Sie ein Paket aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, entpacken Sie die DAC, und untersuchen Sie den Code, z. B. gespeicherte Prozeduren oder sonstigen benutzerdefinierten Code. Weitere Informationen zum Ausführen dieser Tests finden Sie unter [Validate a DAC Package](validate-a-dac-package.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Zur Erhöhung der Sicherheit werden die Anmeldenamen für die SQL Server-Authentifizierung ohne Kennwort in einem DAC-Paket gespeichert. Sobald das Paket bereitgestellt oder aktualisiert wird, wird der Anmeldename als deaktivierter Anmeldename mit einem generierten Kennwort erstellt. Um die Anmeldenamen zu aktivieren, melden Sie sich unter einem Anmeldenamen an, der über die ALTER ANY LOGIN-Berechtigung verfügt, und verwenden ALTER LOGIN, um den Anmeldenamen zu aktivieren und ein neues Kennwort zuzuweisen, das dem Benutzer mitgeteilt werden kann. Dies ist für Anmeldenamen der Windows-Authentifizierung nicht erforderlich, da die zugehörigen Kennwörter nicht von SQL Server verwaltet werden.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Eine DAC kann nur von Mitgliedern der festen Serverrollen **sysadmin** oder **serveradmin** bereitgestellt werden bzw. unter Verwendung von Anmeldenamen aus der festen Serverrolle **dbcreator** , die über ALTER ANY-LOGIN-Berechtigungen verfügen. Außerdem kann das integrierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemadministratorkonto mit der Bezeichnung **sa** zum Bereitstellen einer DAC verwendet werden. Um eine DAC mit Anmeldungen bei [!INCLUDE[ssSDS](../../includes/sssds-md.md)] bereitstellen zu können, müssen Sie Mitglied der Rollen "loginmanager" oder "serveradmin" sein. Um eine DAC ohne Anmeldenamen in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] bereitstellen zu können, müssen Sie Mitglied der Rollen "dbmanager" oder "serveradmin" sein.  
  
##  <a name="using-the-deploy-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a>Verwenden des Assistenten zum Bereitstellen von Datenebenenanwendungen  
 **So stellen Sie eine DAC mithilfe eines Assistenten bereit**  
  
1.  Erweitern Sie im **Objekt-Explorer**den Knoten für die Instanz, für die Sie die DAC bereitstellen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken** , und wählen Sie dann **Datenebenenanwendung** bereitstellen aus.  
  
3.  Bearbeiten Sie die Dialogfenster des Assistenten:  
  
    -   [Seite "Einführung"](#Introduction)  
  
    -   [Seite "DAC-Paket auswählen"](#Select_dac_package)  
  
    -   [Seite "Richtlinie überprüfen"](#Review_policy)  
  
    -   [Seite "Konfiguration aktualisieren"](#Update_configuration)  
  
    -   [Seite "Zusammenfassung"](#Summary)  
  
    -   [Seite "Bereitstellen"](#Deploy)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite werden die Schritte zum Bereitstellen einer Datenebenenanwendung beschrieben.  
  
 **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Seite in Zukunft nicht mehr angezeigt wird.  
  
 **Weiter >**:Geht zur Seite **DAC-Paket auswählen** über.  
  
 **Abbrechen**: Beendet den Assistenten, ohne eine DAC bereitzustellen.  
  
##  <a name="select-dac-package-page"></a><a name="Select_dac_package"></a>Seite "DAC-Paket auswählen"  
 Verwenden Sie diese Seite, um das DAC-Paket anzugeben, das die bereitzustellende Datenebenenanwendung enthält. Die Seite durchläuft drei Statusübergänge.  
  
### <a name="select-the-dac-package"></a>Auswählen des DAC-Pakets  
 Verwenden Sie die Seite in ihrem Ausgangszustand, um das bereitzustellende DAC-Paket auszuwählen. Das DAC-Paket muss eine gültige DAC-Paketdatei sein und die Erweiterung .dacpac aufweisen.  
  
 **DAC-Paket** : Geben Sie den Pfad und den Dateinamen des DAC-Pakets an, das die bereitzustellende Datenebenenanwendung enthält. Sie können die Schaltfläche **Durchsuchen** rechts neben dem Feld auswählen, um zum Speicherort des DAC-Pakets zu wechseln.  
  
 **Anwendungsname** : Ein schreibgeschütztes Feld mit dem DAC-Namen, der beim Erstellen oder Extrahieren der DAC aus einer Datenbank zugewiesen wurde.  
  
 **Version** : Ein schreibgeschütztes Feld mit der Version, die beim Erstellen oder Extrahieren der DAC aus einer Datenbank zugewiesen wurde.  
  
 **Beschreibung**: Ein schreibgeschütztes Feld mit der Beschreibung, die beim Erstellen oder Extrahieren der DAC aus einer Datenbank erstellt wurde.  
  
 ** \< Previous** : kehrt zur **Einführungs** Seite zurück.  
  
 **Weiter >**: Zeigt eine Statusanzeige an, da der Assistent bestätigt, dass es sich bei der ausgewählten Datei um ein gültiges DAC-Paket handelt.  
  
 **Abbrechen** : Beendet den Assistenten, ohne die DAC bereitzustellen.  
  
### <a name="validating-the-dac-package"></a>Überprüfen des DAC-Pakets  
 Zeigt eine Statusanzeige an, da der Assistent bestätigt, dass es sich bei der ausgewählten Datei um ein gültiges DAC-Paket handelt. Wenn das DAC-Paket überprüft wird, geht der Assistent zur abschließenden Version der Seite **Paket auswählen** über. Dort können Sie die Ergebnisse der Überprüfung einsehen. Wenn die Datei kein gültiges DAC-Paket ist, verbleibt der Assistent auf der Seite **DAC-Paket auswählen**. Wählen Sie entweder ein anderes gültiges DAC-Paket aus, oder brechen Sie den Assistenten ab, und generieren Sie ein neues DAC-Paket.  
  
 **Der DAC-Inhalt wird überprüft**: Die Statusanzeige, die den aktuellen Status des Überprüfungsprozesses angibt.  
  
 ** \< Previous** : kehrt zum Ausgangszustand der Seite **Paket auswählen** zurück.  
  
 **Weiter >**: Geht zur abschließenden Version der Seite **Paket auswählen** über.  
  
 **Abbrechen** : Beendet den Assistenten, ohne die DAC bereitzustellen.  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a>Richtlinie überprüfen  
 Verwenden Sie diese Seite, um die Auswertungsergebnisse der DAC-Richtlinie zur Serverauswahl zu überprüfen, wenn die DAC über eine Richtlinie verfügt. Die DAC-Richtlinie zur Serverauswahl ist optional und wird der DAC während der Erstellung in Visual Studio zugewiesen. Die Richtlinie verwendet Facets für die Richtlinie zur Serverauswahl, um Bedingungen anzugeben, die eine [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz zum Hosten der DAC erfüllen sollte.  
  
 **Auswertungsergebnisse der Richtlinienbedingungen** : Ein schreibgeschützter Bericht, der anzeigt, ob die Bedingungen der Richtlinie zur DAC-Bereitstellung erfüllt sind. Die Auswertungsergebnisse für die einzelnen Bedingungen werden in einer separaten Zeile angezeigt.  
  
 Beim Bereitstellen von DAC auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ergeben die folgenden Serverauswahlrichtlinien immer false: Betriebssystemversion, Sprache, Named Pipes aktiviert, Plattform und tcp aktiviert.  
  
 **Richtlinienverletzungen ignorieren** : Verwenden Sie dieses Kontrollkästchen, um mit der Bereitstellung fortzufahren, wenn eine oder mehrere Richtlinienbedingungen nicht erfüllt wurden. Aktivieren Sie diese Option nur, wenn Sie sicher sind, dass keine der fehlgeschlagenen Bedingungen die erfolgreiche Ausführung der DAC verhindert.  
  
 Zurück ** \< : kehrt** zur Seite **Paket auswählen** zurück.  
  
 **Weiter >**: Geht zur Seite **Konfiguration aktualisieren** über.  
  
 **Abbrechen** : Beendet den Assistenten, ohne die DAC bereitzustellen.  
  
##  <a name="update-configuration-page"></a><a name="Update_configuration"></a>Seite "Konfiguration aktualisieren"  
 Verwenden Sie diese Seite, um die Namen der bereitgestellten DAC-Instanz und der bei der Bereitstellung erstellten Datenbank anzugeben und die Datenbankoptionen festzulegen.  
  
 **Datenbankname** : Geben Sie den Namen der Datenbank an, die von der Bereitstellung erstellt werden soll. Standardmäßig wird der Name der Quelldatenbank verwendet, aus der die DAC extrahiert wurde. Der Name muss innerhalb der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz eindeutig sein und den Regeln für [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Bezeichner entsprechen.  
  
 Wenn Sie den Datenbanknamen ändern, werden die Namen der Datendatei und der Protokolldateien entsprechend dem neuen Wert angepasst.  
  
 Der Datenbankname wird auch als Name der DAC-Instanz verwendet. Der Instanzname wird im Knoten der DAC unter dem Knoten **Datenebenenanwendungen** im **Objekt-Explorer**oder im Knoten **Bereitgestellte Datenebenenanwendungen** im **Hilfsprogramm-Explorer**angezeigt.  
  
 Die folgenden Optionen gelten nicht für [!INCLUDE[ssSDS](../../includes/sssds-md.md)]und werden beim Bereitstellen auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]nicht angezeigt.  
  
 **Standardspeicherort für Datenbankdatei verwenden** : Wählen Sie diese Option aus, um die Datenbankdaten- und Protokolldateien am Standardspeicherort der Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]s abzulegen. Die Dateinamen werden anhand des Datenbanknamens erstellt.  
  
 **Datenbankdateien angeben** : Wählen Sie diese Option aus, um einen anderen Speicherort oder Namen für die Daten- und Protokolldateien anzugeben.  
  
 **Pfad und Name der Datendatei** : Geben Sie den vollständigen Pfad- und Dateinamen für die Datendatei an. Das Feld wird mit dem Standardpfad und -dateinamen aufgefüllt. Bearbeiten Sie die Zeichenfolge im Feld, um den Standardeintrag zu ändern, oder verwenden Sie die Schaltfläche Durchsuchen, um zum Ordner zu navigieren, in dem die Datendatei abgelegt werden soll.  
  
 **Pfad und Name der Protokolldatei** : Geben Sie den vollständigen Pfad- und Dateinamen für die Protokolldatei an. Das Feld wird mit dem Standardpfad und -dateinamen aufgefüllt. Bearbeiten Sie die Zeichenfolge im Feld, um den Standardeintrag zu ändern, oder verwenden Sie die Schaltfläche **Durchsuchen** , um zum Ordner zu navigieren, in dem die Protokolldatei abgelegt werden soll.  
  
 ** \< ** Zurück: kehrt zur Seite **DAC-Paket auswählen** zurück.  
  
 **Weiter >**: Geht zur Seite **Zusammenfassung** über.  
  
 **Abbrechen** : Beendet den Assistenten, ohne die DAC bereitzustellen.  
  
##  <a name="summary-page"></a><a name="Summary"></a> Seite "Zusammenfassung"  
 Verwenden Sie diese Seite, um die Aktionen zu überprüfen, die der Assistent beim Bereitstellen der DAC ausführt.  
  
 **Die folgenden Einstellungen werden zur Bereitstellung der DAC verwendet.** – Überprüfen Sie die angezeigten Informationen darauf, ob die ergriffenen Maßnahmen richtig sind. Im Fenster werden das ausgewählte DAC-Paket und der für die bereitgestellte DAC-Instanz ausgewählte Name angezeigt. Im Fenster werden auch die Einstellungen angezeigt, die beim Erstellen der mit der DAC verbundenen Datenbank verwendet werden.  
  
 Zurück ** \< : wechselt** zur Seite " **Update Konfiguration** ", um Ihre Auswahl zu ändern.  
  
 **Weiter >**: Stellt die DAC bereit und zeigt die Ergebnisse auf der Seite **DAC bereitstellen** an.  
  
 **Abbrechen** : Beendet den Assistenten, ohne die DAC bereitzustellen.  
  
##  <a name="deploy-page"></a><a name="Deploy"></a>Seite bereitstellen  
 Auf dieser Seite wird angegeben, ob der Bereitstellungsvorgang erfolgreich war oder fehlgeschlagen ist.  
  
 **DAC wird bereitgestellt** : Gibt an, ob die Aktionen zur Bereitstellung der DAC erfolgreich oder fehlerhaft waren. Überprüfen Sie die Informationen, um zu bestimmen, ob die einzelnen Aktionen erfolgreich waren oder fehlgeschlagen sind. Für alle Aktionen, die fehlerhaft waren, ist in der Spalte **Ergebnis** ein Link enthalten. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 **Bericht speichern** : Klicken Sie auf diese Schaltfläche, um den Bereitstellungsbericht in einer HTML-Datei zu speichern. In der Datei ist der Status der einzelnen Aktionen aufgeführt, einschließlich aller durch die Aktionen generierten Fehler. Der Standardordner ist der Ordner "SQL Server Management Studio\DAC Packages" im Ordner "Dokumente" unter Ihrem Windows-Konto.  
  
 **Fertig stellen** – Beendet den Assistenten.  
  
##  <a name="using-powershell"></a><a name="DeployDACPowerShell"></a> Verwenden von PowerShell  
 **Bereitstellen einer DAC mithilfe der Install()-Methode in einem PowerShell-Skript**  
  
1.  Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, auf der Sie die DAC bereitstellen möchten.  
  
2.  Öffnen Sie ein `ServerConnection`-Objekt, und stellen Sie eine Verbindung mit derselben Instanz her.  
  
3.  Laden Sie die DAC-Paketdatei mithilfe von `System.IO.File`.  
  
4.  Verwenden Sie `add_DacActionStarted` und `add_DacActionFinished`, um die DAC-Bereitstellungsereignisse zu abonnieren.  
  
5.  Legen Sie die `DatabaseDeploymentProperties` fest.  
  
6.  Verwenden Sie die `DacStore.Install`-Methode zum Bereitstellen der DAC.  
  
7.  Schließen Sie den Dateidatenstrom, der zum Lesen der DAC-Paketdatei verwendet wurde.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird eine DAC mit dem Namen "MyApplication" auf einer Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]bereitgestellt, wobei eine DAC-Definition aus einem MyApplication.dacpac-Paket verwendet wird.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC deployment events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Deploy the DAC and create the database.  
$dacName  = "MyApplication"  
$evaluateTSPolicy = $true  
$deployProperties = New-Object Microsoft.SqlServer.Management.Dac.DatabaseDeploymentProperties($serverconnection,$dacName)  
$dacstore.Install($dacType, $deployProperties, $evaluateTSPolicy)  
$fileStream.Close()  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](data-tier-applications.md)   
 [Extrahieren einer DAC aus einer Datenbank](extract-a-dac-from-a-database.md)   
 [Datenbankbezeichner](../databases/database-identifiers.md)  
