---
title: Veraltete Analysis Services Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b3de78dfea70196e0c2855167e5ce2fda2369a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718895"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a><span data-ttu-id="c3f34-102">Veraltete Analysis Services-Funktionen in SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="c3f34-102">Deprecated Analysis Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="c3f34-103">In diesem Thema werden die als veraltet markierten Funktionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]noch verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c3f34-103">This topic describes the deprecated [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c3f34-104">Diese Funktionen werden voraussichtlich in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]entfernt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c3f34-105">Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c3f34-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a><span data-ttu-id="c3f34-106">Funktionen, die in der nächsten Version von SQL Server nicht unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="c3f34-106">Features Not Supported in the Next Version of SQL Server</span></span>  
 <span data-ttu-id="c3f34-107">Die folgenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-107">The following [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features will not be supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c3f34-108">Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c3f34-108">Do not use these features in new development work, and modify applications that currently use these features as soon as possible.</span></span>  
  
|<span data-ttu-id="c3f34-109">Category</span><span class="sxs-lookup"><span data-stu-id="c3f34-109">Category</span></span>|<span data-ttu-id="c3f34-110">Als veraltet markierte Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-110">Deprecated feature</span></span>|<span data-ttu-id="c3f34-111">Ersatz</span><span class="sxs-lookup"><span data-stu-id="c3f34-111">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="c3f34-112">MDX-Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-112">MDX Function</span></span>|<span data-ttu-id="c3f34-113">CalculationPassValue-Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-113">CalculationPassValue function</span></span>|<span data-ttu-id="c3f34-114">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-114">None.</span></span> <span data-ttu-id="c3f34-115">Die OLAP-Engine verwaltet den Berechnungsdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="c3f34-115">The OLAP engine manages the calculation pass.</span></span> <span data-ttu-id="c3f34-116">Diese Funktion wird nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-116">This function is no longer needed.</span></span>|  
|<span data-ttu-id="c3f34-117">MDX-Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-117">MDX Function</span></span>|<span data-ttu-id="c3f34-118">CalculationCurrentPass-Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-118">CalculationCurrentPass function</span></span>|<span data-ttu-id="c3f34-119">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-119">None.</span></span> <span data-ttu-id="c3f34-120">Die OLAP-Engine verwaltet den Berechnungsdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="c3f34-120">The OLAP engine manages the calculation pass.</span></span> <span data-ttu-id="c3f34-121">Diese Funktion wird nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-121">This function is no longer needed.</span></span>|  
|<span data-ttu-id="c3f34-122">Multidimensional Expressions (MDX)</span><span class="sxs-lookup"><span data-stu-id="c3f34-122">Multidimensional Expressions (MDX)</span></span>|<span data-ttu-id="c3f34-123">Der Hinweis für den Abfrageoptimierer NON_EMPTY_BEHAVIOR wurde standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c3f34-123">NON_EMPTY_BEHAVIOR query optimizer hint was turned on by default.</span></span>|<span data-ttu-id="c3f34-124">Der Hinweis für den Abfrageoptimierer NON_EMPTY_BEHAVIOR wird in einer zukünftigen Version standardmäßig deaktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="c3f34-124">The NON_EMPTY_BEHAVIOR query optimizer hint will be turned off by default in a future release.</span></span> <span data-ttu-id="c3f34-125">Der MDX-Optimierungshinweis kann zu falschen Ergebnissen führen, wenn er nicht ordnungsgemäß verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c3f34-125">It is an MDX optimization hint that can produce incorrect results when it is not used correctly.</span></span>|  
|<span data-ttu-id="c3f34-126">Andere</span><span class="sxs-lookup"><span data-stu-id="c3f34-126">Other</span></span>|<span data-ttu-id="c3f34-127">Systeminterne Zelleneigenschaft CELL_EVALUATION_LIST</span><span class="sxs-lookup"><span data-stu-id="c3f34-127">CELL_EVALUATION_LIST intrinsic cell property</span></span>|<span data-ttu-id="c3f34-128">Stellte ursprünglich eine Liste ausgewerteter Formeln bereit, die für eine Zelle gelten.</span><span class="sxs-lookup"><span data-stu-id="c3f34-128">Originally provided a list of evaluated formulas that apply to a cell.</span></span> <span data-ttu-id="c3f34-129">Sie ist in dieser Version von Analysis Services leer.</span><span class="sxs-lookup"><span data-stu-id="c3f34-129">It is blank in this release of Analysis Services.</span></span>  <span data-ttu-id="c3f34-130">Die Lösungsreihenfolge wird jetzt im MDX-Skript angegeben.</span><span class="sxs-lookup"><span data-stu-id="c3f34-130">Solve order is now specified in MDX script.</span></span> <span data-ttu-id="c3f34-131">Weitere Informationen finden Sie Untergrund Legendes zu [Durchlauf-und Lösungs Reihenfolge &#40;MDX&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)</span><span class="sxs-lookup"><span data-stu-id="c3f34-131">For more information, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)</span></span>|  
|<span data-ttu-id="c3f34-132">Objekte</span><span class="sxs-lookup"><span data-stu-id="c3f34-132">Objects</span></span>|<span data-ttu-id="c3f34-133">COM-Assemblys</span><span class="sxs-lookup"><span data-stu-id="c3f34-133">COM assemblies</span></span>|<span data-ttu-id="c3f34-134">COM-Assemblys können ein Sicherheitsrisiko darstellen.</span><span class="sxs-lookup"><span data-stu-id="c3f34-134">COM assemblies can pose a security risk.</span></span> <span data-ttu-id="c3f34-135">COM-Assemblys werden in einer zukünftigen Version nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-135">Support for COM assemblies will be removed in a future release.</span></span>|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a><span data-ttu-id="c3f34-136">Funktionen, die in einer zukünftigen Version von SQL Server nicht unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="c3f34-136">Features Not Supported in a Future Version of SQL Server</span></span>  
 <span data-ttu-id="c3f34-137">Die folgenden Funktionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-137">The following [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="c3f34-138">Die betreffende Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde noch nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c3f34-138">The specific version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has not been determined.</span></span>  
  
|<span data-ttu-id="c3f34-139">Category</span><span class="sxs-lookup"><span data-stu-id="c3f34-139">Category</span></span>|<span data-ttu-id="c3f34-140">Als veraltet markierte Funktion</span><span class="sxs-lookup"><span data-stu-id="c3f34-140">Deprecated feature</span></span>|<span data-ttu-id="c3f34-141">Ersatz</span><span class="sxs-lookup"><span data-stu-id="c3f34-141">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="c3f34-142">Mehrdimensionale Modelle</span><span class="sxs-lookup"><span data-stu-id="c3f34-142">Multidimensional models</span></span>|<span data-ttu-id="c3f34-143">Remotepartitionen</span><span class="sxs-lookup"><span data-stu-id="c3f34-143">Remote partitions</span></span>|<span data-ttu-id="c3f34-144">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-144">None.</span></span> <span data-ttu-id="c3f34-145">Verwenden Sie stattdessen lokale Partitionen.</span><span class="sxs-lookup"><span data-stu-id="c3f34-145">Use local partitions instead.</span></span> <span data-ttu-id="c3f34-146">Weitere Informationen finden Sie unter [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f34-146">See [Create and Manage a Local Partition &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) for more information.</span></span>|  
|<span data-ttu-id="c3f34-147">Mehrdimensionale Modelle</span><span class="sxs-lookup"><span data-stu-id="c3f34-147">Multidimensional models</span></span>|<span data-ttu-id="c3f34-148">Remoteverknüpfte Measuregruppen</span><span class="sxs-lookup"><span data-stu-id="c3f34-148">Remote linked measure groups</span></span>|<span data-ttu-id="c3f34-149">Eine remoteverknüpfte Measuregruppe ist eine verknüpfte Measuregruppe, die eine Datenquelle auf einem Remoteserver verwendet.</span><span class="sxs-lookup"><span data-stu-id="c3f34-149">A remote linked measure group is a linked measure group using a data source on a remote server.</span></span> <span data-ttu-id="c3f34-150">Die Fähigkeit, eine Remotedatenquelle für eine verknüpfte Measuregruppe zu verwenden, ist jetzt als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="c3f34-150">The ability to use a remote data source for a linked measure group is now scheduled for deprecation.</span></span><br /><br /> <span data-ttu-id="c3f34-151">Es gibt keinen Ersatz für diese Funktion.</span><span class="sxs-lookup"><span data-stu-id="c3f34-151">There is no replacement for this feature.</span></span> <span data-ttu-id="c3f34-152">Es wird empfohlen, stattdessen lokale verknüpfte Measuregruppen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c3f34-152">We recommend using local linked measure groups instead.</span></span> <span data-ttu-id="c3f34-153">Weitere Informationen finden Sie unter [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f34-153">See [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) for more information.</span></span>|  
|<span data-ttu-id="c3f34-154">Mehrdimensionale Modelle</span><span class="sxs-lookup"><span data-stu-id="c3f34-154">Multidimensional models</span></span>|<span data-ttu-id="c3f34-155">Dimensionales Rückschreiben</span><span class="sxs-lookup"><span data-stu-id="c3f34-155">Dimensional writeback</span></span>|<span data-ttu-id="c3f34-156">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-156">None.</span></span> <span data-ttu-id="c3f34-157">Verwenden Sie das Rückschreiben von Partitionen, wenn Sie Funktionen zum Rückschreiben benötigen.</span><span class="sxs-lookup"><span data-stu-id="c3f34-157">Use partition writeback if you require writeback capability.</span></span> <span data-ttu-id="c3f34-158">Weitere Informationen finden Sie unter [Festlegen des Rück Schreibens von Partitionen](multidimensional-models/set-partition-writeback.md) .</span><span class="sxs-lookup"><span data-stu-id="c3f34-158">See [Set Partition Writeback](multidimensional-models/set-partition-writeback.md) for more information.</span></span>|  
|<span data-ttu-id="c3f34-159">Mehrdimensionale Modelle</span><span class="sxs-lookup"><span data-stu-id="c3f34-159">Multidimensional models</span></span>|<span data-ttu-id="c3f34-160">Verknüpfte Dimensionen</span><span class="sxs-lookup"><span data-stu-id="c3f34-160">Linked dimensions</span></span>|<span data-ttu-id="c3f34-161">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-161">None.</span></span> <span data-ttu-id="c3f34-162">Sie können Dimensionen in zusätzliche Modelle kopieren, statt eine Verknüpfung mit einer Dimension in einem anderen Modell zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c3f34-162">Consider copying dimensions to additional models rather than linking to a dimension in another model.</span></span>|  
|<span data-ttu-id="c3f34-163">MDX</span><span class="sxs-lookup"><span data-stu-id="c3f34-163">MDX</span></span>|<span data-ttu-id="c3f34-164">Non_Empty_Behavior-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c3f34-164">Non_Empty_Behavior property</span></span>|<span data-ttu-id="c3f34-165">Keine.</span><span class="sxs-lookup"><span data-stu-id="c3f34-165">None.</span></span> <span data-ttu-id="c3f34-166">Wenn Sie ein berechnetes Element erstellen, wird durch das falsche Festlegen dieser Eigenschaft die Wahrscheinlichkeit erhöht, dass ungültige Ergebnisse zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c3f34-166">When creating a calculated member, setting this property incorrectly increases the likelihood of returning invalid results.</span></span> <span data-ttu-id="c3f34-167">Durch kürzliche Optimierungen der OLAP-Engine wurden Vorgänge für Datasets mit geringer Dichte verbessert, sodass diese Eigenschaft weniger relevant geworden ist.</span><span class="sxs-lookup"><span data-stu-id="c3f34-167">Recent optimizations to the OLAP engine have improved operations over sparse data sets, making this property less relevant.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3f34-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c3f34-168">See Also</span></span>  
 <span data-ttu-id="c3f34-169">[Analysis Services Abwärtskompatibilität](analysis-services-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="c3f34-169">[Analysis Services Backward Compatibility](analysis-services-backward-compatibility.md) </span></span>  
 [<span data-ttu-id="c3f34-170">Nicht mehr unterstützte Analysis Services-Funktionalität in SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="c3f34-170">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  