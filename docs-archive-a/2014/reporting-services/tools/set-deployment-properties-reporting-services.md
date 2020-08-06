---
title: Festlegen von Bereitstellungseigenschaften (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], deploying
- publishing reports [Reporting Services]
- properties [Reporting Services], deployment
- deploying reports [Reporting Services]
ms.assetid: 18201ca0-bf4a-484f-b3a2-95d1046a6a9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fac1903e4d6738d6a08db55656acba353e4c338d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615259"
---
# <a name="set-deployment-properties-reporting-services"></a><span data-ttu-id="51c21-102">Festlegen von Bereitstellungseigenschaften (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="51c21-102">Set Deployment Properties (Reporting Services)</span></span>
  <span data-ttu-id="51c21-103">In[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]müssen Sie den Berichtsserver und optional die Ordner für Berichte und freigegebene Datenquellen angeben, damit Sie die Elemente in einem Berichtsserverprojekt auf einem Berichtsserver veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="51c21-103">In[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you must specify the report server and optionally the folders for reports and shared data sources so that you can publish the items in a Report Server project to a report server.</span></span> <span data-ttu-id="51c21-104">Die Eigenschaften und Werte, die von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt werden müssen, und eine Vorschau der bereitgestellten Berichte werden in Projektkonfigurationen des Berichtsserverprojekts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="51c21-104">The properties and values that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] needs to build, preview an deploy reports are stored in project configurations of the Report Server project.</span></span> <span data-ttu-id="51c21-105">Sie können mehrere benannte Mengen für diese Projekteigenschaften erstellen, damit Sie problemlos zwischen Eigenschaftensätzen wechseln können.</span><span class="sxs-lookup"><span data-stu-id="51c21-105">You can create multiple named sets for these project properties, so that you can conveniently switch between property sets.</span></span> <span data-ttu-id="51c21-106">Jede Eigenschaftsgruppe ist eine Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="51c21-106">Each set of properties is a configuration.</span></span> <span data-ttu-id="51c21-107">So können Sie z. B. über eine Konfiguration zum Veröffentlichen von Berichten auf einem Testserver und eine andere Konfiguration zum Veröffentlichen von Berichten auf einem Produktionsserver verfügen.</span><span class="sxs-lookup"><span data-stu-id="51c21-107">For example, you can have a configuration for publishing reports to a test server and a different configuration for publishing reports to a production server.</span></span>  
  
 <span data-ttu-id="51c21-108">Verwenden Sie den Konfigurations-Manager, um Gruppen mit Projekteigenschaften in Projektkonfigurationen zu erstellen und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="51c21-108">Use Configuration Manager to create and manage sets of project properties in project configurations.</span></span> <span data-ttu-id="51c21-109">Der Konfigurations-Manager ist eine von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]unterstützte Funktion, auf dem [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] basiert.</span><span class="sxs-lookup"><span data-stu-id="51c21-109">Configuration Manager is a feature supported by [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], on which [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is based.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51c21-110">Verwechseln Sie diese Funktion nicht mit dem Reporting Services-Konfigurations-Manager, der verwendet wird, um nach der Installation Reporting Services zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="51c21-110">Do not confuse this feature with the Reporting Services Configuration Manager, which is used to configure Reporting Services after installation.</span></span> <span data-ttu-id="51c21-111">Weitere Informationen finden Sie unter [Konfigurieren und Verwalten eines Berichtsservers (einheitlicher SSRS-Modus)](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="51c21-111">For more information, see [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51c21-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]wird der Vorgang zur Veröffentlichung von Berichten aus einem Berichtsserverprojekt oder einer Projektmappe als *Bereitstellen von Berichten*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="51c21-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], the action of publishing reports from a Report Server project or solution is known as *deploying reports*.</span></span>  
  
### <a name="to-set-deployment-properties"></a><span data-ttu-id="51c21-113">So legen Sie Bereitstellungseigenschaften fest</span><span class="sxs-lookup"><span data-stu-id="51c21-113">To set deployment properties</span></span>  
  
