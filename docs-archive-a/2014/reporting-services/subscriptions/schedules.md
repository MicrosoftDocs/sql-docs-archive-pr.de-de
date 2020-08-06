---
title: Zeitpläne | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- schedules [Reporting Services]
- schedules [Reporting Services], about schedules
- published reports [Reporting Services], schedules
- reports [Reporting Services], scheduling
- subscriptions [Reporting Services], scheduling
- automatic report processing
ms.assetid: ecccd16b-eba9-4e95-b55d-f15c621e003f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99bcfbf6559c0f3b59bede54eae6224b4973797b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723317"
---
# <a name="schedules"></a>Zeitpläne
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt freigegebene und berichtsspezifische Zeitpläne bereit, mit denen Sie die Verarbeitung und Verteilung von Berichten steuern können. Der Unterschied zwischen den beiden Typen von Zeitplänen liegt in ihrer Definition, Speicherung und Verwaltung. Die interne Konstruktion der beiden Typen von Zeitplänen ist die gleiche. Alle Zeitpläne geben einen Wiederholungstyp an: monatlich, wöchentlich oder täglich. Innerhalb des Wiederholungstyps legen Sie die Intervalle und den Zeitraum der Häufigkeit eines Ereignisses fest. Die Wiederholungsoption und die Art und Weise, wie diese festgelegt ist, sind dieselbe, unabhängig davon, ob Sie einen freigegebenen oder einen berichtsspezifischen Zeitplan erstellen.  
  
 Inhalte dieses Themas:  
  
