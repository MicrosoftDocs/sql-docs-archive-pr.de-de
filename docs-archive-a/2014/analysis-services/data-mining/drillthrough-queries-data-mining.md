---
title: Drillthrough-Abfragen (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AllowDrillThrough property
- drillthrough [Analysis Services]
- drillthrough [DMX]
ms.assetid: 246c784b-1b0c-4f0b-96f7-3af265e67051
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21e8c6f7cb6938e629be9d252c208c61c04d17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620671"
---
# <a name="drillthrough-queries-data-mining"></a>Drillthroughabfragen (Data Mining)
  Mithilfe einer *Drillthroughabfrage* können Sie Details aus zugrunde liegenden Fällen oder Strukturdaten abrufen, indem Sie eine Anfrage an das Miningmodell senden. Ein Drillthrough ist hilfreich, wenn Sie die Fälle anzeigen möchten, die zum Trainieren des Modells verwendet wurden, und nicht die Fälle, die zum Testen des Modells verwendet wurden, oder wenn Sie zusätzliche Details aus den Falldaten einsehen möchten.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Data Mining stellt zwei verschiedene Drillthroughoptionen bereit:  
  
-   Drillthrough zu den **Fällen im Modell**  
  
     Drillthrough zu Modell Fällen wird verwendet, wenn Sie von einem bestimmten Muster im Modell, z. b. einem Cluster oder einer Verzweigung einer Entscheidungsstruktur, gehen und Details zu den einzelnen Fällen anzeigen möchten.  
  
-   Drillthrough zu den **Fällen in der Struktur**  
  
     Ein Drillthrough zu Strukturfällen wird verwendet, wenn die Struktur Informationen enthält, die im Modell möglicherweise nicht verfügbar sind. Sie würden beispielsweise keine Kundenkontaktdaten in einem Clustermodell verwenden, selbst wenn die Daten in der Struktur enthalten wären. Nachdem Sie das Modell erstellt haben, können Sie jedoch Kontaktinformationen für Kunden abrufen, die in einem bestimmten Cluster gruppiert sind.  
  
 Dieser Abschnitt enthält Beispiele dafür, wie Sie diese Abfragen erstellen können.  
  
 [Verwenden von Drillthrough in Data Mining-Designer](#bkmk_Designer)  
  
 [Erstellen von Drillthroughabfragen mit DMX](#bkmk_DMX)  
  
 [Überlegungen zur Verwendung von Drillthrough](#bkmk_Considerations)  
  
-   [Sicherheitsprobleme](#bkmk_Security)  
  
-   [Einschränkungen](#bkmk_Limits)  
  
##  <a name="using-drillthrough-in-data-mining-designer"></a><a name="bkmk_Designer"></a>Verwenden von Drillthrough im Data Mining-Designer  
 Wenn ein Miningmodell für die Verwendung von Drillthrough konfiguriert wurde, und wenn Sie über die erforderlichen Berechtigungen verfügen, können Sie beim Durchsuchen eines Modells im entsprechenden Viewer auf einen Knoten klicken, und detaillierte Informationen über die Fälle in diesem bestimmten Knoten abrufen.  
  
 Führen [Sie einen Drillthrough zu Falldaten aus einem Mining Modell aus](drill-through-to-case-data-from-a-mining-model.md).  
  
 Wenn die Trainingsfälle bei der Verarbeitung der Miningstruktur zwischengespeichert wurden und Sie über die erforderlichen Berechtigungen verfügen, können Sie Informationen von den Modellfällen und der Miningstruktur zurückgeben, einschließlich Spalten, die nicht im Miningmodell enthalten sind.  
  
##  <a name="creating-drillthrough-queries-using-dmx"></a><a name="bkmk_DMX"></a>Erstellen von Drillthrough-Abfragen mit DMX  
 Sie können durch Erstellen einer DMX-Abfrage einen Drillthrough zu Falldaten ausführen, wenn Sie über Berechtigungen für das Modell oder die Struktur verfügen. Beispiele der Syntax zum Erstellen von Drillthroughabfragen in DMX finden Sie im folgenden Thema:  
  
 [Erstellen von Drillthroughabfragen mit DMX](create-drillthrough-queries-using-dmx.md)  
  
##  <a name="considerations-when-using-drillthrough"></a><a name="bkmk_Considerations"></a>Überlegungen bei der Verwendung von Drillthrough  
  
-   Wenn Sie den Data Mining-Assistenten verwenden, befindet sich die Option zur Aktivierung von Drillthrough für die Modellfälle auf der letzten Seite des Assistenten. Drillthrough ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Abschließen des Assistenten &#40;Data Mining-Assistent&#41;](../completing-the-wizard-data-mining-wizard.md).  
  
-   Sie können die Drillthroughfähigkeit einem vorhandenen Miningmodell hinzufügen, in diesem Fall muss das Modell jedoch neu verarbeitet werden, bevor Sie einen Drillthrough mit den Daten ausführen.  
  
-   Drillthrough funktioniert, indem Informationen über die Trainingsfälle abgerufen werden, die bei der Verarbeitung der Miningstruktur zwischengespeichert wurden. Wenn Sie alle zwischengespeicherten Daten nach Verarbeitung der Struktur durch Ändern der <xref:Microsoft.AnalysisServices.MiningStructureCacheMode>-Eigenschaft in `ClearAfterProcessing` löschen, funktioniert der Drillthrough nicht. Um Drillthrough für Strukturspalten zu aktivieren, müssen Sie die <xref:Microsoft.AnalysisServices.MiningStructureCacheMode>-Eigenschaft in `KeepTrainingCases` ändern und die Struktur erneut verarbeiten.  
  
-   Wenn die Miningstruktur keinen Drillthrough gestattet, jedoch das Miningmodell, können Sie nur Informationen der Modellfälle anzeigen, nicht jedoch der Miningstruktur.  
  
###  <a name="security-issues-for-drillthrough"></a><a name="bkmk_Security"></a>Sicherheitsprobleme bei Drillthrough  
 Wenn Sie einen Drillthrough zu Struktur Fällen aus dem Modell ausführen möchten, müssen Sie überprüfen, ob sowohl für die Mining Struktur als auch für das Mining Modell die [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) -Eigenschaft auf festgelegt ist `True` . Außerdem müssen Sie Mitglied einer Rolle sein, die sowohl für die Struktur als auch für das Modell über Drillthroughberechtigungen verfügt. Informationen zum Erstellen von Rollen finden Sie unter [Rollen-Designer &#40;Analysis Services – Mehrdimensionale Daten&#41;](https://msdn.microsoft.com/library/ms189696(v=sql.120).aspx). Thema  
  
 Drillthroughberechtigungen werden getrennt für die Struktur und das Modell festgelegt. Mit den Modellberechtigungen können Sie einen Drillthrough des Modells durchführen, auch wenn Sie keine Berechtigungen für die Struktur besitzen. Mit Drillthroughberechtigungen für die Struktur können Sie außerdem mit der Funktion [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) Strukturspalten in Drillthroughabfragen für das Modell einbeziehen.  
  
> [!NOTE]  
>  Wenn Sie Drillthrough sowohl für die Miningstruktur als auch für das Miningmodell aktivieren, kann jeder Benutzer, der Mitglied einer Rolle mit Drillthroughberechtigungen für das Miningmodell ist, auch Spalten in der Miningstruktur einsehen, selbst wenn diese Spalten nicht Teil des Miningmodells sind. Daher sollten Sie zum Schutz sensibler Daten die Datenquellensicht so einrichten, dass persönliche Informationen verborgen sind, und Drillthroughzugriff auf die Miningstruktur nur zulassen, wenn es wirklich erforderlich ist.  
  
###  <a name="limitations-on-drillthrough"></a><a name="bkmk_Limits"></a>Einschränkungen für Drillthrough  
  
-   Die folgenden Einschränkungen gelten für Drillthroughvorgänge auf einem Modell in Abhängigkeit von dem für die Erstellung des Modells verwendeten Algorithmus:  
  
|Algorithmusname|Problem|  
|--------------------|-----------|  
|Microsoft Naive Bayes-Algorithmus|Wird nicht unterstützt. Diese Algorithmen weisen bestimmten Knoten im Inhalt keine Fälle zu.|  
|Microsoft Neural Network-Algorithmus|Wird nicht unterstützt. Diese Algorithmen weisen bestimmten Knoten im Inhalt keine Fälle zu.|  
|Microsoft Logistic Regression-Algorithmus|Wird nicht unterstützt. Diese Algorithmen weisen bestimmten Knoten im Inhalt keine Fälle zu.|  
|Microsoft Linear Regression-Algorithmus|Unterstützt. Da das Modell jedoch als einzigen Knoten `All` erstellt, gibt Drillthrough alle Trainingsfälle des Modells zurück. Bei einem großen Trainingssatz kann es sehr lange dauern, bis die Ergebnisse geladen werden.|  
|Microsoft Time Series-Algorithmus|Unterstützt. Sie können jedoch keinen Drillthrough mit Struktur- oder Falldaten unter Verwendung des **Miningmodell-Viewers** im Data Mining-Designer ausführen. Sie müssen stattdessen eine DMX-Abfrage erstellen.<br /><br /> Sie können außerdem keinen Drillthrough auf bestimmten Knoten ausführen oder DMX-Abfragen schreiben, um Fälle von bestimmten Knoten eines Zeitreihenmodells abzurufen. Sie können Falldaten entweder aus dem Modell oder aus der Struktur abrufen, indem Sie andere Kriterien verwenden, beispielsweise Datums- oder Attributwerte.<br /><br /> Sie können auch die Datumsangaben der Modellfälle zurückgeben, indem Sie die [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx)-Funktion verwenden.<br /><br /> Wenn Sie Details der vom Microsoft Time Series-Algorithmus erstellten ARTXP- und ARIMA-Knoten anzeigen möchten, können Sie den [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) verwenden.|  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> Verwandte Aufgaben  
 Verwenden Sie die folgenden Links, um in bestimmten Szenarien mit Drillthroughs zu arbeiten.  
  
|Aufgabe|Link|  
|----------|----------|  
|Schritte zur Verwendung von Drillthroughs im Data Mining-Designer|[Ausführen von Drillthroughs für Falldaten aus einem Miningmodell](drill-through-to-case-data-from-a-mining-model.md)|  
|So ändern Sie ein vorhandenes Miningmodell, um Drillthroughs zu ermöglichen|[Aktivieren von Drillthrough für ein Miningmodell](enable-drillthrough-for-a-mining-model.md)|  
|Aktivieren von Drillthroughs für eine Miningstruktur mit der DMX WITH DRILLTHROUGH-Klausel|[CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)|  
|Weitere Informationen über das Zuweisen von Berechtigungen, die für Drillthroughs in Miningstrukturen und Miningmodellen gelten|[Erteilen von Berechtigungen für Data Mining-Strukturen und -Modelle &#40;Analysis Services&#41;](../multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Viewer für Data Mining-Modelle](data-mining-model-viewers.md)   
 [Data Mining-Abfragen](data-mining-queries.md)  
  
  
