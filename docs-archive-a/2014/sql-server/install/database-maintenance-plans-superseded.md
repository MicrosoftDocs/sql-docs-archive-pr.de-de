---
title: Erersetzte Datenbank-Wartungspläne | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- suspended database maintenance plans
- database maintenance plans [SQL Server Agent]
- maintenance plans [SQL Server Agent]
ms.assetid: efac127c-6c81-4c7a-a6c4-9aae5d15545d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3aea75cc4ecc94ccbaeb1f35cecd0b18ff3a65ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608244"
---
# <a name="database-maintenance-plans-superseded"></a>Außer Kraft gesetzte Datenbank-Wartungspläne
    
## <a name="component"></a>Komponente  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent  
  
## <a name="description"></a>BESCHREIBUNG  
 Vorhandene Datenbank-Wartungspläne werden aktualisiert und funktionieren weiterhin. Sie können allerdings keine neuen Datenbank-Wartungspläne mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen. Um die Wartungspläne im Objekt-Explorer anzuzeigen, erweitern Sie Verwaltung und dann Legacy. Sie können vorhandene Daten Bank Wartungspläne in das neue Format migrieren, indem Sie im Kontextmenü für einen beliebigen Datenbank-Wartungsplan **Migrieren** auswählen. Da die neue Wartungsplanfunktion kein direkter Ersatz der Datenbank-Wartungspläne ist, stehen möglicherweise einige Funktionen nach der Migration nicht mehr zur Verfügung. Bei der Migration eines Datenbank-Wartungsplans wird der alte Plan nicht gelöscht, sodass Sie seine Funktionalität als Wartungsplan testen können, bevor Sie den alten Plan entfernen.  
  
 Die folgenden Funktionen werden innerhalb der Datenbank-Wartungspläne nicht mehr unterstützt:  
  
-   Protokollversand  
  
-   Der **Versuch, geringfügige Probleme zu beheben,** der Task " **Daten Bank Integritätsprüfung** "  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindert ein Einschließen des Protokollversands in Datenbankwartungspläne. Weitere Informationen finden Sie unter "Protokollversand" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
  
