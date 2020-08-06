---
title: Zählen der Zeilen in einer Tabelle (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700514"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a>Zählen der Zeilen in einer Tabelle (Visual Database Tools)
  Mit dem Zählen der Zeilen in einer Tabelle können folgende Werte bestimmt werden:  
  
-   Die Gesamtanzahl von Zeilen in einer Tabelle, beispielsweise die Anzahl von allen Büchern in einer `titles` -Tabelle  
  
-   Die Anzahl von Zeilen in einer Tabelle, die eine bestimmte Bedingung erfüllen, beispielsweise die Anzahl von Büchern eines Herausgebers in einer Tabelle `titles`  
  
-   Die Anzahl von Werten in einer bestimmten Spalte  
  
 Beim Zählen der Werte in einer Spalte werden NULL-Werte nicht berücksichtigt. So kann z. B. in einer Tabelle `titles` die Anzahl von Büchern gezählt werden, für die in der Spalte `advance` Werte vorhanden sind. In der Standardeinstellung werden nicht nur eindeutige, sondern alle Werte berücksichtigt.  
  
 Die Prozeduren für die drei Zählverfahren ähneln sich.  
  
### <a name="to-count-all-the-rows-in-a-table"></a>So zählen Sie alle Zeilen in einer Tabelle  
  
1.  Stellen Sie sicher, dass die Tabelle, die Sie zusammenfassen möchten, bereits im Diagrammbereich angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü die Option **Gruppe hinzufügen nach** aus. Der [Abfrage- und Sicht-Designer](visual-database-tools.md) fügt dem Datenblatt im Kriterienbereich die Spalte **Gruppieren nach** hinzu.  
  
3.  Wählen Sie ** \* (alle Spalten)** in dem Rechteck aus, das die Tabelle oder das Tabellen Wertobjekt darstellt.  
  
     Der Abfrage- und Sicht-Designer setzt den Ausdruck **Anzahl** automatisch in die Spalte **Gruppieren nach** des Kriterienbereichs ein und weist der Spalte, die zusammengefasst werden soll, einen Spaltenalias zu. Sie können diesen automatisch generierten durch einen aussagekräftigeren Alias ersetzen. Weitere Informationen finden Sie unter [Erstellen von Spaltenaliasen &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Führen Sie die Abfrage aus.  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a>So zählen Sie alle Zeilen, die eine Bedingung erfüllen  
  
1.  Stellen Sie sicher, dass die Tabelle, die Sie zusammenfassen möchten, bereits im Diagrammbereich angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü die Option **Gruppe hinzufügen nach** aus. Der Abfrage- und Sicht-Designer fügt dem Datenblatt im Kriterienbereich die Spalte **Gruppieren nach** hinzu.  
  
3.  Wählen Sie ** \* (alle Spalten)** in dem Rechteck aus, das die Tabelle oder das Objekt mit Tabellenstruktur darstellt.  
  
     Der Abfrage- und Sicht-Designer setzt den Ausdruck **Anzahl** automatisch in die Spalte **Gruppieren nach** des Kriterienbereichs ein und weist der Spalte, die zusammengefasst werden soll, einen Spaltenalias zu. Informationen, wie eine aussagekräftigere Spaltenüberschrift in einer Abfrageausgabe erstellt wird, finden Sie unter [Erstellen von Spaltenaliasen &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Fügen Sie die zu durchsuchende Datenspalte hinzu, und deaktivieren Sie das Kontrollkästchen in der Spalte **Ausgabe**.  
  
     Der Abfrage- und Sicht-Designer fügt automatisch den Ausdruck **Gruppieren nach** in die **Gruppieren nach** -Spalte des Rasters ein.  
  
5.  Ändern Sie den Ausdruck **Gruppieren nach** in der **Gruppieren nach** Spalte in **Wobei**.  
  
6.  Geben Sie die Suchbedingung in die Spalte **Filter** der zu durchsuchenden Datenspalte ein.  
  
7.  Führen Sie die Abfrage aus.  
  
### <a name="to-count-the-values-in-a-column"></a>So zählen Sie die Werte in einer Spalte  
  
1.  Stellen Sie sicher, dass die Tabelle, die Sie zusammenfassen möchten, bereits im Diagrammbereich angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagrammbereichs, und wählen Sie im Kontextmenü die Option **Gruppe hinzufügen nach** aus. Der Abfrage- und Sicht-Designer fügt dem Datenblatt im Kriterienbereich die Spalte **Gruppieren nach** hinzu.  
  
3.  Fügen Sie dem Kriterienbereich die Spalte hinzu, in der gezählt werden soll.  
  
     Der Abfrage- und Sicht-Designer fügt automatisch den Ausdruck **Gruppieren nach** in die **Gruppieren nach** -Spalte des Rasters ein.  
  
4.  Ändern Sie den Ausdruck **Gruppieren nach** in der Spalte **Gruppieren nach** in **Anzahl**.  
  
    > [!NOTE]  
    >  Wenn nur eindeutige Werte gezählt werden sollen, wählen Sie **Count Distinct**aus.  
  
5.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sortieren und Gruppieren von Abfrage Ergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
