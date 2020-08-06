---
title: Erstellen und Verwalten von freigegebenen Datenquellen (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], shared data sources
- shared data sources [Reporting Services]
ms.assetid: 2d3428e4-a810-4e66-a287-ff18e57fad76
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5eedb74dd5a24f40469b3ee6a4a24e97e6e59174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615330"
---
# <a name="create-and-manage-shared-data-sources-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="62e51-102">Erstellen und Verwalten von freigegebenen Datenquellen (Reporting Services im integrierten SharePoint-Modus)</span><span class="sxs-lookup"><span data-stu-id="62e51-102">Create and Manage Shared Data Sources (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="62e51-103">Beim Ausführen eines Berichts aus einer SharePoint-Bibliothek können die Verbindungsinformationen innerhalb des Berichts oder in einer externen Datei definiert werden, die mit dem Bericht verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="62e51-103">When you run a report from a SharePoint library, connection information can be defined inside the report or in an external file that is linked to the report.</span></span> <span data-ttu-id="62e51-104">Falls die Verbindungsinformationen in den Bericht eingebettet sind, wird die Datenquelle als benutzerdefinierte Datenquelle bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="62e51-104">If the connection information is embedded within the report, it is called a custom data source.</span></span> <span data-ttu-id="62e51-105">Sind die Verbindungsinformationen in einer externen Datei definiert, wird sie als freigegebene Datenquelle bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="62e51-105">If the connection information is defined in an external file, it is called a shared data source.</span></span> <span data-ttu-id="62e51-106">Bei der externen Datei kann es sich um eine RSDS-Datei (Report Server Data Source, Berichtsserver-Datenquellendatei) oder um eine Office Data Connection-Datei (ODC-Datei) handeln.</span><span class="sxs-lookup"><span data-stu-id="62e51-106">The external file can be a report server data source (.rsds) file or an Office Data Connection (.odc) file.</span></span>  
  
 <span data-ttu-id="62e51-107">Eine RSDS-Datei ist mit einer RDS-Datei vergleichbar, aber sie weist ein anderes Schema auf.</span><span class="sxs-lookup"><span data-stu-id="62e51-107">An .rsds file is similar to an .rds file, but it has a different schema.</span></span> <span data-ttu-id="62e51-108">Zum Erstellen einer RSDS-Datei können Sie eine RDS-Datei aus dem Berichts-Designer oder dem Modell-Designer in einer SharePoint-Bibliothek veröffentlichen (aus der ursprünglichen RDS-Datei wird eine neue RSDS-Datei erstellt).</span><span class="sxs-lookup"><span data-stu-id="62e51-108">To create an .rsds file, you can publish an .rds from Report Designer or Model Designer to a SharePoint library (a new .rsds file is created from the original .rds file).</span></span> <span data-ttu-id="62e51-109">Alternativ können Sie eine neue Datei in einer Bibliothek auf einer SharePoint-Website erstellen.</span><span class="sxs-lookup"><span data-stu-id="62e51-109">Or, you can create a new file in a library on a SharePoint Site.</span></span>  
  
 <span data-ttu-id="62e51-110">Nachdem Sie eine freigegebene Datenquelle erstellt oder veröffentlicht haben, können Sie die Verbindungseigenschaften bearbeiten oder die Datei löschen, wenn sie nicht mehr verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="62e51-110">After you create or publish a shared data source, you can edit connection properties or delete the file if it is no longer used.</span></span> <span data-ttu-id="62e51-111">Bevor Sie eine freigegebene Datenquelle löschen, sollten Sie bestimmen, ob sie von Berichten oder Berichtsmodellen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="62e51-111">Before you delete a shared data source, you should determine whether it is used by reports and report models.</span></span> <span data-ttu-id="62e51-112">Zeigen Sie dazu abhängige Elemente an, die auf die freigegebene Datenquelle verweisen.</span><span class="sxs-lookup"><span data-stu-id="62e51-112">You can do this by viewing dependent items that reference the shared data source.</span></span>  
  
 <span data-ttu-id="62e51-113">Obwohl Sie in der Liste der abhängigen Elemente Informationen erhalten, ob auf die freigegebene Datenquelle verwiesen wird, erfahren Sie nicht, ob sie aktiv verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="62e51-113">Although the list of dependent items tells you whether the shared data source is referenced, it does not tell you whether the item is actively used.</span></span> <span data-ttu-id="62e51-114">Um zu bestimmen, ob die freigegebene Datenquelle oder das Modell aktiv verwendet wird, können Sie die Protokolldateien auf dem Berichtsservercomputer überprüfen.</span><span class="sxs-lookup"><span data-stu-id="62e51-114">To determine whether the shared data source or model is actively used, you can review the log files on the report server computer.</span></span> <span data-ttu-id="62e51-115">Wenn Sie keinen Zugriff auf die Protokolldateien haben oder wenn die Dateien die gewünschten Informationen nicht enthalten, können Sie den Bericht während der Statusbestimmung in einen Ordner verschieben, auf den kein Zugriff besteht.</span><span class="sxs-lookup"><span data-stu-id="62e51-115">If you do not have access to the log files or if the files do not contain the information you want, consider moving the report to an inaccessible folder while you determine its actual status.</span></span>  
  
