---
title: Ändern der Product-Dimension | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 04c0a778a73371dada92c9ff207a17366a2fbc7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619434"
---
# <a name="modifying-the-product-dimension"></a>Ändern der Product-Dimension
  In den Aufgaben in diesem Thema verwenden Sie eine benannte Berechnung, um aussagekräftigere Namen für Produktlinien zur Verfügung zu stellen, definieren eine Hierarchie in der Product-Dimension, und geben den (All) -Elementnamen für die Hierarchie an. Außerdem gruppieren Sie Attribute in Anzeigeordner.  
  
## <a name="adding-a-named-calculation"></a>Hinzufügen einer benannten Berechnung  
 Sie können einer Tabelle in einer Datenquellensicht eine benannte Berechnung hinzufügen. In der folgenden Aufgabe erstellen Sie eine benannte Berechnung, die den vollständigen Produktliniennamen anzeigt.  
  
#### <a name="to-add-a-named-calculation"></a>So fügen Sie eine benannte Berechnung hinzu  
  
1.  Um die **Adventure Works DW 2012** -Datenquellensicht zu öffnen, doppelklicken Sie im Projektmappen-Explorer im Ordner **Datenquellensichten** auf **Adventure Works DW 2012** .  
  
2.  Klicken Sie unten im Diagrammbereich mit der rechten Maustaste auf die Tabellenüberschrift **Product** . Klicken Sie anschließend auf **Neue benannte Berechnung**.  
  
3.  Geben Sie im Dialogfeld **benannte Berechnung erstellen** `ProductLineName` im Feld **Spaltenname** ein.  
  
4.  Geben Sie in das Feld **Ausdruck** die folgende **CASE** -Anweisung ein (Sie können sie auch kopieren und einfügen):  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     Diese **CASE** -Anweisung erstellt benutzerfreundliche Namen für jede Produktlinie im Cube.  
  
5.  Klicken Sie auf **OK** , um die `ProductLineName` benannte Berechnung zu erstellen. Sie müssen möglicherweise einen Moment warten.  
  
6.  Klicken Sie im Menü **File** (Datei) auf **Save All** (Alles speichern).  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>Ändern der NameColumn-Eigenschaft eines Attributs  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>So ändern Sie den Wert der NameColumns-Eigenschaft eines Attributs  
  
1.  Wechseln Sie zum Dimensions-Designer für die Product-Dimension. Doppelklicken Sie dazu auf die **Product** -Dimension im **Dimensionen** -Knoten des Projektmappen-Explorers.  
  
2.  Wählen Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** die Option **Product Line**aus.  
  
3.  Klicken Sie im Eigenschaftenfenster auf der rechten Seite des Bildschirms unten im Fenster auf das Eigenschafts Feld **namecolumzun** , und klicken Sie dann auf die Schaltfläche zum Durchsuchen (**..**.), um das Dialogfeld **Namensspalte** zu öffnen. (Sie müssen ggf. auf die Registerkarte **Eigenschaften** auf der rechten Seite vom Bildschirm klicken, um das Eigenschaftenfenster zu öffnen).  
  
4.  Wählen Sie `ProductLineName` unten in der Liste **Quell Spalte** die Option aus, und klicken Sie dann auf **OK**.  
  
     Das Feld „NameColumn“ enthält jetzt den Text **Product.ProductLineName (WChar)**. Die Elemente der Attributhierarchie **Product Line** zeigen nun den vollständigen Namen der Produktlinie anstelle eines abgekürzten Produktliniennamens an.  
  
5.  Wählen Sie im Bereich **Attribute** der Registerkarte **Dimensionsstruktur** die Option **Product Key**aus.  
  
6.  Klicken Sie im Eigenschaftenfenster auf das Eigenschafts Feld **namecolumzun** , und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten (**...**), um das Dialogfeld **Namensspalte** zu öffnen.  
  
7.  Wählen Sie **EnglishProductName** in der Liste **Quellspalte** aus, und klicken Sie auf **OK**.  
  
     Das Feld "NameColumn" enthält jetzt den Text **Product.EnglishProductName (WChar)**.  
  
8.  Scrollen Sie im Eigenschaftenfenster nach oben, klicken Sie auf das Eigenschafts Feld **Name** , und geben Sie dann ein `Product Name` .  
  
## <a name="creating-a-hierarchy"></a>Erstellen einer Hierarchie  
  
#### <a name="to-create-a-hierarchy"></a>So erstellen Sie eine Hierarchie  
  
1.  Ziehen Sie das **Product Line** -Attribut vom Bereich **Attribute** in den Bereich **Hierarchien** .  
  
2.  Ziehen Sie das **Model Name** -Attribut aus dem **Attribute** -Bereich in die Zelle **\<new level>** des Bereichs **Hierarchien** unterhalb der **Product Line** -Ebene.  
  
3.  Ziehen Sie das- `Product Name` Attribut aus dem Bereich **Attribute** in die Zelle des Bereichs **\<new level>** **Hierarchien** unterhalb der **Model Name** -Ebene. (Sie haben im vorherigen Abschnitt Product Key in Product Name umbenannt.)  
  
4.  Klicken Sie im Bereich **Hierarchien** der Registerkarte **Dimensions Struktur** mit der rechten Maustaste auf die Titelleiste der **Hierarchie** Hierarchie, klicken Sie auf **Umbenennen**, und geben Sie dann ein `Product Model Lines` .  
  
     Der Name der Hierarchie lautet jetzt `Product Model Lines` .  
  
