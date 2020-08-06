---
title: Herstellen einer Verbindung mit einem Berichts Server im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615784"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="b18f7-102">Herstellen einer Verbindung mit einem Berichtsserver im einheitlichen Modus</span><span class="sxs-lookup"><span data-stu-id="b18f7-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="b18f7-103">Verwenden Sie dieses Dialogfeld, um eine Verbindung mit einer lokalen oder Remote-Berichtsserverinstanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder einer späteren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Version herzustellen.</span><span class="sxs-lookup"><span data-stu-id="b18f7-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="b18f7-104">Dieses Tool kann nicht verwendet werden, um eine Verbindung mit früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsservern herzustellen.</span><span class="sxs-lookup"><span data-stu-id="b18f7-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="b18f7-105">Sie können nur jeweils eine Verbindung zu einer Instanz herstellen.</span><span class="sxs-lookup"><span data-stu-id="b18f7-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="b18f7-106">Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.</span><span class="sxs-lookup"><span data-stu-id="b18f7-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b18f7-107">Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager wird nicht zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet.</span><span class="sxs-lookup"><span data-stu-id="b18f7-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="b18f7-108">Verwenden Sie die SharePoint-Zentraladministration und PowerShell-Skripts zum Konfigurieren eines Berichtsservers im SharePoint-Modus.</span><span class="sxs-lookup"><span data-stu-id="b18f7-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="b18f7-109">Weitere Informationen finden Sie unter [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span><span class="sxs-lookup"><span data-stu-id="b18f7-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="b18f7-110">Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) wird mit der Berechtigungsstufe "highestAvailable" installiert.</span><span class="sxs-lookup"><span data-stu-id="b18f7-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="b18f7-111">Dieses Verhalten ist beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="b18f7-111">This behavior is by design.</span></span> <span data-ttu-id="b18f7-112">Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erfordert Kommunikation mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-APIs.</span><span class="sxs-lookup"><span data-stu-id="b18f7-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="b18f7-113">Ein Teil der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Kommunikation erfordert eine höhere Stufe oder Administratorprivilegien.</span><span class="sxs-lookup"><span data-stu-id="b18f7-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="b18f7-114">Um eine Verbindung zu einer lokalen Berichtsserverinstanz herzustellen, verwenden Sie die Standardwerte, und klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="b18f7-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="b18f7-115">Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager gibt den Namen des lokalen Servers vor und erkennt die Standardinstanz.</span><span class="sxs-lookup"><span data-stu-id="b18f7-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="b18f7-116">In den meisten Fällen können Sie auf **Verbinden** klicken, ohne die Werte ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="b18f7-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="b18f7-117">Wenn Sie mehr als eine Instanz installiert haben, müssen Sie diejenige auswählen, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b18f7-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="b18f7-118">Um eine Verbindung zu einer Remote-Berichtsserverinstanz herzustellen, geben Sie den Servernamen ein, klicken Sie auf **Suchen**, wählen Sie die Instanz aus, und klicken Sie dann auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="b18f7-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="b18f7-119">Um dieses Dialogfeld zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager.</span><span class="sxs-lookup"><span data-stu-id="b18f7-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="b18f7-120">Dieses Dialogfeld wird sofort angezeigt, wenn Sie das Tool starten.</span><span class="sxs-lookup"><span data-stu-id="b18f7-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="b18f7-121">Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="b18f7-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b18f7-122">Tastatur</span><span class="sxs-lookup"><span data-stu-id="b18f7-122">Options</span></span>  
 <span data-ttu-id="b18f7-123">**Servername**</span><span class="sxs-lookup"><span data-stu-id="b18f7-123">**Server Name**</span></span>  
 <span data-ttu-id="b18f7-124">Geben Sie den Netzwerknamen des Computers ein, auf dem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder eine spätere Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b18f7-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="b18f7-125">Geben Sie nur den Computernamen ein, kein Präfix oder Schrägstriche.</span><span class="sxs-lookup"><span data-stu-id="b18f7-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="b18f7-126">**Sich**</span><span class="sxs-lookup"><span data-stu-id="b18f7-126">**Find**</span></span>  
 <span data-ttu-id="b18f7-127">Suchen Sie den unter **Servername**angegebenen Computer.</span><span class="sxs-lookup"><span data-stu-id="b18f7-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="b18f7-128">**Berichtsserverinstanz**</span><span class="sxs-lookup"><span data-stu-id="b18f7-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="b18f7-129">Wählen Sie aus, zu welcher Instanz Sie eine Verbindung herstellen möchten, wenn mehrere Berichtsserverinstanzen installiert sind.</span><span class="sxs-lookup"><span data-stu-id="b18f7-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="b18f7-130">Es stehen nur gültige Instanzen zur Auswahl zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b18f7-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="b18f7-131">Wenn Sie ältere Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gleichzeitig mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz ausführen, werden diese Instanzen nicht in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b18f7-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="b18f7-132">**Herstellen einer Verbindung**</span><span class="sxs-lookup"><span data-stu-id="b18f7-132">**Connect**</span></span>  
 <span data-ttu-id="b18f7-133">Stellen Sie die Verbindung zum Server und zur Instanz, die Sie angegeben haben, her.</span><span class="sxs-lookup"><span data-stu-id="b18f7-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18f7-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b18f7-134">See Also</span></span>  
 [<span data-ttu-id="b18f7-135">Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;</span><span class="sxs-lookup"><span data-stu-id="b18f7-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  