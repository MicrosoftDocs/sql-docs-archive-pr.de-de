---
title: Deinstallieren von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617433"
---
# <a name="uninstall-reporting-services"></a>Deinstallieren von Reporting Services
  Bei der Deinstallation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] werden nicht der Inhalt, den Sie erstellt haben, bzw. die von Ihnen vorgenommenen Konfigurationsänderungen entfernt. Wenn es jedoch Inhalt gibt, den Sie nach der Deinstallation benötigen, sollten Sie Kopien des Inhalts erstellen, bevor Sie den Deinstallationsprozess starten.

## <a name="uninstall-sharepoint-mode"></a>Deinstallation im SharePoint-Modus
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint Modus deinstallieren, wird Folgendes entfernt:

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst und -Dienstproxy.

-   Für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation verwendete Dateien.

 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen werden nicht entfernt. Wenn Sie die Dienstanwendungen nicht mehr benötigen, löschen Sie diese mithilfe von Windows PowerShell oder der SharePoint-Zentraladministration.

 Die Berichtselemente und verwandte Metadaten werden nicht entfernt. Diese Informationen sind im Inhalt und in den Konfigurationsdatenbanken enthalten, die mit den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendungen verwandt sind. Die Datenbanken werden nicht entfernt, und Sie können die Datenbanken manuell zu einer anderen Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus migrieren. Wenn Sie die Informationen jedoch nicht mehr benötigen, löschen Sie die Datenbanken. Weitere Informationen finden Sie unter [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

 Im Folgenden finden Sie Beispielnamen der drei [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenbanken, die nicht entfernt werden.

-   **Berichtsserver-Datenbank:** ReportingService_7f616e2d253040e8ab5653b3c09a065e

-   **Temporäre Berichtsserver-Datenbank:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB

-   **Berichtsserver-Warnungsdatenbank:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting

### <a name="uninstall-the-add-in-for-sharepoint-products"></a>Deinstallation des Add-Ins für SharePoint-Produkte.
 Wenn Sie das Add-In von einem Computer deinstallieren, können Sie auswählen, ob Sie nur die Dateien entfernen möchten oder auch die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktion von der Farm entfernen möchten. Informationen zum Deinstallieren des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins für SharePoint-Produkte finden Sie unter [installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).

## <a name="uninstall-native-mode"></a>Deinstallation im einheitlichen Modus
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus deinstallieren, wird alles, was nach der Installation **erstellt** oder **geändert** wurde, beibehalten. Beispiele für Datenbankdateien, Protokolldateien, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdateien und Inhaltselemente wie Berichte und Datenquellendateien.

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist eine Instanzfunktion und deshalb in der Systemsteuerung, den Programmen und Funktionen von Windows nicht aufgeführt. So deinstallieren Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus:

1.  Klicken Sie in der Windows-Systemsteuerung auf **Programme und Funktionen**.

2.  Wählen Sie unter **Programme und Funktionen** die Option **Microsoft SQL Server 2012**aus.

3.  Wählen Sie im Deinstallations-Assistenten die Instanz aus, die die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Instanzfunktion **RS**enthält.

     ![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")

4.  Wählen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktion aus, nachdem Sie die Instanz ausgewählt haben.

     ![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")

5.  Schließen Sie den Assistenten ab.

## <a name="see-also"></a>Weitere Informationen
 [Deinstallieren Sie eine vorhandene Instanz von SQL Server &#40;Setup,&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [installieren oder deinstallieren Sie das PowerPivot für SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [installieren oder deinstallieren Sie das Reporting Services-Add-in für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)


