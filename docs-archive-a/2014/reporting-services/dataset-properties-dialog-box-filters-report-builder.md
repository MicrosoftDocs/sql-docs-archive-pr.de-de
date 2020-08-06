---
title: Dataseteigenschaften (Dialog Feld), Filter (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bc13b0eeff1eaf27fb0ec0c4279ff00d0809e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609736"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a>Dataseteigenschaften (Dialogfeld), Filter (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Filter** aus, um Filter für das Dataset zu erstellen.  
  
 Filter, die Teil einer freigegebenen Datasetdefinition auf dem Berichtsserver sind, wirken sich auf alle Berichte aus, die das freigegebene Dataset verwenden. Zusätzliche Filter für das freigegebene Dataset können angegeben werden, nachdem es einem Bericht hinzugefügt wurde. Diese Filter wirken sich nur auf Berichte aus, in denen sie definiert sind.  
  
 Filter für ein eingebettetes Dataset wirken sich nur auf Berichte aus, in denen sie definiert sind.  
  
 Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Add (Hinzufügen)**  
 Fügt eine neue Filterklausel zur Liste hinzu.  
  
 **Löschen**  
 Löscht die ausgewählte Filterklausel aus der Liste.  
  
 **Pfeil nach oben**  
 Verschiebt den ausgewählten Filter in der Liste nach oben.  
  
 **Pfeil nach unten**  
 Verschiebt den ausgewählten Filter in der Liste nach unten.  
  
 **Ausdruck**  
 Geben Sie den Ausdruck ein, auf den ein Filter angewendet werden soll, oder wählen Sie ihn aus. Klicken Sie auf die Ausdrucks Schaltfläche (**FX**), um den Ausdruck zu bearbeiten.  
  
 **Datentyp**  
 Wählen Sie den Datentyp für **Wert**. Wählen Sie, sofern möglich, einen Datentyp aus, der dem Datentyp für **Ausdruck**entspricht.  
  
 Die Werte in **Ausdruck** und **Wert** müssen mit dem gleichen Datentyp ausgewertet werden. Wenn **Ausdruck** beispielsweise auf ein Feld mit dem Datentyp „System.Int32“ festgelegt ist und **Wert** auf 7 festgelegt ist, wählen Sie aus der Dropdownliste den Wert **Ganze Zahl**.  
  
 Wenn die benötigte Datentyp-Option nicht in der Dropdownliste aufgeführt wird, erstellen Sie einen Ausdruck, um den Wert in den richtigen Datentyp zu konvertieren. Weitere Informationen finden Sie unter [Beispiele für Filtergleichungen &#40;Berichts-Generator und SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
 **Operator**  
 Wählen Sie den Operator aus, der zum Vergleichen des Ausdrucks und des Werts verwendet werden soll.  
  
 **Wert**  
 Geben Sie den Ausdruck oder Wert ein, der beim Auswerten des im Feld **Ausdruck** angegebenen Ausdrucks verwendet werden soll. Klicken Sie auf die Ausdrucks Schaltfläche (**FX**), um den Ausdruck zu bearbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Melden Sie eingebettete Datasets und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Berichts Parameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Hinzufügen eines Filters zu einem DataSet &#40;Berichts-Generator und SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)   
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