5.  Klicken Sie im Menü **File** (Datei) auf **Save All** (Alles speichern).  
  
## <a name="specifying-folder-names-and-all-member-names"></a>Angeben von Ordnernamen und Namen für alle Elemente  
  
#### <a name="to-specify-the-folder-and-member-names"></a>So geben Sie die Ordner- und Elementnamen an  
  
1.  Wählen Sie im Bereich **Attribute** die folgenden Attribute, indem Sie beim Klicken die STRG-Taste gedrückt halten:  
  
    -   **Klasse**  
  
    -   **Farbe**  
  
    -   **Zu Produktionstage**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **Größe**  
  
    -   **Size Range**  
  
    -   **style**  
  
    -   **Weight**  
  
2.  Geben Sie im Eigenschaftenfenster **AttributeHierarchyDisplayFolder** -Eigenschafts Feld ein `Stocking` .  
  
     Sie haben diese Attribute jetzt in einen einzigen Anzeigeordner gruppiert.  
  
3.  Wählen Sie im Bereich **Attribute** die folgenden Attribute aus:  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  Geben Sie in der **AttributeHierarchyDisplayFolder** -Eigenschafts Zelle im Eigenschaftenfenster ein `Financial` .  
  
     Sie haben diese Attribute jetzt in einen zweiten Anzeigeordner gruppiert.  
  
5.  Wählen Sie im Bereich **Attribute** die folgenden Attribute aus:  
  
    -   **Enddatum**  
  
    -   **Startdatum**  
  
    -   **Status**  
  
6.  Geben Sie in der **AttributeHierarchyDisplayFolder** -Eigenschafts Zelle im Eigenschaftenfenster ein `History` .  
  
     Sie haben diese Attribute jetzt in einen dritten Anzeigeordner gruppiert.  
  
7.  Wählen Sie die `Product Model Lines` Hierarchie im Bereich **Hierarchien** aus, und ändern Sie dann die **allmembership Name** -Eigenschaft in der Eigenschaftenfenster auf `All Products` .  
  
8.  Klicken Sie im Bereich **Hierarchien** auf einen geöffneten Bereich, und ändern Sie dann die **attributeallmembership Name** -Eigenschaft am oberen Rand des Eigenschaftenfenster in `All Products` .  
  
     Durch das Anklicken eines offenen Bereichs können Sie Eigenschaften der Produktdimension selbst ändern. Sie können auch auf **Product** am oberen Rand der Attributliste im Bereich **Attribute** klicken.  
  
9. Klicken Sie im Menü **File** (Datei) auf **Save All** (Alles speichern).  
  
## <a name="defining-attribute-relationships"></a>Definieren von Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch Attributbeziehungen zwischen Attributen definieren. Durch Definieren von Attributbeziehungen wird die Dimensions-, Partitions- und Abfrageverarbeitung beschleunigt. Weitere Informationen finden Sie unter [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md) und [Attributbeziehungen](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>So definieren Sie Attributbeziehungen  
  
1.  Klicken Sie im **Dimensions-Designer** für die Product-Dimension auf die Registerkarte **Attributbeziehungen** .  
  
2.  Klicken Sie im Diagramm mit der rechten Maustaste auf das **Model Name** -Attribut und anschließend auf **Neue Attributbeziehung**.  
  
3.  Im Dialogfeld **Attributbeziehung erstellen** lautet das **Quellattribut****Model Name**. Legen Sie für **Verknüpftes Attribut** die Einstellung **Produktgruppe**fest.  
  
     Belassen Sie in der Liste **Beziehungstyp** den Beziehungstyp auf **Flexibel** , da sich Beziehungen zwischen den Elementen im Laufe der Zeit ändern können. So könnte ein Produktmodell beispielsweise in eine andere Produktlinie verschoben werden.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie im Menü **File** (Datei) auf **Save All** (Alles speichern).  
  
## <a name="reviewing-product-dimension-changes"></a>Überprüfen von Produktdimensionsänderungen  
  
#### <a name="to-review-the-product-dimension-changes"></a>So überprüfen Sie die Produktdimensionsänderungen  
  
1.  Klicken Sie im Menü **Erstellen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf **Analysis Services Tutorial bereitstellen**.  
  
2.  Nachdem die Meldung **Bereitstellung erfolgreich abgeschlossen** angezeigt wird, klicken Sie auf die Registerkarte **Browser** im **Dimensions-Designer** für die **Product** -Dimension und anschließend auf der Symbolleiste auf die Schaltfläche zum Wiederherstellen der Verbindung.  
  
3.  Vergewissern Sie sich, dass `Product Model Lines` in der Liste **Hierarchie** ausgewählt ist, und erweitern Sie dann `All Products` .  
  
     Beachten Sie, dass der Name des Elements **alle** als angezeigt wird `All Products` . Dies liegt daran, dass Sie die **allmembership Name** -Eigenschaft für die Hierarchie `All Products` in eine frühere Version der Lektion geändert haben. Auch verfügen die Elemente der **Product Line** -Ebene jetzt über benutzerfreundliche Namen anstelle von Abkürzungen aus einem Buchstaben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ändern der Date-Dimension](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren Sie benannte Berechnungen in einer Datenquellen Sicht &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)   
 [Erstellen von benutzerdefinierten Hierarchien](multidimensional-models/user-defined-hierarchies-create.md)   
 [Konfigurieren der Ebene &#40;Alle&#41; für Attributhierarchien](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
