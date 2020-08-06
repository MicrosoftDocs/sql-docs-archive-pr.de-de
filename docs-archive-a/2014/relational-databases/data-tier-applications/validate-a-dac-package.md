---
title: Überprüfen eines DAC-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078c7bfeef2ff8636243f4853c03de252c7b9289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622165"
---
# <a name="validate-a-dac-package"></a>Überprüfen eines DAC-Pakets
  Es wird empfohlen, den Inhalt eines DAC-Pakets vor der Bereitstellung in der Produktionsumgebung sowie die Upgradeaktionen vor dem Aktualisieren einer vorhandenen DAC zu überprüfen. Dies gilt insbesondere für die Bereitstellung von Paketen, die nicht im Unternehmen entwickelt wurden.  
  
1.  **Vorbereitungen:**  [Voraussetzungen](#Prerequisites)  
  
2.  **So aktualisieren Sie eine DAC:**  [Anzeigen des Inhalts einer DAC](#ViewDACContents), [Anzeigen der Datenbankänderungen](#ViewDBChanges), [Anzeigen der Upgradeaktionen](#ViewUpgradeActions), [Vergleichen von DACs](#CompareDACs)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Das Bereitstellen eines DAC-Pakets aus unbekannten oder nicht vertrauenswürdigen Quellen wird nicht empfohlen. Solche DACs können schädlichen Code enthalten, der möglicherweise unbeabsichtigten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code ausführt oder Fehler verursacht, indem er das Schema ändert. Bevor Sie eine DAC aus einer unbekannten oder nicht vertrauenswürdigen Quelle verwenden, stellen Sie sie auf einer isolierten [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Testinstanz bereit, führen [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) für die Datenbank aus und überprüfen außerdem den Code, z. B. gespeicherte Prozeduren oder sonstigen benutzerdefinierten Code.  
  
##  <a name="view-the-contents-of-a-dac"></a><a name="ViewDACContents"></a> Anzeigen des Inhalts einer DAC  
 Es gibt zwei Vorgehensweisen, um den Inhalt eines Datenebenenanwendungs-Pakets (DAC) anzuzeigen. Sie können das DAC-Paket in ein DAC-Projekt in SQL Server Developer Tools importieren. Der Inhalt des Pakets kann in einen Ordner entpackt werden.  
  
 **Anzeigen einer DAC in SQL Server Developer Tools**  
  
1.  Öffnen Sie das Menü **Datei**, und klicken Sie auf **Neu** und dann auf **Projekt...** .  
  
2.  Wählen Sie die **SQL Server** -Projektvorlage aus, und geben Sie **Name**, **Speicherort**und **Projektmappenname**ein.  
  
3.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
4.  Aktivieren Sie auf der Registerkarte **Projekteinstellungen** im Abschnitt **Ausgabetypen** das Kontrollkästchen **Datenebenenanwendung (DACPAC-Datei)** , und schließen Sie dann das Dialogfeld mit den Eigenschaften.  
  
5.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Datenebenenanwendung importieren** aus.  
  
6.  Öffnen Sie mit dem **Projektmappen-Explorer** alle Dateien in der DAC, z. B. die Richtlinie zur Serverauswahl und die vor und nach der Bereitstellung auszuführenden Skripts.  
  
7.  Überprüfen Sie alle Objekte im Schema mithilfe der **Schemaansicht** , insbesondere auch den Code in Objekten wie Funktionen oder gespeicherten Prozeduren.  
  
 **Anzeigen einer DAC in einem Ordner**  
  
-   Entpacken Sie das DAC-Paket in einen Ordner anhand der Anweisungen unter [Unpack a DAC Package](unpack-a-dac-package.md).  
  
-   Zeigen Sie den Inhalt der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts an, indem Sie sie im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]öffnen.  
  
-   Zeigen Sie den Inhalt der Textdateien in Tools an, z. B. im Editor.  
  
##  <a name="view-database-changes"></a><a name="ViewDBChanges"></a> Anzeigen von Datenbankänderungen  
 Nach der Bereitstellung der aktuellen Version einer DAC in der Produktionsumgebung wurden möglicherweise Änderungen direkt an der zugeordneten Datenbank vorgenommen, die einen Konflikt mit dem in einer neuen Version der DAC definierten Schema verursachen. Überprüfen Sie vor dem Upgrade auf eine neue Version der DAC, ob solche Änderungen an der Datenbank vorgenommen wurden.  
  
 **Anzeigen von Datenbankänderungen mit einem Assistenten**  
  
1.  Führen Sie den **Assistenten zum Aktualisieren von Datenebenenanwendungen** aus, und geben Sie die derzeit bereitgestellte DAC und das DAC-Paket mit der neuen Version der DAC an.  
  
2.  Überprüfen Sie auf der Seite **Änderung erkennen** den Bericht der an der Datenbank vorgenommenen Änderungen.  
  
3.  Wählen Sie **Abbrechen** , wenn Sie das Upgrade nicht fortsetzen möchten.  
  
4.  Weitere Informationen zur Verwendung des Assistenten finden Sie unter [Upgrade einer Datenebenenanwendung](upgrade-a-data-tier-application.md).  
  
### <a name="view-database-changes-by-using-powershell"></a>Anzeigen von Datenbankänderungen mithilfe von PowerShell
  
1.  Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, die die anzuzeigende DAC enthält.  
  
2.  Öffnen Sie ein `ServerConnection`-Objekt, und stellen Sie eine Verbindung mit derselben Instanz her.  
  
3.  Gibt den DAC-Namen in einer Variablen an.  
  
4.  Rufen Sie mit der `GetDatabaseChanges()`-Methode ein `ChangeResults`-Objekt ab, und übergeben Sie das Objekt an eine Textdatei, um einen einfachen Bericht der neuen, gelöschten und geänderten Objekte zu generieren.  
  
### <a name="view-database-changes-example-powershell"></a>Anzeigen eines Beispiels für Datenbankänderungen (PowerShell)
  
 Im folgenden Beispiel werden alle Datenbankänderungen gemeldet, die in einer bereitgestellten DAC namens "MyApplicaiton" vorgenommen wurden.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="view-upgrade-actions"></a><a name="ViewUpgradeActions"></a> Anzeigen von Upgradeaktionen  
 Vor der Verwendung einer neuen Version eines DAC-Pakets zum Aktualisieren einer DAC, die aus einem früheren DAC-Paket bereitgestellt wurde, können Sie einen Bericht generieren, der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen enthält, die während des Upgrades ausgeführt werden, und die Anweisungen dann überprüfen.  
  
 **Melden von Upgradeaktionen mithilfe eines Assistenten**  
  
1.  Führen Sie den **Assistenten zum Aktualisieren von Datenebenenanwendungen** aus, und geben Sie die derzeit bereitgestellte DAC und das DAC-Paket mit der neuen Version der DAC an.  
  
2.  Überprüfen Sie auf der Seite **Zusammenfassung** den Bericht der Upgradeaktionen.  
  
3.  Wählen Sie **Abbrechen** , wenn Sie das Upgrade nicht fortsetzen möchten.  
  
4.  Weitere Informationen zur Verwendung des Assistenten finden Sie unter [Upgrade einer Datenebenenanwendung](upgrade-a-data-tier-application.md).  
  
 **Melden von Upgradeaktionen mithilfe von PowerShell**  
  
1.  Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, die die bereitgestellte DAC enthält.  
  
2.  Öffnen Sie ein `ServerConnection`-Objekt, und stellen Sie eine Verbindung mit derselben Instanz her.  
  
3.  Laden Sie die DAC-Paketdatei mithilfe von `System.IO.File`.  
  
4.  Gibt den DAC-Namen in einer Variablen an.  
  
5.  Rufen Sie mithilfe der `GetIncrementalUpgradeScript()`-Methode eine Liste der Transact-SQL-Anweisungen ab, die bei einem Upgrade ausgeführt werden würden, und übergeben Sie die Liste an eine Textdatei.  
  
6.  Schließen Sie den Dateidatenstrom, der zum Lesen der DAC-Paketdatei verwendet wurde.  
  
### <a name="view-upgrade-actions-example-powershell"></a>Anzeigen eines Beispiels für Upgradeaktionen (PowerShell)
  
 Im folgenden Beispiel werden die Transact-SQL-Anweisungen gemeldet, die zum Aktualisieren der DAC "MyApplicaiton" auf das in einer MyApplicationVNext.dacpac-Datei definierte Schema ausgeführt werden würde.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="compare-dacs"></a><a name="CompareDACs"></a>Vergleichen von DACs  
 Vor dem Aktualisieren einer DAC empfiehlt es sich, die Unterschiede in der Datenbank und in den Objekten auf Instanzebene zwischen der aktuellen und der neuen DAC zu vergleichen. Wenn Sie über keine Kopie des Pakets für die aktuelle DAC verfügen, können Sie ein Paket aus der aktuellen Datenbank extrahieren.  
  
 Wenn Sie beide DAC-Pakete in DAC-Projekte in SQL Server Developer Tools importieren, können Sie das Tool "Schemavergleich" verwenden, um die Unterschiede zwischen den beiden DACs zu analysieren.  
  
 Entpacken Sie alternativ die DACs in separate Ordner. Anschließend können Sie die Unterschiede mit einem Vergleichstool wie dem Hilfsprogramm "WinDiff" analysieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](data-tier-applications.md)   
 [Bereitstellen einer Datenebenenanwendung](deploy-a-data-tier-application.md)   
 [Aktualisieren einer Datenebenenanwendung](upgrade-a-data-tier-application.md)  