1.  <span data-ttu-id="51c21-114">Klicken Sie mit der rechten Maustaste auf das Berichtsprojekt, und klicken Sie anschließend auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="51c21-114">Right-click the report project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="51c21-115">Wählen Sie im Dialogfeld **Eigenschaftenseiten** für das Projekt in der Liste **Konfiguration** eine Konfiguration aus, die Sie bearbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="51c21-115">In the **Property Pages** dialog box for the project, select a configuration to edit from the **Configuration** list.</span></span> <span data-ttu-id="51c21-116">Häufige Konfigurationen sind **DebugLocal**, **Debug**und **Release**.</span><span class="sxs-lookup"><span data-stu-id="51c21-116">Common configurations are **DebugLocal**, **Debug**, and **Release**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51c21-117">Sie können mehrere Konfigurationen verwenden, um schnell zwischen verschiedenen Berichtsservern oder Einstellungen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="51c21-117">You can use multiple configurations to switch quickly between different report servers or settings.</span></span>  
  
3.  <span data-ttu-id="51c21-118">Im Textfeld **OutputPath** können Sie den Pfad in Ihrem lokalen Dateisystem eingeben oder einfügen, um die in der Buildüberprüfung, Bereitstellung und Berichts Vorschau verwendete Berichtsdefinition zu speichern.</span><span class="sxs-lookup"><span data-stu-id="51c21-118">In the **OutputPath** textbox, type or paste the path in your local file system to store the report definition used in build verification, deployment, and preview of reports.</span></span> <span data-ttu-id="51c21-119">Der Pfad muss sich von dem für das Projekt verwendeten Pfad und einem relativen Pfad unterscheiden, der einem untergeordneten Ordner des Projektpfads entspricht.</span><span class="sxs-lookup"><span data-stu-id="51c21-119">The path must be different than the path that you use for the project and a relative path that is a child folder under the path of the project.</span></span>  
  
4.  <span data-ttu-id="51c21-120">Geben Sie im Textfeld **ERRORLEVEL** den Schweregrad der Erstellungs Probleme ein, die als Fehler gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="51c21-120">In the **ErrorLevel** text box, type the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="51c21-121">Probleme, die bei der Erstellung von Berichten, Datenquellen oder anderen Projektressourcen auftreten, deren Schweregrad kleiner oder gleich dem Wert von **ERRORLEVEL** ist, werden als Fehler gemeldet. Andernfalls werden die Probleme als Warnungen gemeldet.</span><span class="sxs-lookup"><span data-stu-id="51c21-121">Issues occurring when building reports, data sources, or other project resources with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="51c21-122">Jeder Fehler führt dazu, dass die Erstellung fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="51c21-122">Any error will cause the build task to fail.</span></span> <span data-ttu-id="51c21-123">Die gültigen Schweregrade sind 0 bis einschließlich 4.</span><span class="sxs-lookup"><span data-stu-id="51c21-123">The valid severity levels are 0 through 4 inclusive.</span></span> <span data-ttu-id="51c21-124">Der Standardwert ist 2.</span><span class="sxs-lookup"><span data-stu-id="51c21-124">The default value is 2.</span></span>  
  
     <span data-ttu-id="51c21-125">**ErrorLevel** kann verwendet werden, um die Vertraulichkeit des Berichterstellung zu erhöhen oder zu verringern.</span><span class="sxs-lookup"><span data-stu-id="51c21-125">**ErrorLevel** can be used to increase or decrease the sensitivity of the build.</span></span> <span data-ttu-id="51c21-126">Wenn beispielsweise ein Bericht mit einer Karte während der Bereitstellung auf einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Berichtsserver erstellt wird, wird standardmäßig ein Fehler angezeigt, und der Bericht wird nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="51c21-126">For example, when a report with a map is built during deployment to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] report server an error displays by default and building the report fails.</span></span> <span data-ttu-id="51c21-127">Wenn Sie **ErrorLevel** herabsetzen, wird die Karte aus dem Bericht entfernt, eine Warnung angezeigt und die Berichterstellung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="51c21-127">If you lower **ErrorLevel** the map is removed from the report, a warning displays, and building the report continues.</span></span>  
  
