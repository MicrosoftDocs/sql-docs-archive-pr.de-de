---
title: Datenwarnungs-Manager für Warnungsadministratoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 32fd968f-1c0c-4ba8-851c-8a3b5e1fbbf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 050107d07e976b99609a456506eb7bbfbf5e20d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619645"
---
# <a name="data-alert-manager-for-alerting-administrators"></a>Datenwarnungs-Manager für Warnungsadministratoren
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] stellt den Datenwarnungs-Manager zum Verwalten von Datenwarnungen für SharePoint-Warnungsadministratoren bereit. Warnungsadministratoren können Informationen zu allen auf der Website gespeicherten Warnungen anzeigen und Warnungen löschen. Das folgende Bild zeigt SharePoint-Warnungsadministratoren die verfügbaren Funktionen im Datenwarnungs-Manager.

 ![Warnungs-Manager für SharePoint-Websiteadministratoren](media/rs-alertmanagersite.gif "Warnungs-Manager für SharePoint-Websiteadministratoren")

 Wenn die Website für Datenwarnungen aktiviert ist, werden zwei SharePoint-Seiten (MyDataAlerts.aspx und SiteDataAlerts.aspx) erstellt und der SharePoint-Website hinzugefügt. SiteDataAlerts.aspx entspricht dem Datenwarnungs-Manager für Warnungsadministratoren. Warnungsadministratoren können den Datenwarnungs-Manager über die SharePoint-Seite "Siteeinstellungen" öffnen. Warnungsadministratoren müssen die SharePoint-Berechtigung "Benachrichtigungen verwalten" besitzen, um den Datenwarnungs-Manager zu öffnen.

 Sie können den Datenwarnungs-Manager auch direkt über eine URL öffnen. Die Syntax der URL wird nachfolgend angezeigt:

 `http: //<site name>/_layouts/ReportServer/ SiteDataAlerts.aspx`

> [!NOTE]
>  Als Warnungsadministrator können Sie Information Workern die Berechtigung erteilen, auf die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Datenwarnungsfunktionen zuzugreifen. Weitere Informationen zu den erforderlichen Berechtigungen finden Sie unter [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md).

##  <a name="viewing-data-alert-information"></a><a name="ViewingAlerts"></a> Anzeigen von Datenwarnungsinformationen
 Wenn Reporting Services installiert ist und in SharePoint konfiguriert wird, enthält die SharePoint-Seite "Siteeinstellungen" die **Reporting Services** -Optionen. Warnungsadministratoren klicken in Reporting Services auf die Option **Datenwarnungen verwalten** , um den Datenwarnungs-Manager zu öffnen. Das folgende Bild zeigt, wie sich der Datenwarnungs-Manager auf der Seite "Siteeinstellungen" öffnen lässt.

 ![Reporting Services-Abschnitt der Seite „Siteeinstellungen“](media/rs-sitesettings.gif "Reporting Services-Abschnitt der Seite „Siteeinstellungen“")

 Der Datenwarnungs-Manager umfasst eine Tabelle mit dem Warnungsnamen, Berichtsnamen, Namen des Warnungseigentümers, der Nummer der Warnmeldung, der letzten Ausführung der Warnung, der letzten Änderung der Warnungsdefinition und dem Status der Warnmeldung. Wenn die Datenwarnung nicht generiert oder gesendet werden kann, enthält die Statusspalte Informationen zum Fehler und hilft Ihnen bei der Behebung des Problems mit der Warnung. Weitere Informationen finden Sie unter [Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).

 In der folgenden Tabelle werden Beispieldaten einer Tabelle im Datenwarnungs-Manager angezeigt. Tritt ein Fehler auf, werden die Fehlermeldung und der Bezeichner des Eintrags im Protokoll (eine GUID) in das Feld **Status** der Tabelle aufgenommen.

|Name der Warnung|Berichtsname|Created By|Gesendete Warnungen|Zuletzt ausgeführt|Zuletzt geändert|Status|
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|
|SalesQTR|SalesByTerritoryAndQTR|Lauren Johnson|4|6/12/2011|6/1/2011|Die letzte Warnung war erfolgreich, und die Warnung wurde gesendet.|
|UnitsSold|ProductsSalesByQTR|Michael Blythe|2|7/1/2011|6/28/2011|Die letzte Warnung wurde erfolgreich ausgeführt, aber die Daten blieben unverändert, und es wurde keine Warnung gesendet.|
|InventoryCount|StockStatusByQTR|Lauren Johnson|7|7/10/2011|7/2/2011|\<error message>Die Protokolldatei enthält ausführliche Informationen zum Fehler. Verweisen Sie auf den Protokolleintrag mit dem Bezeichner: \<GUID> .|
|TopPromotion|PromotionTracking|Cristian Petculescu|0||5/23/2011|Die Warnung wurde erstellt.|

 Weitere Informationen finden Sie unter [Verwalten aller Daten Warnungen auf einer SharePoint-Website im datenwarnungs-Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).

 Sie können alle von Websitebenutzern erstellten Warnungen anzeigen. Sie wählen erst einen Benutzer und wählen dann, ob alle Warnungen oder nur Warnungen für einen bestimmten Bericht angezeigt werden sollen.


##  <a name="delete-data-alerts"></a><a name="DeleteAlerts"></a>Löschen von Daten Warnungen
 Warnungsdefinitionen lassen sich über den Datenwarnungs-Manager löschen. Jede Datenwarnungsdefinition hat einen Eigentümer (den SharePoint-Benutzer, der sie erstellt hat). Eigentümer können nur die von ihnen erstellten Warnungsdefinitionen löschen. Weitere Informationen finden Sie unter [Verwalten meiner Datenwarnungen im Datenwarnungs-Manager](manage-my-data-alerts-in-data-alert-manager.md).

 Ein SharePoint-Warnungsadministrator kann Warnungsdefinitionen auflisten und dann löschen, die von einem beliebigen Benutzer der Website erstellt wurden. Weitere Informationen finden Sie unter [Verwalten aller Daten Warnungen auf einer SharePoint-Website im datenwarnungs-Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md) .

 Nach dem Löschen der Warnungsdefinition werden keine weiteren Warnungen gesendet. Wenn Sie jedoch die Warnungsdatenbank abfragen, stellen Sie möglicherweise fest, dass die Warnungsdefinition immer noch vorhanden ist. Der Warndienst führt den Cleanup nach einem Zeitplan durch. Die Warnungsdefinition wird beim nächsten Cleanup dauerhaft gelöscht. Das Standardintervall für den Cleanup beträgt 20 Minuten. Dieses und andere Cleanupintervalle sind konfigurierbar. Weitere Informationen finden Sie unter [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md).


##  <a name="related-tasks"></a><a name="HowTo"></a> Verwandte Aufgaben
 In diesem Abschnitt ist eine Prozedur aufgeführt, die das Verwalten der Warnungen zeigt.

-   [Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)


## <a name="see-also"></a>Weitere Informationen
 [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md)


