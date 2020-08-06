---
title: Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierten Komponenten von Drittanbietern. Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12ff188fb6aa6ac286817a7cc1c3ad726483c886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630504"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a><span data-ttu-id="35c50-102">Die Microsoft-Volltext-Engine für SQL Server lädt standardmäßig keine nicht signierten Komponenten von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="35c50-102">The Microsoft Full-Text Engine for SQL Server will not load unsigned third-party components by default</span></span>
  <span data-ttu-id="35c50-103">Standardmäßig lädt die [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Komponenten, die nicht von [!INCLUDE[msCoName](../../includes/msconame-md.md)] signiert sind.</span><span class="sxs-lookup"><span data-stu-id="35c50-103">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not load components that are not signed by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="35c50-104">Komponente</span><span class="sxs-lookup"><span data-stu-id="35c50-104">Component</span></span>  
 <span data-ttu-id="35c50-105">Volltextsuche</span><span class="sxs-lookup"><span data-stu-id="35c50-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="35c50-106">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="35c50-106">Description</span></span>  
 <span data-ttu-id="35c50-107">Ein Filter eines Drittanbieters, wie z. B. ein PDF-Filter, der derzeit auf dem Server installiert ist, wird nach dem Upgrade standardmäßig nicht von der [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Volltext-Engine für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen.</span><span class="sxs-lookup"><span data-stu-id="35c50-107">A third-party filter, such as a PDF filter, that is currently installed on the server will not be loaded by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by default after upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="35c50-108">Korrekturmaßnahme</span><span class="sxs-lookup"><span data-stu-id="35c50-108">Corrective Action</span></span>  
 <span data-ttu-id="35c50-109">Um einen Drittanbieter Filter zu laden, müssen Sie *load_os_resource* festlegen und *verify_signature* für diese Instanz deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="35c50-109">To load a third party filter, you must set *load_os_resource* and turn off *verify_signature* on that instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c50-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="35c50-110">See Also</span></span>  
 [<span data-ttu-id="35c50-111">Arbeiten mit dem Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="35c50-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  