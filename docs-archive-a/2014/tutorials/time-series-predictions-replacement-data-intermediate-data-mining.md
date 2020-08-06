---
title: Zeitreihen Vorhersagen mit Ersetzungs Daten (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a23a6e1d-1d49-41ea-8314-925dc8e4df5e
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c96b70775105ea9446810ac3b064ae7cb07d4337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608128"
---
# <a name="time-series-predictions-using-replacement-data-intermediate-data-mining-tutorial"></a>Erstellen von Zeitreihenvorhersagen mit Ersetzungsdaten (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe erstellen Sie auf Grundlage weltweiter Umsatzdaten ein neues Modell. Sie erstellen dann eine Vorhersageabfrage, mit der Sie das weltweite Umsatzmodell auf eine einzelnen Region anwenden.  
  
## <a name="building-a-general-model"></a>Erstellen eines allgemeinen Modells  
 Denken Sie daran, dass die Analyse der Ergebnisse des ursprünglichen Miningmodells große Unterschiede zwischen Regionen und Produktreihen aufgedeckt hat. Das M200-Modell verzeichnete beispielsweise einen starken Umsatz für Nordamerika, was für die Verkäufe des T1000-Modells nicht der Fall war. Die Analyse wird jedoch durch die Tatsache erschwert, dass einige Reihen keine großen Daten haben oder dass Daten zu einem anderen Zeitpunkt gestartet wurden. Darüber hinaus fehlten einige Daten.  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Um einige dieser Data Quality-Probleme zu beheben, entscheiden Sie sich für eine Zusammenführung der weltweiten Umsatzdaten, um aus diesem Satz allgemeiner Verkaufstrends ein allgemeines Modell zu erstellen, mit dem zukünftige Verkäufe in einer beliebigen Region vorhergesagt werden können.  
  
 Wenn Sie Vorhersagen erstellen, wenden Sie das an den weltweiten Umsatzdaten trainierte Muster an, ersetzen aber die Vergangenheitsdaten-Punkte durch die Umsatzdaten jeder einzelnen Region. So wird die Form des Trends beibehalten, während die vorhergesagten Werte an den historischen Umsatzzahlen für jede Region und jedes Modell ausgerichtet werden.  
  
## <a name="performing-cross-prediction-with-a-time-series-model"></a>Kreuzvorhersagen mit einem Zeitreihenmodell  
 Das Verfahren, die Daten aus einer Reihe zur Vorhersage von Trends in einer anderen Reihe zu verwenden, wird "Kreuzvorhersage" genannt. Sie können Kreuzvorhersagen in vielen Szenarien verwenden: Sie könnten z. B. entscheiden, dass die Verkäufe von Fernsehern gute Rückschlüsse bei der Vorhersage der wirtschaftlichen Aktivität allgemein sind, und wenden ein an Umsatzdaten von Fernsehern trainiertes Modell auf allgemeine Wirtschaftsdaten an.  
  
 In SQL Server Data Mining führen Sie Kreuz Vorhersagen durch die Verwendung des-Parameters REPLACE_MODEL_CASES in den Argumenten der-Funktion, " [prättimeseries" &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx).  
  
 In der nächsten Aufgabe lernen Sie, wie REPLACE_MODEL_CASES verwendet wird. Sie erstellen aus den zusammengeführten Weltumsatzdaten ein Modell und dann eine Vorhersageabfrage, die das allgemeine Modell den Ersatzdaten zuordnet.  
  
 Es wird davon ausgegangen, dass Sie inzwischen mit dem Erstellen von Data Mining-Modelle vertraut sind; daher wurden die Anweisungen zum Erstellen des Modells vereinfacht.  
  
#### <a name="to-build-a-mining-structure-and-mining-model-using-the-aggregated-data"></a>So erstellen Sie eine Miningstruktur und ein Miningmodell mit den aggregierten Daten  
  
1.  Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf **Mining Strukturen**, und wählen Sie dann **neue Mining Struktur** aus, um den Data Mining-Assistenten zu starten.  
  
