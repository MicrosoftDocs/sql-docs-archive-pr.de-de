---
title: Sekundäre Datenbank ist nicht verknüpft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724210"
---
# <a name="secondary-database-is-not-joined"></a>Sekundäre Datenbank ist nicht verknüpft
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Joinzustand der Verfügbarkeitsdatenbank|  
|**Problem**|Die sekundäre Datenbank ist nicht verknüpft.|  
|**Kategorie**|**Warning**|  
|**Facet**|Verfügbarkeitsdatenbank|  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Richtlinie überprüft den Joinstatus der sekundären Datenbank (auch bekannt als "sekundäres Datenbankreplikat"). Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn das Datenbankreplikat nicht verknüpft wird. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Sekundäre Datenbank ist nicht verknüpft](https://go.microsoft.com/fwlink/p/?LinkId=220862) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Diese sekundäre Datenbank ist nicht mit der Verfügbarkeitsgruppe verknüpft. Die Konfiguration dieser sekundären Datenbank ist unvollständig.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verknüpfen Sie das sekundäre Replikat mit der Verfügbarkeitsgruppe mithilfe von Transact-SQL, PowerShell oder SQL Server Management Studio. Weitere Informationen zum Verknüpfen sekundärer Replikate mit Verfügbarkeitsgruppen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
