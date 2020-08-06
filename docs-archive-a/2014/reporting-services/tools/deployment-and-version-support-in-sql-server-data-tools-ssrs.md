---
title: Bereitstellung und Versions Unterstützung in SQL Server Data Tools (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 512f762d828f56ceadc8458a8666bfe6269f5bb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616367"
---
# <a name="deployment-and-version-support-in-sql-server-data-tools-ssrs"></a>Bereitstellung und Versionsunterstützung in  SQL Server Data Tools (SSRS)
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] unterstützt die folgenden Szenarien:  
  
-   Öffnen von Berichtsdefinitionen (*.rdl) und Berichtsserverprojekten (\*.rptproj)  
  
-   Erstellen von Berichtsdefinitionen  
  
-   Anzeigen einer Berichtsvorschau im Berichts-Designer  
  
-   Bereitstellen von Berichten auf Berichtsservern  
  
##  <a name="configuration-and-deployment-properties"></a><a name="bkmk_ConfigurationandDeploymentProperties"></a> Konfigurations- und Bereitstellungseigenschaften  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] unterstützt Projektkonfigurationen. Eine Projektkonfiguration besteht aus einer Gruppe von Eigenschaften, die Speicherorte und Verhaltensweisen angeben, wenn ein Projekt im Rahmen der Vorschau oder Bereitstellung von Berichten erstellt wird. Weitere Informationen zu Projektkonfigurationen finden Sie in der Visual Studio-Dokumentation.  
  
 Das Upgrade von Berichtsdefinitionen auf Schemaversionen, die mit den Zielberichtsservern kompatibel sind, steuern Sie mithilfe von Projektkonfigurationen. Zu den mittels Projektkonfigurationen gesteuerten Eigenschaften zählen der Zielberichtsserver, der Ordner, in dem der Buildprozess vorübergehend Berichtsdefinitionen für die Vorschau und Bereitstellung speichert, und die Fehlerebenen.  
  
 Berichte werden erstellt, bevor sie als Vorschauberichte im Berichts-Designer gerendert oder auf dem Berichtsserver bereitgestellt werden.  
  
 Die Konfigurationseigenschaften legen Sie im Dialogfeld [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Projekteigenschaften**von** fest.  
  
 Die Erstellungs- und Bereitstellungseigenschaften umfassen:  
  
-   OutputPath ist eine Erstellungseigenschaft, die den Pfad von Ordnern angibt, unter denen die für die Erstellungsüberprüfung, Bereitstellung und Berichtsvorschau verwendete Berichtsdefinition gespeichert wird.  
  
-   ErrorLevel ist eine Erstellungseigenschaft, die den Schweregrad der Erstellungsprobleme identifiziert, die als Fehler gemeldet werden. Probleme mit einem Schweregrad kleiner oder gleich dem Wert von ErrorLevel werden als Fehler gemeldet. Andernfalls werden die Probleme als Warnungen gemeldet. Weitere Informationen finden Sie im Abschnitt „Berichtsüberprüfung und Fehlerebenen“ im Artikel [Entwerfen von Berichten mit dem Berichts-Designer &#40;SSRS&#41;](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
-   TargetServerVersion ist eine Bereitstellungseigenschaft, die die erwartete Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] identifiziert, die auf dem in der Eigenschaft „TargetServerURL“ angegebenen Zielberichtsserver installiert ist.  
  
 Wenn Sie die frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im Dialogfeld **Projekteigenschaften** angeben, werden die Berichte nicht automatisch auf die frühere Version zurückgesetzt. Das bedeutet, dass ein Berichtsserverprojekt Berichte aus zwei verschiedenen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten kann. Wenn das Berichtsserverprojekt bereitgestellt wird, werden alle im Projekt enthaltenen Berichte in die Version konvertiert, die in TargetServerVersion angegeben ist.  
  
 Sie können einem Projekt mehr als eine Projektkonfiguration hinzufügen; jede einzelne wird für ein anderes Szenario verwendet, z. B. das Bereitstellen auf verschiedenen Berichtsserverversionen. Weitere Informationen finden Sie unter [Festlegen von Bereitstellungseigenschaften &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) und unter [Eigenschaftsseiten für Projekt &#40;Dialogfeld&#41;](project-property-pages-dialog-box.md).  
  
##  <a name="supported-versions"></a><a name="bkmk_SupportedVersions"></a> Unterstützte Versionen  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die 32-Bit-Entwicklungsumgebung für Berichtsserverprojekte, ist nicht für die Ausführung auf [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-basierten Computern konzipiert und wird auf [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-basierten Servern nicht installiert. Für x64-basierte Computer ist jedoch Support für [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] verfügbar.  
  
 In der nachfolgenden Tabelle werden die unterstützten Versionen zum Verfassen und Veröffentlichen von Berichten in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erläutert.  
  
> [!NOTE]  
>  Das Schema ist seit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]unverändert.  
  
|Projekt- oder Dateityp|Version|Berichte verfassen|Veröffentlichen von Berichten|Notizen|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|Berichtsserverprojekt<br /><br /> oder<br /><br /> Berichtsserver-Assistenten-Projekt|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|2014-RDL-Schema|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Berichtsserverprojekt<br /><br /> oder<br /><br /> Berichtsserver-Assistenten-Projekt|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|2012-RDL-Schema|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Berichtsserverprojekt<br /><br /> oder<br /><br /> Berichtsserver-Assistenten-Projekt|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|2008 R2-RDL-Schema|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Berichtsserverprojekt<br /><br /> oder<br /><br /> Berichtsserver-Assistenten-Projekt|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|2008-RDL-Schema|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]nur Berichts Server|Aktualisiert 2003 RDL und 2005 RDL lokal auf das 2008 RDL-Schema.|  
|Berichtsserverprojekt<br /><br /> oder<br /><br /> Berichtsserver-Assistenten-Projekt|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|2005-RDL-Schema|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichts Server||  
|Berichtsserverprojekt|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|2003-RDL-Schema|Nicht unterstützt||  
|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-RDLC-Berichts-Designer|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2005<br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2008|2005-RDL-Schema|Nicht unterstützt|2008-RDL-Schema wird nicht unterstützt.|  
|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Viewer-Steuerelemente|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2005<br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2008|2008-RDL wird im lokalen Modus nicht unterstützt|–|Kann 2008 RDL-Berichte auf dem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichts Server im Server Modus anzeigen.|  
  
 Weitere Informationen über das Öffnen von Berichten in einer vorherigen Version des Berichtsdefinitionsschemas finden Sie unter [Aktualisieren von Berichten](../install-windows/upgrade-reports.md). Weitere Informationen zu spezifischen Berichtsdefinitionsschemata finden Sie im [Thema zum Angeben der Berichtsdefinitionssprache](https://go.microsoft.com/fwlink/?linkid=116865).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Datenquellen und Berichten](../reports/publishing-data-sources-and-reports.md)  
  
  
