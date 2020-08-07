---
title: Konfigurieren von Berichts-Manager (einheitlicher Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da33950953d0aa600c1b04cdf1a2633c2416c66d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619593"
---
# <a name="configure-report-manager-native-mode"></a>Konfigurieren des Berichts-Managers (einheitlicher Modus)
  Der Berichts-Manager ist eine Front-End-Webanwendung, in der Sie Berichte anzeigen, Berichtsserverinhalt verwalten und den Benutzerzugriff auf einen Berichtsserver im einheitlichen Modus gewähren können. Der Berichts-Manager wird mit dem Berichtsserver-Webdienst in derselben Berichtsserverinstanz installiert und kann konfiguriert werden, wenn Sie in Setup die Option **Standardkonfiguration im einheitlichen Modus installieren** auswählen. Sie können den Berichts-Manager auch nach der Installation konfigurieren. Dieses Thema enthält Informationen zu den folgenden Berichts-Manager-Konfigurationsszenarios:  
  
-   [Konfigurieren des Berichts-Managers für die Verwendung der Standard-URL](#ConfigureRMURL)  
  
     Der Berichts-Manager ist eine Webanwendung, auf die Benutzer in einem Webbrowser zugreifen. Sie müssen auf jeden Fall die URL definieren, die verwendet wird, um die Anwendung in einem Browserfenster zu öffnen. Die URL besteht aus einem Hostnamen, einem Port und einem virtuellem Verzeichnis. Zu den Standardwerten für diese URL gehören der Wert für den Hostnamen und der Wert für den Port, die Sie für die URL des Berichtsserver-Webdiensts definiert haben, sowie der Name des virtuellen Verzeichnisses **reports** . Wenn Sie über eine benannte Instanz verfügen, wird das virtuelle Verzeichnis **reports_instance**, wobei **instance** der Name der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Instanz ist.  
  
-   **Führen Sie den Berichts-Manager von einem Remotecomputer aus**. Abhängig von der Netzwerkkonfiguration müssen Sie auf Computern u. U. Port 80 aktivieren, damit Anforderungen vom Berichts-Manager zulässig sind.  
  
    > [!TIP]  
    >  Wenn Sie versuchen, auf den Berichts-Manager auf einem Remotecomputer zuzugreifen und im Browser Meldungen zu Verbindungsfehlern erhalten, sind häufig die Firewalleinstellungen dafür verantwortlich. Anweisungen finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](configure-a-firewall-for-report-server-access.md).  
  
     Aktivieren Sie ggf. auf beiden Computern Port 80, um Anforderungen über diesen Port zuzulassen. Anweisungen finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](configure-a-firewall-for-report-server-access.md).  
  
