---
title: Topologien für die Websynchronisierung | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618642"
---
# <a name="topologies-for-web-synchronization"></a>Topologies for Web Synchronization
  Sie können aus unterschiedlichen Websynchronisierungs-Replikationstopologien von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswählen. Hier einige der gängigen Konfigurationsmethoden für die Websynchronisierung:  
  
-   Einzelserver  
  
-   Zwei Server  
  
-   Mehrere Systeme mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internetinformationsdiensten (IIS, Internet Information Services) und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Wiederveröffentlichung  
  
 Informationen zur Konfiguration der Websynchronisierung finden Sie unter [Konfigurieren der Websynchronisierung](configure-web-synchronization.md).  
  
## <a name="single-server"></a>Einzelner Server  
 In der einfachsten Topologie befinden sich IIS, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger sowie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verteiler auf einem einzigen Server. Die Abonnenten führen den Synchronisierungsvorgang aus, indem sie mit IIS auf dem Verleger eine Verbindung herstellen. Der Verleger kann sich hinter einer Firewall befinden.  
  
> [!NOTE]  
>  Diese Konfiguration wird nur für Intranetszenarien empfohlen. Bei anderen Szenarien sollten sich der IIS-Server und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger/-Verteiler auf separaten Computern befinden.  
  
 ![Websynchronisierung mit einem einzelnen Server](media/web-sync02.gif "Websynchronisierung mit einem einzelnen Server")  
  
## <a name="two-servers"></a>Zwei Server  
 Sie können IIS auf dem einen Server installieren und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger/-Verteiler auf dem anderen Server konfigurieren. Der Server, auf dem IIS ausgeführt wird, kann durch eine Firewall vom Internet isoliert werden. Die Abonnenten führen den Synchronisierungsvorgang aus, indem sie mit IIS auf dem Verleger eine Verbindung herstellen.  
  
 ![Websynchronisierung mit zwei Servern](media/web-sync03.gif "Websynchronisierung mit zwei Servern")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>Mehrere IIS-Systeme und SQL Server-Wiederveröffentlichung  
 Wenn eine große Anzahl an Abonnenten unterstützt werden müssen, die gleichzeitig synchronisieren, kann die Arbeitsauslastung auf mehrere Computer verteilt werden, auf denen IIS ausgeführt wird.  
  
 ![Websynchronisierung mit mehreren IIS-Servern](media/web-sync04.gif "Websynchronisierung mit mehreren IIS-Servern")  
  
 Wenn auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt ist, weiterer Lastenausgleich erforderlich ist, können Sie auf mehreren Computern eine Wiederveröffentlichungshierarchie erstellen. Der Verleger der obersten Ebene veröffentlicht Daten für Abonnenten, die die Daten wiederum erneut veröffentlichen; hierbei erfolgt der Lastenausgleich hinsichtlich Anforderungen von Abonnenten.  
  
> [!NOTE]  
>  Abonnenten können nur mit einem bestimmten Verleger synchronisiert werden. Beispielsweise kann ein Abonnent von Neuverleger A nicht mit Neuverleger B synchronisiert werden, wenn A nicht verfügbar ist.  
  
 ![Websynchronisierung mit Wiederveröffentlichung](media/web-sync05.gif "Websynchronisierung mit Wiederveröffentlichung")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Websynchronisierung](configure-web-synchronization.md)   
 [Websynchronisierung für die Mergereplikation](web-synchronization-for-merge-replication.md)  
  
  
