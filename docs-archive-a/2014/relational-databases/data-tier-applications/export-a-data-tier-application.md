---
title: Exportieren einer Datenebenenanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportdac.settings.f1
- sql12.swb. exportdac.settings.f1
- sql12.swb.exportdac.welcome.f1
- sql12.swb. exportdac.summary.f1
- sql12.swb.exportdac.progress.f1
- sql12.swb.exportdac.summary.f1
- sql12.swb.exportdac.results.f1
- sql12.swb. exportdac.results.f1
helpviewer_keywords:
- How to [DAC], export
- wizard [DAC], export
- export DAC
- data-tier application [SQL Server], export
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5e1bbfc5c38dee5e7f29598086d87b680880641
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620987"
---
# <a name="export-a-data-tier-application"></a>Exportieren einer Datenebenenanwendung
  Beim Exportieren einer bereitgestellten Datenebenenanwendung (DAC) oder einer Datenbank wird eine Exportdatei erstellt, die sowohl die Definitionen der Objekte in der Datenbank als auch alle in den Tabellen enthaltenen Daten enthält. Die Exportdatei kann dann in eine andere Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]oder in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]importiert werden. Die Export-/Importvorgänge können kombiniert werden, um eine DAC zwischen Instanzen zu migrieren oder eine logische Sicherung zu erstellen oder um eine lokale Kopie einer in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] bereitgestellten Datenbank zu erstellen.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Beim Exportvorgang wird in zwei Phasen eine DAC-Exportdatei erstellt.  
  
1.  Beim Export wird eine DAC-Definition in der Exportdatei (BACPAC-Datei) erstellt. Dieser Vorgang entspricht dem Erstellen einer DAC-Definition in einer DAC-Paketdatei durch einen DAC-Auszug. Die exportierte DAC-Definition enthält alle Objekte in der aktuellen Datenbank. Wenn der Exportvorgang für die ursprünglich von einer DAC bereitgestellten Datenbank ausgeführt wird und nach der Bereitstellung Änderungen direkt an der Datenbank vorgenommen wurden, entspricht die exportierte Definition dem Objektsatz in der Datenbank und nicht dem in der ursprünglichen DAC festgelegten Inhalt.  
  
2.  Beim Export werden die Daten per Massenkopieren aus allen Tabellen in der Datenbank kopiert und in die Exportdatei integriert.  
  
 Beim Exportvorgang wird die DAC-Version auf 1.0.0.0 und die DAC-Beschreibung in der Exportdatei auf eine leere Zeichenfolge festgelegt. Wurde die Datenbank von einer DAC bereitgestellt, enthält die DAC-Definition in der Exportdatei den Namen der ursprünglichen DAC. Andernfalls wird der DAC-Name auf den Datenbanknamen festgelegt.  
  

###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Eine DAC oder Datenbank kann nur aus einer Datenbank in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]oder [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) oder höher exportiert werden.  
  
 Sie können keine Datenbank exportieren, die über in einer DAC nicht unterstützte Objekte oder eigenständige Benutzer verfügt. Weitere Informationen zu den in einer DAC unterstützten Objekttypen finden Sie unter [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).  
  
###  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Zum Exportieren einer DAC sind mindestens die ALTER ANY LOGIN-Berechtigung und die VIEW DEFINITION-Berechtigung im Datenbankbereich sowie SELECT-Berechtigungen für **sys.sql_expression_dependencies**erforderlich. Zum Exportieren einer DAC sind nur Mitglieder der festen Serverrolle "securityadmin" berechtigt, die ebenfalls Mitglieder der festen Datenbankrolle "database_owner" in der Datenbank sind, aus der die DAC exportiert wird. Mitglieder der festen Serverrolle „sysadmin“ oder des integrierten SQL Server-Systemadministratorkontos **sa** sind ebenfalls berechtigt, eine DAC zu exportieren.  
  
##  <a name="using-the-export-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a>Verwenden des Assistenten zum Exportieren von Datenebenenanwendungen  
 **So exportieren Sie eine DAC mithilfe eines Assistenten**  
  
1.  Stellen Sie entweder lokal oder in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine Verbindung zu einer Instanz von [!INCLUDE[ssSDS](../../includes/sssds-md.md)]her.  
  
2.  Erweitern Sie im **Objekt-Explorer** den Knoten für die Instanz, von der aus Sie die DAC exportieren möchten.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Datenbanknamen.  
  
4.  Klicken Sie auf **Tasks**, und wählen Sie dann **Exportieren von Datenebenenanwendungen** aus.  
  
