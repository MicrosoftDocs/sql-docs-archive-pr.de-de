---
title: Cubes in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 372bb8075b232ff8fbf8a54facf9bc065e6763a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725098"
---
# <a name="cubes-in-multidimensional-models"></a>Cubes in mehrdimensionalen Modellen
  Ein Cube ist eine mehrdimensionale Struktur, die Informationen für analytische Zwecke enthält. Die Hauptbestandteile eines Cubes sind Dimensionen und Measures. Dimensionen definieren die Struktur des Cubes, den Sie für Aufteilungen verwenden, während Measures dem Endbenutzer numerische Werte zur Verfügung stellen, die für ihn von Interesse sind. Als logische Struktur ermöglicht ein Cube einer Clientanwendung das Abrufen von Werten von Measures, so als ob sie in Zellen im Cube enthalten wären. Zellen werden für jeden möglichen zusammengefassten Wert definiert. Eine Zelle im Cube wird von der Schnittmenge von Dimensionselementen definiert und enthält die aggregierten Werte der Measures an dieser speziellen Schnittmenge.  
  
## <a name="benefits-of-using-cubes"></a>Vorteile der Verwendung von Cubes  
 Ein Cube bietet eine einzelne Position, an der alle verknüpften Daten für die Analyse gespeichert werden.  
  
## <a name="components-of-cubes"></a>Komponenten von Cubes  
 Ein Cube besteht aus den folgenden Elementen:  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|Dimensionen|[Dimensionen in mehrdimensionalen Modellen](dimensions-in-multidimensional-models.md)|  
|Measures und Measuregruppen|[Erstellen von Measures und Measuregruppen in mehrdimensionalen Modellen](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Partitionen|[Partitionen in mehrdimensionalen Modellen](partitions-in-multidimensional-models.md)|  
|Perspektiven|[Perspektiven in mehrdimensionalen Modellen](perspectives-in-multidimensional-models.md)|  
|Hierarchien|[Erstellen von benutzerdefinierten Hierarchien](user-defined-hierarchies-create.md)|  
|Aktionen|[Aktionen in mehrdimensionalen Modellen](actions-in-multidimensional-models.md)|  
|Key Performance Indicators (KPI)|[Leistungskennzahlen &#40;Key Performance Indicators, KPIs&#41; in mehrdimensionalen Modellen](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|Berechnungen|[Berechnungen in mehrdimensionalen Modellen](calculations-in-multidimensional-models.md)|  
|Translations|[Übersetzungen in mehrdimensionalen Modellen](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen eines Cubes mit dem Cube-Assistenten](create-a-cube-using-the-cube-wizard.md)|Beschreibt das Definieren von Cubes, Dimensionen, Dimensionsattributen und benutzerdefinierten Hierarchien mithilfe des Cube-Assistenten.|  
|[Erstellen von Measures und Measuregruppen in mehrdimensionalen Modellen](create-measures-and-measure-groups-in-multidimensional-models.md)|Beschreibt das Definieren von Measuregruppen.|  
|[Berechnungen in mehrdimensionalen Modellen](calculations-in-multidimensional-models.md)|Beschreibt das Definieren und Konfigurieren einer Berechnung in einem MDX-Skript.|  
|[Aktionen in mehrdimensionalen Modellen](actions-in-multidimensional-models.md)|Beschreibt das Definieren und Konfigurieren einer Aktion.|  
|[Perspektiven in mehrdimensionalen Modellen](perspectives-in-multidimensional-models.md)|Beschreibt das Definieren und Konfigurieren einer Perspektive.|  
|[Definieren von gespeicherten Proze](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Beschreibt das Verwenden von gespeicherten Prozeduren.|  
  
  
