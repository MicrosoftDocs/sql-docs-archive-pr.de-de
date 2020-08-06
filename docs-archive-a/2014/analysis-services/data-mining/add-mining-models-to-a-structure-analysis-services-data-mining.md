---
title: Hinzufügen von Mining Modellen zu einer Struktur (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], creating
- mining models [Analysis Services], creating
- mining models [Analysis Services], modifying
ms.assetid: a175daa5-58ea-474c-a82f-9648c5155dc8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cc504016ac378a66795e7522365bd570cfca84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609542"
---
# <a name="add-mining-models-to-a-structure-analysis-services---data-mining"></a>Hinzufügen von Miningmodellen zu einer Struktur (Analysis Services - Data Mining)
  Eine Miningstruktur ist für die Unterstützung mehrerer Miningmodelle bestimmt. Nachdem Sie den Assistenten beendet haben, können Sie die Struktur öffnen und neue Miningmodelle hinzufügen. Jedes Mal, wenn Sie ein Modell erstellen, können Sie einen anderen Algorithmus verwenden, die Parameter ändern oder Filter anwenden, um eine andere Teilmenge der Daten zu verwenden.  
  
## <a name="adding-new-mining-models"></a>Hinzufügen von neuen Miningmodellen  
 Wenn Sie den Data Mining-Assistenten zur Erstellung eines neuen Miningmodells verwenden, müssen Sie standardmäßig zunächst immer eine Miningstruktur erstellen. Mithilfe des Assistenten ist die Option verfügbar, der Struktur ein ursprüngliches Miningmodell hinzuzufügen. Sie müssen jedoch nicht sofort ein Modell erstellen. Wenn Sie nur die Struktur erstellen, müssen Sie nicht entscheiden, welche Spalte als vorhersagbares Attribut verwendet werden soll oder wie die Daten in einem bestimmten Modell verwendet werden sollen. Stattdessen richten Sie nur die allgemeine Datenstruktur ein, die Sie künftig verwenden möchten. Später können Sie mit [Data Mining Designer](data-mining-designer.md) neue Miningmodelle hinzufügen, die auf der Struktur basieren.  
  
> [!NOTE]  
>  In DMX fängt die CREATE MINING MODEL-Anweisung mit dem Miningmodell an. Das heißt, Sie definieren die Auswahl des Miningmodells, und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert die zugrunde liegende Struktur automatisch. Später können Sie weitere Mining Modelle zu dieser Struktur hinzufügen, indem Sie die Alter Structure... Add Model-Anweisung.  
  
## <a name="choosing-an-algorithm"></a>Auswählen eines Algorithmus  
 Wenn Sie einer vorhandenen Struktur ein neues Modell hinzufügen, besteht der erste Schritte darin, einen Data Mining-Algorithmus für dieses Modell auszuwählen. Die Auswahl des Algorithmus ist wichtig, da jeder Algorithmus einen anderen Analysetyp ausführt und andere Anforderungen hat.  
  
 Wenn Sie einen Algorithmus auswählen, der mit den Daten nicht kompatibel ist, wird eine Warnung angezeigt. In einigen Fällen können Sie Spalten ignorieren, die nicht vom Algorithmus verarbeitet werden können. In anderen Fällen nimmt der Algorithmus die Anpassungen automatisch für Sie vor. Wenn die Struktur z. B. numerische Daten enthält und der Algorithmus nur mit diskreten Werten arbeiten kann, werden die numerischen Werte in diskrete Bereiche gruppiert. In einigen Fällen müssen Sie ggf. die Daten zuerst manuell korrigieren, indem Sie einen Schlüssel oder ein vorhersagbares Attribut auswählen.  
  
 Sie müssen den Algorithmus nicht ändern, wenn Sie ein neues Modell erstellen. Sie können oftmals sehr unterschiedliche Ergebnisse erhalten, wenn Sie den gleichen Algorithmus verwenden, aber die Daten filtern oder einen Parameter, wie beispielsweise die Clustermethode oder die Mindestgröße des Itemsets, ändern. Es wird empfohlen, dass Sie mit mehreren Modellen experimentieren, um zu sehen, welche Parameter zu den besten Ergebnissen führen.  
  
 Beachten Sie, dass alle neuen Modelle verarbeitet werden müssen, bevor Sie sie verwenden können.  
  
