---
title: Angeben eines Achsenintervalls (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b64b824933753a8482360f193ca4ccf71e8d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608270"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a>Angeben eines Achsenintervalls (Berichts-Generator und SSRS)
  Das Achsenintervall definiert die Anzahl von Bezeichnungen und zugehörigen Teilstrichen auf einer Achse. Auf der Wertachse stellen die Achsenintervalle ein konsistentes Maß für die Datenpunkte im Diagramm bereit. Auf der Kategorieachse kann diese Funktion jedoch bewirken, dass Kategorien ohne Achsenbezeichnungen angezeigt werden. Sie können die Anzahl der Intervalle in der Interval-Eigenschaft der Achse festlegen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] berechnet die Anzahl der Intervalle zur Laufzeit basierend auf den Daten im Resultset. Weitere Informationen zum Berechnen von Achsenintervallen finden Sie unter [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  
  
 Dieses Thema gilt nicht für Datums- oder Zeitwerte auf der Kategorieachse. Standardmäßig werden `DateTime`-Werte als Tage angezeigt. Wenn Sie ein anderes Datums- oder Zeitintervall angeben möchten, z. B. ein Monats- oder Zeitintervall, müssen Sie die Achsenbezeichnungen formatieren und die Achse auf die Anzeige von Instanzen von `DateTime`-Typen statt von `String`-Typen festlegen. Darüber hinaus müssen Sie die Interval-Eigenschaft festlegen. Weitere Informationen finden Sie unter [Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung &#40;Berichts-Generator und SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).  
  
 Dieses Thema gilt nicht für Kreis-, Ring-, Trichter- oder Pyramidendiagramme, die keine Achsen haben.  
  
> [!NOTE]  
>  Die Kategorieachse ist normalerweise die horizontale Achse oder x-Achse. Bei Balkendiagrammen ist die Kategorieachse jedoch die vertikale Achse oder y-Achse.  
  
 Ein Beispiel für ein Diagramm, in dem andere Achsenintervalle angegeben werden, ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a>So zeigen Sie alle Kategoriebezeichnungen auf der X-Achse an  
  
1.  Klicken Sie mit der rechten Maustaste auf die Kategorieachse, und klicken Sie auf **Achseneigenschaften**. Das Dialogfeld **Achseneigenschaften** wird angezeigt.  
  
2.  Legen Sie unter **Achsen Optionen** `Interval` auf **1**fest. Jede Kategoriegruppenbezeichnung wird angezeigt. Wenn Sie jede zweite Kategoriegruppenbezeichnung auf der X-Achse anzeigen möchten, geben Sie **2**ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Wenn ein Achsenintervall festgelegt wird, wird die automatische Kennzeichnung deaktiviert. Wenn Sie einen Wert für das Achsenintervall angeben, kann es je nach Anzahl der Kategorien auf der Kategorieachse zu unerwartetem Kennzeichnungsverhalten kommen.  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a>So aktivieren Sie eine variable Intervallberechnung auf einer Achse  
  
1.  Klicken Sie mit der rechten Maustaste auf die Diagrammachse, die Sie ändern möchten, und klicken Sie dann auf **Achseneigenschaften**. Das Dialogfeld **Achseneigenschaften** wird angezeigt.  
  
2.  Legen Sie unter **Achsen Optionen die Option** `Interval` auf **automatisch**fest. Im Diagramm wird die optimale Anzahl von Kategoriebezeichnungen angezeigt, die auf die Achse passen.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Sortieren von Daten in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Achsen Eigenschaften (Dialog Feld), Achsen Optionen &#40;Berichts-Generator und SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [Geben Sie eine logarithmische Skalierung &#40;Berichts-Generator und SSRS an&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Zeichnen von Daten auf einer sekundären Achse (Berichts-Generator und SSRS)](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
