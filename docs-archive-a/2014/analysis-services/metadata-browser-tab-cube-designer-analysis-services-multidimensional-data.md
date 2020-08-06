---
title: Metadaten (Registerkarte "Browser", Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8093ac8cac8e3cd5a609e97b47ede89912897e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724281"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Metadaten (Registerkarte 'Browser', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie im Cube-Designer auf der Registerkarte **Browser** den Bereich **Metadaten** , um die Struktur des Cubes zu durchsuchen, verwandte Measures zu sehen und Dimensionen anzuzeigen und zu erstellen. Sie können einen Drilldown in Hierarchien ausführen, eine Liste von verfügbaren Measures und KPIs anzeigen und die vollqualifizierten Namen von Objekten kopieren.  
  
 Sie können auch die Objekte und die Hierarchien im Bereich **Metadaten** in den Bereich zum Erstellen von Abfragen ziehen, um neue Abfragen zu erstellen oder Daten zum Durchsuchen in Excel zu exportieren.  
  
## <a name="options"></a>Tastatur  
 **Metadaten**  
 Zeigt die in der aktuellen Sicht verfügbaren Metadaten an. Sie können die Sicht (das heißt, die derzeit ausgewählte Perspektive oder den Cube) ändern, indem Sie auf das Cubesymbol klicken und anschließend mit dem Dialogfeld **Cubeauswahl** einen neuen Cube oder eine neue Perspektive auswählen. Sie können auch auf **Measuregruppe**klicken und eine neue Measuregruppe in der Dropdownliste auswählen, um die Objekte zu filtern, die im Bereich **Metadaten** verfügbar sind.  
  
 Ziehen Sie die ausgewählten Elemente im Bereich [!INCLUDE[msCoName](../includes/msconame-md.md)] Bericht **in den Filter-, Daten-, Zeilen- oder Spaltenbereich des PivotTable-Steuerelements von** Office 11.0, um die Daten für das ausgewählte Element anzuzeigen.  
  
 **Funktionen**  
 Zeigt eine Liste aller Funktionen, Operatoren und Konstanten an, die verwendet werden können, um Abfragen oder Datensichten im **Browser**zu erstellen. Um eine Funktion zu verwenden, suchen Sie das gewünschte Objekt, und ziehen Sie es in den Abfragebereich. Die Syntaxdefinition wird dem Text hinzugefügt  
  
> [!WARNING]  
>   Beim Arbeiten in der grafischen Entwurfssicht ist die Liste **Funktion** nicht verfügbar.  
  
 Bei Verwendung eines tabellarischen Modells enthält die Funktionsliste sowohl MDX-Funktionen als auch DAX-Funktionen. Andernfalls enthält die Liste nur MDX-Funktionen. Ein mehrdimensionales Modell kann DAX-Funktionen nicht direkt verwenden, obwohl eine Objektdefinition einen DAX-Ausdruck enthalten kann.  
  
 Tipp: Die Ordner, die DAX-Funktionen enthalten, sind vollständig in Großbuchstaben aufgeführt. Alle anderen Ordner enthalten MDX-Funktionen. Es gibt z. B. zwei Ordner für statistische Funktionen: **STATISTICAL** enthält die verwandten DAX-Funktionen.  
  
## <a name="context-menu"></a>Kontextmenü  
 Wenn Sie mit der rechten Maustaste auf eines der im Bereich **Metadaten** angezeigten Elemente klicken, wird ein Kontextmenü angezeigt, das die folgenden Optionen enthält:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Zu Abfrage hinzufügen**|Klicken Sie, um dem unteren Bereich des Abfrageerstellungsbereichs das ausgewählte Objekt hinzuzufügen.|  
|**Zu Filter hinzufügen**|Klicken Sie, um dem Filterbereich des **Browsers**die ausgewählte Dimension, das Attribut, die Hierarchie oder die Ebene hinzuzufügen.<br /><br /> Hinweis: Diese Option ist nur aktiviert, wenn eine Dimension, ein Attribut, eine Hierarchie oder eine Ebene ausgewählt wird.|  
|**Kopieren**|Klicken Sie auf diese Option, um der Zwischenablage das ausgewählte Element hinzuzufügen.<br /><br /> Hinweis: Mit dieser Option wird der vollqualifizierte Name des Objekts kopiert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbolleiste &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [In Excel &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Abfragen und Filtern &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services-mehrdimensionalen Daten&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Browser &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