2.  Wählen Sie im Data Mining-Assistenten folgende Optionen aus:  
  
    -   Algorithmus: Microsoft Time Series  
  
    -   Verwenden Sie die Datenquelle, die Sie in dieser fortgeschrittenen Lektion bereits als Quelle für das Modell erstellt haben. Siehe [Erweiterte Zeitreihen Vorhersagen &#40;Data Mining ](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene&#41;.  
  
         Datenquellen Sicht:`AllRegions`  
  
    -   Wählen Sie die folgenden Spalten für den Reihenschlüssel und den Zeitschlüssel aus:  
  
         Schlüsselzeit: ReportingDate  
  
         Schlüssel: Region  
  
    -   Wählen Sie die folgenden Spalten für `Input` und `Predict` aus:  
  
         SumQty  
  
         SumAmt  
  
         AvgAmt  
  
         AvgQty  
  
    -   Geben Sie für **Mining Struktur Name**Folgendes ein:`All Regions`  
  
    -   Geben Sie für **Mining Modellname**Folgendes ein:`All Regions`  
  
3.  Verarbeiten Sie die neue Struktur und das neue Modell.  
  
#### <a name="to-build-the-prediction-query-and-map-the-replacement-data"></a>So erstellen Sie die Vorhersageabfrage und ordnen Ersetzungsdaten zu  
  
1.  Wenn das Modell nicht bereits geöffnet ist, doppelklicken Sie auf die AllRegions-Struktur, und klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
2.  Im Bereich **Mining Modell** sollte das Modell AllRegions bereits ausgewählt sein. Wenn diese Option nicht ausgewählt ist, klicken Sie auf **Modell auswählen**, und wählen Sie dann das Modell AllRegions aus.  
  
3.  Klicken Sie im Bereich **Eingabe Tabelle (n) auswählen** auf **Fall Tabelle auswählen**.  
  
4.  Ändern Sie im Dialogfeld **Tabelle auswählen** die Datenquelle in T1000 Pacific Region, und klicken Sie dann auf **OK**.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Joinlinie zwischen dem Mining Modell und den Eingabedaten, und wählen Sie **Verbindungen ändern**aus. Ordnen Sie die Daten in der Datenquellensicht wie folgt dem Modell zu:  
  
    1.  Vergewissern Sie sich, dass die ReportingDate-Spalte im Mining Modell der ReportingDate-Spalte in den Eingabedaten zugeordnet ist.  
  
    2.  Klicken Sie im Dialogfeld **Zuordnung ändern** in der Zeile für die AvgQty-Modell Spalte auf unter **Tabellenspalte** , und wählen Sie dann T1000 Pacific. Menge aus. Klicken Sie auf **OK**.  
  
         In diesem Schritt ordnen Sie die Spalte zu, die Sie im Modell für die Vorhersage der Durchschnittsmenge aus den tatsächlichen Umsatzdaten der Reihe T1000 erstellt haben.  
  
    3.  Ordnen Sie den Spalten Bereich im Modell keiner Eingabe Spalte zu.  
  
         Da die Daten aller Reihen im Modell aggregiert sind, findet kein Abgleich der Reihenwerte wie T1000 Pacific statt, und bei der Ausführung der Vorhersageabfrage wird ein Fehler ausgegeben.  
  
6.  Nun erstellen Sie die Vorhersageabfrage.  
  
     Fügen Sie zunächst den Ergebnissen eine Spalte hinzu, die die Bezeichnung "AllRegions" aus dem Modell zusammen mit den Vorhersagen ausgibt. So wissen Sie, dass die Ergebnisse auf dem allgemeinen Modell basieren.  
  
    1.  Klicken Sie im Raster auf die erste leere Zeile unter **Quelle**, und wählen Sie dann AllRegions-Mining Modell aus.  
  
    2.  Wählen Sie für **Feld**die Option Region aus.  
  
    3.  Geben **Alias**Sie als Alias **Model used**ein.  
  
7.  Im nächsten Schritt fügen Sie den Ergebnissen eine weitere Bezeichnung hinzu, der Sie entnehmen können, auf welche Reihe sich die Vorhersage bezieht.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**die Option **Benutzerdefinierter Ausdruck**aus.  
  
    2.  Geben Sie in der Spalte **Alias** die Bezeichnung **ModelRegion**ein.  
  
    3.  Geben Sie in der Spalte **Kriterium/Argument** den Namen ein `'T1000 Pacific'` .  
  
8.  Nun richten Sie die Funktion für die Kreuzvorhersage ein.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**die Option **Vorhersagefunktion**aus.  
  
    2.  Wählen Sie in der Spalte **Feld** die Option **prättimeseries**aus.  
  
    3.  Geben **Alias**Sie als Alias **vorhergesagte Werte**ein.  
  
    4.  Ziehen Sie das Feld AvgQty aus dem Bereich **Mining Modell** in die Spalte **Kriterium/Argument** , indem Sie den Drag & Drop-Vorgang verwenden.  
  
    5.  Geben Sie in der Spalte **Kriterium/Argument** nach dem Feldnamen den folgenden Text ein:`,5, REPLACE_MODEL_CASES`  
  
         Der vollständige Text des Textfelds **Kriterium/Argument** sollte wie folgt lauten:`[AllRegions].[AvgQty],5,REPLACE_MODEL_CASES`  
  
9. Klicken Sie auf **Ergebnisse**.  
  
## <a name="creating-the-cross-prediction-query-in-dmx"></a>Erstellen der Kreuzvorhersage-Abfrage in DMX  
 Möglicherweise ist Ihnen ein Problem aufgefallen, das bei Kreuzvorhersagen besteht: Sie müssen nämlich für jede Reihe eine neue Abfrage erstellen, um so das allgemeine Modell auf andere Datenreihen anwenden und jeden Satz von Eingaben dem Modell zuordnen zu können.  
  
 Sie haben aber die Möglichkeit, die Abfrage nicht im Designer zu erstellen, sondern zu DMX zu wechseln und die von Ihnen erstellte DMX-Anweisung zu bearbeiten. Die folgende DMX-Anweisung stellt beispielsweise die Abfrage dar, die Sie gerade erstellt haben:  
  
```  
SELECT  
      ([All Regions].[Region]) as [Model Used],  
      ('T-1000 Pacific') as [ModelRegion],  
      (PredictTimeSeries([All Regions].[Avg Qty],5, REPLACE_MODEL_CASES)) as [Predicted Quantity]  
     FROM [All Regions]  
PREDICTION JOIN  
    OPENQUERY([Adventure Works DW2003R2], 'SELECT [ReportingDate] FROM  
      (  
       SELECT  ReportingDate, ModelRegion, Quantity, Amount   
       FROM dbo.vTimeSeries   
       WHERE (ModelRegion = N''T1000 Pacific'')  
       ) as [T1000 Pacific]    ')   
    AS t  
ON   
[All Regions].[Reporting Date] = t.[ReportingDate]   
AND   
[All Regions].[Avg Qty] = t.[Quantity]  
```  
  
 Wenn Sie sie auf ein anderes Modell anwenden möchten, müssen Sie nur die Filterbedingung im Abfrageausdruck ersetzen und die mit den einzelnen Ergebnissen verknüpften Bezeichnungen aktualisieren.  
  
 Wenn Sie beispielsweise die Filterbedingungen und die Spaltenbezeichnungen ändern, indem Sie "Pacific" durch "North America" ersetzen, erhalten Sie Vorhersagen für das T1000-Produkt in Nordamerika auf Basis des allgemeinen Modells.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Vergleichen von Vorhersagen für Prognosemodelle &#40;Data&#41;Mining-Lernprogramm für Fortgeschrittene](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage Beispiele für Zeitreihen Modelle](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)  
  
  