### <a name="to-create-a-shared-data-source-rsds-file-sharepoint-2010"></a><span data-ttu-id="62e51-116">So erstellen Sie eine freigegebene Datenquellendatei (RSDS-Datei) in Sharepoint 2010</span><span class="sxs-lookup"><span data-stu-id="62e51-116">To create a shared data source (.rsds) file (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="62e51-117">Klicken Sie auf dem Bibliothekmenüband auf die Registerkarte **Dokumente** .</span><span class="sxs-lookup"><span data-stu-id="62e51-117">Click the **Documents** tab on the library ribbon.</span></span>  
  
2.  <span data-ttu-id="62e51-118">Klicken Sie im Menü **Neues Dokument** auf **Berichtsdatenquelle**.</span><span class="sxs-lookup"><span data-stu-id="62e51-118">On the **New Document** menu, click **Report Data Source**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62e51-119">Wenn das Element **Berichtsdatenquelle** nicht im Menü angezeigt wird, wurde der Inhaltstyp für Berichtsdatenquellen noch nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="62e51-119">If you do not see the **Report Data Source** item on the menu, the report data source content type has not been enabled.</span></span> <span data-ttu-id="62e51-120">Weitere Informationen finden Sie unter [Hinzufügen von Berichts Server-Inhaltstypen zu einer Bibliothek &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span><span class="sxs-lookup"><span data-stu-id="62e51-120">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
3.  <span data-ttu-id="62e51-121">Geben Sie unter **Name**einen beschreibenden Namen für die RSDS-Datei ein.</span><span class="sxs-lookup"><span data-stu-id="62e51-121">In **Name**, enter a descriptive name for the .rsds file.</span></span>  
  
