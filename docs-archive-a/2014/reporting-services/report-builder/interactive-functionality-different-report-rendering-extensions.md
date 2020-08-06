---
title: Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f0bd1c4c-e8b5-467f-b5a1-541f19c7e3e2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5778425fecdc941c10c2853cdcbb8f9798de752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615833"
---
# <a name="interactive-functionality-for-different-report-rendering-extensions-report-builder-and-ssrs"></a>Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen (Berichts-Generator und SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt interaktive Berichtsfunktionen bereit, die das Arbeiten mit einem Bericht zur Laufzeit ermöglichen. Nicht alle Berichtsrenderingformate unterstützen die interaktiven Funktionen in vollem Umfang. In der folgenden Tabelle ist die Funktionsweise der einzelnen interaktiven Funktionen in bestimmten Formaten beschrieben.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="interactive-features-in-different-output-formats"></a>Interaktive Funktionen in verschiedenen Ausgabeformaten  
 Berichte, die im XML-, CSV- oder IMAGE-Format gerendert werden, unterstützen keine interaktiven Funktionen.  
  
 Im Berichts-Manager, in SharePoint-Webparts oder in einem Browser angezeigte Berichte werden in HTML gerendert. HTML und Windows Forms sind die einzigen Berichtsausgabeformate, die alle interaktiven Funktionen vollständig unterstützen. Alternative HTML-Formate (wie MHTML) unterstützen viele interaktive Funktionen. Falls Ausnahmen für MHTML bestehen, wird in der folgenden Tabelle darauf hingewiesen.  
  
### <a name="document-maps"></a>Dokumentstrukturen  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Die interaktive Dokumentstruktur stellt einen Navigationsbereich mit hierarchischen Links bereit, mit denen zu verschiedenen Abschnitten des Berichts navigiert werden kann.|  
|PDF|PDF rendert eine Dokumentstruktur in Form des Lesezeichen-Bereichs. Alle Elemente in der Dokumentstruktur werden in dem Bereich von oben nach unten aufgelistet. Dies schließt eine Hierarchie aus Links ein. Wenn ein Seitenbereich angegeben wird, sind nur die Lesezeichen, die gerendert werden, in der Hierarchie vorhanden.|  
|Excel|Excel rendert in der Arbeitsmappe eine Dokumentstruktur als erstes Arbeitsblatt. Dies schließt eine Hierarchie aus Links ein. Beim Klicken auf den Link in der Dokumentstruktur wird die entsprechende Zielzelle im jeweiligen Arbeitsblatt geöffnet.|  
|Word|Word rendert die Dokumentstruktur als Inhaltsverzeichnisbezeichnungen.|  
|Andere (z. B., TIFF, XML und CSV)|Nicht verfügbar in MHTML, XML, CSV oder IMAGE.|  
  
### <a name="drillthrough-links-to-other-reports"></a>Drillthroughlinks zu anderen Berichten  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Datenwerte im Bericht, um verwandte Daten in einem anderen Bericht anzuzeigen.|  
|PDF|Drillthroughlinks sind in PDF nicht verfügbar. Für PDF-Berichte, die Links zu anderen Seiten enthalten, sollten Sie Links verwenden.|  
|Excel|Drillthroughlinks werden in Excel gerendert.<br /><br /> Der Link wird zu einem Link auf den Bericht, auf den der Drillthroughlink verweist. Beim Klicken auf den Link wird ein Bericht in einem Browserfenster geöffnet.|  
|Word|Drillthroughlinks werden in Word gerendert.<br /><br /> Der Link wird zu einem Link auf den Bericht, auf den der Drillthroughlink verweist. Beim Klicken auf den Link wird ein Bericht in einem Browserfenster geöffnet.|  
|Andere|Nicht verfügbar in XML, CSV oder IMAGE.|  
  
