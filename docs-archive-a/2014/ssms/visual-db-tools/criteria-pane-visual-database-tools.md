---
title: Kriterienbereich (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], Criteria pane
- View Designer, Criteria pane
- entering query options into grid [SQL Server]
- Criteria pane
- inserting query options into grid
- grid showing query options [SQL Server]
- adding query options into grid
ms.assetid: 6291affe-580e-482f-a7ff-45ce3837956a
author: stevestein
ms.author: sstein
ms.openlocfilehash: bbfbe9cd1b7e61c424518c2bafc2c7bee90f0481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699105"
---
# <a name="criteria-pane-visual-database-tools"></a>Kriterienbereich (Visual Database Tools)
  Im Kriterienbereich können Sie Abfrageoptionen angeben, d.h. welche Datenspalten angezeigt oder wie die Ergebnisse sortiert werden und welche Zeilen ausgewählt werden sollen. Hierzu geben Sie die gewünschten Optionen in einem Datenblatt ähnlich einer Kalkulationstabelle ein. Im Kriterienbereich können Sie Folgendes angeben:  
  
-   die anzuzeigenden Spalten sowie Aliase für Spaltennamen  
  
-   die Tabelle, zu der eine Spalte gehört  
  
-   Ausdrücke für berechnete Spalten  
  
-   die Sortierreihenfolge für die Abfrage  
  
-   Suchbedingungen  
  
-   Gruppierungskriterien für Zusammenfassungsberichte, einschließlich Aggregatfunktionen  
  
-   Neue Werte für UPDATE- oder INSERT INTO-Abfragen  
  
-   Zielspaltennamen für INSERT FROM-Abfragen  
  
 Änderungen im Kriterienbereich werden automatisch im Diagrammbereich und im SQL-Bereich wiedergegeben. Entsprechend wird auch der Kriterienbereich automatisch aktualisiert, wenn Sie Änderungen in den anderen Bereichen vornehmen.  
  
## <a name="about-the-criteria-pane"></a>Informationen über den Kriterienbereich  
 Die Zeilen im Kriterienbereich zeigen die Datenspalten an, die in der Abfrage verwendet werden. Die Spalten im Kriterienbereich geben die Abfrageoptionen wieder.  
  
 Welche Informationen genau im Kriterienbereich angezeigt werden, ist abhängig vom Typ der erstellten Abfrage.  
  
 Wenn der Kriterienbereich nicht sichtbar ist, klicken Sie mit der rechten Maustaste auf den Designer, zeigen Sie auf **Bereich**, und klicken Sie dann auf **Kriterien**.  
  
## <a name="options"></a>Tastatur  
  
