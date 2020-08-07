---
title: Servereigenschaften (Seite Erweitert) – Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1834b1eb458ec718db23ad229a4ed6e04ae826c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619015"
---
# <a name="server-properties-advanced-page---reporting-services"></a>Servereigenschaften (Seite Erweitert) – Reporting Services
  Verwenden Sie diese Seite, um Systemeigenschaften auf dem Berichtsserver festzulegen. Es gibt eine Anzahl von Möglichkeiten, Systemeigenschaften festzulegen. Dieses Tool stellt eine grafische Benutzeroberfläche bereit, so dass Sie Eigenschaften festlegen können, ohne Code schreiben zu müssen.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie anschließend **Eigenschaften**aus. Klicken Sie auf **Erweitert** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Optionen  
 **EnableMyReports**  
 Gibt an, ob die Funktion <legacyBold>Meine Berichte</legacyBold> aktiviert ist. Der Wert `true` gibt an, dass die Funktion aktiviert ist.  
  
 **MyReportsRole**  
 Der Name der Rolle, die beim Erstellen von Sicherheitsrichtlinien für die Ordner <legacyBold>Meine Berichte</legacyBold> des Benutzers verwendet wird. Der Standardwert ist `My Reports Role`.  
  
 **EnableClientPrinting**  
 Bestimmt, ob das RSClientPrint-ActiveX-Steuerelement zum Herunterladen vom Berichtsserver verfügbar ist. Gültige Werte sind `true` und `false` . Der Standardwert ist `true`. Weitere Informationen zu zusätzlichen Einstellungen, die für dieses Steuerelement erforderlich sind, finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 **EnableExecutionLogging**  
 Gibt an, ob die Protokollierung der Berichtsausführung aktiviert ist. Der Standardwert ist `true`. Weitere Informationen zum Berichts Server-Ausführungs Protokoll finden Sie unter [Berichts Server-Ausführungs Protokoll und die ExecutionLog3-Sicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **ExecutionLogDaysKept**  
 Die Anzahl von Tagen, in denen die Berichtsausführungsdaten im Ausführungsprotokoll verbleiben. Gültige Werte für diese Eigenschaft sind `-1` und `2`,`147`,`483`,`647`. Wenn der Wert `-1` ist, werden Einträge nicht aus der Ausführungsprotokolltabelle gelöscht. Der Standardwert ist `60`.  
  
 **SessionTimeout**  
 Der Zeitraum in Sekunden, in dem die Sitzung aktiv bleibt. Der Standardwert ist `600`.  
  
 **SharePointIntegratedMode**  
 Dies ist eine schreibgeschützte Eigenschaft, die den Servermodus angibt. Wenn dieser Wert False ist, wird der Berichtsserver im einheitlichen Modus ausgeführt.  
  
 **Sitename**  
 Der Name der Berichtsserversite, der im Seitentitel des Berichts-Managers angezeigt wird. Der Standardwert ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Diese Eigenschaft kann eine leere Zeichenfolge sein. Die maximale Länge beträgt 8,000 Zeichen.  
  
 **StoredParametersLifetime**  
 Gibt die maximale Anzahl von Tagen an, während derer ein gespeicherter Parameter gespeichert werden kann. Gültige Werte sind `-1`, `+1` und `2,147,483,647`. Der Standardwert ist `180` Tage.  
  
 **StoredParametersThreshold**  
 Gibt die maximale Anzahl von Parameterwerten an, die von dem Berichtsserver gespeichert werden können. Gültige Werte sind `-1`, `+1` und `2,147,483,647`. Der Standardwert ist `1500`.  
  
 **UseSessionCookies**  
 Gibt an, ob der Berichtsserver beim Kommunizieren mit Clientbrowsern Sitzungscookies verwenden soll. Der Standardwert ist `true`.  
  
 **ExternalImagesTimeout**  
 Legt den Zeitraum fest, innerhalb dessen eine externe Bilddatei abgerufen werden muss, bevor ein Timeout für die Verbindung vorliegt. Der Standardwert ist `600` Sekunden.  
  
 **SnapshotCompression**  
 Definiert, wie Momentaufnahmen komprimiert werden. Der Standardwert ist `SQL`. Die folgenden Werte sind gültig:  
  
 **SQL =** Momentaufnahmen werden komprimiert, wenn sie in der Berichtsserver-Datenbank gespeichert werden. Dies ist das aktuelle Verhalten.  
  
 **Keine** = Momentaufnahmen werden nicht komprimiert.  
  
 **Alle =** Momentaufnahmen werden bei allen Speicheroptionen komprimiert, was auch die Berichtsserver-Datenbank oder das Dateisystem einschließt.  
  
 **SystemReportTimeout**  
 Der Standard-Timeoutwert für die Berichtsverarbeitung in Sekunden für alle im Berichtsserver-Namespace verwalteten Berichte. Dieser Wert kann auf Berichtsebene überschrieben werden. Ist diese Eigenschaft festgelegt, versucht der Berichtsserver, die Verarbeitung eines Berichts zu beenden, sobald der angegebene Zeitraum überschritten wird. Gültige Werte sind `-1` und `2`,`147`,`483`,`647`. Wenn der Wert `-1` ist, tritt bei Berichten im Namespace während der Verarbeitung kein Timeout auf. Der Standardwert ist `1800`.  
  
 **SystemSnapshotLimit**  
 Die maximale Anzahl an Momentaufnahmen, die für einen Bericht gespeichert werden. Gültige Werte sind `-1` und `2`,`147`,`483`,`647`. Lautet der Wert `-1`, so ist die Anzahl der Momentaufnahmen nicht einschränkt.  
  
 **EnableIntegratedSecurity**  
 Bestimmt, ob die integrierte Sicherheit von Windows für Berichtsdatenquellen-Verbindungen unterstützt wird. Der Standardwert lautet `True`. Die folgenden Werte sind gültig:  
  
 `True` = Integrierte Sicherheit von Windows ist aktiviert.  
  
 `False` = Integrierte Sicherheit von Windows ist nicht aktiviert. Berichtsdatenquellen, die für die Verwendung der integrierten Sicherheit von Windows konfiguriert sind, werden nicht ausgeführt.  
  
 `EnableLoadReportDefinition`  
 Wählen Sie diese Option um anzugeben, ob Benutzer eine Ad-hoc-Berichtsausführung von einem Bericht des Berichts-Generators ausführen können. Durch Festlegen dieser Option wird der Wert der `EnableLoadReportDefinition`-Eigenschaft auf dem Berichtsserver bestimmt.  
  
 Wenn Sie diese Option deaktivieren, wird die Eigenschaft auf False festgelegt, und der Berichtsserver generiert keine Berichte mit Durchklicken für Berichte, die ein Berichtsmodell als Datenquelle verwenden. Alle Aufrufe der LoadReportDefinition-Methode werden blockiert.  
  
 Die Deaktivierung dieser Option führt zu einem Sicherheitsrisiko, weil böswillige Benutzer einen Denial-of-Service-Angriff ausführen können, bei dem der Berichtsserver mit LoadReportDefinition-Anforderungen überlastet wird.  
  
 **EnableRemoteErrors**  
 Nimmt externe Fehlerinformationen (beispielsweise Fehlerinformationen zu Berichtsdatenquellen) in die Fehlermeldungen auf, die für Benutzer zurückgegeben werden, die Berichte von Remotecomputern anfordern. Gültige Werte sind `true` und `false`. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [Aktivieren von Remotefehlern &#40;Reporting Services&#41;](../report-server/enable-remote-errors-reporting-services.md).  
  
 **EnableReportDesignClientDownload**  
 Gibt an, ob das Berichts-Generator-Installationspaket vom Berichtsserver heruntergeladen werden kann. Wenn Sie diese Einstellung deaktivieren, funktioniert die URL zum Berichts-Generator nicht. Weitere Informationen finden Sie unter [Konfigurieren des Berichts-Generator-Zugriffs](../report-server/configure-report-builder-access.md).  
  
 **EditSessionCacheLimit**  
 Gibt die Anzahl von Datencacheeinträgen an, die in einer Berichtsbearbeitungssitzung aktiv sein können. Die Standardanzahl ist 5.  
  
 **EditSessionTimeout**  
 Gibt die Anzahl von Sekunden bis zum Timeout einer Berichts Bearbeitungs Sitzung an. Der Standardwert ist 7200 Sekunden (2 Stunden).  
  
 **EnableTestConnectionDetailedErrors**  
 Gibt an, ob ausführliche Fehlermeldungen an den Clientcomputer gesendet werden, wenn Benutzer Datenquellverbindungen mit dem Berichtsserver testen. Der Standardwert ist `true`. Wenn die Option auf `false` festgelegt wird, werden nur generische Fehlermeldungen gesendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#40;Management Studio Eigenschaften für Berichts Server festlegen&#41;](set-report-server-properties-management-studio.md)   
 [Herstellen einer Verbindung mit einem Berichts Server in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Eigenschaften von Reporting Services](../report-server-web-service/net-framework/reporting-services-properties.md)   
 [Berichts Server in Management Studio F1-Hilfe](report-server-in-management-studio-f1-help.md)   
 [Berichts Server-System Eigenschaften](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
 [Skript Bereitstellungs-und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md)   
 [Aktivieren und Deaktivieren von "Meine Berichte"](../report-server/enable-and-disable-my-reports.md)  
  
  
