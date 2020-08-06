---
title: Listen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c33231a5-b3a8-42e4-95bc-d05bdf2222f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9afb0dfabe5ccc3962d43eef30031a728514135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616417"
---
# <a name="lists-report-builder-and-ssrs"></a>Listen (Berichts-Generator und SSRS)
  Ein Listendatenbereich wird mit jeder Gruppe oder Zeile im Berichtsdataset wiederholt. Eine Liste kann verwendet werden, um Freiformberichte oder -formulare, z. B. Rechnungen, oder Berichte und Formulare in Verbindung mit anderen Datenbereichen zu erstellen. Sie können Listen definieren, die beliebig viele Berichtselemente enthalten. Listen können ineinander geschachtelt werden, um mehrere Datengruppen bereitzustellen.  
  
> [!NOTE]  
>  Sie können Listen in einem Bericht als Berichtsteile getrennt veröffentlichen. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 Einen schnellen Einstieg in Matrizen finden Sie unter [Tutorial: Erstellen eines Freiformberichts &#40;Berichts-Generator&#41;](../tutorial-creating-a-free-form-report-report-builder.md).  
  
 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Beispielberichte schließen einen Bericht ein, der eine Liste verwendet. Sie erhalten weitere Informationen zu Listen, wenn Sie die Berichtsdefinition des Beispielberichts in Berichts-Generator oder Berichts-Designer lesen oder den gerenderten Bericht in Berichts-Generator oder Berichts-Designer in der Vorschau anzeigen. Weitere Informationen zum Herunterladen der Beispielberichte finden Sie unter [(SSRS) Reporting Services-Beispiele](https://go.microsoft.com/fwlink/?LinkID=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-list-to-your-report"></a><a name="AddingList"></a>Hinzufügen einer Liste zum Bericht  
 Fügen Sie der Entwurfsoberfläche über die Registerkarte "Einfügen" auf dem Menüband eine Liste hinzu. Standardmäßig enthält die Liste anfänglich eine einzelne Zelle in einer der Detailgruppe zugeordneten Zeile.  
  
 ![Berichtselement „Neue Liste“ auf der Entwurfsoberfläche](../media/rs-listtemplatenew.gif "Berichtselement „Neue Liste“ auf der Entwurfsoberfläche")  
  
 Wenn Sie auf der Entwurfsoberfläche eine Liste auswählen, werden Zeilen- und Spaltenhandles angezeigt, wie in der folgenden Abbildung dargestellt.  
  
 ![Ausgewählte neu zur Toolbox hinzugefügte Liste](../media/rs-listtemplatenewselected.gif "Ausgewählte neu zur Toolbox hinzugefügte Liste")  
  
 Die zu Beginn verwendete Liste ist eine Vorlage auf Grundlage des Tablix-Datenbereichs. Wenn Sie eine Liste hinzugefügt haben, können Sie den Entwurf weiter verbessern, indem Sie den Inhalt oder die Darstellung der Liste durch Angeben von Filter-, Sortier- oder Gruppierungsausdrücken ändern oder indem Sie die Art der Anzeige der Liste für alle Berichtsseiten ändern. Weitere Informationen finden Sie unter [Steuern der Tablix-Datenbereichsanzeige auf einer Berichtsseite &#40;Berichts-Generator und SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md). Die Liste enthält anfangs nur eine Spalte und Zeile. Sie können den Listenentwurf jedoch weiterentwickeln, indem Sie geschachtelte oder angrenzende Zeilengruppen oder Spaltengruppen oder zusätzliche Detailzeilen hinzufügen. Weitere Informationen finden Sie unter [Untersuchen der Flexibilität eines Tablix-Datenbereichs &#40;Berichts-Generator und SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).  
  

  
##  <a name="displaying-data-in-a-free-form-layout"></a><a name="DisplayingLayout"></a> Anzeigen von Daten in einem Freiformlayout  
 Wenn Sie Daten nicht in einem Raster, sondern in einem Freiformlayout anordnen möchten, können Sie der Entwurfsoberfläche eine Liste hinzufügen. Ziehen Sie Felder aus dem Berichtsdatenbereich in die Zelle. Standardmäßig enthält die Zelle ein Rechteck, das als Container verwendet wird. Verschieben Sie jedes Feld im Container, bis Sie der Entwurf Ihren Wünschen entspricht. Die Ausrichtungslinien, die beim Ziehen von Textfeldern im rechteckigen Container angezeigt werden, erleichtern das vertikale und horizontale Ausrichten der Kanten. Entfernen Sie unerwünschte Abstände, indem Sie die Größe der Zelle anpassen. Weitere Informationen finden Sie unter [Ändern der Zeilenhöhe oder der Spaltenbreite (Berichts-Generator und SSRS)](change-row-height-or-column-width-report-builder-and-ssrs.md).  
  
 Die folgende Abbildung zeigt eine Liste mit Informationen zu einer Bestellung, den Feldern "Date", "Order", "Qty", "Product" und "LineTotal" sowie einer Grafik.  
  
 ![Liste in Entwurfsansicht, 4 Felder und ein Bild](../media/rs-basiclistformdesign.gif "Liste in Entwurfsansicht, 4 Felder und ein Bild")  
  
 In der Vorschau wird die Liste wiederholt, sodass die Felddaten im Freiformformat angezeigt werden, wie in der folgenden Abbildung dargestellt:  
  
 ![Vorschau für Liste mit 4 Feldern und einem Bild](../media/rs-basiclistformpreview.gif "Vorschau für Liste mit 4 Feldern und einem Bild")  
  
> [!NOTE]  
>  Die gepunkteten Linien in diesen Abbildungen geben das Freiformlayout für die einzelnen Feldwerte an. Normalerweise werden in einem Produktionsbericht keine gepunkteten Linien verwendet.  
  

  
##  <a name="displaying-data-with-one-level-of-grouping"></a><a name="DisplayingGrouping"></a> Anzeigen von Daten mit einer Gruppierungsebene  
 Da Listen automatisch einen Container bereitstellen, können sie verwendet werden, um gruppierte Daten mit mehreren Sichten anzuzeigen. Wenn Sie die Standardliste zum Angeben einer Gruppe ändern möchten, bearbeiten Sie die Gruppe Details, und geben Sie einen neuen Namen sowie einen Gruppierungsausdruck an.  
  
 Zum Beispiel können Sie eine Tabelle und ein Diagramm mit unterschiedlichen Sichten desselben Datasets einbetten. Der Liste können Sie eine Gruppe hinzufügen, sodass die geschachtelten Berichtselemente einmal für jeden Gruppenwert wiederholt werden. Die folgende Abbildung zeigt eine nach Produktkategorie gruppierte Liste. Es ist keine Detailzeile vorhanden. Zwei Tabellen sind in der Liste nebeneinander geschachtelt. In der ersten Tabelle sind die Unterkategorien mit Gesamtverkäufen dargestellt. In der zweiten Tabelle ist die Kategorie nach geografischem Gebiet gruppiert angezeigt, mit einem Diagramm mit der Verteilung der Unterkategorien.  
  
 ![Eine Liste mit 2 Tabellen, eine davon mit geschachteltem Diagramm](../media/rs-basiclistgroupdesign.gif "Eine Liste mit 2 Tabellen, eine davon mit geschachteltem Diagramm")  
  
 In der Vorschau zeigt die Tabelle die Gesamtverkäufe für alle Unterkategorien von Fahrrädern, und die Tabelle daneben zeigt die Übersicht über die Verkäufe nach geografischem Gebiet. Die erste Tabelle stellt anhand eines Ausdrucks zur Angabe der Hintergrundfarbe der Tabelle und einer benutzerdefinierten Palette für das Diagramm auch die Legende für die Diagrammfarben bereit.  
  
 ![Vorschau, 2 Tabellen, eine davon mit geschachteltem Diagramm](../media/rs-basiclistgrouppreview.gif "Vorschau, 2 Tabellen, eine davon mit geschachteltem Diagramm")  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
