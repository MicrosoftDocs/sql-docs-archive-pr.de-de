---
title: Gruppierungsbereich (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10033"
helpviewer_keywords:
- Grouping Pane dialog box
ms.assetid: 983ee5a4-944c-491e-8720-7cd9f3881961
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31da07cb7f0cf16e2e5c4468c6204153af1a9ebd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695321"
---
# <a name="grouping-pane-report-builder"></a>Gruppierungsbereich (Berichts-Generator)
  Im Gruppierungsbereich werden die Zeilengruppen und Spaltengruppen für den derzeit ausgewählten Tablix-Datenbereich angezeigt. Der Gruppierungsbereich ist für die Diagramm- und Messgerätdatenbereiche nicht verfügbar. Der Gruppierungsbereich umfasst den Bereich Zeilengruppen und den Bereich Spaltengruppen. Der Gruppierungsbereich weist zwei Modi auf, den Standard- und den erweiterten Modus. Im Standardmodus wird eine hierarchische Sicht der dynamischen Elemente für Zeilen- und Spaltengruppen angezeigt. Im erweiterten Modus werden dynamische und statische Elemente für Zeilen- und Spaltengruppen angezeigt. Eine Gruppe ist ein benannter Satz von Daten aus einem Berichtsdataset, der in einem Datenbereich angezeigt wird. Gruppen werden in Hierarchien organisiert, die statische und dynamische Elemente einschließen. Weitere Informationen finden Sie unter [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Wenn der Gruppierungsbereich nicht angezeigt wird, klicken Sie in der Registerkarte **Sicht** in der Gruppe **Ein-/Ausblenden**auf die Option **Gruppierung**.  
  
 Zellen in den Zeilen- und Spaltengruppenbereiche können statische oder dynamische Elemente einer Tablix-Zeile oder Spaltengruppe sein. Statische Elemente wiederholen sich einmal pro Gruppe und enthalten meist Bezeichnungen oder Gesamtbeträge. Dynamische Elemente wiederholen sich einmal pro Gruppeninstanz und enthalten meist die eindeutigen Werte des Gruppierungsausdrucks. Wenn Sie Tablix-Zellen im Zeilengruppenbereich oder Spaltengruppenbereich auswählen, wird das entsprechende Gruppenelement im Bereich Zeilengruppen oder Spaltengruppen ausgewählt. Wenn Sie umgekehrt Gruppen im Gruppierungsbereich auswählen, wird die entsprechende, dem Gruppenelement zugeordnete Zelle auf der Entwurfsoberfläche ausgewählt. Weitere Informationen zu Tablix-Zeilen- und -Spaltengruppierungsbereichen finden Sie unter [Zonen des Tablix-Datenbereichs (Berichts-Generator und SSRS)](tablix-data-region-areas-report-builder-and-ssrs.md).  
  
 Der Gruppierungsbereich unterstützt die folgenden Modi:  
  
-   **Standard.** Verwenden Sie den Standardmodus, um Gruppen hinzuzufügen, zu bearbeiten oder zu löschen. Sie können übergeordnete, untergeordnete und Detailgruppen hinzufügen, indem Sie Felder aus dem Berichtsdatenbereich ziehen und diese in der Gruppenhierarchie einfügen. Um eine angrenzende Gruppe hinzuzufügen, müssen Sie die Verknüpfung **Gruppe hinzufügen** verwenden. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen einer Gruppe in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
-   **Erweitert**. Verwenden Sie den **erweiterten Modus** , um alle Elemente der Zeilen- und Spaltengruppen anzuzeigen und die Eigenschaften auf statische Elemente festzulegen. Wenn Sie Gruppen erstellen oder Gesamtwerte hinzufügen, werden die Eigenschaften automatisch festgelegt, mit denen gesteuert wird, wie der Tablix-Datenbereich Zeilen und Spalten für die einzelnen Berichtsseiten rendert. Um diese Eigenschaften manuell anzupassen, müssen Sie diese für das Tablix-Element festlegen. Weitere Informationen finden Sie unter [Steuern der Tablix-Datenbereichsanzeige auf einer Berichtsseite &#40;Berichts-Generator und SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).  
  
## <a name="default-mode"></a>Standardmodus  
 Im Standardmodus wird im Bereich Zeilengruppen und im Bereich Spaltengruppen eine hierarchische Sicht für alle übergeordneten Gruppen, untergeordneten Gruppen und angrenzenden Gruppen angezeigt. Untergeordnete Gruppen werden eingezogen unter der jeweils übergeordneten Gruppe angezeigt. Angrenzende Gruppen werden auf der gleichen Einzugsebene wie gleichgeordnete Gruppen angezeigt. Die folgende Abbildung zeigt einen Tablix-Datenbereich mit geschachtelten Zeilengruppen und geschachtelten und angrenzenden Spaltengruppen.  
  
 ![Tablix, geschachtelte und angrenzende Zeilen- und Spaltengruppen](../media/rs-basictablixdesigngroupingpane.gif "Tablix, geschachtelte und angrenzende Zeilen- und Spaltengruppen")  
  
 Der Bereich Gruppierung zeigt die entsprechenden Zeilen- und Spaltengruppen an. In der folgenden Abbildung wurde die auf der Unterkategorie basierende Gruppe im Bereich Zeilengruppen ausgewählt, und die Gruppierungszelle [Subcat] ist im Tablix-Datenbereich ausgewählt:  
  
 ![Gruppierungsbereich für geschachtelte Zeilen- und Spaltengruppen](../media/rs-basictablixdesigngroupingpanedefaultview.gif "Gruppierungsbereich für geschachtelte Zeilen- und Spaltengruppen")  
  
 Im Bereich Zeilengruppen ist die auf der Unterkategorie basierende Gruppe ein untergeordnetes Element der auf der Kategorie basierenden Gruppe. Im Bereich Spaltengruppen ist die Gruppe für Land und Region ein untergeordnetes Element der Gruppe für Geographie. Die Gruppe für das Jahr und die Gruppen für Land und Region sind angrenzende Gruppen.  
  
 Weitere Informationen finden Sie unter [Zellen, Zeilen und Spalten des Tablix-Datenbereichs (Berichts-Generator und SSRS)](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## <a name="advanced-mode"></a>erweiterten Modus  
 Im erweiterten Modus wird im Bereich Zeilengruppen und im Bereich Spaltengruppen eine hierarchische Sicht für alle Gruppen angezeigt, einschließlich statischen und dynamischen Elementen. Wenn Sie ein Element auswählen, zeigt der Eigenschaftenbereich Eigenschaften für das derzeit ausgewählte Tablix-Element an.  
  
> [!NOTE]  
>  Wenn Sie den **erweiterten Modus**umschalten möchten, klicken Sie am Rand des Bereichs Spaltengruppen mit der rechten Maustaste auf den Pfeil nach unten, und klicken Sie anschließend auf **Erweiterter Modus**.  
  
 In den meisten Fällen werden Eigenschaften, die die Anzeige statischer und dynamischer Gruppenzeilen und Gruppenspalten steuern, automatisch beim Erstellen einer Gruppe oder Hinzufügen von Gesamtwerten festgelegt. Zum Bearbeiten der Standardwerte müssen Sie das Gruppenelement im Bereich Zeilengruppen oder Spaltengruppen auswählen und die Eigenschaftenwerte im Eigenschaftenfenster ändern. Die folgenden Eigenschaften sind verfügbar:  
  
-   **FixedData**. Boolesch. Für äußere und Zeilen- und Spaltenheader. Frieren Sie den Zeilengruppenbereich für vertikale Bildläufe oder den Spaltengruppenbereich für horizontale Bildläufe in einem Renderer ein, z. B. HTML.  
  
-   **HideIfNoRows**. Boolesch. Nur für statische Elemente. Bei erfolgter Festlegung werden Hidden und ToggleItem ignoriert. Blenden Sie dieses Element aus, wenn der Tablix-Datenbereich keine Datenzeilen enthält.  
  
-   **KeepTogether**. Boolesch. Gibt an, dass das gesamte Tablix-Element und eventuell geschachtelte Elemente wenn möglich auf einer Seite zusammengehalten werden sollen.  
  
-   `KeepWithGroup`. Boolesch. Nur für statische Zeilenelemente. Trennen Sie diese Zeile nach Möglichkeit nicht vom vorherigen oder folgenden gleichgeordneten dynamischen Element, sofern dieses nicht ausgeblendet ist. Um einen Zeilenkopf bei der zugehörigen Gruppe zu belassen, legen Sie KeepWithGroup auf **After**fest.  
  
-   `RepeatOnNewPage`. Boolesch. Nur für statische Zeilenelemente und wenn KeepWithGroup nicht „None“ ist. Wiederholen Sie diese statische Zeile nach Möglichkeit auf jeder Seite, die mindestens eine Instanz des von KeepWithGroup angegebenen dynamischen Elements aufweist. Um einen Zeilenkopf bei der zugehörigen Gruppe zu belassen, legen Sie RepeatOnNewPage auf **TRUE**fest.  
  
-   `Hidden`. Boolesch. Gibt an, ob die Zeile oder die Spalte anfänglich ausgeblendet sein soll.  
  
-   **ToggleItem.** Eine Zeichenfolge. Der Name des Textfelds, dem das Umschaltbild hinzugefügt werden soll. Das Textfeld muss demselben Gruppenbereich oder einem enthaltenden Bereich angehören.  
  
 Weitere Informationen finden Sie unter [Steuern der Tablix-Datenbereichsanzeige auf einer Berichtsseite (Berichts-Generator und SSRS)](controlling-the-tablix-data-region-display-on-a-report-page.md), [Anzeigen von Kopf- und Fußzeilen einer Gruppe (Berichts-Generator und SSRS)](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md), und [Anzeigen von Zeilen- und Spaltenüberschriften auf mehreren Seiten (Berichts-Generator und SSRS)](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).  
  
 Nicht jedes statische Element verfügt über einen Header, der einer Zelle auf der Entwurfsoberfläche entspricht. Im Gruppierungsbereich wird mit der folgenden Konvention angegeben, ob ein statisches Element keinen Header besitzt:  
  
-   **Statisch** Gibt ein statisches Element mit einer Headerzelle an.  
  
-   **(Statisch)** Gibt ein statisches Element ohne Headerzelle an, wird als ausgeblendet statisch bezeichnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Filtern, gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
