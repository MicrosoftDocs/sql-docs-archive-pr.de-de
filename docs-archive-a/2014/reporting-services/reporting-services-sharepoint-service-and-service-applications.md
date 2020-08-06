---
title: Reporting Services SharePoint-Dienst und-Dienst Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5654764f7913002cdae58d3264848250a292c585
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630518"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Reporting Services-SharePoint-Dienst und -Dienstanwendungen
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus basiert auf der SharePoint-Dienstarchitektur und verwendet einen SharePoint-Dienst sowie mindestens eine Dienstanwendung. Beim Erstellen einer Dienstanwendung wird der Dienst verfügbar gemacht und die Datenbank der Dienstanwendung generiert. Sie können mehrere Reporting Services-Dienstanwendungen erstellen, doch für die meisten Bereitstellungsszenarien ist eine Dienstanwendung ausreichend.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Erstellen einer Reporting Services-Dienst Anwendung](#bkmk_createapp)  
  
-   [Ändern der Zuordnungen der Dienst Anwendung mit einer Proxy Gruppe](#bkmk_associations)  
  
-   [Bearbeiten von Eigenschaften der Dienst Anwendung](#bkmk_editserviceapplication)  
  
-   [So erstellen Sie eine Reporting Services-Dienstanwendung mit PowerShell](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [Verwandte Aufgaben](#bkmk_related)  
  
##  <a name="creating-a-reporting-services-service-application"></a><a name="bkmk_createapp"></a>Erstellen einer Reporting Services-Dienst Anwendung  
 Sie können die SharePoint-Zentraladministrations- oder PowerShell-Skripts verwenden, um die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendungen zu erstellen. Weitere Informationen zum Verwenden der SharePoint-Zentraladministration finden Sie im Abschnitt „Erstellen einer Reporting Services-Dienstanwendung“ in [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md). Lesen Sie den PowerShell-Abschnitt weiter unten in diesem Thema, um ein Beispiel zu einem PowerShell-Skript für die Erstellung von Dienstanwendungen zu erhalten.  
  
##  <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a><a name="bkmk_associations"></a>Ändern der Zuordnungen der Dienst Anwendung mit einer Proxy Gruppe  
 Die Seite Neu zum Erstellen einer Dienstanwendung enthält den Abschnitt **Zuordnung der Webanwendung**. Dieser Abschnitt ermöglicht es Ihnen, die Dienstanwendung im Rahmen der Erstellung zuzuordnen. Führen Sie die folgenden Schritte aus, um die Zuordnung zu ändern und der Dienstanwendung eine Kundenkonfiguration zuzuweisen. Sie können dasselbe allgemeine Verfahren auch verwenden, um den Proxy der Standardgruppe hinzuzufügen, anstatt die Zuordnung der Dienstanwendung in eine benutzerdefinierte Gruppe zu ändern.  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Anwendungsverwaltung auf **Zuordnungen von Dienstanwendungen konfigurieren**.  
  
2.  Ändern Sie auf der Seite Zuordnungen von Dienstanwendungen die Ansicht in **Dienstanwendungen**.  
  
3.  Suchen und klicken Sie auf den Namen der neuen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung. Sie können auch auf den Namen der Anwendungsproxygruppe **default** klicken, um den Proxy zur Standardgruppe hinzuzufügen, anstatt die folgenden Schritte auszuführen.  
  
4.  Wählen Sie im Auswahlfeld **Folgende Gruppe von Verbindungen bearbeiten** die Option **Benutzerdefiniert**.  
  
5.  Aktivieren Sie das Kontrollkästchen für den Proxy, und klicken Sie auf **OK**.  
  
##  <a name="edit-service-application-properties"></a><a name="bkmk_editserviceapplication"></a>Bearbeiten von Eigenschaften der Dienst Anwendung  
 Sie können die Eigenschaftenseite der Dienstanwendung erneut öffnen, um die Eigenschaften zu ändern.  
  
1.  Klicken Sie in der SharePoint-zentral Administration in der Gruppe Anwendungs Verwaltung auf **Dienst Anwendungen verwalten**.  
  
2.  Wählen Sie die Dienstanwendung aus, indem Sie zum Auswählen der ganzen Zeile auf die Typspalte klicken. Wenn Sie auf den Namen der Anwendung klicken, wird die Seite mit Verwaltungsoptionen für den Dienst und nicht die Eigenschaftenseite der Dienstanwendung geöffnet.  
  
3.  Klicken Sie im Menüband Dienstanwendungen auf **Eigenschaften**.  
  
##  <a name="to-create-a-reporting-services-service-application-using-powershell"></a><a name="bkmk_powershell_create_ssrs_serviceapp"></a>So erstellen Sie eine Reporting Services-Dienst Anwendung mithilfe von PowerShell  
 Sie können die Dienstanwendung und den Proxy mithilfe von PowerShell erstellen. Im Beispiel unten wird davon ausgegangen, dass Sie wissen, welchen Anwendungspool Sie für die Dienstanwendung konfigurieren möchten.  
  
1.  Fügen Sie das Anwendungspoolobjekt des Anwendungspoolnamens einer Variablen hinzu, die an die neue Aktion übergeben wird.  
  
    ```powershell
    $appPoolName = Get-SPServiceApplicationPool "<application pool name>"  
    ```  
  
2.  Erstellen Sie die Dienstanwendung mit einem von Ihnen angegebenen Namen und Anwendungspool.  
  
    ```powershell
    New-SPRSServiceApplication -Name 'MyServiceApplication' -ApplicationPool $appPoolName -DatabaseName 'MyServiceApplicationDatabase' -DatabaseServer '<Server Name>'  
    ```  
  
3.  Rufen Sie das neue Dienstanwendungsobjekt ab, und übergeben Sie das Objekt in die Pipe des neuen Proxy-Cmdlets.  
  
    ```powershell
    Get-SPRSServiceApplication -name MyServiceApplication | New-SPRSServiceApplicationProxy "MyServiceApplicationProxy"  
    ```  
  
##  <a name="related-tasks"></a><a name="bkmk_related"></a> Verwandte Aufgaben  
  
|Aufgabe|Link|  
|----------|----------|  
|Verwalten der Einstellungen der Dienstanwendung|[Verwalten einer Reporting Services SharePoint-Dienst Anwendung](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|Führen Sie für die Dienstanwendung (einschließlich zugehöriger Komponenten wie Verschlüsselungsschlüssel und Proxy) eine Sicherung und Wiederherstellung aus.|[Sichern und Wiederherstellen von Reporting Services-SharePoint-Dienstanwendungen](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
