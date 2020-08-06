---
title: Exportieren als CSV-Datei (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 635d5904acf6e616378f5423bfbaf4cf5390fa9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608363"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a>Exportieren als CSV-Datei (Berichts-Generator und SSRS)
  Die durch Trennzeichen getrennte CSV (Comma-Separated Value)-Renderingerweiterung rendert Berichte als vereinfachte Darstellung der Daten eines Berichts in einem standardisierten Nur-Text-Format, das leicht lesbar und mit anderen Anwendungen austauschbar ist.  
  
 Dabei werden Felder und Zeilen durch ein Trennzeichen getrennt, für das auch ein anderes Zeichen als ein Komma gewählt werden kann. Die erstellte Datei kann in einem Tabellenkalkulationsprogramm wie [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] geöffnet oder als Importformat für andere Programme verwendet werden. Der exportierte Bericht wird zu einer CSV-Datei umgewandelt und gibt den MIME-Typ `text/csv` zurück.  
  
 Wenn Sie in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]mit Daten für Diagramme, Datenbalken, Sparklines, Messgeräte oder Indikatoren arbeiten möchten, exportieren Sie den Bericht in eine CSV-Datei, und öffnen Sie diese anschließend in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a>CSV-Rendering  
 Ein CSV-Bericht, der mit den Standardeinstellungen gerendert wurde, besitzt folgende Merkmale:  
  
-   Das standardmäßige Feldtrennzeichen ist ein Komma (,).  
  
    > [!NOTE]  
    >  Sie können das Feldtrennzeichen in ein beliebiges Zeichen (einschließlich TAB) ändern, indem Sie die Geräteinformationseinstellungen ändern. Weitere Informationen finden Sie unter [CSV Device Information Settings](../csv-device-information-settings.md).  
  
-   Die Daten Satz Trennzeichen-Zeichenfolge ist das Wagen Rücklauf-und Zeilenvorschub Zeichen ( \<cr> \<lf> ).  
  
