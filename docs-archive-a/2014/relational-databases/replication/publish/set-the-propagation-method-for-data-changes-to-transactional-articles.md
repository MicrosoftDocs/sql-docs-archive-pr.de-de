---
title: Festlegen der Propagierungsmethode für Datenänderungen an Transaktionsartikeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
- propagating data changes [SQL Server replication]
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3f8be8b6df1034b06d0aaff6ee61c0c494833c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717848"
---
# <a name="set-the-propagation-method-for-data-changes-to-transactional-articles"></a><span data-ttu-id="c7688-102">Festlegen der Propagierungsmethode für Datenänderungen an Transaktionsartikeln</span><span class="sxs-lookup"><span data-stu-id="c7688-102">Set the Propagation Method for Data Changes to Transactional Articles</span></span>
  <span data-ttu-id="c7688-103">In diesem Thema wird beschrieben, wie die Propagierungsmethode für Datenänderungen an Transaktionsartikeln in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="c7688-103">This topic describes how to set the propagation method for data changes to transactional articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c7688-104">Standardmäßig werden bei der Transaktionsreplikation an Abonnenten vorgenommene Änderungen mithilfe eines Satzes gespeicherter Prozeduren für den jeweiligen Artikel weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="c7688-104">By default, transactional replication propagates changes to Subscribers using a set of stored procedures for each article.</span></span> <span data-ttu-id="c7688-105">Sie können diese Prozeduren durch benutzerdefinierte Prozeduren ersetzen.</span><span class="sxs-lookup"><span data-stu-id="c7688-105">You can replace these procedures with custom procedures.</span></span> <span data-ttu-id="c7688-106">Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
 <span data-ttu-id="c7688-107">**In diesem Thema**</span><span class="sxs-lookup"><span data-stu-id="c7688-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c7688-108">**Vorbereitungen:**</span><span class="sxs-lookup"><span data-stu-id="c7688-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c7688-109">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="c7688-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="c7688-110">**So legen Sie die Propagierungsmethode für Datenänderungen an Transaktionsartikeln fest**</span><span class="sxs-lookup"><span data-stu-id="c7688-110">**To set the propagation method for data changes to transactional articles, using:**</span></span>  
  
     [<span data-ttu-id="c7688-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7688-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c7688-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c7688-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
## <a name="before-you-begin"></a><span data-ttu-id="c7688-113">Vorbereitungen</span><span class="sxs-lookup"><span data-stu-id="c7688-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c7688-114">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="c7688-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c7688-115">Gehen Sie bei der Bearbeitung der bei der Replikation generierten Momentaufnahmedateien mit Bedacht vor.</span><span class="sxs-lookup"><span data-stu-id="c7688-115">Care must be taken when editing any of the snapshot files generated by replication.</span></span> <span data-ttu-id="c7688-116">Sie müssen die benutzerdefinierte Logik in den benutzerdefinierten gespeicherten Prozeduren testen und unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c7688-116">You must test and support custom logic in the custom stored procedures.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c7688-117">bietet keine Unterstützung für benutzerdefinierte Logik.</span><span class="sxs-lookup"><span data-stu-id="c7688-117">does not provide support for custom logic.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c7688-118">Verwenden von SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c7688-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c7688-119">Geben Sie die Propagierungsmethode im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** an. Diese Registerkarte steht sowohl im Assistenten für neue Veröffentlichungen als auch im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c7688-119">Specify the propagation method on the **Properties** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="c7688-120">Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-120">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-the-propagation-method"></a><span data-ttu-id="c7688-121">So geben Sie die Propagierungsmethode an</span><span class="sxs-lookup"><span data-stu-id="c7688-121">To specify the propagation method</span></span>  
  
1.  <span data-ttu-id="c7688-122">Wählen Sie im Assistenten für neue Veröffentlichungen auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="c7688-122">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="c7688-123">Klicken Sie auf die Option **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen**.</span><span class="sxs-lookup"><span data-stu-id="c7688-123">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="c7688-124">Geben Sie im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** im Abschnitt **Anweisungsübermittlung** die Propagierungsmethode für die einzelnen Vorgänge an. Verwenden Sie hierzu die Menüs **INSERT-Übermittlungsformat**, **UPDATE-Übermittlungsformat** und **DELETE-Übermittlungsformat**.</span><span class="sxs-lookup"><span data-stu-id="c7688-124">On the **Properties** tab of the **Article Properties - \<Article>** dialog box, in the **Statement Delivery** section, specify the propagation method for each operation using the **INSERT delivery format**, **UPDATE delivery format**, and **DELETE delivery format** menus.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="c7688-125">Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c7688-125">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-generate-and-use-custom-stored-procedures"></a><span data-ttu-id="c7688-126">So generieren und verwenden Sie benutzerdefinierte Prozeduren</span><span class="sxs-lookup"><span data-stu-id="c7688-126">To generate and use custom stored procedures</span></span>  
  
1.  <span data-ttu-id="c7688-127">Wählen Sie im Assistenten für neue Veröffentlichungen auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="c7688-127">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="c7688-128">Klicken Sie auf die Option **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen**.</span><span class="sxs-lookup"><span data-stu-id="c7688-128">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
     <span data-ttu-id="c7688-129">Wählen Sie im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** im Abschnitt **Anweisungsübermittlung** die CALL-Syntax im Menü des entsprechenden Übermittlungsformats (**INSERT-Übermittlungsformat**, **UPDATE-Übermittlungsformat** oder **DELETE-Übermittlungsformat**) aus, und geben Sie dann den Namen der Prozedur ein, die in **gespeicherter Prozedur INSERT**, in **gespeicherter Prozedur DELETE** oder **in gespeicherter Prozedur UPDATE** verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c7688-129">On the **Properties** tab of the **Article Properties - \<Article>** dialog box, in the **Statement Delivery** section, select the CALL syntax from the appropriate delivery format menu (**INSERT delivery format**, **UPDATE delivery format**, or **DELETE delivery format**), and then type the name of the procedure to use in **INSERT stored procedure**, **DELETE stored procedure**, or **UPDATE stored procedure**.</span></span> <span data-ttu-id="c7688-130">Weitere Informationen zur CALL-Syntax finden Sie im Abschnitt „Aufrufsyntax für gespeicherte Prozeduren“ in [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-130">For more information about CALL syntax, see the section "Call syntax for stored procedures" in [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="c7688-131">Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c7688-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
5.  <span data-ttu-id="c7688-132">Wenn die Momentaufnahme für die Veröffentlichung generiert wird, enthält er die Prozedur, die Sie im vorherigen Schritt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="c7688-132">When the snapshot for the publication is generated, it will include the procedure you specified in the previous step.</span></span> <span data-ttu-id="c7688-133">Von den Prozeduren wird die von Ihnen angegebene CALL-Syntax verwendet, die bei der Replikation verwendete Standardlogik ist jedoch enthalten.</span><span class="sxs-lookup"><span data-stu-id="c7688-133">The procedures will use the CALL syntax you specified, but will include the default logic that replication uses.</span></span>  
  
     <span data-ttu-id="c7688-134">Navigieren Sie nach der Momentaufnahmegenerierung zu dem Momentaufnahmeordner der Veröffentlichung, zu der dieser Artikel gehört, und suchen Sie die **.sch** -Datei, die denselben Namen wie der Artikel trägt.</span><span class="sxs-lookup"><span data-stu-id="c7688-134">After the snapshot has been generated, navigate to the snapshot folder for the publication to which this article belongs and locate the **.sch** file with the same name as the article.</span></span> <span data-ttu-id="c7688-135">Öffnen Sie diese Datei im Editor oder einem anderen Text-Editor, suchen Sie den CREATE PROCEDURE-Befehl für die gespeicherte Prozedur INSERT, UPDATE oder DELETE, und bearbeiten Sie die Prozedurdefinition, um jegliche benutzerdefinierte Logik für das Propagieren von Datenänderungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c7688-135">Open this file using Notepad or another text editor, locate the CREATE PROCEDURE command for the insert, update, or delete stored procedures, and edit the procedure definition to supply any custom logic for propagating data changes.</span></span> <span data-ttu-id="c7688-136">Wenn die Momentaufnahme erneut generiert wird, muss die benutzerdefinierte Prozedur ebenfalls erneut erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="c7688-136">If the snapshot is regenerated, you must re-create the custom procedure.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c7688-137">Verwenden von Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c7688-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="c7688-138">Die Transaktionsreplikation ermöglicht es Ihnen zu steuern, wie Änderungen vom Verleger an die Abonnenten weitergegeben (propagiert) werden. Diese Propagierungsmethode kann bei der Erstellung eines Artikels programmgesteuert festgelegt und später anhand gespeicherter Replikationsprozeduren geändert werden.</span><span class="sxs-lookup"><span data-stu-id="c7688-138">Transactional replication enables you to control how changes are propagated from the Publisher to Subscribers, and this propagation method can be set programmatically when an article is created and changed later using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7688-139">Sie können für jeden DML-Vorgangstyp (Data Manipulation Language, Datenbearbeitungssprache), der auf einer Zeile veröffentlichter Daten vorkommt (Einfügen, Aktualisieren oder Löschen), eine andere Propagierungsmethode angeben.</span><span class="sxs-lookup"><span data-stu-id="c7688-139">You can specify a different propagation method for each type of DML (data manipulation language) operation (insert, update, or delete) that occurs on a row of a published data.</span></span>  
  
 <span data-ttu-id="c7688-140">Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-140">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-create-an-article-that-uses-transact-sql-commands-to-propagate-data-changes"></a><span data-ttu-id="c7688-141">So erstellen Sie einen Artikel, der Transact-SQL-Befehle verwendet, um Datenänderungen weiterzugeben</span><span class="sxs-lookup"><span data-stu-id="c7688-141">To create an article that uses Transact-SQL commands to propagate data changes</span></span>  
  
1.  <span data-ttu-id="c7688-142">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="c7688-142">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="c7688-143">Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das Datenbankobjekt, das veröffentlicht wird, für **\@source_object** und den Wert **SQL** für mindestens einen der folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="c7688-143">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and a value of **SQL** for at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="c7688-144">**\@ins_cmd**: Steuert die Replikation von [INSERT](/sql/t-sql/statements/insert-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-144">**\@ins_cmd** - controls the replication of [INSERT](/sql/t-sql/statements/insert-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="c7688-145">**\@upd_cmd**: Steuert die Replikation von [UPDATE](/sql/t-sql/queries/update-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-145">**\@upd_cmd** - controls the replication of [UPDATE](/sql/t-sql/queries/update-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="c7688-146">**\@del_cmd**: Steuert die Replikation von [DELETE](/sql/t-sql/statements/delete-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-146">**\@del_cmd** - controls the replication of [DELETE](/sql/t-sql/statements/delete-transact-sql) commands.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-147">Wenn Sie den Wert **SQL** für einen der obigen Parameter angeben, werden die Befehle des betreffenden Typs auf den Abonnenten als entsprechende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Befehle repliziert.</span><span class="sxs-lookup"><span data-stu-id="c7688-147">When specifying a value of **SQL** for any of the above parameters, commands of that type will be replicated to the Subscriber as the appropriate [!INCLUDE[tsql](../../../includes/tsql-md.md)] command.</span></span>  
  
     <span data-ttu-id="c7688-148">Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-148">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-create-an-article-that-does-not-propagate-data-changes"></a><span data-ttu-id="c7688-149">So erstellen Sie einen Artikel, der keine Datenänderungen weitergibt</span><span class="sxs-lookup"><span data-stu-id="c7688-149">To create an article that does not propagate data changes</span></span>  
  
1.  <span data-ttu-id="c7688-150">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="c7688-150">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="c7688-151">Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das Datenbankobjekt, das veröffentlicht wird, für **\@source_object** und den Wert **NONE** für mindestens einen der folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="c7688-151">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and a value of **NONE** for at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="c7688-152">**\@ins_cmd**: Steuert die Replikation von [INSERT](/sql/t-sql/statements/insert-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-152">**\@ins_cmd** - controls the replication of [INSERT](/sql/t-sql/statements/insert-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="c7688-153">**\@upd_cmd**: Steuert die Replikation von [UPDATE](/sql/t-sql/queries/update-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-153">**\@upd_cmd** - controls the replication of [UPDATE](/sql/t-sql/queries/update-transact-sql) commands.</span></span>  
  
    -   <span data-ttu-id="c7688-154">**\@del_cmd**: Steuert die Replikation von [DELETE](/sql/t-sql/statements/delete-transact-sql)-Befehlen.</span><span class="sxs-lookup"><span data-stu-id="c7688-154">**\@del_cmd** - controls the replication of [DELETE](/sql/t-sql/statements/delete-transact-sql) commands.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-155">Wenn Sie den Wert **NONE** für einen der obigen Parameter angeben, werden die Befehle des betreffenden Typs auf den Abonnenten nicht repliziert.</span><span class="sxs-lookup"><span data-stu-id="c7688-155">When specifying a value of **NONE** for any of the above parameters, commands of that type will not be replicated to the Subscriber.</span></span>  
  
     <span data-ttu-id="c7688-156">Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-156">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-create-an-article-with-user-modified-custom-stored-procedures"></a><span data-ttu-id="c7688-157">So erstellen Sie einen Artikel mit benutzerdefinierten gespeicherten Prozeduren</span><span class="sxs-lookup"><span data-stu-id="c7688-157">To create an article with user-modified custom stored procedures</span></span>  
  
1.  <span data-ttu-id="c7688-158">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="c7688-158">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="c7688-159">Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das zu veröffentlichende Datenbankobjekt für **\@source_object**, einen Wert für die **\@schema_option**-Bitmaske, der den Wert **0x02** enthält (aktiviert die automatische Erstellung benutzerdefinierter gespeicherter Prozeduren), und mindestens einen der folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="c7688-159">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, a value for the **\@schema_option** bitmask that contains the value **0x02** (enables automatic generation of custom stored procedures), and at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="c7688-160">\*\* \@ ins_cmd\*\* geben Sie den Wert " <strong>callsp_MSins_*article_name*</strong>" an, wobei **_article_name_** der für den \*\* \@ Artikel\*\*angegebene Wert ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-160">**\@ins_cmd** - specify a value of <strong>CALL sp_MSins_*article_name*</strong>, where **_article_name_** is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="c7688-161">\*\* \@ del_cmd\*\* : Geben Sie den Wert " <strong>callsp_MSdel_*article_name* </strong> " oder " <strong>xcallsp_MSdel_*article_name*</strong>" an, wobei **_article_name_** der Wert ist, der für _ \* \@ article \* \* angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-161">**\@del_cmd** - specify a value of <strong>CALL sp_MSdel_*article_name*</strong> or <strong>XCALL sp_MSdel_*article_name*</strong>, where **_article_name_** is the value specified for _\*\@article\*\*.</span></span>  
  
    -   <span data-ttu-id="c7688-162">\*\* \@ upd_cmd\*\* : Geben Sie den Wert <strong>SCALL sp_Msupd_*article_name*</strong>, den Befehl <strong>sp_Msupd_*article_name*</strong>, <strong>xcallsp_MSupd__article_name *</strong> oder <strong>mcallsp_MSupd_* article_name \*</strong>an, wobei _**article_name**_ der Wert ist, der für den \*\* \@ Artikel\*\*angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-162">**\@upd_cmd** - specify a value of <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd__article_name*</strong>, or <strong>MCALL sp_MSupd_* article_name\*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-163">Für jeden der obigen Befehlsparameter gilt: Sie können einen selbst gewählten Namen für die gespeicherten Prozeduren angeben, die von der Replikation generiert werden.</span><span class="sxs-lookup"><span data-stu-id="c7688-163">For each of the above command parameters, you can specify your own name for the stored procedures that replication generates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-164">Weitere Informationen über die CALL, SCALL, XCALL und MCALL-Syntax finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-164">For more information on CALL, SCALL, XCALL, and MCALL syntax, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
     <span data-ttu-id="c7688-165">Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="c7688-166">Navigieren Sie nach der Momentaufnahmegenerierung zu dem Momentaufnahmeordner der Veröffentlichung, zu der dieser Artikel gehört, und suchen Sie die **.sch** -Datei, die denselben Namen wie der Artikel trägt.</span><span class="sxs-lookup"><span data-stu-id="c7688-166">After the snapshot has been generated, navigate to the snapshot folder for the publication to which this article belongs and locate the **.sch** file with the same name as the article.</span></span> <span data-ttu-id="c7688-167">Öffnen Sie diese Datei mit Notepad.exe, suchen Sie den CREATE PROCEDURE-Befehl für die gespeicherte Prozedur INSERT, UPDATE oder DELETE, und bearbeiten Sie die Prozedurdefinition, um eine benutzerdefinierte Logik für die Propagierung von Datenänderungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c7688-167">Open this file using Notepad.exe, locate the CREATE PROCEDURE command for the insert, update, or delete stored procedures, and edit the procedure definition to supply any custom logic for propagating data changes.</span></span> <span data-ttu-id="c7688-168">Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-168">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-create-an-article-with-custom-scripting-in-the-custom-stored-procedures-to-propagate-data-changes"></a><span data-ttu-id="c7688-169">So erstellen Sie einen Artikel mit benutzerdefinierter Skriptprozedur in den benutzerdefinierten gespeicherten Prozeduren, um Datenänderungen weiterzugeben</span><span class="sxs-lookup"><span data-stu-id="c7688-169">To create an article with custom scripting in the custom stored procedures to propagate data changes</span></span>  
  
1.  <span data-ttu-id="c7688-170">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="c7688-170">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="c7688-171">Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das zu veröffentlichende Datenbankobjekt für **\@source_object**, einen Wert für die **\@schema_option**-Bitmaske, der den Wert **0x02** enthält (aktiviert die automatische Erstellung benutzerdefinierter gespeicherter Prozeduren), und mindestens einen der folgenden Parameter an:</span><span class="sxs-lookup"><span data-stu-id="c7688-171">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, a value for the **\@schema_option** bitmask that contains the value **0x02** (enables automatic generation of custom stored procedures), and at least one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="c7688-172">\*\* \@ ins_cmd\*\* geben Sie den Wert " <strong>callsp_MSins_*article_name*</strong>" an, wobei _**article_name**_ der für den \*\* \@ Artikel\*\*angegebene Wert ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-172">**\@ins_cmd** - specify a value of <strong>CALL sp_MSins_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="c7688-173">\*\* \@ del_cmd\*\* : Geben Sie den Wert " <strong>callsp_MSdel_*article_name* </strong> " oder " <strong>xcallsp_MSdel_*article_name*</strong>" an, wobei _**article_name**_ der für den \*\* \@ Artikel\*\*angegebene Wert ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-173">**\@del_cmd** - specify a value of <strong>CALL sp_MSdel_*article_name*</strong> or <strong>XCALL sp_MSdel_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    -   <span data-ttu-id="c7688-174">\*\* \@ upd_cmd\*\* : Geben Sie den Wert <strong>SCALL sp_Msupd_*article_name*</strong>an, und <strong>sp_Msupd_*article_name*</strong>, <strong>xcallsp_MSupd_*article_name*</strong>article_name, <strong>mcallsp_MSupd_*article_name article_name*</strong>, wobei _**article_name**_ der Wert ist, der für den \*\* \@ Artikel\*\*angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="c7688-174">**\@upd_cmd** - specify a value of <strong>SCALL sp_MSupd_*article_name*</strong>, <strong>CALL sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd_*article_name*</strong>, <strong>MCALL sp_MSupd_*article_name*</strong>, where _**article_name**_ is the value specified for **\@article**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-175">Für jeden der obigen Befehlsparameter gilt: Sie können einen selbst gewählten Namen für die gespeicherten Prozeduren angeben, die von der Replikation generiert werden.</span><span class="sxs-lookup"><span data-stu-id="c7688-175">For each of the above command parameters, you can specify your own name for the stored procedures that replication generates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7688-176">Weitere Informationen über die CALL, SCALL, XCALL und MCALL-Syntax finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-176">For more information on CALL, SCALL, XCALL, and MCALL syntax, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
     <span data-ttu-id="c7688-177">Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-177">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="c7688-178">Verwenden Sie auf dem Verleger für die Veröffentlichungsdatenbank die [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) -Anweisung, um [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) so zu bearbeiten, dass ein [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) -Skript für die benutzerdefinierten, gespeicherten Prozeduren INSERT, UPDATE und DELETE zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c7688-178">At the Publisher on the publication database, use the [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) statement to edit [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) so that it returns a [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) script for the insert, update, and delete custom stored procedures.</span></span> <span data-ttu-id="c7688-179">Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span><span class="sxs-lookup"><span data-stu-id="c7688-179">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
#### <a name="to-change-the-method-of-propagating-changes-for-an-existing-article"></a><span data-ttu-id="c7688-180">So ändern Sie die Methode zur Weitergabe von Änderungen an einen vorhandenen Artikel</span><span class="sxs-lookup"><span data-stu-id="c7688-180">To change the method of propagating changes for an existing article</span></span>  
  
1.  <span data-ttu-id="c7688-181">Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)aus.</span><span class="sxs-lookup"><span data-stu-id="c7688-181">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="c7688-182">Geben Sie **\@publication**, **\@article**, den Wert **ins_cmd**, **upd_cmd** oder **del_cmd** für **\@property** und die entsprechende Propagierungsmethode für **\@value** an.</span><span class="sxs-lookup"><span data-stu-id="c7688-182">Specify **\@publication**, **\@article**, a value of **ins_cmd**, **upd_cmd**, or **del_cmd** for **\@property**, and the appropriate propagation method for **\@value**.</span></span>  
  
2.  <span data-ttu-id="c7688-183">Wiederholen Sie Schritt 1 für jede Propagierungsmethode, die geändert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c7688-183">Repeat step 1 for each propagation method to be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7688-184">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c7688-184">See Also</span></span>  
 <span data-ttu-id="c7688-185">[Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md) </span><span class="sxs-lookup"><span data-stu-id="c7688-185">[Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md) </span></span>  
 [<span data-ttu-id="c7688-186">Erstellen einer Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="c7688-186">Create a publication</span></span>](create-a-publication.md)  
  
  