5.  <span data-ttu-id="51c21-128">Wählen Sie in der Liste **StartItem** einen Bericht aus, der im Vorschaufenster oder in einem Browserfenster angezeigt werden soll, wenn das Berichts Projekt ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="51c21-128">In the **StartItem** list, select a report to display in the preview window or in a browser window when the report project is run.</span></span>  
  
6.  <span data-ttu-id="51c21-129">Wählen Sie in der Liste **OverwriteDataSources** den Wert **TRUE** aus, um bei jedem Veröffentlichen von freigegebenen Datenquellen die freigegebene Datenquelle auf dem Server zu überschreiben, oder wählen Sie **FALSE** aus, um die Datenquelle auf dem Server beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="51c21-129">In the **OverwriteDataSources** list, select **True** to overwrite the shared data source on the server each time shared data sources are published, or select **False** to keep the data source on the server.</span></span>  
  
7.  <span data-ttu-id="51c21-130">Wählen Sie in der Liste **targetserverversion** entweder die-oder die- [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Version von aus, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder wählen Sie **Version erkennen** aus, um automatisch die Version zu ermitteln, die auf dem durch die Eigenschaft **TargetServer URL** identifizierten Server installiert ist.</span><span class="sxs-lookup"><span data-stu-id="51c21-130">In the **TargetServerVersion** list, select either the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or select **Detect Version** to automatically determine the version installed on the server identified by the **TargetServer URL** property.</span></span> <span data-ttu-id="51c21-131">Der Standardwert ist **SQL Server 2008 R2**.</span><span class="sxs-lookup"><span data-stu-id="51c21-131">The default value is **SQL Server 2008 R2**.</span></span>  
  
     <span data-ttu-id="51c21-132">Verwenden Sie **TargetServerVersion** , um die erstellten Berichte unter dem in OutputPath angegebenen Pfad für die Version des Berichtsservers anzupassen, der in **TargetServerURL**angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="51c21-132">Use **TargetServerVersion** to customize the built reports, placed in the path specified in OutputPath, for the version of the report server specified in **TargetServer URL**.</span></span>  
  
8.  <span data-ttu-id="51c21-133">Geben Sie im Textfeld **TargetDataSourceFolder** den Ordner auf dem Berichtsserver ein, in dem die veröffentlichten, freigegebenen Datenquellen gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="51c21-133">In the **TargetDataSourceFolder** text box, type the folder on the report server in which to place the published shared data sources.</span></span> <span data-ttu-id="51c21-134">Der Standardwert für **TargetDataSourceFolder** lautet Datenquellen.</span><span class="sxs-lookup"><span data-stu-id="51c21-134">The default value for **TargetDataSourceFolder** is Data Sources.</span></span> <span data-ttu-id="51c21-135">Wenn Sie hierfür keinen Wert angeben, werden die Datenquellen an dem in **TargetReportFolder**angegebenen Speicherort veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="51c21-135">If you leave this value blank, the data sources will be published to the location specified in **TargetReportFolder**.</span></span>  
  
9. <span data-ttu-id="51c21-136">Geben Sie im Textfeld **TargetReportFolder** den Ordner auf dem Berichtsserver ein, in dem die veröffentlichten Berichte gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="51c21-136">In the **TargetReportFolder** text box, type the folder on the report server in which to place the published reports.</span></span> <span data-ttu-id="51c21-137">Der Standardwert für **TargetReportFolder** ist der Name des Berichts Projekts.</span><span class="sxs-lookup"><span data-stu-id="51c21-137">The default value for **TargetReportFolder** is the name of the report project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51c21-138">Für einen Berichtsserver, der im einheitlichen Modus ausgeführt wird, müssen Sie im Zielordner über Berechtigungen zum **Veröffentlichen** verfügen, um Berichte in diesem Ordner zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="51c21-138">For a report server running in native mode, you must have **Publish** permissions on the target folder to publish reports to that folder.</span></span> <span data-ttu-id="51c21-139">Berechtigungen zum Veröffentlichen werden über eine Rollenzuweisung erteilt, bei der das Benutzerkonto einer Rolle zugeordnet wird, die Veröffentlichungsvorgänge enthalt.</span><span class="sxs-lookup"><span data-stu-id="51c21-139">Publish permissions are provided through a role assignment that maps your user account to a role that includes publish operations.</span></span> <span data-ttu-id="51c21-140">Weitere Informationen finden Sie unter [Erstellen und Verwalten von Rollenzuweisungen](../security/create-and-manage-role-assignments.md).</span><span class="sxs-lookup"><span data-stu-id="51c21-140">For more information, see [Create and Manage Role Assignments](../security/create-and-manage-role-assignments.md).</span></span> <span data-ttu-id="51c21-141">Für einen Berichtsserver, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie auf der SharePoint-Website über Berechtigungen als **Mitglied** oder **Eigentümer** verfügen.</span><span class="sxs-lookup"><span data-stu-id="51c21-141">For a report server running in SharePoint integrated mode, you must have **Member** or **Owner** permission on the SharePoint site.</span></span> <span data-ttu-id="51c21-142">Weitere Informationen finden Sie unter [Referenz zu SharePoint Website- und Listenberechtigungen für Berichtsserverelemente](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).</span><span class="sxs-lookup"><span data-stu-id="51c21-142">For more information, see [SharePoint Site and List Permission Reference for Report Server Items](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).</span></span>  
  
10. <span data-ttu-id="51c21-143">Geben Sie im Textfeld **TargetServerURL** die URL des Zielberichtsservers ein.</span><span class="sxs-lookup"><span data-stu-id="51c21-143">In the **TargetServerURL** text box, type the URL of the target report server.</span></span> <span data-ttu-id="51c21-144">Diese Eigenschaft müssen Sie vor dem Veröffentlichen eines Berichts auf eine gültige URL eines Berichtsservers festlegen.</span><span class="sxs-lookup"><span data-stu-id="51c21-144">Before you publish a report, you must set this property to a valid report server URL.</span></span> <span data-ttu-id="51c21-145">Wenn Sie auf einem Berichtsserver veröffentlichen, der im einheitlichen Modus ausgeführt wird, verwenden Sie die URL des virtuellen Verzeichnisses des Berichtsservers (z.B. http: *//Server/Berichtsserver* oder https: *//Server/Berichtsserver)* .</span><span class="sxs-lookup"><span data-stu-id="51c21-145">When publishing to a report server running in native mode, use the URL of the virtual directory of the report server (for example, http:*//server/reportserver* or https:*//server/reportserver)*.</span></span> <span data-ttu-id="51c21-146">Dies ist das virtuelle Verzeichnis des Berichtsservers, nicht des Berichts-Managers.</span><span class="sxs-lookup"><span data-stu-id="51c21-146">This is the virtual directory of the report server, not Report Manager.</span></span>  
  
     <span data-ttu-id="51c21-147">Verwenden Sie eine URL für eine SharePoint-Stammwebsite oder -Unterwebsite, wenn der Bericht auf einem Berichtsserver veröffentlicht wird, der im integrierten SharePoint-Modus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="51c21-147">When publishing to a report server running in SharePoint integrated mode, use a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="51c21-148">Wenn Sie keine Website angeben, wird die Standard Website der obersten Ebene verwendet (z. b. http://*Servername*, http://*Servername* / *Site* oder http://*Servername* / *Site* / *unter Website*).</span><span class="sxs-lookup"><span data-stu-id="51c21-148">If you do not specify a site, the default top-level site is used (for example, http://*servername*, http://*servername*/*site* or http://*servername*/*site*/*subsite*).</span></span>  
  
### <a name="to-set-configuration-manager-properties"></a><span data-ttu-id="51c21-149">So legen Sie Konfigurations-Manager-Eigenschaften fest</span><span class="sxs-lookup"><span data-stu-id="51c21-149">To set Configuration Manager properties</span></span>  
  
1.  <span data-ttu-id="51c21-150">Klicken Sie mit der rechten Maustaste auf das Berichtsprojekt, und klicken Sie anschließend auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="51c21-150">Right-click the report project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="51c21-151">Klicken Sie im Dialogfeld **Eigenschaftenseiten** für das Projekt auf **Konfigurations-Manager**.</span><span class="sxs-lookup"><span data-stu-id="51c21-151">In the **Property Pages** dialog box for the project, click **Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="51c21-152">Wählen Sie im Dialogfeld **Konfigurations-Manager** die zu bearbeitende Konfiguration aus.</span><span class="sxs-lookup"><span data-stu-id="51c21-152">In the **Configuration Manager** dialog box, select the configuration to edit.</span></span> <span data-ttu-id="51c21-153">Die derzeit aktive Konfiguration wird als **aktiv ( ***\<configuration>*** )** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="51c21-153">The currently active configuration is displayed as **Active(***\<configuration>***)**.</span></span>  
  
4.  <span data-ttu-id="51c21-154">Aktivieren oder deaktivieren Sie unter **Projektkontext**für jedes Projekt der Projektmappe **Erstellen** oder **Bereitstellen**.</span><span class="sxs-lookup"><span data-stu-id="51c21-154">In **Project Contexts**, for each project in the solution, select or clear **Build** or **Deploy**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51c21-155">Wenn **Erstellen** ausgewählt ist, erstellt der Berichts-Designer das Berichtsprojekt und überprüft es auf Fehler, bevor es auf einem Berichtsserver veröffentlicht oder eine Vorschau angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="51c21-155">If **Build** is selected, Report Designer builds the report project and checks for errors before previewing or publishing to a report server.</span></span> <span data-ttu-id="51c21-156">Wenn **Bereitstellen** ausgewählt ist, veröffentlicht der Berichts-Designer die Berichte gemäß der Definition in den Bereitstellungseigenschaften auf dem Berichtsserver.</span><span class="sxs-lookup"><span data-stu-id="51c21-156">If **Deploy** is selected, Report Designer publishes the reports to the report server as defined in deployment properties.</span></span> <span data-ttu-id="51c21-157">Wenn **Bereitstellen** nicht ausgewählt ist, zeigt der Berichts-Designer den in der **StartItem** -Eigenschaft angegebenen Bericht in einem lokalen Vorschaufenster an.</span><span class="sxs-lookup"><span data-stu-id="51c21-157">If **Deploy** is not selected, Report Designer displays the report specified in the **StartItem** property in a local preview window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c21-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="51c21-158">See Also</span></span>  
 <span data-ttu-id="51c21-159">[Veröffentlichen von Datenquellen und Berichten](../reports/publishing-data-sources-and-reports.md) </span><span class="sxs-lookup"><span data-stu-id="51c21-159">[Publishing Data Sources and Reports](../reports/publishing-data-sources-and-reports.md) </span></span>  
 <span data-ttu-id="51c21-160">[Anzeigen einer Vorschau für Berichte](../reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="51c21-160">[Previewing Reports](../reports/previewing-reports.md) </span></span>  
 <span data-ttu-id="51c21-161">[Berichts-Designer F1-Hilfe](report-designer-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="51c21-161">[Report Designer F1 Help](report-designer-f1-help.md) </span></span>  
 <span data-ttu-id="51c21-162">[URL-Beispiele für veröffentlichte Berichts Elemente auf einem Berichts Server im SharePoint-Modus &#40;SSRS&#41;](url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="51c21-162">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="51c21-163">[Eigenschaften Seiten für Projekt (Dialog Feld)](project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="51c21-163">[Project Property Pages Dialog Box](project-property-pages-dialog-box.md) </span></span>  
 [<span data-ttu-id="51c21-164">Veröffentlichen von Berichten auf einem Berichtsserver</span><span class="sxs-lookup"><span data-stu-id="51c21-164">Publishing Reports to a Report Server</span></span>](../reports/publishing-reports-to-a-report-server.md)  
  
  