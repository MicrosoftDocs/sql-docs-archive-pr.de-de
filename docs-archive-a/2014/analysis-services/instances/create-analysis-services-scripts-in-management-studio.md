---
title: Erstellen von Analysis Services Skripts in Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bb380e271510ea5a35860d4850bfaeed3aad8cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698811"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a><span data-ttu-id="52fa6-102">Erstellen von Analysis Services-Skripts in Management Studio</span><span class="sxs-lookup"><span data-stu-id="52fa6-102">Create Analysis Services Scripts in Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="52fa6-103">schließt Skriptgenerierungsfunktionen, Vorlagen und Editoren ein, mit denen Sie Analysis Services-Objekte und Tasks schreiben können.</span><span class="sxs-lookup"><span data-stu-id="52fa6-103">includes script generation features, templates, and editors that you can use to script Analysis Services objects and tasks.</span></span>  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a><span data-ttu-id="52fa6-104">Script Analysis Services-Tasks in Management Studio</span><span class="sxs-lookup"><span data-stu-id="52fa6-104">Script Analysis Services Tasks in Management Studio</span></span>  
 <span data-ttu-id="52fa6-105">Sie können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Skripts erstellen, indem auf eine der Skriptoptionen in einem taskbezogenen Dialogfeld geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="52fa6-105">Scripting tasks in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by clicking one of the Script options in a task-oriented dialog box.</span></span> <span data-ttu-id="52fa6-106">Alle Dialogfelder, die Sie zum Ausführen von Aufgaben verwenden (z. B. Sicherung oder Wiederherstellungsdatenbank, Objektverarbeitung oder Aggregationsentwurf), beinhalten oben eine Skriptoption.</span><span class="sxs-lookup"><span data-stu-id="52fa6-106">All of the dialog boxes that you use to perform tasks such as backup or restore database, process an object, or design an aggregation, include a Script option at the top of the dialog box.</span></span> <span data-ttu-id="52fa6-107">Durch die Auswahl einer dieser Optionen wird auf Grundlage der Informationen und der Einstellungen im Dialogfeld ein XMLA-Skript generiert.</span><span class="sxs-lookup"><span data-stu-id="52fa6-107">Selecting one of these options generates an XMLA script based on the information and settings in the dialog box.</span></span>  
  
 <span data-ttu-id="52fa6-108">Standardmäßig wird das Skript generiert und in einem XMLA-Abfrage-Editor eingefügt. Sie können die Skriptoptionsliste jedoch auch erweitern, um das Skript an die Windows-Zwischenablage oder eine Datei weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="52fa6-108">By default, the script is generated and placed in an XMLA query editor, but you can also expand the Script option list to direct the script to the Windows Clipboard or a file.</span></span>  
  
#### <a name="to-script-an-analysis-services-task"></a><span data-ttu-id="52fa6-109">So erstellen Sie Skripts für einen Analysis Services-Task</span><span class="sxs-lookup"><span data-stu-id="52fa6-109">To script an Analysis Services task</span></span>  
  
1.  <span data-ttu-id="52fa6-110">Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her.</span><span class="sxs-lookup"><span data-stu-id="52fa6-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="52fa6-111">Klicken Sie mit der rechten Maustaste auf eine Datenbank, und klicken Sie auf **Sichern**.</span><span class="sxs-lookup"><span data-stu-id="52fa6-111">Right-click a database and click **Backup**.</span></span> <span data-ttu-id="52fa6-112">Daraufhin wird das Dialogfeld Datenbank sichern geöffnet.</span><span class="sxs-lookup"><span data-stu-id="52fa6-112">This opens the Backup Database dialog box.</span></span> <span data-ttu-id="52fa6-113">Geben Sie einen Sicherungsdateinamen an, und wählen Sie die gewünschten Optionen für diese Sicherung aus.</span><span class="sxs-lookup"><span data-stu-id="52fa6-113">Specify a backup file name and choose the options you want for this backup.</span></span>  
  
