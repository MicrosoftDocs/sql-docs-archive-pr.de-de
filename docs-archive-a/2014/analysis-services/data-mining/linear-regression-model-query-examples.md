---
title: Beispiele für lineare Regressionsmodell Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02d4b7309d7b5ea3d6295089f0fb2e778b1c9b4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622308"
---
# <a name="linear-regression-model-query-examples"></a>Beispiele für lineare Regressionsmodellabfrage
  Beim Erstellen einer Abfrage für ein Data Mining-Modell können Sie eine Inhaltsabfrage erstellen, die Details über die bei der Analyse ermittelten Muster liefert. Alternativ dazu können Sie auch eine Vorhersageabfrage erstellen, die Vorhersagen für neue Daten anhand der im Modell befindlichen Muster vornimmt. Eine Inhaltsabfrage stellt beispielsweise zusätzliche Details über die Regressionsformel zur Verfügung, während eine Vorhersageabfrage Aufschluss darüber gibt, ob ein neuer Datenpunkt in das Modell passt. Mit einer Abfrage können Sie auch Metadaten zum Modell abrufen.  
  
 In diesem Abschnitt wird erläutert, wie Abfragen für Modelle erstellt werden, die auf dem Microsoft Linear Regression-Algorithmus basieren.  
  
> [!NOTE]  
>  Da die lineare Regression auf einem Sonderfall des Microsoft Decision Trees-Algorithmus basiert, gibt es einige Ähnlichkeiten. Einige Entscheidungsstrukturmodelle, die kontinuierliche vorhersagbare Attribute verwenden, können Regressionsformeln enthalten. Weitere Informationen finden Sie unter [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md).  
  
 **Inhalts Abfragen**  
  
 [Verwenden des Data Mining-Schemarowsets zur Ermittlung der für ein Modell verwendeten Parameter](#bkmk_Query1)  
  
 [Verwenden von DMX zur Ermittlung der Regressionsformel für das Modell](#bkmk_Query2)  
  
 [Zurückgeben des Koeffizienten für das Modell](#bkmk_Query3)  
  
 **Vorhersage Abfragen**  
  
 [Vorhersagen von Einkommen mit einer SINGLETON-Abfrage](#bkmk_Query4)  
  
 [Verwenden von Vorhersagefunktionen mit einem Regressionsmodell](#bkmk_Query5)  
  
##  <a name="finding-information-about-the-linear-regression-model"></a><a name="bkmk_top"></a> Suchen nach Informationen über das lineare Regressionsmodell  
 Die Struktur eines linearen Regressionsmodells ist äußerst einfach. Das Miningmodell repräsentiert die Daten als einzelnen Knoten, der die Regressionsformel definiert. Weitere Informationen finden Sie unter [Miningmodellinhalt von logistischen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).  
  
 [Zurück zum Anfang](#bkmk_top)  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-determine-parameters-used-for-a-model"></a><a name="bkmk_Query1"></a> Beispielabfrage 1: Verwenden des Data Mining-Schemarowsets zur Ermittlung der für ein Modell verwendeten Parameter  
 Metadaten für das Modell finden Sie, indem Sie das Data Mining-Schemarowset abfragen. Dazu gehören beispielsweise das Erstellungsdatum des Modells, das Datum der letzten Verarbeitung, der Name der Miningstruktur, auf der das Modell basiert, und der Name der als vorhersagbares Attribut verwendeten Spalte. Sie können auch die Parameter zurückgeben, die beim ersten Erstellen des Modells verwendet wurden.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 Beispielergebnisse:  
  
|MINING_PARAMETERS|  
|------------------------|  
|COMPLEXITY_PENALTY=0.9,<br /><br /> MAXIMUM_INPUT_ATTRIBUTES=255,<br /><br /> MAXIMUM_OUTPUT_ATTRIBUTES=255,<br /><br /> MINIMUM_SUPPORT=10,<br /><br /> SCORE_METHOD=4,<br /><br /> SPLIT_METHOD=3,<br /><br /> FORCE_REGRESSOR=|  
  
> [!NOTE]  
>  Die Parametereinstellung "`FORCE_REGRESSOR =` " gibt an, dass der aktuelle Wert für den FORCE_REGRESSOR-Parameter NULL ist.  
  
 [Zurück zum Anfang](#bkmk_top)  
  
###  <a name="sample-query-2-retrieving-the-regression-formula-for-the-model"></a><a name="bkmk_Query2"></a> Beispielabfrage 2: Abrufen der Regressionsformel für das Modell  
 Die folgende Abfrage gibt den Miningmodellinhalt für ein lineares Regressionsmodell zurück, das mit der Targeted Mailing-Datenquelle erstellt wurde, die bereits im [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)verwendet wurde. Dieses Modell sagt das Kundeneinkommen basierend auf dem Alter vorher.  
  
 Die Abfrage gibt den Inhalt des Knotens zurück, der die Regressionsformel enthält. Jede Variable und jeder Koeffizient wird in einer separaten Zeile der geschachtelten NODE_DISTRIBUTION-Tabelle gespeichert. Wenn Sie die vollständige Regressions Formel anzeigen möchten, verwenden Sie den [Microsoft Tree-Viewer](browse-a-model-using-the-microsoft-tree-viewer.md), klicken Sie auf den Knoten **(alle)** , und öffnen Sie die **Mining Legende**.  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  Wenn Sie auf einzelne Spalten der geschachtelten Tabelle durch Verwenden einer Abfrage wie `SELECT <column name> from NODE_DISTRIBUTION`verweisen, müssen einige Spalten, wie **SUPPORT** oder **PROBABILITY**, in Klammern eingeschlossen werden, um sie von den gleichnamigen reservierten Schlüsselwörtern zu unterscheiden.  
  
 Erwartete Ergebnisse:  
  
|T.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Yearly Income|Missing|0|0.000457142857142857|0|1|  
|Yearly Income|57220.8876687257|17484|0.999542857142857|1041275619.52776|3|  
|Age|471.687717702463|0|0|126.969442359327|7|  
|Age|234.680904692439|0|0|0|8|  
|Age|45.4269617936399|0|0|126.969442359327|9|  
||35793.5477381267|0|0|1012968919.28372|11|  
  
 In Vergleich dazu wird die Regressionsformel in der **Mininglegende**wie folgt angezeigt:  
  
 Yearly Income = 57,220.919 + 471.688 * (Age - 45.427)  
  
 In der **Mininglegende**sind einige Zahlen gerundet. Die NODE_DISTRIBUTION-Tabelle und die **Mininglegende** enthalten im Wesentlichen jedoch die gleichen Werte.  
  
 Die Werte in der VALUETYPE-Spalte geben Aufschluss über die Art der in jeder Zeile enthaltenen Informationen. Dies ist nützlich, wenn Sie die Ergebnisse programmgesteuert verarbeiten. In der folgenden Tabelle werden die Werttypen, die für eine lineare Regressionsformel ausgegeben werden, angezeigt.  
  
|VALUETYPE|  
|---------------|  
|1 (Missing)|  
|3 (Continuous)|  
|7 (Koeffizient)|  
|8 (Score Gain)|  
|9 (Statistik)|  
|7 (Koeffizient)|  
|8 (Score Gain)|  
|9 (Statistik)|  
|11 (Intercept)|  
  
 Weitere Informationen über die Bedeutung der einzelnen Werttypen für Regressionsmodelle finden Sie unter [Miningmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).  
  
 [Zurück zum Anfang](#bkmk_top)  
  
###  <a name="sample-query-3-returning-only-the-coefficient-for-the-model"></a><a name="bkmk_Query3"></a> Beispielabfrage 3: Zurückgeben des Koeffizienten für das Modell  
 Mit der VALUETYPE-Enumeration können Sie nur den Koeffizienten für die Regressionsgleichung zurückgeben, wie in der folgenden Abfrage veranschaulicht:  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 Mit dieser Abfrage werden zwei Zeilen zurückgegeben, eine Zeile aus dem Miningmodellinhalt und die Zeile der geschachtelten Tabelle, die den Koeffizienten enthält. Die Spalte ATTRIBUTE_NAME ist hier nicht eingeschlossen, da sie für den Koeffizienten stets leer ist.  
  
|MODEL_NAME|t.ATTRIBUTE_VALUE|t.VALUETYPE|  
|-----------------|------------------------|-----------------|  
|LR_PredictIncome|||  
|LR_PredictIncome|35793.5477381267|11|  
  
 [Zurück zum Anfang](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a>Treffen von Vorhersagen aus einem linearen Regressionsmodell  
 Mit der Registerkarte Miningmodellvorhersage im Data Mining-Designer können Sie Vorhersageabfragen für lineare Regressionsmodelle erstellen. Der Generator für Vorhersageabfragen ist sowohl in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] als auch in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verfügbar.  
  
> [!NOTE]  
>  Abfragen für Regressionsmodelle können Sie auch mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Data Mining-Add-Ins für Excel oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Data Mining-Add-Ins für Excel erstellen. Auch wenn die Data Mining-Add-Ins für Excel keine Regressionsmodelle erstellen, können Sie jedes Miningmodell, das in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz gespeichert ist, durchsuchen und abfragen.  
  
 [Zurück zum Anfang](#bkmk_top)  
  
###  <a name="sample-query-4-predicting-income-using-a-singleton-query"></a><a name="bkmk_Query4"></a> Beispielabfrage 4: Vorhersagen von Einkommen mit einer SINGLETON-Abfrage  
 Die einfachste Möglichkeit zum Erstellen einer einzelnen Abfrage für ein Regressionsmodell bietet das Dialogfeld **SINGLETON-Abfrageeingabe** . Beispielsweise können Sie die folgende DMX-Abfrage erstellen, indem Sie das entsprechende Regressionsmodell auswählen, **Singleton-Abfrage**auswählen und dann `20` als Wert für **Age**eingeben.  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 Beispielergebnisse:  
  
|Yearly Income|  
|-------------------|  
|45227.302092176|  
  
 [Zurück zum Anfang](#bkmk_top)  
  
###  <a name="sample-query-5-using-prediction-functions-with-a-regression-model"></a><a name="bkmk_Query5"></a> Beispielabfrage 5: Verwenden von Vorhersagefunktionen mit einem Regressionsmodell  
 Sie können viele der Standardvorhersagefunktionen mit linearen Regressionsmodellen verwenden. Im folgenden Beispiel wird veranschaulicht, wie den Vorhersageabfrageergebnissen einige aussagekräftige statistische Daten hinzugefügt werden. Aus diesen Ergebnissen ist ersichtlich, dass es eine beträchtliche Abweichung vom Mittelwert für dieses Modell gibt.  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 Beispielergebnisse:  
  
|Yearly Income|StDev1|  
|-------------------|------------|  
|45227.302092176|31827.1726561396|  
  
 [Zurück zum Anfang](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a>Liste der Vorhersagefunktionen  
 Alle Algorithmen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] unterstützen einen gemeinsamen Funktionssatz. Allerdings unterstützt der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus zusätzliche Funktionen, die in der folgenden Tabelle aufgelistet sind.  
  
|||  
|-|-|  
|Vorhersagefunktion|Verwendung|  
|[IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx)|Bestimmt, ob ein Knoten ein untergeordnetes Element eines anderen Knotens im Modell ist.|  
|[IsInNode &#40;DMX&#41;](/sql/dmx/isinnode-dmx)|Zeigt an, ob der angegebene Knoten den aktuellen Fall enthält.|  
|[PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)|Gibt einen vorhergesagten Wert oder eine Gruppe von Werten für eine angegebene Spalte zurück.|  
|[PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx)|Gibt "Node_ID" für jeden Fall zurück.|  
|[PredictStdev &#40;DMX&#41;](/sql/dmx/predictstdev-dmx)|Gibt die Standardabweichung für den prognostizierten Wert zurück.|  
|[PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx)|Gibt den Unterstützungswert für einen bestimmten Status zurück.|  
|[PredictVariance &#40;DMX&#41;](/sql/dmx/predictvariance-dmx)|Gibt die Varianz einer angegebenen Spalte zurück.|  
  
 Eine Liste der Funktionen, die allen [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Algorithmen gemeinsam sind, finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md). Weitere Informationen zum Verwenden dieser Funktionen finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; – Funktionsreferenz](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm.md)   
 [Data Mining-Abfragen](data-mining-queries.md)   
 [Technische Referenz für den Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm-technical-reference.md)   
 [Miningmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
