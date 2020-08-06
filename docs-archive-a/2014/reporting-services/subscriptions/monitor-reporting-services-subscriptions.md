---
title: Überwachen von Reporting Services-Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], inactive
- subscriptions [Reporting Services], status
- monitoring [Reporting Services], subscriptions
- status information [Reporting Services]
- inactive subscriptions [Reporting Services]
ms.assetid: 054c4a87-60bf-4556-9a8c-8b2d77a534e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c94cd093fb4a5a095e270ae3cb0eb29d795347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618464"
---
# <a name="monitor-reporting-services-subscriptions"></a>Überwachen von Reporting Services-Abonnements
  Sie können [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnements über die Benutzeroberfläche, Windows PowerShell oder Protokolldateien überwachen. Die für die Überwachung verfügbaren Optionen hängen davon ab, welchen Modus des Berichtsservers Sie ausführen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
 **In diesem Thema:**  
  
-   [Benutzeroberfläche des einheitlichen Modus](#bkmk_native_mode)  
  
-   [SharePoint-Modus](#bkmk_sharepoint_mode)  
  
-   [Verwenden von PowerShell zur Überwachung von Abonnements](#bkmk_use_powershell)  
  
-   [Verwalten inaktiver Abonnements](#bkmk_manage_inactive)  
  
##  <a name="native-mode-user-interface"></a><a name="bkmk_native_mode"></a> Benutzeroberfläche des einheitlichen Modus  
 Einzelne [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Benutzer können den Status eines Abonnements mithilfe der Seite **Meine Abonnements** oder der Registerkarte **Abonnements** im Berichts-Manager überwachen. Abonnementseiten enthalten Spalten mit dem Status des Abonnements und mit Informationen, wann das Abonnement zuletzt ausgeführt wurde. Statusmeldungen werden aktualisiert, wenn das Abonnement zur Verarbeitung ansteht. Falls dieser Vorgang niemals ausgelöst wird (z. B. wenn eine Momentaufnahme zur Berichtsausführung niemals aktualisiert oder ein Zeitplan niemals ausgeführt wird), wird die Statusmeldung nicht aktualisiert.  
  
 Die folgende Tabelle enthält die möglichen Werte für die Spalte **Status** .  
  
|Status|BESCHREIBUNG|  
|------------|-----------------|  
|Neues Abonnement|Wird beim Erstellen des Abonnements angezeigt.|  
|Inaktiv|Wird angezeigt, wenn ein Abonnement nicht verarbeitet werden kann. Weitere Informationen finden Sie weiter unten unter "Verwalten inaktiver Abonnements".|  
|Abgeschlossen: \<*number*> insgesamt verarbeitet \<*number*> ; \<*number*> Fehler.|Zeigt den Status der Ausführung eines datengesteuerten Abonnements an. Diese Meldung stammt vom Prozessor für Zeitplanung und Übermittlung.|  
|\<*number*>bearbeitet|Die Anzahl von Benachrichtigungen, die der Prozessor für Zeitplanung und Übermittlung erfolgreich übermittelt hat oder nicht mehr zu übermitteln versucht. Beim Abschluss einer datengesteuerten Übermittlung sollte die Anzahl von verarbeiteten Benachrichtigungen den insgesamt generierten Benachrichtigungen entsprechen.|  
|\<*number*>totales|Die Gesamtzahl der Benachrichtigungen, die für die letzte Übermittlung für das Abonnement generiert wurden.|  
|\<*number*>Zeit|Die Anzahl von Benachrichtigungen, die der Prozessor für Zeitplanung und Übermittlung nicht übermitteln konnte oder nicht mehr zu übermitteln versucht.|  
|Fehler beim Senden von E-Mail: Transportfehler beim Verbinden mit dem Server.|Zeigt an, dass der Berichtsserver keine Verbindung zum Mailserver hergestellt hat. Diese Meldung stammt von der E-Mail-Übermittlungserweiterung.|  
|\<*filename*>Die Datei wurde in geschrieben \<path> .|Zeigt an, dass die Datei erfolgreich an den Speicherort der Dateifreigabe übermittelt wurde. Diese Meldung stammt von der Dateifreigabe-Übermittlungserweiterung.|  
|Unbekannter Fehler beim Schreiben der Datei.|Zeigt an, dass die Datei nicht an den Speicherort der Dateifreigabe übermittelt werden konnte. Diese Meldung stammt von der Dateifreigabe-Übermittlungserweiterung.|  
|Fehler beim Herstellen einer Verbindung mit dem Zielordner \<path> . Überprüfen Sie, ob der Zielordner oder die Dateifreigabe vorhanden ist.|Zeigt an, dass der angegebene Ordner nicht gefunden wurde. Diese Meldung stammt von der Dateifreigabe-Übermittlungserweiterung.|  
|Es \<filename> konnte nicht in die Datei geschrieben werden \<path> . Es erfolgt ein erneuter Versuch.|Zeigt an, dass die Datei nicht durch eine neuere Version aktualisiert werden konnte. Diese Meldung stammt von der Dateifreigabe-Übermittlungserweiterung.|  
|Fehler beim Schreiben der Datei \<filename> :\<message>|Zeigt an, dass die Datei nicht an den Speicherort der Dateifreigabe übermittelt werden konnte. Diese Meldung stammt von der Dateifreigabe-Übermittlungserweiterung.|  
|\<custom status messages>|Statusmeldungen zum Erfolg oder Fehlschlagen der Übermittlung. Diese Meldungen stammen von Übermittlungserweiterungen. Falls Sie eine Übermittlungserweiterung von einem Drittanbieter oder eine benutzerdefinierte Übermittlungserweiterung verwenden, werden möglicherweise zusätzliche Statusmeldungen angezeigt.|  
  
 Berichtsserveradministratoren können auch Standardabonnements überwachen, die gerade verarbeitet werden. Datengesteuerte Abonnements können nicht überwacht werden. Weitere Informationen finden Sie unter [Verwalten eines ausgeführten Prozesses](manage-a-running-process.md).  
  
 Falls ein Abonnement nicht übermittelt werden kann (z. B., weil der Mailserver nicht verfügbar ist), wiederholt die Übermittlungserweiterung den Versuch. Eine Konfigurationseinstellung gibt die Anzahl von Wiederholungsversuchen an. Standardmäßig wird der Vorgang nicht wiederholt. Es kann vorkommen, dass der Bericht ohne Daten verarbeitet wird (z. B., wenn die Datenquelle offline ist). In diesem Fall wird durch einen entsprechenden Text in der Meldung darauf hingewiesen.  
  
### <a name="native-mode-log-files"></a>Protokolldateien im einheitlichen Modus  
 Beim Auftreten eines Fehlers während der Übermittlung erfolgt ein Eintrag im Ablaufverfolgungsprotokoll des Berichtsservers.  
  
 Berichts Server Administratoren können die Dateien **ReportServerService_ \* . log** überprüfen, um den Status der Abonnement Übermittlung zu ermitteln. Für die E-Mail-Übermittlung schließen Protokolldateien des Berichtsservers eine Aufzeichnung der Verarbeitungs- und Übermittlungsvorgänge für bestimmte E-Mail-Konten ein. Der Standardspeicherort der Protokolldateien lautet:  
  
 `C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\LogFiles`  
  
 Es folgt ein Beispiel für einen Protokolldateinamen:  
  
 `ReportServerService__05_21_2014_00_05_07.log`  
  
 Es folgt eine Beispielfehlermeldung einer Ablaufverfolgungsprotokolldatei im Zusammenhang mit Abonnements:  
  
-   library!WindowsService_7!b60!05/20/2014-22:34:36:: i INFO: Initialisieren von EnableExecutionLogging auf TRUE gemäß Serversystemeigenschaften properties.emailextension!WindowsService_7!b60!05/20/2014-22:34:41:: e ERROR: **E-Mail-Sendefehler**. Ausnahme: System.Net.Mail.SmtpException: Für den SMTP-Server ist eine sichere Verbindung erforderlich, oder der Client wurde nicht authentifiziert. Die Serverantwort lautete: 5.7.1 Client wurde nicht auf System.Net.Mail.MailCommand.CheckResponse(SmtpStatusCode statusCode, String response) authentifiziert.  
  
 Die Protokolldatei enthält keine Informationen, ob der Bericht geöffnet wurde oder ob die Übermittlung tatsächlich erfolgreich war. Eine erfolgreiche Übermittlung bedeutet, dass der Prozessor für Zeitplanung und Übermittlung keine Fehler generiert und der Berichtsserver eine Verbindung zum Mailserver hergestellt hat. Falls für die E-Mail im Postfach des Benutzers eine Fehlermeldung wegen Unzustellbarkeit generiert wird, werden diese Informationen nicht in die Protokolldatei aufgenommen. Weitere Informationen zu Protokolldateien finden Sie unter [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md).  
  
##  <a name="sharepoint-mode"></a><a name="bkmk_sharepoint_mode"></a>SharePoint-Modus  
 So überwachen Sie ein Abonnement im SharePoint-Modus: Der Abonnementstatus kann auf der Seite **Abonnements verwalten** überwacht werden.  
  
1.  Navigieren Sie zu der Dokumentbibliothek, die den Bericht enthält.  
  
2.  Öffnen Sie das Kontextmenü des Berichts ( **...** ).  
  
3.  Wählen Sie die erweiterte Menüoption ( **...** ) aus.  
  
4.  Wählen Sie **Abonnements verwalten**aus.  
  
### <a name="sharepoint-uls-log-files"></a>SharePoint ULS-Protokolldateien  
 Abonnementbezogene Informationen werden in das SharePoint ULS-Protokoll geschrieben. Weitere Informationen zum Konfigurieren von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Ereignissen für das ULS-Protokoll finden Sie unter [Aktivieren von Reporting Services-Ereignissen für das SharePoint-Ablaufverfolgungsprotokoll (ULS)](../report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md).  Das folgende Beispiel zeigt einen ULS-Protokolleintrag im Zusammenhang mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Abonnements.  
  
||||||||  
|-|-|-|-|-|-|-|  
|Date|Prozess|Bereich|Category|Ebene|Correlation|`Message`|  
|5/21/2014 14:34:06:15|App-Pool: a0ba039332294f40bc4a81544afde01d|SQL Server Reporting Services|Berichtsserver-E-Mail-Erweiterung|Unerwartet|(leer)|**Fehler beim Senden von E-Mail.** Ausnahme: System.Net.Mail.SmtpException: Postfach nicht verfügbar. Die Serverantwort lautete: 5.7.1 Client does not have permissions to send as this sender at System.Net.Mail.DataStopCommand.CheckResponse(SmtpStatusCode statusCode, String serverResponse) at System.Net.Mail.DataStopCommand.Send(SmtpConnection conn) at System.Net.Mail.SmtpClient.Send(MailMessage message) at Microsoft.ReportingServices.EmailDeliveryProvider.EmailProvider.Deliver(Notification notification) (5.7.1 Client ist nicht berechtigt, als dieser Absender zu senden: an System.Net.Mail.DataStopCommand.CheckResponse(SmtpStatusCode statusCode, String serverResponse), an System.Net.Mail.DataStopCommand.Send(SmtpConnection conn), an System.Net.Mail.SmtpClient.Send(MailMessage message) und an Microsoft.ReportingServices.EmailDeliveryProvider.EmailProvider.Deliver(Notification notification))|  
  
##  <a name="use-powershell-to-monitor-subscriptions"></a><a name="bkmk_use_powershell"></a> Verwenden von PowerShell zur Überwachung von Abonnements  
 Beispiele für PowerShell-Skripts zum Überprüfen des Status von Abonnements im einheitlichen Modus oder im SharePoint-Modus finden Sie unter [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md).  
  
##  <a name="managing-inactive-subscriptions"></a><a name="bkmk_manage_inactive"></a>Verwalten inaktiver Abonnements  
 Falls ein Abonnement nicht mehr aktiv ist, sollten Sie es entweder löschen oder erneut aktivieren, indem Sie die zugrunde liegenden Bedingungen auflösen, die die Verarbeitung verhindern. Abonnements können beim Auftreten von Bedingungen, die die Verarbeitung verhindern, deaktiviert werden. Dazu zählen die folgenden Bedingungen:  
  
-   Entfernen oder Deinstallieren der im Abonnement angegebenen Übermittlungserweiterung.  
  
-   Ändern der Einstellungen für Anmeldeinformationen von gespeicherten zu integrierten oder eingegebenen Werten.  
  
-   Ändern eines Parameternamens oder Datentyps in der Berichtsdefinition und anschließend erneutes Veröffentlichen eines Berichts. Enthält ein Abonnement einen Parameter, der nicht mehr gültig ist, wird das Abonnement deaktiviert.  
  
-   Ändern des Ausführungsmodus eines Berichts (z. B. Ändern eines bedarfsgesteuerten Berichts, damit er als Momentaufnahme zur Berichtsausführung ausgeführt wird). Weitere Informationen finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](../report-server/set-report-processing-properties.md).  
  
 Auf ein inaktives Abonnement wird durch eine Meldung im Abonnement selbst hingewiesen. Diese Meldung enthält Informationen zum Grund der Deaktivierung und zu den Schritten, die zum erneuten Aktivieren des Abonnements ausgeführt werden müssen.  
  
 Wenn Bedingungen zur Deaktivierung des Abonnements führen, wird dies im  Abonnement beim Ausführen durch den Berichtsserver angezeigt. Wenn ein Abonnement einen Bericht laut Zeitplan jeden Freitag um 02:00 Uhr übermitteln soll und die verwendete Übermittlungserweiterung am Montag um 09:00 Uhr deinstalliert wurde, wird der inaktive Status des Abonnements erst am Freitag um 02:00 Uhr angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus](../create-manage-subscriptions-native-mode-report-servers.md)   
 [Abonnements und Übermittlung (Reporting Services)](subscriptions-and-delivery-reporting-services.md)  
  
  
