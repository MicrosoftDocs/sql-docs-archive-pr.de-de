---
title: Hinzufügen, ändern oder Löschen von Standardwerten für einen Berichts Parameter (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10460"
- sql12.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d50fdbbe42a656ef839785c0968b36c8c829e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617761"
---
# <a name="add-change-or-delete-default-values-for-a-report-parameter-report-builder-and-ssrs"></a>Hinzufügen, Ändern oder Löschen von Standardwerten für einen Berichtsparameter (Berichts-Generator und SSRS)
  Nachdem Sie einen Berichtsparameter erstellt haben, können Sie eine Liste mit Standardwerten bereitstellen. Wenn alle Parameter über einen gültigen Standardwert verfügen, wird der Bericht beim ersten Anzeigen bzw. bei der ersten Vorschau automatisch ausgeführt.  
  
 Berichtsparameter können einen Wert oder mehrere Werte darstellen. Für einzelne Werte können Sie ein Literal oder einen Ausdruck bereitstellen. Für mehrere Werte können Sie eine statische Liste oder eine Liste anhand eines Berichtsdatasets bereitstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Nachdem ein Bericht veröffentlicht wurde, können Sie die Standardwerte, die Sie im Bericht im Berichterstellungstool definieren, durch Festlegen von Parametereigenschaftswerten auf dem Berichtsserver überschreiben. Sie können auch mehrere Gruppen von Standardparameterwerten bereitstellen, indem Sie verknüpfte Berichte erstellen. Weitere Informationen finden Sie unter  [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a>So fügen Sie die Standardwerte für einen Berichtsparameter hinzu bzw. ändern diese  
  
1.  Erweitern Sie im Berichtsdatenbereich den Knoten **Parameter** . Klicken Sie mit der rechten Maustaste auf den Parameter, und klicken Sie anschließend auf **Bearbeiten**. Das Dialogfeld **Berichtsparametereigenschaften** wird geöffnet.  
  
    > [!NOTE]  
    >  Zum Anzeigen des Berichtsdatenbereichs klicken Sie im Menü **Ansicht** auf **Berichtsdaten**.  
  
2.  Klicken Sie auf **Standardwerte**.  
  
3.  Wählen Sie eine Standardoption:  
  
    -   Klicken Sie auf **Werte angeben**, um manuell einen Wert oder eine Liste mit Werten bereitzustellen. Klicken Sie auf **Hinzufügen** , und geben Sie den Wert in das Textfeld **Wert** ein. Sie können einen Ausdruck für einen Wert schreiben. Der Datentyp muss mit dem Datentyp des Parameters übereinstimmen. In einem Ausdruck für einen Parameter können keine Feldnamen verwendet werden.  
  
         Wiederholen Sie diesen Schritt bei Parametern mit mehreren Werten entsprechend der Anzahl der Werte, die Sie bereitstellen möchten. Die Reihenfolge der in dieser Liste angezeigten Elemente bestimmt die Reihenfolge, die Benutzer in der Dropdownliste sehen. Wenn Sie die Position eines Elements in der Liste ändern möchten, klicken Sie auf das Textfeld **Wert** , um das Element auszuwählen. Bewegen Sie das Element dann mit den Nach-oben- und Nach-unten-Pfeilen in der Liste nach oben bzw. nach unten.  
  
    -   Klicken Sie auf **Werte aus Abfrage abrufen**, um den Namen eines vorhandenen Datasets bereitzustellen, mit dem die Werte abgerufen werden. Wählen Sie unter **Dataset**den Namen des Datasets aus.  
  
         Wählen Sie unter **Wertfeld**den Namen des Felds aus, das Parameterwerte bereitstellt.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a>So entfernen Sie die Standardwerte für einen Berichtsparameter  
  
1.  Erweitern Sie im Berichtsdatenbereich den Knoten **Parameter** . Klicken Sie mit der rechten Maustaste auf den Parameter, und klicken Sie anschließend auf **Bearbeiten**. Das Dialogfeld **Berichtsparametereigenschaften** wird geöffnet.  
  
2.  Klicken Sie auf **Standardwerte**.  
  
3.  Klicken Sie unter **Wählen Sie eine der folgenden Optionen aus**auf **Kein Standardwert**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Hinzufügen von kaskadierenden Parametern zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Tutorial: Add a Parameter to Your Report (Report Builder) (Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator))](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Parameters Collection References (Report Builder and SSRS) (Verweise auf Parameterauflistungen (Berichts-Generator und SSRS))](built-in-collections-parameters-collection-references-report-builder.md)   
 [Ändern der Reihenfolge von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Hinzufügen, Ändern oder Löschen von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
  
