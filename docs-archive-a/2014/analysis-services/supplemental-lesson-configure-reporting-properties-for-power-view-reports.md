---
title: Konfigurieren von Bericht Erstellungs Eigenschaften für Power View Berichte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ffc5f44-17d3-42d4-bc2c-baf3b4485e2d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7776d9af8b2eb98533ac9ff2e7b1b8a760b92565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721789"
---
# <a name="configure-reporting-properties-for-power-view-reports"></a>Konfigurieren von Berichterstellungseigenschaften für Power View-Berichte
  In dieser ergänzenden Lektion legen Sie Berichterstellungseigenschaften für das Projekt Adventure Works Internet Sales Model fest. Berichterstellungseigenschaften erleichtern Endbenutzern das Auswählen und Anzeigen von Modelldaten in Power View. Zusätzlich legen Sie Eigenschaften fest, um bestimmte Spalten und Tabellen auszublenden und neue Daten zur Verwendung in Diagrammen zu erstellen.  
  
 Nach Abschluss dieser Lektion und der erneuten Bereitstellung des Modells für eine in SharePoint und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] integrierte [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Instanz können Sie eine Datenquelle erstellen, Informationen zu Datenverbindungen angeben, Power View starten und Berichte anhand des Modells entwerfen.  
  
 In dieser Lektion wird nicht beschrieben, wie Power View-Berichte erstellt und verwendet werden. Diese Lektion bietet Entwicklern tabellarischer Modelle eine Einführung in die Eigenschaften und Einstellungen, mit denen die Darstellung der Modelldaten in Power View beeinflusst wird. Weitere Informationen zum Erstellen von Power View-Berichten finden Sie unter [Tutorial: Erstellen eines Beispielberichts in Power View](https://go.microsoft.com/fwlink/?LinkId=221204).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **30 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Diese ergänzende Lektion ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie diese ergänzende Lektion beginnen, sollten Sie alle vorherigen Lektionen abgeschlossen haben.  
  
 Zum Ausführen dieser ergänzenden Lektion benötigen Sie zusätzlich Folgendes:  
  
-   Das (in diesem Lernprogramm fertig gestellte) Adventure Works Internet Sales Model, das für eine Analysis Services-Instanz bereitgestellt werden kann, die im tabellarischen Modus ausgeführt wird, bzw. das bereits bereitgestellt wurde.  
  
-   Eine SharePoint-Website, die in [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] im tabellarischem Modus sowie in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]integriert ist, die für die Unterstützung von Power View-Berichten konfiguriert wurden.  
  
-   Ausreichende Berechtigungen zum Erstellen einer Datenverbindung auf der SharePoint-Website, die auf das Adventure Works Internet Sales Model verweist.  
  
## <a name="model-properties-that-affect-reporting"></a>Modelleigenschaften, die sich auf die Berichterstellung auswirken  
 Beim Erstellen eines tabellarischen Modells können bestimmte Eigenschaften für einzelne Spalten und Tabellen festgelegt werden, um die Berichterstellung in Power View für den Endbenutzer zu verbessern. Darüber hinaus können Sie zusätzliche Modelldaten erstellen, um die Datenvisualisierung und weitere Funktionen zu unterstützen, die für den Berichterstellungsclient spezifisch sind. Im Folgenden sind einige Änderungen aufgeführt, die Sie am Beispiel Adventure Works Internet Sales Model vornehmen:  
  
-   **Hinzufügen neuer Daten** : durch das Hinzufügen neuer Daten in einer berechneten Spalte mithilfe einer DAX-Formel werden Datumsinformationen in einem Format erstellt, das in Diagrammen einfacher angezeigt werden kann.  
  
-   **Tabellen und Spalten ausblenden, die für den Endbenutzer nicht von Nutzen sind** – Die Eigenschaft **Ausgeblendet** steuert, ob Tabellen und Tabellenspalten im Berichterstellungsclient angezeigt werden. Elemente mit dieser Eigenschaft werden zwar ausgeblendet, bleiben jedoch Teil des Modells und sind weiterhin für Abfragen und Berechnungen verfügbar.  
  
-   **One-Click-Tabellen aktivieren** : Standardmäßig erfolgt keine Aktion, wenn ein Endbenutzer auf eine Tabelle in der Feldliste klickt. Um dieses Verhalten zu ändern, legen Sie für jede Spalte, die Sie in die Tabelle aufnehmen möchten, einen Standardfeldsatz fest, damit die Tabelle dem Bericht hinzugefügt wird, wenn darauf geklickt wird. Diese Eigenschaft wird für die Tabellenspalten festgelegt, die Endbenutzer am wahrscheinlichsten verwenden möchten.  
  
-   **Gruppierungen festlegen, falls erforderlich** – Die Eigenschaft **Eindeutige Zeilen beibehalten** bestimmt, ob die Werte in der Spalte nach Werten in einem anderen Feld gruppiert werden sollen, z.B. einem Bezeichnerfeld. Für Spalten, die doppelte Werte aufweisen (z.B. wenn die Spalte „Kundenname“ mehrere Kunden mit dem Namen „John Smith“ enthält), sollte unbedingt eine Gruppierung ( **Eindeutige Zeilen beibehalten** ) nach dem Feld Zeilenbezeichner ausgeführt werden, damit Endbenutzern die richtigen Ergebnisse zur Verfügung gestellt werden können.  
  
-   **Datentypen und Datenformate festlegen** – Power View wendet standardmäßig Regeln auf Grundlage des Spaltendatentyps an, um zu bestimmen, ob das Feld als Measure verwendet werden kann. Da auch jede Datenvisualisierung in Power View über Regeln verfügt, die bestimmen, wo Measures und Nicht-Measures platziert werden können, ist es wichtig, den Datentyp im Modell festzulegen oder den Standardwert zu überschreiben, um das für den Endbenutzer gewünschte Verhalten zu erzielen.  
  
-   **Legen Sie die Eigenschaft nach Spalte sortieren fest** . die Eigenschaft **nach Spalte sortieren** gibt an, ob die Werte in der Spalte nach Werten in einem anderen Feld sortiert werden sollen. Beispiel: In der Spalte Month Calendar, die den Monatsnamen enthält, soll eine Sortierung nach der Spalte Month Number ausgeführt werden.  
  
## <a name="hide-tables-from-client-tools"></a>Ausblenden von Tabellen aus Clienttools  
 Da bereits eine berechnete Spalte Product Category und eine berechnete Spalte Product Subcategory in der Tabelle Product vorhanden sind, ist es nicht notwendig, dass die Tabellen Product Category und Product Subcategory für Clientanwendungen sichtbar sind.  
  
#### <a name="to-hide-the-product-category-and-product-subcategory-tables"></a>So blenden Sie die Tabellen "Product Category" und "Product Subcategory" aus  
  
1.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die Tabelle (Registerkarte) **Product Category** , und klicken Sie anschließend auf **Aus Clienttools ausblenden**.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle (Registerkarte) **Product Subcategory** , und klicken Sie anschließend auf **Aus Clienttools ausblenden**.  
  
## <a name="create-new-data-for-charts"></a>Erstellen neuer Daten für Diagramme  
 Es kann zeitweise erforderlich sein, mithilfe von DAX-Formeln neue Daten im Modell zu erstellen. In dieser Aufgabe fügen Sie der Tabelle Date zwei neue berechnete Spalten hinzu. Diese neuen Spalten enthalten Datumsfelder in einem für Diagramme geeigneten Format.  
  
#### <a name="to-create-new-data-for-charts"></a>So erstellen Sie neue Daten für Diagramme  
  
1.  Führen Sie in der Tabelle **Date** einen Bildlauf zum rechten Rand der Tabelle durch, und klicken Sie anschließend auf **Spalte hinzufügen**.  
  
2.  Fügen Sie mithilfe der folgenden Formeln in der Bearbeitungsleiste zwei neue berechnete Spalten hinzu:  
  
    |Spaltenname|Formel|  
    |-----------------|-------------|  
    |Year Quarter|=[Calendar Year] & " Q" & [Calendar Quarter]|  
    |Year Month|=[Calendar Year] & FORMAT([Month],"#00")|  
  
## <a name="default-field-set"></a>Standardfeldsatz  
 Der Standardfeldsatz ist eine vordefinierte Liste von Spalten und Measures für eine Tabelle, die dem Power View-Berichtszeichenbereich automatisch hinzugefügt werden, wenn in der Berichtsfeldliste auf die Tabelle geklickt wird. Im Wesentlichen können Sie die standardmäßigen Spalten und Measures sowie die Feldreihenfolge angeben, die Benutzer erwarten würden, wenn diese Tabelle in Power View-Berichten visuell dargestellt wird.  Für das Modell Internet Sales definieren Sie einen Standardfeldsatz und eine Standardreihenfolge für die Tabellen Customer, Geography und Product. Es werden nur die am häufigsten verwendeten Spalten aufgenommen, die Benutzer zum Analysieren der Daten in Adventure Works Internet Sales mithilfe von Power View-Berichten benötigen.  
  
 Ausführliche Informationen zum Standardfeldsatz finden Sie unter [Konfigurieren eines Standardfeldsatzes für Power View-Berichte &#40;SSAS – tabellarisch&#41;](tabular-models/power-view-configure-default-field-set-for-reports.md) in der SQL Server-Onlinedokumentation.  
  
#### <a name="to-set-default-field-set-for-tables"></a>So legen Sie den Standardfeldsatz für Tabellen fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie im **Eigenschaftenfenster** unter **Berichterstellungseigenschaften**in der Eigenschaft **Standardfeldsatz** auf **Zum Bearbeiten klicken** , um das Dialogfeld **Standardfeldsatz** zu öffnen.  
  
3.  Drücken Sie im Dialogfeld **Standardfeldsatz** im Listenfeld **Felder in der Tabelle** STRG, wählen Sie die folgenden Felder aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
     **Birth Date**, **Customer Alternate Id**, **First Name**, **Last Name**.  
  
4.  Verwenden Sie im Fenster **Standardfelder in Reihenfolge** die Schaltflächen Nach oben und Nach unten, um die folgende Reihenfolge festzulegen:  
  
     **Customer Alternate ID**  
  
     **Vorname**  
  
     **Last Name**  
  
     **Birth Date**  
  
5.  Klicken Sie auf **OK** , um das Dialogfeld **Standardfeldsatz** für die Tabelle **Customer** zu schließen.  
  
6.  Führen Sie die gleichen Schritte für die Tabelle **Geography** aus, wobei Sie die folgenden Felder auswählen und die angegebene Reihenfolge beachten.  
  
     **City**, **State Province Code**, **State Region Code**.  
  
7.  Führen Sie zuletzt die gleichen Schritte für die Tabelle **Product** aus, wobei Sie die folgenden Felder auswählen und die angegebene Reihenfolge beachten.  
  
     **Product Alternate Id**, **Product Name**.  
  
## <a name="table-behavior"></a>Tabellenverhalten  
 Mit den Eigenschaften für das Tabellenverhalten können Sie das Standardverhalten für unterschiedliche Visualisierungstypen und das Gruppierungsverhalten für die in Power View-Berichten verwendeten Tabellen ändern. Auf diese Weise wird eine bessere Standardplatzierung von identifizierenden Informationen, wie Namen, Bildern oder Titeln, in Kachel-, Karten- und Diagrammlayouts erzielt.  
  
 Ausführliche Informationen zu-Tabellenverhaltenseigenschaften finden Sie unter [Konfigurieren von Tabellenverhaltenseigenschaften für Power View-Berichte &#40;SSAS – tabellarisch&#41;](tabular-models/power-view-configure-table-behavior-properties-for-reports.md) in der SQL Server-Onlinedokumentation.  
  
#### <a name="to-set-table-behavior-for-tables"></a>So legen Sie das Tabellenverhalten für Tabellen fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie im **Eigenschaftenfenster** in der Eigenschaft **Tabellenverhalten** auf **Zum Bearbeiten klicken**, um das Dialogfeld **Tabellenverhalten** zu öffnen.  
  
3.  Wählen Sie im Dialogfeld **Tabellenverhalten** im Dropdown-Listenfeld **Zeilenbezeichner** die Spalte **Customer Id** aus.  
  
4.  Wählen Sie im Listenfeld **Eindeutige Zeilen beibehalten****First Name** und **Last Name**aus.  
  
     Durch diese Eigenschafteneinstellung wird angegeben, dass diese Spalten Werte bereitstellen, die selbst dann als eindeutige Werte angesehen werden sollen, wenn sie doppelt vorkommen, z. B. wenn mindestens zwei Mitarbeiter den gleichen Namen aufweisen.  
  
5.  Wählen Sie im Dropdown-Listenfeld **Standardbeschriftung** die Spalte **Last Name** aus.  
  
     Durch diese Eigenschafteneinstellung wird angegeben, dass diese Spalte einen Anzeigenamen zur Darstellung von Zeilendaten bereitstellt.  
  
6.  Wiederholen Sie diese Schritte für die Tabelle **Geography** , wobei Sie die Spalte **Geography Id** als Zeilenbezeichner und die Spalte **City** im Listenfeld **Eindeutige Zeilen beibehalten** auswählen. Sie müssen keine Standardbeschriftung für diese Tabelle festlegen.  
  
7.  Wiederholen Sie diese Schritte für die Tabelle **Product** , wobei Sie die Spalte **Product Id** als Zeilenbezeichner und die Spalte **Product Name** im Listenfeld **Eindeutige Zeilen beibehalten** auswählen. Wählen Sie für **Standardbeschriftung****Product Alternate Id**aus.  
  
## <a name="reporting-properties-for-columns"></a>Berichterstellungseigenschaften für Spalten  
 Für Spalten können eine Reihe grundlegender Spalteneigenschaften und bestimmte Berichterstellungseigenschaften festgelegt werden, mit deren Hilfe sich die Berichterstellung anhand von Modellen verbessern lässt. Es ist u. U. nicht erforderlich, dass Benutzer jede Spalte in jeder Tabelle sehen können. Ebenso wie Sie die Tabellen "Product Category" und "Product Subcategory" zuvor verborgen haben, können Sie mithilfe der Hidden-Eigenschaft einer Spalte bestimmte Spalten aus einer Tabelle ausblenden, die ansonsten angezeigt wird. Auch andere Eigenschaften, wie Datenformat und Nach Spalte sortieren, können die Darstellung von Spaltendaten in Berichten beeinflussen. Jetzt legen Sie einige Eigenschaften für bestimmten Spalten fest. Für andere Spalten ist keine Aktion erforderlich, daher werden sie unten nicht dargestellt.  
  
 Sie legen hier nur einige von zahlreichen Spalteneigenschaften fest. Ausführlichere Informationen zu Berichterstellungseigenschaften für Spalten finden Sie unter [Spalteneigenschaften &#40;SSAS – tabellarisch&#41;](tabular-models/properties-ssas-tabular.md) in der SQL Server-Onlinedokumentation.  
  
#### <a name="to-set-properties-for-columns"></a>So legen Sie Eigenschaften für Spalten fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie auf die Spalte **Customer Id** , um die Spalteneigenschaften im **Eigenschaftenfenster** anzuzeigen.  
  
3.  Legen Sie im **Eigenschaftenfenster** die Eigenschaft **Ausgeblendet** auf True fest. Daraufhin wird die Spalte **Customer Id** im Modell-Designer abgeblendet dargestellt.  
  
4.  Wiederholen Sie diese Schritte, und legen Sie die folgenden Spalten- und Berichterstellungseigenschaften für alle angegebenen Tabellen fest. Verwenden Sie für alle anderen Eigenschaften die Standardeinstellungen.  
  
     **Customer**  
  
    |Spalte|Eigenschaft|Wert|  
    |------------|--------------|-----------|  
    |Geography Id|Ausgeblendet|True|  
    |Birth Date|Datenformat|Short Date|  
  
     **Datum**  
  
    > [!NOTE]  
    >  Da die Tabelle Date mithilfe der Einstellung Als Datumstabelle markieren in "Lektion 7: Markieren als Datumstabelle" als Datumstabelle für das Modell ausgewählt wurde und die Spalte Date in der Tabelle Date als Spalte ausgewählt wurde, die als eindeutiger Bezeichner fungieren soll, wird die Eigenschaft Zeilenbezeichner für die Spalte Date automatisch auf True festgelegt und kann nicht geändert werden. Bei Verwendung von Zeitintelligenzfunktionen in DAX-Formeln müssen Sie eine Datumstabelle angeben. In diesem Modell haben Sie unter Verwendung von Zeitintelligenzfunktionen eine Reihe von Measures zur Berechnung von Umsatzdaten für verschiedene Zeiträume, z. B. das vorherige und aktuelle Quartal, sowie zur Verwendung in KPIs erstellt. Weitere Informationen zum Angeben einer Datumstabelle finden Sie unter [Angeben von „Als Datumstabelle markieren“ zur Verwendung mit Zeitintelligenz &#40;SSAS – tabellarisch&#41;](tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md) in der SQL Server-Onlinedokumentation.  
  
    |Spalte|Eigenschaft|Wert|  
    |------------|--------------|-----------|  
    |Date|Datenformat|Short Date|  
    |Day Number of Week|Ausgeblendet|True|  
    |Day Name|Nach Spalte sortieren|Day Number of Week|  
    |Tag der Woche|Ausgeblendet|True|  
    |Tag des Monats|Ausgeblendet|True|  
    |Tag des Jahres|Ausgeblendet|True|  
    |Name Monat|Nach Spalte sortieren|Month|  
    |Month|Ausgeblendet|True|  
    |Month Calendar|Ausgeblendet|True|  
    |Fiscal Quarter|Ausgeblendet|True|  
    |Fiscal Year|Ausgeblendet|True|  
    |Fiscal Semester|Ausgeblendet|True|  
  
     **Geografie**  
  
    |Spalte|Eigenschaft|Wert|  
    |------------|--------------|-----------|  
    |Geography Id|Ausgeblendet|True|  
    |Sales Territory Id|Ausgeblendet|True|  
  
     **Produkt**  
  
    |Spalte|Eigenschaft|Wert|  
    |------------|--------------|-----------|  
    |Product Id|Ausgeblendet|True|  
    |Product Alternate Id|Standardbeschriftung|True|  
    |Product Subcategory Id|Ausgeblendet|True|  
    |Product Start Date|Datenformat|Short Date|  
    |Product End Date|Datenformat|Short Date|  
    |Large Photo|Ausgeblendet|True|  
  
     **Internetumsätze**  
  
    |Spalte|Eigenschaft|Wert|  
    |------------|--------------|-----------|  
    |Product Id|Ausgeblendet|True|  
    |Customer Id|Ausgeblendet|True|  
    |Promotion Id|Ausgeblendet|True|  
    |Currency Id|Ausgeblendet|True|  
    |Sales Territory Id|Ausgeblendet|True|  
    |Order Quantity|Datentyp<br /><br /> Datenformat<br /><br /> Dezimalstellen|Decimal Number<br /><br /> Decimal Number<br /><br /> 0|  
    |Order Date|Datentyp|Short Date|  
    |Due Date|Datentyp|Short Date|  
    |Ship Date|Datentyp|Short Date|  
  
## <a name="redeploy-the-adventure-works-internet-sales-tabular-model"></a>Erneutes Bereitstellen des tabellarischen Modells "Adventure Works Internet Sales"  
 Da Sie das Modell geändert haben, müssen Sie es erneut bereitstellen. Sie wiederholen im Wesentlichen die in [Lektion 14: Bereitstellen](lesson-13-deploy.md)ausgeführten Aufgaben.  
  
#### <a name="to-redeploy-the-adventure-works-internet-sales-tabular-model"></a>So stellen Sie das tabellarische Modell "Adventure Works Internet Sales" erneut bereit  
  
-   Klicken Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]im Menü **Erstellen** auf die Option zum Bereitstellen von **Adventure Works Internet Sales Model**.  
  
     Das **Dialogfeld** bereitstellen wird angezeigt und zeigt den Bereitstellungs Status der Metadaten sowie jede im Modell enthaltene Tabelle an.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Jetzt können Sie Daten aus dem Modell mithilfe von Power View visuell darstellen. Vergewissern Sie sich, dass das Analysis Services-Konto und Reporting Services-Konto auf der SharePoint-Website über Leseberechtigungen für die Analysis Services-Instanz verfügen, in der Sie das Modell bereitgestellt haben.  
  
 Informationen zum Erstellen einer Reporting Services-Berichtsdatenquelle, die auf das Modell verweist, finden Sie unter [Tabellenmodell-Verbindungstyp (SSRS)](https://msdn.microsoft.com/library/hh270317%28v=SQL.110%29.aspx).  
  
  