|**Spalte**|**Abfragetyp**|**Beschreibung**|  
|----------------|--------------------|---------------------|  
|Column|All|Zeigt entweder den Namen einer in der Abfrage verwendeten Datenspalte oder den Ausdruck für eine berechnete Spalte an. Diese Spalte ist gesperrt und bleibt somit bei einem horizontalen Bildlauf immer sichtbar.|  
|Alias|SELECT, INSERT FROM, UPDATE, MAKE TABLE|Gibt entweder einen alternativen Namen für eine Spalte an oder den Namen, den Sie für eine berechnete Spalte verwenden können.|  
|Tabelle|SELECT, INSERT FROM, UPDATE, MAKE TABLE|Gibt den Namen der Tabelle oder des Objekts mit Tabellenstruktur für die zugeordnete Datenspalte an. Diese Spalte ist bei berechneten Spalten leer.|  
|Output|SELECT, INSERT FROM, MAKE TABLE|Gibt an, ob eine Datenspalte in der Abfrageausgabe aufgeführt wird oder nicht.<br /><br /> Hinweis: Wenn dies in der Datenbank zulässig ist, können Sie eine Datenspalte in Sortier- oder Suchklauseln verwenden, ohne die Spalte im Resultset anzuzeigen.|  
|Sortiertyp|SELECT, INSERT FROM|Gibt an, dass die zugeordnete Datenspalte zum Sortieren der Abfrageergebnisse verwendet wird. Zeigt außerdem an, ob aufsteigend oder absteigend sortiert wird.|  
|Sortierreihenfolge|SELECT, INSERT FROM|Gibt die Sortierpriorität für Datenspalten an, die zum Sortieren des Resultsets verwendet werden. Wenn Sie die Sortierreihenfolge für eine Datenspalte ändern, wird die Sortierreihenfolge für alle anderen Spalten entsprechend aktualisiert.|  
|Gruppieren nach|SELECT, INSERT FROM, MAKE TABLE|Gibt an, dass die zugeordnete Datenspalte zum Erstellen einer Aggregatabfrage verwendet wird. Diese Datenblattspalte wird nur angezeigt, wenn Sie im Menü **Extras** die Option **Gruppieren nach** ausgewählt oder im SQL-Bereich eine GROUP BY-Klausel hinzugefügt haben.<br /><br /> In der Standardeinstellung ist der Wert dieser Spalte auf **Gruppieren nach**gesetzt, und die Spalte ist Teil der GROUP BY-Klausel.<br /><br /> Wenn Sie in eine Zelle in dieser Spalte wechseln und eine Aggregatfunktion auf die zugeordnete Datenspalte anwenden, wird für den sich ergebenden Ausdruck eine Ausgabespalte zum Resultset hinzugefügt.|  
|Kriterien|All|Gibt eine Suchbedingung (Filter) für die zugeordnete Datenspalte an. Geben Sie einen Operator (Standardeinstellung ist "=") und den zu suchenden Wert ein. Setzen Sie Textwerte in einfache Anführungszeichen.<br /><br /> Wenn die zugeordnete Datenspalte Teil einer GROUP BY-Klausel ist, wird der von Ihnen eingegebene Ausdruck für eine HAVING-Klausel verwendet.<br /><br /> Wenn Sie in der Datenblattspalte **Kriterien** Werte für mehrere Zellen eingeben, werden die sich ergebenden Suchbedingungen automatisch durch ein logisches AND verknüpft.<br /><br /> Um mehrere Ausdrücke für Suchbedingungen für eine einzelne Datenbankspalte anzugeben, z. B. (fname > 'A') AND (fname < 'M'), fügen Sie die Datenspalte zweimal in den Kriterienbereich ein, und geben Sie für jede Instanz der Datenspalte unterschiedliche Werte in der Spalte **Kriterien** ein.|  
|Oder...|All|Gibt einen zusätzlichen Ausdruck für eine Suchbedingung für die Datenspalte an, der mit vorherigen Ausdrücken durch ein logisches OR verknüpft wird. Sie können weitere **Oder** -Rasterspalten hinzufügen, indem Sie in der äußerst rechten **Oder** -Spalte die TAB-TASTE drücken.|  
|Anfügen|INSERT FROM|Gibt den Namen der Zieldatenspalte für die zugeordnete Datenspalte an. Wenn Sie eine INSERT FROM-Abfrage erstellen, versucht der Abfrage- und Sicht-Designer, die Quelle einer übereinstimmenden Zieldatenspalte zuzuordnen. Wenn der Abfrage- und Sicht-Designer keine Übereinstimmung finden kann, müssen Sie den Spaltennamen angeben.|  
|Neuer Wert|UPDATE, INSERT INTO|Gibt den Wert an, der in der zugeordneten Spalte gesetzt werden soll. Geben Sie einen Literalwert oder einen Ausdruck ein.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Themen zur Vorgehensweise beim Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Diagrammbereich &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md)   
 [Regeln für das Eingeben von Such Werten &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Sortieren und Gruppieren von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Ergebnisbereich &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)   
 [SQL-Bereich &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md)  
  
  