-   [Konfigurieren des Berichts-Managers für die Verwendung einer bestimmten Berichtsserver-URL](#ConfigureSpecificURL)  
  
     Standardmäßig stellt der Berichts-Manager eine Verbindung mit dem Berichtsserver-Webdienst her, der im selben Berichtsserverdienst ausgeführt wird. Der Berichts-Manager verwendet zum Herstellen der Verbindung die URL des Berichtsserver-Webdiensts. Wenn Sie mehrere URLs für den Berichtsserver-Webdienst definieren, verwendet der Berichts-Manager die zuletzt definierte URL. In manchen Bereitstellungen soll der Berichts-Manager jedoch möglicherweise über eine statische URL die Verbindung mit dem Webdienst herstellen. Dies kann z. B. der Fall sein, wenn Sie für einen bestimmten Port oder eine bestimmte IP-Adresse die Paketfilterung konfiguriert haben und alle Verbindungen mit dem Berichtsserver die definierten Filterregeln passieren sollen.  
  
-   [Verweisen auf einen Remoteberichtsserver mit dem Berichts-Manager](#ConfigureRemoteRS)  
  
     Standardmäßig bietet der Berichts-Manager Front-End-Zugriff auf den Berichtsserver-Webdienst, der in derselben Serverinstanz ausgeführt wird. Sie können den Berichts-Manager jedoch so konfigurieren, dass er die Verbindung mit einem Remoteberichtsserver-Webdienst herstellt, wenn der Webdienst und der Berichts-Manager in separaten Prozessen ausgeführt werden sollen oder wenn Sie den Serverzugriff für jeden Server unterschiedlich konfigurieren (z. B. wenn Sie den Berichts-Manager für Benutzer bereitstellen, die eine Extranet- oder Internetverbindung verwenden, und Sie zwischen dem Berichtsserver und dem Berichts-Manager eine Firewall platzieren möchten).  
  
-   [Anpassen von Formaten und Anwendungstitel](#ModifyTitle)  
  
     Es gibt beschränkte Möglichkeiten zum Anpassen des Berichts-Managers, des HTML-Berichts-Viewers und der Berichtssymbolleiste. Zu diesem Zweck können Sie die Formate ändern und den Anwendungstitel bearbeiten, der im Berichts-Manager angezeigt wird.  
  
-   [Berichts-Manager ausschalten](#DisableRM)  
  
     Wenn Sie eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanz installieren, die den einheitlichen Modus verwendet, wird der Berichts-Manager standardmäßig aktiviert. Sie können den Berichts-Manager jedoch deaktivieren, wenn Sie eine benutzerdefinierte Front-End-Anwendung haben, die eine entsprechende Funktionalität bietet, wenn Sie nur die SOAP- oder URL-Zugriffsschnittstellen für den Zugriff auf den Berichtsserver verwenden möchten oder wenn Sie einen Berichts-Manager aus einer anderen Berichtsserverinstanz verwenden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Für den Berichts-Manager müssen folgende Voraussetzungen erfüllt sein:  
  
-   Sie müssen einen minimal konfigurierten Berichtsserver haben. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers &#40;einheitlicher Reporting Services-Modus&#41;](configure-a-report-server-reporting-services-native-mode.md).  
  
-   Der Berichtsserver muss im einheitlichen Modus ausgeführt werden. Der Berichts-Manager kann mit einem Berichtsserver, der für den integrierten SharePoint-Modus konfiguriert ist, nicht verwendet werden. In SQL Server 2012 kann ein Berichtsserver nicht von einem Modus in den anderen wechseln. Wenn Sie den von der Umgebung verwendeten Berichtsservertyp ändern möchten, müssen Sie den gewünschten Berichtsservermodus installieren und dann die Berichtselemente vom alten Berichtsserver zum neuen Berichtsserver kopieren oder verschieben. Dieser Prozess wird in der Regel als „Migration“ bezeichnet. Die für das Migrieren erforderlichen Schritte hängen vom Modus ab, zu dem Sie migrieren, und von der Version, von der Sie migrieren. Weitere Informationen finden Sie unter [Upgrade and Migration Reporting Services](../install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Außerdem benötigen Sie Internet Explorer 7.0 oder höher mit aktivierter Skripterstellung. Weitere Informationen finden Sie [unter Planning for Reporting Services und Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
##  <a name="configure-report-manager-to-use-the-default-url"></a><a name="ConfigureRMURL"></a>Konfigurieren Sie Berichts-Manager, um die Standard-URL zu verwenden.  
 Standardmäßig besteht die URL des Berichts-Managers aus dem eindeutigen Namen eines virtuellen Verzeichnisses sowie dem Port und dem Hostnamen, der für den Berichtsserver-Webdienst definiert ist, der in derselben Instanz ausgeführt wird. In den meisten Fällen handelt es sich bei dem Hostnamen um den Netzwerknamen des Berichtsservercomputers, aber es kann sich auch im eine IP-Adresse oder einen Hostheader handeln, der den Computer auflöst. Verwenden Sie die Seite **Berichts-Manager-URL** im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, um den Berichts-Manager so zu konfigurieren, dass er die Standard-URL verwendet.  
  
#### <a name="to-configure-the-default-report-manager-url-and-virtual-directory"></a>So konfigurieren Sie die Standard-URL für den Berichts-Manager und das virtuelle Verzeichnis  
  
1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool, und stellen Sie eine Verbindung mit der Berichtsserverinstanz her.  
  
2.  Klicken Sie im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool auf **Berichts-Manager-URL** , um die Seite zum Konfigurieren der URL zu öffnen.  
  
3.  Geben Sie für den Berichts-Manager einen eindeutigen Namen des virtuellen Verzeichnisses ein.  
  
4.  Klicken Sie auf **Übernehmen**.  
  
5.  Wenn Sie [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] oder Windows Server 2008 verwenden, sind unter Umständen zusätzliche Schritte nötig, bevor Sie den Berichts-Manager lokal verwalten können. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="configure-report-manager-to-use-a-specific-report-server-url"></a><a name="ConfigureSpecificURL"></a>Konfigurieren von Berichts-Manager für die Verwendung einer bestimmten Berichts Server-URL  
 Wenn Sie URLs im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool konfigurieren, erkennt der Berichts-Manager automatisch neue und aktualisierte URLs für den Berichtsserver, der in derselben Instanz ausgeführt wird, und verwendet diese. Wenn Ihre Bereitstellung die Verwendung einer einzelnen, statischen URL für alle Berichtsserveranforderungen erfordert, können Sie diese URL in der Datei RSReportServer.config angeben.  
  
#### <a name="to-configure-a-static-report-server-url"></a>So konfigurieren Sie eine statische Berichtsserver-URL  
  
1.  Öffnen Sie die Datei **RSReportServer.config** in einem Text-Editor. Standardmäßig befindet sich diese Datei unter "\Programme\Microsoft SQL server\msrs12. \<*instancename*> ". \Reporting Services\ReportServer.  
  
2.  Suchen Sie `ReportServerURL`.  
  
3.  Ersetzen Sie die URL durch die URL der Berichtsserverinstanz.  
  
4.  Speichern Sie Ihre Änderungen, und schließen Sie die Datei.  
  
 Weitere Informationen zur Konfigurationsdatei finden Sie unter [Ändern einer Reporting Services Konfigurationsdatei &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) und [RSReportServer-Konfigurationsdatei](rsreportserver-config-configuration-file.md).  
  
##  <a name="configure-report-manager-to-use-a-remote-report-server"></a><a name="ConfigureRemoteRS"></a>Konfigurieren von Berichts-Manager für die Verwendung eines Remote Berichts Servers  
 In Bereitstellungskonfigurationen, in denen sich der Berichts-Manager und der Berichtsserver auf verschiedenen Computern befinden, benötigen Sie zwei separate Installationen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Der Berichts-Manager ist in den Berichtsserverdienst eingebettet und kann nicht alleine installiert werden. Wenn der Berichts-Manager auf einem anderen Computer in einem eigenen Prozess ausgeführt werden soll, müssen Sie einen weiteren Berichtsserver installieren. Bei beiden Serverinstanzen muss es sich um [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Berichtsserver handeln.  
  
#### <a name="to-connect-report-manager-to-a-remote-report-server-instance"></a>So stellen Sie eine Verbindung zwischen dem Berichts-Manager und einer Remote-Berichtsserverinstanz her  
  
1.  Installieren Sie zwei Berichtsserverinstanzen.  
  
2.  Konfigurieren Sie die erste Installation, die als Host für den Berichtsserver fungiert:  
  
    1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool.  
  
    2.  Klicken Sie auf **Webdienst-URL** , um einen Hostnamen, einen Port und ein virtuelles Verzeichnis für den Berichtsserver zu konfigurieren.  
  
    3.  Klicken Sie auf **Datenbank** , um die Berichtsserver-Datenbank zu konfigurieren.  
  
3.  Konfigurieren Sie die zweite Installation, die als Host für den Berichts-Manager fungiert:  
  
    1.  Starten Sie das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool.  
  
    2.  Klicken Sie auf **Berichts-Manager-URL** , um den Namen eines virtuellen Verzeichnisses für den Berichts-Manager einzugeben.  
  
     Konfigurieren Sie die Datenbank nicht. Testen Sie die URLs nicht.  
  
4.  Ändern Sie auf dem Berichts-Manager-Computer die Konfigurationseinstellungen in der Datei RSReportServer.config, um auf die Remote-Berichtsserverinstanz zu verweisen. Beim Start liest der Berichts-Manager die Konfigurationsdatei, um die URL zum Berichtsserver abzurufen:  
  
    1.  Öffnen Sie RSReportServer.config in einem Text-Editor. Standardmäßig befindet sich diese Datei unter "\Programme\Microsoft SQL server\msrs11. \<*instancename*> ". \Reporting Services\ReportServer.  
  
    2.  Suchen Sie `ReportServerURL`.  
  
    3.  Ersetzen Sie die URL durch die URL der Remote-Berichtsserverinstanz.  
  
    4.  Speichern Sie Ihre Änderungen, und schließen Sie die Datei.  
  
5.  > [!TIP]  
    >  Aktivieren Sie ggf. auf beiden Computern Port 80, um Anforderungen über diesen Port zuzulassen. Anweisungen finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](configure-a-firewall-for-report-server-access.md).  
  
6.  Starten Sie den Berichtsserver neu.  
  
7.  Öffnen Sie den Berichts-Manager in einem Browserfenster. Falls er bereits geöffnet ist, aktualisieren Sie den Browser, um zu überprüfen, ob der Berichts-Manager mit dem Remoteserver verbunden ist. Der Inhalt des Zielservers sollte angezeigt werden.  
  
8.  Deaktivieren Sie die Serverfunktionen, die Sie nicht verwenden:  
  
    -   Deaktivieren Sie auf dem Berichts-Manager-Computer `WebServiceAndHTTPAccessEnabled` und `ScheduleEventsAndReportDeliveryEnabled`.  
  
    -   Deaktivieren Sie auf dem Berichtsserver-Computer `ReportManagerEnabled`.  
  
 Weitere Informationen zu Deaktivieren von Funktionen finden Sie im Abschnitt [Aktivieren und Deaktivieren der Reporting Services-Funktionen](turn-reporting-services-features-on-or-off.md).  
  
##  <a name="customize-styles-or-application-title"></a><a name="ModifyTitle"></a>Anpassen von Stilen oder Anwendungs Titeln  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] bietet keine Unterstützung zum Anpassen der Stylesheets für den Berichts-Manager. Wenn Sie jedoch über Erfahrung in der Webentwicklung verfügen, können Sie die Stylesheets auf eigenes Risiko ändern. Weitere Informationen darüber, welche Dateien Formatinformationen enthalten, finden Sie unter [Anpassen von Stylesheets für den HTML-Viewer und Berichts-Manager](../customize-style-sheets-for-html-viewer-and-report-manager.md).  
  
 Der Berichts-Manager weist einen Anwendungstitel auf, der am oberen Seitenrand angezeigt wird. Der Standardwert für den Titel lautet **SQL Server Reporting Services**. Dieser Titel kann angepasst werden. Verwenden Sie die Seite Siteeinstellungen im Berichts-Manager, um den Titel zu ändern. Zum Ändern der Anwendungseinstellungen im Berichts-Manager müssen Sie der Rolle **Systemadministrator** zugewiesen sein, mit der Sie Eigenschaften auf der Seite Siteeinstellungen festlegen können. Zum Anzeigen des Anwendungstitels müssen Benutzer der Rolle **Systembenutzer** zugewiesen sein.  
  
#### <a name="to-modify-application-title"></a>So ändern Sie den Anwendungstitel  
  
1.  Melden Sie sich mit einem Konto an, dem auf dem Berichtsserver **Systemadministrator** -Berechtigungen zugewiesen sind.  
  
2.  Öffnen Sie Internet Explorer.  
  
3.  Geben Sie die Berichts-Manager-URL ein. Standardmäßig ist dies http:// \<**your-server-name**> /Reports, aber wenn Sie Reporting Services als benannte Instanz installiert haben, lautet die Standard-URL http:// \<**your-server-name**> /Reports \<**_instancename**> .  
  
4.  Klicken Sie auf **Siteeinstellungen**.  
  
5.  Ersetzen Sie auf der Registerkarte **Allgemein** unter **Name****SQL Server Reporting Services** durch einen anderen Namen.  
  
6.  Klicken Sie auf **Übernehmen**.  
  
##  <a name="turn-off-report-manager"></a><a name="DisableRM"></a>Berichts-Manager ausschalten  
 Sie können den Berichts-Manager deaktivieren, wenn Sie eine benutzerdefinierte Anwendung haben, die eine entsprechende Funktionalität bietet, oder wenn Sie die Berichts-Manager-Anwendung einer anderen Berichtsserverinstanz verwenden. Zum Deaktivieren des Berichts-Managers können Sie die Datei RSReportServer.config modifizieren.  
  
#### <a name="to-turn-off-report-manager"></a>So deaktivieren Sie den Berichts-Manager  
  
1.  Öffnen Sie die Datei RSReportServer.config in einem Text-Editor. Standardmäßig befindet sich diese Datei unter "\Programme\Microsoft SQL server\msrs11. \<*instancename*> ". \Reporting Services\ReportServer.  
  
2.  Suchen Sie **IsReportManagerEnabled**.  
  
3.  Stellen Sie den Wert auf **False**ein.  
  
4.  Speichern Sie Ihre Änderungen, und schließen Sie die Datei.  
  
 Weitere Informationen zum Ändern der Konfigurationsdatei finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md). Weitere Informationen zum Deaktivieren von Funktionen in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]finden Sie unter [Aktivieren und Deaktivieren der Reporting Services-Funktionen](turn-reporting-services-features-on-or-off.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Planen der Reporting Services-und Power View Browser Unterstützung &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)   
 [Konfigurieren einer URL &#40;SSRS-Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Überprüfen einer Reporting Services Installation](../install-windows/verify-a-reporting-services-installation.md)   
 [Anpassen von Stylesheets für den HTML-Viewer und Berichts-Manager](../customize-style-sheets-for-html-viewer-and-report-manager.md)   
 [Aktivieren und Deaktivieren von Reporting Services Features](turn-reporting-services-features-on-or-off.md)   
 [Verwalten eines Reporting Services Berichts Servers im einheitlichen Modus](manage-a-reporting-services-native-mode-report-server.md)   
 [RSReportServer-Konfigurationsdatei](rsreportserver-config-configuration-file.md)   
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung (SSRS)](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
  
  
