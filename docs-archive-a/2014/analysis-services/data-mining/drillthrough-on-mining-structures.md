---
title: Drillthrough für Mining Strukturen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a0b00a3b-f9db-4289-a8cb-ddf600cd64ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: e8b3dad28227547f88956f1ac49e2878b2940f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622954"
---
# <a name="drillthrough-on-mining-structures"></a>Drillthrough in Miningstrukturen
  *Drillthrough* beschreibt die Fähigkeit, entweder ein Miningmodell oder eine Miningstruktur abzufragen und ausführliche Daten zu erhalten, die im Modell nicht verfügbar sind.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] bietet zwei verschiedene Optionen für Drillthroughs in Falldaten. Sie können einen Drillthrough zu den Daten ausführen, die für die Erstellung des Miningmodells verwendet wurden, oder Sie führen einen Drillthrough zu den Quelldaten in der Miningstruktur aus.  
  
## <a name="drillthrough-to-model-cases-vs-drillthrough-to-structure"></a>Drillthrough zu Modellfällen im Vergleich zu Drillthrough zu Strukturen  
 Ein Drillthrough zu **Modellfällen** ist hilfreich für die Suche nach weiteren Details zu Regeln, Mustern oder Clustern in einem Modell.  
  
 Demgegenüber soll ein **** Drillthrough in Bezug auf Strukturdaten einen Zugriff auf Informationen ermöglichen, die im Modell nicht verfügbar waren. Wenn Sie zum Beispiel über die entsprechenden Berechtigungen verfügen, möchten Sie unter Umständen feststellen, welche Datenzeilen für das Training des Modells und welche für Tests verwendet wurden.  
  
 Sie können auch Attribute der Daten anzeigen, die in der Analyse nicht verwendet wurden, vorausgesetzt, sie wurden in die Strukturdefinition eingeschlossen. Beispiel: Oftmals unterstützen Miningstrukturen zahlreiche andere Arten von Modellen, und einige Strukturspalten wurden möglicherweise aus einem Modell ausgeschlossen, da der Datentyp nicht kompatibel war oder da die Daten nicht für Analysen geeignet waren. Zum Beispiel würden Sie keine Kundenkontaktinformationen in einem Clusteringmodell verwenden, auch wenn die Daten in die Struktur eingeschlossen wurden. Durch das Aktivieren des Drillthroughs erhalten Sie jedoch Zugang zu diesen Informationen, ohne gesonderte Abfragen der Datenquelle ausführen zu müssen.  
  
## <a name="enabling-drillthrough-to-structure-data"></a>Aktivieren von Drillthroughs zu Strukturdaten  
 Um Drillthroughvorgänge in der Miningstruktur verwenden zu können, müssen die folgenden Bedingungen erfüllt werden:  
  
-   Drillthrough für das Modell muss ebenfalls aktiviert werden. Standardmäßig werden beide Formen des Drillthroughs deaktiviert. Um Drillthrough im Data Mining-Assistenten zu aktivieren, wählen Sie die Option aus, um Drillthrough zu Modellfällen auf der letzten Seite des Assistenten zu aktivieren. Sie können die Option für Drillthroughvorgänge für ein Modell auch später durch Ändern der `AllowDrillthrough`-Eigenschaft hinzufügen.  
  
-   Wenn Sie die Miningstruktur mit DMX erstellen, verwenden Sie die WITH DRILLTHROUGH-Klausel. Weitere Informationen finden Sie unter [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).  
  
-   Drillthrough funktioniert, indem Informationen über die Trainingsfälle abgerufen werden, die bei der Verarbeitung der Miningstruktur zwischengespeichert wurden. Wenn Sie die zwischengespeicherten Daten nach der Verarbeitung der Struktur durch Ändern der- <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> Eigenschaft in löschen `ClearAfterProcessing` , funktioniert der Drillthrough nicht. Um Drillthrough für Strukturspalten zu aktivieren, müssen Sie die <xref:Microsoft.AnalysisServices.MiningStructureCacheMode>-Eigenschaft in `KeepTrainingCases` ändern und die Struktur erneut verarbeiten.  
  
-   Überprüfen Sie, ob sowohl für die Mining Struktur als auch für das Mining Modell die [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) -Eigenschaft auf festgelegt ist `True` . Außerdem müssen Sie Mitglied einer Rolle sein, die sowohl für die Struktur als auch für das Modell über Drillthroughberechtigungen verfügt.  
  
## <a name="security-issues-for-drillthrough"></a>Sicherheitsprobleme mit Drillthrough  
 Drillthroughberechtigungen werden getrennt für die Struktur und das Modell festgelegt. Mit den Modellberechtigungen können Sie einen Drillthrough des Modells durchführen, auch wenn Sie keine Berechtigungen für die Struktur besitzen. Mit Drillthroughberechtigungen für die Struktur können Sie außerdem mit der Funktion [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) Strukturspalten in Drillthroughabfragen für das Modell einbeziehen.  
  
 Informationen zum Erstellen von Rollen und zum Zuweisen von Berechtigungen in Analysis Services finden Sie unter [Rollen-Designer &#40;Analysis Services – Mehrdimensionale Daten&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx).  
  
> [!NOTE]  
>  Wenn Sie Drillthrough sowohl für die Miningstruktur als auch für das Miningmodell aktivieren, kann jeder Benutzer, der Mitglied einer Rolle mit Drillthroughberechtigungen für das Miningmodell ist, auch Spalten in der Miningstruktur einsehen, selbst wenn diese Spalten nicht Teil des Miningmodells sind. Daher sollten Sie zum Schutz sensibler Daten die Datenquellensicht so einrichten, dass persönliche Informationen verborgen sind, und Drillthroughzugriff auf die Miningstruktur nur zulassen, wenn es wirklich erforderlich ist.  
  
## <a name="related-tasks"></a>Related Tasks  
 In den folgenden Themen finden Sie weitere Informationen zur Verwendung von Drillthroughs mit Miningmodellen.  
  
|||  
|-|-|  
|Verwenden von Drillthrough zu Struktur von den Miningmodell-Viewern|[Verwenden von Drillthrough mit den Modell-Viewern](use-drillthrough-from-the-model-viewers.md)|  
|In Beispielen von Drillthroughabfragen finden Sie Informationen zu bestimmten Modelltypen.|[Data Mining-Abfragen](data-mining-queries.md)|  
|Informationen über Berechtigungen, die für bestimmte Miningstrukturen und Miningmodelle gelten.|[Erteilen von Berechtigungen für Data Mining-Strukturen und -Modelle &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Miningmodell-Drillthrough](drillthrough-on-mining-models.md)  
  
  
