---
title: Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10054250-d915-4bcb-8a1d-26837db4e932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8dbd4243320dd8d36dafc27ea910755fd3e70a83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615334"
---
# <a name="print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs"></a><span data-ttu-id="bec3b-102">Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS)</span><span class="sxs-lookup"><span data-stu-id="bec3b-102">Print Reports from a Browser with the Print Control (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bec3b-103">Ein Browser ist zwar die am häufigsten verwendete Clientanwendung zum Anzeigen von Berichten, die Druckfunktionen des Browsers sind jedoch für das Drucken von Berichten nicht ideal.</span><span class="sxs-lookup"><span data-stu-id="bec3b-103">Although a browser is the most common client application used to view a report, browser print functionality is not ideal for printing reports.</span></span> <span data-ttu-id="bec3b-104">Die Druckfunktionen eines Browsers sind zum Drucken von Webseiten konzipiert.</span><span class="sxs-lookup"><span data-stu-id="bec3b-104">Print functionality in a browser is designed for printing Web pages.</span></span> <span data-ttu-id="bec3b-105">In der Regel enthalten die von einem Browser gedruckten Seiten alle visuellen Elemente einer Webseite, dazu Kopf- und Fußzeileninformationen zur Identifikation der Seite oder Website.</span><span class="sxs-lookup"><span data-stu-id="bec3b-105">Typically, pages that you print from a browser include all of the visual elements that are on a Web page, plus header and footer information that identifies the page or Web site.</span></span> <span data-ttu-id="bec3b-106">Beim Drucken über einen Browser wird der Inhalt des aktuellen Fensters gedruckt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-106">Printing from a browser prints the contents of the current window.</span></span> <span data-ttu-id="bec3b-107">Bei mehrseitigen Berichten wird maximal die erste Seite gedruckt, möglicherweise sogar weniger, wenn die Berichtsseite die Dimensionen der gedruckten Seite übersteigt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-107">For a multipage report, the browser prints the first page at most, and possibly less if the report page extends beyond the dimensions of a printed page.</span></span>  
  
 <span data-ttu-id="bec3b-108">Wenn Sie die Druckqualität von Berichten verbessern möchten, die Sie in einem Browser anzeigen und mehrere Seiten drucken möchten, können Sie die Client seitige Druck Funktionalität verwenden, die in bereitgestellt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bec3b-108">To improve the print quality of reports that you view in a browser and to print multiple pages, you can use the client-side print functionality provided in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="bec3b-109">Die clientseitige Druckfunktion stellt ein Standarddialogfeld **Drucken** bereit, das zum Auswählen eines Druckers, Angeben von Seiten und Rändern sowie zum Anzeigen einer Vorschau des Berichts vor dem Drucken verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bec3b-109">Client-side printing provides a standard **Print** dialog box that can be used to select a printer, specify pages and margins, and preview the report before you print.</span></span> <span data-ttu-id="bec3b-110">Verwenden Sie die clientseitige Druckfunktion anstelle des Befehls **Drucken** im Menü **Datei** des Browsers.</span><span class="sxs-lookup"><span data-stu-id="bec3b-110">Client-side printing is intended to be used in place of the **Print** command on the browser's **File** menu.</span></span> <span data-ttu-id="bec3b-111">Beim Verwenden dieser Funktion wird der Bericht gemäß seines Entwurfs gedruckt, ohne zusätzliche Elemente, die im Ausdruck einer Webseite zu finden sind.</span><span class="sxs-lookup"><span data-stu-id="bec3b-111">When you use client-side printing, the report is printed as it was designed, without the extra elements you see in a Web page print out.</span></span>  
  
 <span data-ttu-id="bec3b-112">Für den clientseitigen Druck müssen Sie ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] -ActiveX-Steuerelement installieren.</span><span class="sxs-lookup"><span data-stu-id="bec3b-112">To use client-side printing, you need to install a [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX control.</span></span> <span data-ttu-id="bec3b-113">Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span><span class="sxs-lookup"><span data-stu-id="bec3b-113">For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="print-options"></a><span data-ttu-id="bec3b-114">Druckoptionen</span><span class="sxs-lookup"><span data-stu-id="bec3b-114">Print Options</span></span>  
 <span data-ttu-id="bec3b-115">Sie können Druckeigenschaften für Ihren Bericht konfigurieren, indem Sie im Dialogfeld **Drucken** auf die Schaltfläche **Eigenschaften** klicken.</span><span class="sxs-lookup"><span data-stu-id="bec3b-115">To configure print properties for your report, in the **Print** dialog box, click the **Properties** button.</span></span> <span data-ttu-id="bec3b-116">Der Wert für**Papierformat** wird durch die Standardhöhe und -breite der Berichtsseitengröße gemäß Berichtsdefinition bestimmt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-116">**Paper size** is determined by the default height and width of the report page size as defined in the report definition.</span></span> <span data-ttu-id="bec3b-117">Die verfügbaren Werte sind vom Druckertyp und seinen Funktionen abhängig.</span><span class="sxs-lookup"><span data-stu-id="bec3b-117">The available values are dependent on the printer type and its capabilities.</span></span> <span data-ttu-id="bec3b-118">Für Breite und Höhe werden Standardwerte angezeigt, die durch die auf dem Computer konfigurierten Druckertreiber bestimmt werden.</span><span class="sxs-lookup"><span data-stu-id="bec3b-118">Width and height display default values as determined by the print drivers that are configured on the computer.</span></span> <span data-ttu-id="bec3b-119">Nach dem Ändern dieser Werte wird der Bericht mit den neuen Abmessungen gedruckt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-119">Changing these values causes the report to print using the new dimensions.</span></span> <span data-ttu-id="bec3b-120">Die Seitenbreite und -höhe wird durch **Ausrichtung**bestimmt. Mögliche Werte sind **Hochformat** oder **Querformat**.</span><span class="sxs-lookup"><span data-stu-id="bec3b-120">Page width and height are each determined by **Orientation**, which is set to either **Portrait** or **Landscape**.</span></span> <span data-ttu-id="bec3b-121">Die angezeigte Standardausrichtung ist von der Seitenbreite und Seitenhöhe des Berichts abhängig.</span><span class="sxs-lookup"><span data-stu-id="bec3b-121">The default orientation displayed is dependent on the page width and page height of the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bec3b-122"> Das Dialogfeld **Drucken** und die Standarddruckereinstellungen für Breite, Höhe und Seitenausrichtung werden von der Berichtsdefinition bestimmt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-122">The **Print** dialog box and the default printer settings for width, height, and page orientation are determined by the report definition.</span></span>  
  
### <a name="print-preview"></a><span data-ttu-id="bec3b-123">Seitenansicht</span><span class="sxs-lookup"><span data-stu-id="bec3b-123">Print Preview</span></span>  
 <span data-ttu-id="bec3b-124">Sie können die Vorschau eines Berichts anzeigen, indem Sie im Dialogfeld **Drucken** auf die Schaltfläche **Vorschau** klicken.</span><span class="sxs-lookup"><span data-stu-id="bec3b-124">To preview a report, in the **Print** dialog box, click the **Preview** button.</span></span> <span data-ttu-id="bec3b-125">Durch Klicken auf Vorschau wird die erste Seite des Berichts in einem separaten Vorschaufenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="bec3b-125">Clicking preview opens the first page of the report in a separate preview window.</span></span> <span data-ttu-id="bec3b-126">Weitere Seiten werden beim Rendern des Berichts auf dem Berichtsserver verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bec3b-126">Additional pages are made available as the report is rendered on the report server.</span></span> <span data-ttu-id="bec3b-127">Ein als Vorschau angezeigter Bericht wird im EMF-Format gerendert.</span><span class="sxs-lookup"><span data-stu-id="bec3b-127">A previewed report is rendered in EMF format.</span></span> <span data-ttu-id="bec3b-128">Sie können zur vorherigen oder nächsten Seite navigieren, bis die letzte Seite erreicht ist. Dann ist die Schaltfläche **Weiter** deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="bec3b-128">You can navigate to the previous or next page until the last page is reached, and the **Next** button is disabled.</span></span>  
  
### <a name="adjusting-print-margins"></a><span data-ttu-id="bec3b-129">Anpassen der Druckränder</span><span class="sxs-lookup"><span data-stu-id="bec3b-129">Adjusting Print Margins</span></span>  
 <span data-ttu-id="bec3b-130">Sie können die Druckränder im gerenderten EMF-Bericht vor dem Drucken des Berichts ändern.</span><span class="sxs-lookup"><span data-stu-id="bec3b-130">You can modify the print margins in the rendered EMF report prior to printing the report.</span></span> <span data-ttu-id="bec3b-131">Klicken Sie hierzu im Dialogfeld **Drucken** auf die Schaltfläche **Vorschau** .</span><span class="sxs-lookup"><span data-stu-id="bec3b-131">To do this, in the **Print** dialog box, click the **Preview** button.</span></span> <span data-ttu-id="bec3b-132">Klicken Sie oben auf der Vorschauseite auf die Schaltfläche **Ränder** .</span><span class="sxs-lookup"><span data-stu-id="bec3b-132">At the top of the preview page, click the **Margins** button.</span></span> <span data-ttu-id="bec3b-133">Das Dialogfeld Ränder wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bec3b-133">The Margins dialog box is displayed.</span></span> <span data-ttu-id="bec3b-134">Konfigurieren Sie bei Bedarf den oberen, unteren, rechten und linken Rand.</span><span class="sxs-lookup"><span data-stu-id="bec3b-134">Configure the top, bottom, right, and left margins as desired.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)] <span data-ttu-id="bec3b-135">Das Dialogfeld wird geschlossen, und die Einstellungen werden für die Renderingvorschau und den Druckvorgang gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bec3b-135">The dialog box closes and the settings are stored for rendering preview and printing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec3b-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bec3b-136">See Also</span></span>  
 <span data-ttu-id="bec3b-137">[Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bec3b-137">[Print Reports &#40;Report Builder and SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bec3b-138">Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bec3b-138">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](print-a-report-report-builder-and-ssrs.md)  
  
  