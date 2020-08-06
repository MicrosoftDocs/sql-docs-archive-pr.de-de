---
title: Mehrere Reihen in einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b99e4398-1fba-4824-958f-5c75d10485ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fcd8cd8f1fbfece296fba49aaceebd822d7406a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719549"
---
# <a name="multiple-series-on-a-chart-report-builder-and-ssrs"></a>Mehrere Reihen in einem Diagramm (Berichts-Generator und SSRS)
  Wenn in einem Diagramm mehrere Reihen vorhanden sind, müssen Sie die optimale Möglichkeit zum Vergleichen der Reihen bestimmen. Sie können ein gestapeltes Diagramm verwenden, in dem die relativen Anteile der einzelnen Reihen angezeigt werden. Wenn Sie nur zwei Reihen vergleichen, die über eine gemeinsame Kategorieachse (X) verfügen, verwenden Sie die sekundäre Achse. Dies ist hilfreich, wenn zwei aufeinander bezogene Reihen von Daten angezeigt werden, z. B. Preis und Volumen oder Einkommen und Steuern. Wenn die Lesbarkeit des Diagramms beeinträchtigt wird, empfiehlt es sich, mehrere Diagrammflächen zu verwenden, um die einzelnen Reihen visuell stärker voneinander zu trennen.  
  
 Neben der Verwendung von Diagrammfunktionen ist er unerlässlich zu entscheiden, welcher Diagrammtyp für die Daten verwendet werden soll. Wenn die Felder im Dataset in Beziehung zueinander stehen, empfiehlt es sich, ein Bereichsdiagramm zu verwenden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-stacked-and-100-stacked-charts"></a>Vewenden von gestapelten Diagrammen und gestapelten Diagrammen (100 %)  
 Gestapelte Diagramme werden häufig verwendet, um mehrere Reihen in einer Diagrammfläche anzuzeigen. Die Verwendung gestapelter Diagramme empfiehlt sich, wenn die darzustellenden Daten in enger Beziehung zueinander stehen. Darüber hinaus wird empfohlen, höchstens vier Reihen in einem gestapelten Diagramm anzuzeigen. Wenn Sie die Anteile der einzelnen Reihen in Bezug auf das Ganze vergleichen möchten, verwenden Sie ein gestapeltes Flächen-, Balken oder Säulendiagramm (100 %). In diesen Diagrammen wird der relative Prozentsatz berechnet, den die einzelnen Reihen zur Kategorie beitragen. Weitere Informationen finden Sie unter [Flächendiagramme (Berichts-Generator und SSRS)](charts-report-builder-and-ssrs.md), [Balkendiagramme (Berichts-Generator und SSRS)](bar-charts-report-builder-and-ssrs.md) und [Säulendiagramme (Berichts-Generator und SSRS)](column-charts-report-builder-and-ssrs.md).  
  
## <a name="using-the-secondary-axis"></a>Verwenden der sekundären Achse  
 Wenn dem Diagramm eine neue Reihe hinzugefügt wird, wird diese mit der primären X-Achse und Y-Achse dargestellt. Wenn Sie Werte mit verschiedenen Maßeinheiten vergleichen möchten, empfiehlt es sich, die *sekundäre Achse* zu verwenden, sodass Sie zwei Reihen auf separaten Achsen darstellen können. Die sekundäre Achse ist besonders hilfreich bei Vergleichen von Werten mit verschiedenen Maßeinheiten. Die sekundäre Achse wird auf der Seite gezeichnet, die der primären Achse gegenüberliegt. Das Diagramm unterstützt nur eine primäre und eine sekundäre Achse. Die sekundäre Achse verfügt über dieselben Eigenschaften wie die primäre Achse. Weitere Informationen finden Sie unter [Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS)](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md).  
  
 Wenn Sie mehr als zwei Reihen mit unterschiedlichen Datenbereichen anzeigen möchten, empfiehlt es sich, die Reihen in separaten Diagrammflächen zu platzieren.  
  
