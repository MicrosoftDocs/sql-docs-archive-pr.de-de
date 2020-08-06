---
title: Zusammenfassen oder Aggregieren von Werten für alle Zeilen in einer Tabelle (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4d80c8ab2b811b8e796f0a37b2180a2866c332
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720728"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a>Wertzusammenfassung oder -aggregation für alle Zeilen in einer Tabelle (Visual Database Tools)
  Mithilfe einer Aggregatfunktion können Sie eine Zusammenfassung für alle Werte in einer Tabelle erstellen. Sie können z. B. folgende Abfrage erstellen, um den Gesamtpreis aller Bücher in der Tabelle `titles` anzeigen zu lassen:  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 Sie können mehrere Aggregationen in derselben Abfrage erstellen, wenn Sie Aggregatfunktionen auf mehrere Spalten anwenden. Beispielsweise können Sie eine Abfrage erstellen, in der die Gesamtsumme der `price` -Spalte und der Durchschnittswert der `discount` -Spalte berechnet werden.  
  
 Sie können jedoch auch eine einzige Spalte in derselben Abfrage auf unterschiedliche Weise aggregieren (z. B. Ausgabe der Gesamtsumme, der Anzahl und des Durchschnittswerts). In der folgenden Abfrage wird beispielsweise der Durchschnittswert und die Gesamtsumme für die `price` -Spalte in der Tabelle `titles` berechnet:  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 Wenn Sie eine Suchbedingung hinzufügen, können Sie die Teilmenge von Zeilen aggregieren, die die entsprechende Bedingung erfüllt.  
  
> [!NOTE]  
>  Sie können außerdem alle Zeilen in der Tabelle oder nur die Zeilen zählen, die eine bestimmte Bedingung erfüllen. Weitere Informationen finden Sie unter [Zählen der Zeilen in einer Tabelle &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Wenn Sie für alle Zeilen in einer Tabelle einen einzigen Aggregatwert erstellen, werden nur die Aggregatwerte selbst angezeigt. Wenn Sie z. B. die Gesamtsumme des Werts für die `price` -Spalte in der Tabelle `titles` berechnen, werden die einzelnen Buchtitel, Herausgebernamen usw. nicht angezeigt.  
  
> [!NOTE]  
>  Wenn Sie Teilergebnisse berechnen, d.h. Gruppen erstellen, können Sie die Spaltenwerte für jede Gruppe anzeigen. Weitere Informationen finden Sie unter [Gruppieren von Zeilen in Abfrageergebnissen &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).  
  
### <a name="to-aggregate-values-for-all-rows"></a>So aggregieren Sie Werte für alle Zeilen  
  
1.  Stellen Sie sicher, dass die Tabelle, die Sie aggregieren möchten, bereits im Diagrammbereich angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü die Option **Gruppieren nach** aus. Der [Abfrage-und Sicht-Designer](query-and-view-designer-tools-visual-database-tools.md) fügt dem Raster im Kriterienbereich eine Spalte **vom Typ gruppieren nach** hinzu.  
  
3.  Fügen Sie dem Kriterienbereich die Spalte hinzu, die aggregiert werden soll. Vergewissern Sie sich, dass die Spalte für die Ausgabe ausgewählt ist.  
  
     Der Abfrage- und Sicht-Designer weist der Spalte, die zusammengefasst wird, automatisch einen Spaltenalias zu. Sie können diesen Alias durch einen aussagekräftigeren Alias ersetzen. Ausführliche Informationen finden Sie unter [Erstellen von Spaltenaliasen &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Wählen Sie in der **Gruppieren nach**-Rasterspalte die gewünschte Aggregatfunktion aus, z. B.: **SUM**, **AVG**, **MIN**, **MAX**, **COUNT**. Wenn im Resultset nur eindeutige Zeilen aggregiert werden sollen, wählen Sie eine Aggregatfunktion mit den DISTINCT-Optionen aus, z. B. **Min Distinct**. Verwenden Sie nicht **Gruppieren nach**, **Ausdruck**oder **Wobei**, da diese Optionen bei einer Aggregation aller Zeilen nicht anwendbar sind.  
  
     Der Abfrage- und Sicht-Designer ersetzt den Spaltennamen in der Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md) durch die angegebene Aggregatfunktion. Die SQL-Anweisung könnte z. B. folgendermaßen aussehen:  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  Wenn Sie mehrere Aggregationen in der Abfrage erstellen möchten, wiederholen Sie die Schritte 3 und 4.  
  
     Wenn Sie der Liste der Abfrageergebnisse oder der ORDER BY-Liste eine weitere Spalte hinzufügen, wird vom Abfrage- und Sicht-Designer automatisch der Begriff **Gruppieren nach** in die **Gruppieren nach** Spalte des Rasters eingefügt. Wählen Sie die entsprechende Aggregatfunktion aus.  
  
6.  Fügen Sie bei Bedarf Suchbedingungen hinzu, um die Teilmenge der zusammenzufassenden Zeilen anzugeben.  
  
 Bei Ausführung der Abfrage werden die angegebenen Aggregationen im Ergebnisbereich angezeigt.  
  
> [!NOTE]  
>  Der Abfrage- und Sicht-Designer behält die Aggregatfunktionen so lange als Bestandteil der SQL-Anweisung im SQL-Bereich bei, bis Sie den Gruppieren nach-Modus explizit ausschalten. Wenn Sie daher den Typ der Abfrage ändern oder ändern, welche Tabellen bzw. Tabellenwertobjekte im Diagrammbereich vorhanden sind, kann die resultierende Abfrage unter Umständen ungültige Aggregatfunktionen enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sortieren und Gruppieren von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
