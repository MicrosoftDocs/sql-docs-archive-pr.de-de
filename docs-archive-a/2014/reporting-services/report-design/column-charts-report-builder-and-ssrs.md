---
title: Säulendiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6ebada49e65d44a2294228a3840bf4951140812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726514"
---
# <a name="column-charts-report-builder-and-ssrs"></a>Säulendiagramme (Berichts-Generator und SSRS)
  Ein Säulendiagramm zeigt eine Reihe als Satz vertikaler Balken an, die nach Kategorie gruppiert sind. Säulendiagramme sind nützlich, um Datenänderungen über einen bestimmten Zeitraum anzuzeigen oder Vergleiche zwischen Elementen zu veranschaulichen. Das einfache Säulendiagramm ist eng mit dem Balkendiagramm und dem Säulenbereichsdiagramm verbunden. Das Balkendiagramm zeigt Reihen als Sätze horizontaler Balken an, während das Bereichssäulendiagramm Reihen als Sätze vertikaler Balken mit verschiedenen Anfangs- und Endpunkten darstellt. Weitere Informationen finden Sie unter [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md) und [Bereichsdiagramme &#40;Berichts-Generator und SSRS&#41;](range-charts-report-builder-and-ssrs.md).  
  
 Das Säulendiagramm ist für diese Daten ausgezeichnet geeignet, da alle drei Reihen einen gemeinsamen Zeitraum verwenden und so zuverlässige Vergleiche vorgenommen werden können.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a>Variationen eines Säulendiagramms  
  
-   **Gestapelt**. Ein Säulendiagramm, in dem mehrere Reihen vertikal gestapelt werden. Wenn nur eine Reihe im Diagramm vorhanden ist, wird das gestapelte Säulendiagramm angezeigt wie ein Säulendiagramm.  
  
-   **Prozentual gestapelt**. Ein Säulendiagramm, in dem mehrere Reihen vertikal gestapelt sind, um auf 100 % der Diagrammfläche zu passen. Wenn nur eine Reihe im Diagramm vorhanden ist, werden alle Säulenbalken so angepasst, dass sie 100 % der Diagrammfläche ausfüllen.  
  
-   **3D gruppiert**. Ein Säulendiagramm, das in einem 3D-Diagramm einzelne Reihen in separaten Zeilen anzeigt.  
  
-   **3D-Zylinder**. Ein Säulendiagramm, dessen Balken wie Zylinder in einem 3D-Diagramm gestaltet sind.  
  
-   `Histogram`. Ein Säulendiagramm, das das Diagramm berechnet, damit seine Balken in einer Normalverteilung angeordnet werden.  
  
-   `Pareto`. Ein Säulendiagramm, dessen Balken von der höchsten zur niedrigsten Instanz angeordnet werden.  
  
## <a name="data-considerations-for-a-column-chart"></a>Überlegungen zu Daten für ein Säulendiagramm  
  
-   Balken- und Säulendiagramme werden häufig verwendet, um Vergleiche zwischen Gruppen anzuzeigen. Wenn mehr als drei Reihen im Diagramm vorhanden sind, bietet sich eher ein gestapeltes Balken- oder Säulendiagramm an. Außerdem können Sie gestapelte Balken- oder Säulendiagramme in mehrere Gruppen zusammenfassen, wenn mehrere Reihen im Diagramm vorhanden sind. Weitere Informationen finden Sie unter [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md) und *Säulen Diagramme*.  
  
-   In einem Säulendiagramm haben Sie weniger Platz, um Kategorieachsenbezeichnungen horizontal anzuzeigen. Bei längeren Kategoriebezeichnungen sollten Sie erwägen, ein Balkendiagramm zu verwenden oder den Drehwinkel für die Bezeichnung zu ändern.  
  
-   Sie können den einzelnen Balken eines Säulendiagramms besondere Zeichnungsarten hinzufügen, um die visuelle Wirkung zu erhöhen. Zeichnungsarten schließen Keil, Prägen, Zylinder und Helligkeitsabstufungen ein. Diese Effekte sollen die Darstellung des 2D-Diagramms verbessern. Bei Verwendung eines 3D-Diagramms werden die Zeichnungsarten zwar ebenfalls übernommen, sie haben jedoch möglicherweise nicht den gleichen Effekt. Weitere Informationen zum Hinzufügen einer Zeichnungsart zu einem Diagramm finden Sie unter [Hinzufügen einer Abschrägung, Prägung und Struktur zu einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).  
  
-   Säulendiagramme besitzen die einzigartige Fähigkeit, ein Diagramm als Histogramm oder Paretodiagramm anzuzeigen. Legen Sie dazu die Eigenschaft ShowColumnAs auf `Histogram` oder im Eigenschaftenfenster auf oder fest `Pareto` `true` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Balkendiagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Bereichsdiagramme &#40;Berichts-Generator und SSRS&#41;](range-charts-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)](../tutorial-add-a-bar-chart-to-your-report-report-builder.md)   
 [Leere und NULL-Datenpunkte in Diagrammen &#40;Berichts-Generator und SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
