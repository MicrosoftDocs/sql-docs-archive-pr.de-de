---
title: Hinzufügen von Berichts Server-Inhaltstypen zu einer Bibliothek (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e0ee56c235a54920fba5389a61f300eeaa65329
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723633"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a>Hinzufügen von Berichtsserver-Inhaltstypen zu einer Bibliothek (Reporting Services im integrierten SharePoint-Modus)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Für SharePoint werden vordefinierte Inhaltstypen bereitgestellt, die zum Verwalten freigegebener Datenquellendateien (RSDS), Berichtsmodelldateien (SMDL) und Berichtsgenerator-Berichtsdefinitionsdateien (RDL) verwendet werden können. Wenn einer Bibliothek ein Inhaltstyp ( **Berichts-Generator-Bericht**, **Berichtsmodell**und **Berichtsdatenquelle** ) hinzugefügt wird, wird der Befehl **Neu** aktiviert, sodass Sie neue Dokumente des betreffenden Typs erstellen können.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint-Modus  
  
 Wenn Sie einer Bibliothek Inhaltstypen hinzufügen möchten, müssen Sie Websiteadministrator sein oder über die Berechtigungsstufe "Vollzugriff" verfügen.  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypen sowie die Verwaltung dieser Inhaltstypen werden in allen Dokumentbibliotheken für vorhandene Websitesammlungen, die von folgenden **Business Intelligence Center** -Websitevorlagen erstellt wurden, automatisch aktiviert:  
  
 Für Websites, die nach der Integration von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] erstellt wurden, sind die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypen nicht aktiviert.  
  
> [!TIP]  
>  Wenn Sie zuvor **keine** Inhaltstypen für eine Bibliothek konfiguriert haben, aktivieren Sie zunächst die Verwaltung von Inhaltstypen und dann die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypen. Siehe die Verfahren zum Aktivieren der Inhaltstypverwaltung in einer einzelnen Dokumentbibliothek.  
  
 **Kurzvideo:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w) ((SSRS) Aktivieren von Inhaltstypen in SharePoint2010.wmv).  
  
 **In diesem Thema:**  
  
