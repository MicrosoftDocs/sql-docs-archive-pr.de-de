---
title: Entwurfsansicht für Berichte (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10440"
- "10426"
- "10439"
- "10434"
- "10438"
- "10436"
helpviewer_keywords:
- reports, creating
- user interface
- overview of Report Builder
ms.assetid: 1544472c-2803-448d-af52-e901cb457a00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0aef92d69539ffc74900c069630cb2dc546d28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609686"
---
# <a name="report-design-view-report-builder"></a>Berichtsentwurfsansicht (Berichts-Generator)
  Das Berichts-Generator-Fenster ist so aufgebaut, dass Sie Berichtsressourcen einfach anordnen und schnell die gewünschten Berichte erstellen können. Die Entwurfsoberfläche befindet sich in der Mitte des Fensters. Darüber ist das Menüband angeordnet. Die Bereiche "Berichtsdaten", "Gruppierung" und "Eigenschaften" und der BerichtsteilKatalog befinden sich links, unter und rechts neben der Entwurfsoberfläche. Auf der Entwurfsoberfläche können Sie die Berichtselemente hinzufügen und anordnen. Auf dem Menüband sind herkömmliche Menüelemente in Kategorien angeordnet, die einfach zu finden und zu verwenden sind. In den Bereichen können Sie die Berichtsressourcen hinzufügen, auswählen und anordnen und Berichtselementeigenschaften ändern.  
  
 ![ReportDesignView](../media/reportdesignview.gif "ReportDesignView")  
  
##  <a name="the-ribbon"></a><a name="Ribbon"></a>Das Menüband  
 Mit dem Menüband können Sie Befehle, die Sie zur Ausführung einer Aufgabe benötigen, schnell finden. Befehle sind in logischen Gruppen organisiert, die unter Registerkarten zusammengefasst werden. Jede Registerkarte bezieht sich auf einen Aktivitätstyp, wie das Einfügen von Berichtselementen oder das Formatieren von Text.  
  
 In der Berichtentwurfsansicht ist das Menüband in folgende Registerkarten unterteilt: "Home", "Einfügen" und "Ansicht". Wenn Sie eine Task auf dem Menüband nicht finden können, verfügen einige Menübandgruppen über ein zugehöriges Dialogfeld, das Sie öffnen können, indem Sie auf den Pfeil in der unteren rechten Ecke der Gruppe klicken. Sie können das Menüband nicht minimieren oder löschen oder durch Symbolleisten und Menüs ersetzen.  
  
 Im Lauf Modus verfügt das Menüband nur über eine Registerkarte, **führen**Sie aus.  
  
### <a name="home-tab"></a>Registerkarte "Home"  
 Bei der Registerkarte "Home" handelt es sich um eine Auflistung von häufig benutzten Befehlen, die sich im Wesentlichen auf die Darstellung der Elemente im Bericht beziehen. Auf der Registerkarte Home können Sie auf die Befehle für Ausführung, Schriftart, Absatz, Rahmen, Zahl und Layout zugreifen. Wenn Sie auf ein Element in der Registerkarte klicken, ändert sich das ausgewählte Element auf der Entwurfsoberfläche. Wenn Sie auf **Ausführen**klicken, wird der Bericht in HTML gerendert, damit Sie sehen können, wie der Inhalt des Berichts bei der Veröffentlichung angezeigt wird, und Sie sehen die Registerkarte ausführen anstelle der Registerkarte Home. Die Registerkarte Start ist die Standard Registerkarte, die beim ersten Erstellen eines Berichts angezeigt wird.  
  
### <a name="insert-tab"></a>Registerkarte Einfügen  
 Die Registerkarte Einfügen ist eine Auflistung von Befehlen, die häufig zum Hinzufügen von Berichtselementen zum Bericht verwendet werden. Auf der Registerkarte Einfügen können Sie Assistenten verwenden, um eine Tabelle, eine Matrix, ein Diagramm oder eine Karte hinzuzufügen. Sie können diese Elemente auch ohne einen Assistenten hinzufügen. Außerdem können Sie weitere Berichtselemente wie Sparklines, Indikatoren, Textfelder, Bilder, Rechtecke, Unterberichte sowie Berichtskopf- und -ußzeilen hinzufügen.  
  
 Wenn Sie auf der Registerkarte Einfügen auf **Berichts Teile** klicken, wird der Berichts Teil Katalog geöffnet. Sie können Berichtsteile suchen, die auf einem Berichtsserver gespeichert sind. Weitere Informationen finden Sie unter [Berichts Teile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
 Nachdem Sie ein Element eingefügt haben, wechselt der Berichts-Generator automatisch zurück zur Registerkarte Home.  
  
### <a name="view-tab"></a>Registerkarte Ansicht  
 Die Registerkarte Ansicht ist eine Auflistung von Befehlen, mit denen bestimmt wird, was im Berichts-Generator-Fenster angezeigt wird. Sie können Anzeigeoptionen für das Lineal und den Gruppierungs-, Berichtsdaten- und Eigenschaftenbereich ändern.  
  
### <a name="run-tab"></a>Registerkarte „Run“ (Ausführen)  
 Wenn Sie auf der Registerkarte Start auf **Ausführen** klicken, führen Sie eine Vorschau des Berichts im HTML-Viewer aus, und anstelle der Registerkarte Home wird die Registerkarte ausführen angezeigt.  
  
 Die Registerkarte Ausführen enthält eine Auflistung von Befehlen, die Sie verwenden können, nachdem der Bericht gerendert wurde. Sie können den Bericht drucken, durch die Berichtsseiten navigieren, den Bericht in ein anderes Dateiformat exportieren, die Dokumentstruktur oder Parameter (sofern der Bericht Parameter enthält) anzeigen und nach Elementen im Bericht suchen. Weitere Informationen finden Sie unter [Anzeigen einer Vorschau des Berichts im Lauf Modus](#RunMode).  
  
 Um zur Berichtsentwurfs Ansicht zurückzukehren, klicken Sie auf der Registerkarte **Ausführen** auf **Entwurf**.  
  
  
##  <a name="the-report-design-surface"></a><a name="RptDesignSurface"></a>Der Bericht Designoberfläche  
 Die Berichtsentwurfsoberfläche des Berichts-Generators ist der Hauptarbeitsbereich zum Entwerfen der Berichte. Fügen Sie der Entwurfsoberfläche Berichtselemente wie Datenbereiche, Unterberichte, Textfelder, Bilder, Rechtecke und Linien aus dem Menüband oder dem Berichtsteilkatalog hinzu, um sie in den Bericht einzufügen. Dort können Sie den Berichtselementen Gruppen, Ausdrücke, Parameter, Filter, Aktionen, Sichtbarkeit und Formatierung hinzufügen.  
  
 Sie können auch folgende Eigenschaften ändern:  
  
-   Ändern Sie die Eigenschaften des Berichtshauptteils (z.B. Rahmen- und Füllfarbe), indem Sie außerhalb von Berichtselementen mit der rechten Maustaste auf die weiße Fläche der Entwurfsoberfläche klicken und anschließend auf **Eigenschaften des Berichtshauptteils**klicken.  
  
-   Ändern Sie die Kopf- und Fußzeileneigenschaften (z.B. Rahmen- und Füllfarbe), indem Sie außerhalb von Berichtselementen mit der rechten Maustaste auf die weiße Fläche der Entwurfsoberfläche klicken und anschließend auf **Seitenkopfeigenschaften** oder **Fußzeileneigenschaften**klicken.  
  
-   Die Eigenschaften des Berichts selbst, z. b. Seiten Einrichtung, klicken Sie mit der rechten Maustaste auf den blauen Bereich um die Entwurfs Oberfläche, und klicken Sie dann auf **Berichts Eigenschaften**.  
  
-   Ändern Sie die Eigenschaften von Berichtselementen, indem Sie mit der rechten Maustaste auf die Elemente klicken und anschließend auf **Eigenschaften**klicken.  
  
> [!NOTE]  
>  Wenn Sie ein Feld vom Berichtsdatenbereich direkt in die Berichtsentwurfsoberfläche ziehen, anstatt es in einem Datenbereich wie einer Tabelle oder einem Diagramm einzufügen, wird beim Ausführen des Berichts nur der erste Wert von den Daten in diesem Feld angezeigt.  
  
 Informationen zum Bearbeiten von Elementen auf der Entwurfsoberfläche über die Tastatur finden Sie unter [Tastenkombinationen (Berichts-Generator)](keyboard-shortcuts-report-builder.md).  
  
### <a name="design-surface-size-and-print-area"></a>Entwurfsoberflächengröße und Druckbereich  
 Die Größe der Entwurfsoberfläche kann sich von der Größe des Druckbereichs unterscheiden, den Sie für das Drucken des Berichts angeben. Wenn Sie die Größe der Entwurfsoberfläche ändern, ändert sich der Druckbereich des Berichts dadurch nicht. Unabhängig von der Größe, die Sie für den Druckbereich des Berichts festlegen, ändert sich die Größe des vollständigen Entwurfsbereichs nicht. Weitere Informationen finden Sie unter [Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>   Aktivieren Sie auf der Registerkarte **Ansicht** das Kontrollkästchen **Lineal** , um das Lineal anzuzeigen.  
  
  
##  <a name="the-report-data-pane"></a><a name="ReptDataPane"></a>Der Berichtsdaten Bereich  
 Im Berichtsdatenbereich des Berichts-Generators können Sie die für einen Bericht benötigten Berichtsdaten und -ressourcen definieren, bevor Sie mit dem Entwurf des Berichtslayouts beginnen. Sie können dem Berichtsdatenbereich z. B. Datenquellen, Datasets, berechnete Felder, Berichtsparameter und Bilder hinzufügen.  
  
 Nachdem Sie dem Berichtsdatenbereich Elemente hinzugefügt haben, können Sie Felder in Berichtselemente auf der Entwurfsoberfläche ziehen und so bestimmen, wo die Daten auf der Berichtsseite angezeigt werden.  
  
 Sie können auch integrierte Felder vom Berichtsdatenbereich in die Berichtsentwurfsoberfläche ziehen. Beim Rendern enthalten diese Felder Informationen zum Bericht, z. B. Berichtsname, Gesamtanzahl von Seiten im Bericht und aktuelle Seitennummer.  
  
 Einige Elemente werden dem Berichtsdatenbereich automatisch hinzugefügt, wenn Sie der Berichtsentwurfsoberfläche etwas hinzufügen. Wenn Sie z. B. ein Berichtsteil aus dem Berichtsteilkatalog hinzufügen und der Berichtsteil ein Datenbereich ist, wird das Dataset dem Berichtsdatenbereich automatisch hinzugefügt. Weitere Informationen finden Sie unter [Berichtsteile und Datasets](../report-data/report-parts-and-datasets-in-report-builder.md). Wenn Sie ein Bild in den Bericht einbetten, wird es dem Ordner "Bilder" im Berichtsdatenbereich hinzugefügt.  
  
> [!NOTE]  
>  Mit der Schaltfläche **Neu** können Sie dem Berichtsdatenbereich ein neues Element hinzufügen. Sie können dem Bericht mehrere Datasets aus derselben Datenquelle oder anderen Datenquellen hinzufügen. Außerdem können Sie dem Berichtsserver freigegebene Datasets hinzufügen. Klicken Sie mit der rechten Maustaste auf eine Datenquelle, und klicken Sie anschließend auf **Dataset hinzufügen**, um ein neues Dataset aus derselben Datenquelle hinzuzufügen.  
  
 Weitere Informationen zu den Elementen im Berichtsdatenbereich finden Sie in den folgenden Themen:  
  
-   [Integrierte globale Werte und Benutzerverweise &#40;Berichts-Generator und SSRS&#41;](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
-   [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
-   [Bilder &#40;Berichts-Generator und SSRS&#41;](../report-design/images-report-builder-and-ssrs.md)  
  
-   [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Berichts-Generator](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
-   [Melden Sie eingebettete Datasets und freigegebene Datasets &#40;Berichts-Generator und SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
-   [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
##  <a name="the-report-part-gallery"></a><a name="ReptPartGallery"></a>Der Berichts Teil Katalog  
 Die einfachste Methode zum Erstellen eines Berichts besteht darin, auf dem Berichtsserver oder einem in eine SharePoint-Website integrierten Berichtsserver nach einem vorhandenen Berichtsteil zu suchen (z. B. eine Tabelle oder ein Diagramm). Im Berichts Teil Katalog können Sie nach Berichts teilen suchen, die dem Bericht hinzugefügt werden sollen. Sie können die Berichtsteile nach dem Namen des Berichtsteils (vollständig oder teilweise), nach der Person, von der der Berichtsteil erstellt oder zuletzt geändert wurde, nach dem letzten Änderungsdatum, dem Speicherort oder dem Typ des Berichtsteils filtern. Sie konnten z. B. nach allen Diagrammen suchen, die in der vorhergehenden Woche von einem oder mehreren Ihrer Kollegen erstellt wurden.  
  
> [!NOTE]  
>  Sie müssen eine Verbindung mit einem Server herstellen, um den Berichtsteilkatalog anzuzeigen.  
  
 Sie können die Suchergebnisse als Miniaturansichten oder in Listenform anzeigen und nach Name, Erstellungs- und Änderungsdatum und dem Ersteller sortieren. Weitere Informationen finden Sie unter [Berichts Teile &#40;Berichts-Generator und SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
  
##  <a name="the-properties-pane-report-builder"></a><a name="PropertiesPane"></a>Der Bereich "Eigenschaften" (Berichts-Generator)  
 Mit jedem Element in einem Bericht, einschließlich Berichtshauptteil, Datenbereichen, Bildern und Textfeldern, sind Eigenschaften verknüpft. Beispiel: Die Eigenschaft BorderColor für ein Textfeld gibt den Farbwert für den Rahmen des Textfelds an, während die Eigenschaft PageSize für den Bericht die Seitengröße des Berichts angibt.  
  
 Diese Eigenschaften werden im Bereich "Eigenschaften" angezeigt. Die Eigenschaften im Bereich ändern sich je nach ausgewähltem Berichtselement.  
  
 Klicken Sie auf der Registerkarte "Ansicht" in der Gruppe "Ein-/Ausblenden" auf "Eigenschaften", um den Bereich "Eigenschaften" anzuzeigen.  
  
### <a name="changing-property-values"></a>Ändern von Eigenschaftswerten  
 In Berichts-Generator gibt es verschiedene Möglichkeiten, die Eigenschaften für Berichtselemente zu ändern:  
  
-   Durch Klicken auf Schaltflächen und Listen auf dem Menüband.  
  
-   Durch Ändern von Einstellungen in Dialogfeldern.  
  
-   Durch Ändern von Eigenschaftswerten im Eigenschaftenbereich.  
  
 Die gebräuchlichsten Eigenschaften sind in den Dialogfeldern und auf dem Menüband verfügbar.  
  
 Je nach Eigenschaft können Sie einen Eigenschaftswert aus einer Dropdownliste festlegen, den Wert eingeben oder auf `<Expression>` klicken, um einen Ausdruck zu erstellen.  
  
### <a name="changing-the-properties-pane-view"></a>Ändern der Eigenschaftenbereichsansicht  
 Standardmäßig sind die Eigenschaften, die im Eigenschaftenbereich angezeigt werden, in größere Kategorien unterteilt, wie Aktion, Rahmen, Ausfüllen, Schriftart und Allgemein. Mit jeder Kategorie ist eine Gruppe von Eigenschaften verknüpft. Beispiel: Die folgenden Eigenschaften werden in der Kategorie Schriftart aufgeführt: Color, FontFamily, FontSize, FontStyle, FontWeight, LineHeight und TextDecoration. Sie können alle Eigenschaften, die im Bereich aufgeführt werden, auch alphabetisieren. In diesem Fall werden die Kategorien entfernt. Alle Eigenschaften werden ungeachtet der Kategorie in alphabetischer Reihenfolge aufgeführt.  
  
 Der Eigenschaftenbereich enthält drei Schaltflächen am oberen Rand: Kategorie, Alphabetisieren und Eigenschaftenseiten. Klicken Sie auf die Schaltfläche Kategorie und Alphabetisieren, um zwischen den Ansichten des Eigenschaftenbereichs zu wechseln. Klicken Sie auf die Schaltfläche **Eigenschaftenseiten** , um das Eigenschaftendialogfeld für ein ausgewähltes Berichtselement zu öffnen.  
  
  
##  <a name="the-grouping-pane-report-builder"></a><a name="GroupPane"></a>Der Gruppierungs Bereich (Berichts-Generator)  
 Gruppen werden verwendet, um die Berichtsdaten in einer visuellen Hierarchie zu organisieren und Ergebnisse zu berechnen. Sie können die Zeilen- und Spaltengruppen innerhalb eines Datenbereichs auf der Entwurfsoberflache und im Gruppierungsbereich anzeigen. Der Gruppierungsbereich enthält zwei Bereiche: Zeilengruppen und Spaltengruppen. Wenn Sie einen Datenbereich wählen, werden im Gruppierungsbereich alle Gruppen innerhalb dieses Datenbereichs in Form einer hierarchischen Liste angezeigt: Untergeordnete Gruppen werden eingerückt unter den übergeordneten Gruppen angezeigt.  
  
 ![Gruppierungsbereich für geschachtelte Zeilen- und Spaltengruppen](../media/rs-basictablixdesigngroupingpanedefaultview.gif "Gruppierungsbereich für geschachtelte Zeilen- und Spaltengruppen")  
  
 Sie können Gruppen erstellen, indem Sie Felder mit Drag and Drop aus dem Berichtsdatenbereich ziehen und auf der Entwurfsoberfläche oder im Gruppierungsbereich einfügen. Sie können übergeordnete, angrenzende und untergeordnete Gruppen im Gruppierungsbereich hinzufügen, Gruppeneigenschaften ändern und Gruppen löschen.  
  
 Der Gruppierungs Bereich wird standardmäßig angezeigt, Sie können den Bereich jedoch schließen, indem Sie auf der Registerkarte Ansicht das Kontrollkästchen Gruppierungs Bereich deaktivieren. Der Gruppierungs Bereich ist für die Diagramm-oder Messgeräte Datenbereiche nicht verfügbar.  
  
 Weitere Informationen finden Sie unter [Gruppierungsbereich &#40;Berichts-Generator&#41;](../report-design/grouping-pane-report-builder.md) und [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](../report-design/understanding-groups-report-builder-and-ssrs.md).  
  
  
##  <a name="previewing-your-report-in-run-mode"></a><a name="RunMode"></a>Anzeigen einer Vorschau des Berichts im Lauf Modus  
 In der Berichtsentwurfsansicht arbeiten Sie nicht mit tatsächlichen Daten, sondern mit einer durch den Feldnamen oder Ausdruck angegebenen Darstellung der Daten. Wenn die tatsächlichen Daten im Kontext des entworfenen Berichts angezeigt werden sollen, können Sie den Bericht ausführen, um eine Vorschau der Daten aus der zugrunde liegenden Datenbank im Berichtslayout anzuzeigen. Durch Wechseln zwischen dem Entwurf und der Ausführung des Berichts können Sie den Entwurf des Berichts anpassen und die Ergebnisse sofort anzeigen. Klicken Sie im Menüband in der Gruppe Ansichten auf **Ausführen** , um **einen** Bericht in der Vorschau anzuzeigen.  
  
 Wenn Sie auf **Ausführen**klicken, stellt der Berichts-Generator eine Verbindung mit den Berichtsdatenquellen her. Die Daten werden auf dem Computer zwischengespeichert und mit dem Layout kombiniert, und anschließend wird der Bericht im HTML-Viewer gerendert. Sie können den Bericht beliebig oft ausführen, während Sie weiterhin am Entwurf des Berichts arbeiten. Wenn Sie mit dem Entwurf des Berichts zufrieden sind, können Sie ihn auf dem Berichtsserver speichern. Dort kann er von Benutzern mit den entsprechenden Berechtigungen angezeigt werden.  
  
### <a name="running-a-report-with-parameters"></a>Ausführen eines Berichts mit Parametern  
 Wenn Sie den Bericht ausführen, wird er automatisch verarbeitet. Wenn der Bericht Parameter enthält, müssen alle Parameter Standardwerte haben, bevor der Bericht automatisch ausgeführt werden kann. Wenn ein Parameter keinen Standardwert hat, müssen Sie beim Ausführen des Berichts einen Wert für den Parameter auswählen und dann auf der Registerkarte Ausführen auf **Bericht anzeigen** klicken. Weitere Informationen finden Sie unter [Berichts Parameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
### <a name="print-preview"></a>Seitenansicht  
 Wenn Sie im Ausführungsmodus einen Bericht in der Vorschau anzeigen, entspricht er einem in HTML erstellten Bericht. Die Vorschau ist kein HTML-Code, das Layout und die Paginierung des Berichts gleichen jedoch der HTML-Ausgabe. Sie können die Ansicht ändern und einen gedruckten Bericht darstellen, indem Sie zur Seitenansicht wechseln. Klicken Sie auf der Registerkarte **Ausführen** auf die Schaltfläche Seiten **Ansicht** . Der Bericht wird so angezeigt, als ob er sich auf einer physischen Seite befand. Diese Ansicht gleicht der Ausgabe durch die Bild- und PDF-Renderingerweiterung. Die Seitenansicht ist keine Bild- oder PDF-Datei, das Layout und die Paginierung des Berichts ähneln jedoch der Ausgabe in diesen Formaten.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Suchen, anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Berichts-Generator in SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
