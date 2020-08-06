---
title: Hinzufügen, löschen oder Freigeben eines Verbindungs-Managers in einem Paket | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], adding
- adding connection managers
ms.assetid: 6f2ba4ea-10be-4c40-9e80-7efcf6ee9655
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 145d4e64310c41b5b74e7bd3ac9e0154a0390bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617248"
---
# <a name="add-delete-or-share-a-connection-manager-in-a-package"></a>Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket
  In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist eine Vielzahl an Verbindungs-Managern zum Herstellen von Verbindungen mit verschiedenen Datenquellen enthalten, beispielsweise mit relationalen Datenbanken, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbanken und Dateien im CSV- und XML-Format. Ein Verbindungs-Manager kann auf Paketebene oder auf Projektebene erstellt werden. Ein auf Projektebene erstellter Verbindungs-Manager ist für alle Pakete im Projekt verfügbar. Ein auf Paketebene erstellter Verbindungs-Manager ist nur für das betreffende Paket verfügbar.  
  
 Auf Projektebene erstellte Verbindungs-Manager werden anstelle von Datenquellen verwendet, um Verbindungen mit Quellen freizugeben. Damit ein Verbindungs-Manager auf Projektebene hinzugefügt werden kann, muss das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt das Projektbereitstellungsmodell verwenden. Wenn ein Projekt für die Verwendung des Modells konfiguriert wurde, wird der Ordner **Verbindungs-Manager** im **Projektmappen-Explorer**angezeigt, und der Ordner **Datenquellen** wird aus dem **Projektmappen-Explorer**entfernt.  
  