3.  <span data-ttu-id="52fa6-114">Klicken Sie auf **Skript** am oberen Rand des Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="52fa6-114">Click **Script** at the top of the dialog box.</span></span> <span data-ttu-id="52fa6-115">Die Funktion Skript ist ein Teil aller taskbasierten Dialogfelder in Management Studio.</span><span class="sxs-lookup"><span data-stu-id="52fa6-115">The Script feature is part of all task-based dialog boxes in Management Studio.</span></span> <span data-ttu-id="52fa6-116">Es hat die folgenden Optionen: **Skript für Aktion in Fenster 'Neue Abfrage' schreiben** , um das Abfrage-Editor-Fenster zu öffnen, **Skript für Aktion in Datei schreiben** , um das XMLA-Skript in einer Datei zu speichern, oder **Skript für Aktion in Zwischenablage schreiben** , um das XMLA-Skript in der Zwischenablage zu speichern.</span><span class="sxs-lookup"><span data-stu-id="52fa6-116">It has the following options: **Script Action to New Query Window** to open the query editor window, **Script Action to File** to save the XMLA script to a file, or **Script Action to Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
     <span data-ttu-id="52fa6-117">Beachten Sie, dass die Option **Skript für Aktion in Auftrag schreiben** , die in Management Studio als Skriptoption aufgelistet wird, für Analysis Services-Skripts nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="52fa6-117">Note that the **Script Action to Job** option that is listed as a script option in Management Studio is not supported for Analysis Services scripts.</span></span>  
  
4.  <span data-ttu-id="52fa6-118">Wenn Sie die Standardoption **Skript für Aktion in Fenster 'Neue Abfrage' schreiben**aktivieren, wird ein generiertes Skript in einem XMLA-Abfragefenster eingefügt.</span><span class="sxs-lookup"><span data-stu-id="52fa6-118">If you select the default option, **Script Action to New Query Window**, a generated script is placed in an XMLA query window.</span></span>  
  
     <span data-ttu-id="52fa6-119">Sie können jetzt das Dialogfeld Datenbank sichern und das XMLA-Skript direkt bearbeiten oder ausführen.</span><span class="sxs-lookup"><span data-stu-id="52fa6-119">You can now close the Backup Database dialog box and edit or run the XMLA script directly.</span></span>  
  
