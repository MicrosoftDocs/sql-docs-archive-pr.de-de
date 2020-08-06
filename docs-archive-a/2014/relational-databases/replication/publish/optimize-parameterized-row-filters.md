---
title: Optimieren von parametrisierten Zeilenfiltern |Microsoft Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1c6448d8e2dba7a68fab441d4d08fd4a4a1db4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724498"
---
# <a name="optimize-parameterized-row-filters"></a><span data-ttu-id="98ef2-102">Optimieren von parametrisierten Zeilenfiltern</span><span class="sxs-lookup"><span data-stu-id="98ef2-102">Optimize Parameterized Row Filters</span></span>
  <span data-ttu-id="98ef2-103">In diesem Thema wird beschrieben, wie parametrisierte Zeilenfilter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="98ef2-103">This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="98ef2-104">**In diesem Thema**</span><span class="sxs-lookup"><span data-stu-id="98ef2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="98ef2-105">**Vorbereitungen:**</span><span class="sxs-lookup"><span data-stu-id="98ef2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="98ef2-106">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="98ef2-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="98ef2-107">**So optimieren Sie parametrisierte Zeilenfilter mit:**</span><span class="sxs-lookup"><span data-stu-id="98ef2-107">**To optimize parameterized row filters, using:**</span></span>  
  
     [<span data-ttu-id="98ef2-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="98ef2-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="98ef2-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="98ef2-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="98ef2-110">Vorbereitungen</span><span class="sxs-lookup"><span data-stu-id="98ef2-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="98ef2-111">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="98ef2-111">Recommendations</span></span>  
  
-   <span data-ttu-id="98ef2-112">Wenn Sie parametrisierte Filter verwenden, können Sie festlegen, wie die Filter durch die Mergereplikation verarbeitet werden, indem Sie bei der Erstellung der Veröffentlichung entweder die Option **use partition groups** oder die Option **keep partition changes** wählen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-112">When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication.</span></span> <span data-ttu-id="98ef2-113">Diese Optionen verbessern bei Veröffentlichungen mit gefilterten Artikeln die Synchronisierungsleistung, da in der Veröffentlichungsdatenbank zusätzliche Metadaten gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="98ef2-113">These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database.</span></span> <span data-ttu-id="98ef2-114">Sie können steuern, wie die Daten auf die einzelnen Abonnenten aufgeteilt werden, indem Sie bei der Erstellung eines Artikels **partition options** festlegen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-114">You can control how the data is shared among Subscribers by setting **partition options** when you create an article.</span></span> <span data-ttu-id="98ef2-115">Weitere Informationen zu diesen Anforderungen finden Sie unter [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-115">For more information about these requirements, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="98ef2-116">Mit [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact-Abonnenten muss "keep_partition_changes" auf "true" festgelegt werden, um sicherzustellen, dass Löschvorgänge ordnungsgemäß weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="98ef2-116">With [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated.</span></span> <span data-ttu-id="98ef2-117">Wenn die Einstellung auf "false" festgelegt ist, erhält der Abonnent möglicherweise mehr Zeilen als erwartet.</span><span class="sxs-lookup"><span data-stu-id="98ef2-117">When set to false, the subscriber might have more rows than expected.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="98ef2-118">Verwenden von SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="98ef2-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="98ef2-119">Folgende Einstellungen können zur Optimierung von parametrisierten Zeilenfiltern verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="98ef2-119">The following settings can be used to optimize parameterized row filters:</span></span>  
  
 <span data-ttu-id="98ef2-120">**Partition Options**</span><span class="sxs-lookup"><span data-stu-id="98ef2-120">**Partition Options**</span></span>  
 <span data-ttu-id="98ef2-121">Legen Sie diese Option auf der Seite **Eigenschaften** des Dialogfelds **Artikeleigenschaften – \<Article>** oder über das Dialogfeld **Filter hinzufügen** fest.</span><span class="sxs-lookup"><span data-stu-id="98ef2-121">Set this option on the **Properties** page of the **Article Properties - \<Article>** dialog box, or in the **Add Filter** dialog box.</span></span> <span data-ttu-id="98ef2-122">Der Zugriff auf beide Dialogfelder ist über den Assistenten für neue Veröffentlichungen sowie über das Dialogfeld **Veröffentlichungseigenschaften – \<Publication>** verfügbar.</span><span class="sxs-lookup"><span data-stu-id="98ef2-122">Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="98ef2-123">Im Dialogfeld **Artikeleigenschaften – \<Article>** können Sie weitere Werte für diese Option angeben, die im Dialogfeld **Filter hinzufügen** nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="98ef2-123">The **Article Properties - \<Article>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.</span></span>  
  
 <span data-ttu-id="98ef2-124">**Partitionen im Voraus berechnen**</span><span class="sxs-lookup"><span data-stu-id="98ef2-124">**Precompute Partitions**</span></span>  
 <span data-ttu-id="98ef2-125">Diese Option ist standardmäßig auf **Wahr** festgelegt, wenn die Artikel in Ihrer Veröffentlichung einem Satz von Anforderungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-125">This option is set to **True** by default if the articles in your publication adhere to a set of requirements.</span></span> <span data-ttu-id="98ef2-126">Weitere Informationen zu diesen Anforderungen finden Sie unter [Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-126">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="98ef2-127">Diese Option können Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften – \<Publication>** ändern.</span><span class="sxs-lookup"><span data-stu-id="98ef2-127">Modify this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="98ef2-128">**Synchronisierung optimieren**</span><span class="sxs-lookup"><span data-stu-id="98ef2-128">**Optimize Synchronization**</span></span>  
 <span data-ttu-id="98ef2-129">Diese Option sollte nur auf **Wahr** festgelegt werden, wenn **Partitionen im Voraus berechnen** auf **Falsch**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="98ef2-129">This option should be set to **True** only if **Precompute Partitions** is set to **False**.</span></span> <span data-ttu-id="98ef2-130">Diese Option können Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften – \<Publication>** festlegen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-130">Set this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="98ef2-131">Weitere Informationen zum Assistenten für neue Veröffentlichungen sowie zum Zugriff auf das Dialogfeld **Veröffentlichungseigenschaften – \<Publication>** finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-131">For more information about using the New Publication Wizard and accessing the **Publication Properties - \<Publication>** dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a><span data-ttu-id="98ef2-132">So legen Sie Partitionsoptionen im Dialogfeld Filter hinzufügen bzw. Filter bearbeiten fest</span><span class="sxs-lookup"><span data-stu-id="98ef2-132">To set Partition options in the Add Filter or Edit Filter dialog box</span></span>  
  
1.  <span data-ttu-id="98ef2-133">Klicken Sie auf der Seite **Tabellenzeilen filtern** im Assistenten für neue Veröffentlichungen bzw. auf der Seite **Zeilen filtern** des Dialogfelds **Veröffentlichungseigenschaften - \<Publication>** zunächst auf **Hinzufügen** und anschließend auf **Filter hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="98ef2-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="98ef2-134">Erstellen Sie einen parametrisierten Filter.</span><span class="sxs-lookup"><span data-stu-id="98ef2-134">Create a parameterized filter.</span></span> <span data-ttu-id="98ef2-135">Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-135">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="98ef2-136">Wählen Sie die Option aus, mit der angegeben wird, wie Daten für mehrere Abonnenten freigegeben werden:</span><span class="sxs-lookup"><span data-stu-id="98ef2-136">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="98ef2-137">**Eine Zeile aus dieser Tabelle wird an mehrere Abonnements gesendet**</span><span class="sxs-lookup"><span data-stu-id="98ef2-137">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="98ef2-138">**Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**</span><span class="sxs-lookup"><span data-stu-id="98ef2-138">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="98ef2-139">Wenn Sie **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**auswählen, kann die Mergereplikation die Leistung optimieren, da weniger Metadaten gespeichert und verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="98ef2-139">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="98ef2-140">Sie müssen jedoch sicherstellen, dass die Daten so partitioniert werden, dass eine Zeile nicht für mehrere Abonnenten repliziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="98ef2-140">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="98ef2-141">Weitere Informationen finden Sie im Abschnitt zum Festlegen von Partitionsoptionen unter [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-141">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="98ef2-142">Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-142">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a><span data-ttu-id="98ef2-143">Festlegen von Partitionsoptionen im Dialogfeld „Artikeleigenschaften – \<Article>“</span><span class="sxs-lookup"><span data-stu-id="98ef2-143">To set Partition Options in the Article Properties - \<Article> dialog box</span></span>  
  
1.  <span data-ttu-id="98ef2-144">Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="98ef2-144">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="98ef2-145">Klicken Sie auf **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen** oder **Eigenschaften aller Tabellenartikel festlegen**.</span><span class="sxs-lookup"><span data-stu-id="98ef2-145">Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.</span></span>  
  
3.  <span data-ttu-id="98ef2-146">Geben Sie im Abschnitt **Zielobjekt** der Registerkarte **Eigenschaften** des Dialogfelds **Artikeleigenschaften – \<Article>** einen der folgenden Werte für **Partitionsoptionen** an:</span><span class="sxs-lookup"><span data-stu-id="98ef2-146">In the **Destination Object** section of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify one of the following values for **Partition Options**:</span></span>  
  
    -   <span data-ttu-id="98ef2-147">**Überlappend**</span><span class="sxs-lookup"><span data-stu-id="98ef2-147">**Overlapping**</span></span>  
  
    -   <span data-ttu-id="98ef2-148">**Überlappend, Datenänderungen außerhalb der Partition nicht zulassen**</span><span class="sxs-lookup"><span data-stu-id="98ef2-148">**Overlapping, disallow out-of-partition data changes**</span></span>  
  
    -   <span data-ttu-id="98ef2-149">**Nicht überlappend, ein Abonnement**</span><span class="sxs-lookup"><span data-stu-id="98ef2-149">**Nonoverlapping, single subscription**</span></span>  
  
    -   <span data-ttu-id="98ef2-150">**Nicht überlappend, für mehrere Abonnements freigegeben**</span><span class="sxs-lookup"><span data-stu-id="98ef2-150">**Nonoverlapping, shared between subscriptions**</span></span>  
  
     <span data-ttu-id="98ef2-151">Weitere Informationen zu diesen Optionen und dazu, in welcher Beziehung Sie zu den Optionen stehen, die im Dialogfeld **Filter hinzufügen** und **Filter bearbeiten** verfügbar sind, finden Sie im Abschnitt über das Festlegen von Partitionsoptionen unter [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-151">For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="98ef2-152">Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-152">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-precompute-partitions"></a><span data-ttu-id="98ef2-153">So legen Sie einen Wert für Partitionen im Voraus berechnen fest</span><span class="sxs-lookup"><span data-stu-id="98ef2-153">To set Precompute Partitions</span></span>  
  
1.  <span data-ttu-id="98ef2-154">Wählen Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften – \<Publication>** einen Wert für die Option **Partitionen im Voraus berechnen** aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-154">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value for the **Precompute Partitions** option.</span></span> <span data-ttu-id="98ef2-155">Die Eigenschaft ist in folgenden Fällen schreibgeschützt:</span><span class="sxs-lookup"><span data-stu-id="98ef2-155">The property is read-only if:</span></span>  
  
    -   <span data-ttu-id="98ef2-156">Die Veröffentlichung erfüllt die Anforderungen für im Voraus berechnete Partitionen nicht.</span><span class="sxs-lookup"><span data-stu-id="98ef2-156">The publication does not meet the requirements for precomputed partitions.</span></span>  
  
    -   <span data-ttu-id="98ef2-157">Es wurde noch keine Momentaufnahme für die Veröffentlichung generiert.</span><span class="sxs-lookup"><span data-stu-id="98ef2-157">A snapshot has not yet been generated for the publication.</span></span> <span data-ttu-id="98ef2-158">In diesem Fall wird für die Option der Wert **Wird automatisch beim Erstellen einer Momentaufnahme festgelegt**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="98ef2-158">In this case, the option displays a value of **Set automatically when a snapshot is created**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a><span data-ttu-id="98ef2-159">So legen Sie einen Wert für Synchronisierung optimieren fest</span><span class="sxs-lookup"><span data-stu-id="98ef2-159">To set Optimize Synchronization</span></span>  
  
1.  <span data-ttu-id="98ef2-160">Wählen Sie im Dialogfeld \*\*Veröffentlichungs Eigenschaften- \<Publication> \*\* auf der Seite **Abonnementoptionen** den Wert **wahr** für die Option **Synchronisierung optimieren** aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-160">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Optimize Synchronization** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="98ef2-161">Verwenden von Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="98ef2-161">Using Transact-SQL</span></span>  
 <span data-ttu-id="98ef2-162">Definitionen der Filteroptionen für \*\* \@ keep_partition_changes\*\* und \*\* \@ use_partition_groups\*\*finden Sie unter [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="98ef2-162">For definitions of the filtering options for **\@keep_partition_changes** and **\@use_partition_groups**, see [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a><span data-ttu-id="98ef2-163">So geben Sie die Optimierungen für Mergefilter beim Erstellen einer neuen Veröffentlichung an</span><span class="sxs-lookup"><span data-stu-id="98ef2-163">To specify merge filter optimizations when creating a new publication</span></span>  
  
1.  <span data-ttu-id="98ef2-164">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-164">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="98ef2-165">Geben Sie die \*\* \@ Veröffentlichung\*\* und `true` den Wert für einen der folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="98ef2-165">Specify **\@publication** and a value of `true` for one the following parameters:</span></span>  
  
    -   <span data-ttu-id="98ef2-166">\*\* \@ use_partition_groups\*\*: die höchste Leistungsoptimierung, vorausgesetzt, dass die Artikel den Anforderungen für Voraus berechnete Partitionen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="98ef2-166">**\@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions.</span></span> <span data-ttu-id="98ef2-167">Weitere Informationen finden Sie unter [Optimieren Parametrisierter Filter-Leistung mit Vorausberechneten Partitionen ](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-167">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="98ef2-168">\*\* \@ keep_partition_changes\*\* : Verwenden Sie diese Optimierung, wenn Voraus berechnete Partitionen nicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="98ef2-168">**\@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.</span></span>  
  
2.  <span data-ttu-id="98ef2-169">Fügen Sie einen Momentaufnahme-Auftrag für die Veröffentlichung hinzu.</span><span class="sxs-lookup"><span data-stu-id="98ef2-169">Add a snapshot job for the publication.</span></span> <span data-ttu-id="98ef2-170">Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-170">For more information see [Create a Publication](create-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="98ef2-171">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus, und geben Sie die folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="98ef2-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), specifying the following parameters:</span></span>  
  
    -   <span data-ttu-id="98ef2-172">\*\* \@ Veröffentlichung\*\* : der Name der Veröffentlichung aus Schritt 1.</span><span class="sxs-lookup"><span data-stu-id="98ef2-172">**\@publication** - the name of the publication from step 1.</span></span>  
  
    -   <span data-ttu-id="98ef2-173">\*\* \@ Artikel\*\* : ein Name für den Artikel.</span><span class="sxs-lookup"><span data-stu-id="98ef2-173">**\@article** - a name for the article</span></span>  
  
    -   <span data-ttu-id="98ef2-174">\*\* \@ source_object\*\* : das Datenbankobjekt, das veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="98ef2-174">**\@source_object** - the database object being published.</span></span>  
  
    -   <span data-ttu-id="98ef2-175">\*\* \@ subset_filterclause\*\* -die optionale parametrisierte Filter Klausel zum horizontalen Filtern des Artikels.</span><span class="sxs-lookup"><span data-stu-id="98ef2-175">**\@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.</span></span>  
  
    -   <span data-ttu-id="98ef2-176">\*\* \@ partition_options\*\* : die Partitions Optionen für den gefilterten Artikel.</span><span class="sxs-lookup"><span data-stu-id="98ef2-176">**\@partition_options** - the partition options for the filtered article.</span></span>  
  
4.  <span data-ttu-id="98ef2-177">Wiederholen Sie Schritt 3 für jeden Artikel in der Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="98ef2-177">Repeat step 3 for each article in the publication.</span></span>  
  
5.  <span data-ttu-id="98ef2-178">(Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um einen Joinfilter zwischen zwei Artikeln zu definieren.</span><span class="sxs-lookup"><span data-stu-id="98ef2-178">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="98ef2-179">Weitere Informationen finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-179">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a><span data-ttu-id="98ef2-180">So zeigen Sie das Verhalten von Mergefiltern für eine vorhandene Veröffentlichung an und ändern es</span><span class="sxs-lookup"><span data-stu-id="98ef2-180">To view and modify merge filter behaviors for an existing publication</span></span>  
  
1.  <span data-ttu-id="98ef2-181">Optionale Führen Sie auf dem Verleger für die Veröffentlichungs Datenbank [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)aus, und geben Sie die \*\* \@ Veröffentlichung\*\*an.</span><span class="sxs-lookup"><span data-stu-id="98ef2-181">(Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication**.</span></span> <span data-ttu-id="98ef2-182">Achten Sie auf den Wert von **keep_partition_changes** und **use_partition_groups** im Resultset.</span><span class="sxs-lookup"><span data-stu-id="98ef2-182">Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.</span></span>  
  
2.  <span data-ttu-id="98ef2-183">(Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-183">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="98ef2-184">Geben Sie den Wert **use_partition_groups** für die- \*\* \@ Eigenschaft\*\* und entweder `true` oder `false` für \*\* \@ value\*\*an.</span><span class="sxs-lookup"><span data-stu-id="98ef2-184">Specify a value of **use_partition_groups** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
3.  <span data-ttu-id="98ef2-185">(Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-185">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="98ef2-186">Geben Sie den Wert **keep_partition_changes** für die- \*\* \@ Eigenschaft\*\* und entweder `true` oder `false` für \*\* \@ value\*\*an.</span><span class="sxs-lookup"><span data-stu-id="98ef2-186">Specify a value of **keep_partition_changes** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98ef2-187">Wenn Sie **keep_partition_changes**aktivieren, müssen Sie zuerst **use_partition_groups** deaktivieren und den Wert **1** für \*\* \@ force_reinit_subscription\*\*angeben.</span><span class="sxs-lookup"><span data-stu-id="98ef2-187">When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
4.  <span data-ttu-id="98ef2-188">(Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="98ef2-188">(Optional) At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="98ef2-189">Geben Sie den Wert **partition_options** für die \*\* \@ Eigenschaft\*\* und den entsprechenden Wert für \*\* \@ Wert\*\*an.</span><span class="sxs-lookup"><span data-stu-id="98ef2-189">Specify a value of **partition_options** for **\@property** and the appropriate value for **\@value**.</span></span> <span data-ttu-id="98ef2-190">Informationen zur Definition dieser Filteroptionen finden Sie unter [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) .</span><span class="sxs-lookup"><span data-stu-id="98ef2-190">See [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) for definitions of these filtering options.</span></span>  
  
5.  <span data-ttu-id="98ef2-191">(Optional) Starten Sie den Momentaufnahme-Agent, um, wenn notwendig, die Momentaufnahme erneut zu generieren.</span><span class="sxs-lookup"><span data-stu-id="98ef2-191">(Optional) Start the Snapshot Agent to regenerate the snapshot if necessary.</span></span> <span data-ttu-id="98ef2-192">Informationen dazu, welche Änderungen die Generierung einer neuen Momentaufnahme erforderlich machen, finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).</span><span class="sxs-lookup"><span data-stu-id="98ef2-192">For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ef2-193">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="98ef2-193">See Also</span></span>  
 <span data-ttu-id="98ef2-194">[Automatisches Generieren einer Reihe von Joinfiltern zwischen Mergeartikeln &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="98ef2-194">[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span></span>  
 <span data-ttu-id="98ef2-195">[Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="98ef2-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 [<span data-ttu-id="98ef2-196">Parametrisierte Zeilenfilter</span><span class="sxs-lookup"><span data-stu-id="98ef2-196">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  