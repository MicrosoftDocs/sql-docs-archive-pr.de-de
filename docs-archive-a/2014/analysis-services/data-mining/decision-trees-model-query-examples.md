---
title: Beispiele für Entscheidungsstruktur-Modell Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- decision tree algorithms [Analysis Services]
- content queries [DMX]
- decision trees [Analysis Services]
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a6b158a42c9ca90bf2cfd2e9b981a1e2a735ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697326"
---
# <a name="decision-trees-model-query-examples"></a>Beispiele für Entscheidungsstruktur-Modellabfragen
  Beim Erstellen einer Abfrage für ein Data Mining-Modell können Sie eine Inhaltsabfrage erstellen, die Details über die bei der Analyse ermittelten Muster liefert. Alternativ dazu können Sie auch eine Vorhersageabfrage erstellen, die Vorhersagen für neue Daten anhand der im Modell befindlichen Muster vornimmt. So könnte beispielsweise eine Inhaltsabfrage für ein Entscheidungsstrukturmodell statistische Angaben zur Anzahl der Fälle auf jeder Ebene der Struktur oder die Regeln liefern, die die Fälle voneinander unterscheiden. Alternativ dazu ordnet eine Vorhersageabfrage das Modell neuen Daten zu, um Empfehlungen, Klassifikationen und so weiter zu generieren. Mit einer Abfrage können Sie auch Metadaten zum Modell abrufen.  
  
 In diesem Abschnitt wird erklärt, wie Abfragen für Modelle erstellt werden, die auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus basieren.  
  
 **Inhaltsabfragen**  
  
 [Abrufen von Modellparametern aus dem Data Mining-Schemarowset](#bkmk_Query1)  
  
 [Abrufen von Details zu Strukturen im Modell mit DMX](#bkmk_Query2)  
  
 [Abrufen von Teilstrukturen aus dem Modell](#bkmk_Query3)  
  
 **Vorhersageabfragen**  
  
 [Zurückgeben von Vorhersagen mit Wahrscheinlichkeiten](#bkmk_Query4)  
  
 [Vorhersagen von Zuordnungen aus einem Entscheidungsstrukturmodell](#bkmk_Query5)  
  
 [Abrufen einer Regressionsformel aus einem Entscheidungsstrukturmodell](#bkmk_Query6)  
  
##  <a name="finding-information-about-a-decision-trees-model"></a><a name="bkmk_top2"></a>Suchen nach Informationen über ein Entscheidungsstruktur Modell  
 Um aussagekräftige Abfragen des Inhalts eines Entscheidungsstrukturmodells zu erstellen, müssen Sie die Struktur des Inhaltsmodells kennen und wissen, in welchem Knotentyp welche Art von Informationen gespeichert ist. Weitere Informationen finden Sie unter [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).  
  
###  <a name="sample-query-1-retrieving-model-parameters-from-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a>Beispiel Abfrage 1: Abrufen von Modellparametern aus dem Data Mining-Schemarowset  
 Durch Abfrage des Data Mining-Schemarowsets können Sie Metadaten zum Modell ermitteln, wie das Datum der Modellerstellung, das Datum der letzten Modellverarbeitung, den Namen der Miningstruktur, auf der das Modell basiert, und den Namen der als vorhersagbares Attribut verwendeten Spalte. Sie können auch die Parameter zurückgeben, die beim ersten Erstellen des Modells verwendet wurden.  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 Beispielergebnisse:  
  
 MINING_PARAMETERS  
  
 COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MINIMUM_SUPPORT=10, SCORE_METHOD=4, SPLIT_METHOD=3, FORCE_REGRESSOR=  
  
###  <a name="sample-query-2-returning-details-about-the-model-content-by-using-dmx"></a><a name="bkmk_Query2"></a>Beispiel Abfrage 2: Zurückgeben von Details zum Modell Inhalt mit DMX  
 Die folgende Abfrage gibt einige grundlegende Informationen über die Entscheidungsstrukturen zurück, die beim Erstellen des Modells im [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)erstellt wurden. Jede Struktur wird in einem eigenen Knoten gespeichert. Da dieses Modell nur ein einziges vorhersagbares Attribut enthält, gibt es nur einen Strukturknoten. Wenn Sie jedoch ein Zuordnungsmodell unter Verwendung des Decision Trees-Algorithmus erstellen, können Hunderte von Strukturen vorhanden sein, eine für jedes Produkt.  
  
 Diese Abfrage gibt alle Knoten vom Typ 2 zurück, die die Knoten auf oberster Ebene einer Struktur sind, welche ein bestimmtes vorhersagbares Attribut darstellt.  
  
> [!NOTE]  
>  Die Spalte `CHILDREN_CARDINALITY` muss in Klammern eingeschlossen werden, um sie von dem reservierten MDX-Schlüsselwort mit dem gleichen Namen unterscheiden zu können.  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 Beispielergebnisse:  
  
|MODEL_NAME|NODE_NAME|NODE_CAPTION|NODE_SUPPORT|CHILDREN_CARDINALITY|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|TM_DecisionTree|000000001|All|12939|5|  
  
 Was bedeuten diese Ergebnisse? In einem Entscheidungsstrukturmodell sagt die Kardinalität eines bestimmten Knotens aus, wie viele direkt untergeordnete Elemente dieser Knoten hat. Die Kardinalität für diesen Knoten ist 5. Dies bedeutet, dass das Modell die Zielgruppe potenzieller Fahrradkäufer in 5 Untergruppen aufgeteilt hat.  
  
 Die nachfolgende verwandte Abfrage gibt die untergeordneten Elemente für diese fünf Untergruppen zurück, zusammen mit der Verteilung der Attribute und Werte in den untergeordneten Knoten. Da statistische Informationen wie Unterstützung, Wahrscheinlichkeit und Varianz in der geschachtelten Tabelle `NODE_DISTRIBUTION`gespeichert sind, wird in diesem Beispiel das Schlüsselwort `FLATTENED` zur Ausgabe der Spalten der geschachtelten Tabelle verwendet.  
  
> [!NOTE]  
>  Die verschachtelte Tabellenspalte `SUPPORT` muss in Klammern eingeschlossen werden, um sie von dem reservierten Schlüsselwort mit dem gleichen Namen unterscheiden zu können.  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 Beispielergebnisse:  
  
|NODE_NAME|NODE_CAPTION|T.ATTRIBUTE_NAME|T.ATTRIBUTE_VALUE|Alias|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|00000000100|Number Cars Owned = 0|Bike Buyer|Missing|0|  
|00000000100|Number Cars Owned = 0|Bike Buyer|0|1067|  
|00000000100|Number Cars Owned = 0|Bike Buyer|1|1875|  
|00000000101|Number Cars Owned = 3|Bike Buyer|Missing|0|  
|00000000101|Number Cars Owned = 3|Bike Buyer|0|678|  
|00000000101|Number Cars Owned = 3|Bike Buyer|1|473|  
  
 Aus diesen Ergebnissen können Sie herausfinden, dass Kunden, die ein Fahrrad gekauft `[Bike Buyer]` haben (= 1), 1067 Kunden 0 Autos und 473 Kunden drei Autos hatten.  
  
###  <a name="sample-query-3-retrieving-subtrees-from-the-model"></a><a name="bkmk_Query3"></a>Beispiel Abfrage 3: Abrufen von Teil Strukturen aus dem Modell  
 Angenommen, Sie möchten mehr über die Kunden in Erfahrung bringen, die ein Fahrrad gekauft haben. Sie können zusätzliche Details für jede Teilstruktur über die Funktion [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) in der Abfrage anzeigen, wie im folgenden Beispiel dargestellt. Die Abfrage gibt die Anzahl der Fahrradkäufer zurück, indem die Blattknoten (NODE_TYPE = 4) aus der Struktur abgerufen werden, die Kunden im Alter von über 42 Jahren enthält. Die Abfrage beschränkt die Zeilen aus der geschachtelten Tabelle auf die Zeilen, in denen Bike Buyer = 1 ist.  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 Beispielergebnisse:  
  
|NODE_NAME|NODE_CAPTION|t.SUPPORT|  
|----------------|-------------------|---------------|  
|000000001000100|Yearly Income >= 26000 and < 42000|266|  
|00000000100010100|Total Children = 3|75|  
|0000000010001010100|Number Children At Home = 1|75|  
  
## <a name="making-predictions-using-a-decision-trees-model"></a>Treffen von Vorhersagen mit einem Entscheidungsstrukturmodell  
 Da Entscheidungsstrukturen für eine Vielzahl von Tasks wie Klassifikation, Regression und sogar Zuordnung eingesetzt werden können, stehen Ihnen beim Erstellen einer Vorhersageabfrage für ein Entscheidungsstrukturmodell zahlreiche Optionen zur Verfügung. Sie müssen den Zweck kennen, für den das Modell erstellt wurde, um die Ergebnisse der Vorhersage zu verstehen. In den folgenden Abfragebeispielen werden drei verschiedene Szenarien veranschaulicht:  
  
-   Zurückgeben einer Vorhersage für ein Klassifikationsmodell, zusammen mit der Wahrscheinlichkeit, mit der diese Vorhersage richtig ist, und anschließendes Filtern der Ergebnisse nach der Wahrscheinlichkeit  
  
-   Erstellen einer SINGLETON-Abfrage zur Vorhersage von Zuordnungen  
  
-   Abrufen der Regressionsformel für einen Teil der Entscheidungsstruktur, in dem die Beziehung zwischen Eingabe und Ausgabe linear ist  
  
###  <a name="sample-query-4-returning-predictions-with-probabilities"></a><a name="bkmk_Query4"></a>Beispiel Abfrage 4: Zurückgeben von Vorhersagen mit Wahrscheinlichkeiten  
 In der folgenden Beispielabfrage wird das Entscheidungsstrukturmodell verwendet, das im [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)erstellt wurde. Die Abfrage gibt einen neuen Satz von Beispieldaten aus der Tabelle dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW weiter, um vorauszusagen, welche Kunden im neuen Dataset ein Fahrrad kaufen werden.  
  
 Die Abfrage verwendet die Vorhersagefunktion [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), die eine geschachtelte Tabelle mit nützlichen Informationen über die in dem Modell erkannten Wahrscheinlichkeiten zurückgibt. Die Ergebnisse werden durch die letzte WHERE-Klausel der Abfrage so gefiltert, dass nur die Kunden zurückgegeben werden, für die die Wahrscheinlichkeit, dass sie ein Fahrrad kaufen, über 0 Prozent liegt.  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 Standardmäßig gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] geschachtelte Tabellen mit der Spaltenbezeichnung **Ausdruck**zurück. Sie können diese Bezeichnung durch Aliasing der Spalte ändern, die zurückgegeben wird. Wenn Sie so vorgehen, wird der Alias (in diesem Fall **Ergebnisse**) sowohl als Spaltenbezeichnung als auch als Wert in der geschachtelten Tabelle verwendet. Sie müssen die geschachtelte Tabelle erweitern, um die Ergebnisse zu sehen.  
  
 Beispiel Ergebnisse, bei denen Bike Buyer = 1:  
  
|Bike Buyer|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|$VARIANCE|$STDEV|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|1|2540|0.634849242045644|0.013562168281562|0|0|  
|0|1460|0.364984174579377|0.00661336932550915|0|0|  
||0|0.000166583374979177|0.000166583374979177|0|0|  
  
 Wenn Ihr Anbieter keine hierarchischen Rowsets wie die hier dargestellten unterstützt, können unter Verwendung des FLATTENED-Schlüsselworts in der Abfrage die Ergebnisse als Tabelle zurückgeben lassen, die NULL-Werte anstelle der wiederholten Spaltenwerte enthält. Weitere Informationen finden Sie unter [Geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](nested-tables-analysis-services-data-mining.md) oder [Grundlegendes zur SELECT-Anweisung (DMX)](/sql/dmx/understanding-the-dmx-select-statement).  
  
###  <a name="sample-query-5-predicting-associations-from-a-decision-trees-model"></a><a name="bkmk_Query5"></a>Beispiel Abfrage 5: Vorhersagen von Zuordnungen aus einem Entscheidungsstruktur Modell  
 Die folgende Beispielabfrage basiert auf der Association-Miningstruktur. Darüber hinaus können Sie in dem Beispiel dieser Miningstruktur ein neues Modell hinzufügen und Microsoft Decision Trees als Algorithmus auswählen. Weitere Informationen zum Erstellen der Association-Miningstruktur finden Sie unter [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Data Mining-Tutorial für Fortgeschrittene&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).  
  
 Die folgende Beispielabfrage ist eine SINGLETON-Abfrage, die Sie mühelos in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellen können, indem Sie Felder wählen und anschließend Werte für diese Felder in einer Dropdownliste auswählen.  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Erwartete Ergebnisse:  
  
|Modell|  
|-----------|  
|Mountain-200|  
|Mountain Tire Tube|  
|Touring Tire Tube|  
  
 Die Ergebnisse sagen aus, welches die drei besten Produkte zur Empfehlung für Kunden sind, die das Produkt Patch Kit erworben haben. Sie können auch mehrere Produkte als Eingabe liefern, wenn Sie Empfehlungen machen, entweder durch Eingabe von Werten oder über das Dialogfeld **SINGLETON-Abfrageeingabe** , in dem Sie Werte hinzufügen oder entfernen. Die folgende Beispielabfrage zeigt, wie mehrere Werte geliefert werden, für die eine Vorhersage getroffen werden soll. Die Werte sind mittels einer UNION-Klausel in der SELECT-Anweisung verbunden, die die Eingabewerte definiert.  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Erwartete Ergebnisse:  
  
|Modell|  
|-----------|  
|Long-Sleeve Logo Jersey|  
|Mountain-400-W|  
|Classic Vest|  
  
###  <a name="sample-query-6-retrieving-a-regression-formula-from-a-decision-trees-model"></a><a name="bkmk_Query6"></a>Beispiel Abfrage 6: Abrufen einer Regressions Formel aus einem Entscheidungsstruktur Modell  
 Wenn Sie ein Entscheidungsstrukturmodell erstellen, das eine Regression für ein kontinuierliches Attribut enthält, können Sie die Regressionsformel verwenden, um Vorhersagen zu treffen, oder Sie können Informationen über die Regressionsformel extrahieren. Weitere Informationen zu Abfragen für Regressionsmodelle finden Sie unter [Beispiele für lineare Regressionsmodellabfragen](linear-regression-model-query-examples.md).  
  
 Wenn ein Entscheidungsstrukturmodell eine Mischung aus Regressionsknoten und Knoten enthält, die nach diskreten Attributen oder Bereichen unterteilt sind, können Sie eine Abfrage erstellen, die nur den Regressionsknoten zurückgibt. Die Tabelle NODE_DISTRIBUTION enthält Einzelheiten der Regressionsformel. In diesem Beispiel werden die Spalten vereinfacht, und für die NODE_DISTRIBUTION-Tabelle wird ein Alias verwendet, um sie übersichtlicher anzuzeigen. In diesem Modell wurden jedoch keine Regressoren gefunden, die „Income“ mit anderen kontinuierlichen Attributen in Beziehung setzen. In solchen Fällen gibt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] den Mittelwert des Attributs und die Gesamtvarianz im Modell für dieses Attribut zurück.  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 Beispielergebnisse:  
  
|T.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Yearly Income|Missing|0|0.000457142857142857|0|1|  
|Yearly Income|57220.8876687257|17484|0.999542857142857|1041275619.52776|3|  
||57220.8876687257|0|0|1041216662.54387|11|  
  
 Weitere Informationen zu den einzelnen Werttypen für Regressionsmodelle finden Sie unter [Miningmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).  
  
## <a name="list-of-prediction-functions"></a>Liste der Vorhersagefunktionen  
 Alle Algorithmen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] unterstützen einen gemeinsamen Funktionssatz. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus unterstützt jedoch zusätzliche Funktionen, die in der folgenden Tabelle aufgeführt werden.  
  
|||  
|-|-|  
|Vorhersagefunktion|Verwendung|  
|[IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx)|Bestimmt, ob ein Knoten ein untergeordnetes Element eines anderen Knotens im Modell ist.|  
|[IsInNode &#40;DMX&#41;](/sql/dmx/isinnode-dmx)|Zeigt an, ob der angegebene Knoten den aktuellen Fall enthält.|  
|[PredictAdjustedProbability &#40;DMX&#41;](/sql/dmx/predictadjustedprobability-dmx)|Gibt die gewichtete Wahrscheinlichkeit zurück.|  
|[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx)|Sagt eine Mitgliedschaft in einem assoziativen Dataset voraus.|  
|[PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)|Gibt eine Tabelle mit Werten zurück, die sich auf den aktuellen vorhergesagten Wert beziehen.|  
|[PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx)|Gibt "Node_ID" für jeden Fall zurück.|  
|[PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx)|Gibt die Wahrscheinlichkeit für den vorhergesagten Wert zurück.|  
|[PredictStdev &#40;DMX&#41;](/sql/dmx/predictstdev-dmx)|Gibt die vorhergesagte Standardabweichung für die angegebene Spalte zurück.|  
|[PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx)|Gibt den Unterstützungswert für einen bestimmten Status zurück.|  
|[PredictVariance &#40;DMX&#41;](/sql/dmx/predictvariance-dmx)|Gibt die Varianz einer angegebenen Spalte zurück.|  
  
 Eine Liste der Funktionen, die von allen [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Algorithmen verwendet werden, finden Sie unter [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx). Die Syntax einzelner Funktionen finden Sie unter [Data Mining-Erweiterungen &#40;DMX&#41; – Funktionsreferenz](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Abfragen](data-mining-queries.md)   
 [Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm.md)   
 [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md)   
 [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
