---
title: Deinstallieren PowerPivot für SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3941a2f0-0d0c-4d1a-8618-7a6a7751beac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ca65a04578cbce2ed7eb2831068260d9f0e445a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617435"
---
# <a name="uninstall-powerpivot-for-sharepoint"></a>Deinstallieren von PowerPivot für SharePoint
  Die Deinstallation einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Installation ist ein Vorgang mit mehreren Schritten, der die Vorbereitung auf die Deinstallation, das Entfernen von Funktionen und Lösungen aus der Farm und das Entfernen von Programmdateien und Registrierungseinstellungen umfasst.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010  
  
 **In diesem Thema:**  
  
-   [Voraussetzungen](#prereq)  
  
-   [Schritt 1: Prüfliste vor der Deinstallation](#bkmk_before)  
  
-   [Schritt 2: Entfernen von Funktionen und Lösungen von SharePoint](#bkmk_remove)  
  
-   [Schritt 3: Ausführen des SQL Server-Setups zum Entfernen von Programmen vom lokalen Computer](#bkmk_uninstall)  
  
-   [Schritt 4: Deinstallieren des PowerPivot für SharePoint-Add-Ins](#bkmk_addin)  
  
-   [Schritt 5: Überprüfen der Deinstallation](#verify)  
  
-   [Schritt 6: Prüfliste nach der Deinstallation](#bkmk_post)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> Voraussetzungen  
  
-   Sie müssen ein SharePoint-Farmadministrator oder ein Dienstanwendungsadministrator sein, um Funktionen und Lösungen in der Farm zu deinstallieren.  
  
-   Sie müssen SQL Server-Systemadministrator und Mitglied der lokalen Administratorengruppe sein, wenn Sie auch die Datenbank-Engine deinstallieren.  
  
-   Sie müssen Analysis Services-Systemadministrator und Mitglied der lokalen Administratorengruppe sein, um Analysis Services und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]zu deinstallieren.  
  
##  <a name="step-1-pre-uninstall-checklist"></a><a name="bkmk_before"></a> Schritt 1: Prüfliste vor der Deinstallation  
 Der PowerPivot-Datenzugriff wird deaktiviert, sobald die Software, die die Abfrage- und -Datenverarbeitung unterstützt, aus der Farm entfernt wird. Als ersten Schritt sollten Sie die Dateien und Bibliotheken, die nicht mehr funktionsfähig sein werden, präventiv löschen. Auf diese Weise können Sie Fragen oder Bedenken hinsichtlich „fehlender Daten“ bereits vor der Deinstallation der Software klären.  
  
1.  Löschen Sie alle PowerPivot-Arbeitsmappen, -Dokumente und -Bibliotheken, die mit einer PowerPivot für SharePoint-Installation verknüpft sind. Weder die Bibliotheken noch die Dokumente sind nach der Deinstallation der Software funktionsfähig.  
  
    -   [Löschen des PowerPivot-Katalogs](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [Löschen einer PowerPivot-Datenfeedbibliothek](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
2.  Löschen Sie Excel-Arbeitsmappen oder Reporting Services-Berichte in den anderen Bibliotheken, die PowerPivot-Daten enthalten oder darauf verweisen.  
  
3.  Entfernen Sie jedes Webpart in einem PerformancePoint-Dashboard, das auf PowerPivot-Daten verweist.  
  
4.  Prüfen Sie die SharePoint-Berechtigungen für vorhandene Websites und Bibliotheken, um zu ermitteln, ob sie geändert werden müssen. Für einige PowerPivot-Datenzugriffsszenarien, insbesondere für den sekundären Datenzugriff auf PowerPivot-Daten in einer anderen Arbeitsmappe über eine URL-Verbindungszeichenfolge, sind Leseberechtigungen erforderlich. Dies ist eine höhere Berechtigungsstufe als die Anzeigeberechtigungen, die SharePoint-Benutzern, die nur eine Website besuchen, normalerweise zugeordnet werden. Wenn Sie keine Leseberechtigungen mehr benötigen, können Sie die Berechtigungen entsprechend herabstufen.  
  
5.  Optional können Sie die Dienste beenden und mehrere Tage warten, bevor Sie die Software deinstallieren. Dieser Schritt ist zur Deinstallation zwar nicht erforderlich, bietet aber die Möglichkeit, den Dienst temporär fortzusetzen. Dies ist nützlich, wenn Sie an Problemlösungen in Bezug auf die Datenmigration oder den Technologieaustausch arbeiten, die Sie ggf. übersehen haben.  
  
##  <a name="step-2-remove-features-and-solutions-from-sharepoint"></a><a name="bkmk_remove"></a> Schritt 2: Entfernen von Funktionen und Lösungen von SharePoint  
 Verwenden Sie das PowerPivot-Konfigurationstool, um PowerPivot-Dienste und -Anwendungen aus SharePoint zu entfernen.  
  
-   Sie müssen ein Farmadministrator, ein Serveradministrator auf der Analysis Services-Instanz und Mitglied der Rolle **db_owner** der Konfigurationsdatenbank der Farm sein.  
  
-   Verwenden Sie die für die genutzte SharePoint-Version geeignete Version des Konfigurationstools. Verwenden Sie keines der beiden Tools mit Installationen von [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
-   Überprüfen Sie, ob der SharePoint-Verwaltungsdienst ausgeführt wird.  
  
1.  **Ausführen des Konfigurationstools:** Beachten Sie, dass die Konfigurationstools nur dann aufgeführt werden, wenn [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf dem lokalen Server installiert ist. Zeigen Sie im Menü **Start** auf **Alle Programme**, klicken Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], auf **Konfigurationstools**und dann auf eine der folgenden Optionen:  
  
    -   **Konfiguration von PowerPivot für SharePoint 2013**  
  
    -   **Power Pivot-Konfigurations Tool**  
  
2.  Wählen Sie **Funktionen, Dienste, Anwendungen und Lösungen entfernen** aus, und klicken Sie dann auf **OK**.  
  
3.  Erweitern Sie optional das Fenster auf Vollbildgröße. Am unteren Rand des Fensters wird eine Schaltflächenleiste angezeigt, die die Befehle **Überprüfen**, **Ausführen**und **Beenden** enthält.  
  
4.  Überprüfen Sie alle Aktionen in der Taskliste, um nachzuvollziehen, was die einzelnen Aktionen bewirken.  
  
     Unter **PowerPivot Service-Anwendungen entfernen**haben Sie die Option, die der Dienstanwendung zugeordneten Anwendungsdaten zu löschen. Die Anwendungsdaten bilden eine SQL Server-Datenbank, die mit der Dienstanwendung zum Speichern von Datenaktualisierungszeitplänen, Datenbankinstanzinformationen, Verwendungsdaten und anderen von PowerPivot für SharePoint verwendeten Daten erstellt wurde. Benutzerdateien, z. B. PowerPivot-Arbeitsmappen, werden nicht gespeichert. Wenn Sie die Anwendungsdaten nicht aus einem bestimmten Grund speichern müssen (z. B. wenn auf Datenaktualisierung oder Datenzugriff bezogene Datenbeibehaltungsrichtlinien angewendet werden), können Sie die Anwendungsdatenbank löschen, ohne Dateien zu entfernen, die von SharePoint-Benutzern erstellt oder gespeichert wurden.  
  
     Wählen Sie zum Löschen der Datenbank **PowerPivot Service-Anwendungen entfernen** aus, und wählen Sie dann die Option zum Löschen der dieser Dienstanwendung zugeordneten Anwendungsdaten ****.  
  
5.  Überprüfen Sie optional ausführliche Informationen auf der Registerkarte **Ausgabe** oder auf der Registerkarte **Skript** .  
  
     Die Registerkarte "Ausgabe" ist eine Zusammenfassung der Aktionen, die vom Tool ausgeführt werden. Diese Informationen werden unter folgendem Protokolldateipfad gespeichert:  
  
     `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Log`  
  
     Die Registerkarte "Skript" enthält die PowerShell-Cmdlets oder verweist auf die PowerShell-Skriptdateien, die vom Tool ausgeführt werden.  
  
6.  Klicken Sie auf **Überprüfen** , um zu überprüfen, ob jede Aktion gültig ist. Wenn **Überprüfen** nicht verfügbar ist, bedeutet das, dass alle Aktionen für das System gültig sind.  
  
7.  Klicken Sie auf **Ausführen** , um alle Aktionen auszuführen, die für diesen Task gültig sind. **Ausführen** ist nur verfügbar, nachdem die Überprüfung erfolgreich war. Wenn Sie auf **Ausführen** klicken, wird die folgende Warnung angezeigt und erinnert Sie, dass Aktionen im Batchmodus verarbeitet werden: „Alle im Tool als gültig gekennzeichneten Konfigurationseinstellungen werden auf die SharePoint-Farm angewendet. Möchten Sie den Vorgang fortsetzen?“  
  
8.  Klicken Sie zum Fortsetzen des Vorgangs auf **Ja** .  
  
 **Problembehandlung:**  
  
 Im Konfigurationstool können Sie Fehlerinformationen für jede Aktion im Bereich Parameter anzeigen. Überprüfen Sie bei Problemen mit der Bereitstellung bzw. Aufheben der Bereitstellung, ob der SharePoint-Administrationsdienst gestartet wurde. Dieser Dienst führt die Zeitgeberaufträge aus, die Konfigurationsänderungen in einer Farm auslösen. Wird der Dienst nicht ausgeführt, tritt beim Bereitstellen oder Zurückziehen der Lösung ein Fehler auf. Persistente Fehler weisen darauf hin, dass sich bereits ein Auftrag zum Bereitstellen oder Zurückziehen in der Warteschlange befindet und weitere Aktionen des Konfigurationstools blockiert. Anhand des folgenden PowerShell-Befehls können Sie überprüfen, ob der Dienst ausgeführt wird.  
  
```powershell
Get-Service | Where {$_.displayname -like "*sharepoint* administration*"}  
```  
  
 Gehen Sie folgendermaßen vor, um einen Auftrag zum Bereitstellen oder Zurückziehen, der sich bereits in der Warteschlange befindet, zu suchen und zu entfernen:  
  
1.  Überprüfen Sie bei allen anderen Fehlern die ULS-Protokolle. Weitere Informationen finden Sie unter [Konfigurieren und Anzeigen von SharePoint-Protokolldateien und Diagnoseprotokollierung &#40;PowerPivot für SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging).  
  
2.  Starten Sie die SharePoint-Verwaltungsshell als Administrator, und führen Sie dann den folgenden Befehl aus, um Aufträge in der Warteschlange anzuzeigen:  
  
    ```cmd
    stsadm -o enumdeployments  
    ```  
  
3.  Überprüfen Sie vorhandene Bereitstellungen auf die folgenden Informationen: **Typ** ist "Zurückziehung" oder "Bereitstellung", **Datei** ist "powerpivotwebapp.wsp" oder "powerpivotfarm.wsp".  
  
4.  Kopieren Sie bei bereit Stellungen oder zurück Ziehungen im Zusammenhang mit Power Pivot-Lösungen den GUID-Wert für **JobID** , und fügen Sie ihn in den folgenden Befehl ein (verwenden Sie zum Kopieren der GUID die Befehle zum Markieren, kopieren und Einfügen im Bearbeitungs Menü der Shell):  
  
    ```cmd
    stsadm -o canceldeployment -id "<GUID>"  
    ```  
  
5.  Wiederholen Sie den Task im Konfigurationstool, indem Sie auf **Überprüfen** und **Ausführen**klicken.  
  
 Sie können alternativ Funktionen und Lösungen von der Farm mithilfe von PowerShell entfernen. Weitere Informationen finden Sie unter [PowerShell-Referenz für PowerPivot für SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).  
  
##  <a name="step-3-run-sql-server-setup-to-remove-programs-from-the-local-computer"></a><a name="bkmk_uninstall"></a> Schritt 3: Ausführen des SQL Server-Setups zum Entfernen von Programmen vom lokalen Computer  
 Programmdateien zu löschen erfordert, dass Sie SQL Server-Setup ausführen, um die Software zu deinstallieren. Durch das Deinstallieren werden die Dateien und die von Setup erstellten Registrierungseinträge entfernt. Sie können die Seite Programme und Funktionen verwenden, um die Software zu deinstallieren. Eine Installation von [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ist Teil einer SQL Server-Installation.  
  
 Sie können einen Teil einer Installation deinstallieren, ohne dabei andere SQL Server-Instanzen (oder Funktionen in der gleichen Instanz) zu beeinflussen, die bereits installiert sind. Sie können z. B. PowerPivot für SharePoint deinstallieren, aber andere Komponenten, wie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder die Datenbank-Engine, installiert lassen.  
  
1.  Wählen Sie **Microsoft SQL Server 2014 (64-Bit)** aus der Programmliste aus.  
  
2.  Klicken Sie auf **Deinstallieren/ändern**.  
  
3.  Klicken Sie auf **Entfernen**. Dies startet SQL Server-Setup.  
  
     Im Setup können Sie die **PowerPivot** -Instanz und anschließend **Analysis Services** und **Analysis Services-SharePoint-Integration** auswählen, um nur diese Funktion zu entfernen und alle anderen Funktionen unverändert zu lassen.  
  
##  <a name="step-4-uninstall-the-powerpivot-for-sharepoint-add-in"></a><a name="bkmk_addin"></a>Schritt 4: Deinstallieren des PowerPivot für SharePoint-Add-ins  
 Wenn Ihre [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Bereitstellung zwei oder mehr Server umfasst und Sie das [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Add-In installiert haben, deinstallieren Sie das [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Add-In von jedem Server, auf dem es installiert wurde, um alle [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] -Dateien vollständig zu deinstallieren. Weitere Informationen finden Sie unter [installieren oder Deinstallieren des PowerPivot für SharePoint-Add-ins &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).  
  
##  <a name="step-5-verify-uninstall"></a><a name="verify"></a> Schritt 5: Überprüfen der Deinstallation  
  
1.  Stellen Sie in der Zentraladministration unter **Dienste auf dem Server verwalten**eine Verbindung mit dem Server her, von dem aus Sie PowerPivot für SharePoint deinstalliert haben.  
  
2.  -   Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 deinstalliert haben, vergewissern Sie sich, dass **SQL Server PowerPivot-Systemdienst** nicht mehr in der Liste aufgeführt wird.  
  
    -   Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 deinstalliert haben, vergewissern Sie sich, dass **SQL Server Analysis Services** und **SQL Server PowerPivot-Systemdienst** nicht mehr in der Liste aufgeführt werden.  
  
3.  Nachdem Sie den letzten PowerPivot für SharePoint-Server in der Farm deinstalliert haben, gehen Sie wie folgt vor:  
  
    1.  Überprüfen Sie in der Anwendungsverwaltung unter **Dienstanwendungen verwalten**, ob die PowerPivot-Dienstanwendung nicht mehr in der Liste angezeigt wird.  
  
    2.  Überprüfen Sie in den Systemeinstellungen, unter **Farmfunktionen verwalten**, ob die PowerPivot-Integrationfunktion nicht mehr auf der Seite angezeigt wird. Überprüfen Sie unter **Farmlösungen verwalten**, dass die PowerPivot-Lösungen nicht mehr auf der Seite angezeigt werden.  
  
    3.  Überprüfen Sie unter Überwachung, in **Diagnoseprotokollierung konfigurieren** und **Verwendungs- und Integritätsdatenerfassung konfigurieren**, ob PowerPivot-Ereignisse und Ereigniskategorien nicht mehr angezeigt werden.  
  
    4.  Stellen Sie in Allgemeine Anwendungseinstellungen sicher, dass **PowerPivot-Management-Dashboard** nicht mehr auf der Seite angezeigt wird.  
  
##  <a name="step-6-post-uninstall-checklist"></a><a name="bkmk_post"></a> Schritt 6: Prüfliste nach der Deinstallation  
 Verwenden Sie die folgende Liste, um Software und Dateien zu entfernen, die bei der Deinstallation nicht gelöscht wurden.  
  
1.  Löschen Sie alle Datendateien und Unterordner aus `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`, und löschen Sie dann den Ordner. Bei diesem Schritt werden auch zuvor zwischengespeicherte Dateien im DATA-Verzeichnis gelöscht.  
  
2.  Löschen Sie alle PowerPivot-Arbeitsmappen, -Dokumente und -Bibliotheken, falls noch nicht geschehen.  
  
    -   [Löschen des PowerPivot-Katalogs](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [Löschen einer PowerPivot-Datenfeedbibliothek](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
3.  Löschen Sie in Secure Store Service alle Zielanwendungen, die die von PowerPivot für SharePoint verwendeten gespeicherten Anmeldeinformationen enthalten. Einige (aber nicht alle) Einträge in Secure Store Service werden gelöscht, wenn PowerPivot für SharePoint deinstalliert wird. Zielanwendungen, die für das unbeaufsichtigte Datenaktualisierungskonto für PowerPivot erstellt wurden, sowie alle für die Datenaktualisierung erstellten Zielanwendungen sind noch vorhanden und müssen manuell gelöscht werden.  
  
     Im Gegensatz dazu werden einzelne Zielanwendungen, die vom PowerPivot-Systemdienst automatisch generiert wurden, bei der Deinstallation von PowerPivot automatisch gelöscht.  
  
4.  Klicken Sie in der Systemsteuerung auf **Programme**und dann auf **Programm deinstallieren** Deinstallieren Sie alle Analysis Services-Clientbibliotheken, die nicht mehr verwendet werden. Microsoft SQL Server 2008 Analysis Services-ADOMD.NET und Microsoft SQL Servers Analysis Management Objects werden bei der Deinstallation von PowerPivot für SharePoint nicht entfernt. Da die Bibliotheken möglicherweise von anderen Programmen verwendet werden, die Analysis Services-Daten verwenden, werden diese beim SQL Server-Setup nicht automatisch deinstalliert. Sie müssen die Clientbibliotheken einzeln deinstallieren, wenn Sie sie nicht mehr benötigen.  
  
     Deinstallieren Sie das SQL Server Reporting Services SharePoint 2010-Add-In, sofern Sie keine Problembehandlungs- oder Installationsanweisungen befolgen und darin zur Deinstallation aufgefordert werden. Das Reporting Services-Add-In wird von Access Services verwendet. Es wird mit dem SharePoint Products-Produktvorbereitungstool installiert und sollte im System verbleiben, um die für SharePoint erforderlichen Funktionen zu unterstützen.  
  
     Deinstallieren Sie nicht den Analysis Services OLE DB-Anbieter. Bei der SharePoint-Installation wird der OLE DB-Anbieter als Voraussetzung für Excel-Arbeitsmappen installiert, die eine Verbindung mit Analysis Services-Datenbanken herstellen. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] wird eine neuere Version installiert. Diese Version ist jedoch abwärts kompatibel und sollte daher im System bleiben, um spätere Datenverbindungsprobleme zu vermeiden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-ins &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)   
 [PowerPivot Configuration Tools](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)  