## <a name="specifying-the-usage-of-columns-in-a-new-mining-model"></a>Angeben der Spaltenverwendung in einem neuen Miningmodell  
 Wenn Sie einer vorhandenen Miningstruktur neue Miningmodelle hinzufügen, müssen Sie angeben, wie jede Datenspalte vom Modell verwendet werden soll. Abhängig vom Algorithmustyp, den Sie für das Modell auswählen, werden einige dieser Auswahlen standardmäßig durchgeführt. Wenn Sie keinen Verwendungstyp für eine Spalte angeben, wird die Spalte nicht in die Miningstruktur übernommen. Die Daten in der Spalte können jedoch immer noch für Drillthrough verfügbar sein, wenn das Modell dies unterstützt.  
  
 Spalten in der Miningstruktur, die vom Modell verwendet werden (wenn "Ignorieren" nicht festgelegt ist), müssen ein Schlüssel, eine Eingabespalte, eine vorhersagbare Spalte oder eine vorhersagbare Spalte für die Werte sein, die auch als Eingaben für das Modell verwendet werden.  
  
-   Schlüsselspalten enthalten einen eindeutigen Bezeichner für jede Zeile in einer Tabelle. Einige Miningmodelle, wie die Modelle auf der Basis von Sequenzcluster- und Zeitreihen-Algorithmen, können mehrere Schlüsselspalten enthalten. Diese mehrfachen Schlüssel sind jedoch keine Verbundschlüssel im relationalen Sinn, sondern müssen zur Unterstützung von Zeitreihen und der Analyse des Sequenzclustering ausgewählt werden.  
  
-   Eingabespalten stellen die Informationen bereit, aus denen Vorhersagen erstellt werden. Der Data Mining-Assistent stellt die Funktion **Vorschlagen** bereit, die aktiviert ist, wenn Sie eine vorhersagbare Spalte auswählen. Wenn Sie auf diese Schaltfläche klicken, führt der Assistent eine Stichprobe für die vorhersagbaren Werte durch und bestimmt, welche der anderen Spalten in der Struktur gute Variablen aufweisen. Schlüsselspalten oder andere Spalten mit vielen eindeutigen Werten werden abgelehnt und Spalten vorgeschlagen, die mit dem Ergebnis korrelieren.  
  
     Diese Funktion ist besonders praktisch, wenn Datasets mehr Spalten enthalten, als Sie eigentlich zur Erstellung eines Miningmodells benötigen. Die Funktion **Vorschlagen** berechnet einen numerischen Ergebniswert von 0 bis 1, der die Beziehung zwischen jeder Spalte im Dataset und der vorhersagbaren Spalte beschreibt. Auf Grundlage des Ergebniswerts empfiehlt die Funktion Spalten, die als Eingabespalten für das Miningmodell verwendet werden können. Wenn Sie die Funktion **Vorschlagen** verwenden, können Sie entweder die vorgeschlagenen Spalten verwenden, die Auswahl Ihren Anforderungen entsprechend anpassen oder die Vorschläge ignorieren.  
  
-   Vorhersagbare Spalten enthalten die Informationen, die im Miningmodell vorhergesagt werden sollen. Sie können mehrere Spalten als vorhersagbare Attribute auswählen. Clusteringmodelle stellen eine Ausnahme dar, da ein vorhersagbares Attribut optional ist.  
  
     Abhängig vom Modelltyp muss die vorhersagbare Spalte ggf. ein bestimmter Datentyp sein: ein lineares Regressionsmodell benötigt z. B. eine numerische Spalte als vorhergesagten Wert; der Naive Bayes-Algorithmus erfordert einen diskreten Wert (und alle Eingaben müssen auch diskret sein).  
  
## <a name="specifying-column-content"></a>Angeben von Spalteninhalt  
 Für einige Spalten müssen Sie gegebenenfalls auch den *Spalteninhalt*angeben. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining weist die Eigenschaft Content Type der einzelnen Datenspalten den Algorithmus an, wie die Daten in der entsprechenden Spalte zu verarbeiten sind. Wenn Ihre Daten eine Spalte Income beinhalten, müssen Sie angeben, dass die Spalte fortlaufende Nummern enthält, indem Sie den Content Type auf Continuous festlegen. Sie können jedoch auch angeben, dass die Nummern in der Spalte Income in Buckets gruppiert werden. Legen Sie dazu die Eigenschaft Content Type auf Discretized fest, und geben Sie wahlweise die genaue Zahl der Buckets an. Sie können verschiedene Modelle erstellen, die die Spalten auf unterschiedliche Weise verarbeiten. Beispielsweise können Sie ein Modell ausprobieren, das Kunden in drei Altersgruppen einteilt, und ein anderes Modell mit zehn Altersgruppen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](mining-structures-analysis-services-data-mining.md)   
 [Erstellen einer relationalen Mining Struktur](create-a-relational-mining-structure.md)   
 [Mining Modell Eigenschaften](mining-model-properties.md)   
 [Miningmodellspalten](mining-model-columns.md)  
  
  
