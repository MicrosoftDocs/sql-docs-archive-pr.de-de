---
title: Durchsuchen eines Modells mit dem Microsoft Sequence Cluster-Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Sequence Cluster Viewer
- clusters [Analysis Services]
- data mining [Analysis Services], sequences
- discrimination [Analysis Services]
- mining model content, viewing
- mining models [Analysis Services], sequences
- Microsoft Sequence Cluster Viewer
- sequence [Analysis Services]
- transitions [Analysis Services]
ms.assetid: 3ada00aa-da9e-488a-9f53-c3e188f81f84
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6e2c95a08f293dad8793ba5d4367753ae2c6db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630437"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a>Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer
  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequenz Cluster-Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zeigt Mining Modelle an, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering-Algorithmus erstellt wurden. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering-Algorithmus ist ein Algorithmus für die Sequenzanalyse, der zum Durchsuchen von Daten verwendet wird, und der Ereignisse enthält, die durch folgende Pfade oder *Sequenzen*verknüpft werden können. Weitere Informationen zu diesem Algorithmus finden Sie unter [Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm.md).  
  
> [!NOTE]  
>  Wenn Sie detaillierte Informationen über die im Modell verwendeten Formeln und die entdeckten Muster sehen möchten, verwenden Sie den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree-Viewer. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) oder [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).  
  
> [!NOTE]  
>  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster-Viewer bietet Funktionalitäten und Optionen, die denen des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster-Viewer ähnlich sind. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md).  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a>Viewer-Registerkarten  
 Wenn Sie ein Miningmodell in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]durchsuchen, wird das Modell im Data Mining-Designer auf der Registerkarte **Miningmodell-Viewer** mit dem jeweils geeigneten Viewer für das Modell angezeigt. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequenzcluster-Viewer bietet die folgenden Registerkarten zum Durchsuchen von Sequenzcluster-Miningmodellen:  
  