-   [Aktivieren von Inhaltstypen in allen Dokumentbibliotheken eines vorhandenen Business Intelligence Centers](#bkmk_enable_all)  
  
-   [So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2013)](#bkmk_enable_content_management)  
  
-   [So fügen Sie Reporting Services-Inhaltstypen hinzu (SharePoint 2013)](#bkmk_add_single)  
  
-   [So aktivieren Sie die Inhaltstypverwaltung für eine einzelne Dokumentbibliothek (SharePoint 2010)](#bkmk_enable_content_management_2010)  
  
-   [So fügen Sie Berichtsserver-Inhaltstypen hinzu (SharePoint 2010)](#bkmk_add_single_2010)  
  
-   [So aktivieren Sie Inhaltstypen und die Inhaltsverwaltung für mehrere BI-Websites](#bkmk_enable_multiple_sites)  
  
##  <a name="enable-content-types-in-all-document-libraries-in-an-existing-bi-center"></a><a name="bkmk_enable_all"></a>Aktivieren von Inhaltstypen in allen Dokument Bibliotheken eines vorhandenen BI Centers  
  
1.  Um Inhaltstypen sowie die Inhaltsverwaltung in allen Dokumentbibliotheken einer vorhandenen **Business Intelligence Center** -Website zu aktivieren, können Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Integrationsfunktion aktivieren/deaktivieren.  
  
2.  Wechseln Sie zu **Siteeinstellungen**.  
  
    -   Klicken Sie in SharePoint 2013 auf das **Einstellungssymbol**. ![SharePoint-Einstellungen](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen")  
  
    -   Klicken Sie in SharePoint 2010 auf **Websiteaktionen**und auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Website Sammlungs Features**.  
  
4.  Suchen Sie die **Berichtsserver-Integrationsfunktion** , und klicken Sie auf **Deaktivieren**.  
  
     ![rs_Berichtsserver_Integration_aktiviert](media/rs-reportserver-integration-active.gif "rs_Berichtsserver_Integration_aktiviert")  
  
5.  Aktualisieren Sie den Browser, und klicken Sie unter **Berichtsserver-Integrationsfunktion** auf **Aktivieren**.  
  
    ![Deaktivieren](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2013"></a><a name="bkmk_enable_content_management"></a>So aktivieren Sie die Inhaltstyp Verwaltung für eine einzelne Dokumentbibliothek (SharePoint 2013)  
  
1.  Öffnen Sie die Bibliothek, für die Sie mehrere Inhaltstypen aktivieren möchten.  
  
2.  Klicken Sie im Menüband auf **Bibliothek** .  
  
     ![rs_SharePoint2013_MenübandBibliothek](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_MenübandBibliothek")  
  
3.  Klicken Sie im Menüband **Bibliothek** auf **Bibliothekeinstellungen**. Falls **Bibliothekseinstellungen** nicht angezeigt wird oder die Schaltfläche deaktiviert ist, sind Sie nicht berechtigt, Bibliothekseinstellungen sowie Inhaltstypen zu konfigurieren.  
  
     ![rs_SharePoint2013_Bibliothekseinstellungen](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_Bibliothekseinstellungen")  
  
4.  Klicken Sie im Abschnitt **Allgemeine Einstellungen** auf **Erweiterte Einstellungen**.  
  
     ![rs_SharePoint2013_Bibliothekseinstellungen_ErweiterteEinstellungen](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_Bibliothekseinstellungen_ErweiterteEinstellungen")  
  
5.  Wählen Sie im Abschnitt **Inhaltstypen** die Option **Ja** aus, um die Verwaltung von Inhaltstypen zuzulassen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="to-add-reporting-services-content-types-sharepoint-2013"></a><a name="bkmk_add_single"></a>So fügen Sie Reporting Services Inhaltstypen hinzu (SharePoint 2013)  
  
1.  Öffnen Sie die Bibliothek, für die Sie Reporting Services-Inhaltstypen hinzufügen möchten.  
  
2.  Klicken Sie im Menüband auf **Bibliothek**.  
  
3.  Klicken Sie auf **Bibliothekeinstellungen**.  
  
4.  Klicken Sie unter **Inhaltstypen**auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**.  
  
5.  Wählen Sie unter **Websiteinhaltstypen auswählen aus**die Option **SQL Server Reporting Services-Inhaltstypen**aus.  
  
6.  Klicken Sie in der Liste **Verfügbare Websiteinhaltstypen** auf **Berichts-Generator**, und klicken Sie dann auf **Hinzufügen** , um den ausgewählten Inhaltstyp in die Liste **Hinzuzufügende Inhaltstypen** zu verschieben.  
  
7.  Wiederholen Sie den vorherigen Schritt, um die Inhaltstypen **Berichtsmodell** und **Berichtsdatenquelle** hinzuzufügen.  
  
8.  Nachdem Sie alle gewünschten Inhaltstypen hinzugefügt haben, klicken Sie auf **OK**.  
  
9. > [!NOTE]  
    >   Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypgruppe **SQL Server Reporting Services-Inhaltstypen** wird unter folgenden Bedingungen auf der Seite **Inhaltstypen hinzufügen** nicht angezeigt:  
  
    -   Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte wurde nicht installiert. Weitere Informationen finden Sie unter [installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Das Thema enthält Informationen zum Installieren des Add-Ins und es wird Schritt für Schritt erläutert, wie Sie eine Nur-Datei-Installation des Add-Ins ausführen können, um Probleme zu umgehen.  
  
    -   Das Add-In wird installiert, aber die **Funktion für die Berichtsserverintegration** für die Websitesammlung ist nicht aktiv. Prüfen Sie die Websitesammlungsfunktion unter **Siteeinstellungen**.  
  
    -   Der Bibliothek wurden bereits sämtliche [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstypen hinzugefügt. Wenn alle Inhaltstypen einer Bibliothek angehören, wird die Gruppe von der Seite **Inhaltstypen hinzufügen** entfernt. Nachdem mindestens ein [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Inhaltstyp gelöscht wurde, wird die Gruppe **SQL Server Reporting Services-Inhaltstypen** auf der Seite **Inhaltstypen hinzufügen** angezeigt.  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2010"></a><a name="bkmk_enable_content_management_2010"></a>So aktivieren Sie die Inhaltstyp Verwaltung für eine einzelne Dokumentbibliothek (SharePoint 2010)  
  
1.  Öffnen Sie die Bibliothek, für die Sie mehrere Inhaltstypen aktivieren möchten. Auf der Menüleiste der Bibliothek sollten die folgenden Menüs angezeigt werden: **Neu**, **Upload**, **Aktionen**und **Einstellungen**. Falls **Einstellungen**nicht angezeigt wird, sind Sie nicht berechtigt, Inhaltstypen hinzuzufügen.  
  
2.  Klicken Sie im Menüband **Bibliothekstools** auf **Bibliothek**.  
  
     ![rs_SharePoint2010_MenübandBibliothek](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_MenübandBibliothek")  
  
3.  Klicken Sie in der Menübandgruppe **Einstellungen** auf **Bibliothekseinstellungen**.  
  
4.  Klicken Sie unter **Allgemeine Einstellungen**auf **Erweiterte Einstellungen**.  
  
5.  Wählen Sie im Abschnitt **Inhaltstypen** die Option **Ja** aus, um die Verwaltung von Inhaltstypen zuzulassen.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="to-add-report-server-content-types-sharepoint-2010"></a><a name="bkmk_add_single_2010"></a>So fügen Sie Berichts Server-Inhaltstypen hinzu (SharePoint 2010)  
  
1.  Öffnen Sie die Bibliothek, für die Sie Reporting Services-Inhaltstypen hinzufügen möchten.  
  
2.  Klicken Sie auf den Registerkarten des Menübands **Bibliothekstools** auf die Registerkarte **Bibliothek**.  
  
3.  Klicken Sie in der Menübandgruppe **Einstellungen** auf **Bibliothekseinstellungen**.  
  
4.  Klicken Sie unter **Inhaltstypen**auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**.  
  
5.  Klicken Sie im Abschnitt **Inhaltstypen auswählen** in der Liste **Websiteinhaltstypen auswählen aus**auf den Pfeil, um **SQL Server Reporting Services-Inhaltstypen**auszuwählen.  
  
6.  Klicken Sie in der Liste **Verfügbare Websiteinhaltstypen** auf **Berichts-Generator**, und klicken Sie dann auf **Hinzufügen** , um den ausgewählten Inhaltstyp in die Liste **Hinzuzufügende Inhaltstypen** zu verschieben.  
  
7.  Wiederholen Sie den vorherigen Schritt, um die Inhaltstypen **Berichtsmodell** und **Berichtsdatenquelle** hinzuzufügen.  
  
8.  Nachdem Sie alle gewünschten Inhaltstypen hinzugefügt haben, klicken Sie auf **OK**.  
  
##  <a name="to-enable-content-types-and-content-management-for-multiple-bi-sites"></a><a name="bkmk_enable_multiple_sites"></a>So aktivieren Sie Inhaltstypen und die Inhalts Verwaltung für mehrere BI-Websites  
  
1.  Bei Berichtsservern unter SQL Server Reporting Services 2008 und 2008 R2 können Inhaltstypen sowie die Inhaltsverwaltung für mehrere Business Intelligence Center-Websites aktiviert werden:  
  
2.  Klicken Sie in der SharePoint-Zentraladministration auf **Allgemeine Anwendungseinstellungen**. Klicken Sie im Abschnitt **SQL Server Reporting Services (2008 und 2008 R2)** auf **Reporting Services-Integration**.  
  
     ![rs_allgemeine_Appeinstellungen](media/rs-general-app-settings.gif "rs_allgemeine_Appeinstellungen")  
  
3.  Klicken Sie auf **Funktion in allen vorhandenen Websitesammlungen aktivieren**.  
  
     ![rs_allgemeine_Appeinstellungen_alte_Integrationen](media/rs-general-app-settings-old-integrations.gif "rs_allgemeine_Appeinstellungen_alte_Integrationen")  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Referenz zu SharePoint-Website-und Listen Berechtigungen für Berichts Server Elemente](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Starten Sie Berichts-Generator &#40;Berichts-Generator&#41;](report-builder/start-report-builder.md)  
  
  
