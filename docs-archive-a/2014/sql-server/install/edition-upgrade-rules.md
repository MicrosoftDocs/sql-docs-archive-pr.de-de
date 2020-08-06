---
title: Editions upgraderegeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 77c4d751-4fea-4e69-a7c8-ab8fc0dbadb2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 453944ede41bfc5cf258c6f0946b15b716c6c22c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617477"
---
# <a name="edition-upgrade-rules"></a><span data-ttu-id="930b5-102">Upgraderegeln für Editionen</span><span class="sxs-lookup"><span data-stu-id="930b5-102">Edition Upgrade Rules</span></span>
  <span data-ttu-id="930b5-103">Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup überprüft die Computerkonfiguration, bevor der Setupvorgang abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="930b5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="930b5-104">Während des Setups von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchsucht die Systemkonfigurationsprüfung (System Configuration Checker, SCC) den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="930b5-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="930b5-105">SCC sucht nach Bedingungen, die ein erfolgreiches Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindern.</span><span class="sxs-lookup"><span data-stu-id="930b5-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="930b5-106">Bevor Setup das Editionsupgrade startet, ruft SCC den Status jedes Elements ab.</span><span class="sxs-lookup"><span data-stu-id="930b5-106">Before Setup starts the edition upgrade, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="930b5-107">SCC vergleicht dann das Ergebnis mit den erforderlichen Bedingungen und gibt Anweisungen zum Entfernen der Blockierungsprobleme.</span><span class="sxs-lookup"><span data-stu-id="930b5-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="930b5-108">Die Systemkonfigurationsprüfung generiert einen Bericht, der eine kurze Beschreibung für jede ausgeführte Regel sowie den Ausführungsstatus enthält.</span><span class="sxs-lookup"><span data-stu-id="930b5-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="930b5-109">Der Bericht der Systemkonfigurations Prüfung befindet sich unter% Program Files% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\setup Bootstrap\LOG \\<YYYYMMDD_HHMM>\\ .</span><span class="sxs-lookup"><span data-stu-id="930b5-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="930b5-110">Bevor Sie Setup ausführen, lesen Sie die folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="930b5-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="930b5-111">Hardware- und Softwareanforderungen für die Installation von SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="930b5-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="930b5-112">Von den Editionen von SQL Server 2014 unterstützte Features</span><span class="sxs-lookup"><span data-stu-id="930b5-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="930b5-113">Überlegungen zur Sicherheit bei SQL Server-Installationen</span><span class="sxs-lookup"><span data-stu-id="930b5-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="930b5-114">Lokale Sprachversionen in SQL Server</span><span class="sxs-lookup"><span data-stu-id="930b5-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="930b5-115">Weitere Referenzen:</span><span class="sxs-lookup"><span data-stu-id="930b5-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="930b5-116">Unterstützte Versions- und Editionsupgrades</span><span class="sxs-lookup"><span data-stu-id="930b5-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="930b5-117">Vor dem Installieren des Failoverclusterings</span><span class="sxs-lookup"><span data-stu-id="930b5-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a><span data-ttu-id="930b5-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="930b5-118">See Also</span></span>  
 [<span data-ttu-id="930b5-119">Installationsregeln</span><span class="sxs-lookup"><span data-stu-id="930b5-119">Install Rules</span></span>](../../../2014/sql-server/install/install-rules.md)  
  
  