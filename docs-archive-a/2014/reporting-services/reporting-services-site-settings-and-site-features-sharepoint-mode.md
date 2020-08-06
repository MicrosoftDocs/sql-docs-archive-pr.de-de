---
title: Reporting Services Site Einstellungen und Website Features (SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 11b429a31d38941803bf3b412aff56c2ad064bc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619572"
---
# <a name="reporting-services-site-settings-and-site-featuressharepoint-mode"></a>Einstellungen und Funktionen für Reporting Services-Websites (SharePoint-Modus)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus bietet mehrere benutzerdefinierte Funktionen auf Websiteebene und Websitefunktionen, die auf der Seite mit den SharePoint-Websiteeinstellungen verwaltet werden können. Die Einstellungen gelten auf der gesamten Website und für alle [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen. Sie müssen über Inhalts-Manager- und Systemadministratorberechtigungen verfügen, um diese Seite anzuzeigen.  
  
|Siteeinstellung|BESCHREIBUNG|  
|------------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Siteeinstellungen|In diesem Thema beschriebene websiteweite Einstellungen.|  
|Datenwarnungen verwalten|Verwaltung der Datenwarnungsfunktion.|  
|Berichtsserver-Dateisynchronisierung|Eine Funktion auf Websiteebene, die standardmäßig deaktiviert wird.<br /><br /> Synchronisiert Berichtsserverdateien (.rdl, .rsds, .smdl, .rsd, .rsc, .rdlx) einer SharePoint-Dokumentbibliothek mit dem Berichtsserver, wenn Dateien direkt in der Dokumentbibliothek hinzugefügt oder aktualisiert werden.<br /><br /> Weitere Informationen finden Sie unter [Aktivieren der Berichts Server Dateisynchronisierung Funktion in der SharePoint-zentral Administration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) .|  
  
## <a name="to-open-the-reporting-services-site-settings-page"></a>So öffnen Sie die Reporting Services-Seite Siteeinstellungen  
  
1.  Klicken Sie im Menü **Website Aktionen** der SharePoint-Website auf **Website Einstellungen**.  
  
2.  Klicken Sie im Abschnitt **Reporting Services** auf **Einstellungen für Reporting Services-Websites**.  
  
## <a name="options-for-reporting-services-site-settings"></a>Optionen für Einstellungen für Reporting Services-Websites  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Download des RSClientPrint-ActiveX-Steuerelements aktivieren**|Vom Steuerelement wird ein benutzerdefiniertes Dialogfeld zum Drucken angezeigt, das die in Dialogfeldern zum Drucken üblichen Funktionen enthält. Dazu zählen Druckvorschau, Seitenauswahl zum Angeben bestimmter Seiten und Bereiche, Seitenränder und Ausrichtung. Weitere Informationen zum Steuerelement finden Sie unter [Using the RSClientPrint Control in Custom Applications](report-server-web-service/net-framework/using-the-rsclientprint-control-in-custom-applications.md)|  
|**Remotefehler im lokalen Modus aktivieren**|Zeigen Sie bei der Ausführung im lokalen Modus ausführliche Fehlermeldungen auf Remotecomputern an, oder blenden Sie sie aus. Wenn ungefähr folgende Fehlermeldung angezeigt wird, ist die Aktivierung von Remotefehlern möglicherweise nützlich:<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Barrierefreiheit-Metadaten für Berichte aktivieren**|Barrierefreiheit-Metadaten in der HTML-Ausgabe für Berichte aktivieren|  
|**Genaue Größenanpassung der Datenvisualisierung für Berichte aktivieren**|Konfigurieren Sie das Verhalten für die Datenvisualisierungsanpassung in einem Tablix, damit sie genau passt. Dies schließt Diagramm, Messgerät und Karte ein. Ist die Funktion deaktiviert, bewirkt das Verhalten für Datenvisualisierungen die ungefähre Anpassung, wodurch möglicherweise Leerzeichen auftreten. Diese Einstellung gilt nur für das Rendern im Berichts-Viewer-Webpart. Sie müssen zum Verwalten dieses Verhaltens für serverseitiges Rendering die Datei **rsreportserver.config** ändern. Weitere Informationen finden Sie unter<br /><br /> [RSReportServer-Konfigurationsdatei](report-server/rsreportserver-config-configuration-file.md).<br /><br /> [Anpassen von Renderingerweiterungsparametern in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md).<br /><br /> [HTML-Geräte Informationseinstellungen](html-device-information-settings.md).<br /><br /> Die Aktivierung der genauen Anpassung hat möglicherweise Auswirkungen auf die Leistung, da die Verarbeitung zur Ermittlung der genauen Größe möglicherweise länger als eine ungefähre Anpassung dauert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten einer Reporting Services SharePoint-Dienst Anwendung](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
  