5.  Bearbeiten Sie die Dialogfenster des Assistenten:  
  
    -   [Seite "Einführung"](#Introduction)  
  
    -   [Exporteinstellungen (Seite)](#Export_settings)  
  
    -   [Überprüfung (Seite)](#Validation)  
  
    -   [Seite "Zusammenfassung"](#Summary)  
  
    -   [Seite "Status"](#Progress)  
  
    -   [Ergebnisse (Seite)](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite werden die Schritte für den Assistenten zum Exportieren von Datenebenenanwendungen beschrieben.  
  
 **Optionen**  
  
 **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Einführungsseite in Zukunft nicht mehr angezeigt wird.  
  
 **Weiter** – Geht zur Seite **DAC-Paket auswählen** über.  
  
 **Abbrechen** : bricht den Vorgang ab und schließt den Assistenten.  
  
##  <a name="export-settings-page"></a><a name="Export_settings"></a>Seite "Einstellungen exportieren"  
 Auf dieser Seite können Sie den Ort angeben, wo die BACPAC-Datei erstellt werden soll.  
  
-   **Auf lokalem Datenträger speichern** – Erstellt eine BACPAC-Datei in einem Verzeichnis auf dem lokalen Computer. Klicken Sie auf **Durchsuchen...**, um den lokalen Computer zu durchsuchen oder um den Pfad im bereitgestellten Feld anzugeben. Der Pfadname muss einen Dateinamen und die Erweiterung BACPAC enthalten.  
  
-   **In Azure speichern** – Erstellt eine BACPAC-Datei in einem Azure-Container. Sie müssen eine Verbindung mit einem Azure-Container herstellen, um diese Option zu überprüfen. Beachten Sie, dass diese Option auch erfordert, dass Sie ein lokales Verzeichnis für die temporäre Datei angeben. Beachten Sie, dass die temporäre Datei am angegebenen Speicherort erstellt wird und dort verbleibt, nachdem der Vorgang abgeschlossen wurde.  
  
 Um eine Teilmenge von zu exportierenden Tabellen anzugeben, verwenden Sie die Option **Erweitert** .  
  
##  <a name="validation-page"></a><a name="Validation"></a>Validierungs Seite  
 Verwenden Sie die Überprüfungsseite, um sämtliche Probleme zu überprüfen, die den Vorgang blockieren. Beheben Sie zum Fortfahren die Blockierungsprobleme, und klicken Sie dann auf **Überprüfung erneut ausführen** , um sicherzustellen, dass die Überprüfung erfolgreich ist.  
  
 Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.  
  
##  <a name="summary-page"></a><a name="Summary"></a> Seite "Zusammenfassung"  
 Verwenden Sie diese Seite, um die angegebene Quelle und die Zieleinstellungen für den Vorgang zu überprüfen. Klicken Sie auf **Fertig stellen**, um den Exportvorgang mithilfe der angegebenen Einstellungen abzuschließen. Klicken Sie auf **Abbrechen**, um den Exportvorgang abzubrechen und um den Assistenten zu beenden.  
  
##  <a name="progress-page"></a><a name="Progress"></a> Status (Seite)  
 Auf dieser Seite wird eine Statusanzeige angezeigt, die den Status des Vorgangs anzeigt. Klicken Sie auf die Option **Details anzeigen** , um ausführliche Informationen anzuzeigen.  
  
##  <a name="results-page"></a><a name="Results"></a>Seite "Ergebnisse"  
 Auf dieser Seite wird angegeben, ob der Exportvorgang erfolgreich war oder ob dabei Fehler auftraten, dabei werden die Ergebnisse jeder Aktion angezeigt. Für alle Aktionen, die fehlerhaft waren, ist in der Spalte **Ergebnis** ein Link enthalten. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 Klicken Sie auf **Fertig** stellen, um den Assistenten zu schließen.  
  
##  <a name="using-a-net-framework-application"></a><a name="NetApp"></a>Verwenden einer .NET Framework-Anwendung  
 **So exportieren Sie eine DAC mithilfe der Export()-Methode in einer .NET Framework-Anwendung**  
  
 Laden Sie zum Anzeigen eines Codebeispiels die DAC-Beispielanwendung unter [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)herunter.  
  
1.  Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, die die zu exportierende DAC enthält.  
  
2.  Öffnen Sie ein `ServerConnection`-Objekt, und stellen Sie eine Verbindung mit derselben Instanz her.  
  
3.  Exportieren Sie die DAC mithilfe der `Export`-Methode des `Microsoft.SqlServer.Management.Dac.DacStore`-Typs. Geben Sie den Namen der zu exportierenden DAC sowie den Pfad zum Ordner an, in dem die Exportdatei abgelegt werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenebenenanwendungen](data-tier-applications.md)   
 [Extrahieren einer DAC aus einer Datenbank](extract-a-dac-from-a-database.md)  
  
  
