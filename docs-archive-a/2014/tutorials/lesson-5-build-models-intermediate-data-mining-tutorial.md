---
title: 'Lektion 5: aufbauen von neuronalen Netzwerk-und logistischen Regressionsmodellen (Data Mining-Tutorial für Fortgeschrittene) Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a8c9fcf0380582f15fa2bf30d6fdeb97bb2ab1fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616865"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a>Lektion 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen (Data Mining-Lernprogramm für Fortgeschrittene)
  
  
 Die Betriebsabteilung von [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] arbeitet daran, die Kundenzufriedenheit bezüglich des Callcenters zu verbessern. Ein Drittanbieter wurde mit der Führung des Callcenters und der Erstellung von Berichten zu Metriken bezüglich der Effektivität des Callcenters beauftragt. Ihre Aufgabe ist es, einige vorläufige durch den Drittanbieter bereitgestellte Daten zu analysieren. Ihr Auftraggeber möchte wissen, ob es interessante Ergebnisse gibt. Insbesondere ist interessant, ob die Daten Rückschlüsse auf Probleme mit der Personalbesetzung zulassen oder Möglichkeiten aufzeigen, die Kundenzufriedenheit zu verbessern.  
  
 Das Dataset ist klein und umfasst nur einen Zeitraum von 30 Tagen im Betrieb des Callcenters. Die Daten verfolgen die Anzahl der neuen und erfahrenen Operatoren in jeder Schicht, die Anzahl der eingehenden Aufrufe, die Anzahl von Bestellungen und zu lösenden Problemen sowie die durchschnittlich Wartezeit eines Kunden, bis ein Operator auf einen Aufruf reagiert. Die Daten enthalten zudem eine Dienstqualitätsmetrik auf Grundlage der *Abbruchrate*, die ein Indikator der Kundenfrustration ist.  
  
 Da Sie im Voraus keine bestimmten Ergebnisse von der Datenanalyse erwarten, beschließen Sie, mithilfe eines neuronalen Netzwerkmodells die Daten auf mögliche Korrelationen zu durchsuchen. Neuronale Netzwerkmodelle werden oft zum Durchsuchen von Daten verwendet, da mit diesen komplexe Beziehungen zwischen vielen Eingaben und Ausgaben analysiert werden können.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In dieser Lektion verwenden Sie den Neural Network-Algorithmus, um ein Modell zu erstellen, das Sie und das Betriebsteam verwenden können, um die Trends in den Daten zu verstehen. Als Teil dieser Lektion versuchen Sie, die folgenden Fragen zu beantworten:  
  
-   Welche Faktoren beeinflussen die Kundenzufriedenheit?  
  
-   Wie kann das Callcenter die Dienstqualität verbessern?  
  
 Auf Grundlage der Ergebnisse erstellen Sie dann ein logistisches Regressionsmodell, das Sie für Vorhersagen verwenden können. Die Vorhersagen werden vom Betriebsteam für die Betriebsplanung des Callcenters verwendet.  
  
 Diese Lektion enthält die folgenden Themen:  
  
-   [Hinzufügen einer Datenquellen Sicht für callcenterdata &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [Erstellen einer neuronalen Netzwerkstruktur und eines Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Untersuchen des Callcentermodells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [Hinzufügen eines logistischen Regressionsmodells zur Callcenterstruktur &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [Erstellen von Vorhersagen für die Callcentermodelle &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Hinzufügen einer Datenquellen Sicht für callcenterdata &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der Data Mining-Lösung für fortgeschrittene &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Data Mining-Tutorial für Fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 4: Entwickeln eines Sequence Clustering-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 Lektion 5: Neuronale Netzwerk- und logistische Regressionsszenarios (Data Mining-Tutorial für Fortgeschrittene)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
