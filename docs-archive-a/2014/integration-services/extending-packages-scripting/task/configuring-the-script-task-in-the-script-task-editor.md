---
title: Konfigurieren des Skripttasks im Skripttask-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75b4a030e6c5baa2e26c610b0e8216843c8cca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615448"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a><span data-ttu-id="92a16-102">Konfigurieren des Skripttasks im Skripttask-Editor</span><span class="sxs-lookup"><span data-stu-id="92a16-102">Configuring the Script Task in the Script Task Editor</span></span>
  <span data-ttu-id="92a16-103">Bevor Sie benutzerdefinierten Code in den Skripttask schreiben, konfigurieren Sie auf den drei Seiten im **Skripttask-Editor** seine Prinzipaleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="92a16-103">Before you write custom code in the Script task, you configure its principal properties in the three pages of the **Script Task Editor**.</span></span> <span data-ttu-id="92a16-104">Mithilfe des Eigenschaftsfensters können Sie zusätzliche Taskeigenschaften, die nicht nur für den Skripttask vorhanden sind, konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="92a16-104">You can configure additional task properties that are not unique to the Script task by using the Properties window.</span></span>

> [!NOTE]
>  <span data-ttu-id="92a16-105">Anders als in früheren Versionen, in denen Sie angeben konnten, ob die Skripts vorkompiliert sind, werden ab [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] alle Skripts vorkompiliert.</span><span class="sxs-lookup"><span data-stu-id="92a16-105">Unlike earlier versions where you could indicate whether scripts were precompiled, all scripts are precompiled beginning in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].</span></span>

## <a name="general-page-of-the-script-task-editor"></a><span data-ttu-id="92a16-106">Seite 'Allgemein' des Skripttask-Editors</span><span class="sxs-lookup"><span data-stu-id="92a16-106">General Page of the Script Task Editor</span></span>
 <span data-ttu-id="92a16-107">Auf der Seite **Allgemein** im **Skripttask-Editor** können Sie dem Skripttask einen eindeutigen Namen und eine Beschreibung zuweisen.</span><span class="sxs-lookup"><span data-stu-id="92a16-107">On the **General** page of the **Script Task Editor**, you assign a unique name and a description for the Script task.</span></span>

## <a name="script-page-of-the-script-task-editor"></a><span data-ttu-id="92a16-108">Seite 'Skript' des Skripttask-Editors</span><span class="sxs-lookup"><span data-stu-id="92a16-108">Script Page of the Script Task Editor</span></span>
 <span data-ttu-id="92a16-109">Auf der Seite **Skript** im **Skripttask-Editor** werden die benutzerdefinierten Eigenschaften des Skripttasks angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92a16-109">The **Script** page of the **Script Task Editor** displays the custom properties of the Script task.</span></span>

### <a name="scriptlanguage-property"></a><span data-ttu-id="92a16-110">ScriptLanguage-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="92a16-110">ScriptLanguage Property</span></span>
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="92a16-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) unterstützt die Programmiersprachen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span><span class="sxs-lookup"><span data-stu-id="92a16-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# programming languages.</span></span> <span data-ttu-id="92a16-112">Nach der Erstellung eines Skripts im Skripttask können Sie den Wert der **ScriptLanguage**-Eigenschaft nicht mehr ändern.</span><span class="sxs-lookup"><span data-stu-id="92a16-112">After you create a script in the Script task, you cannot change value of the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="92a16-113">Um die Standardskriptsprache für Skripttasks und Skriptkomponenten festzulegen, verwenden Sie im Dialogfeld **Optionen** auf der Seite **Allgemein** die **ScriptLanguage**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="92a16-113">To set the default script language for Script tasks and Script components, use the **ScriptLanguage** property on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="92a16-114">Weitere Informationen finden Sie unter [General Page](../../general-page-of-integration-services-designers-options.md).</span><span class="sxs-lookup"><span data-stu-id="92a16-114">For more information, see [General Page](../../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="entrypoint-property"></a><span data-ttu-id="92a16-115">EntryPoint-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="92a16-115">EntryPoint Property</span></span>
 <span data-ttu-id="92a16-116">Die `EntryPoint`-Eigenschaft gibt die Methode für die `ScriptMain`-Klasse im VSTA-Projekt an, die die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Laufzeit als Einstiegspunkt in den Code des Skripttasks aufruft.</span><span class="sxs-lookup"><span data-stu-id="92a16-116">The `EntryPoint` property specifies the method on the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="92a16-117">Die `ScriptMain`-Klasse ist die Standardklasse, die von den Skriptvorlagen generiert wird.</span><span class="sxs-lookup"><span data-stu-id="92a16-117">The `ScriptMain` class is the default class generated by the script templates.</span></span>

 <span data-ttu-id="92a16-118">Wenn Sie den Namen der Methode im VSTA-Projekt ändern, müssen Sie den Wert der `EntryPoint`-Eigenschaft ändern.</span><span class="sxs-lookup"><span data-stu-id="92a16-118">If you change the name of the method in the VSTA project, you must change the value of the `EntryPoint` property.</span></span>

