---
title: Balkendiagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: db0cf6a0-2114-41d0-ab27-0319e52dee76
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483266607bc021a5c5a0a946aff6e7202248c582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617754"
---
# <a name="bar-charts-report-builder-and-ssrs"></a>Balkendiagramme (Berichts-Generator und SSRS)
  Ein Balkendiagramm zeigt Reihen als Sätze horizontaler Balken an. Das einfache Balkendiagramm ist eng mit dem Säulendiagramm und dem Bereichsbalkendiagramm verbunden. Das Säulendiagramm zeigt Reihen als Sätze vertikaler Balken an, während das Bereichsbalkendiagramm Reihen als Sätze horizontaler Balken mit verschiedenen Anfangs- und Endpunkten darstellt.  
  
 Das Balkendiagramm ist der einzige Diagrammtyp, der Daten horizontal anzeigt. Aus diesem Grund wird ein Balkendiagramm häufig zur Darstellung von Daten verwendet, die über einen Zeitraum hinweg auftreten, der ein festes Anfangs- und Enddatum hat. Es wird auch häufig zum Anzeigen von Kategorieinformationen herangezogen, da die Kategorien horizontal angezeigt werden können. Weitere Informationen zu Hinzufügen von Daten zu einem Ballkendiagramm finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Die folgende Abbildung zeigt ein Balkendiagramm. Das Balkendiagramm ist für diese Daten ausgezeichnet geeignet, da alle drei Reihen einen gemeinsamen Zeitraum verwenden und so zuverlässige Vergleiche vorgenommen werden können.  
  
 ![Balkendiagramm](../media/barchart.gif "Balkendiagramm")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-the-bar-chart"></a>Variationen des Balkendiagramms  
  
-   **Gestapelt**. Ein Balkendiagramm, in dem mehrere Reihen vertikal gestapelt werden. Wenn nur eine Reihe im Diagramm vorhanden ist, wird das gestapelte Balkendiagramm angezeigt wie ein Balkendiagramm.  
  
-   **Prozentual gestapelt**. Ein Balkendiagramm, in dem mehrere Reihen vertikal gestapelt sind, um auf 100 % der Diagrammfläche zu passen. Wenn nur eine Reihe im Diagramm vorhanden ist, werden alle Balken so angepasst, dass sie 100 % der Diagrammfläche ausfüllen.  
  
-   **3D gruppiert**. Ein Balkendiagramm, das in einem 3D-Diagramm einzelne Reihen in separaten Zeilen anzeigt.  
  
-   **3D-Zylinder**. Ein Balkendiagramm, das die Balken als Zylinder in einem 3D-Diagramm gestaltet.  
  
## <a name="data-considerations-for-bar-charts"></a>Überlegungen zu Daten für ein Balkendiagramm  
  
-   Bei Balkendiagrammen werden die Achsen umgekehrt. Die Kategorieachse ist die vertikale Achse ("Y-Achse") und die Wertachse ist die horizontale Achse ("X-Achse"). Dies bedeutet, dass in einem Balkendiagramm mehr Platz für Kategoriebezeichnungen entlang der Y-Achse zur Verfügung steht als in einer Liste mit Einträgen von oben nach unten.  
  
-   Balken- und Säulendiagramme werden häufig verwendet, um Vergleiche zwischen Gruppen anzuzeigen. Wenn mehr als drei Reihen im Diagramm vorhanden sind, bietet sich eher ein gestapeltes Balken- oder Säulendiagramm an. Außerdem können Sie gestapelte Balken- oder Säulendiagramme in mehrere Gruppen zusammenfassen, wenn mehrere Reihen im Diagramm vorhanden sind.  
  
-   In einem Balkendiagramm werden Werte von links nach rechts angezeigt, was beim Anzeigen von Daten bezogen auf die Dauer intuitiver sein kann.  
  
-   Wenn Sie Balken zu einer Tabelle oder Matrix innerhalb des Berichts hinzufügen möchten, sollten Sie erwägen, ein lineares Messgerät statt eines Balkendiagramms zu verwenden. Das lineare Messgerät ist für die Anzeige eines Werts statt mehrerer Gruppen konzipiert, sodass es für die Verwendung innerhalb einer Liste oder eines Tabellendatenbereichs mehr Flexibilität bietet. Weitere Informationen finden Sie unter [Messgeräte &#40;Berichts-Generator und SSRS&#41;](gauges-report-builder-and-ssrs.md).  
  
-   Sie können den einzelnen Balken eines Balkendiagramms besondere Zeichnungsformate hinzufügen, um die visuelle Wirkung zu erhöhen. Zeichnungsarten schließen Keil, Prägen, Zylinder und Helligkeitsabstufungen ein. Diese Effekte sollen die Darstellung des 2D-Diagramms verbessern. Bei Verwendung eines 3D-Diagramms werden die Zeichnungsarten zwar ebenfalls übernommen, sie haben jedoch möglicherweise nicht den gleichen Effekt. Weitere Informationen zum Hinzufügen einer Zeichnungsart zu einem Diagramm finden Sie unter [Hinzufügen einer Abschrägung, Prägung und Struktur zu einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).  
  
-   Bei gestapelten Balkendiagrammen werden Reihen aufeinander gestapelt, sodass sie einen mehrteiligen Stapel ergeben. Sie können das gestapelte Balkendiagramm für jede Kategorie in mehrere Gruppen von Stapeln unterteilen. Die gruppierten gestapelten Diagramme werden nebeneinander angezeigt. Ein Diagramm kann beliebig viele gruppierte Stapelfolgen enthalten.  
  
-   Wenn in einem Balkendiagramm Datenpunktbezeichnungen angezeigt werden, werden diese außerhalb der Balken platziert. Dies kann dazu führen, dass Bezeichnungen überlappen, wenn die Balken den gesamten zugewiesenen Raum im Diagrammbereich einnehmen. Sie können die Position der Datenpunktbezeichnungen, die für die einzelnen Balken angezeigt werden, durch Festlegen der **BarLabelStyle** -Eigenschaft im Eigenschaftenbereich ändern.  
  
-   Wenn im Verhältnis zur Größe des Diagramms viele Datenpunkte im Dataset vorhanden sind, wird die Größe der Säulen oder Balken und der Abstand zwischen diesen verringert. Um die Breite der Säulen in einem Diagramm manuell festzulegen, ändern Sie deren Breite in Pixel, indem Sie die **PointWidth** -Eigenschaft ändern. Standardmäßig ist der Wert dieser Eigenschaft 0,8. Wenn Sie die Breite der Säulen oder Balken in einem Diagramm erhöhen, verringert sich der Abstand zwischen den einzelnen Säulen oder Balken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Leere und NULL-Datenpunkte in Diagrammen (Berichts-Generator und SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Säulendiagramme (Berichts-Generator und SSRS)](column-charts-report-builder-and-ssrs.md)   
 [Bereichsdiagramme &#40;Berichts-Generator und SSRS&#41;](range-charts-report-builder-and-ssrs.md)   
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Hinzufügen einer Abschrägung, Prägung und Struktur zu einem Diagramm (Berichts-Generator und SSRS)](chart-effects-add-bevel-emboss-or-texture-report-builder.md)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)](https://go.microsoft.com/fwlink/?LinkId=198052)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht](https://go.microsoft.com/fwlink/?LinkId=198042)  
  
  
