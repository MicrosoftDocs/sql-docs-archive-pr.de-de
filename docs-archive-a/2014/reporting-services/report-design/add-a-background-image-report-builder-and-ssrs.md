---
title: Hinzufügen eines Hintergrundbilds (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7bc15e1b063a73c463cdb1e7e99075af2a3dce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723489"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a>Hinzufügen eines Hintergrundbilds (Berichts-Generator und SSRS)
  Sie können einem Berichtselement, z. B. einem Rechteck, Textfeld, einer Liste, Matrix, Tabelle und einigen Teilen eines Diagramms, oder einem Berichtsabschnitt, z. B. dem Seitenkopf, Seitenfuß oder Berichtshauptteil, ein Hintergrundbild hinzufügen. Sie können ein Hintergrundbild für jedes ausgewählte Element in der Berichtsentwurfsoberfläche definieren, für das **BackgroundImage** im Bereich Eigenschaften angezeigt wird. Bei dem Hintergrundbild kann es sich wie bei anderen Bildern um eine URL zu einem Bild auf dem Berichtsserver handeln, ein Bild aus einem Datasetfeld oder ein in die Berichtsdefinition eingebettetes Bild. Wenn Sie ein in den Bericht eingebettetes Bild verwenden möchten, müssen Sie es der Berichtsdefinition hinzufügen, bevor Sie es der Entwurfsoberfläche hinzufügen können.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a>So betten Sie ein Bild in die Berichtsdefinition ein  
  
1.  Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf den Knoten **Bilder** , und klicken Sie dann auf **Bild hinzufügen**.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie auf der Registerkarte **Ansicht** auf **Berichtsdaten**.  
  
2.  Navigieren Sie zu dem Bild, das Sie in die Berichtsdefinition einbetten möchten, und klicken Sie dann auf **OK**.  
  
### <a name="to-add-a-background-image"></a>So fügen Sie ein Hintergrundbild hinzu  
  
1.  Wählen Sie in der Berichtsentwurfsansicht das Berichtselement aus, dem Sie ein Hintergrundbild hinzufügen möchten.  
  
2.  Klicken Sie auf der Registerkarte **Ansicht** auf **Eigenschaften**, falls der Bereich "Eigenschaften" nicht angezeigt wird.  
  
3.  Erweitern Sie im Bereich "Eigenschaften" die **BackgroundImage**-Eigenschaft, und führen Sie dann die folgenden Schritte aus:  
  
    -   Eingebettetes Bild:  
  
         Legen Sie **Source** auf **Embedded**fest.  
  
         Legen Sie für **Value** den Namen eines Bilds fest, das in den Bericht eingebettet ist.  
  
    -   Externes Bild:  
  
         Legen Sie **Source** auf **External**fest.  
  
         Legen Sie für **Value** einen gültigen Pfad zu einem Bild fest. Dieses kann sich auf einem Berichtsserver im einheitlichen Modus oder im integrierten SharePoint-Modus bzw. auf einer beliebigen anderen Website befinden. Weitere Informationen finden Sie unter [Hinzufügen eines externen Bilds (Berichts-Generator und SSRS)](add-an-external-image-report-builder-and-ssrs.md).  
  
    -   Bild, das in einem Feld in der Datenbank enthalten ist, mit der das Berichtselement verbunden ist:  
  
         Legen Sie **Source** auf **Database**fest.  
  
         Legen Sie für **Value** den Namen eines Felds im Berichtsdataset fest. Weitere Informationen finden Sie unter [Hinzufügen eines datengebundenen Bilds (Berichts-Generator und SSRS)](add-a-data-bound-image-report-builder-and-ssrs.md).  
  
         Wählen Sie für **MIMEType** oder als Dateiformat den entsprechenden MIME-Typ für das Bild aus, beispielsweise BMP.  
  
        > [!NOTE]  
        >  Die MIMEType-Eigenschaft trifft nur dann zu, wenn die **Source** -Eigenschaft auf **Database**festgelegt ist. Wenn die **Source** -Eigenschaft auf **External** oder **Embedded**festgelegt ist, wird der Wert von **MIMEType** ignoriert.  
  
    -   Wählen Sie für **BackgroundRepeat**einen Ausdruck, **Default**, **Repeat**, **RepeatX**, **RepeatY**oder **Clip**aus.  
  
         Für Hintergrundbilder in einem Diagramm kann **BackgroundRepeat** auf **Default**, **Repeat**, **Fit**und **Clip**festgelegt werden, jedoch nicht auf **RepeatX** oder **RepeatY**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bilder &#40;Berichts-Generator und SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
