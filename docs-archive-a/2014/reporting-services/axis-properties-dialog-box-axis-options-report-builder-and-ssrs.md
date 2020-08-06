---
title: Dialog Feld "Achsen Eigenschaften", "Achsen Optionen" (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617816"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a>Achseneigenschaften (Dialogfeld), Achsenoptionen (Berichts-Generator und SSRS)
  Wählen Sie im Dialogfeld Eigenschaften für **horizontale** oder **verticalaxis** die **Option Achsen Optionen** aus, um die Darstellung der angegebenen Achse im Diagramm zu definieren. In älteren Versionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]wurden standardmäßig alle Bezeichnungen auf der x-Achse angezeigt. Ab Version [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008 werden Bezeichnungen ggf. übersprungen, um ein übersichtlicheres Bild zu erzielen und sich überlappende Beschriftungen zum vermeiden. Weitere Informationen finden Sie unter [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Skalierungsunterbrechungen aktivieren**  
 Wählen Sie diese Option aus, damit das Diagramm bei Bedarf Skalierungsunterbrechungen zeichnen kann. Wenn diese Option aktiviert ist, berechnet das Diagramm automatisch, ob genügend Unterschied zwischen den oberen und unteren Punkten des Datasets besteht, um eine Skalierungsunterbrechung zu zeichnen.  
  
 **Richtung umkehren**  
 Wählen Sie diese Option aus, um die Richtung des Diagramms umzukehren. Standardmäßig wird z. B. in einem Spaltendiagramm die Y-Achse auf der linken Seite des Diagramms angezeigt, während Kategorien von links nach rechts angezeigt werden. Wenn diese Option aktiviert ist, wird die Y-Achse im Diagramm auf der rechten Seite angezeigt; Kategorien werden von rechts nach links angezeigt.  
  
 **Zeilensprungfarbe verwenden**  
 Aktivieren Sie diese Option, um dem Diagramm Bereichsstreifen hinzuzufügen, und wählen Sie dann eine Farbe aus, oder geben Sie einen Ausdruck ein. Bereichsstreifen sind schattierte Bänder in der Diagrammfläche, die abwechselnd helle und dunkle Bereiche zwischen Gitternetzlinien ergeben. Diese Bereichsstreifen sind nützlich, um Wiederholungsmuster auf einer Achse hervorzuheben.  
  
 **Null immer einschließen**  
 Wählen Sie diese Option, um 0 (null) immer auf der Achsenskala einzuschließen. Wenn diese Option nicht aktiviert wird, wird der Nullwert auf der Achse nicht beschriftet. Den Nullwert einzuschließen ist nützlich, wenn das Dataset negative oder Nullwerte enthält.  
  
 **Skalare Achse**  
 Wählen Sie diese Option, um einen Satz von Achsenwerten über eine fortlaufende Skala anzuzeigen. Wenn das Dataset beispielsweise Daten für Januar, März und November enthält, zeigt eine Nicht-Skalarachse nur diese Monate an, während eine Skalarachse alle Monate des Jahrs anzeigt.  
  
 **Logarithmische Skalierung verwenden**  
 Wählen Sie diese Option aus, um anzugeben, dass die Achsenskalierung logarithmisch ist. Diese Option ist nur auf der Y-Achse verfügbar, wenn die Achse positive numerische Werte enthält.  
  
 Geben Sie die zu verwendende logarithmische Basis in das Feld ein, wenn für die Achse die Verwendung einer logarithmischen Skala festgelegt wurde. Standardmäßig verwendet das Diagramm eine Basis von 10 für die logarithmische Skalierung einer Achse. Diese Option ist nur auf der Y-Achse verfügbar, wenn die Achse numerische Werte enthält.  
  
 **Mindestanforderungen**  
 Geben Sie einen Ausdruck oder einen Wert für den Minimalwert für die X-Achse ein. Falls kein Wert angegeben ist, wird der Minimalwert durch die Daten bestimmt, die durch das Dataset zurückgegeben werden.  
  
 **Maximum**  
 Geben Sie einen Ausdruck oder einen Wert für den Maximalwert für die X-Achse ein. Falls kein Wert angegeben ist, wird der Maximalwert durch die Daten bestimmt, die durch das Dataset zurückgegeben werden.  
  
 **Intervall**  
 Geben Sie einen Ausdruck oder einen Wert für das Intervall zwischen den Achsenbeschriftungen ein. Geben Sie z. B. 1 ein, damit jede Kategoriebezeichnung auf der Achse angezeigt wird. Geben Sie 2 ein, um nur jede zweite Kategoriebezeichnung anzuzeigen. Falls kein Wert angegeben wird, werden die Bezeichnungen automatisch anhand der Werte im Dataset berechnet.  
  
 **Intervalltyp**  
 Geben Sie einen Ausdruck oder einen Wert für den Intervalltyp des angegebenen Intervalls ein. Wenn das Intervall beispielsweise zwei Tage betragen soll, geben Sie **2** für das Intervall und **Tage** für den Intervalltyp ein.  
  
 **Seitenränder**  
 Geben Sie einen Ausdruck ein, oder wählen Sie einen Wert aus, um einen Rand zwischen den Diagrammelementen und den Seiten des Diagramms hinzuzufügen bzw. zu entfernen. Wenn diese Option auf **Automatisch**festgelegt wird, werden Seitenränder hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Achsen Bezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Formatieren von Reihen Farben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Angeben eines Achsen Intervalls &#40;Berichts-Generator und SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Formatieren von Achsen Bezeichnungen als Datumsangaben oder Währungen &#40;Berichts-Generator und SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Zeichnen von Daten auf einer sekundären Achse &#40;Berichts-Generator und SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)   
 [Sparklines und Daten Balken &#40;Berichts-Generator und SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)   
 [Hinzufügen oder Entfernen von Rändern aus einem Diagramm &#40;Berichts-Generator und SSRS&#41;](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