### <a name="toggle-items-within-a-report"></a>Elemente zum Ein-/Ausschalten in einem Bericht  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Symbole zum Erweitern und Reduzieren, um Abschnitte eines Berichts anzuzeigen.|  
|PDF|Der Berichtsserver exportiert den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
|Excel|Drilldownlinks und Elemente, die umgeschaltet werden können, werden in Excel als reduzierbare Konturen gerendert. Sie können Abschnitte des Berichts in Excel erweitern und reduzieren. Weitere Informationen zu Einschränkungen durch Excel finden Sie unter [Exportieren nach Microsoft Excel (Berichts-Generator und SSRS)](exporting-to-microsoft-excel-report-builder-and-ssrs.md).|  
|Word|Der Berichtsserver exportiert den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
|Andere|Nicht verfügbar in MHTML, XML oder CSV. Beim Exportieren in ein Bildformat exportiert der Berichtsserver den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
  
### <a name="interactive-sorting"></a>Interaktives Sortieren  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|In tabellarischen Berichten klicken Benutzer auf Sortierpfeile in Spalten, um die Sortierung der Daten zu ändern.|  
|PDF|Nicht verfügbar in PDF.|  
|Excel|Nicht verfügbar in Excel.|  
|Word|Nicht verfügbar in Word.|  
|Andere|Nicht verfügbar in MHTML, XML, CSV oder IMAGE.|  
  
### <a name="hyperlinks-to-external-web-content-or-images"></a>Links zu externen Webinhalten oder Bildern  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Links, um externe Webseiten in einem neuen Browserfenster zu öffnen.|  
|PDF|Links werden von der PDF-Renderingerweiterung gerendert. Wenn ein Benutzer auf einen Link klickt, werden die verknüpften Seiten im Browser geöffnet.|  
|Excel|Links werden in Excel gerendert.|  
|Word|Links werden in Word gerendert.|  
|Andere|Links sind in MHTML, XML, CSV oder IMAGE nicht verfügbar.<br /><br /> In MHTML und IMAGE werden externe Bilder als statisches Bild gerendert.|  
  
### <a name="bookmark-or-anchor"></a>Lesezeichen oder Anker  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Links, um zu einem anderen Abschnitt desselben Berichts zu navigieren.|  
|PDF|Nicht verfügbar in PDF.|  
|Excel|Lesezeichen werden in Excel gerendert.<br /><br /> Das Lesezeichen wird zu einem Link, der auf den Namen des Berichtselements verweist.|  
|Word|Lesezeichen werden in Word gerendert.<br /><br /> Das Lesezeichen wird zu einem Link, der auf das Lesezeichen des Berichtselements verweist. Es werden nur 40 Zeichen eines Lesezeichens oder Anchornamens beim Exportieren des Berichts konvertiert. Dies kann zu doppelten Lesezeichen oder Anchornamen führen. Leerzeichen werden in Unterstriche (_) konvertiert.|  
|Andere|Nicht verfügbar in XML, CSV oder IMAGE.|  
  
### <a name="prompted-parameters-obtained-at-run-time"></a>Angeforderte Parameter, die zur Laufzeit abgerufen wurden  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Oben im Bericht wird ein Parametereingabebereich angezeigt. Dieser Bereich ist Teil des HTML-Viewers, mit dem Berichte in einem Browser angezeigt werden.|  
|PDF|Der Berichtsserver exportiert den Bericht nach PDF mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Excel|Der Berichtsserver exportiert den Bericht nach Excel mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Word|Der Berichtsserver exportiert den Bericht nach Word mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Andere|Der Berichtsserver exportiert den Bericht in andere Formate mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
  
### <a name="filters-applied-at-run-time"></a>Filter, die zur Laufzeit angewendet wurden  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Die gefilterten Daten werden dem Benutzer zur Laufzeit angezeigt.|  
|PDF|Der Berichtsserver exportiert den Bericht nach PDF mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Excel|Der Berichtsserver exportiert den Bericht nach Excel mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Word|Der Berichtsserver exportiert den Bericht nach Word mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Andere|Der Berichtsserver exportiert den Bericht in andere Formate mithilfe der gefilterten Daten im aktuellen Bericht.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Interaktive Sortierung, Dokument Strukturen und Verknüpfungen &#40;Berichts-Generator und SSRS&#41;](../report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Matrizen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md)  
  
  
