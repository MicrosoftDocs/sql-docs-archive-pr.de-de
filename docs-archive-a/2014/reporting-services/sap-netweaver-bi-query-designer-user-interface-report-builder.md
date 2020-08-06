---
title: Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
helpviewer_keywords:
- query designers, SAP
ms.assetid: 8edda06d-1608-498b-bd50-10905e54f6ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69a009322bd2d4dcd7211e6b21aa3ecd7c9466e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615277"
---
# <a name="sap-netweaver-bi-query-designer-user-interface-report-builder"></a><span data-ttu-id="96a89-102">Benutzeroberfläche des Abfrage-Designers für SAP NetWeaver BI (Berichts-Generator)</span><span class="sxs-lookup"><span data-stu-id="96a89-102">SAP NetWeaver BI Query Designer User Interface (Report Builder)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="96a89-103">stellt einen grafischen Abfrage-Designer zum Erstellen von MDX-Abfragen (Multidimensional Expression) für eine SAP NetWeaver® Business Intelligence-Datenquelle bereit.</span><span class="sxs-lookup"><span data-stu-id="96a89-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a SAP NetWeaver® Business Intelligence data source.</span></span> <span data-ttu-id="96a89-104">Der grafische MDX-Abfrage-Designer verfügt über zwei Modi: Entwurfsmodus und Abfragemodus.</span><span class="sxs-lookup"><span data-stu-id="96a89-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="96a89-105">Jeder Modus bietet einen Metadatenbereich, aus dem Sie Elemente aus einem InfoCube, einem MultiProvider oder einer für die Datenquelle definierten, webfähigen Abfrage ziehen können, um eine MDX-Abfrage zu erstellen, die bei der Berichtsverarbeitung Daten abruft.</span><span class="sxs-lookup"><span data-stu-id="96a89-105">Each mode provides a Metadata pane from which you can drag members from an InfoCube, MultiProvider, or Web-enabled query defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="96a89-106">Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="96a89-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="96a89-107">Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.</span><span class="sxs-lookup"><span data-stu-id="96a89-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="96a89-108">In diesem Abschnitt werden die Schaltflächen auf der Symbolleiste und die Bereiche des Abfrage-Designers für jeden Modus des grafischen Abfrage-Designers beschrieben.</span><span class="sxs-lookup"><span data-stu-id="96a89-108">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="96a89-109">Grafischer Abfrage-Designer im Entwurfsmodus</span><span class="sxs-lookup"><span data-stu-id="96a89-109">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="96a89-110">Wenn Sie in der Datenansicht des Berichts-Designers ein Dataset mit einer [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] -Datenquelle bearbeiten, wird der grafische Abfrage-Designer im Entwurfsmodus geöffnet.</span><span class="sxs-lookup"><span data-stu-id="96a89-110">When you edit a dataset query that uses a [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] data source, the graphical query designer opens in the Design mode.</span></span>

 <span data-ttu-id="96a89-111">![Verwenden von MDX im Entwurfsmodus des Abfrage-Designers](media/rsqd-dssapbw-mdx-designmode.gif "Verwenden von MDX im Entwurfsmodus des Abfrage-Designers")</span><span class="sxs-lookup"><span data-stu-id="96a89-111">![Query Designer using MDX in Design Mode](media/rsqd-dssapbw-mdx-designmode.gif "Query Designer using MDX in Design Mode")</span></span>

 <span data-ttu-id="96a89-112">In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="96a89-112">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="96a89-113">Bereich</span><span class="sxs-lookup"><span data-stu-id="96a89-113">Pane</span></span>|<span data-ttu-id="96a89-114">Funktion</span><span class="sxs-lookup"><span data-stu-id="96a89-114">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="96a89-115">Cube auswählen (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="96a89-115">Select Cube button</span></span>|<span data-ttu-id="96a89-116">Zeigt den zurzeit ausgewählten InfoCube, MultiProvider oder die zurzeit ausgewählte webfähige Abfrage an.</span><span class="sxs-lookup"><span data-stu-id="96a89-116">Displays the currently selected InfoCube, MultiProvider, or Web-enabled query.</span></span>|
|<span data-ttu-id="96a89-117">Metadaten (Bereich)</span><span class="sxs-lookup"><span data-stu-id="96a89-117">Metadata pane</span></span>|<span data-ttu-id="96a89-118">Zeigt eine hierarchische Liste von InfoCubes, MultiProvidern und Abfragen an.</span><span class="sxs-lookup"><span data-stu-id="96a89-118">Displays a hierarchical list of InfoCubes, MultiProviders, and queries.</span></span> <span data-ttu-id="96a89-119">An der Datenquelle erstellte Abfragen werden möglicherweise unter dem entsprechenden Cube angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96a89-119">Queries created at the data source may appear under the corresponding cube.</span></span>|
|<span data-ttu-id="96a89-120">Berechnete Elemente (Bereich)</span><span class="sxs-lookup"><span data-stu-id="96a89-120">Calculated Members pane</span></span>|<span data-ttu-id="96a89-121">Zeigt die aktuell definierten berechneten Elemente an, die für eine Verwendung in der Abfrage verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="96a89-121">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="96a89-122">Daten (Bereich)</span><span class="sxs-lookup"><span data-stu-id="96a89-122">Data pane</span></span>|<span data-ttu-id="96a89-123">Zeigt die Ergebnisse des Ausführens der Abfrage an.</span><span class="sxs-lookup"><span data-stu-id="96a89-123">Displays the results of running the query.</span></span>|

 <span data-ttu-id="96a89-124">Sie können Dimensionen und Kennzahlen aus dem Metadatenbereich und berechnete Elemente aus dem Bereich Berechnete Elemente in den Datenbereich ziehen.</span><span class="sxs-lookup"><span data-stu-id="96a89-124">You can drag dimensions and key figures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="96a89-125">Wenn die Umschaltfläche **AutoExecute** auf der Symbolleiste aktiviert ist, führt der Abfrage-Designer die Abfrage jedes Mal aus, wenn Sie ein Objekt im Datenbereich ablegen.</span><span class="sxs-lookup"><span data-stu-id="96a89-125">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="96a89-126">Wenn **AutoExecute** deaktiviert ist, führt der Abfrage-Designer die Abfrage nicht aus, während Sie Änderungen am Datenbereich vornehmen.</span><span class="sxs-lookup"><span data-stu-id="96a89-126">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="96a89-127">Sie können die Abfrage mithilfe der Schaltfläche **Ausführen** auf der Symbolleiste manuell ausführen.</span><span class="sxs-lookup"><span data-stu-id="96a89-127">You can manually run the query using the **Run** button on the toolbar.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="96a89-128">Symbolleiste für den grafischen Abfrage-Designer im Entwurfsmodus</span><span class="sxs-lookup"><span data-stu-id="96a89-128">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="96a89-129">Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen.</span><span class="sxs-lookup"><span data-stu-id="96a89-129">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="96a89-130">In der folgenden Tabelle werden die Schaltflächen und ihre Funktionen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="96a89-130">The following table describes the buttons and their functions.</span></span>

|<span data-ttu-id="96a89-131">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="96a89-131">Button</span></span>|<span data-ttu-id="96a89-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="96a89-132">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="96a89-133">**Als Text bearbeiten**</span><span class="sxs-lookup"><span data-stu-id="96a89-133">**Edit As Text**</span></span>|<span data-ttu-id="96a89-134">Wechseln zwischen dem textbasierten Abfrage-Designer und dem grafischen Abfrage-Designer.</span><span class="sxs-lookup"><span data-stu-id="96a89-134">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="96a89-135">Nicht verfügbar für diesen Datenquellentyp.</span><span class="sxs-lookup"><span data-stu-id="96a89-135">Not available for this data source type.</span></span>|
|<span data-ttu-id="96a89-136">**Importieren**</span><span class="sxs-lookup"><span data-stu-id="96a89-136">**Import**</span></span>|<span data-ttu-id="96a89-137">Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="96a89-137">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|
|<span data-ttu-id="96a89-138">![Datasetfelder aktualisieren](media/rsqdicon-refreshfields.gif "Aktualisieren der Datasetfelder")</span><span class="sxs-lookup"><span data-stu-id="96a89-138">![Refresh dataset fields](media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="96a89-139">Aktualisieren von Metadaten aus der Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="96a89-139">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="96a89-140">![Berechnetes Element hinzufügen](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen")</span><span class="sxs-lookup"><span data-stu-id="96a89-140">![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="96a89-141">Zeigt das Dialogfeld **Generator für berechnete Elemente** an.</span><span class="sxs-lookup"><span data-stu-id="96a89-141">Display the **Calculated Member Builder** dialog box.</span></span>|
|<span data-ttu-id="96a89-142">![Leere Zellen anzeigen/nicht anzeigen](../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen")</span><span class="sxs-lookup"><span data-stu-id="96a89-142">![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="96a89-143">Umschalten zwischen Einblenden und Ausblenden leerer Zellen im Datenbereich.</span><span class="sxs-lookup"><span data-stu-id="96a89-143">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="96a89-144">(Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)</span><span class="sxs-lookup"><span data-stu-id="96a89-144">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="96a89-145">![Abfrage automatisch ausführen](../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")</span><span class="sxs-lookup"><span data-stu-id="96a89-145">![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="96a89-146">Automatisches Ausführen der Abfrage und Anzeigen des Ergebnisses, sobald eine Änderung vorgenommen wird, beispielsweise Löschen einer Spalte im Datenbereich.</span><span class="sxs-lookup"><span data-stu-id="96a89-146">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="96a89-147">Die Ergebnisse werden im Datenbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96a89-147">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="96a89-148">![Löschen](../analysis-services/media/rsqdicon-delete.gif "Löschen")</span><span class="sxs-lookup"><span data-stu-id="96a89-148">![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="96a89-149">Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.</span><span class="sxs-lookup"><span data-stu-id="96a89-149">Delete the selected column in the Data pane from the query.</span></span>|
|<span data-ttu-id="96a89-150">![Symbol für das Dialogfeld „Abfrageparameter“](../analysis-services/media/iconqueryparameter.gif "Symbol für das Dialogfeld „Abfrageparameter“")</span><span class="sxs-lookup"><span data-stu-id="96a89-150">![Icon for the Query Parameters dialog box](../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="96a89-151">Anzeigen des Dialogfelds **Variablen** .</span><span class="sxs-lookup"><span data-stu-id="96a89-151">Display the **Variables** dialog box.</span></span> <span data-ttu-id="96a89-152">Diese Schaltfläche ist nur aktiviert, wenn es sich bei dem ausgewählten Cube um einen Abfragecube handelt (da nur Abfragecubes Variablen unterstützen).</span><span class="sxs-lookup"><span data-stu-id="96a89-152">This button is enabled only when the selected cube is a Query cube (because only query cubes support variables).</span></span> <span data-ttu-id="96a89-153">Wenn Sie einer Variablen einen Standardwert zuweisen, wird ein entsprechender Berichtsparameter erstellt.</span><span class="sxs-lookup"><span data-stu-id="96a89-153">When you assign a default value to a variable, a corresponding report parameter is created.</span></span>|
|<span data-ttu-id="96a89-154">![Abfrage ausführen](../analysis-services/media/rsqdicon-run.gif "Abfrage ausführen")</span><span class="sxs-lookup"><span data-stu-id="96a89-154">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="96a89-155">Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.</span><span class="sxs-lookup"><span data-stu-id="96a89-155">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="96a89-156">![Abfrage abbrechen](../analysis-services/media/rsqdicon-cancel.gif "Abfrage abbrechen")</span><span class="sxs-lookup"><span data-stu-id="96a89-156">![Cancel the query](../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="96a89-157">Abbrechen der Abfrage.</span><span class="sxs-lookup"><span data-stu-id="96a89-157">Cancel the query.</span></span>|
|<span data-ttu-id="96a89-158">![In Entwurfsmodus wechseln](../analysis-services/media/rsqdicon-designmode.gif "Wechselt in den Entwurfsmodus")</span><span class="sxs-lookup"><span data-stu-id="96a89-158">![Switch to Design mode](../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="96a89-159">Umschalten zwischen Entwurfsmodus und Abfragemodus.</span><span class="sxs-lookup"><span data-stu-id="96a89-159">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="96a89-160">Grafischer Abfrage-Designer im Abfragemodus</span><span class="sxs-lookup"><span data-stu-id="96a89-160">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="96a89-161">Klicken Sie zum Umschalten des grafischen Abfrage-Designers in den Abfragemodus auf der Symbolleiste auf die Umschaltfläche **Entwurfsmodus** .</span><span class="sxs-lookup"><span data-stu-id="96a89-161">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="96a89-162">In der folgenden Abbildung werden die Teile des Abfrage-Designers im Abfragemodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96a89-162">The following figure indicates the parts of the query designer in Query mode.</span></span>

 <span data-ttu-id="96a89-163">![MDX-Abfrage-Designer für SAP BW in der Abfrageansicht](media/rsqd-dssapbw-mdx-querymode.gif "MDX-Abfrage-Designer für SAP BW in der Abfrageansicht")</span><span class="sxs-lookup"><span data-stu-id="96a89-163">![SAP BW MDX query designer in query view](media/rsqd-dssapbw-mdx-querymode.gif "SAP BW MDX query designer in query view")</span></span>

 <span data-ttu-id="96a89-164">Die folgende Tabelle beschreibt die Funktion jedes Bereichs.</span><span class="sxs-lookup"><span data-stu-id="96a89-164">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="96a89-165">Bereich</span><span class="sxs-lookup"><span data-stu-id="96a89-165">Pane</span></span>|<span data-ttu-id="96a89-166">Funktion</span><span class="sxs-lookup"><span data-stu-id="96a89-166">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="96a89-167">Cube auswählen (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="96a89-167">Select Cube button</span></span>|<span data-ttu-id="96a89-168">Zeigt den zurzeit ausgewählten InfoCube, MultiProvider oder sonstigen Cube an.</span><span class="sxs-lookup"><span data-stu-id="96a89-168">Displays the currently selected InfoCube, MultiProvider, or other cube.</span></span>|
|<span data-ttu-id="96a89-169">Metadaten/Funktionen (Bereich)</span><span class="sxs-lookup"><span data-stu-id="96a89-169">Metadata/Functions pane</span></span>|<span data-ttu-id="96a89-170">Zeigt ein Fenster im Registerformat mit einer Liste verfügbarer Metadaten oder Funktionen an, die zum Erstellen des Abfragetexts verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="96a89-170">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="96a89-171">Variablen (Bereich)</span><span class="sxs-lookup"><span data-stu-id="96a89-171">Variables pane</span></span>|<span data-ttu-id="96a89-172">Zeigt die zurzeit definierten Variablen an, die für die Verwendung in der Abfrage verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="96a89-172">Displays the currently defined variables available for use in the query.</span></span>|
|<span data-ttu-id="96a89-173">Abfragebereich</span><span class="sxs-lookup"><span data-stu-id="96a89-173">Query pane</span></span>|<span data-ttu-id="96a89-174">Zeigt den aktuellen Abfragetext an.</span><span class="sxs-lookup"><span data-stu-id="96a89-174">Displays the current query text.</span></span>|
|<span data-ttu-id="96a89-175">Ergebnisbereich</span><span class="sxs-lookup"><span data-stu-id="96a89-175">Result pane</span></span>|<span data-ttu-id="96a89-176">Zeigt die Ergebnisse der Abfrage an.</span><span class="sxs-lookup"><span data-stu-id="96a89-176">Displays the results of the query.</span></span>|

 <span data-ttu-id="96a89-177">Aus dem Metadatenbereich können Sie Kennzahlen und Dimensionen von der Registerkarte **Metadaten** in den MDX-Abfragebereich ziehen. Der technische Name für die Metadaten wird an der Cursorposition eingefügt.</span><span class="sxs-lookup"><span data-stu-id="96a89-177">From the Metadata pane, you can drag key figures and dimensions from the **Metadata** tab onto the MDX Query pane; the technical name for the metadata is inserted at the cursor.</span></span> <span data-ttu-id="96a89-178">Sie können Funktionen von der Registerkarte **Funktionen** in den MDX-Abfragebereich ziehen.</span><span class="sxs-lookup"><span data-stu-id="96a89-178">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="96a89-179">Wenn Sie die Abfrage ausführen, zeigt der Ergebnisbereich die Ergebnisse für die aktuelle MDX-Abfrage an.</span><span class="sxs-lookup"><span data-stu-id="96a89-179">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

 <span data-ttu-id="96a89-180">Wenn es sich bei dem von Ihnen ausgewählten Cube um eine webfähige Abfrage handelt, werden Sie aufgefordert, statische Standardwerte für die vorhandenen Variablen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="96a89-180">If your selected cube is a Web-enabled query, you will be prompted to set static default values for the existing variables.</span></span> <span data-ttu-id="96a89-181">Sie können dann Variablen in den MDX-Abfragebereich ziehen.</span><span class="sxs-lookup"><span data-stu-id="96a89-181">You can then drag variables onto the MDX Query pane.</span></span>

 <span data-ttu-id="96a89-182">Im Metadatenbereich und im Variablenbereich werden Anzeigenamen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="96a89-182">The Metadata and Variable panes display friendly names.</span></span> <span data-ttu-id="96a89-183">Wenn Sie die Objekte im MDX-Abfragebereich ablegen, sehen Sie, wie die technischen Namen, die von der Datenquelle benötigt werden, in die MDX-Abfrage eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="96a89-183">When you drop the objects onto the MDX Query pane, you see the technical names needed by the data source entered into the MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="96a89-184">Symbolleiste für den grafischen Abfrage-Designer im Abfragemodus</span><span class="sxs-lookup"><span data-stu-id="96a89-184">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="96a89-185">Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen.</span><span class="sxs-lookup"><span data-stu-id="96a89-185">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="96a89-186">Die Schaltflächen der Symbolleiste sind im Entwurfs- und Abfragemodus identisch, aber die folgenden Schaltflächen sind für den Abfragemodus nicht aktiviert:</span><span class="sxs-lookup"><span data-stu-id="96a89-186">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="96a89-187">**Als Text bearbeiten**</span><span class="sxs-lookup"><span data-stu-id="96a89-187">**Edit As Text**</span></span>

-   <span data-ttu-id="96a89-188">**Berechnetes Element hinzufügen** (![Berechnetes Element hinzufügen](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen"))</span><span class="sxs-lookup"><span data-stu-id="96a89-188">**Add Calculated Member** (![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="96a89-189">**Leere Zellen anzeigen** (![Schaltfläche zum ein-/ausblenden leerer Zellen](../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen"))</span><span class="sxs-lookup"><span data-stu-id="96a89-189">**Show Empty Cells** (![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="96a89-190">**AutoExecute** (![Abfrage automatisch ausführen](../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen"))</span><span class="sxs-lookup"><span data-stu-id="96a89-190">**AutoExecute** (![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

-   <span data-ttu-id="96a89-191">**Löschen** (![Löschen](../analysis-services/media/rsqdicon-delete.gif "Löschen"))</span><span class="sxs-lookup"><span data-stu-id="96a89-191">**Delete** (![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete"))</span></span>

## <a name="see-also"></a><span data-ttu-id="96a89-192">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="96a89-192">See Also</span></span>
 [<span data-ttu-id="96a89-193">Abfrage-Designer &#40;Berichts-Generator&#41;</span><span class="sxs-lookup"><span data-stu-id="96a89-193">Query Designers &#40;Report Builder&#41;</span></span>](../../2014/reporting-services/query-designers-report-builder.md)

