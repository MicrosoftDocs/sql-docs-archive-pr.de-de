---
title: Durchsuchen des bereitgestellten Cubes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b876c8b2876aaf4ad28b0f4ea3fb8bab32cd787b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619430"
---
# <a name="browsing-the-deployed-cube"></a>Durchsuchen des bereitgestellten Cubes
  In der folgenden Aufgabe durchsuchen Sie den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube. Da Measures in der Analyse dimensionsübergreifend verglichen werden, verwenden Sie zum Durchsuchen von Daten eine Excel-PivotTable. Mithilfe einer PivotTable lassen sich Kunden-, Datums- und Produktinformationen auf verschiedenen Achsen platzieren. So können Sie verfolgen, wie sich die Internetverkäufe ändern, wenn sie für bestimmte Zeiträume, Kundendemografien und Produktlinien angezeigt werden.  
  
### <a name="to-browse-the-deployed-cube"></a>So durchsuchen Sie den bereitgestellten Cube  
  
1.  Um zum Cube-Designer in zu wechseln [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] , doppelklicken Sie im Ordner **Cubes** der Projektmappen-Explorer auf den ** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial** -Cube.  
  
2.  Öffnen Sie die Registerkarte **Browser** , und klicken Sie dann auf der Symbolleiste des Designers auf die Schaltfläche **Verbindung wiederherstellen** .  
  
3.  Klicken Sie auf das Excel-Symbol, um Excel zu starten, wobei die Arbeitsbereichsdatenbank als Datenquelle verwendet wird. Sobald Sie aufgefordert werden, Verbindungen zu aktivieren, klicken Sie auf **Aktivieren**.  
  
4.  Erweitern Sie in der PivotTable-Feldliste **Internet Sales**, und ziehen Sie dann das **Sales Amount** -Measure in den Bereich **Werte** .  
  
5.  Erweitern Sie in der PivotTable-Feldliste den Eintrag **Product**.  
  
6.  Ziehen Sie die **Product Model Lines** -Benutzerhierarchie in den Bereich **Spalten** .  
  
7.  Erweitern Sie in der PivotTable-Feldliste die Option **Customer**, erweitern Sie **Location**, und ziehen Sie die **Customer Geography** -Hierarchie aus dem Anzeigeordner **Location** in der Customer-Dimension in den Bereich Zeilen.  
  
8.  Erweitern Sie in der PivotTable-Feldliste den Eintrag **Order Date**, und ziehen Sie dann die **Order Date.Calendar Date** -Hierarchie in den Bereich **Berichtsfilter** .  
  
9. Klicken Sie auf den Filter rechts vom Filter **Order Date.Calendar Date** im Datenbereich, deaktivieren Sie das Kontrollkästchen für die Ebene **(Alle)** , erweitern Sie **2006**&gt; **H1 CY 2006**&gt; **Q1 CY 2006**, aktivieren Sie das Kontrollkästchen für **Februar 2006**, und klicken Sie anschließend auf **OK**.  
  
     Internetverkäufe nach Region und Produktgruppe für den Monat Februar 2006 werden wie im folgenden Bild angezeigt.  
  
     ![Internet Sales nach Land/Region und Produktlinie](../../2014/tutorials/media/l3-cube-browser-finish.gif "Internet Sales nach Land/Region und Produktlinie")  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Definieren von erweiterten Attributen und Dimensionseigenschaften](lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