### <a name="readonlyvariables-and-readwritevariables-properties"></a><span data-ttu-id="92a16-119">Eigenschaften 'ReadOnlyVariables' und 'ReadWriteVariables'</span><span class="sxs-lookup"><span data-stu-id="92a16-119">ReadOnlyVariables and ReadWriteVariables Properties</span></span>
 <span data-ttu-id="92a16-120">Sie können kommagetrennte Listen von vorhandenen Variablen als Werte dieser Eigenschaften eingeben, um die Variablen für schreibgeschützten oder Lese-/Schreibzugriff im Code des Skripttasks verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="92a16-120">You can enter comma-delimited lists of existing variables as the values of these properties to make the variables available for read-only or read/write access within the Script task code.</span></span> <span data-ttu-id="92a16-121">Auf Variablen beider Typen wird im Code über die <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>-Eigenschaft des `Dts`-Objekts zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="92a16-121">Variables of both types are accessed in code through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="92a16-122">Weitere Informationen finden Sie unter [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span><span class="sxs-lookup"><span data-stu-id="92a16-122">For more information, see [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="92a16-123">Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.</span><span class="sxs-lookup"><span data-stu-id="92a16-123">Variable names are case-sensitive.</span></span>

 <span data-ttu-id="92a16-124">Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ( **…** ) neben dem Eigenschaftenfeld, um Variablen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="92a16-124">To select the variables, click the ellipsis (**...**) button next to the property field.</span></span> <span data-ttu-id="92a16-125">Weitere Informationen finden Sie unter [Select Variables Page](../../control-flow/select-variables-page.md) (Seite „Variablen auswählen“).</span><span class="sxs-lookup"><span data-stu-id="92a16-125">For more information, see [Select Variables Page](../../control-flow/select-variables-page.md).</span></span>

### <a name="edit-script-button"></a><span data-ttu-id="92a16-126">Schaltfläche 'Skript bearbeiten'</span><span class="sxs-lookup"><span data-stu-id="92a16-126">Edit Script Button</span></span>
 <span data-ttu-id="92a16-127">Über die Schaltfläche **Skript bearbeiten** wird die VSTA-Entwicklungsumgebung gestartet, in der Sie das benutzerdefinierte Skript schreiben.</span><span class="sxs-lookup"><span data-stu-id="92a16-127">The **Edit Script** button launches the VSTA development environment in which you write your custom script.</span></span> <span data-ttu-id="92a16-128">Weitere Informationen siehe [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md) (Codieren und Debuggen des Skripttasks).</span><span class="sxs-lookup"><span data-stu-id="92a16-128">For more information, see [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md).</span></span>

## <a name="expressions-page-of-the-script-task-editor"></a><span data-ttu-id="92a16-129">Seite 'Ausdrücke' des Skripttask-Editors</span><span class="sxs-lookup"><span data-stu-id="92a16-129">Expressions Page of the Script Task Editor</span></span>
 <span data-ttu-id="92a16-130">Auf der Seite **Ausdrücke** im **Skripttask-Editor** können Sie Ausdrücke verwenden, um Werte für die Eigenschaften des oben aufgeführten Skripttasks und für viele weitere Taskeigenschaften bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="92a16-130">On the **Expressions** page of the **Script Task Editor**, you can use expressions to provide values for the properties of the Script task listed above and for many other task properties.</span></span> <span data-ttu-id="92a16-131">Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="92a16-131">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>

<span data-ttu-id="92a16-132">![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  </span><span class="sxs-lookup"><span data-stu-id="92a16-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="92a16-133">Die neuesten Downloads, Artikel, Beispiele und Videos von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] sowie ausgewählte Lösungen aus der Community finden Sie auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Seite auf MSDN:</span><span class="sxs-lookup"><span data-stu-id="92a16-133">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="92a16-134">Besuchen Sie die Integration Services-Seite auf MSDN</span><span class="sxs-lookup"><span data-stu-id="92a16-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="92a16-135">Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="92a16-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="92a16-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="92a16-136">See Also</span></span>
 [<span data-ttu-id="92a16-137">Codieren und Debuggen des Skripttasks</span><span class="sxs-lookup"><span data-stu-id="92a16-137">Coding and Debugging the Script Task</span></span>](coding-and-debugging-the-script-task.md)

