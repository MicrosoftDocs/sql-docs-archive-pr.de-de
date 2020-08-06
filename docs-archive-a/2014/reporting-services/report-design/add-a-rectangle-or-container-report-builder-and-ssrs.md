---
title: Hinzufügen eines Rechtecks oder Containers (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fddda2f02b9f370d9742ae6add5bae444f8f55f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608293"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a>Hinzufügen eines Rechtecks oder Containers (Berichts-Generator und SSRS)
  Fügen Sie dem Bericht ein Rechteck hinzu, wenn Sie durch ein grafisches Element Bereiche des Berichts trennen oder hervorheben oder einen Hintergrund für ein oder mehrere Berichtselemente bereitstellen möchten. Rechtecke werden auch als Container verwendet, mit denen das Rendering von Datenbereichen in einem Bericht gesteuert werden kann. Sie können die Darstellung eines Rechtecks anpassen, indem Sie die Rechteckeigenschaften bearbeiten, z. B. den Hintergrund und die Rahmenfarben. Weitere Informationen zum Verwenden eines Rechtecks als Container finden Sie unter [Rechtecke und Linien (Berichts-Generator und SSRS)](rectangles-and-lines-report-builder-and-ssrs.md) und [Anzeigen derselben Daten in einer Matrix und einem Diagramm (Berichts-Generator)](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a>So fügen Sie ein Rechteck hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Berichtselemente** auf **Rechteck**.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf die Stelle, an der die obere linke Ecke des Rechtecks positioniert werden soll, und ziehen Sie den Mauszeiger an die Stelle, an der die untere rechte Ecke des Rechtecks positioniert werden soll.  
  
     Während Sie den Cursor bewegen, werden "Ausrichtungslinien" angezeigt, wenn der Cursor mit anderen Objekten auf der Entwurfsoberfläche ausgerichtet ist. Mit diesen Ausrichtungslinien können Sie die Objekte besser ausrichten.  
  
### <a name="to-create-a-container"></a>So erstellen Sie einen Container  
  
1.  Fügen Sie dem Bericht ein Rechteckberichtsobjekt hinzu.  
  
2.  Ziehen Sie andere Berichtselemente in das Rechteck.  
  
    > [!NOTE]  
    >  Ein Rechteck ist lediglich ein Container für Elemente, die Sie im Rechteck erstellen oder in das Rechteck ziehen. Wenn Sie ein Rechteck um ein Element zeichnen, das bereits auf der Entwurfsoberfläche vorhanden ist, fungiert das Rechteck nicht als Container.  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a>So ändern Sie Rechteckeigenschaften, z. B. Farbe, Format oder Gewichtung  
  
1.  Wählen Sie das Rechteck aus, und klicken Sie auf die Optionen für Linienfarbe, Format oder Gewichtung im Abschnitt **Rahmen** der Registerkarte Home.  
  
2.  Klicken Sie auf den Pfeil neben der Schaltfläche **Rahmen** , um zu bestimmen, welche Seiten des Rechtecks geändert werden sollen.  
  
    > [!NOTE]  
    >  Wenn Sie die Linienart auf **Double** festlegen und die Linienstärke 1 1/2 pt oder schmaler ist, wird die Linie möglicherweise nicht doppelt angezeigt, wenn Sie den Bericht in Berichts-Generator, Berichts-Designer oder Berichts-Manager ausführen. Sie wird doppelt angezeigt, wenn Sie den Bericht in andere Formate wie Microsoft Word oder Acrobat PDF exportieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
