---
title: Technische Referenz für den Microsoft Naive Bayes-Algorithmus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622297"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a>Technische Referenz für den Microsoft Naive Bayes-Algorithmus
  Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus ist ein Klassifizierungs Algorithmus, der von zur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Verwendung bei der Vorhersage Modellierung bereitgestellt wird. Der Algorithmus berechnet die bedingte Wahrscheinlichkeit zwischen Eingabespalten und vorhersagbaren Spalten und setzt die Unabhängigkeit der Spalten voraus. Diese Annahme der Unabhängigkeit führt zum Namen Naive Bayes.  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a>Implementierung des Microsoft Naive Bayes-Algorithmus  
 Der Rechenaufwand für diesen Algorithmus ist geringer als der der anderen [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Algorithmen und ist daher hilfreich für das schnelle Generieren von Miningmodellen, um Beziehungen zwischen Eingabespalten und vorhersagbaren Spalten zu ermitteln. Der Algorithmus berücksichtigt jedes Eingabeattributwertpaar und Ausgabeattributwertpaar.  
  
 Eine Beschreibung der mathematischen Eigenschaften des Bayes-Theorems würde den Rahmen dieser Dokumentation sprengen. Weitere Informationen finden Sie unter Microsoft Research im Dokument mit dem Titel [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029).  
  
 Eine Beschreibung, wie Wahrscheinlichkeiten in allen Modellen angepasst werden, um potenzielle fehlende Werte zu berücksichtigen, finden Sie unter [Fehlende Werte &#40;Analysis Services – Data Mining&#41;](missing-values-analysis-services-data-mining.md).  
  
### <a name="feature-selection"></a>Featureauswahl  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus führt eine automatische Funktionsauswahl durch, um die Zahl der Werte, die beim Erstellen des Modells berücksichtigt werden, einzuschränken. Weitere Informationen finden Sie unter [Funktionsauswahl &#40;Data Mining&#41;](feature-selection-data-mining.md).  
  
|Algorithmus|Analysemethode|Kommentare|  
|---------------|------------------------|--------------|  
|Naive Bayes|Shannon-Entropie<br /><br /> Bayes-Methode mit K2-A-priori-Verteilung<br /><br /> Bayes-Dirichlet mit uniformer A-priori-Verteilung (Standard)|Der Naive Bayes-Algorithmus akzeptiert nur diskrete oder diskretisierte Attribute, daher kann er den Interessantheitsgrad nicht verwenden.|  
  
 Der Algorithmus ist so konzipiert, dass die Verarbeitungszeit minimiert wird und die Attribute mit der höchsten Wichtigkeit effizient ausgewählt werden. Sie können jedoch steuern, welche Daten der Algorithmus verwendet, indem Sie die Parameter wie folgt festlegen:  
  
-   Um die Werte einzuschränken, die als Eingaben verwendet werden, setzen Sie den Wert von MAXIMUM_INPUT_ATTRIBUTES herab.  
  
-   Um die Anzahl der vom Modell analysierten Attribute einzuschränken, setzen Sie den Wert von MAXIMUM_OUTPUT_ATTRIBUTES herab.  
  
-   Um die Anzahl der Werte zu beschränken, die für ein Attribut berücksichtigt werden können, setzen Sie den Wert von MINIMUM_STATES herab.  
  
## <a name="customizing-the-naive-bayes-algorithm"></a>Anpassen des Naive Bayes-Algorithmus  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus unterstützt mehrere Parameter, die Auswirkungen auf das Verhalten, die Leistung und die Genauigkeit des resultierenden Miningmodells haben. Sie können außerdem Modellierungsflags für die Modellspalten festlegen, um die Verarbeitung der Daten zu steuern, oder Flags für die Miningstruktur setzen, um anzugeben, wie fehlende oder NULL-Werte behandelt werden sollen.  
  
### <a name="setting-algorithm-parameters"></a>Festlegen von Algorithmusparametern  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus unterstützt mehrere Parameter, die Auswirkungen auf die Leistung und die Genauigkeit des resultierenden Miningmodells haben. In der folgenden Tabelle wird jeder Parameter beschrieben.  
  
 *MAXIMUM_INPUT_ATTRIBUTES*  
 Gibt die maximale Anzahl von Eingabeattributen an, die der Algorithmus verarbeiten kann, bevor die Funktionsauswahl aufgerufen wird. Wenn dieser Wert auf 0 festgelegt wird, ist die Funktionsauswahl für Eingabeattribute deaktiviert.  
  
 Der Standardwert ist 255.  
  
 *MAXIMUM_OUTPUT_ATTRIBUTES*  
 Gibt die maximale Anzahl von Ausgabeattributen an, die der Algorithmus verarbeiten kann, bevor die Funktionsauswahl aufgerufen wird. Wenn dieser Wert auf 0 festgelegt wird, ist die Funktionsauswahl für Ausgabeattribute deaktiviert.  
  
 Der Standardwert ist 255.  
  
 *MINIMUM_DEPENDENCY_PROBABILITY*  
 Gibt die minimale Abhängigkeitswahrscheinlichkeit zwischen Eingabe- und Ausgabeattributen an. Dieser Wert wird verwendet, um die Größe der vom Algorithmus generierten Inhalte zu beschränken. Diese Eigenschaft kann Werte zwischen 0 und 1 annehmen. Größere Werte reduzieren die Anzahl von Attributen im Inhalt des Modells.  
  
 Der Standardwert ist 0,5.  
  
 *MAXIMUM_STATES*  
 Gibt die maximale Anzahl der vom Algorithmus unterstützten Attributstatus an. Wenn die Anzahl der Status eines Attributs größer als die maximale Anzahl von Zuständen ist, verwendet der Algorithmus die beliebtesten Zustände des Attributs und behandelt die restlichen Zustände als fehlend.  
  
 Der Standardwert ist 100.  
  
### <a name="modeling-flags"></a>Modellierungsflags  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Tree-Algorithmus unterstützt die folgenden Modellierungsflags. Wenn Sie die Miningstruktur oder das Miningmodell erstellen, definieren Sie Modellierungsflags, die angeben, wie die Werte in den einzelnen Spalten während der Analyse behandelt werden. Weitere Informationen finden Sie unter [Modellierungsflags &#40;Data Mining&#41;](modeling-flags-data-mining.md).  
  
|Modellierungsflag|BESCHREIBUNG|  
|-------------------|-----------------|  
|MODEL_EXISTENCE_ONLY|Dies bedeutet, dass die Spalte zwei mögliche Statuswerte haben kann: Missing und Existing. Ein NULL-Wert ist ein fehlender Wert.<br /><br /> Gilt für die Miningmodellspalte.|  
|NOT NULL|Gibt an, dass die Spalte keinen NULL-Wert enthalten kann. Ein Fehler tritt auf, wenn Analysis Services während des Modelltrainings einen NULL-Wert erkennt.<br /><br /> Gilt für die Miningstrukturspalte.|  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Ein Naive Bayes-Strukturmodell muss eine Schlüsselspalte, mindestens ein vorhersagbares Attribut und mindestens ein Eingabeattribut enthalten. Kein Attribut darf kontinuierlich sein. Wenn die Daten kontinuierliche numerische Daten enthalten, werden sie ignoriert oder diskretisiert.  
  
### <a name="input-and-predictable-columns"></a>Eingabespalten und vorhersagbare Spalten  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus unterstützt bestimmte Eingabespalten und vorhersagbare Spalten. Diese sind in der nachstehenden Tabelle aufgelistet. Weitere Informationen zur Bedeutung der Inhaltstypen in einem Miningmodell finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md).  
  
|Spalte|Inhaltstypen|  
|------------|-------------------|  
|Eingabeattribut|Cyclical, Discrete, Discretized, Key, Table und Ordered|  
|Vorhersagbares Attribut|Cyclical, Discrete, Discretized, Table und Ordered|  
  
> [!NOTE]  
>  Zyklische und sortierte Inhaltstypen werden unterstützt, der Algorithmus behandelt sie jedoch als diskrete Werte und führt keine spezielle Verarbeitung durch.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Naive Bayes-Algorithmus](microsoft-naive-bayes-algorithm.md)   
 [Naive Bayes-Modell Abfrage Beispiele](naive-bayes-model-query-examples.md)   
 [Miningmodellinhalt von Naive Bayes-Modellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
