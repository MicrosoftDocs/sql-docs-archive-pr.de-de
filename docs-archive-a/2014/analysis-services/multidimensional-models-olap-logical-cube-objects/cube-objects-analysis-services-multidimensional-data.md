---
title: Cubeobjekte (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618941"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Cubeobjekte (Analysis Services – Mehrdimensionale Daten)
    
## <a name="introducing-cube-objects"></a>Einführung in Cubeobjekte  
 Ein einfaches <xref:Microsoft.AnalysisServices.Cube>-Objekt besteht aus grundlegenden Informationen, Dimensionen und Measuregruppen. Grundlegende Informationen beinhalten den Namen des Cubes, das Standardmeasure des Cubes, die Datenquelle, den Speichermodus usw.  
  
 Die Dimensionsauflistung enthält den eigentlichen Dimensionssatz, der im Cube aus der Dimensionsauflistung der Datenbank verwendet wird. Alle Dimensionen müssen in der Dimensionsauflistung der Datenbank definiert werden, bevor im Cube auf sie verwiesen wird. Private Dimensionen sind in nicht verfügbar [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Measuregruppen sind Sätze von Measures im Cube. Eine Measuregruppe ist eine Auflistung von Measures, die eine gemeinsame Datenquellensicht und einen gemeinsamen Satz von Dimensionen besitzen. Eine Measuregruppe ist die Verarbeitungseinheit für Measures. Measuregruppen können einzeln verarbeitet und dann durchsucht werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|||  
|-|-|  
|Thema||  
|[Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[Aggregations and Aggregation Designs](aggregations-and-aggregation-designs.md)||  
|[Berechnungen](calculations.md)||  
|[Cubezellen &#40;Analysis Services-Mehrdimensionale Daten&#41;](cube-cells-analysis-services-multidimensional-data.md)||  
|[Cubeeigenschaften](cube-properties-multidimensional-model-programming.md)||  
|[Cube-Speicher &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-storage-analysis-services-multidimensional-data.md)||  
|[Cubeübersetzungen](cube-translations.md)||  
|[Dimensionsbeziehungen](dimension-relationships.md)||  
|[Leistungskennzahlen &#40;Key Performance Indicators, KPIs&#41; in mehrdimensionalen Modellen](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[Measures und Measuregruppen](../multidimensional-models/measures-and-measure-groups.md)||  
|[Partitionen &#40;Analysis Services – mehrdimensionale Daten&#41;](partitions-analysis-services-multidimensional-data.md)||  
|[Perspektiven](perspectives.md)||  
  
  