4.  <span data-ttu-id="62e51-122">Wählen Sie unter **Datenquellentyp**den Datenquellentyp aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="62e51-122">In **Data Source Type**, select the type of data source from the list.</span></span> <span data-ttu-id="62e51-123">Weitere Informationen finden Sie unter [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="62e51-123">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
5.  <span data-ttu-id="62e51-124">Geben Sie unter **Connection String**einen Zeiger auf die Datenquelle und alle anderen Einstellungen an, die zum Herstellen einer Verbindung mit der externen Datenquelle erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="62e51-124">In **Connection String**, specify a pointer to the data source and any other settings that are necessary for establishing a connection to the external data source.</span></span> <span data-ttu-id="62e51-125">Die Syntax der Verbindungszeichenfolge wird durch den von Ihnen verwendeten Datenquellentyp bestimmt.</span><span class="sxs-lookup"><span data-stu-id="62e51-125">The type of data source you are using determines the syntax of the connection string.</span></span> <span data-ttu-id="62e51-126">Weitere Informationen und Beispiele finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="62e51-126">For more information and examples, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
6.  <span data-ttu-id="62e51-127">Geben Sie in **Anmeldeinformationen**an, wie der Berichtsserver Anmeldeinformationen für den Zugriff auf die externe Datenquelle erhält.</span><span class="sxs-lookup"><span data-stu-id="62e51-127">In **Credentials**, specify how the report server obtains credentials to access the external data source.</span></span> <span data-ttu-id="62e51-128">Anmeldeinformationen können für die unbeaufsichtigte Berichtsverarbeitung gespeichert, angefordert, integriert oder konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="62e51-128">Credentials can be stored, prompted, integrated, or configured for unattended report processing.</span></span>  
  
    -   <span data-ttu-id="62e51-129">Wählen Sie **Windows-Authentifizierung (integriert)** aus, wenn der Zugriff auf die Daten mit den Anmeldeinformationen des Benutzers erfolgen soll, der den Bericht geöffnet hat.</span><span class="sxs-lookup"><span data-stu-id="62e51-129">Select **Windows authentication (integrated)** if you want to access the data using the credentials of the user who opened the report.</span></span> <span data-ttu-id="62e51-130">Wählen Sie diese Option nicht aus, wenn für die SharePoint-Website oder -Farm die Formularauthentifizierung verwendet oder über ein vertrauenswürdiges Konto eine Verbindung mit dem Berichtsserver hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="62e51-130">Do not select this option if the SharePoint site or farm uses forms authentication or connects to the report server through a trusted account.</span></span> <span data-ttu-id="62e51-131">Wählen Sie diese Option nicht aus, wenn Sie eine Abonnement- oder Datenverarbeitung für diesen Bericht planen möchten.</span><span class="sxs-lookup"><span data-stu-id="62e51-131">Do not select this option if you want to schedule subscription or data processing for this report.</span></span> <span data-ttu-id="62e51-132">Diese Option kann am besten verwendet werden, wenn die Kerberos-Authentifizierung für die Domäne aktiviert ist oder wenn sich die Datenquelle auf demselben Computer wie der Berichtsserver befindet.</span><span class="sxs-lookup"><span data-stu-id="62e51-132">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="62e51-133">Wenn die Kerberos-Authentifizierung nicht aktiviert ist, können die Windows-Anmeldeinformationen nur an einen anderen Computer weitergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="62e51-133">If Kerberos authentication is not enabled, Windows credentials can only be passed to one other computer.</span></span> <span data-ttu-id="62e51-134">Dies bedeutet, dass statt der erwarteten Daten ein Fehler angezeigt wird, wenn sich die externe Datenquelle auf einem anderen Computer befindet, für den eine zusätzliche Verbindung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="62e51-134">This means that if the external data source is on another computer, requiring an additional connection, you will get an error instead of the data you expect.</span></span>  
  
    -   <span data-ttu-id="62e51-135">Wählen Sie **Zur Eingabe der Anmeldeinformationen auffordern** aus, wenn der Benutzer die Anmeldeinformationen bei jeder Ausführung des Berichts eingeben soll.</span><span class="sxs-lookup"><span data-stu-id="62e51-135">Select **Prompt for credentials** if you want the user to enter his or her credentials each time he or she runs the report.</span></span> <span data-ttu-id="62e51-136">Wählen Sie diese Option nicht aus, wenn Sie eine Abonnement- oder Datenverarbeitung für diesen Bericht planen möchten.</span><span class="sxs-lookup"><span data-stu-id="62e51-136">Do not select this option if you want to schedule subscription or data processing for this report.</span></span>  
  
    -   <span data-ttu-id="62e51-137">Wählen Sie **Gespeicherte Anmeldeinformationen** aus, wenn der Zugriff auf die Daten mit einem einzigen Satz Anmeldeinformationen erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="62e51-137">Select **Stored credentials** if you want to access the data using a single set of credentials.</span></span> <span data-ttu-id="62e51-138">Die Anmeldeinformationen werden vor der Speicherung verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="62e51-138">The credentials are encrypted before they are stored.</span></span> <span data-ttu-id="62e51-139">Sie können Optionen auswählen, die bestimmen, wie die gespeicherten Anmeldeinformationen authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="62e51-139">You can select options that determine how the stored credentials are authenticated.</span></span> <span data-ttu-id="62e51-140">Wählen Sie Windows-Anmeldeinformationen verwenden aus, wenn die gespeicherten Anmeldeinformationen zu einem Windows-Benutzerkonto gehören.</span><span class="sxs-lookup"><span data-stu-id="62e51-140">Select Use as Windows credentials if the stored credentials belong to a Windows user account.</span></span> <span data-ttu-id="62e51-141">Wählen Sie **Ausführungskontext für dieses Konto festlegen** aus, wenn Sie den Ausführungskontext auf dem Datenbankserver festlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="62e51-141">Select **Set execution context to this account** if you want to set the execution context on the database server.</span></span> <span data-ttu-id="62e51-142">Bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbanken kann mit dieser Option die SETUSER-Funktion festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="62e51-142">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases, this option sets the SETUSER function.</span></span> <span data-ttu-id="62e51-143">Weitere Informationen finden Sie unter [SETUSER (Transact-SQL)](/sql/t-sql/statements/setuser-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="62e51-143">For more information, see [SETUSER &#40;Transact-SQL&#41;](/sql/t-sql/statements/setuser-transact-sql).</span></span>  
  
    -   <span data-ttu-id="62e51-144">Wählen Sie **Anmeldeinformationen sind nicht erforderlich** aus, wenn Sie Anmeldeinformationen in der Verbindungszeichenfolge angeben möchten oder wenn Sie den Bericht mithilfe eines Kontos mit Minimalprivilegien ausführen möchten, das auf dem Berichtsserver konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="62e51-144">Select **Credentials are not required** if you want to specify credentials in the connection string, or if you want to run the report using a least-privilege account that is configured on the report server.</span></span> <span data-ttu-id="62e51-145">Ist das Konto nicht auf dem Berichtsserver konfiguriert, werden die Anmeldeinformationen von den Benutzern angefordert, und geplante Vorgänge, die Sie für den Bericht definieren, werden nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="62e51-145">If this account is not configured on the report server, users will be prompted for credentials and any scheduled operations that you define for the report will not run.</span></span>  
  
7.  <span data-ttu-id="62e51-146">Wählen Sie **Diese Datenquelle aktivieren** aus, wenn die Datenquelle aktiviert sein soll.</span><span class="sxs-lookup"><span data-stu-id="62e51-146">Select **Enable this data source** if you want the data source to be active.</span></span> <span data-ttu-id="62e51-147">Wenn die Datenquelle konfiguriert aber nicht aktiv ist, wird Benutzern beim Versuch, einen Bericht auf Grundlage der Datenquelle zu verwenden, eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="62e51-147">If the data source is configured but not active, users will see an error message when they attempt to use a report based on the data source.</span></span>  
  
8.  <span data-ttu-id="62e51-148">Klicken Sie auf die Schaltfläche **Verbindung testen** , um die Datenquellenkonfiguration zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="62e51-148">Click the **Test Connection** button to validate the data source configuration.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="62e51-149">Die Schaltfläche zum Testen der Verbindung wird für den XML-Datenquellentyp nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="62e51-149">The Test Connection button is not supported for the XML data source type.</span></span>  
  
9. <span data-ttu-id="62e51-150">Klicken Sie auf **OK** , um die freigegebene Datenquelle zu speichern.</span><span class="sxs-lookup"><span data-stu-id="62e51-150">Click **OK** to save create the shared data source.</span></span>  
  
### <a name="to-view-dependent-items"></a><span data-ttu-id="62e51-151">So zeigen Sie abhängige Elemente an</span><span class="sxs-lookup"><span data-stu-id="62e51-151">To view dependent items</span></span>  
  
1.  <span data-ttu-id="62e51-152">Öffnen Sie die Bibliothek, die die RSDS-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="62e51-152">Open the library that contains the .rsds file.</span></span>  
  
2.  <span data-ttu-id="62e51-153">Zeigen Sie auf die freigegebene Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="62e51-153">Point to the shared data source.</span></span>  
  
3.  <span data-ttu-id="62e51-154">Klicken Sie, um einen Pfeil nach unten anzuzeigen, und wählen Sie **Abhängige Elemente anzeigen**aus.</span><span class="sxs-lookup"><span data-stu-id="62e51-154">Click to display a down arrow, and select **View Dependent Items**.</span></span>  
  
     <span data-ttu-id="62e51-155">Für Berichtsmodelle enthält die Liste der abhängigen Elemente die Berichte, die im Berichts-Generator erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="62e51-155">For report models, the list of dependent items shows the reports that were created in Report Builder.</span></span> <span data-ttu-id="62e51-156">Bei freigegebenen Datenquellen kann die Liste der abhängigen Elemente sowohl Berichte als auch Berichtsmodelle enthalten.</span><span class="sxs-lookup"><span data-stu-id="62e51-156">For shared data sources, the dependent items list can include both reports and report models.</span></span>  
  
### <a name="to-delete-a-shared-data-source-rsds-file"></a><span data-ttu-id="62e51-157">So löschen Sie eine freigegebene Datenquellendatei (RSDS-Datei)</span><span class="sxs-lookup"><span data-stu-id="62e51-157">To delete a shared data source (.rsds) file</span></span>  
  
1.  <span data-ttu-id="62e51-158">Öffnen Sie die Bibliothek, die die RSDS-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="62e51-158">Open the library that contains the .rsds file.</span></span>  
  
2.  <span data-ttu-id="62e51-159">Zeigen Sie auf die freigegebene Datenquelle.</span><span class="sxs-lookup"><span data-stu-id="62e51-159">Point to the shared data source.</span></span>  
  
3.  <span data-ttu-id="62e51-160">Klicken Sie, um einen Pfeil nach unten anzuzeigen, und klicken Sie auf **Löschen**.</span><span class="sxs-lookup"><span data-stu-id="62e51-160">Click to display a down arrow, and click **Delete**.</span></span>  
  
 <span data-ttu-id="62e51-161">Wenn Sie versehentlich eine freigegebene Datenquelle löschen, die beibehalten werden sollte, können Sie eine neue Datenquelle mit denselben Verbindungsinformationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="62e51-161">If you mistakenly delete a shared data source that you meant to keep, you can create a new one that contains the same connection information.</span></span> <span data-ttu-id="62e51-162">Nachdem Sie die freigegebene Datenquelle erneut erstellt haben, müssen Sie jeden Bericht und jedes Berichtsmodell, von dem diese Datenquelle verwendet wurde, öffnen und die freigegebene Datenquelle auswählen.</span><span class="sxs-lookup"><span data-stu-id="62e51-162">After you recreate the shared data source, you must open each report and model that used that data source and select the shared data source.</span></span> <span data-ttu-id="62e51-163">Der Name, die Anmeldeinformationen und die Syntax der Verbindungszeichenfolge des neuen freigegebenen Datenquellenelements müssen nicht mit denen des gelöschten übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="62e51-163">The new shared data source item can have a different name, credentials, or connection string syntax from the one you delete.</span></span> <span data-ttu-id="62e51-164">Solange die Verbindung zur selben Datenquelle aufgelöst wird, können Datenquelleneigenschaften von den ursprünglichen Werten abweichen.</span><span class="sxs-lookup"><span data-stu-id="62e51-164">As long as the connection resolves to the same data source, data source properties can vary from the original values.</span></span>  
  
 <span data-ttu-id="62e51-165">Gehen Sie beim Löschen eines Berichtsmodells umsichtig vor.</span><span class="sxs-lookup"><span data-stu-id="62e51-165">Use caution when deleting a report model.</span></span> <span data-ttu-id="62e51-166">Wenn Sie ein Modell löschen, können Sie die Berichte, die auf diesem Modell im Berichts-Generator basieren, nicht mehr öffnen und ändern.</span><span class="sxs-lookup"><span data-stu-id="62e51-166">If you delete a model, you can no longer open and modify any reports that are based on that model in Report Builder.</span></span> <span data-ttu-id="62e51-167">Wenn Sie versehentlich ein Modell löschen, das von vorhandenen Berichten verwendet wird, müssen Sie das Modell erneut generieren, alle Berichte, von denen das Modell verwendet wird, erneut erstellen und speichern und die zu verwendende Modellelementsicherheit erneut angeben.</span><span class="sxs-lookup"><span data-stu-id="62e51-167">If you inadvertently delete a model that is used by existing reports, you must regenerate the model, re-create and save any reports that use the model, and re-specify any model item security that you want to use.</span></span> <span data-ttu-id="62e51-168">Es ist nicht möglich, das Modell einfach neu zu generieren und es anschließend einem vorhandenen Bericht anzufügen.</span><span class="sxs-lookup"><span data-stu-id="62e51-168">You cannot simply regenerate the model and then attach it to an existing report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e51-169">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="62e51-169">See Also</span></span>  
 [<span data-ttu-id="62e51-170">Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen</span><span class="sxs-lookup"><span data-stu-id="62e51-170">Specify Credential and Connection Information for Report Data Sources</span></span>](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  