-   [Möglichkeiten von Zeitplänen](#bkmk_whatyoucando)  
  
-   [Vergleichen von freigegebenen und Berichts spezifischen Zeitplänen](#bkmk_compare)  
  
-   [Konfigurieren der Datenquellen](#bkmk_configuredatasources)  
  
-   [Speichern von Anmelde Informationen und Verarbeiten von Konten](#bkmk_credentials)  
  
-   [Funktionsweise von Zeitplanung und Übermittlungs Verarbeitung](#bkmk_how_scheduling_works)  
  
-   [Server Abhängigkeiten](#bkmk_serverdependencies)  
  
-   [Auswirkungen des Anhaltens der SQL Server-Agent](#bkmk_stoppingagent)  
  
-   [Auswirkungen des Anhaltens auf den Berichts Server Dienst](#bkmk_stoppingservice)  
  
  
##  <a name="what-you-can-do-with-schedules"></a><a name="bkmk_whatyoucando"></a> Verwenden von Zeitplänen  
 Sie können den Berichts-Manager im einheitlichen Modus und SharePoint-Seiten für die Websiteadministration im SharePoint-Modus verwenden, um Zeitpläne zu erstellen und zu verwalten. Ihre Möglichkeiten:  
  
-   Planen der Berichtsübermittlung in einem standardmäßigen oder datengesteuerten Abonnement.  
  
-   Planen der Generierung des Berichtsverlaufs, sodass in regelmäßigen Abständen neue Momentaufnahmen dem Berichtsverlauf hinzugefügt werden.  
  
-   Planen, wann die Daten einer Berichtsmomentaufnahme aktualisiert werden.  
  
-   Planen, wann die Daten eines freigegebenen Datasets aktualisiert werden.  
  
-   Planen des Ablaufs eines zwischengespeicherten Berichts oder freigegebenen Datasets zu einem vordefinierten Zeitpunkt, damit er anschließend aktualisiert werden kann.  
  
 Wenn Sie die gleichen Zeitplaninformationen für mehrere Berichte oder Abonnements verwenden möchten, können Sie einen freigegebenen Zeitplan erstellen. Freigegebene Zeitpläne werden separat definiert und dann in Berichten, freigegebenen Datasets und Abonnements herangezogen, die Zeitplaninformationen benötigen.  
  
 Beim Erstellen eines Zeitplans werden die Zeitplaninformationen vom Bericht in der Berichtsserver-Datenbank bzw. im SharePoint-Modus in der Dienstanwendungs-Datenbank gespeichert. Der Berichtsserver erstellt außerdem einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag, der zum Auslösen des Zeitplans verwendet wird. Die Zeitplanverarbeitung basiert auf der lokalen Zeit des Berichtsservers, auf dem sich der Zeitplan befindet. Das Zeitformat entspricht dem Standard des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Betriebssystems.  
  
 Einzelheiten zum Erstellen und Verwalten von Zeitplänen finden Sie unter [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md).  
  
> [!NOTE]  
>  Zeitplanvorgänge sind nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den-Editionen unterstützt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , finden Sie [unter von den-Editionen unterstützte Funktionen SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) () https://go.microsoft.com/fwlink/?linkid=232473) .  
  
##  <a name="comparing-shared-and-report-specific-schedules"></a><a name="bkmk_compare"></a> Vergleichen von freigegebenen und berichtsspezifischen Zeitplänen  
 Beide Typen von Zeitplänen führen zum selben Ergebnis.  
  
-   **Freigegebene Zeitpläne** sind portable, für verschiedene Zwecke ausgerichtete Elemente, die einsatzbereite Zeitplaninformationen enthalten. Da freigegebene Zeitpläne Elemente auf Systemebene darstellen, sind zum Erstellen eines freigegebenen Zeitplans Berechtigungen auf Systemebene erforderlich. Deshalb erstellt normalerweise ein Berichtsserveradministrator oder Inhalts-Manager die freigegebenen Zeitpläne, die auf dem Berichtsserver verfügbar sind. Freigegebene Zeitpläne werden mit dem Berichts-Manager oder mit SharePoint-Siteeinstellungen auf dem Berichtsserver gespeichert und verwaltet.  
  
     Im Gegensatz zu bestimmten Zeitplänen, die Sie über die Eigenschaften von Berichten, freigegebenen Datasets oder Abonnements definieren, sind freigegebene Zeitpläne aus den folgenden Gründen einfacher zu verwalten und zu pflegen:  
  
    -   Freigegebene Zeitpläne können von einem zentralen Speicherort aus verwaltet werden, wodurch Zeitplaneigenschaften einfacher verglichen und Häufigkeits- sowie Wiederholungsmuster einfacher angepasst werden können, wenn geplante Vorgänge zu eng beieinander liegen oder mit anderen Prozessen auf dem Server in Konflikt stehen.  
  
    -   Ermöglicht Ihnen, schnell auf Änderungen in der Computerumgebung einzugehen. Angenommen, Sie haben einen Satz von Berichten, die um 04:00 Uhr ausgeführt werden, nachdem ein Data Warehouse aktualisiert wurde. Wenn der Vorgang der Datenaktualisierung neu geplant wird oder sich verzögert, können Sie auf einfache Weise auf diese Änderung eingehen, indem Sie die Zeitplandaten in einem einzelnen, zentralen Zeitplan aktualisieren.  
  
    -   Wenn Sie nur freigegebene Zeitpläne verwenden, wissen Sie genau, wann geplante Vorgänge auftreten. Auf diese Weise kann die Serverauslastung vorhergesagt und darauf reagiert werden, bevor Leistungsprobleme auftreten. Wenn Sie zum Beispiel Computersicherungen zu einer bestimmten Zeit planen möchten, können Sie die freigegebenen Zeitpläne so anpassen, dass sie zu unterschiedlichen Zeiten durchgeführt werden.  
  
-   **Berichtsspezifische Zeitpläne** werden im Kontext eines bestimmten Berichts, Abonnements oder eines bestimmten Vorgangs für die Berichtsausführung definiert, um den Ablaufzeitpunkt des Caches oder Momentaufnahmeupdates zu bestimmen. Diese Zeitpläne werden inline erstellt, wenn Sie ein Abonnement definieren oder Eigenschaften zur Berichtsausführung festlegen. Erstellen Sie einen berichtsspezifischen Zeitplan, wenn ein freigegebener Zeitplan nicht die benötigte Häufigkeits- oder Wiederholungsoption bereitstellt. Einen berichtsspezifischen Zeitplan müssen Sie manuell bearbeiten, um zu verhindern, dass der Bericht ausgeführt wird. Berichtsspezifische Zeitpläne können von einzelnen Benutzern erstellt werden.  
  
##  <a name="configure-the-data-sources"></a><a name="bkmk_configuredatasources"></a> Konfigurieren der Datenquellen  
 Bevor Sie die Daten- oder Abonnementverarbeitung für einen Bericht planen können, müssen Sie die Berichtsdatenquelle so konfigurieren, dass sie gespeicherte Anmeldeinformationen oder das Konto für die unbeaufsichtigte Berichtsverarbeitung verwendet. Wenn Sie gespeicherte Anmeldeinformationen verwenden, können Sie nur einen Satz von Anmeldeinformationen speichern. Diese werden von allen Benutzern verwendet, die den Bericht ausführen. Bei den Anmeldeinformationen kann es sich um ein Windows-Benutzerkonto oder ein Datenbank-Benutzerkonto handeln.  
  
 Bei dem Konto für die unbeaufsichtigte Berichtsverarbeitung handelt es sich um ein spezielles Konto, das auf dem Berichtsserver konfiguriert wird. Es wird vom Berichtsserver für das Herstellen einer Verbindung mit Remotecomputern verwendet, wenn für einen geplanten Vorgang der Abruf einer externen Datei oder eine Verarbeitung erforderlich ist. Wenn Sie das Konto konfigurieren, können Sie es zum Herstellen einer Verbindung mit externen Datenquellen verwenden, die einem Bericht Daten bereitstellen.  
  
 Wenn Sie gespeicherte Anmeldeinformationen oder das Konto für die unbeaufsichtigte Berichtsverarbeitung angeben möchten, bearbeiten Sie die Datenquelleneigenschaften des Berichts. Wenn der Bericht eine freigegebene Datenquelle verwendet, bearbeiten Sie stattdessen die freigegebene Datenquelle.  
  
##  <a name="store-credentials-and-processing-accounts"></a><a name="bkmk_credentials"></a> Speichern von Anmeldeinformationen und Verarbeitungskonten  
 Ihre Arbeitsweise mit Zeitplänen hängt von Aufgaben ab, die Bestandteil Ihrer Rollenzuweisung sind. Bei der Verwendung vordefinierter Rollen können Inhalts-Manager und Systemadministratoren beliebige Zeitpläne erstellen und verwalten. Wenn Sie benutzerdefinierte Rollenzuweisungen verwenden, muss die Rollenzuweisung Aufgaben für geplante Vorgänge enthalten.  
  
|Aufgabe|Verwendete Aufgabe|Vordefinierte Rollen im einheitlichen Modus|Gruppen im SharePoint-Modus|  
|----------------|-----------------------|----------------------------------|----------------------------|  
|Erstellen, Ändern oder Löschen freigegebener Zeitpläne|Freigegebene Zeitpläne verwalten|Systemadministrator|Besitzer|  
|Auswählen freigegebener Zeitpläne|Freigegebene Zeitpläne anzeigen|Systembenutzer|Members|  
|Erstellen, Ändern oder Löschen berichtsspezifischer Zeitpläne in einem benutzerdefinierten Abonnement|Einzelne Abonnements verwalten|Browser, Berichts-Generator, Meine Berichte, Inhalts-Manager|Besucher, Mitglieder|  
|Erstellen, Ändern oder Löschen berichtsspezifischer Zeitpläne für alle anderen geplanten Vorgänge|Berichtsverlauf verwalten, Alle Abonnements verwalten, Berichte verwalten|Inhalts-Manager|Besitzer|  
  
 Weitere Informationen zur Sicherheit im einheitlichen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Modus finden Sie unter [Vordefinierte Rollen](../security/role-definitions-predefined-roles.md), [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](../security/granting-permissions-on-a-native-mode-report-server.md) und [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md). Informationen zum SharePoint-Modus finden Sie unter [Vergleichen der Rollen und Aufgaben in Reporting Services mit SharePoint-Gruppen und -Berechtigungen](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
  
##  <a name="how-scheduling-and-delivery-processing-works"></a><a name="bkmk_how_scheduling_works"></a> Funktionsweise des Prozessors für Zeitplanung und Übermittlung  
 Der Prozessor für Zeitplanung und Übermittlung stellt die folgenden Funktionen bereit:  
  
-   Verwaltet eine Warteschlange von Ereignissen und Benachrichtigungen in der Berichtsserver-Datenbank. In einer Bereitstellung für dezentrales Skalieren ist die Warteschlange für alle Berichtsserver freigegeben.  
  
-   Ruft den Berichtsprozessor ab, um Berichte auszuführen, Abonnements zu verarbeiten oder einen zwischengespeicherten Bericht zu löschen. Die gesamte Berichtsverarbeitung, die als Folge eines geplanten Ereignisses auftritt, wird als Hintergrundprozess durchgeführt. Im SharePoint-Modus werden Zeitgeberaufträge verwendet.  
  
-   Ruft die Übermittlungserweiterung auf, die im Abonnement angegeben ist, damit der Bericht übermittelt werden kann.  
  
 Andere Aspekte der Zeitplanung und Übermittlung werden von anderen Komponenten und Diensten verarbeitet, die mit dem Prozessor für Zeitplanung und Übermittlung zusammenarbeiten. Genauer gesagt wird der Prozessor für Zeitplanung und Übermittlung im Berichtsserverdienst ausgeführt und verwendet den SQL Server-Agent als Zeitgeber zum Generieren von geplanten Ereignissen. In der folgenden schrittweisen Beschreibung wird erläutert, wie die geplanten Vorgänge in einer Reporting Services-Bereitstellung funktionieren:  
  
1.  Ein geplanter Vorgang wird definiert, wenn ein Benutzer einen Zeitplan erstellt. In dem Plan werden ein Datum und eine Uhrzeit definiert, die zum Auslösen eines Abonnements für die Berichtsübermittlung, zum Aktualisieren einer Momentaufnahme oder zum Ablaufen eines Caches verwendet werden.  
  
2.  Der Berichtsserver speichert die Zeitplaninformationen in der Berichtsserverdatenbank.  
  
3.  Vom Berichtsserver wird ein entsprechender Auftrag im SQL Server-Agent erstellt, der die bereitgestellten Zeitplaninformationen enthält. Die Aufträge werden über eine gespeicherte Prozedur erstellt, wobei die vorhandene offene Verbindung mit der Berichtsserverdatenbank verwendet wird.  
  
4.  Der SQL Server-Agent führt den Auftrag zum im Zeitplan angegebenen Zeitpunkt aus. Der Auftrag erstellt ein Ereignis, das einer von Reporting Services verwalteten Warteschlange hinzugefügt wird.  
  
5.  Das Ereignis führt zu einem Berichts- oder Abonnementprozess. Die Verarbeitung der Ereignisse erfolgt sofort, wenn sie in der Warteschlange erkannt werden. Der Bericht wird dann entsprechend verarbeitet und übermittelt.  
  
     Bevor die Ereignisse verarbeitet werden, führt der Prozessor für Zeitplanung und Übermittlung einen Authentifizierungsschritt durch, um zu überprüfen, ob der Abonnementbesitzer über die Berechtigung verfügt, den Bericht anzuzeigen.  
  
 Reporting Services verwaltet eine Ereigniswarteschlange für alle geplanten Vorgänge. Die Warteschlange wird in regelmäßigen Abständen nach neuen Ereignissen abgefragt. Standardmäßig wird die Warteschlange alle 10 Sekunden überprüft. Sie können das Intervall ändern, indem Sie in der Datei „RSReportServer.config“ die Konfigurationseinstellungen `PollingInterval`, `IsNotificationService` und `IsEventService` ändern. Im SharePoint-Modus wird ebenfalls die Datei „RSreporserver.config“ für diese Einstellungen verwendet, und die Werte gelten für alle [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen. Weitere Informationen finden Sie unter [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).  
  
##  <a name="server-dependencies"></a><a name="bkmk_serverdependencies"></a> Serverabhängigkeiten  
 Für den Prozessor für Zeitplanung und Übermittlung müssen der Berichtsserverdienst und der SQL Server-Agent gestartet sein. Die Funktion für die Verarbeitung von Zeitplanung und Übermittlung muss über die- `ScheduleEventsAndReportDeliveryEnabled` Eigenschaft der **Oberflächenkonfiguration für Reporting Services** Facette in der Richtlinien basierten Verwaltung aktiviert werden. Sowohl der SQL Server-Agent als auch der Berichtsserverdienst müssen ausgeführt werden, damit geplante Vorgänge auftreten.  
  
> [!NOTE]  
>  Mit dem Facet **Oberflächenkonfiguration für Reporting Services** können geplante Vorgänge vorübergehend oder dauerhaft beendet werden. Obwohl Sie benutzerdefinierte Übermittlungserweiterungen erstellen und bereitstellen können, ist der Prozessor für Zeitplanung und Übermittlung an sich nicht erweiterbar. Sie können die Weise, wie er Ereignisse und Benachrichtigungen verwaltet, nicht ändern. Weitere Informationen zu Deaktivieren von Funktionen finden Sie in die im Abschnitt **Geplante Ereignisse und Übermittlung** von [Turn Reporting Services Features On or Off](../report-server/turn-reporting-services-features-on-or-off.md).  
  
###  <a name="effects-of-stopping-the-sql-server-agent"></a><a name="bkmk_stoppingagent"></a> Auswirkungen beim Beenden des SQL Server-Agents  
 Die geplante Berichtsverarbeitung verwendet standardmäßig den SQL Server-Agent. Wenn Sie den Dienst anhalten, werden keine neuen Verarbeitungsanforderungen zur Warteschlange hinzugefügt, außer Sie fügen sie programmgesteuert mithilfe der <xref:ReportService2010.ReportingService2010.FireEvent%2A> -Methode hinzu. Wenn Sie den Dienst neu starten, werden die Aufträge, die die Berichtsverarbeitungsanforderungen erstellen, fortgesetzt. Der Berichtsserver versucht nicht, Berichtsverarbeitungsaufträge neu zu erstellen, die möglicherweise in der Vergangenheit aufgetreten sind, während der SQL Server-Agent offline war. Wenn Sie den SQL Server-Agent für eine Woche anhalten, sind alle für diese Woche geplanten Vorgänge verloren.  
  
> [!NOTE]  
>  Die Funktionen, die der SQL Server-Agent für Reporting Services bereitstellt, können durch einen benutzerdefinierten Code ersetzt werden, der die <xref:ReportService2010.ReportingService2010.FireEvent%2A> -Methode verwendet, um der Warteschlange geplante Ereignisse hinzuzufügen.  
  
###  <a name="effects-of-stopping-the-report-server-service"></a><a name="bkmk_stoppingservice"></a> Auswirkungen beim Beenden des Berichtsserverdienstes  
 Wenn Sie den Berichtsserverdienst beenden, fährt der SQL Server-Agent fort, Berichtsverarbeitungsanforderungen der Warteschlange hinzuzufügen. Statusinformationen des SQL Server-Agents zeigen an, dass der Auftrag erfolgreich war. Da der Berichtsserverdienst jedoch beendet war, findet keine Berichtsverarbeitung statt. Die Anforderungen werden in der Warteschlange gesammelt, bis Sie den Berichtsserverdienst neu starten. Sobald Sie den Berichtsserverdienst neu gestartet haben, werden alle Berichtsverarbeitungsanforderungen, die sich in der Warteschlange befinden, nacheinander verarbeitet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen, Ändern und Löschen von Momentaufnahmen im Berichtsverlauf](../report-server/create-modify-and-delete-snapshots-in-report-history.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Data-Driven Subscriptions](data-driven-subscriptions.md)   
 [Zwischenspeichern von Berichten (SSRS)](../report-server/caching-reports-ssrs.md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [Zwischenspeichern von freigegebenen Datasets &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md)  
  
  
