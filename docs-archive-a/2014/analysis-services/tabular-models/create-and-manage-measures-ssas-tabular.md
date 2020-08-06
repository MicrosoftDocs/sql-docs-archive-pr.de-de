---
title: Erstellen und Verwalten von Measures (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
author: minewiskan
ms.author: owend
ms.openlocfilehash: da507bf48b285a1414ffb85ba79da50508a2ae2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616209"
---
# <a name="create-and-manage-measures-ssas-tabular"></a>Erstellen und Verwalten von Measures (SSAS – tabellarisch)
  Ein Measure ist eine Formel, die zur Verwendung in einem Bericht oder einer PivotTable (oder einem PivotChart) von Excel erstellt wird. Measures können auf Standardaggregationsfunktionen basieren, z. B. COUNT oder SUM, oder Sie können mit DAX eigene Formeln definieren. In den Tasks in diesem Thema wird beschrieben, wie Measures mithilfe des measurerasters einer Tabelle erstellt und verwaltet werden.  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So erstellen Sie ein Measure mithilfe einer Standardaggregationsformel](#bkmk_create_stand)  
  
-   [So erstellen Sie ein Measure mithilfe einer benutzerdefinierten Formel](#bkmk_create_custom)  
  
-   [So bearbeiten Sie Measure-Eigenschaften](#bkmk_edit)  
  
-   [So benennen Sie ein Measure um](#bkmk_rename)  
  
-   [So löschen Sie ein Measure](#bkmk_delete)  
  
## <a name="tasks"></a>Aufgaben  
 Zum Erstellen und Verwalten von Measures verwenden Sie das measureraster einer Tabelle. Sie können das Measureraster für eine Tabelle nur in der Datensicht des Modell-Designers anzeigen. In der Diagrammsicht können Sie keine Measures erstellen und kein Measureraster anzeigen. Vorhandene Measures können in der Diagrammsicht jedoch angezeigt werden. Um das Measureraster für eine Tabelle anzuzeigen, klicken Sie auf das Menü **Tabelle** und dann auf **Measureraster anzeigen**.  
  
###  <a name="to-create-a-measure-using-a-standard-aggregation-formula"></a><a name="bkmk_create_stand"></a>So erstellen Sie ein Measure mithilfe einer Standard Aggregations Formel  
  
-   Klicken Sie auf die Spalte, für die Sie das Measure erstellen möchten, klicken Sie dann auf das Menü **Spalte** , zeigen Sie auf **AutoSumme**, und klicken Sie dann auf einen Aggregationstyp.  
  
     Das Measure wird automatisch mit einem Standardnamen erstellt, gefolgt von der Formel in der ersten Zelle im Measureraster direkt unterhalb der Spalte.  
  
###  <a name="to-create-a-measure-using-a-custom-formula"></a><a name="bkmk_create_custom"></a> So erstellen Sie ein Measure mithilfe einer benutzerdefinierten Formel  
  
-   Klicken Sie im Measureraster unter der Spalte, für die Sie das Measure erstellen möchten, auf eine Zelle, und geben Sie dann in der Bearbeitungsleiste einen Namen gefolgt von einem Doppelpunkt (:), einem Gleichheitszeichen (=) und der Formel ein. Drücken Sie die EINGABETASTE, um die Formel zu übernehmen.  
  
###  <a name="to-edit-measure-properties"></a><a name="bkmk_edit"></a> So bearbeiten Sie Measureeigenschaften  
  
-   Klicken Sie im Measureraster auf ein Measure, und geben Sie dann im Fenster **Eigenschaften** einen anderen Eigenschaftswert ein, oder wählen Sie ihn aus.  
  
###  <a name="to-rename-a-measure"></a><a name="bkmk_rename"></a> So benennen Sie ein Measure um  
  
-   Klicken Sie im Measureraster auf ein Measure, und geben Sie dann im Fenster **Eigenschaften** in **Measurename**einen neuen Namen ein, und drücken Sie die EINGABETASTE.  
  
     Sie können ein Measure auch in der Bearbeitungsleiste umbenennen. Der Measurename ist der Formel gefolgt von einem Doppelpunkt vorangestellt.  
  
###  <a name="to-delete-a-measure"></a><a name="bkmk_delete"></a>So löschen Sie ein Measure  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf ein Measure, und klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Measures &#40;tabellarischen SSAS-&#41;](measures-ssas-tabular.md)   
 [KPIs &#40;tabellarischen SSAS-&#41;](kpis-ssas-tabular.md)   
 [Berechnete Spalten &#40;SSAS – tabellarisch&#41;](ssas-calculated-columns.md)  
  
  