## <a name="script-analysis-services-objects-in-management-studio"></a><span data-ttu-id="52fa6-120">Script Analysis Services-Objekte in Management Studio</span><span class="sxs-lookup"><span data-stu-id="52fa6-120">Script Analysis Services Objects in Management Studio</span></span>  
 <span data-ttu-id="52fa6-121">Die Skripterstellung für Objekte mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] wird ausgeführt durch Klicken mit der rechten Maustaste auf ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und Auswählen von entweder **CREATE in**, **ALTER in**oder **DELETE in**.</span><span class="sxs-lookup"><span data-stu-id="52fa6-121">Scripting objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by right-clicking an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and selecting either **Create to**, **Alter to**, or **Delete to**.</span></span> <span data-ttu-id="52fa6-122">Jede dieser Optionen kann für ein Fenster oder eine Datei gelten, aber unabhängig davon, wofür das Skript gilt, wird es in Form eines DDL-Skripts in einem XMLA-Wrapper erstellt.</span><span class="sxs-lookup"><span data-stu-id="52fa6-122">Each of these options can be directed to a window or a file, but regardless of where the script is directed to, it will come in the form of a DDL script in an XMLA wrapper.</span></span> <span data-ttu-id="52fa6-123">Ein großer Vorteil solcher Skripts ist, dass sie auf jedem Server ausgeführt werden können, auf den Sie sie verweisen.</span><span class="sxs-lookup"><span data-stu-id="52fa6-123">One great advantage to such scripts is that they can be run against any server you point them at.</span></span> <span data-ttu-id="52fa6-124">Namen in den Skripts können geändert werden, und sie können auf iterativer Basis zur Massenerstellung, Änderung oder zur Löschung von Objekten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="52fa6-124">Also, names in the scripts can be changed and run on an iterative basis for mass construction, alteration, or deletion of objects.</span></span>  
  
 <span data-ttu-id="52fa6-125">Objekte, die Sie schreiben können, schließen die Elemente einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank ein, einschließlich Datenquellen, Datenquellensichten, Cubes, Dimensionen, Miningstrukturen und Rollen.</span><span class="sxs-lookup"><span data-stu-id="52fa6-125">Objects that you can script include the elements of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, including data sources, data source views, cubes, dimensions, mining structures, and roles.</span></span>  
  
 <span data-ttu-id="52fa6-126">Erforderliche Komponenten schließen ein Verständnis für XML for Analysis (XMLA) ein.</span><span class="sxs-lookup"><span data-stu-id="52fa6-126">Prerequisites include an understanding of XML for Analysis (XMLA).</span></span> <span data-ttu-id="52fa6-127">Glücklicherweise verfügt [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] über eine Funktion, mit der das zum Erstellen von Objekten wie Cubes benötigte XMLA-Skript automatisch erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="52fa6-127">Fortunately, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has a feature that automatically creates the XMLA script required to create objects, such as cubes.</span></span> <span data-ttu-id="52fa6-128">Diese Automatisierungsfunktion erleichtert die Verwendung von XMLA.</span><span class="sxs-lookup"><span data-stu-id="52fa6-128">This automation feature helps reduce the learning curve for XMLA.</span></span> <span data-ttu-id="52fa6-129">Weitere Informationen zur Verwendung von XMLA finden Sie unter [Entwickeln mit XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="52fa6-129">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span> <span data-ttu-id="52fa6-130">Weitere Informationen zur Verwendung von XMLA finden Sie unter [Entwickeln mit XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span><span class="sxs-lookup"><span data-stu-id="52fa6-130">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52fa6-131">Wenn Sie Skripts für das Role-Objekt erstellen, müssen Sie sich darüber bewusst sein, dass die Sicherheitsberechtigungen in den Objekten enthalten sind, die sie sichern, statt in der Sicherheitsrolle, der sie zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="52fa6-131">When scripting the Role Object, be aware that security permissions are contained by the objects they secure rather than with the security role with which they are associated.</span></span>  
  
#### <a name="to-script-analysis-services-objects"></a><span data-ttu-id="52fa6-132">So erstellen Sie Skripts für Analysis Services-Objekte</span><span class="sxs-lookup"><span data-stu-id="52fa6-132">To script Analysis Services objects</span></span>  
  
1.  <span data-ttu-id="52fa6-133">Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]her.</span><span class="sxs-lookup"><span data-stu-id="52fa6-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="52fa6-134">Suchen Sie das Objekt, für das Sie ein Skript zum Erstellen, Ändern oder Löschen von Objekten erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="52fa6-134">Locate the object for which you want to create a script that either creates, alters, or deletes objects.</span></span>  
  
3.  <span data-ttu-id="52fa6-135">Klicken Sie mit der rechten Maustaste auf das Objekt, zeigen Sie auf **Skript für Cube als**, zeigen Sie auf **CREATE in**, **ALTER in**oder **DELETE in**, und klicken Sie anschließend auf eine der folgenden Optionen: **Neues Abfrage-Editorfenster** zum Öffnen des Abfrage-Editorfensters, **Datei** zum Speichern des XMLA-Skripts in einer Datei oder **Zwischenablage** zum Speichern des XMLA-Skripts in der Zwischenablage.</span><span class="sxs-lookup"><span data-stu-id="52fa6-135">Right-click the object, point to **Script Cube as**, point to **CREATE To**, **ALTER To**, or **Delete To**, and then click one of the following options: **New Query Editor Window** to open the query editor window, **File** to save the XMLA script to a file, or **Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52fa6-136">Normalerweise würden Sie **Datei** auswählen, wenn Sie mehrere verschiedene Versionen der Datei erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="52fa6-136">Typically, you would select **File** if you want to create multiple different versions of the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52fa6-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="52fa6-137">See Also</span></span>  
 <span data-ttu-id="52fa6-138">[Skripterstellung für administrative Aufgaben in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="52fa6-138">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="52fa6-139">XMLA-Abfrage-Editor &#40;Analysis Services – Mehrdimensionale Daten&#41;</span><span class="sxs-lookup"><span data-stu-id="52fa6-139">XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  