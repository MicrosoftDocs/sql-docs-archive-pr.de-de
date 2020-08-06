---
title: Rendern von Daten (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a458fdf9-fb2a-4fee-9fbd-b38f36e91753
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc2757d308529c8b5a03e206a827fce7028edbfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721136"
---
# <a name="rendering-data-report-builder-and-ssrs"></a>Rendern von Daten (Berichts-Generator und SSRS)
  Bei Verwendung von Layoutrenderern, wie HTML, MHTML, Word, Excel, PDF oder Image, bleiben die Daten und ihre Struktur unverändert. Beim Exportieren mit einem Datenrendererformat, wie CSV (Comma-Separated Value; durch Trennzeichen getrennt) oder XML, werden keine visuellen Layoutelemente gerendert. CSV und XML wenden beim Rendern des Berichts bestimmte Regeln auf den Hauptteil des Berichts und seinen Inhalt an. Diese Regeln bestimmen, wie die Daten in diesen Formaten gerendert werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Sie können Datenrenderer zu folgenden Zwecken verwenden:  
  
-   Importieren in eine Datenbank. CSV ist ein gängiges Format, das von vielen Datenbankanwendungen, einschließlich SQL Server und Microsoft Access, problemlos importiert werden kann.  
  
-   Importieren in Excel. Verwenden Sie den CSV-Renderer, um die Daten ohne das visuelle Layout nach Excel zu exportieren. Nach dem Importieren der Daten in Excel können Sie die Excel-Standardtools, wie Diagramme, Formeln und PivotTables, nutzen.  
  
-   XSLT-Transformationen. Eine XSLT-Transformation kann für die Ausgabe des XML-Renderers übernommen werden. Diese serverseitige Transformation ist eine leistungsstarke Technik, um die Daten praktisch in jedes beliebige Format zu transformieren.  
  
-   Datenaustausch/EDI. Ein externer Prozess kann ein CSV- oder XML-Rendering eines Berichts anfordern und die entsprechenden Daten verwenden.  
  
 Datenrendererformate werden von einem anderen Satz von Eigenschaften gesteuert als Layoutrenderer. In der folgenden Liste sind die Eigenschaften aufgeführt, die im Bereich **Eigenschaften** festgelegt werden und nur für Datenrenderer gelten:  
  
-   Die DataElementOutput-Eigenschaft steuert, ob beim Exportieren ein bestimmtes Element in den Daten vorhanden ist.  
  
-   Die DataElementName-Eigenschaft steuert den Namen des Datenelements. In CSV steuert diese Eigenschaft den Namen der CSV-Spaltenkopfzeile. In XML wird diese Eigenschaft zum Namen des XML-Elements oder des Attributs für das Element.  
  
-   Die DataElementStyle-Eigenschaft steuert in XML, ob das Berichtselement als Element oder Attribut gerendert wird.  
  
 Die CSV-Exportoption (Comma-Separated Value) speichert Berichtsdaten in durch Trennzeichen getrennte Nur-Text-Dateien ohne jede Formatierung. Standardmäßig verwendet die Datei ein Komma (,) zur Trennung von Feldern und Zeilen. Diese Einstellung ist jedoch über die Geräteinformationseinstellungen konfigurierbar. Die resultierende Datei kann in einem Tabellenkalkulationsprogramm wie Office SharePoint Server geöffnet oder als Importformat für andere Programme verwendet werden. Die CSV-Datei wird in einem Text-Editor wie Notepad geöffnet. Wenn auf die CSV-Datei als URL zugegriffen wird, wird der MIME-Typ **text/csv**zurückgegeben. Die Dateien haben die MIME-Version 1.0. Weitere Informationen zum Rendern eines Berichts im CSV-Dateiformat finden Sie unter [Exportieren als CSV-Datei (Berichts-Generator und SSRS)](../report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
 Die Exportoption XML-Datei mit Berichtsdaten speichert einen Bericht als XML-Datei. Das XML-Schema für den Bericht hängt vom jeweiligen Bericht ab. Berichtslayoutinformationen werden von der XML-Exportoption nicht gespeichert. Der mithilfe dieser Option erstellte XML-Code kann in eine Datenbank importiert, als XML-Datennachricht verwendet oder an eine benutzerdefinierte Anwendung gesendet werden. Weitere Informationen zum Rendern eines Berichts im XML-Dateiformat finden Sie unter [Exportieren als XML (Berichts-Generator und SSRS)](../report-builder/exporting-to-xml-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichtselementen (Berichts-Generator und SSRS)](rendering-report-items-report-builder-and-ssrs.md)   
 [Listet &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Geräteinformationseinstellungen in Reporting Services](https://go.microsoft.com/fwlink/?LinkId=102515)  
  
  