## <a name="using-chart-areas"></a>Verwenden von Diagrammflächen  
 Das Diagramm stellt den Container der obersten Ebene dar, der den äußeren Rahmen, den Diagrammtitel und die Legende enthält. Standardmäßig wird im Diagramm eine Diagrammfläche angezeigt. Die Diagrammfläche ist auf der Diagrammoberfläche nicht sichtbar. Sie können sich diese jedoch als Container vorstellen, in dem lediglich die Achsenbezeichnungen, der Achsentitel und der Zeichnungsbereich einer oder mehrerer Reihen enthalten sind. In der folgenden Abbildung wird das Konzept der Diagrammflächen in einem einzelnen Diagramm veranschaulicht.  
  
 ![Diagramm eines Diagrammbereichs](../media/chartareasdiagram.gif "Diagramm eines Diagrammbereichs")  
  
 Im Dialogfeld **Diagrammflächeneigenschaften** können Sie die 2D- und 3D-Ausrichtung aller auf der Diagrammfläche enthaltenen Reihen angeben, mehrere Diagrammflächen in einem Diagramm ausrichten und die Farben des Zeichnungsbereichs formatieren. Wenn eine neue Diagrammfläche in einem Diagramm definiert wird, das nur eine Standarddiagrammfläche enthält, wird der für eine Diagrammfläche verfügbare Platz horizontal durch 2 dividiert, und die neue Diagrammfläche wird unterhalb der ersten Diagrammfläche platziert.  
  
 Jede Reihe kann mit nur jeweils einer Diagrammfläche verbunden werden. Standardmäßig werden alle Reihen der Standarddiagrammfläche hinzugefügt. In Flächen-, Säulen-, Linien- und Punktdiagrammen kann in einer Diagrammfläche eine beliebige Kombination dieser Reihen angezeigt werden. Sie können beispielsweise eine Spaltenreihe und eine Linienreihe auf derselben Diagrammfläche anzeigen. Der Vorteil mehrerer Reihen auf ein und derselben Diagrammfläche besteht darin, dass Endbenutzer auf einfache Weise Vergleiche durchführen können.  
  
 Balken-, Netz- und Formdiagramme können nicht mit anderen Diagrammtypen auf derselben Diagrammfläche kombiniert werden. Wenn Sie Vergleiche mehrerer Reihen für Balken-, Netz- und Formdiagrammtypen durchführen möchten, müssen Sie einen der folgenden Vorgänge ausführen:  
  
-   Ändern Sie alle Reihen auf der Diagrammfläche, sodass diese denselben Diagrammtyp aufweisen.  
  
-   Erstellen Sie eine neue Diagrammfläche, und verschieben Sie eine oder mehrere Reihen von der Standarddiagrammfläche auf die neu erstellte Diagrammfläche.  
  
 Mehrere Diagrammflächen in einem Diagramm sind auch nützlich, wenn Sie Daten vergleichen möchten, die unterschiedliche Werteskalen aufweisen. Wenn z. B. die erste Reihe Daten im Bereich von 10 bis 20 und die zweite Reihe Daten im Bereich von 400 bis 800 enthält, werden die Werte in der ersten Reihe möglicherweise verdeckt. Es empfiehlt sich, die einzelnen Reihen in verschiedenen Diagrammflächen voneinander zu trennen. Weitere Informationen finden Sie unter [Angeben einer Diagrammfläche für eine Reihe (Berichts-Generator und SSRS)](specify-a-chart-area-for-a-series-report-builder-and-ssrs.md).  
  
## <a name="using-range-charts"></a>Verwenden von Bereichsdiagrammen  
 Bereichsdiagramme weisen zwei Werte pro Datenpunkt auf. Wenn das Diagramm zwei Reihen aufweist, die dieselbe Kategorieachse (X) verwenden, können Sie mithilfe eines Bereichsdiagramms die Differenz zwischen den beiden Reihen anzeigen. Bereichsdiagramme eignen sich optimal für die Anzeige von Hoch-Tief-Daten und Öffnungs-Schluss-Daten. Wenn die erste Reihe beispielsweise den Höchstumsatz für jeden Tag im Januar enthält, während die zweite Reihe den geringsten Umsatz für jeden Tag im Januar enthält, können Sie mithilfe eines Bereichsdiagramms die Differenz zwischen dem Höchstumsatz und dem geringsten Umsatz für jeden Tag veranschaulichen. Weitere Informationen finden Sie unter [Bereichsdiagramme (Berichts-Generator und SSRS)](range-charts-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Anzeigen einer Reihe mit mehreren Datenbereichen in einem Diagramm (Berichts-Generator und SSRS)](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)   
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)  
  
  
