---
title: Abfrage und Filter (Registerkarte ' Browser ', Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616247"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Abfrage und Filter (Registerkarte 'Browser', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Dieser Bereich der Registerkarte **Browser** im Cube-Designer enthält einen Abfrage- und Filterbereich, der Sie bei der Auswahl der Daten aus dem Cube unterstützt, die beim Durchsuchen oder Abfragen verwendet werden. Sie können beliebig viele Cubeobjekte hinzufügen und dann die Ergebnisse im Datenbereich anzeigen oder die Ergebnisse in einen Bericht exportieren und In Excel analysieren verwenden, um visuell darzustellen, wie die Daten von Endbenutzern angezeigt werden.  
  
> [!WARNING]  
>  Wenn Sie in diesem Bereich mit Daten arbeiten, verwendet der **Browser** standardmäßig den grafischen Entwurfsmodus. Sie können die Abfrage jedoch direkt mit MDX bearbeiten, indem Sie auf die Umschaltfläche **Entwurfsmodus** klicken. Dabei wird der Bereich, in dem Sie Filter für Dimensionen entwerfen können, ausgeblendet. Falls Sie einen Filter hinzufügen möchten, können Sie in den grafischen Entwurfsmodus zurückwechseln.  
  
 Die Anmeldeinformationen des aktuellen Benutzers, nicht die auf der Seite **Identitätswechselinformationen** angegebenen Anmeldeinformationen, werden standardmäßig zum Herstellen einer Verbindung mit der Datenquelle verwendet, wenn eine Abfrage ausgeführt wird. Sie können jedoch auch den Benutzerkontext für die Abfrage oder den Bericht ändern, indem Sie auf der **Symbolleiste** auf **Benutzer wechseln**klicken.  
  
## <a name="options"></a>Tastatur  
 **Dimension**  
 Wählen Sie die Dimension aus, in der der Teilcube in Slices aufgeteilt werden soll.  
  
 **Hierarchy**  
 Wählen Sie die Hierarchie aus, in der der Teilcube in Slices aufgeteilt werden soll.  
  
 **Operator**  
 Wählen Sie den Operator aus, der definiert, wie der Ausdruck in **Filterausdruck** auf die ausgewählte Hierarchie angewendet wird. Die folgende Tabelle beschreibt die verfügbaren Operatoren.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Gleich**|Die Ergebnisse sind auf die in **Filterausdruck**definierte Menge beschränkt.|  
|**Ungleich**|Die Ergebnisse sind auf die Elemente beschränkt, die durch die in **Filterausdruck**definierte Menge ausgeschlossen werden.|  
|**Geben Sie in**|Die Ergebnisse sind auf die in **Filterausdruck**gewählte benannte Menge beschränkt.|  
|**Not In**|Die Ergebnisse sind auf die Elemente beschränkt, die durch die in **Filterausdruck**gewählte benannte Menge ausgeschlossen werden.|  
|**Contains**|Die Ergebnisse sind auf die Elemente beschränkt, deren Elementnamen die in **Filterausdruck**angegebene Zeichenfolge enthalten.|  
|**Beginnt mit**|Die Ergebnisse sind auf die Elemente beschränkt, deren Elementnamen mit der in **Filterausdruck**angegebenen Zeichenfolge beginnen.|  
|**Bereich (inklusiv)**|Die Ergebnisse sind auf den in **Filterausdruck**ausgewählten Bereich beschränkt.|  
|**Bereich (exklusiv)**|Die Ergebnisse sind auf die Elemente beschränkt, die durch den in **Filterausdruck**ausgewählten Bereich ausgeschlossen werden.|  
|**MDX**|Die Ergebnisse sind auf den in **Filterausdruck**festgelegten MDX-Ausdruck (Multidimensional Expressions) beschränkt.|  
  
 **Filterausdruck**  
 Geben Sie den Ausdruck ein, der durch **Operator**ausgewertet werden soll, um die zu durchsuchenden Ergebnisse zu beschränken.  
  
> [!NOTE]  
>  Bei dem Feld handelt es sich um ein dynamisches Dateneingabeelement, dessen Anzeigemodus sich je nach dem vom ausgewählten Operator benötigten Datentyp ändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Browser &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [In Excel &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Metadaten &#40;Registerkarte "Browser", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
