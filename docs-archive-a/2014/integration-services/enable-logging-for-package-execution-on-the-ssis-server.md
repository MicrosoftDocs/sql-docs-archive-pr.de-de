---
title: Aktivieren der Protokollierung für die Paket Ausführung auf dem SSIS-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb0ca1e03466e6cad277905093262b9aec048c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618814"
---
# <a name="enable-logging-for-package-execution-on-the-ssis-server"></a><span data-ttu-id="b285a-102">Aktivieren der Protokollierung für die Paketausführung auf dem SSIS-Server</span><span class="sxs-lookup"><span data-stu-id="b285a-102">Enable Logging for Package Execution on the SSIS Server</span></span>
  <span data-ttu-id="b285a-103">In diesem Verfahren wird beschrieben, wie Sie den Protokolliergrad für ein Paket festlegen oder ändern, wenn Sie ein auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server bereitgestelltes Paket ausführen.</span><span class="sxs-lookup"><span data-stu-id="b285a-103">This procedure describes how to set or change the logging level for a package when you execute a package that you have deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="b285a-104">Der Protokolliergrad, den Sie beim Ausführen des Pakets festgelegt haben, überschreibt die Paketprotokollierung, die Sie mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b285a-104">The logging level you set when you execute the package overrides the package logging you configure using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b285a-105">Weitere Informationen finden Sie unter [Aktivieren der Paketprotokollierung in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="b285a-105">See [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md) for more information.</span></span>  
  
 <span data-ttu-id="b285a-106">Sie können den Protokolliergrad mit einer der folgenden Methoden angeben.</span><span class="sxs-lookup"><span data-stu-id="b285a-106">You can specify the logging level by using one of the following methods.</span></span> <span data-ttu-id="b285a-107">In diesem Thema wird die erste Methode behandelt.</span><span class="sxs-lookup"><span data-stu-id="b285a-107">This topic covers the first method.</span></span>  
  
-   <span data-ttu-id="b285a-108">Konfigurieren einer Instanz einer Paketausführung mithilfe des Dialogfelds "Paket ausführen"</span><span class="sxs-lookup"><span data-stu-id="b285a-108">Configuring an instance of a package execution by using the Execute Package dialog box</span></span>  
  
-   <span data-ttu-id="b285a-109">Das Festlegen von Parametern für eine Instanz mithilfe von [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)</span><span class="sxs-lookup"><span data-stu-id="b285a-109">Setting parameters for an instance of an execution by using the [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)</span></span>  
  
-   <span data-ttu-id="b285a-110">Das Konfigurieren eines Auftrags des SQL Server-Agents für eine Paketausführung mit dem Dialogfeld "Neuer Auftragsschritt".</span><span class="sxs-lookup"><span data-stu-id="b285a-110">Configuring a SQL Server Agent job for a package execution by using the New Job Step dialog box.</span></span>  
  
### <a name="to-set-the-logging-level-for-a-package-by-using-the-execute-package-dialog-box"></a><span data-ttu-id="b285a-111">So legen Sie den Protokolliergrad für ein Paket mithilfe des Dialogfelds "Paket ausführen" fest</span><span class="sxs-lookup"><span data-stu-id="b285a-111">To set the logging level for a package by using the Execute Package dialog box</span></span>  
  
1.  <span data-ttu-id="b285a-112">Navigieren Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]zum Paket im Objekt-Explorer.</span><span class="sxs-lookup"><span data-stu-id="b285a-112">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], navigate to the package in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="b285a-113">Klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Ausführen**aus.</span><span class="sxs-lookup"><span data-stu-id="b285a-113">Right-click the package and select **Execute**.</span></span>  
  
3.  <span data-ttu-id="b285a-114">Wählen Sie im Dialogfeld **Paket ausführen** die Registerkarte **Erweitert** aus.</span><span class="sxs-lookup"><span data-stu-id="b285a-114">Select the **Advanced** tab in the **Execute Package** dialog box.</span></span>  
  
4.  <span data-ttu-id="b285a-115">Wählen Sie unter **Protokolliergrad**den Protokolliergrad aus.</span><span class="sxs-lookup"><span data-stu-id="b285a-115">Under **Logging level**, select the logging level.</span></span> <span data-ttu-id="b285a-116">Eine Beschreibung der verfügbaren Werte finden Sie in der unten stehenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b285a-116">See the table below for a description of available values.</span></span>  
  
5.  <span data-ttu-id="b285a-117">Nehmen Sie ggf. weitere Einstellungen für die Paketkonfiguration vor, und klicken Sie anschließend auf **OK** , um das Paket auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b285a-117">Complete any other package configurations, then click **OK** to run the package.</span></span>  
  
 <span data-ttu-id="b285a-118">Die folgenden Protokolliergrade sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b285a-118">The following logging levels are available.</span></span>  
  