> [!NOTE]  
>  Wenn Sie Datenquellen im Paket verwenden möchten, müssen Sie das Projekt in das Paketbereitstellungsmodell konvertieren.  
>   
>  Weitere Informationen zu den beiden Modellen finden Sie unter [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md). Weitere Informationen zum Konvertieren eines Projekts in das Projektbereitstellungsmodell finden Sie unter [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 Die folgenden Prozeduren gelten für alle Typen von Verbindungs-Managern und beschreiben die Vorgehensweise bei folgenden Aufgaben:  
  
-   [So fügen Sie bei der Erstellung eines Pakets einen Verbindungs-Manager hinzu](#wizard)  
  
-   [So fügen Sie einen Verbindungs-Manager zu einem vorhandenen Paket hinzu](#package)  
  
-   [So fügen Sie einen Verbindungs-Manager auf Projektebene hinzu](#project)  
  
-   [So erstellen Sie einen Parameter für eine Verbindungs-Manager-Eigenschaft](#parameter)  
  
-   [So löschen Sie einen Verbindungs-Manager aus einem Paket](#DeletePackageLevel)  
  
-   [So löschen Sie einen gemeinsam genutzten Verbindungs-Manager (Verbindungs-Manager auf Projektebene)](#DeleteProjectLevel)  
  
##  <a name="to-add-a-connection-manager-when-creating-a-package"></a><a name="wizard"></a>So fügen Sie einen Verbindungs-Manager hinzu, wenn Sie ein Paket erstellen  
  
-   Verwenden des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import-/Export-Assistenten  
  
     Die Assistenten helfen Ihnen nicht nur bei dem Erstellen und Konfigurieren eines Verbindungs-Managers, sondern auch beim Erstellen und Konfigurieren der Quellen und Ziele, die einen Verbindungs-Manager verwenden. Weitere Informationen finden Sie unter [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).  
  
##  <a name="to-add-a-connection-manager-to-an-existing-package"></a><a name="package"></a>So fügen Sie einen Verbindungs-Manager zu einem vorhandenen Paket hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Ablaufsteuerung** , **Datenfluss** oder **Ereignishandler** , um den Bereich **Verbindungs-Manager** anzuzeigen.  
  
4.  Klicken Sie mit der rechten Maustaste an eine beliebige Stelle im Bereich **Verbindungs-Manager** , und gehen Sie anschließend wie folgt vor:  
  
    -   Klicken Sie auf den Verbindungs-Manager-Typ, den Sie dem Paket hinzufügen möchten.  
  
         Oder  
  
    -   Wenn der Typ, den Sie hinzufügen möchten, nicht aufgelistet ist, klicken Sie auf **Neue Verbindung** . Das Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** wird aufgerufen. Wählen Sie einen Verbindungs-Manager-Typ aus, und klicken Sie dann auf **OK**.  
  
     Das benutzerdefinierte Dialogfeld für den ausgewählten Verbindungs-Manager-Typ wird aufgerufen. Weitere Informationen zu den Verbindungs-Manager-Typen und den verfügbaren Optionen finden Sie in der folgenden Optionentabelle.  
  
    |Ziel-Editor für Dimensionsverarbeitung|Tastatur|  
    |------------------------|-------------|  
    |[ADO-Verbindungs-Manager](connection-manager/ado-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md)|[ADO.NET-Verbindungs-Manager konfigurieren](configure-ado-net-connection-manager.md)|  
    |[Analysis Services-Verbindungs-Manager](connection-manager/analysis-services-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Analysis Services-Verbindungs-Manager hinzufügen“](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Excel-Verbindungs-Manager](connection-manager/excel-connection-manager.md)|[Verbindungs-Manager-Editor für Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)|[Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Verbindungs-Manager für mehrere Dateien](connection-manager/multiple-files-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Dateiverbindungs-Manager hinzufügen“](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Verbindungs-Manager für Flatfiles](connection-manager/flat-file-connection-manager.md)|[Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Verbindungs-Manager für mehrere Flatfiles](connection-manager/multiple-flat-files-connection-manager.md)|[Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Allgemein“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Spalten“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[FTP-Verbindungs-Manager](connection-manager/ftp-connection-manager.md)|[FTP-Verbindungs-Manager-Editor](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[HTTP-Verbindungs-Manager](connection-manager/http-connection-manager.md)|[HTTP-Verbindungs-Manager-Editor &#40;Seite „Server“&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [HTTP-Verbindungs-Manager-Editor &#40;Seite „Proxy“&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[MSMQ-Verbindungs-Manager](connection-manager/msmq-connection-manager.md)|[MSMQ-Verbindungs-Manager-Editor](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[ODBC-Verbindungs-Manager](connection-manager/odbc-connection-manager.md)|[ODBC-Verbindungs-Manager: Referenz zur Benutzeroberfläche](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)|[SMO-Verbindungs-Manager-Editor](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[SMTP-Verbindungs-Manager](connection-manager/smtp-connection-manager.md)|[SMTP-Verbindungs-Manager-Editor](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[SQL Server Compact Edition-Verbindungs-Manager](connection-manager/sql-server-compact-edition-connection-manager.md)|[Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Verbindung“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Alle“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md)|[WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     Der Bereich **Verbindungs-Manager** enthält eine Liste mit den hinzugefügten Verbindungs-Managern.  
  
5.  Klicken Sie wahlweise mit der rechten Maustaste auf den Verbindungs-Manager, klicken Sie auf **Umbenennen**, und ändern Sie anschließend den Standardnamen des Verbindungs-Managers.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
##  <a name="to-add-a-connection-manager-at-the-project-level"></a><a name="project"></a>So fügen Sie einen Verbindungs-Manager auf Projektebene hinzu  
  
1.  Öffnen Sie das [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Projekt in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Verbindungs-Manager**, und klicken Sie auf **Neuer Verbindungs-Manager**.  
  
3.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** den Typ des Verbindungs-Managers aus, und klicken Sie dann auf **Hinzufügen**.  
  
     Das benutzerdefinierte Dialogfeld für den ausgewählten Verbindungs-Manager-Typ wird aufgerufen. Weitere Informationen zu den Verbindungs-Manager-Typen und den verfügbaren Optionen finden Sie in der folgenden Optionentabelle.  
  
    |Ziel-Editor für Dimensionsverarbeitung|Tastatur|  
    |------------------------|-------------|  
    |[ADO-Verbindungs-Manager](connection-manager/ado-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[ADO.NET-Verbindungs-Manager](connection-manager/ado-net-connection-manager.md)|[ADO.NET-Verbindungs-Manager konfigurieren](configure-ado-net-connection-manager.md)|  
    |[Analysis Services-Verbindungs-Manager](connection-manager/analysis-services-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Analysis Services-Verbindungs-Manager hinzufügen“](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)|  
    |[Excel-Verbindungs-Manager](connection-manager/excel-connection-manager.md)|[Verbindungs-Manager-Editor für Excel](../../2014/integration-services/excel-connection-manager-editor.md)|  
    |[Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)|[Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)|  
    |[Verbindungs-Manager für mehrere Dateien](connection-manager/multiple-files-connection-manager.md)|[Referenz zur Benutzeroberfläche des Dialogfelds „Dateiverbindungs-Manager hinzufügen“](connection-manager/add-file-connection-manager-dialog-box-ui-reference.md)|  
    |[Verbindungs-Manager für Flatfiles](connection-manager/flat-file-connection-manager.md)|[Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Spalten&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)|  
    |[Verbindungs-Manager für mehrere Flatfiles](connection-manager/multiple-flat-files-connection-manager.md)|[Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Allgemein“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-general-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Spalten“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-columns-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Erweitert“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-advanced-page.md)<br /><br /> [Verbindungs-Manager-Editor für mehrere Flatfiles &#40;Seite „Vorschau“&#41;](../../2014/integration-services/multiple-flat-files-connection-manager-editor-preview-page.md)|  
    |[FTP-Verbindungs-Manager](connection-manager/ftp-connection-manager.md)|[FTP-Verbindungs-Manager-Editor](../../2014/integration-services/ftp-connection-manager-editor.md)|  
    |[HTTP-Verbindungs-Manager](connection-manager/http-connection-manager.md)|[HTTP-Verbindungs-Manager-Editor &#40;Seite „Server“&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)<br /><br /> [HTTP-Verbindungs-Manager-Editor &#40;Seite „Proxy“&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)|  
    |[MSMQ-Verbindungs-Manager](connection-manager/msmq-connection-manager.md)|[MSMQ-Verbindungs-Manager-Editor](../../2014/integration-services/msmq-connection-manager-editor.md)|  
    |[ODBC-Verbindungs-Manager](connection-manager/odbc-connection-manager.md)|[ODBC-Verbindungs-Manager: Referenz zur Benutzeroberfläche](../../2014/integration-services/odbc-connection-manager-ui-reference.md)|  
    |[OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md)|[Konfigurieren des OLE DB-Verbindungs-Managers](configure-ole-db-connection-manager.md)|  
    |[SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)|[SMO-Verbindungs-Manager-Editor](../../2014/integration-services/smo-connection-manager-editor.md)|  
    |[SMTP-Verbindungs-Manager](connection-manager/smtp-connection-manager.md)|[SMTP-Verbindungs-Manager-Editor](../../2014/integration-services/smtp-connection-manager-editor.md)|  
    |[SQL Server Compact Edition-Verbindungs-Manager](connection-manager/sql-server-compact-edition-connection-manager.md)|[Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Verbindung“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)<br /><br /> [Verbindungs-Manager-Editor für SQL Server Compact Edition &#40;Seite „Alle“&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-all-page.md)|  
    |[WMI-Verbindungs-Manager](connection-manager/wmi-connection-manager.md)|[WMI-Verbindungs-Manager-Editor](../../2014/integration-services/wmi-connection-manager-editor.md)|  
  
     Der Verbindungs-Manager, den Sie hinzugefügt haben, wird unter dem Knoten **Verbindungs-Manager** im **Projektmappen-Explorer**angezeigt. Er wird auch auf der Registerkarte **Verbindungs-Manager** im Fenster **SSIS-Designer** für alle Pakete im Projekt angezeigt. Der Name des Verbindungs-Managers auf dieser Registerkarte enthält **(project)** als Präfix, um diesen Verbindungs-Manager auf Projektebene von den Verbindungs-Managern auf Paketebene zu unterscheiden.  
  
4.  Klicken Sie optional mit der rechten Maustaste auf den Verbindungs-Manager im Fenster des **Projektmappen-Explorer** unter dem Knoten **Verbindungs-Manager** , bzw. klicken Sie auf der Registerkarte **Verbindungs-Manager** des Fensters **SSIS-Designer** auf **Umbenennen**, und ändern Sie anschließend den Standardnamen des Verbindungs-Managers.  
  
    > [!NOTE]  
    >  Auf der Registerkarte **Verbindungs-Manager** des Fensters **SSIS-Designer** kann das Präfix **(project)** im Namen des Verbindungs-Managers nicht überschrieben werden. Dies ist beabsichtigt.  
  
##  <a name="to-create-a-parameter-for-a-connection-manager-property"></a><a name="parameter"></a>So erstellen Sie einen Parameter für eine Verbindungs-Manager-Eigenschaft  
  
1.  Klicken Sie mit der rechten Maustaste im Bereich **Verbindungs-Manager** auf den Verbindungs-Manager, für den Sie einen Parameter erstellen möchten, und klicken Sie anschließend auf **Parametrisieren**.  
  
2.  Konfigurieren Sie die Parametereinstellungen im Dialogfeld **Parametrisieren** . Weitere Informationen finden Sie unter [Parameterize Dialog Box](../../2014/integration-services/parameterize-dialog-box.md).  
  
##  <a name="to-delete-a-connection-manager-from-a-package"></a><a name="DeletePackageLevel"></a>So löschen Sie einen Verbindungs-Manager aus einem Paket  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Ablaufsteuerung** , **Datenfluss** oder **Ereignishandler** , um den Bereich **Verbindungs-Manager** anzuzeigen.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Verbindungs-Manager, den Sie löschen möchten, und klicken Sie anschließend auf **Löschen**.  
  
     Wenn Sie einen Verbindungs-Manager löschen, der von Paketelementen wie dem Task SQL ausführen oder einer OLE DB-Quelle verwendet wird, erhalten Sie die folgenden Ergebnisse:  
  
    -   Auf dem Paketelement, das den gelöschten Verbindungs-Manager verwendet hat, wird ein Fehlersymbol angezeigt.  
  
    -   Die Überprüfung des Pakets schlägt fehl.  
  
    -   Das Paket kann nicht ausgeführt werden.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
##  <a name="to-delete-a-shared-connection-manager-project-level-connection-manager"></a><a name="DeleteProjectLevel"></a>So löschen Sie einen freigegebenen Verbindungs-Manager (Verbindungs-Manager auf Projektebene)  
  
1.  Klicken Sie mit der rechten Maustaste auf den Verbindungs-Manager unter dem Knoten **Verbindungs-Manager** im Fenster des **Projektmappen-Explorers** , und klicken Sie anschließend auf **Löschen**, um einen Verbindungs-Manager auf Projektebene zu löschen. [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] zeigt die folgende Warnmeldung an:  
  
    > [!WARNING]  
    >  Wenn Sie einen Verbindungs-Manager auf Projektebene löschen, könnten Pakete, die den Verbindungs-Manager verwenden, nicht ausgeführt werden. Dieser Vorgang lässt sich nicht rückgängig machen. Möchten Sie den Verbindungs-Manager löschen?  
  
2.  Klicken Sie auf "OK", um den Verbindungs-Manager zu löschen, oder auf "Abbrechen", um ihn beizubehalten.  
  
    > [!NOTE]  
    >  Sie können auch einen Verbindungs-Manager auf Projektebene von der Registerkarte **Verbindungs-Manager** des Fensters **SSIS-Designer** löschen, das für ein beliebiges Paket im Projekt geöffnet wurde. Klicken Sie hierfür mit der rechten Maustaste auf den Verbindungs-Manager auf der Registerkarte und anschließend auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Verbindungen](connection-manager/integration-services-ssis-connections.md)   
 [Festlegen der Eigenschaften eines Verbindungs-Managers](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)  
  
  
