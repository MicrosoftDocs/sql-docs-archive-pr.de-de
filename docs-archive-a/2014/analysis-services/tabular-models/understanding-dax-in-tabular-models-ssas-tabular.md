---
title: Grundlegendes zu DAX in tabellarischen Modellen (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2693985-1bea-4861-a100-cea4761ba809
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bf7dc2f41a1d42e8b565459c3b094479d937a91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621188"
---
# <a name="understanding-dax-in-tabular-models-ssas-tabular"></a>Grundlegendes zu DAX in tabellarischen Modellen (SSAS – tabellarisch)
  Data Analysis Expressions (DAX) ist die Formelsprache, mit der benutzerdefinierte Berechnungen in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Microsoft Excel-Arbeitsmappen und tabellarische [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Modellprojekte erstellt werden. DAX-Formeln beinhalten Funktionen, Operatoren und Werte zum Ausführen erweiterter Berechnungen für Daten in Tabellen und Spalten.  
  
 Obwohl DAX sowohl für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen als auch für tabellarische Modellprojekte verwendet wird, betrifft dieses Thema in erster Linie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellte tabellarische Modellprojekte. Dieses Thema setzt umfassende Kenntnisse in tabellarischen Modellen und der Erstellungsumgebung für tabellarische Modellprojekte in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]voraus.  
  
 Abschnitte in diesem Thema:  
  
-   [DAX in tabellarischen Modellen](#bkmk_DAXintm)  
  
-   [DAX-Formeln in berechneten Spalten, Measures und Zeilenfiltern](#bkmk_DAX)  
  
-   [DAX-Datentypen](#bkmk_DAX_datatypes)  
  
-   [DAX-Operatoren](#bkmk_DAX_opertors)  
  
-   [DAX-Formeln](#bkmk_DAX_Formulas)  
  
-   [DAX-Funktionen](#bkmk_DAX_functions)  
  
-   [Kontext in DAX-Formeln](#bkmk_context)  
  
-   [Formeln und das tabellarische Modell](#bkmk_RelModel)  
  
-   [Arbeiten mit Tabellen und Spalten](#bkmk_tables)  
  
-   [Aktualisieren der Ergebnisse von Formeln (Prozess)](#bkmk_RefreshRecalc)  
  
-   [Beheben von Fehlern in Formeln](#bkmk_troubleshoot)  
  
-   [Weitere Ressourcen](#bkmk_addional_resources)  
  
##  <a name="dax-in-tabular-models"></a><a name="bkmk_DAXintm"></a>DAX in tabellarischen Modellen  
 In [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und tabellarischen Modellen besteht kein funktioneller Unterschied bezüglich der Art und Weise, wie DAX-Formeln Werte aus den entsprechenden Datasets berechnen. Die Stelle, an der DAX-Formeln in der Arbeitsmappe und Modellerstellungstools erstellt werden und Kontext in bestimmten Measures ausgewertet wird, unterscheidet sich jedoch.  
  
 In [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]werden Berechnungsformeln in der Regel vom Benutzer der Arbeitsmappe für die Self-Service-Business Intelligence-Analyse erstellt. Berechnete Spalten werden für eine Tabelle im PowerPivot-Fenster erstellt, und Measures werden in PivotTables oder im Berechnungsbereich erstellt. Im Gegensatz zu Projekten für tabellarische Modelle bieten PowerPivot-Arbeitsmappen keine rollenbasierte Sicherheit, die mithilfe von DAX-Formeln Daten sichern kann.  
  
 In Projekten für tabellarische Modelle werden Berechnungsformeln von Modellentwicklern im Modell-Designer von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt. Während Werte für mit DAX-Formeln berechnete Spalten sofort in der Tabelle im Modell-Designer angezeigt werden, werden Measures, abgesehen von der Measurevorschaufeature im Measureraster, erst berechnet, nachdem ein Benutzer einen Filter in einem Berichterstellungsclient wie [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] oder in PivotTables in Microsoft Excel angegeben hat.  
  
 Wenn Sie eine PowerPivot-Arbeitsmappe mit der Projektvorlage Aus PowerPivot importieren in ein neues tabellarisches Modellprojekt importieren, werden DAX-Formeln für berechnete Spalten automatisch im neuen tabellarischen Modell erstellt. DAX-Formeln für implizite und explizite Measures in der Arbeitsmappe werden automatisch im neuen tabellarischen Modell als explizite Measures erstellt. Da PowerPivot-Arbeitsmappen noch keine Filterfunktionen für Rollen und sichere Zeilen enthalten, müssen Sie mindestens eine Rolle im neuen tabellarischen Modell erstellen, um Rollenmitgliedern Zugriff auf Modelldaten zu erteilen. DAX-Formeln in Zeilenfiltern sind nur erforderlich, wenn Sie Tabellendaten auf der Zeilenebene schützen möchten.  
  
##  <a name="dax-formulas-in-calculated-columns-measures-and-row-filters"></a><a name="bkmk_DAX"></a>DAX-Formeln in berechneten Spalten, Measures und Zeilen filtern  
 Für in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellte tabellarische Modelle werden DAX-Formeln in berechneten Spalten, Measures und Zeilenfiltern verwendet.  
  
### <a name="calculated-columns"></a>Berechnete Spalten  
 Eine berechnete Spalte ist eine Spalte, die Sie einer vorhandenen Tabelle (im Modell-Designer) hinzufügen und für die Sie dann eine DAX-Formel erstellen, die die Spaltenwerte definiert. Formeln für berechnete Spalten werden im Modell-Designer mithilfe der Bearbeitungsleiste erstellt.  
  
> [!NOTE]  
>  Berechnete Spalten werden nicht für Modelle unterstützt, die Daten mit dem DirectQuery-Modus aus einer relationalen Datenquelle abrufen.  
  
 Wenn eine berechnete Spalte eine gültige DAX-Formel enthält, werden Werte für jede Zeile berechnet, sobald die Formel eingegeben wird. Werte werden dann in der Datenbank gespeichert. Wenn in einer Date-Tabelle beispielsweise die Formel `=[Calendar Year] & " Q" & [Calendar Quarter]` in die Bearbeitungsleiste eingegeben wird, wird ein Wert für jede Zeile in der Tabelle berechnet, indem Werten aus der Calendar Year-Spalte (in der gleichen Date-Tabelle) ein Leerzeichen und der Großbuchstabe Q hinzugefügt wird und anschließend die Werte aus der Calendar Quarter-Spalte (in der gleichen Date-Tabelle) hinzugefügt werden. Das Ergebnis wird für jede Zeile in der berechneten Spalte sofort berechnet und beispielsweise in der Form **2010 Q1**angezeigt. Spaltenwerte werden nur neu berechnet, wenn die Daten erneut verarbeitet werden.  
  
 Weitere Informationen finden Sie unter [Berechnete Spalten &#40;SSAS – tabellarisch&#41;](ssas-calculated-columns.md)erstellte tabellarische Modellprojekte.  
  
### <a name="measures"></a>Measures  
 Measures sind dynamische Formeln, deren Ergebnisse sich abhängig vom Kontext ändern. Measures werden in Berichtsformaten verwendet, die das Kombinieren und Filtern von Modelldaten anhand mehrerer Attribute unterstützen, z. B. ein [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Bericht, eine PivotTable oder eine PivotChart. In tabellarischen Modellprojekten werden Measures vom Modellentwickler mit dem Measureraster (und der Bearbeitungsleiste) im Modell-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]definiert.  
  
 Die Formeln in Measures können automatische mithilfe der AutoSumme-Funktion erstellte Standardaggregationsfunktionen verwenden, z. B. COUNT oder SUM, oder Sie können mit DAX eigene Formeln definieren. Wenn Sie in der Bearbeitungsleiste eine Formel für ein Measure definieren, wird über die QuickInfo eine Vorschau der Ergebnisse für den Gesamtwert im aktuellen Kontext angezeigt. Die Ergebnisse werden jedoch noch nicht ausgegeben. Andere Measuredetails werden auch im Bereich **Eigenschaften** angezeigt.  
  
 Der Grund dafür, dass Sie die (gefilterten) Ergebnisse der Berechnung nicht sofort einsehen können, ist, dass das Ergebnis eines Measures ohne einen Kontext nicht bestimmt werden kann. Das Auswerten eines Measures erfordert eine Clientanwendung zur Berichtserstellung, die in der Lage ist, den erforderlichen Kontext bereitzustellen, um die relevanten Daten für jede Zelle abrufen und anschließend den Ausdruck für jede Zelle auswerten zu können. Dieser Client kann eine Excel PivotTable oder PivotChart, ein [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Bericht oder eine MDX-Abfrage sein. Unabhängig vom Berichterstellungsclient wird tatsächlich für jede Zelle in den Ergebnissen eine separate Abfrage ausgeführt. Demzufolge generiert jede Kombination aus Zeilen- und Spaltenüberschriften in einer PivotTable und jede Auswahl von Slicern und Filtern in einem [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Bericht eine andere Teilmenge der Daten, für die das Measure berechnet wird. Wenn ein Benutzer beispielsweise in einem Measure mit der Formel `Total Sales:=SUM([Sales Amount])`das Total Sales-Measure im Fenster Werte in einer PivotTable und anschließend die Product Category-Spalte aus einer Product-Tabelle im Fenster Zeilenfilter einfügt, wird die Summe von Sales Amount berechnet und für jede Produktkategorie angezeigt.  
  
 Im Gegensatz zu berechneten Spalten und Zeilenfiltern enthält die Syntax für ein Measure eine Formel mit vorangestelltem Name des Measures. Im obigen Beispiel wird der Name **Total Sales:** vor der Formel angezeigt. Nachdem Sie ein Measure erstellt haben, werden der Name und die Definition in der Feldliste der Clientanwendung zur Berichtserstellung angezeigt, und das Measure steht, abhängig von Perspektiven und Rollen, allen Benutzern des Modells zur Verfügung.  
  
 Weitere Informationen finden Sie unter [Measures &#40;SSAS – tabellarisch&#41;](measures-ssas-tabular.md)erstellte tabellarische Modellprojekte.  
  
### <a name="row-filters"></a>Zeilenfilter  
 Zeilenfilter definieren, welche Zeilen in einer Tabelle für Mitglieder einer bestimmten Rolle sichtbar sind. Zeilenfilter können für jede Tabelle in einem Modell mithilfe von DAX-Formeln erstellt werden. Zeilenfilter werden für eine bestimmte Rolle mit dem Rollen-Manager in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellt. Zeilenfilter können auch für ein bereitgestelltes Modell mit Rolleneigenschaften in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]definiert werden.  
  
 In einem Zeilenfilter definiert eine DAX-Formel, die den booleschen Wert TRUE oder FALSE ergeben muss, die Zeilen, die von Mitgliedern dieser spezifischen Rolle in Form der Abfrageergebnisse zurückgegeben werden können. Nicht in der DAX-Formel enthaltene Zeilen können nicht zurückgegeben werden. Beispielsweise können Mitglieder der Sales-Rolle in der Customers-Tabelle mit der DAX-Formel `=Customers[Country] = "USA"`nur Daten für Kunden in den USA anzeigen. Außerdem werden Aggregate, z.B. SUM, nur für Kunden in den USA zurückgegeben.  
  
 Wenn Sie mithilfe der DAX-Formel einen Zeilenfilter definieren, erstellen Sie ein zulässiges Rowset. Dadurch wird der Zugriff auf andere Zeilen nicht verweigert, sie werden vielmehr nicht als Teil des zulässigen Rowsets zurückgegeben Andere Rollen können Zugriff auf die von der DAX-Formel ausgeschlossenen Zeilen gewähren. Wenn ein Benutzer Mitglied einer anderen Rolle ist und die Zeilenfilter dieser Rolle Zugriff auf diesen bestimmten Zeilensatz zulassen, kann der Benutzer Daten für diese Zeile anzeigen.  
  
 Zeilenfilter gelten für die angegebenen sowie für verknüpfte Zeilen. Wenn eine Tabelle über mehrere Beziehungen verfügt, wird die Sicherheit für die aktive Beziehung mithilfe von Filtern gewährleistet. Für Zeilenfilter und Zeilenfilter, die für verknüpfte Tabellen definiert wurden, wird eine Schnittmenge gebildet.  
  
 Weitere Informationen finden Sie unter [Rollen &#40;SSAS – tabellarisch&#41;](roles-ssas-tabular.md)erstellte tabellarische Modellprojekte.  
  
##  <a name="dax-data-types"></a><a name="bkmk_DAX_datatypes"></a> DAX-Datentypen  
 Daten können in ein Modell aus vielen unterschiedlichen Datenquellen importiert werden, die unterschiedliche Datentypen unterstützen. Beim Importieren von Daten in ein Modell werden die Daten in einen der tabellarischen Modelldatentypen umgewandelt. Wenn die Modelldaten in einer Berechnung verwendet werden, werden die Daten für die Dauer und die Ausgabe der Berechnung dann in einen DAX-Datentyp konvertiert. Wenn Sie eine DAX-Formel erstellen, bestimmen die in der Formel verwendeten Begriffe automatisch den zurückgegebenen Wertdatentyp.  
  
 Tabellarische Modelle und DAX unterstützen die folgenden Datentypen:  
  
|Datentyp im Modell|Datentyp in DAX|BESCHREIBUNG|  
|------------------------|----------------------|-----------------|  
|Ganze Zahl|Ein ganzzahliger 64-Bit-Wert (acht Byte) <sup>1, 2</sup>|Zahlen ohne Dezimalstellen. Ganze Zahlen können positiv oder negativ sein, aber müssen ganze Zahlen zwischen -9 223 372 036 854 775 808 (-2^63) und 9 223 372 036 854 775 807 (2^63-1) sein.|  
|Decimal Number|Eine reelle 64-Bit-Zahl (acht Byte) <sup>1, 2</sup>|Reelle Zahlen sind Zahlen, die Dezimalstellen aufweisen können. Reelle Zahlen decken viele Werte ab:<br /><br /> Negative Werte von -1,79E +308 bis -2,23E -308<br /><br /> Zero<br /><br /> Positive Werte von 2,23E -308 bis -1,79E +308<br /><br /> Die Anzahl der relevanten Stellen wird jedoch auf siebzehn Dezimalstellen beschränkt.|  
|Boolean|Boolean|Entweder ein True oder ein False-Wert.|  
|Text|String|Eine Unicodezeichen-Datenzeichenfolge. Dies können Zeichenfolgen, Zahlen oder Datumsangaben im Textformat sein.|  
|Date|Datum/Uhrzeit|Datumsangaben und Uhrzeiten in einer akzeptierten Form für die Darstellung von Datum und Uhrzeit.<br /><br /> Gültig sind alle Datumsangaben nach dem 1. März 1900.|  
|Währung|Währung|Der Währungsdatentyp lässt Werte zwischen -922 337 203 685 477,5808 und 922 337 203 685 477,5807 mit vier Dezimalstellen unveränderlicher Genauigkeit zu.|  
|–|Leer|Ein leerer Datentyp in DAX, der SQL-NULLEN darstellt und ersetzt. Sie können mit der BLANK-Funktion ein Leerzeichen erstellen und mit der logischen ISBLANK-Funktion nach Leerzeichen suchen.|  
  
 Tabellarische Modelle beinhalten auch den Table-Datentyp als Eingabe oder Ausgabe für viele DAX-Funktionen. Beispielsweise nimmt die FILTER-Funktion eine Tabelle als Eingabe an und gibt eine neue Tabelle aus, die nur die Zeilen enthält, die die Filterbedingungen erfüllen. Die Kombination von Tabellen- und Aggregationsfunktionen ermöglicht Ihnen die Ausführung komplexer Berechnungen für dynamisch definierte Datasets.  
  
 Obwohl Datentypen in der Regel automatisch festgelegt werden, ist es wichtig, ihre Funktion und Gültigkeit zu verstehen. Dies gilt insbesondere für DAX-Formeln. Fehler in Formeln oder unerwartete Ergebnisse werden z. B. oft von einem bestimmten Operator verursacht, der nicht mit einem in einem Argument angegebenen Datentyp verwendet werden kann. Die Formel `= 1 & 2`gibt z.B. ein Zeichenfolgenergebnis von 12 zurück, die Formel `= "1" + "2"`dagegen die ganze Zahl 3.  
  
 Ausführliche Informationen zu Datentypen in tabellarischen Modellen und expliziten und impliziten Konvertierungen von Datentypen in DAX finden Sie unter [Unterstützte Datentypen &#40;SSAS – tabellarisch&#41;](data-types-supported-ssas-tabular.md).  
  
##  <a name="dax-operators"></a><a name="bkmk_DAX_opertors"></a>DAX-Operatoren  
 In der DAX-Sprache werden vier verschiedene Berechnungsoperatortypen in Formeln verwendet:  
  
-   Vergleichsoperatoren, um Werte zu vergleichen und einen logischen TRUE\FALSE-Wert zurückzugeben  
  
-   Arithmetische Operatoren, um arithmetische Berechnungen auszuführen, die numerische Werte zurückgeben  
  
-   Textverkettungsoperatoren, die zwei oder mehr Textzeichenfolgen verknüpfen  
  
-   Logische Operatoren, die zwei oder mehr Ausdrücke kombinieren, um ein einzelnes Ergebnis zurückzugeben  
  
 Ausführliche Informationen zu den in DAX-Formeln verwendeten Operatoren finden Sie unter [DAX-Operator-Referenz für Power Pivot](/dax/dax-operator-reference).  
  
##  <a name="dax-formulas"></a><a name="bkmk_DAX_Formulas"></a>DAX-Formeln  
 DAX-Formeln sind für das Erstellen von Berechnungen in berechneten Spalten und Measures sowie das Schützen der Daten mit Zeilenebenenfiltern maßgeblich. Um Formeln für berechnete Spalten und Measures zu erstellen, verwenden Sie die Bearbeitungsleiste oben im Modell-Designer-Fenster. Um Formeln für Zeilenfilter zu erstellen, verwenden Sie das Dialogfeld Rollen-Manager. Die Informationen in diesem Abschnitt sollen Ihnen den Einstieg in die Grundlagen von DAX-Formeln erleichtern.  
  
###  <a name="formula-basics"></a><a name="basics"></a> Formelgrundlagen  
 Mit DAX können Entwickler von tabellarischen Modellen eigene Berechnungen in beiden Modelltabellen als Teil berechneter Spalten oder als Measures definieren, die Tabellen zugeordnet sind, in diesen aber nicht direkt erscheinen. DAX ermöglicht es Modellentwicklern auch, Daten zu schützen, indem sie Berechnungen erstellen, die einen booleschen Wert zurückgeben, der definiert, welche Zeilen in einer bestimmten oder einer verknüpften Tabelle von Mitgliedern der zugehörigen Rolle abgefragt werden können.  
  
 DAX-Formeln können sehr einfach oder sehr komplex sein. In der folgenden Tabelle werden einige Beispiele für einfache Formeln aufgeführt, die in einer berechneten Spalte verwendet werden können.  
  
|||  
|-|-|  
|Formel|BESCHREIBUNG|  
|`=TODAY()`|Fügt das aktuelle Datum in jede Zeile der Spalte ein.|  
|`=3`|Fügt den Wert 3 in jede Zeile der Spalte ein.|  
|`=[Column1] + [Column2]`|Fügt die Werte in der gleichen Zeile von [Column1] und [Column2] hinzu und fügt die Ergebnisse in die gleiche Zeile der berechneten Spalte ein.|  
  
 Unabhängig davon, ob die von Ihnen erstellte Formel einfach oder komplex ist, können Sie beim Erstellen einer Formel die folgenden Schritte befolgen:  
  
1.  Alle Formeln müssen mit einem Gleichheitszeichen beginnen.  
  
2.  Sie können einen Funktionsnamen eingeben oder auswählen oder einen Ausdruck eingeben.  
  
3.  Geben Sie die ersten Buchstaben der gewünschten Funktion oder des Namens ein. Mithilfe von AutoVervollständigen wird eine Liste der verfügbaren Funktionen, Tabellen und Spalten angezeigt. Drücken Sie TAB-TASTE, um ein Element aus der AutoVervollständigen-Liste zur Formel hinzuzufügen.  
  
     Sie können auch auf die Schaltfläche **Fx** klicken, um eine Liste der verfügbaren Funktionen anzuzeigen. Um in der Dropdownliste eine Funktion auszuwählen, markieren Sie diese mit den Pfeiltasten, und klicken Sie auf **OK** , um die Formel der Funktion hinzuzufügen.  
  
4.  Geben Sie die Argumente für die Funktion an, indem Sie sie aus einer Dropdownliste möglicher Tabellen und Spalten auswählen oder manuell eingeben.  
  
5.  Überprüfen Sie die Syntax auf Fehler: Stellen Sie sicher, dass alle Klammern geschlossen sind und dass alle Verweise auf Spalten, Tabellen und Werte gültig sind.  
  
6.  Drücken Sie die EINGABETASTE, um die Formel zu übernehmen.  
  
> [!NOTE]  
>  Eine berechnete Spalte wird mit Werten gefüllt, sobald die Formel akzeptiert und die Formel überprüft wurde. In einem Measure wird durch Drücken der EINGABETASTE die Measuredefinition im Measureraster mit der Tabelle gespeichert. Wenn eine Formel ungültig ist, wird ein Fehler angezeigt.  
  
 In diesem Beispiel untersuchen wir eine komplexere Formel in einem Measure mit dem Namen Days in Current Quarter:  
  
```  
Days in Current Quarter:=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))  
```  
  
 Dieses Measure wird zum Erstellen eines Vergleichsverhältnisses zwischen einem unvollständigen Zeitraum und dem vorherigen Zeitraum verwendet. In der Formel muss der Anteil des verstrichenen Zeitraums berücksichtigt und mit dem gleichen Anteil des vorherigen Zeitraums verglichen werden. In diesem Fall gibt [Days Current Quarter to Date]/[Days in Current Quarter] den verstrichenen Anteil des aktuellen Zeitraums zurück.  
  
 Diese Formel enthält die folgenden Elemente:  
  
|Formelelement|BESCHREIBUNG|  
|---------------------|-----------------|  
|`Days in Current Quarter:=`|Der Name des Measures.|  
|`=`|Das Gleichheitszeichen (=) kennzeichnet den Beginn der Formel.|  
|`COUNTROWS`|Die [Count-Funktion &#40;DAX&#41;](/dax/countrows-function-dax) die Anzahl der Zeilen in der Date-Tabelle zählt.|  
|`()`|Öffnende und schließende Klammern geben Argumente an.|  
|`DATESBETWEEN`|Die DATESBETWEEN-Funktion gibt die Daten zwischen dem letzten Datum für jeden Wert in der Date-Spalte in der Date-Tabelle zurück.|  
|`'Date'`|Gibt die Date-Tabelle an. Tabellen werden in einfachen Anführungszeichen angegeben.|  
|`[Date]`|Gibt die Date-Spalte in der Date-Tabelle an. Spalten werden in eckigen Klammern angegeben.|  
|`,`||  
|`STARTOFQUARTER`|Die STARTOFQUARTER-Funktion gibt das Datum des Quartalsanfangs zurück.|  
|`LASTDATE`|Die Funktion LASTDATE gibt den letzten Tag des Quartals zurück.|  
|`'Date'`|Gibt die Date-Tabelle an.|  
|`[Date]`|Gibt die Date-Spalte in der Date-Tabelle an.|  
|`,`||  
|`ENDOFQUARTER`|Die ENDOFQUARTER-Funktion.|  
|`'Date'`|Gibt die Date-Tabelle an.|  
|`[Date]`|Gibt die Date-Spalte in der Date-Tabelle an.|  
  
#### <a name="using-formula-autocomplete"></a>Verwenden von AutoVervollständigen für Formeln  
 Sowohl die Bearbeitungsleiste im Modell-Designer als auch das Formelfenster Zeilenfilter im Dialogfeld Rollen-Manager enthalten eine AutoVervollständigen-Funktion. AutoVervollständigen unterstützt Sie bei der Eingabe einer gültigen Formelsyntax, indem für jedes Element in der Formel Optionen angezeigt werden.  
  
-   Sie können AutoVervollständigen für Formeln auch mitten in einer vorhandenen Formel mit geschachtelten Funktionen verwenden. Ausgehend vom Text unmittelbar vor der Einfügemarke werden Werte in der Dropdownliste angezeigt. Der Text nach der Einfügemarke bleibt unverändert.  
  
-   AutoVervollständigen fügt keine schließende Klammer für Funktionen ein und gleicht Klammern nicht automatisch ab. Sie müssen sicherstellen, dass die Syntax aller Funktionen fehlerfrei ist. Andernfalls können Sie die Formel nicht speichern bzw. verwenden.  
  
#### <a name="using-multiple-functions-in-a-formula"></a>Verwenden mehrerer Funktionen in einer Formel  
 Sie können Funktionen schachteln, d. h. das Ergebnis einer Funktion als Argument in einer anderen Funktion verwenden. Berechnete Spalten unterstützen bis zu 64 Schachtelungsebenen. Die Schachtelung kann jedoch die Formelerstellung und die Problembehandlung erschweren.  
  
 Viele Funktionen wurden zur ausschließlichen Verwendung als geschachtelte Funktionen entwickelt. Diese Funktionen geben eine Tabelle zurück, die nicht direkt als Ergebnis gespeichert werden kann, sondern als Eingabe für eine Tabellenfunktion verwendet werden muss. Die Funktionen SUMX, AVERAGEX und MINX erfordern beispielsweise alle eine Tabelle als erstes Argument.  
  
> [!NOTE]  
>  Für die Schachtelung von Funktionen innerhalb von Measures gelten einige Einschränkungen, um sicherzustellen, dass die Leistung durch die vielen Berechnungen, die die Abhängigkeiten zwischen Spalten erforderlich machen, nicht beeinträchtigt wird.  
  
##  <a name="dax-functions"></a><a name="bkmk_DAX_functions"></a> DAX-Funktionen  
 In diesem Abschnitt finden Sie eine Übersicht über die von DAX unterstützten *Funktionstypen* . Weitere Informationen finden Sie in der [DAX-Funktionsreferenz](/dax/dax-function-reference).  
  
 DAX stellt eine Vielzahl von Funktionen bereit, mit denen Sie Berechnungen mit Datumsangaben und Uhrzeiten durchführen, bedingte Werte erstellen, mit Zeichenfolgen arbeiten, Suchen auf Grundlage von Beziehungen ausführen und eine Tabelle zum Durchführen rekursiver Berechnungen durchlaufen können. Wenn Sie mit Excel-Formeln vertraut sind, werden Sie feststellen, dass viele dieser Funktionen ähnlich erscheinen. DAX-Formeln unterscheiden sich jedoch in den folgenden wichtigen Punkten:  
  
-   Eine DAX-Funktion verweist immer auf eine vollständige Spalte oder eine Tabelle. Wenn Sie nur bestimmte Werte aus einer Tabelle oder Spalte verwenden möchten, können Sie der Formel Filter hinzufügen.  
  
-   Zum Anpassen von Berechnungen auf Zeilenbasis stellt DAX Funktionen bereit, mit denen Sie, ähnlich einem Parameter, den aktuellen Zeilenwert oder einen verknüpften Wert angeben können, um Berechnungen durchzuführen, die sich je nach Kontext unterscheiden. Informationen zur Arbeitsweise dieser Funktionen finden Sie unter „Kontext in DAX-Formeln“ weiter unten.  
  
-   DAX beinhaltet viele Funktionen, die keinen Wert, sondern eine Tabelle zurückgeben. In einem Berichtserstellungsclient wird diese Tabelle nicht angezeigt, sondern als Eingabe für andere Funktionen verwendet. Sie können z. B. eine Tabelle abrufen und dann die unterschiedlichen Werte darin zählen oder dynamische Summen von gefilterten Tabellen oder Spalten berechnen.  
  
-   Zu den DAX-Funktionen zählen auch verschiedene *Zeitintelligenzfunktionen* . Mit diesen Funktionen können Sie Datumsbereiche definieren oder auswählen und dynamische Berechnungen auf Grundlage dieser Datumsangaben oder Bereiche durchführen. Sie können z. B. Summen über parallele Zeiträume vergleichen.  
  
### <a name="date-and-time-functions"></a>Datums- und Uhrzeitfunktionen  
 Die Datums- und Uhrzeitfunktionen in DAX funktionieren ebenfalls ähnlich wie in Microsoft Excel. DAX-Funktionen basieren jedoch auf den von Microsoft SQL Server verwendeten `datetime`-Datentypen. Weitere Informationen finden Sie unter [Datums-und Uhrzeit Funktionen &#40;DAX-&#41;](/dax/date-and-time-functions-dax).  
  
### <a name="filter-functions"></a>Filterfunktionen  
 Mit den Filterfunktionen in DAX können Sie bestimmte Datentypen abrufen, Werte in verknüpften Tabellen suchen und nach verknüpften Werten filtern. Die Suchfunktionen funktionieren mit Tabellen und Beziehungen wie bei einer Datenbank. Die Filterfunktionen ermöglichen die Anpassung des Datenkontexts zur Erstellung dynamischer Berechnungen. Weitere Informationen finden Sie unter [Filter Functions &#40;DAX&#41;](/dax/filter-functions-dax).  
  
### <a name="information-functions"></a>Informationsfunktionen  
 Eine Informationsfunktion prüft die als Argument bereitgestellte Zelle oder Zeile und gibt an, ob der Wert mit dem erwarteten Typ übereinstimmt. Die ISTFEHLER-Funktion gibt z. B. TRUE zurück, wenn der Wert, auf den Sie verweisen, fehlerhaft ist. Weitere Informationen finden Sie unter [Information Functions &#40;DAX&#41;](/dax/information-functions-dax).  
  
### <a name="logical-functions"></a>Logische Funktionen  
 Logische Funktionen werden auf Ausdrücke angewendet, um Informationen zu den Werten in diesem Ausdruck zurückzugeben. Mit der Funktion TRUE können Sie beispielsweise erkennen, ob ein von Ihnen ausgewerteter Ausdruck einen TRUE-Wert zurückgibt. Weitere Informationen finden Sie unter [logische Funktionen &#40;DAX-&#41;](/dax/logical-functions-dax).  
  
### <a name="mathematical-and-trigonometric-functions"></a>Mathematische und trigonometrische Funktionen  
 Die mathematischen Funktionen in DAX sind den mathematischen und trigonometrischen Funktionen in Excel sehr ähnlich. Die von den DAX-Funktionen verwendeten numerischen Datentypen weisen einige kleinere Unterschiede auf. Weitere Informationen finden Sie unter [Math and trg Functions &#40;DAX&#41;](/dax/math-and-trig-functions-dax).  
  
### <a name="statistical-functions"></a>Statistische Funktionen  
 DAX stellt statistische Funktionen bereit, die Aggregationen ausführen. Zusätzlich zum Erstellen von Summen und Durchschnittswerten oder dem Ermitteln von Mindest- und Höchstwerten können in DAX Spalten vor dem Aggregieren gefiltert und Aggregationen auf Grundlage verknüpfter Tabellen erstellt werden. Weitere Informationen finden Sie unter [statistische Funktionen &#40;DAX-&#41;](/dax/statistical-functions-dax).  
  
### <a name="text-functions"></a>Textfunktionen  
 Die DAX-Textfunktionen sind den entsprechenden Funktionen in Excel sehr ähnlich. Sie können einen Teil einer Zeichenfolge zurückgeben, innerhalb einer Zeichenfolge nach Text suchen oder Zeichenfolgenwerte verketten. DAX stellt auch Funktionen zum Steuern der Formate für Datums- und Uhrzeitangaben sowie Zahlen bereit. Weitere Informationen finden Sie unter [Text Functions &#40;DAX&#41;](/dax/text-functions-dax).  
  
### <a name="time-intelligence-functions"></a>Zeitintelligenzfunktionen  
 Mit den in DAX bereitgestellten Zeitintelligenzfunktionen können Sie Berechnungen erstellen, die integriertes Wissen zu Kalendern und Datumsangaben verwenden. Wenn Sie Zeit- und Datumsbereiche in Kombination mit Aggregationen oder Berechnungen verwenden, können Sie sinnvolle Vergleiche in vergleichbaren Zeiträumen für Verkäufe, Bestand usw. erstellen. Weitere Informationen finden Sie unter [Zeit Intelligenz Funktionen &#40;DAX-&#41;](/dax/time-intelligence-functions-dax).  
  
###  <a name="table-valued-functions"></a><a name="bkmk_TableFunc"></a>Tabellenwert Funktionen  
 Es gibt DAX-Funktionen, die Tabellen ausgeben und/oder Tabellen als Eingabe akzeptieren. Da eine Tabelle eine einzelne Spalte enthalten kann, erfordern Tabellenwertfunktionen auch einzelne Spalten als Eingaben. Es ist wichtig zu wissen, wie diese Tabellenwertfunktionen verwendet werden, um DAX-Formeln vollständig nutzen zu können. DAX enthält die folgenden Typen von Tabellenwertfunktionen:  
  
 **Filterfunktionen** geben eine Spalte, eine Tabelle oder Werte zurück, die sich auf die aktuelle Zeile beziehen.  
  
 **Aggregationsfunktionen** aggregieren einen Ausdruck über die Zeilen einer Tabelle.  
  
 **Zeitintelligenzfunktionen** geben eine Tabelle von Datumsangaben zurück oder verwenden eine Tabelle von Daten, um eine Aggregation zu berechnen.  
  
##  <a name="context-in-dax-formulas"></a><a name="bkmk_context"></a> Kontext in DAX-Formeln  
 Beim Erstellen von Formeln mit DAX ist der*Kontext* ein wichtiges Konzept. Mithilfe des Kontexts können Sie dynamische Analysen ausführen, da sich die Ergebnisse einer Formel ändern und die aktuelle Zeilen- oder Zellenauswahl sowie alle verknüpften Daten widerspiegeln. Es ist sehr wichtig, dass Sie den Kontext verstehen und anwenden, um leistungsstarke, dynamische Analysen erstellen und Probleme in Formeln beheben zu können.  
  
 Formeln in tabellarischen Modellen können abhängig von anderen Entwurfselementen in einem anderen Kontext ausgewertet werden:  
  
-   Filter, die auf eine PivotTable oder einen Bericht angewendet werden  
  
-   Innerhalb einer Formel definierte Filter  
  
-   Mit besonderen Funktionen innerhalb einer Formel angegebene Beziehungen  
  
 Es gibt verschiedene Typen von Kontext: *Zeilenkontext*, *Abfragekontext*und *Filterkontext*.  
  
###  <a name="row-context"></a><a name="bkmk_row_context"></a>Zeilen Kontext  
 Der *Zeilen Kontext* kann sich als "die aktuelle Zeile" vorstellen. Wenn Sie in einer berechneten Spalte eine Formel erstellen, enthält der Zeilenkontext für diese Formel die Werte aller Spalten in der aktuellen Zeile. Wenn die Tabelle mit einer anderen Tabelle verknüpft ist, enthält der Kontext auch alle Werte aus der anderen Tabelle, die mit der aktuellen Zeile verknüpft sind.  
  
 Angenommen, Sie erstellen die berechnete Spalte `=[Freight] + [Tax]`, die Werte aus zwei Spalten (Fracht und Steuer) aus derselben Tabelle addiert. Diese Formel ruft automatisch nur die Werte der aktuellen Zeile in der angegebenen Spalte ab.  
  
 Der Zeilenkontext folgt auch allen Beziehungen, die zwischen Tabellen definiert wurden, einschließlich der innerhalb einer berechneten Spalte mit DAX-Formeln definierten Beziehungen, um zu ermitteln, welche Zeilen in verknüpften Tabellen der aktuellen Zeile zugeordnet sind.  
  
 In der folgenden Formel wird z. B. mit der RELATED-Funktion auf Grundlage des Lands, in das die Bestellung ausgeliefert wurde, ein Steuerwert aus einer verknüpften Tabelle abgerufen. Der Steuerwert wird mit dem Wert für Region in der aktuellen Tabelle ermittelt. Die Region wird in der verknüpften Tabelle nachgeschlagen, und anschließend wird der Steuersatz für diese Region aus der verknüpften Tabelle abgerufen.  
  
```  
= [Freight] + RELATED('Region'[TaxRate])  
```  
  
 Diese Formel ruft den Steuersatz für den aktuellen Bereich von der Tabelle Region ab und fügt es dem Wert der Spalte Fracht hinzu. In DAX-Formeln müssen Sie die bestimmte Beziehung zum Verknüpfen der Tabellen nicht kennen oder angeben.  
  
#### <a name="multiple-row-context"></a>Mehrere Zeilenkontexte  
 DAX umfasst Funktionen, die eine Tabelle durchlaufen, um Berechnungen durchzuführen. Diese Funktionen können über mehrere aktuelle Zeilen mit jeweils einem eigenen Zeilenkontext verfügen.  In Wesentlichen können Sie mit diesen Funktionen Formeln erstellen, die Vorgänge rekursiv über eine innere und eine äußere Schleife ausführen.  
  
 Angenommen, das Modell enthält eine **Products** -Tabelle und eine **Sales** -Tabelle. Sie können z. B. die gesamte Sales-Tabelle durchlaufen, die mit Transaktionen verschiedener Produkte gefüllt ist, um die größte Bestellmenge für jedes Produkt in einer beliebigen Transaktion zu ermitteln.  
  
 Mit DAX können Sie eine einzelne Formel erstellen, die den richtigen Wert zurückgibt, und die Ergebnisse werden automatisch bei jedem Hinzufügen von Daten zu den Tabellen aktualisiert.  
  
```  
=MAXX(FILTER(Sales,[ProdKey]=EARLIER([ProdKey])),Sales[OrderQty])  
```  
  
 Eine ausführliche Exemplarische Vorgehensweise für diese Formel finden Sie unter der [früheren Funktion](/dax/earlier-function-dax).  
  
 Zusammengefasst speichert die EARLIER-Funktion den Zeilenkontext des Vorgangs, der dem aktuellen Vorgang vorausging. Die Funktion speichert zu jedem Zeitpunkt zwei Kontextsätze im Arbeitsspeicher: Ein Kontextsatz stellt die aktuelle Zeile für die innere Schleife der Formel dar, und ein weiterer Kontextsatz stellt die aktuelle Zeile für die äußere Schleife der Formel dar. DAX übermittelt automatisch Werte zwischen den zwei Schleifen, sodass komplexe Aggregate erstellt werden können.  
  
####  <a name="query-context"></a><a name="bkmk_query_context"></a>Abfrage Kontext  
 Der*Abfragekontext* ist die Teilmenge von Daten, die implizit für eine Formel abgerufen wird. Wenn ein Benutzer ein Measure oder ein anderes Wertfeld in einer PivotTable oder einem Bericht platziert, die bzw. der auf einem tabellarischen Modell basiert, untersucht die Engine die Zeilen- und Spaltenüberschriften, die Slicer und die Berichtsfilter, um den Kontext zu ermitteln. Anschließend werden die erforderlichen Abfragen für die Datenquelle ausgeführt, um die richtige Teilmenge der Daten abzurufen, die von der Formel definierten Berechnungen auszuführen und dann jede Zelle in der PivotTable oder dem Bericht aufzufüllen. Der Datensatz, der abgerufen wird, ist der Abfragekontext für jede Zelle.  
  
> [!WARNING]  
>  In einem Modell, das den DirectQuery-Modus verwendet, wird der Kontext ausgewertet, und anschließend werden die Set-Vorgänge, mit denen die richtige Teilmenge der Daten abgerufen und die Ergebnisse berechnet werden, in SQL-Anweisungen übersetzt. Diese Anweisungen werden dann direkt auf dem relationalen Datenspeicher ausgeführt. Daher ändert sich der Kontext selbst nicht, obwohl die Methode zum Abrufen der Daten und Berechnen der Ergebnisse anders ist.  
  
 Da sich der Kontext abhängig davon ändert, wo Sie die Formel platzieren, können sich auch die Ergebnisse der Formel ändern.  
  
 Angenommen, Sie erstellen eine Formel, die die Werte in der Spalte **Profit** der **Sales** -Tabelle addiert: `=SUM('Sales'[Profit])`.  Wenn Sie diese Formel in einer berechneten Spalte innerhalb der **Sales** -Tabelle verwenden, sind die Ergebnisse der Formel für die gesamte Tabelle identisch, da der Abfragekontext für die Formel immer dem gesamten Dataset der **Sales** -Tabelle entspricht. Die Ergebnisse enthalten somit den Gewinn für alle Regionen, alle Produkte, alle Jahre usw.  
  
 In der Regel möchten Benutzer jedoch nicht Hunderte Male das gleiche Ergebnis anzeigen, sondern den Gewinn für ein bestimmtes Jahr, ein bestimmtes Land, ein bestimmtes Produkt oder eine Kombination daraus abrufen, um das Gesamtergebnis zu ermitteln.  
  
 In einer PivotTable kann der Kontext durch Hinzufügen oder Entfernen von Spalten- und Zeilenüberschriften oder Slicern geändert werden. Jedes Mal, wenn Benutzer der PivotTable Spalten- oder Zeilenüberschriften hinzufügen, wird der Abfragekontext geändert, in dem das Measure ausgewertet wird. Slice- und Filterungsvorgänge beeinflussen ebenfalls den Kontext. Daher wird dieselbe Formel, wenn sie in einem Measure verwendet wird, für jede Zelle in einem anderen *Abfragekontext* ausgewertet.  
  
####  <a name="filter-context"></a><a name="bkmk_filter_context"></a>Filter Kontext  
 Der*Filterkontext* ist der Satz von Werten, die in jeder Spalte oder in den aus einer verknüpften Tabelle abgerufenen Werten zulässig sind. Filter können im Designer oder in der Darstellungsschicht (Berichte und PivotTables) auf eine Spalte angewendet werden. Filter können auch explizit durch Filterausdrücke innerhalb der Formel definiert werden.  
  
 Der Filterkontext wird hinzugefügt, wenn Sie Filtereinschränkungen für den in einer Spalte oder einer Tabelle zulässigen Satz von Werten angeben, indem Sie in einer Formel Argumente verwenden. Der Filterkontext wird zusätzlich zu anderen Kontexten wie dem Zeilenkontext oder Abfragekontext angewendet.  
  
 In tabellarischen Modellen gibt es verschiedene Möglichkeiten, einen Filterkontext zu erstellen. Innerhalb des Kontexts von Clients, die das Modell verwenden, z.B. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte, können Benutzer Filter bei Bedarf erstellen, indem sie Slicer oder Berichtsfilter für Zeilen- und Spaltenüberschriften hinzufügen. Sie können Filterausdrücke auch direkt in der Formel verwenden, um verknüpfte Werte anzugeben, Tabellen zu filtern, die als Eingaben verwendet werden, oder dynamisch den Kontext für Werte abzurufen, die in Berechnungen verwendet werden. Darüber hinaus können Sie die Filter für einzelne Spalten vollständig oder selektiv löschen. Beim Erstellen von Formeln, die Gesamtergebnisse berechnen, ist dies sehr nützlich.  
  
 Weitere Informationen zum Erstellen von Filtern innerhalb von Formeln finden Sie in der [Filter-Funktion](/dax/filter-function-dax).  
  
 Ein Beispiel dafür, wie Filter gelöscht werden können, um Gesamtsummen zu erstellen, finden Sie unter [All-Funktion](/dax/all-function-dax).  
  
 Beispiele für das selektive löschen und Anwenden von Filtern innerhalb von Formeln finden Sie in der [ALLEXCEPT-Funktion](/dax/allexcept-function-dax).  
  
####  <a name="determining-context-in-formulas"></a><a name="bkmk_determine_context"></a> Bestimmen des Kontexts in Formeln  
 Wenn Sie eine DAX-Formel erstellen, wird die Formel zuerst auf gültige Syntax getestet, und dann wird überprüft, ob die Namen der Spalten und Tabellen innerhalb der Formel im aktuellen Kontext vorhanden sind. Wenn eine Spalte oder Tabelle innerhalb der Formel nicht gefunden wird, wird ein Fehler zurückgegeben.  
  
 Wie in den vorangehenden Abschnitten beschrieben, wird der Kontext während der Validierung (und während Neuberechnungen) anhand der verfügbaren Tabellen im Modell, anhand der Beziehungen zwischen den Tabellen und anhand der angewendeten Filter bestimmt.  
  
 Wenn Sie z.B. gerade einige Daten in eine neue Tabelle importiert haben, die mit keiner anderen Tabelle verknüpft ist (und Sie keine Filter angewendet haben), ist der *aktuelle Kontext* der gesamte Satz von Spalten in der Tabelle. Wenn die Tabelle über Beziehungen mit anderen Tabellen verknüpft ist, beinhaltet der aktuelle Kontext auch die verknüpften Tabellen. Wenn Sie eine Spalte aus der Tabelle einem Bericht hinzufügen, der Slicer und ggf. auch Berichtsfilter verwendet, ist der Kontext für die Formel die Teilmenge der Daten in jeder Zelle des Berichts.  
  
 Der Kontext ist ein leistungsstarkes Konzept, das die Fehlerbehebung in Formeln allerdings auch erschweren kann. Sie sollten daher mit einfachen Formeln und Beziehungen beginnen, um die Funktionsweise des Kontexts zu verstehen. Der folgende Abschnitt enthält einige Beispiele für Formeln, in denen verschiedene Kontexttypen zur dynamischen Rückgabe von Ergebnissen verwendet werden.  
  
##### <a name="examples-of-context-in-formulas"></a>Beispiele für Kontext in Formeln  
  
1.  Die Funktion der [zugehörigen Funktion](/dax/related-function-dax) erweitert den Kontext der aktuellen Zeile, um Werte in einer verknüpften Spalte einzuschließen. Auf diese Weise können Sie Suchvorgänge ausführen. Das Beispiel in diesem Thema veranschaulicht die Interaktion des Filter- und Zeilenkontexts.  
  
2.  Mithilfe der Funktion " [Filter Funktion](/dax/filter-function-dax) " können Sie die Zeilen angeben, die im aktuellen Kontext eingeschlossen werden sollen. Zudem wird anhand der Beispiele in diesem Thema veranschaulicht, wie Filter in andere Funktionen, die Aggregate ausführen, eingebettet werden.  
  
3.  Die [all-Funktions](/dax/all-function-dax) Funktion legt den Kontext in einer Formel fest. Sie können Filter, die als Ergebnis des Abfragekontexts angewendet werden, mithilfe der ALL-Funktion überschreiben.  
  
4.  Mit der [ALLEXCEPT-Funktion](/dax/allexcept-function-dax) können Sie alle Filter entfernen, mit Ausnahme von einer, die Sie angeben. Beide Themen enthalten Beispiele, die Sie durch das Erstellen von Formeln führen, um komplexe Kontexte besser verstehen zu können.  
  
5.  Mit der [früheren Funktion](/dax/earlier-function-dax) und den [frühesten Funktions](/dax/earliest-function-dax) Funktionen können Sie Tabellen durchlaufen, indem Sie Berechnungen durchführen, während Sie auf einen Wert aus einer inneren Schleife verweisen. Wenn Sie mit dem Konzept der Rekursion und inneren und äußeren Schleifen vertraut sind, werden Sie die Leistungsfähigkeit zu schätzen wissen, die die Funktionen EARLIER und EARLIEST bereitstellen. Wenn Sie mit diesen Konzepten nicht vertraut sind, sollten Sie die Schritte in dem Beispiel sorgfältig durchführen, um den inneren und äußeren Kontext beim Durchführen von Berechnungen zu verstehen.  
  
##  <a name="formulas-and-the-tabular-model"></a><a name="bkmk_RelModel"></a>Formeln und das tabellarische Modell  
 Der Modell-Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ist ein Bereich, in dem Sie mit mehreren Datentabellen arbeiten und die Tabellen in einem tabellarischen Modell verbinden können. Innerhalb dieses Modells werden Tabellen über Beziehungen zwischen Spalten mit gemeinsamen Werten (Schlüsseln) verknüpft. Im tabellarischen Modell können Sie Werte mit Spalten in anderen Tabellen verknüpfen und weitere interessante Berechnungen erstellen. Ebenso wie in einer relationalen Datenbank können Sie mehrere Ebenen verknüpfter Tabellen miteinander verbinden und Spalten aus allen Tabellen in den Ergebnissen verwenden.  
  
 Sie können z. B. eine Verkaufstabelle, eine Produkttabelle und eine Tabelle mit Produktkategorien verknüpfen und verschiedene Kombinationen der Spalten in PivotTables und Berichten verwenden. Verwandte Felder können verwendet werden, um verbundene Tabellen zu filtern oder Berechnungen über Teilmengen zu erstellen. (Wenn Sie mit relationalen Datenbanken und dem Arbeiten mit Tabellen und Joins nicht vertraut sind, finden Sie weitere Informationen unter [Beziehungen &#40;SSAS – tabellarisch&#41;](relationships-ssas-tabular.md).)  
  
 Tabellarische Modelle unterstützen mehrere Beziehungen zwischen Tabellen. Um Verwirrungen oder falsche Ergebnisse zu vermeiden, wird jeweils nur eine Beziehung als aktive Beziehung festgelegt, Sie können jedoch die aktive Beziehung nach Bedarf erstellen und ändern, um in Berechnungen unterschiedliche Verbindungen der Daten zu durchlaufen. Die [userelationship-Funktion &#40;DAX-&#41;](/dax/userelationship-function-dax) kann verwendet werden, um mindestens eine Beziehung anzugeben, die in einer bestimmten Berechnung verwendet werden soll.  
  
 In einem tabellarischen Modell sollten die folgenden Regeln für den Formelentwurf beachten werden:  
  
-   Wenn Tabellen durch eine Beziehung verbunden sind, muss sichergestellt werden, dass die beiden als Schlüssel verwendeten Spalten übereinstimmende Werte enthalten. Die referenzielle Integrität wird jedoch nicht erzwungen, daher kann auch bei nicht übereinstimmenden Werten in einer Schlüsselspalte eine Beziehung erstellt werden. In so einem Fall müssen Sie beachten, dass leere oder nicht übereinstimmende Werte die Ergebnisse von Formeln beeinflussen können.  
  
-   Wenn Sie Tabellen im Modell mithilfe von Beziehungen verknüpfen, vergrößern Sie den Bereich oder *Kontext*, in dem die Formeln ausgewertet werden. Änderungen im Kontext, die sich aus der Hinzufügung neuer Tabellen, neuen Beziehungen oder aus Änderungen in der aktiven Beziehung ergeben, können zu unerwarteten Änderungen in den Ergebnissen führen. Weitere Informationen finden Sie weiter oben in diesem Thema unter [Kontext in DAX-Formeln](#bkmk_context) .  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_tables"></a>Arbeiten mit Tabellen und Spalten  
 Tabellen in tabellarischen Modellen sind rein äußerlich mit Excel-Tabellen vergleichbar, allerdings werden Daten und Formeln von ihnen anders verarbeitet:  
  
-   Formeln funktionieren nur für Tabellen und Spalten, nicht für einzelne Zellen, Bereichsverweise oder Arrays.  
  
-   Formeln können Beziehungen verwenden, um Werte aus verknüpften Tabellen abzurufen. Die Werte, die abgerufen werden, beziehen sich immer auf den aktuellen Zeilenwert.  
  
-   Sie können keine unregelmäßigen Daten verwenden, so wie dies in einem Excel-Arbeitsblatt möglich ist. Jede Zeile in einer Tabelle muss die gleiche Anzahl von Spalten enthalten. In einigen Spalten können jedoch leere Werte stehen. Excel-Datentabellen und Datentabellen aus tabellarischen Modellen sind nicht austauschbar.  
  
-   Da der Datentyp für jede Spalte festgelegt ist, muss jeder Wert in dieser Spalte vom gleichen Typ sein,  
  
### <a name="referring-to-tables-and-columns-in-formulas"></a>Verweisen auf Tabellen und Spalten in Formeln  
 Sie können auf alle Tabellen und Spalten anhand des Namens verweisen. Die folgende Formel veranschaulicht z.B., wie Sie auf die Spalten aus zwei Tabellen verweisen, indem Sie den *vollqualifizierten* Namen verwenden:  
  
```  
=SUM('New Sales'[Amount]) + SUM('Past Sales'[Amount])  
```  
  
 Wenn eine Formel ausgewertet wird, überprüft der Modell-Designer zuerst die allgemeine Syntax und vergleicht dann die von Ihnen bereitgestellten Namen der Spalten und Tabellen mit möglichen Spalten und Tabellen im aktuellen Kontext. Wenn der Name mehrdeutig ist oder die Spalte oder die Tabelle nicht gefunden werden kann, wird für die Formel (statt eines Datenwerts wird in Zellen, in denen der Fehler auftritt, eine #ERROR-Zeichenfolge angezeigt) ein Fehler ausgegeben. Weitere Informationen zu den Benennungs Anforderungen für Tabellen, Spalten und andere Objekte finden Sie unter "Benennungs Anforderungen" in der [DAX-Syntax Spezifikation für Power Pivot](/dax/dax-syntax-reference).  
  
### <a name="table-relationships"></a>Tabellenbeziehungen  
 Das Erstellen von Beziehungen zwischen Tabellen bietet die Möglichkeit, in einer anderen Tabelle nach Daten zu suchen und verknüpfte Werte zu verwenden, um komplexe Berechnungen vorzunehmen. Sie können z. B. eine berechnete Spalte verwenden, um alle Versanddatensätze für den aktuellen Wiederverkäufer nachzuschlagen und anschließend die jeweiligen Versandkosten zu addieren. In vielen Fällen ist eine Beziehung u. U. nicht notwendig. Sie können die LOOKUPVALUE-Funktion in einer Formel verwenden, um den Wert in *result_columnName* für die Zeile zurückzugeben, die die im *search_column* -Parameter und im *search_value* -Parameter angegebenen Kriterien erfüllt.  
  
 Viele DAX-Funktionen erfordern, dass zwischen zwei Tabellen oder unter mehreren Tabellen eine Beziehung besteht, um die referenzierten Spalten zu finden und sinnvolle Ergebnisse zurückzugeben. Andere Funktionen versuchen, die Beziehung zu ermitteln. Um jedoch die besten Ergebnisse zu erzielen, sollten Sie nach Möglichkeit immer eine Beziehung erstellen. Weitere Informationen finden Sie unter [Formeln und das tabellarische Modell](#bkmk_RelModel) weiter oben in diesem Thema.  
  
##  <a name="updating-the-results-of-formulas-process"></a><a name="bkmk_RefreshRecalc"></a> Aktualisieren der Ergebnisse von Formeln (Prozess)  
 *Datenverarbeitung* und *Neuberechnung* sind zwei separate, aber verwandte Vorgänge. Diese Konzepte sollten Ihnen sehr geläufig sein, wenn Sie ein Modell mit komplexen Formeln, großen Datenmengen oder aus externen Datenquellen abgerufenen Daten entwerfen.  
  
 *Datenverarbeitung* ist der Vorgang, bei dem die Daten in einem Modell mit neuen Daten aus einer externen Datenquelle aktualisiert werden.  
  
 *Neuberechnung* ist der Vorgang, bei dem die Ergebnisse von Formeln aktualisiert werden, um Änderungen an den Formeln sowie an den zugrunde liegenden Daten widerzuspiegeln. Neuberechnung kann die Leistung in folgender Weise beeinträchtigen:  
  
-   Die Werte in einer berechneten Spalte werden berechnet und im Modell gespeichert. Um die Werte in der berechneten Spalte zu aktualisieren, müssen Sie das Modell mit einem von drei Verarbeitungs Befehlen verarbeiten: vollständig verarbeiten, Daten verarbeiten oder Neuberechnung verarbeiten. Das Ergebnis der Formel muss immer für die ganze Spalte neu berechnet werden, wenn Sie die Formel ändern.  
  
-   Die von Measures berechneten Werte werden dynamisch ausgewertet, sobald ein Benutzer einer PivotTable das Measure hinzufügt oder einen Bericht öffnet. Wenn der Benutzer den Kontext ändert, ändern sich die von dem Measure zurückgegebenen Werte. Die Ergebnisse des Measures spiegeln immer den aktuellen Stand des speicherinternen Caches wider.  
  
 Die Verarbeitung und die Neuberechnung haben nur dann Auswirkungen auf Zeilenfilterformeln, wenn das Ergebnis einer Neuberechnung einen anderen Wert zurückgibt, durch den die Zeile für Rollenmitglieder abfragbar oder nicht abfragbar wird.  
  
 Weitere Informationen finden Sie unter [Verarbeiten von Daten &#40;SSAS – tabellarisch&#41;](../process-data-ssas-tabular.md).  
  
##  <a name="troubleshooting-errors-in-formulas"></a><a name="bkmk_troubleshoot"></a>Problembehandlung bei Fehlern in Formeln  
 Wenn Sie beim Definieren einer Formel einen Fehler erhalten, enthält die Formel eventuell entweder einen *Syntaxfehler*, einen *Semantikfehler*oder einen *Berechnungsfehler*.  
  
 Syntaxfehler sind am einfachsten zu beheben. Meist geht es um eine fehlende Klammer oder ein fehlendes Komma. Hilfe zur Syntax der einzelnen Funktionen finden Sie in der [DAX-Funktionsreferenz](/dax/dax-function-reference).  
  
 Der andere Fehlertyp tritt auf, wenn die Syntax keinen Fehler aufweist, aber der Wert oder die Spalte, auf den bzw. die verwiesen wird, im Kontext der Formel keinen Sinn ergibt. Semantik- und Berechnungsfehler dieser Art können die folgenden Ursachen haben:  
  
-   Die Formel verweist auf eine nicht vorhandene Spalte, Tabelle oder Funktion.  
  
-   Die Formel scheint korrekt zu sein, aber wenn die Daten-Engine die Daten abruft, wird ein Typenkonflikt erkannt und ein Fehler ausgelöst.  
  
-   Die Formel übergibt eine falsche Zahl oder einen falschen Typ von Parametern an eine Funktion.  
  
-   Die Formel verweist auf eine andere Spalte mit einem Fehler, weshalb die Werte ungültig sind.  
  
-   Die Formel verweist auf eine Spalte, die nicht verarbeitet wurde, d. h., es sind Metadaten vorhanden, aber keine tatsächlichen Daten, die für Berechnungen verwendet werden könnten.  
  
 In den ersten vier Fällen kennzeichnet DAX die gesamte Spalte mit der ungültigen Formel. Im letzten Fall blendet DAX die Spalte ab, um anzugeben, dass sich die Spalte in einem nicht verarbeiteten Zustand befindet.  
  
##  <a name="additional-resources"></a><a name="bkmk_addional_resources"></a> Zusätzliche Ressourcen  
 [Tabellenmodellierung &#40;Adventure Works-Tutorial&#41;](../tabular-modeling-adventure-works-tutorial.md) stellt Schritt-für-Schritt-Anleitungen zum Erstellen eines tabellarischen Modells bereit, das viele Berechnungen in berechneten Spalten, Measures und Zeilenfiltern enthält. Für die meisten Formeln ist eine Beschreibung ihrer Funktion verfügbar.  
  
 Der [Analysis Services-und Power Pivot-Teamblog](https://go.microsoft.com/fwlink/?LinkID=220949&clcid=0x409) enthält Informationen, Tipps, Neuigkeiten und Ankündigungen zu [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] und Power Pivot.  
  
 Im [DAX-Ressourcencenter](https://go.microsoft.com/fwlink/?LinkID=220966&clcid=0x409) finden Sie sowohl interne als auch externe Informationen zu DAX, z.B. zahlreiche DAX-Lösungen von führenden Business Intelligence-Experten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Analysis Expressions &#40;DAX-&#41; Referenz](/dax/data-analysis-expressions-dax-reference)   
 [Measures &#40;tabellarischen SSAS-&#41;](measures-ssas-tabular.md)   
 [Berechnete Spalten &#40;tabellarischen SSAS-&#41;](ssas-calculated-columns.md)   
 [Rollen &#40;tabellarischen SSAS-&#41;](roles-ssas-tabular.md)   
 [KPIs &#40;tabellarischen SSAS-&#41;](kpis-ssas-tabular.md)   
 [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](data-sources-supported-ssas-tabular.md)  
  
  
