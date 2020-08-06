---
title: Ändern von Standard Tabellennamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 254f797be95f60211983400b019415431d4cf39c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608052"
---
# <a name="modifying-default-table-names"></a>Ändern von Standardtabellennamen
  Sie können den Wert der **FriendlyName** -Eigenschaft für Objekte in der Datenquellensicht ändern, um die Benutzerfreundlichkeit und Identifizierung zu optimieren.  
  
 In der folgenden Aufgabe ändern Sie den Anzeigenamen jeder Tabelle in der Datenquellensicht, indem Sie die Präfixe**Dim**und**Fact**aus diesen Tabellen entfernen. Dadurch lassen sich der Cube und die Dimensionsobjekte (die Sie in der nächsten Lektion definieren) einfacher identifizieren und verwenden.  
  
> [!NOTE]  
>  Sie können auch die Anzeigenamen von Spalten ändern, berechnete Spalten definieren und Tabellen oder Sichten in der Datenquellensicht verknüpfen, um die Benutzerfreundlichkeit zu erhöhen.  
  
### <a name="to-modify-the-default-name-of-a-table"></a>So ändern Sie den Standardnamen einer Tabelle  
  
1.  Klicken Sie im Bereich **Tabellen** des **Datenquellensicht-Designers**mit der rechten Maustaste auf die Tabelle **FactInternetSales** , und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Wenn das Eigenschaftenfenster auf der rechten Seite des Microsoft Visual Studio-Fensters nicht angezeigt wird, klicken Sie in der Titelleiste des Eigenschaftenfensters auf die Schaltfläche **Automatisch im Hintergrund** , damit es sichtbar bleibt.  
  
     Es ist einfacher, die Eigenschaften für jede Tabelle in der Datenquellensicht zu ändern, wenn das Eigenschaftenfenster geöffnet bleibt. Wenn Sie das Fenster nicht mithilfe der Schaltfläche **Automatisch im Hintergrund** geöffnet halten, wird das Fenster geschlossen, sobald Sie auf ein anderes Objekt im Bereich **Diagramm** klicken.  
  
3.  Ändern Sie die **FriendlyName** -Eigenschaft für das **FactInternetSales** -Objekt in *`InternetSales`* .  
  
     Wenn Sie außerhalb der Zelle für die **FriendlyName** -Eigenschaft klicken, wird die Änderung angewendet. In der nächsten Lektion definieren Sie eine Measuregruppe, die auf dieser Faktentabelle basiert. Der Name der Faktentabelle lautet dann InternetSales statt FactInternetSales, weil Sie in dieser Lektion Änderungen vorgenommen haben.  
  
4.  Klicken Sie im Bereich **Tabellen** auf **DimProduct** . Ändern Sie im Eigenschaftenfenster die **FriendlyName** -Eigenschaft in *`Product`* .  
  
5.  Ändern Sie die **FriendlyName** -Eigenschaft jeder verbleibenden Tabelle in der Datenquellensicht in der gleichen Weise, um das Präfix "**Dim**" zu entfernen.  
  
6.  Klicken Sie nach dem Fertigstellen auf die Schaltfläche **Automatisch im Hintergrund** , um das Eigenschaftenfenster wieder auszublenden.  
  
7.  Klicken Sie im Menü **Datei** oder in der Symbolleiste von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Alle speichern** , um die von Ihnen bis jetzt vorgenommenen Änderungen im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt zu speichern. Sie können das Lernprogramm hier beenden, wenn Sie möchten, und es später fortsetzen.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Definieren und Bereitstellen eines Cubes](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen Sichten in mehrdimensionalen Modellen](multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Ändern von Eigenschaften in einer Datenquellensicht &#40;Analysis Services&#41;](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
