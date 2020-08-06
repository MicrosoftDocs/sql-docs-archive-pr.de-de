---
title: Ändern der Eigenschaften eines Mining Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608931"
---
# <a name="change-the-properties-of-a-mining-model"></a>Ändern der Eigenschaften eines Miningmodells
  Einige Miningmodelleigenschaften gelten für das gesamte Modell, wohingegen andere Modelleigenschaften für einzelne Spalten gelten. Beispiele von Eigenschaften, die für das gesamte Modell gelten, sind die `Drillthrough`-Eigenschaft, die angibt, ob die Falldaten für Abfragen verfügbar sein sollen, und die `Description`-Eigenschaft. Eigenschaften, die für die Spalte gültig sind, schließen `Usage` und `ModelingFlags` ein, die steuern, wie Daten in der Spalte im Modell verwendet werden.  
  
 Die folgenden Modelleigenschaften besitzen erweiterte Editor-Programme, mit denen Ausdrücke erstellt oder komplexe Modelleigenschaften konfiguriert werden können. Funktionen der folgenden Eigenschaften:  
  
-   `Filter`Property: öffnet das [Dialog Feld Datasetfilter oder Modell Filter](../data-set-filter-or-model-filter-dialog-box.md).  
  
-   `AlgorithmParameters`Property: öffnet das [Dialog Feld Algorithmusparameter, &#40;Mining Modell Ansicht&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).  
  
 Informationen zum Festlegen der Eigenschaften eines Miningmodells finden Sie unter [Miningmodellspalten](mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>So ändern Sie die Eigenschaften eines Miningmodells  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste entweder auf den Spaltenheader, der den Namen des Miningmodells enthält, oder auf die Zeile des Rasters mit dem Namen des Miningalgorithmus. Wählen Sie anschließend **Eigenschaften**aus.  
  
2.  Wählen Sie im Fenster **Eigenschaften** auf der rechten Seite des Bildschirms den Wert aus, der der Eigenschaft entspricht, die Sie ändern möchten, und geben Sie dann den neuen Wert ein.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>So ändern Sie die Eigenschaften einer Miningmodellspalte  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf die Zelle des Rasters im Schnittpunkt zwischen Miningstrukturspalte und Miningmodell. Wählen Sie anschließend **Eigenschaften**aus.  
  
2.  Wählen Sie im Fenster **Eigenschaften** auf der rechten Seite des Bildschirms den Wert aus, der der Eigenschaft entspricht, die Sie ändern möchten, und geben Sie dann den neuen Wert ein.  
  
    > [!NOTE]  
    >  Wenn die Spalten Verwendung auf festgelegt ist `Ignore` , ist das Fenster **Eigenschaften** für die Spalte leer.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Miningmodelltasks und Anweisungen](mining-model-tasks-and-how-tos.md)  
  
  
