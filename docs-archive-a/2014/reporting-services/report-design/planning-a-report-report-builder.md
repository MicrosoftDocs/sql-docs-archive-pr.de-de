---
title: Planen eines Berichts (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- getting started
- report design
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 82804dff373cc4221db30f84720c21f9aea009f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695298"
---
# <a name="planning-a-report-report-builder"></a>Planen eines Berichts (Berichts-Generator)
  Mit dem Berichts-Generator können viele Arten von Berichten erstellt werden. Sie können beispielsweise Berichte erstellen, die zusammenfassende oder detaillierte Umsatzdaten, Marketing- und Umsatztrends sowie Betriebsberichte oder Dashboards enthalten. Sie können auch Berichte erstellen, die umfassend formatierten Text nutzen, beispielsweise für Bestellungen, Produktkataloge oder Serienbriefe. All diese Berichte werden mit unterschiedlichen Kombinationen derselben grundlegenden Bausteine im Berichts-Generator erstellt. Das Erstellen eines sinnvollen, verständlichen Berichts erfordert zunächst eine sorgfältige Planung. Bevor Sie beginnen, sollten Sie Folgendes beachten:  
  
-   **In welchem Format soll der Bericht angezeigt werden?**  
  
     Sie können Berichte online in einem Browser wie dem Berichts-Manager rendern oder sie in andere Formate exportieren, beispielsweise Excel, Word oder PDF. Die endgültige Form des Berichts ist ein wichtiger Gesichtspunkt, weil nicht alle Funktionen in sämtlichen Exportformaten verfügbar sind. Weitere Informationen finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).  
  
-   **In welcher Struktur sollen die Daten in dem Bericht dargestellt werden?**  
  
     Sie können zwischen Tabellen-, Matrix-, Diagramm- oder Freiformstrukturen bzw. einer Kombination dieser Strukturen zur Darstellung der Daten wählen (wobei die Matrixstruktur mit einem Kreuztabellen- oder PivotTable-Bericht vergleichbar ist). Weitere Informationen finden Sie unter [Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) und [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
-   **Wie soll der Bericht aussehen?**  
  
     Der Berichts-Generator stellt eine Vielzahl von Berichtselementen bereit, die Sie dem Bericht hinzufügen können, um seine Lesbarkeit zu verbessern, wichtige Informationen hervorzuheben, die Navigation im Bericht für die Zielgruppe zu vereinfachen usw. Wenn Sie wissen, wie der Bericht aussehen soll, können Sie bestimmen, ob Berichtselemente, wie Textfelder, Rechtecke, Bilder und Linien, erforderlich sind. Möglicherweise sollen auch Elemente angezeigt oder ausgeblendet werden, soll eine Dokumentstruktur hinzugefügt, sollen Drillthroughberichte oder Unterberichte aufgenommen oder Links zu anderen Berichten erstellt werden. Weitere Informationen finden Sie unter [Bilder, Textfelder, Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) und [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md).  
  
-   **Welche Daten sollen die Leser sehen? Sollen die Daten oder das Format für unterschiedliche Zielgruppen gefiltert werden?**  
  
     Sie können den Geltungsbereich des Berichts auf bestimmte Benutzer oder Speicherorte bzw. auf einen bestimmten Zeitraum eingrenzen. Zum Filtern der Berichtsdaten verwenden Sie Parameter, um nur die gewünschten Daten abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)" basiert.  
  
-   **Müssen Sie eigene Berechnungen erstellen?**  
  
     Gelegentlich enthalten die Datenquelle und die Datasets nicht die genauen Felder, die Sie für Ihren Bericht benötigen. In diesem Fall müssen Sie möglicherweise eigene berechnete Felder erstellen. Beispiel: Sie möchten den Einzelpreis mit der Stückzahl multiplizieren, um den Umsatz pro Einzelposten zu berechnen. Ausdrücke werden auch für die bedingte Formatierung und andere erweiterte Funktionen verwendet. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
-   **Möchten Sie anfänglich Berichtselemente ausblenden?**  
  
     Überlegen Sie, ob Berichtselemente, einschließlich Datenbereichen, Gruppen und Spalten, bei der ersten Ausführung des Berichts ausgeblendet werden sollen. Beispiel: Sie können anfänglich eine zusammenfassende Tabelle darstellen und danach einen Drilldown auf die detaillierten Daten durchführen. Weitere Informationen finden Sie unter [Drilldownaktion &#40;Berichts-Generator und SSRS&#41;](drilldown-action-report-builder-and-ssrs.md).  
  
-   **Wie soll der Bericht übermittelt werden?**  
  
     Sie können den Bericht auf dem lokalen Computer speichern und weiter bearbeiten oder lokal zu Ihrer eigenen Information ausführen. Sie müssen den Bericht jedoch auf einem im einheitlichen Modus konfigurierten Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus speichern, um ihn für andere Benutzer freizugeben. Wenn Sie den Bericht auf einem Server speichern, können andere Benutzer ihn jederzeit ausführen. Der Berichtsserveradministrator kann jedoch auch ein Abonnement für den Bericht oder eine E-Mail-Übermittlung des Berichts an andere Personen einrichten. Sie können den Bericht auch in einem bestimmten Exportformat übermitteln. Weitere Informationen finden Sie unter [Suchen, Anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Generator in SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md)   
 [Konzepte der Berichterstellung &#40;Berichts-Generator und SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md)  
  
  
