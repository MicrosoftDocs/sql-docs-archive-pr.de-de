---
title: Einschließen oder Ausschließen von Zeilen (Visual Database Tools) Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- included rows
- search conditions [SQL Server], HAVING clause
- search criteria [SQL Server], including rows
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- search conditions [SQL Server], WHERE clause
- row included in search [SQL Server]
- excluding rows
ms.assetid: ba4e1202-31a2-444d-8365-c68a530ef223
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b2d31c51296fa73a503e59a14adb60d79a61178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618965"
---
# <a name="include-or-exclude-rows-visual-database-tools"></a>Einschließen oder Ausschließen von Zeilen (Visual Database Tools)
  Wenn Sie die Anzahl von durch eine SELECT-Abfrage zurückgegebenen Zeilen einschränken möchten, erstellen Sie Suchbedingungen oder Filterkriterien. In SQL werden Suchbedingungen entweder in die WHERE-Klausel der Anweisung eingefügt oder – wenn Sie eine Aggregatabfrage erstellen – in die HAVING-Klausel.  
  
> [!NOTE]  
>  Sie können auch Suchbedingungen definieren, welche die von einer UPDATE-, INSERT RESULTS-, INSERT VALUES-, DELETE- oder MAKE TABLE-Abfrage betroffenen Zeilen angeben.  
  
 Sobald die Abfrage ausgeführt wird, untersucht [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Suchbedingung und wendet sie auf jede Zeile in den durchsuchten Tabellen an. Wenn eine Zeile die Bedingungen erfüllt, wird sie in die Abfrage aufgenommen. Eine Suchbedingung, die z. B. alle Mitarbeiter in einer bestimmten Region ermittelt, könnte folgendermaßen formuliert werden:  
  
```  
region = 'UK'  
```  
  
 Die Definition der Kriterien für die Auswahl der Ergebniszeilen kann über mehrere Suchbedingungen erfolgen. Das folgende Kriterium für die Suche besteht z. B. aus zwei Suchbedingungen. Die Abfrage nimmt eine Zeile nur dann in das Resultset auf, wenn sie beide Bedingungen erfüllt.  
  
```  
region = 'UK' AND product_line = 'Housewares'  
```  
  
 Sie können Bedingungen durch AND oder OR kombinieren. Im oben dargestellten Beispiel wird AND verwendet. Im Gegensatz hierzu sind die Bedingungen im folgenden Beispiel durch ein OR kombiniert. Das zurückgegebene Abfrageergebnis enthält alle Zeilen, die mindestens eine oder beide Suchbedingungen erfüllen:  
  
```  
region = 'UK' OR product_line = 'Housewares'  
```  
  
 Für eine Spalte können auch mehrere Suchbedingungen kombiniert werden. Im folgenden Beispiel sind zwei Bedingungen für die Spalte Region kombiniert:  
  
```  
region = 'UK' OR region = 'US'  
```  
  
 Ausführliche Informationen zum Kombinieren von Suchbedingungen finden Sie unter den folgenden Themen:  
  
-   [Konventionen für das Kombinieren von Suchbedingungen im Kriterienbereich &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
  
-   [Angeben mehrerer Suchbedingungen für eine Spalte &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
-   [Angeben mehrerer Suchbedingungen für mehrere Spalten &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
  
-   [Kombinieren von Bedingungen, wenn AND Vorrang hat &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
  
-   [Kombinieren von Bedingungen, wenn OR Vorrang hat &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
  
## <a name="examples"></a>Beispiele  
 Es folgen einige Beispiele für Abfragen mit verschiedenen Operatoren und Zeilenkriterien:  
  
-   **Literalwert** : Ein einzelner numerischer oder logischer Wert, ein Textwert oder eine Datumsangabe. Im folgenden Beispiel wird ein Literalwert für die Suche nach allen Zeilen für Mitarbeiter in Großbritannien verwendet:  
  
    ```  
    WHERE region = 'UK'  
    ```  
  
-   **Spaltenverweis** : Vergleicht die Werte einer Spalte mit den Werten einer anderen Spalte. Im folgenden Beispiel wird in der `products` -Tabelle nach allen Zeilen gesucht, in denen für die Produktionskosten ein kleinerer Wert als für die Frachtkosten angegeben ist:  
  
    ```  
    WHERE prod_cost < ship_cost  
    ```  
  
-   **Funktion** : Ein Verweis auf eine Funktion, die vom Back-End der Datenbank aufgelöst werden kann, um einen Wert für die Suche zu berechnen. Bei der Funktion kann es sich um eine durch den Datenbankserver definierte Funktion oder um eine benutzerdefinierte Funktion handeln, die einen Skalarwert zurückgibt. Im folgenden Beispiel wird nach allen am jeweiligen Tag erteilten Aufträgen gesucht (die GETDATE( )-Funktion liefert das aktuelle Datum):  
  
    ```  
    WHERE order_date = GETDATE()  
    ```  
  
-   **NULL** : Im folgenden Beispiel wird in einer Tabelle mit dem Namen `authors` nach allen Autoren gesucht, für die der Vorname in der Datenbank gespeichert wurde:  
  
    ```  
    WHERE au_fname IS NOT NULL  
    ```  
  
-   **Berechnung** : Das Ergebnis einer Berechnung, die Literalwerte, Spaltenverweise oder andere Ausdrücke enthalten kann. Im folgenden Beispiel wird in einer Tabelle mit dem Namen `products` nach allen Zeilen gesucht, in denen der Einzelhandelspreis mindestens doppelt so hoch ist wie der Herstellungspreis:  
  
    ```  
    WHERE sales_price > (prod_cost * 2)  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Themen zur Vorgehensweise beim Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Angeben von Suchkriterien &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md)  
  
  
