---
title: Microsoft Linear Regression-Algorithmus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 50a4abb8-c0b0-4380-ba5e-c49b305b9d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d03f4d60131471d1a978fd66306cc73f274a536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622302"
---
# <a name="microsoft-linear-regression-algorithm"></a>Microsoft Linear Regression-Algorithmus
  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus ist eine Variation des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus, der Ihnen dabei hilft, eine lineare Beziehung zwischen einer abhängigen und einer unabhängigen Variablen zu berechnen und diese zur Vorhersage zu verwenden.

 Die Beziehung nimmt die Form einer Formel für eine Linie an, die eine Reihe von Daten am besten darstellt. Die Linie des folgenden Diagramms ist z. B. die bestmögliche lineare Darstellung der Daten.

 ![Eine Gerade als Modell für eine Datenmenge](../media/linear-regression.gif "Eine Gerade als Modell für eine Datenmenge")

 Zu jedem Datenpunkt im Diagramm ist ein Fehler zugeordnet. Dieser wird durch seinen Abstand von der Regressionslinie dargestellt. Der Koeffizient a und der Koeffizient b in der Regressionsgleichung passen den Winkel und die Position der Regressionsgleichung an. Sie können die Regressionsgleichung abrufen, indem Sie a und b anpassen, bis die Summe der Fehler, die mit allen Punkten verknüpft sind, ein Minimum erreicht hat.

 Es gibt andere Arten der Regression, die mehrere Variablen verwenden, sowie nicht lineare Methoden der Regression. Die lineare Regression stellt jedoch eine nützliche und bekannte Methode dar, um eine Antwort auf eine Änderung eines zugrunde liegenden Faktors zu modellieren.

## <a name="example"></a>Beispiel
 Sie können die lineare Regression verwenden, um eine Beziehung zwischen zwei kontinuierlichen Spalten zu bestimmen. Beispielsweise können Sie die lineare Regression verwenden, um eine Trendlinie aus Produktions- oder Umsatzdaten zu berechnen. Sie können die lineare Regression ebenfalls als Vorstufe für die Entwicklung komplexerer Data Mining-Modelle verwenden, um die Beziehungen zwischen Datenspalten zu bewerten.

 Es gibt zahlreiche Möglichkeiten zur Berechnung von linearer Regression, für die keine Data Mining-Tools erforderlich sind. Der Vorteil der Verwendung des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus für diese Aufgabe liegt darin, dass alle möglichen Beziehungen zwischen den Variablen automatisch berechnet und getestet werden. Sie müssen kein Rechenverfahren festlegen, wie z. B. die Methode der kleinsten Quadrate. Die lineare Regression könnte jedoch die Beziehungen in Szenarios zu stark vereinfachen, in denen das Ergebnis durch mehrere Faktoren beeinflusst wird.

## <a name="how-the-algorithm-works"></a>Funktionsweise des Algorithmus
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus ist eine Variation des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus. Bei Auswahl des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus wird ein Sonderfall des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus mit Parametern, die das Verhalten des Algorithmus einschränken und bestimmte Eingabedatentypen erfordern, aufgerufen. Zudem wird das gesamte Dataset in einem linearen Regressionsmodell dazu verwendet, Beziehungen im ersten Durchgang zu berechnen, während ein standardmäßiges Entscheidungsstrukturmodell Daten wiederholt in kleinere Teilmengen oder Strukturen aufteilt.

## <a name="data-required-for-linear-regression-models"></a>Erforderliche Daten für lineare Regressionsmodelle
 Wenn Sie Daten für die Verwendung in einem linearen Regressionsmodell aufbereiten, müssen Sie sich mit den Anforderungen des jeweiligen Algorithmus vertraut machen. Hierbei müssen Sie auch berücksichtigen, welcher Datenumfang erforderlich ist und wie diese Daten verwendet werden. Für diesen Modelltyp gelten folgende Anforderungen:

-   **Nur eine Schlüsselspalte:** Jedes Modell muss eine numerische Spalte oder Textspalte enthalten, die jeden Datensatz eindeutig identifiziert. Verbundschlüssel sind nicht zulässig.

-   **Eine vorhersagbare Spalte** Mindestens eine vorhersagbare Spalte ist erforderlich. Sie können mehrere vorhersagbare Attribute in ein Modell aufnehmen, bei denen es sich jedoch um kontinuierliche numerische Datentypen handeln muss. Sie können keinen datetime-Datentyp als vorhersagbares Attribut verwenden, selbst wenn der systemeigene Speicher für die Daten numerisch ist.

-   **Eingabespalten** Eingabespalten müssen kontinuierliche numerische Daten enthalten, und ihnen muss der entsprechende Datentyp zugewiesen sein.

 Weitere Informationen finden Sie im Abschnitt „Anforderungen“ unter [Technische Referenz für den Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm-technical-reference.md).

## <a name="viewing-a-linear-regression-model"></a>Anzeigen eines linearen Regressionsmodells
 Verwenden Sie den **Microsoft Struktur-Viewer**, um das Modell zu durchsuchen. Die Baumstruktur eines linearen Regressionsmodells ist sehr einfach. Alle Informationen zur Regressionsformel sind in einem einzelnen Knoten enthalten. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Struktur-Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).

 Wenn Sie Näheres über die Formel in Erfahrung bringen möchten, können Sie die Koeffizienten und weitere Details mithilfe des [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)anzeigen.

 Zum Inhalt eines linearen Regressionsmodells zählen Metadaten, die Regressionsformel und statistische Informationen zur Verteilung der Eingabewerte. Weitere Informationen finden Sie unter [Miningmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).

## <a name="creating-predictions"></a>Erstellen von Vorhersagen
 Nachdem das Modell verarbeitet wurde, werden die Ergebnisse als Satz von Statistiken gemeinsam mit der linearen Regressionsformel gespeichert, die Sie zum Berechnen zukünftiger Entwicklungen verwenden können. Beispiele zur Verwendung von Abfragen in Verbindung mit einem linearen Regressionsmodell finden Sie unter [Beispiele für lineare Regressionsmodellabfrage](linear-regression-model-query-examples.md).

 Allgemeine Informationen zum Erstellen von Abfragen für Miningmodelle finden Sie unter [Data Mining-Abfragen](data-mining-queries.md).

 Wenn es sich bei dem vorhersagbaren Attribut um einen kontinuierlichen numerischen Datentyp handelt, können Sie neben der Erstellung eines linearen Regressionsmodells durch Auswahl des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression-Algorithmus auch ein Entscheidungsstrukturmodell entwickeln, das Regressionen enthält. In diesem Fall teilt der Algorithmus die Daten, sofern entsprechende Trennpunkte gefunden werden. Für einige Datenbereiche wird jedoch stattdessen eine Regressionsformel erstellt. Weitere Informationen über Regressionsstrukturen innerhalb eines Entscheidungsstrukturmodells finden Sie unter [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).

## <a name="remarks"></a>Bemerkungen

-   Unterstützt nicht die Verwendung von PMML (Predictive Model Markup Language) zum Erstellen von Miningmodellen.

-   Unterstützt nicht die Erstellung von Data Mining-Dimensionen.

-   Unterstützt Drillthrough.

-   Unterstützt die Verwendung von OLAP-Miningmodellen.

## <a name="see-also"></a>Weitere Informationen
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft LinearRegression-Algorithmus Technische Referenz](microsoft-linear-regression-algorithm-technical-reference.md) [lineare Regressionsmodell Abfrage Beispiele](linear-regression-model-query-examples.md) [Mining Modell Inhalt von linearen Regressionsmodellen &#40;Analysis Services-Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)