-   [Clusterdiagramm](#BKMK_Diagram)  
  
-   [Clusterprofile](#BKMK_Profile)  
  
-   [Cluster Merkmale](#BKMK_Characteristics)  
  
-   [Clusterunterscheidung](#BKMK_Discrimination)  
  
-   [Cluster Übergänge](#BKMK_Transitions)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a>Cluster Diagramm  
 Die Registerkarte **Clusterdiagramm** des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequenzcluster-Viewers zeigt alle in einem Miningmodell enthaltenen Cluster an. Die Schattierung der Linie, die einen Cluster mit einem anderen verbindet, stellt die Ähnlichkeit der Cluster dar. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich. Je stärker die Linie wird, umso mehr ähneln sich die Links. Sie können die Anzahl der im Viewer angezeigten Linien mithilfe des Schiebereglers rechts neben den Clustern anpassen. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Links angezeigt.  
  
 Standardmäßig stellt die Schattierung die Auffüllung des Clusters dar. Mithilfe der Optionen " **shadingvariable** " und " **State** " können Sie auswählen, welches Attribut-und Status paar die Schattierung darstellt. Je stärker die Schattierung ist, umso größer ist die Attributverteilung für einen bestimmten Status. Die Verteilung wird geringer, wenn die Schattierung schwächer wird.  
  
 Klicken Sie zum Umbenennen eines Clusters mit der rechten Maustaste auf den Clusterknoten, und wählen Sie **Cluster umbenennen**aus. Der neue Name wird auf dem Server persistent gespeichert.  
  
 Klicken Sie auf **Diagrammsicht kopieren**, um den sichtbaren Abschnitt des Diagramms in die Zwischenablage zu kopieren. Klicken Sie auf **Gesamtes Diagramm kopieren**, um das gesamte Diagramm zu kopieren. Sie können auch mit **Vergrößern** und **Verkleinern**das Diagramm vergrößern oder verkleinern oder mit **Diagramm an Fenstergröße anpassen**das Diagramm an den Bildschirm anpassen.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a>Cluster profile  
 Die Registerkarte **Clusterprofil** bietet eine Übersicht der Cluster, die der Algorithmus in Ihrem Modell erstellt. Jede Spalte, die der Spalte **Auffüllung** im Raster folgt, stellt einen vom Modell ermittelten Cluster dar. Die \<attribute> Zeile. Samples stellt verschiedene Datensequenzen dar, die im Cluster vorhanden sind, und die \<attribute> Zeile beschreibt alle Elemente, die der Cluster enthält, sowie ihre Gesamtverteilung.  
  
 Mit der Option **Histogrammbalken** wird die Anzahl der im Histogramm sichtbaren Balken gesteuert. Sind mehr Balken vorhanden, als Sie zum Anzeigen ausgewählt haben, werden die wichtigsten Balken beibehalten. Die restlichen Balken werden dabei in einem grauen Bucket zusammengruppiert.  
  
 Sie können die Standardnamen der Cluster ändern, um aussagekräftige Namen bereitzustellen. Benennen Sie einen Cluster um, indem Sie mit der rechten Maustaste auf die Spaltenüberschrift des Clusters klicken und **Cluster umbenennen**auswählen. Sie können Cluster ausblenden, indem Sie **Spalte ausblenden**auswählen. Sie können auch Spalten an andere Positionen ziehen, um diese im Viewer neu zu ordnen.  
  
 Doppelklicken Sie entweder auf eine Zelle in der **Status** -Spalte oder auf ein Histogramm im Viewer, um ein Fenster zu öffnen, das eine größere, detailliertere Ansicht der Cluster bietet.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> Clustermerkmale  
 Wählen Sie zum Verwenden der Registerkarte **Clustermerkmale** in der Liste **Cluster** einen Cluster aus. Nachdem Sie einen Cluster ausgewählt haben, können Sie die Merkmale dieses bestimmten Clusters überprüfen. Die im Cluster enthaltenen Attribute werden in den **Variablen** -Spalten und der Status der aufgelisteten Attribute in der **Werte** -Spalte aufgelistet. Attributstatus werden in der Reihenfolge ihrer Wichtigkeit aufgelistet und durch die Wahrscheinlichkeit, dass sie im Cluster angezeigt werden, beschrieben. Die Wahrscheinlichkeit wird in der Spalte **Wahrscheinlichkeit** angezeigt.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a>Cluster Unterscheidung  
 Sie können die Registerkarte **Clusterunterscheidung** verwenden, um die Attribute zwischen zwei Clustern zu vergleichen, um festzustellen, wie die Elemente einer Sequenz bestimmte Cluster vor anderen bevorzugen. Verwenden Sie die Listen **Cluster 1** und **Cluster 2** , um die zu vergleichenden Cluster auszuwählen. Der Viewer bestimmt die wichtigsten Unterschiede zwischen den Clustern und zeigt die Attributstatus, die den Unterschieden zugeordnet sind, nach der Reihenfolge der Wichtigkeit an. Ein Balken rechts neben dem Attribut zeigt an, welchen Cluster der Status bevorzugt; die Größe des Balkens zeigt dabei an, wie stark der Status den Cluster bevorzugt.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="cluster-transitions"></a><a name="BKMK_Transitions"></a> Clusterübergänge  
 Sie können die Übergänge zwischen Sequenzstatus in einem ausgewählten Cluster durchsuchen, indem Sie auf der Registerkarte **Clusterübergänge** einen Cluster auswählen. Jeder Knoten im Viewer stellt einen Status der Sequenzspalte dar. Ein Pfeil stellt einen Übergang zwischen zwei Status dar, und die Wahrscheinlichkeit, dass dieser einem Übergang zugeordnet ist. Ein Pfeil kann zum Ausgangsknoten zurückverweisen, wenn ein Übergang zum Ausgangsknoten zurückkehrt.  
  
 Ein aus einem Punkt stammender Pfeil stellt die Wahrscheinlichkeit dar, dass der Knoten der Anfang einer Sequenz ist. Eine abschließende Kante, die zu einer Null führt, stellt die Wahrscheinlichkeit dar, dass der Knoten das Ende der Sequenz ist.  
  
 Sie können die Knotenkante mithilfe des Schiebereglers, der sich links von der Registerkarte befindet, filtern.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tasks und Anleitungen des Mining Modell-Viewers](mining-model-viewer-tasks-and-how-tos.md)   
 [Tasks und Anleitungen des Mining Modell-Viewers](mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm.md)   
 [Data Mining-Tools](data-mining-tools.md)   
 [Viewer für Data Mining-Modelle](data-mining-model-viewers.md)   
 [Durchsuchen eines Modells mit dem Microsoft Cluster-Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
