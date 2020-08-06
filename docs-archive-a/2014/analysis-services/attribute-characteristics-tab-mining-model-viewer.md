---
title: Registerkarte "Attribut Merkmale" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29ba482c21bb674a10bc4c9e6c6eccdf30905dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610378"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>Registerkarte "Attributmerkmale" (Miningmodell-Viewer)
  Im Bereich **Attributmerkmale** können Sie die Beziehungen zwischen Ergebnissen und Eingabeattributen in einem Naive Bayes-Modell untersuchen. Sie können den Wert des Zielattributs auswählen und dann eine Liste der Eingabeattribute anzeigen, die die stärksten Auswirkungen auf die Ergebnisse besitzen.  
  
 **Weitere Informationen:** [Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes Miningmodell aus den Modellen in der aktuellen Miningstruktur aus. Das Miningmodell wird automatisch in einem benutzerdefinierten Viewer geöffnet, der für den jeweils ausgewählten Typ von Modell am besten geeignet ist.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Für jedes Modell können Sie einen benutzerdefinierten Viewer oder aber den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte auswählen. Plug-In-Viewer werden in dieser Liste ebenfalls angezeigt, sofern verfügbar.  
  
 **Attribut**  
 Wählen Sie das vorhersagbare Attribut aus, das Sie analysieren möchten.  
  
 **Wert**  
 Wählen Sie einen Status für das unter **Attribut**festgelegte vorhersagbare Attribut aus. Da Naive Bayes-Modelle keine stetigen Größen unterstützen, verfügen alle Zielattribute über diskrete oder diskretisierte Ergebnisse. Das Missing-Attribut wird der Liste stets automatisch hinzugefügt.  
  
 **Merkmale für\<predictable state>**  
 Die Grafik enthält die folgenden Spalten, die die Beziehung zwischen den Statuswerten der Eingabeattribute und den Statuswerten des ausgewählten vorhersagbaren Attributs beschreiben.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Variable**|Führt die Eingabeattribute im Miningmodell auf.|  
|**Werte**|Führt die einzelnen Status des Eingabeattributs in **Variable**auf.|  
|**Wahrscheinlichkeit**|Der Balken stellt die Wahrscheinlichkeit dar, mit der das Attribut und der Wert in dieser Zeile dem ausgewählten Status des ausgewählten vorhersagbaren Attributs entsprechen. Zeigen Sie mit der Maus auf den Balken, um die Wahrscheinlichkeit als Prozentsatz anzuzeigen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
