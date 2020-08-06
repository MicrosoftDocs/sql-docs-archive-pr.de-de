---
title: 'Lektion 1: Erstellen eines neuen Projekts für tabellarische Modelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8b18c18116d5a9dacdf49fe23f4f545bb3a0f987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724293"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a><span data-ttu-id="4ca1d-102">Lektion 1: Erstellen eines neuen Tabellenmodellprojekts</span><span class="sxs-lookup"><span data-stu-id="4ca1d-102">Lesson 1: Create a New Tabular Model Project</span></span>
  <span data-ttu-id="4ca1d-103">In dieser Lektion erstellen Sie ein neues leeres Tabellenmodellprojekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ca1d-103">In this lesson, you will create a new, blank tabular model project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="4ca1d-104">Sobald das neue Projekt erstellt wird, können Sie mithilfe des Tabellenimport-Assistenten Daten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-104">Once your new project is created, you can begin adding data by using the Table Import Wizard.</span></span> <span data-ttu-id="4ca1d-105">Zusätzlich zum Erstellen eines neuen Projekts bietet diese Lektion auch eine kurze Einführung in die Umgebung zur Tabellenmodellerstellung in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ca1d-105">In addition to creating a new project, this lesson also includes a brief introduction to the tabular model authoring environment in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="4ca1d-106">Weitere Informationen zu den verschiedenen Typen von Tabellenmodellprojekten finden Sie unter [Tabellenmodellprojekte &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-model-projects-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1d-106">To learn more about the different types of tabular model projects, see [Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md).</span></span> <span data-ttu-id="4ca1d-107">Weitere Informationen zur Umgebung für die Erstellung von tabellarischen Modellen finden Sie unter tabellarischer [Modell-Designer &#40;SSAS ](tabular-model-designer-ssas-tabular.md)-Tabellen&#41;.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-107">To learn more about the tabular model authoring environment, see [Tabular Model Designer &#40;SSAS Tabular&#41;](tabular-model-designer-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="4ca1d-108">Geschätzte Zeit zum Bearbeiten dieser Lektion: **10 Minuten**</span><span class="sxs-lookup"><span data-stu-id="4ca1d-108">Estimated time to complete this lesson: **10 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4ca1d-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4ca1d-109">Prerequisites</span></span>  
 <span data-ttu-id="4ca1d-110">Dieses Thema stellt die erste Lektion in einem Lernprogramm zur Tabellenmodellerstellung dar.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-110">This topic is the first lesson in a tabular model authoring tutorial.</span></span> <span data-ttu-id="4ca1d-111">Um diese Lektion abzuschließen, benötigen Sie die auf einer SQL Server-Instanz installierte AdventureWorksDW-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-111">To complete this lesson, you must have the AdventureWorksDW database installed on a SQL Server instance.</span></span> <span data-ttu-id="4ca1d-112">Weitere Informationen finden Sie unter [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1d-112">For more information, see [Tabular Modeling &#40;Adventure Works Tutorial&#41;](tabular-modeling-adventure-works-tutorial.md).</span></span>  
  
## <a name="create-a-new-tabular-model-project"></a><span data-ttu-id="4ca1d-113">Erstellen eines neuen Tabellenmodellprojekts</span><span class="sxs-lookup"><span data-stu-id="4ca1d-113">Create a New Tabular Model Project</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project"></a><span data-ttu-id="4ca1d-114">Erstellen eines neuen tabellarischen Modellprojekts</span><span class="sxs-lookup"><span data-stu-id="4ca1d-114">To create a new tabular model project</span></span>  
  
1.  <span data-ttu-id="4ca1d-115">Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf das Menü **Datei** , auf **Neu**und dann auf **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="4ca1d-116">Klicken Sie im Dialogfeld **Neues Projekt** unter **installierte Vorlagen**auf **Business Intelligence**, und klicken Sie dann auf **Analysis Services**und dann auf **Analysis Services tabellarische Projekt**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-116">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, then click **Analysis Services**, and then click **Analysis Services Tabular Project**.</span></span>  
  
3.  <span data-ttu-id="4ca1d-117">Geben **Name**Sie unter Name `AW Internet Sales Tabular Model` den Namen ein, und geben Sie einen Speicherort für die Projektdateien an.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-117">In  **Name**, type `AW Internet Sales Tabular Model`, then specify a location for the project files.</span></span>  
  
     <span data-ttu-id="4ca1d-118">Standardmäßig entspricht der **Projektmappenname** dem Projektnamen; Sie können aber einen anderen Projektmappennamen erfassen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-118">By default, **Solution Name** will be the same as the project name; however, you can type a different solution name.</span></span>  
  
4.  <span data-ttu-id="4ca1d-119">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-119">Click **OK**.</span></span>  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a><span data-ttu-id="4ca1d-120">Einblick in die SQL Server Data Tools-Umgebung zur Tabellenmodellerstellung</span><span class="sxs-lookup"><span data-stu-id="4ca1d-120">Understanding the SQL Server Data Tools Tabular Model Authoring Environment</span></span>  
 <span data-ttu-id="4ca1d-121">Nachdem Sie nun ein neues Projekt für tabellarische Modelle erstellt haben, nehmen wir uns einen Moment Zeit, um die Umgebung für das Erstellen von tabellarischen Modellen in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 oder höher) zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-121">Now that you've created a new tabular model project, let's take a moment to explore the tabular model authoring environment in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 or later).</span></span>  
  
 <span data-ttu-id="4ca1d-122">Nach der Erstellung des Projekts wird es in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]geöffnet.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-122">After your project is created, it opens in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="4ca1d-123">Ein leeres Modell wird im Modell-Designer angezeigt, und die Datei **Model.bim** wird im Fenster des **Projektmappen-Explorers** ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-123">An empty model will appear in the model designer and the **Model.bim** file will be selected in the **Solution Explorer** window.</span></span> <span data-ttu-id="4ca1d-124">Wenn Sie Daten hinzufügen, werden Tabellen und Spalten im Designer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-124">When you add data, tables and columns will appear in the designer.</span></span> <span data-ttu-id="4ca1d-125">Wenn der Designer (das leere Fenster mit der Registerkarte Model. BIM) nicht angezeigt wird, doppelklicken Sie in **Projektmappen-Explorer**auf `AW Internet Sales Tabular Model` die Datei **Model. BIM** .</span><span class="sxs-lookup"><span data-stu-id="4ca1d-125">If you don't see the designer (the empty window with the Model.bim tab), in **Solution Explorer**, under `AW Internet Sales Tabular Model`, double click the **Model.bim** file.</span></span>  
  
 <span data-ttu-id="4ca1d-126">Sie können die grundlegenden Eigenschaften für das Projekt im Fenster **Eigenschaften** anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-126">You can view the basic project properties in the **Properties** window.</span></span> <span data-ttu-id="4ca1d-127">Klicken Sie in **Projektmappen-Explorer**auf `AW Internet Sales Tabular Model` .</span><span class="sxs-lookup"><span data-stu-id="4ca1d-127">In **Solution Explorer**, click `AW Internet Sales Tabular Model`.</span></span> <span data-ttu-id="4ca1d-128">Im Fenster **Eigenschaften** unter **Projektdatei**wird **AW Internet Sales Tabular Model.smproj**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-128">Notice in the **Properties** window, in **Project File**, you will see **AW Internet Sales Tabular Model.smproj**.</span></span> <span data-ttu-id="4ca1d-129">Dies ist der Projektdateiname, und unter **Projektordner**wird der Projektdateispeicherort angegeben.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-129">This is the project file name, and in **Project Folder**, you will see the project file location.</span></span>  
  
 <span data-ttu-id="4ca1d-130">Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das `AW Internet Sales Tabular Model` Projekt, und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-130">In **Solution Explorer**, right-click the `AW Internet Sales Tabular Model` project, and then click **Properties**.</span></span> <span data-ttu-id="4ca1d-131">Das Dialogfeld für die **Eigenschaftenseiten des AW Internet Sales-Tabellenmodells** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-131">The **AW Internet Sales Tabular Model Property Pages** dialog box appears.</span></span> <span data-ttu-id="4ca1d-132">Hierbei handelt es sich um die erweiterten Projekteigenschaften.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-132">These are the advanced project properties.</span></span> <span data-ttu-id="4ca1d-133">Sie werden später einige dieser Eigenschaften festlegen, wenn Sie für die Bereitstellung des Modells bereit sind.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-133">You will set some of these properties later when you are ready to deploy your model.</span></span>  
  
 <span data-ttu-id="4ca1d-134">Nun sehen wir uns die Modell Eigenschaften an.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-134">Now, let's look at the model properties.</span></span> <span data-ttu-id="4ca1d-135">Klicken Sie im **Projektmappen-Explorer**auf **Model.bim**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-135">In **Solution Explorer**, click **Model.bim**.</span></span> <span data-ttu-id="4ca1d-136">Im Fenster **Eigenschaften** sehen Sie jetzt die Modelleigenschaften, wobei die wichtigste Eigenschaft die Eigenschaft **DirectQuery-Modus** ist.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-136">In the **Properties** window, you will now see the model properties, most important of which is the **DirectQuery Mode** property.</span></span> <span data-ttu-id="4ca1d-137">Diese Eigenschaft gibt an, ob das Modell im In-Memory-Modus (Aus) oder im DirectQuery-Modus (Ein) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-137">This property specifies whether or not the model is deployed in In-Memory mode (Off) or DirectQuery mode (On).</span></span> <span data-ttu-id="4ca1d-138">In diesem Lernprogramm wird das Modell im InMemory-Modus erstellt und bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-138">For this tutorial, you will author and deploy your model in In-Memory mode.</span></span>  
  
 <span data-ttu-id="4ca1d-139">Wenn Sie ein neues Modell erstellen, werden bestimmte Modelleigenschaften automatisch gemäß den Datenmodellierungseinstellungen festgelegt, die im Dialogfeld für Tools und Optionen angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-139">When you create a new model, certain model properties are set automatically according to the Data Modeling settings that can be specified in the Tools\Options dialog box.</span></span> <span data-ttu-id="4ca1d-140">Die Eigenschaften für die Datensicherung, Beibehaltung des Arbeitsbereichs und den Arbeitsbereichsserver geben an, wie und wo die Arbeitsbereichsdatenbank (Datenbank zur Modellerstellung) gesichert, speicherintern beibehalten und erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-140">Data Backup, Workspace Retention, and Workspace Server properties specify how and where the workspace database (your model authoring database) is backed up, retained in-memory, and built.</span></span> <span data-ttu-id="4ca1d-141">Sie können diese Einstellungen später ändern, falls erforderlich, aber vorläufig lassen Sie diese Eigenschaften bitte unverändert.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-141">You can change these settings later if necessary, but for now, just leave these properties as they are.</span></span>  
  
 <span data-ttu-id="4ca1d-142">Bei der Installation von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]wurden der Visual Studio-Umgebung mehrere neue Menüelemente hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-142">When you installed [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], several new menu items were added to the Visual Studio environment.</span></span> <span data-ttu-id="4ca1d-143">Sehen wir uns die neuen Menü Elemente an, die für das Erstellen von tabellarischen Modellen spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-143">Let's look at the new menu items that are specific to authoring tabular models.</span></span> <span data-ttu-id="4ca1d-144">Klicken Sie in das Menü **Modell**.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-144">Click on the **Model** menu.</span></span> <span data-ttu-id="4ca1d-145">Über dieses Menü können Sie den Tabellenimport-Assistenten starten, vorhandene Verbindungen anzeigen und bearbeiten, Arbeitsbereichsdaten aktualisieren, Ihr Modell in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel mit der Funktion "In Excel analysieren" durchsuchen, Perspektiven und Rollen erstellen, die Modellsicht auswählen und Berechnungsoptionen festlegen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-145">From here, you can launch the Table Import Wizard, view and edit existing connections, refresh workspace data, browse your model in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel with the Analyze in Excel feature, create perspectives and roles, select the model view, and set calculation options.</span></span>  
  
 <span data-ttu-id="4ca1d-146">Klicken Sie auf das Menü **Tabelle** .</span><span class="sxs-lookup"><span data-stu-id="4ca1d-146">Click on the **Table** menu.</span></span> <span data-ttu-id="4ca1d-147">Hier können Sie Beziehungen zwischen Tabellen erstellen und verwalten, Datumstabelleneigenschaften festlegen, Partitionen erstellen und Tabelleneigenschaften bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-147">Here, you can create and manage relationships between tables, create and manage, specify date table settings, create partitions, and edit table properties.</span></span>  
  
 <span data-ttu-id="4ca1d-148">Klicken Sie auf das Menü **Spalte** .</span><span class="sxs-lookup"><span data-stu-id="4ca1d-148">Click on the **Column** menu.</span></span> <span data-ttu-id="4ca1d-149">Hier können Sie Spalten in einer Tabelle hinzufügen und löschen, Spalten fixieren und die Sortierreihenfolge angeben.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-149">Here, you can add and delete columns in a table, freeze columns, and specify sort order.</span></span> <span data-ttu-id="4ca1d-150">Sie können auch die AutoSumme-Funktion verwenden, um ein Standardaggregationsmeasure für eine ausgewählte Spalte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-150">You can also use the AutoSum feature to create a standard aggregation measure for a selected column.</span></span> <span data-ttu-id="4ca1d-151">Weitere Schaltflächen in der Symbolleiste bieten einen schnellen Zugriff auf häufig verwendete Funktionen und Befehle.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-151">Other toolbar buttons provide quick access to frequently used features and commands.</span></span>  
  
 <span data-ttu-id="4ca1d-152">Erkunden Sie einige der Dialogfelder und Positionen für verschiedene Funktionen, die für die Erstellung von Tabellenmodellen konzipiert sind.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-152">Explore some of the dialogs and locations for various features specific to authoring tabular models.</span></span> <span data-ttu-id="4ca1d-153">Obwohl einige Elemente noch nicht aktiv sind, erhalten Sie dennoch einen Einblick in die Umgebung zur Tabellenmodellerstellung.</span><span class="sxs-lookup"><span data-stu-id="4ca1d-153">While some items will not yet be active, you can get a good idea of the tabular model authoring environment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4ca1d-154">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="4ca1d-154">Next Steps</span></span>  
 <span data-ttu-id="4ca1d-155">Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 2: Hinzufügen von Daten](lesson-2-add-data.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1d-155">To continue this tutorial, go to the next lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
  