-   Als Textqualifizierer-Zeichenfolge dient das Anführungszeichen (").  
  
     Der CSV-Renderer fügt keine Qualifizierer um alle Textzeichenfolgen hinzu. Textqualifizierer werden nur hinzugefügt, wenn der Wert das Trennzeichen oder einen Zeilenumbruch enthält.  
  
-   Falls der Text eine eingebettete Trennzeichenfolge oder Qualifiziererzeichenfolge enthält, wird der Text in den Textqualifizierer eingeschlossen, und die eingebetteten Qualifiziererzeichenfolgen werden verdoppelt.  
  
-   Formatierung und Layout werden ignoriert.  
  
 Die folgenden Elemente werden beim Rendern ignoriert:  
  
-   Seitenkopf  
  
-   Seitenfuß  
  
-   Benutzerdefinierte Berichtselemente  
  
-   Linie  
  
-   Image  
  
-   Rechteck  
  
-   Automatische Teilergebnisse  
  
 Die verbleibenden Berichtselemente werden von oben nach unten und dann von links nach rechts sortiert. Anschließend wird jedes Element in eine Spalte gerendert. Enthält der Bericht geschachtelte Datenelemente, wie Listen oder Tabellen, werden die übergeordneten Elemente in jedem Datensatz wiederholt.  
  
 In der folgenden Tabelle wird die Darstellung von Berichtselementen beim Rendern angegeben:  
  
|Element|Renderingverhalten|  
|----------|------------------------|  
|Textfeld|Der Inhalt des Textfelds wird gerendert. Im Standardmodus werden Elemente auf Grundlage der Formatierungseigenschaften des Elements formatiert. Im kompatiblen Modus kann die Formatierung durch die Geräteinformationseinstellungen geändert werden. Weitere Informationen zu den CSV-Renderingmodi finden Sie weiter unten.|  
|Tabelle|Das Rendering erfolgt durch Erweitern der Tabelle und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf. Drillthroughberichte werden nicht unterstützt.|  
|Matrix|Das Rendering erfolgt durch Erweitern der Matrix und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf.|  
|List|Für jede Detailzeile oder Instanz in der Liste wird ein Datensatz gerendert.|  
|Unterbericht|Das übergeordnete Element wird für jede Instanz des Inhalts wiederholt.|  
|Diagramm|Wird gerendert, indem eine Zeile für jeden Diagrammwert und jede Elementbezeichnung erstellt wird. Bezeichnungen aus Reihen und Kategorien in Hierarchien werden vereinfacht und in die Zeile für einen Diagrammwert eingeschlossen.|  
|Datenbalken|Wird wie ein Diagramm gerendert. Ein Datenbalken enthält normalerweise keine Hierarchien oder Bezeichnungen.|  
|Sparkline|Wird wie ein Diagramm gerendert. Eine Sparkline enthält üblicherweise keine Hierarchien oder Bezeichnungen.|  
|Maßstab|Wird als einzelner Datensatz mit dem Minimal- und Maximalwert der linearen Skala, dem Start- und Endwert des Bereichs und dem Wert des Zeigers gerendert.|  
|Indikator|Es wird als einzelnes Element mit dem Namen des aktiven Zustands, den verfügbaren Zuständen und dem Datenwert als Attribute gerendert.|  
|Karte|Rendert eine Zeile mit den Bezeichnungen und Werten der einzelnen Kartenelemente einer Kartenebene.<br /><br /> Wenn die Karte über mehrere Ebenen verfügt, variieren die Werte in den Zeilen abhängig davon, ob die Kartenebenen die gleichen oder unterschiedliche Kartendatenbereiche verwenden. Wenn mehrere Kartenebenen den gleichen Datenbereich verwenden, enthalten die Zeilen Daten aus allen Ebenen.|  
  
### <a name="hierarchical-and-grouped-data"></a>Hierarchische und gruppierte Daten  
 Hierarchische und gruppierte Daten müssen vereinfacht werden, um im CSV-Format dargestellt zu werden.  
  
 Die Renderingerweiterung vereinfacht den Bericht zu einer Baumstruktur, die die geschachtelten Gruppen innerhalb des Datenbereichs darstellt. So vereinfachen Sie den Bericht:  
  
-   Eine Zeilenhierarchie wird vor einer Spaltenhierarchie vereinfacht.  
  
-   Spalten werden wie folgt sortiert: Textfelder im Hauptteil von links nach rechts und von oben nach unten, gefolgt von Datenbereichen von links nach rechts und von oben nach unten.  
  
-   Innerhalb eines Datenbereichs werden die Spalten wie folgt sortiert: Eckelemente, Zeilenhierarchieelemente, Spaltenhierarchieelemente und Zellen  
  
-   Peerdatenbereiche sind Datenbereiche oder dynamische Gruppen, die einen allgemeinen Datenbereich oder einen dynamischen Vorgänger gemeinsam nutzen. Peerdaten werden durch Verzweigen der vereinfachten Struktur identifiziert.  
  
 Weitere Informationen finden Sie unter [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
 
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> Renderermodi  
 Für die CSV-Renderingerweiterung stehen zwei Modi zur Verfügung. Ein Modus ist für Excel, der andere für Anwendungen von Drittanbietern optimiert, die eine strikte CSV-Kompatibilität mit der CSV-Spezifikation in RFC 4180 erfordern. Je nach verwendetem Modus werden Peerdatenbereiche unterschiedlich behandelt.  
  
### <a name="default-mode"></a>Standardmodus  
 Der Standardmodus ist für Excel optimiert. Im Standardmodus wird der Bericht als CSV-Datei mit mehreren Abschnitten gerenderter CSV-Daten gerendert. Jeder Peerdatenbereich wird durch eine leere Zeile begrenzt. Peerdatenbereiche innerhalb des Berichthauptteils werden als separate Datenblocks innerhalb der CSV-Datei gerendert. Das Ergebnis ist eine CSV-Datei mit folgenden Merkmalen:  
  
-   Einzelne Textfelder innerhalb des Berichthauptteils werden einmal als erster Datenblock innerhalb der CSV-Datei gerendert.  
  
-   Jeder Peerdatenbereich der obersten Ebene im Hauptteil des Berichts wird in einem eigenen Datenblock gerendert.  
  
-   Geschachtelte Datenbereiche werden diagonal in den gleichen Datenblock gerendert.  
  
#### <a name="formatting"></a>Formatierung  
 Numerische Werte werden in ihrem formatierten Status gerendert. Excel kann formatierte numerische Werte, wie Währungen, Prozentwerte und Datumsangaben, erkennen und die Zellen beim Importieren einer CSV-Datei entsprechend formatieren.  
  
### <a name="compliant-mode"></a>Kompatibler Modus  
 Der kompatible Modus ist für Anwendungen von Drittanbietern optimiert.  
  
#### <a name="data-regions"></a>Datenbereiche  
 Nur die erste Textzeile in der Datei enthält die Spaltenkopfzeilen, und jede Zeile verfügt über dieselbe Spaltenanzahl.  
  
#### <a name="formatting"></a>Formatierung  
 Die Werte sind unformatiert.  
  
##  <a name="interactivity"></a><a name="Interactivity"></a>Interaktivität  
 Interaktivität wird von keinem der durch diesen Renderer generierten CSV-Formate unterstützt. Die folgenden interaktiven Elemente werden nicht gerendert:  
  
-   Hyperlinks  
  
-   Anzeigen oder ausblenden  
  
-   Dokumentstruktur  
  
-   Drillthrough oder Links mit Durchklicken  
  
-   Endbenutzersortierung  
  
-   Feste Berichtsköpfe  
  
-   Lesezeichen  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a>Geräte Informationseinstellungen  
 Sie kännen einige Standardeinstellungen für diesen Renderer ändern, beispielsweise den Modus für das Rendern, die Zeichen, die als Trennzeichen verwendet werden können, und die Zeichen, die als Textqualifizierer für die Standardzeichenfolge verwendet werden können. Ändern Sie dazu die Geräteinformationseinstellungen. Weitere Informationen finden Sie unter [CSV Device Information Settings](../csv-device-information-settings.md).  
  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhaltensweisen &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichts Elementen &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
