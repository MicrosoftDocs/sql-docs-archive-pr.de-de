---
title: Konfigurieren von Measure-Gruppen Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03dad3d8ee33ea8a78b08f9a354d0db3d177198c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721970"
---
# <a name="configure-measure-group-properties"></a>Konfigurieren von Measuregruppeneigenschaften
  Measuregruppen haben Eigenschaften, die es Ihnen ermöglichen, die Funktionsweise von Measuregruppen zu definieren.  
  
## <a name="measure-group-properties"></a>Eigenschaften von Measuregruppen  
 Die Eigenschaften von Measuregruppen bestimmen das Verhalten innerhalb der gesamten Measuregruppe und legen das Standardverhalten für bestimmte Eigenschaften von Measures innerhalb einer Measuregruppe fest.  
  
|Eigenschaft|Definition|  
|--------------|----------------|  
|`AggregationPrefix`|Gilt für die ROLAP-Speicherung. Weist den indizierten Sichten in SQL Server ein gemeinsames Präfix zu, das zum Speichern von Aggregationen für die mit dieser Measuregruppe verknüpften Partitionen verwendet wird.|  
|`DataAggregation`|Diese Eigenschaft ist für die zukünftige Verwendung reserviert und hat derzeit keine Auswirkungen. Aus diesem Grund wird empfohlen, diese Einstellung nicht zu ändern.|  
|`Description`|Mit dieser Eigenschaft können Sie die Measuregruppe dokumentieren.|  
|`ErrorConfiguration`|Konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln. Weitere Informationen finden Sie unter [Fehlerkonfiguration für die Verarbeitung von Cubes, Partitionen und Dimensionen &#40;SSAS - mehrdimensional&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).|  
|`EstimatedRows`|Gibt die geschätzte Anzahl von Zeilen in der Faktentabelle an.|  
|`EstimatedSize`|Gibt die geschätzte Größe (in Byte) der Measuregruppe an.|  
|`ID`|Gibt den Bezeichner des Objekts an.|  
|`IgnoreUnrelatedDimensions`|Bestimmt, ob nicht verknüpfte Dimensionen auf ihre höchste Ebene gezwungen werden, wenn Elemente von Dimensionen, die nicht mit der Measuregruppe verknüpft sind, in eine Abfrage eingeschlossen werden. Die Standardeinstellung ist `True` .|  
|`Name`|Name des Measures. Diese Eigenschaft ist schreibgeschützt.|  
|`ProactiveCaching`|Konfigurierbare Fehlerbehandlungseinstellungen für die Bearbeitung doppelter Schlüssel, unbekannter Schlüssel, für Fehlergrenzen, Aktionen bei Erkennung von Fehlern, Fehlerprotokolldateien und die Bearbeitung von NULL-Schlüsseln.|  
|`ProcessingMode`|Gibt an, ob während oder nach der Verarbeitung indiziert und aggregiert werden soll. Die verfügbaren Optionen sind Regular und LazyAggregations. LazyAggregations kann verwendet werden, um die Aggregation als Hintergrundaufgabe auszuführen.|  
|`ProcessingPriority`|Legt die Verarbeitungspriorität des Cubes bei Hintergrundvorgängen wie z. B. verzögerte Aggregationen und Indizierungen fest. Der Standardwert ist **0**.|  
|`StorageLocation`|Der Speicherort des Dateisystems für die Measuregruppe. Wird kein Speicherort angegeben, wird er vom Cube geerbt, der die Measuregruppe enthält.|  
|`StorageMode`|Der Speichermodus für die Measuregruppe. Die verfügbaren Werte sind MOLAP, ROLAP und HOLAP.|  
|`Type`|Gibt den Typ der Measuregruppe an.|  
  
  