|<span data-ttu-id="b285a-119">Protokolliergrad</span><span class="sxs-lookup"><span data-stu-id="b285a-119">Logging Level</span></span>|<span data-ttu-id="b285a-120">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="b285a-120">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="b285a-121">Keine</span><span class="sxs-lookup"><span data-stu-id="b285a-121">None</span></span>|<span data-ttu-id="b285a-122">Die Protokollierung ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="b285a-122">Logging is turned off.</span></span> <span data-ttu-id="b285a-123">Nur der Status der Ausführung von Paketen wird protokolliert.</span><span class="sxs-lookup"><span data-stu-id="b285a-123">Only the package execution status is logged.</span></span>|  
|<span data-ttu-id="b285a-124">Basic</span><span class="sxs-lookup"><span data-stu-id="b285a-124">Basic</span></span>|<span data-ttu-id="b285a-125">Alle Ereignisse werden protokolliert, außer benutzerdefinierten und Diagnose-Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="b285a-125">All events are logged, except custom and diagnostic events.</span></span> <span data-ttu-id="b285a-126">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="b285a-126">This is the default value.</span></span>|  
|<span data-ttu-id="b285a-127">Leistung</span><span class="sxs-lookup"><span data-stu-id="b285a-127">Performance</span></span>|<span data-ttu-id="b285a-128">Nur Leistungsstatistiken sowie OnError- und OnWarning-Ereignisse werden protokolliert.</span><span class="sxs-lookup"><span data-stu-id="b285a-128">Only performance statistics, and OnError and OnWarning events, are logged.</span></span><br /><br /> <span data-ttu-id="b285a-129">In dem Bericht **Ausführungsleistung** wird die aktive Zeit und die Gesamtzeit für Datenflusskomponenten des Pakets angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b285a-129">The **Execution Performance** report displays Active Time and Total Time for package data flow components.</span></span> <span data-ttu-id="b285a-130">Diese Informationen sind verfügbar, wenn der Protokolliergrad der letzten Paketausführung auf **Leistung** oder **Ausführlich**festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b285a-130">This information is available when the logging level of the last package execution was set to **Performance** or **Verbose**.</span></span> <span data-ttu-id="b285a-131">Weitere Informationen finden Sie unter [Berichte für den Integration Services-Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span><span class="sxs-lookup"><span data-stu-id="b285a-131">For more information, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span><br /><br /> <span data-ttu-id="b285a-132">In der [catalog.execution_component_phases](/sql/integration-services/system-views/catalog-execution-component-phases) -Sicht werden die Start- und Beendigungszeiten der Datenflusskomponenten für jede Ausführungsphase angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b285a-132">The [catalog.execution_component_phases](/sql/integration-services/system-views/catalog-execution-component-phases) view displays the start and end times for the data flow components, for each phase of an execution.</span></span> <span data-ttu-id="b285a-133">In dieser Sicht werden die Informationen für diese Komponenten nur angezeigt, wenn der Protokolliergrad der Paketausführung auf **Leistung** oder **Ausführlich**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b285a-133">This view displays this information for these components only when the logging level of the package execution is set to **Performance** or **Verbose**.</span></span>|  
|<span data-ttu-id="b285a-134">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="b285a-134">Verbose</span></span>|<span data-ttu-id="b285a-135">Alle Ereignisse werden protokolliert, einschließlich benutzerdefinierter Ereignisse und Diagnose-Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="b285a-135">All events are logged, including custom and diagnostic events.</span></span><br /><br /> <span data-ttu-id="b285a-136">Ein Beispiel für ein Diagnoseereignis ist das DiagnosticEx-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="b285a-136">An example of a diagnostic event, is the DiagnosticEx event.</span></span> <span data-ttu-id="b285a-137">Jedes Mal, wenn der Task "Paket ausführen" ein untergeordnetes Paket ausführt, wird dieses Ereignis protokolliert.</span><span class="sxs-lookup"><span data-stu-id="b285a-137">Whenever an Execute Package task executes a child package, it logs this event.</span></span> <span data-ttu-id="b285a-138">Die Ereignismeldung besteht aus den Parameterwerten, die an untergeordnete Pakete übergeben wurden</span><span class="sxs-lookup"><span data-stu-id="b285a-138">The event message consists of the parameter values passed to child packages</span></span><br /><br /> <span data-ttu-id="b285a-139">Der Wert der Meldungsspalte für DiagnosticEx ist XML-Text.</span><span class="sxs-lookup"><span data-stu-id="b285a-139">The value of the message column for DiagnosticEx is XML text.</span></span> <span data-ttu-id="b285a-140">.</span><span class="sxs-lookup"><span data-stu-id="b285a-140">.</span></span> <span data-ttu-id="b285a-141">Fragen Sie zum Anzeigen des Meldungstexts für eine Paketausführung die Sicht [catalog.operation_messages &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) ab.</span><span class="sxs-lookup"><span data-stu-id="b285a-141">To view the message text for a package execution, query the [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) view.</span></span><br /><br /> <span data-ttu-id="b285a-142">Hinweis: benutzerdefinierte Ereignisse schließen die Ereignisse ein, die von Tasks protokolliert werden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b285a-142">Note: Custom events include those events that are logged by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tasks.</span></span> <span data-ttu-id="b285a-143">Weitere Informationen finden Sie unter [Custom Messages for Logging](../../2014/integration-services/custom-messages-for-logging.md).</span><span class="sxs-lookup"><span data-stu-id="b285a-143">For more information, see [Custom Messages for Logging](../../2014/integration-services/custom-messages-for-logging.md).</span></span><br /><br /> <span data-ttu-id="b285a-144">In der [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) -Sicht wird eine Zeile angezeigt, sobald eine Datenflusskomponente Daten zur Paketausführung an eine Downstreamkomponente sendet.</span><span class="sxs-lookup"><span data-stu-id="b285a-144">The [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) view displays a row each time a data flow component sends data to a downstream component, for a package execution.</span></span> <span data-ttu-id="b285a-145">Der Protokolliergrad muss auf **Ausführlich** festgelegt werden, um diese Informationen in der Sicht zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="b285a-145">The logging level must be set to **Verbose** to capture this information in the view.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b285a-146">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b285a-146">See Also</span></span>  
 <span data-ttu-id="b285a-147">[Integration Services &#40;SSIS-&#41; Protokollierung](performance/integration-services-ssis-logging.md) </span><span class="sxs-lookup"><span data-stu-id="b285a-147">[Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md) </span></span>  
 [<span data-ttu-id="b285a-148">Aktivieren der Paket Protokollierung in SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="b285a-148">Enable Package Logging in SQL Server Data Tools</span></span>](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)  
  
  