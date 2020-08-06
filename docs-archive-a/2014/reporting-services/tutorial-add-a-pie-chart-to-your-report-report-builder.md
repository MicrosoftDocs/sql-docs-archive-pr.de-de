---
title: 'Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720962"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a>Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator)
  Kreis- und Ringdiagramme zeigen Daten als Teile des Ganzen an. Kreisdiagramme werden häufig verwendet, um Vergleiche zwischen Gruppen zu erstellen. Kreis-und Ring Diagramme bilden zusammen mit Pyramiden-und Trichter Diagrammen eine Gruppe von Diagrammen, die als Form Diagramme bezeichnet werden. Formdiagramme haben keine Achsen. Wenn ein numerisches Feld auf einem Formdiagramm abgelegt wird, berechnet das Diagramm den prozentualen Anteil jedes einzelnen Werts der Gesamtsumme.  
  
 Wenn in einem Kreisdiagramm zu viele Datenpunkte vorhanden sind, können die Datenpunktbezeichnungen zu überfüllt sein, um sie zu lesen. In diesem Fall sollten Sie die Verwendung eines Liniendiagramms erwägen. Verwenden Sie Kreisdiagramme möglichst nur, nachdem Sie die Daten bereits zu einer kleineren Anzahl von Datenpunkten aggregiert haben.  
  
 Die folgende Abbildung zeigt das Kreisdiagramm, das Sie erstellen.  
  
 ![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Was Sie lernen werden  
 In diesem Tutorial lernen Sie Folgendes:  
  
1.  [Erstellen eines Kreisdiagramms im Diagramm-Assistenten](#Chart)  
  
2.  [Auswählen des Diagrammtyps](#ChartType)  
  
3.  [Anzeigen von Prozentsätzen in jedem Slice](#Percentages)  
  
4.  [Kombinieren von kleinen Slices zu einem Slice](#CombineSlices)  
  
5.  [Anpassen des Zeichnungseffekts](#DrawingEffect)  
  
6.  [Hinzufügen eines Berichts Titels](#Title)  
  
7.  [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in zwei Verfahren zusammengefasst. Im ersten Tutorial dieser Reihe erhalten Sie detaillierte Anweisungen zum Navigieren zu einem Berichtsserver, Hinzufügen einer Datenquelle und Hinzufügen eines Datasets: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Ungefähre Dauer dieses Lernprogramms: 10 Minuten  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a>1. Erstellen eines Kreis Diagramms im Diagramm-Assistenten  
 Erstellen Sie im Dialogfeld Erste Schritte mithilfe des Diagramm-Assistenten ein eingebettetes Dataset, wählen Sie eine freigegebene Datenquelle aus, und erstellen Sie ein Kreisdiagramm.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-new-chart-report"></a>So erstellen Sie einen neuen Diagrammbericht  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld Erste Schritte wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld "Getting Started" nicht angezeigt wird, klicken Sie auf der Schaltfläche "Berichts-Generator" auf **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Diagramm-Assistent**.  
  
4.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus. Klicken Sie anschließend auf **Weiter**. Möglicherweise müssen Benutzername und Kennwort eingegeben werden.  
  
    > [!NOTE]  
    >  Welche Datenquelle Sie auswählen, ist unwichtig, solange Sie über ausreichende Berechtigungen verfügen. Aus der Datenquelle werden keine Daten abgerufen. Weitere Informationen finden Sie unter [Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
6.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **als Text bearbeiten**.  
  
7.  Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  (Optional) Klicken Sie auf die Schaltfläche Ausführen (**!**), um die Daten anzuzeigen, auf denen das Diagramm basiert.  
  
9. Klicken Sie auf **Weiter**.  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. Wählen Sie den Diagrammtyp aus.  
 Sie können aus einer Vielzahl vordefinierter Diagrammtypen auswählen.  
  
#### <a name="to-add-a-pie-chart"></a>So fügen Sie ein Kreisdiagramm hinzu  
  
1.  Klicken Sie auf der Seite **Diagrammtyp auswählen** **auf Kreis, und**klicken Sie dann auf **weiter**. Die Seite **Diagrammfelder anordnen** wird geöffnet.  
  
     Ziehen Sie auf der Seite **Diagrammfelder anordnen** das Feld „Product“ in den Bereich **Kategorien** . Kategorien definieren die Anzahl von Slices im Kreisdiagramm. In diesem Beispiel werden acht Slices verwendet, eines für jedes Produkt.  
  
2.  Ziehen Sie das Feld „Sales“ in den Bereich **Werte** . Das Feld "Sales" stellt den Umsatz für die Unterkategorie dar. Im Bereich **Werte** wird `[Sum(Sales)]` angezeigt, da im Diagramm der aggregierte Wert für die einzelnen Produkte angezeigt wird.  
  
3.  Klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite Format **auswählen** im Bereich Stile einen Stil aus.  
  
     Ein Format dient zum Angeben eines Schriftschnitts, einer Farbpalette und einer Rahmenart. Wenn Sie ein Format auswählen, wird im Vorschaubereich ein Beispiel für das Diagramm mit diesem Format angezeigt.  
  
5.  Klicken Sie auf **Fertig stellen**.  
  
     Das Diagramm wird der Entwurfsoberfläche hinzugefügt.  
  
6.  Klicken Sie auf das Diagramm, um die Diagrammziehpunkte anzuzeigen. Ziehen Sie die rechte untere Ecke des Diagramms, um das Diagramm zu vergrößern. Die Berichtsentwurfsoberfläche wird vergrößert, um genügend Platz für das Diagramm zu bieten.  
  
7.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht wird das Kreisdiagramm mit acht Slices angezeigt, eines für jedes Produkt. Die Größe der Slices stellt den Umsatz für das jeweilige Produkt dar. Drei der Slices sind relativ dünn.  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a>3. Anzeigen von Prozentsätzen in jedem Slice  
 Sie können für jeden Slice des Kreisdiagramms den Prozentsatz des Slices im Vergleich zum gesamten Kreis anzeigen.  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a>So zeigen Sie Prozentwerte in den einzelnen Segmenten eines Kreisdiagramms an  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Kreisdiagramm, und klicken Sie anschließend auf **Datenbezeichnungen anzeigen**. Die Datenbezeichnungen werden im Diagramm angezeigt.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Bezeichnung, und klicken Sie dann auf **Reihen Bezeichnung Eigenschaften**.  
  
4.  Wählen Sie unter Bezeichnungs Daten im Dropdown Feld die Option **#percent**aus.  
  
     Die UseValueAsLabel-Eigenschaft muss zum Anzeigen von Werten als Prozentsätze auf "False" festgelegt werden. Klicken Sie auf **Ja** , wenn Sie im Dialogfeld **Aktion bestätigen**zum Festlegen dieses Werts aufgefordert werden.  
  
5.  Optionale Um anzugeben, wie viele Dezimalstellen in der Bezeichnung angezeigt werden, geben Sie ein, `#PERCENT{Pn}` wobei *n* die Anzahl der anzuzeigenden Dezimalstellen ist. Wenn Sie z. b. keine Dezimalstellen anzeigen möchten, geben Sie ein `#PERCENT{P0}` .  
  
    > [!NOTE]  
    >  Die Option**Zahlenformat** im Dialogfeld **Reihenbezeichnungseigenschaften** hat beim Formatieren von Prozentwerten keinen Einfluss auf das Format. Hierdurch werden die Bezeichnungen als Prozentwerte formatiert, die eigentlichen Prozentwerte der einzelnen Slices eines Kreisdiagramms werden jedoch nicht berechnet.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht wird der Prozentsatz am gesamten Kreis für jeden Kreisslice angezeigt.  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a>4. Kombinieren von kleinen Slices zu einem Slice  
 Drei der Slices im Kreis sind relativ klein. Sie können mehrere kleine Slices zu einem größeren Slice kombinieren, durch das alle Slices dargestellt werden.  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a>So kombinieren Sie alle Slices des Kreisdiagramms unter fünf Prozent zu einem Slice  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Wählen Sie auf der Registerkarte **Ansicht** in der Gruppe **anzeigen/ausblenden** die Option **Eigenschaften**aus.  
  
3.  Klicken Sie auf der Entwurfsoberfläche auf ein Segment des Kreisdiagramms. Die Eigenschaften für die Reihe werden im Bereich "Eigenschaften" angezeigt.  
  
4.  Erweitern Sie im Abschnitt **Allgemein** den Knoten **CustomAttributes** .  
  
5.  Legen Sie die Eigenschaft **CollectedStyle** auf **SingleSlice**fest.  
  
6.  Vergewissern Sie sich, dass die **CollectedThreshold** -Eigenschaft auf 5 festgelegt ist.  
  
7.  Vergewissern Sie sich, dass die **CollectedThresholdUsePercent** -Eigenschaft auf **TRUE**festgelegt ist.  
  
8.  Klicken Sie im Menüband auf der Registerkarte **Start** auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 In der Legende ist die Kategorie "Other" jetzt vorhanden. Im neuen Kreisslice werden alle Slices, die kleiner als 5 % waren, zu einem Slice kombiniert, das 6 % des gesamten Kreises darstellt.  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a>5. Anpassen des Zeichnungs Effekts  
 Das Standardformat für Kreisdiagramme im Diagramm-Assistenten ist "Ozean", ein Format mit einem konkaven Zeichnungseffekt. Sie können das Format nach dem Ausführen des Assistenten ändern.  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a>So fügen Sie dem Kreisdiagramm einen Zeichnungseffekt hinzu  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Wenn der Bereich Eigenschaften nicht bereits geöffnet ist, wählen Sie auf der Registerkarte **Ansicht** die Option **Eigenschaften**aus.  
  
3.  Doppelklicken Sie auf das Kreis Diagramm. Die Reiheneigenschaften für das Kreisdiagramm werden im Bereich Eigenschaften angezeigt.  
  
4.  Erweitern Sie im Bereich Eigenschaften den Knoten **CustomAttributes** .  
  
5.  Legen Sie " **PieDrawingStyle** " auf " **SoftEdge**" fest.  
  
    > [!NOTE]  
    >  Zeichnungs Effekte und dreidimensionale Effekte sind exklusive Optionen. Wenn für ein Diagramm dreidimensionale Effekte angewendet werden, ist **PieDrawingStyle** nicht im Bereich Eigenschaften verfügbar.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Die folgende Abbildung zeigt das Kreisdiagramm mit weichen Kanten.  
  
 ![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a>6. Hinzufügen eines Berichts Titels  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Geben Sie wie folgt **Kamera- und Camcorderumsatz**ein, drücken Sie die EINGABETASTE, und geben Sie anschließend **Als Prozentsatz des Gesamtumsatzes**ein:  
  
     **Kamera- und Camcorderumsatz**  
  
     **Als Prozentsatz des Gesamtumsatzes**  
  
3.  Wählen Sie **Kamera-und camcorderumsatz**aus, und klicken Sie im Abschnitt **Schriftart** der Registerkarte **Home** des Menübands auf die Schaltfläche **Fett** .  
  
4.  Wählen Sie **als Prozentsatz des Gesamtumsatzes aus**, und legen Sie auf der Registerkarte **Home** im Abschnitt **Schriftart** den Schrift Grad auf **10**fest.  
  
5.  (Optional) Das Textfeld "Titel" muss ggf. vergrößert werden, damit die beiden Textzeilen hineinpassen.  
  
     Dieser Titel wird am Anfang des Berichts angezeigt. Ist keine Kopfzeile definiert, erfüllen die Elemente über dem Berichtshauptteil die Funktion einer Berichtskopfzeile.  
  
6.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="7-save-the-report"></a><a name="Save"></a>7. Speichern des Berichts  
  
#### <a name="to-save-the-report"></a>So speichern Sie den Bericht  
  
1.  Wechseln Sie zur Berichtsentwurfsansicht.  
  
2.  Klicken Sie auf die Schaltfläche Berichts-Generator und anschließend auf **Speichern unter**.  
  
3.  Geben Sie im Feld **Name**den Namen **Umsatz-Kreisdiagramm**ein.  
  
4.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben das Lernprogramm "Hinzufügen eines Kreisdiagramms zu einem Bericht" erfolgreich abgeschlossen. Weitere Informationen zu Diagrammen finden Sie unter [Diagramme (Berichts-Generator und SSRS)](report-design/charts-report-builder-and-ssrs.md) und [Sparklines und Datenbalken (Berichts-Generator und SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
