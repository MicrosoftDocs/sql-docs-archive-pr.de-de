---
title: Hinzufügen einer Erweiterungs- oder Reduzieraktion zu einem Element (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696422"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a>Hinzufügen einer Erweiterungs- oder Reduzieraktion zu einem Element (Berichts-Generator und SSRS)
  Sie können einem Benutzer das interaktive Erweitern oder Reduzieren von Berichtselementen, oder für eine Tabelle oder Matrix das Erweitern oder Reduzieren der zugehörigen Zeilen und Spalten einer Gruppe ermöglichen. Zu diesem Zweck legen Sie die Sichtbarkeitseigenschaften eines Elements fest, das von Benutzern erweitert oder reduziert werden soll. Die Sichtbarkeit wird in einem HTML-Berichts-Viewer festgelegt. Eine solche Einstellung wird auch als *Drilldownaktion* bezeichnet.  
  
 In der Berichtsentwurfsansicht geben Sie den Namen des Textfelds an, für das Umschaltsymbole zum Erweitern und Reduzieren angezeigt werden sollen. Im gerenderten Bericht wird zusätzlich zum Inhalt des Textfelds ein Pluszeichen (+) oder Minuszeichen (-) für das Feld angezeigt. Wenn der Benutzer auf das Umschaltsymbol klickt, wird die Berichtsanzeige aktualisiert, um das Berichtselement entsprechend den aktuellen Sichtbarkeitseinstellungen für Elemente im Bericht ein- oder auszublenden.  
  
 Im Allgemeinen werden Aktionen zum Erweitern und Reduzieren verwendet, um anfänglich nur Zusammenfassungsdaten anzuzeigen und dem Benutzer die Möglichkeit zu geben, per Klick auf das Pluszeichen Detaildaten anzuzeigen. Sie können anfänglich z. B. eine Tabelle mit Werten für ein Diagramm oder wie in einem Drilldownbericht untergeordnete Gruppen für eine Tabelle mit geschachtelten Zeilen- oder Spaltengruppen ausblenden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a>So fügen Sie einer Gruppe eine Erweiterungs- und Reduzieraktion hinzu  
  
1.  Klicken Sie in der Berichtsentwurfsansicht auf die Tabelle oder Matrix, um sie auszuwählen. Im Gruppierungsbereich werden die Zeilen- und Spaltengruppen angezeigt.  
  
     ![Gruppierungsbereich](../media/groupingpane.png "Gruppierungsbereich")  
  
     Wenn der Gruppierungsbereich nicht erscheint, klicken Sie auf das Menü **Ansicht** , und klicken Sie dann auf **Gruppierung**.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle der Titelleiste des Bereichs Gruppierung, und klicken Sie anschließend auf **Erweitert**. Der Modus des Bereichs Gruppierung wird gewechselt, sodass nun die zugrunde liegende Anzeigestruktur für Zeilen und Spalten in der Entwurfsoberfläche angezeigt wird.  
  
     ![Gruppierungsbereich mit Menüoption für erweiterten Modus](../media/groupingpane-advancedmode.png "Gruppierungsbereich mit Menüoption für erweiterten Modus")  
  
3.  Klicken Sie im entsprechenden Gruppenbereich auf die Zeilengruppe oder Spaltengruppe, deren zugeordnete Zeilen oder Spalten ausgeblendet werden sollen. Die Gruppe wird ausgewählt, und im Bereich Eigenschaften werden die Eigenschaften für **Tablix-Element** angezeigt.  
  
    > [!NOTE]  
    >   Zum Anzeigen des Bereichs „Eigenschaften“ klicken Sie auf **Ansicht** auf dem Menüband, und klicken Sie dann auf **Eigenschaften**.  
  
4.  `Hidden`Wählen Sie in eine der folgenden Optionen aus, um die Sichtbarkeit dieses Berichts Elements beim erstmaligen Ausführen eines Berichts festzulegen:  
  
    -   Wählen Sie diese Option aus `False` , um das Berichts Element anzuzeigen.  
  
    -   Aktivieren Sie diese Option `True` , um das Berichts Element auszublenden.  
  
    -   Wählen Sie diese **\<Expression>** Option aus, um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen, der zur Laufzeit zum Bestimmen der Sichtbarkeit ausgewertet wird.  
  
5.  Wählen Sie unter **ToggleItem**im Dropdownfeld den Namen eines Textfelds aus, dem das Umschaltbild hinzugefügt werden soll.  
  
     In der folgenden Grafik ist die Zeilengruppenfarbe so konfiguriert, dass Benutzer zugehörige Zeilen erweitern und reduzieren können.  
  
     ![Konfigurieren einer zu erweiternden Zeilengruppe](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Konfigurieren einer zu erweiternden Zeilengruppe")  
  
    > [!NOTE]  
    >  Bei dem Textfeld mit dem Umschaltbild kann es sich nicht um die Zeilen- oder Spaltengruppe handeln, deren Zeilen oder Spalten ausgeblendet werden sollen. Es muss sich entweder in derselben Gruppe wie das ausgeblendete Element oder in einer Vorgängergruppe befinden. Beispiel: Wenn Sie die Sichtbarkeit von Zeilen umschalten möchten, die mit einer untergeordneten Gruppe verknüpft sind, wählen Sie ein Textfeld in einer Zeile, die mit der übergeordneten Gruppe verknüpft ist.  
  
6.  Führen Sie den Bericht aus, und klicken Sie auf das Textfeld mit dem Umschaltbild, um die Umschaltfunktion zu testen. Die Berichtsanzeige wird aktualisiert, sodass Zeilengruppen und Spaltengruppen nun mit ihrer umgeschalteten Sichtbarkeit angezeigt werden.  
  
     ![Ausführen des Berichts mit einer erweiterbaren Zeilengruppe](../media/expandcollapse-runreport-rowgroup.png "Ausführen des Berichts mit einer erweiterbaren Zeilengruppe")  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a>So fügen Sie einem Berichtselement eine Erweiterungs- und Reduzieraktion hinzu  
  
1.  Klicken Sie in der Berichtsentwurfs Ansicht mit der rechten Maustaste auf das Berichts Element, das angezeigt oder ausgeblendet werden soll, und klicken Sie dann auf *\<report item>* **Eigenschaften** Das *\<report item>* Dialogfeld **Eigenschaften** für das Berichts Element wird geöffnet.  
  
2.  Klicken Sie auf **Sichtbarkeit**.  
  
3.  Wählen Sie in **Bei erstmaliger Ausführung des Berichts**eine der folgenden Optionen aus, um die Sichtbarkeit dieses Berichtselements bei der erstmaligen Ausführung des Berichts festzulegen:  
  
    -   Wählen Sie **Anzeigen** aus, wenn das Berichtselement angezeigt werden soll.  
  
    -   Wählen Sie **Ausblenden** aus, wenn das Berichtselement ausgeblendet werden soll.  
  
    -   Wählen Sie **Je nach Ausdruck einblenden/ausblenden** aus, wenn die Sichtbarkeit durch einen zur Laufzeit ausgewerteten Ausdruck bestimmt werden soll. Klicken Sie auf (**FX**), um das Dialogfeld **Ausdruck** zu öffnen und einen Ausdruck zu erstellen.  
  
        > [!NOTE]  
        >  Wenn Sie einen Ausdruck für die Sichtbarkeit angeben, legen Sie die Eigenschaft „Hidden“ des Berichtselements fest. Der Ausdruck wird zu einem `Boolean` Wert von `True` ausgewertet, um das Element auszublenden, und zu `False`, um das Element anzuzeigen.  
  
4.  Wählen Sie unter **Sichtbarkeit kann von diesem Berichtselement ein-/ausgeschaltet werden**im Dropdownfeld den Namen eines Textfelds im Bericht aus, dem ein Umschaltbild hinzugefügt werden soll, oder geben Sie den Namen ein (z.B. „Textbox1“).  
  
     In der folgenden Grafik ist die Tabelle so konfiguriert, dass Benutzer sie erweitern und reduzieren können. Die Tabellenanzeige kann mithilfe des Textfelds „Produkttabelle“ ein- bzw. ausgeblendet werden.  
  
     ![Konfigurieren einer zu erweiternden Berichtstabelle](../media/expandcollapse-reporttable.png "Konfigurieren einer zu erweiternden Berichtstabelle")  
  
    > [!NOTE]  
    >  Das ausgewählte Textfeld muss im aktuellen oder enthaltenden Bereich für dieses Berichtselement enthalten sein (bis einschließlich des Berichtshauptteils). Wählen Sie zum Umschalten der Sichtbarkeit eines Diagramms z. B. ein Textfeld aus, das sich in demselben enthaltenden Bereich befindet wie das Diagramm, z. B. der Berichtshauptteil oder ein Rechteck. Das Textfeld muss sich in der gleichen Containerhierarchie oder auf einer höheren Ebene befinden.  
  
5.  Führen Sie den Bericht aus, und klicken Sie auf das Textfeld mit dem Umschaltbild, um die Umschaltfunktion zu testen. Die Berichtsanzeige wird aktualisiert, sodass Berichtselemente nun mit ihrer umgeschalteten Sichtbarkeit angezeigt werden.  
  
     ![Ausführen eines Berichts mit einer erweiterbaren Tabelle](../media/expandcollapse-runreport-reporttable.png "Ausführen eines Berichts mit einer erweiterbaren Tabelle")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drilldown-Aktion &#40;Berichts-Generator und SSRS&#41;](drilldown-action-report-builder-and-ssrs.md)   
 [Ausblenden eines Elements (Berichts-Generator und SSRS)](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
