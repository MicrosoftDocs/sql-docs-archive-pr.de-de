---
title: Hinzufügen neuer Zeilen im Ergebnisbereich (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3137da106279e09305261c6c7cb7fd06d254b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615763"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a>Hinzufügen neuer Zeilen im Ergebnisbereich (Visual Database Tools)
  Sie können neue Daten hinzufügen, indem Sie sie eintippen oder aus einem anderen Programm, z. B. Editor oder Excel, einfügen. Eine einzufügende Zeile muss genau dieselbe Anzahl und denselben Typ von Spalten wie die Tabelle aufweisen, in die Sie die Zeile einfügen. Sie können mehrere Zeilen gleichzeitig in den Ergebnisbereich einfügen.  
  
 Informationen zum Eingeben von Daten finden Sie unter [Regeln zum Aktualisieren von Ergebnissen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
### <a name="to-add-a-new-data-row"></a>So fügen Sie eine neue Datenzeile ein  
  
1.  Wechseln Sie in den unteren Teil des Ergebnisbereichs, in dem eine leere Zeile für das Hinzufügen einer neuen Datenzeile verfügbar ist.  
  
     Die Anfangswerte aller Spalten sind *NULL*.  
  
    > [!TIP]  
    >  Um sofort zur ersten Leerzeile zu wechseln, benutzen Sie die Navigationsleiste am unteren Rand des Ergebnisbereichs.  
  
2.  Wenn Sie Zeilen aus der Zwischenablage einfügen, markieren Sie die neue Zeile, indem Sie auf die Schaltfläche auf der linken Seite klicken.  
  
    > [!NOTE]  
    >  Wenn eine oder mehrere der eingefügten Zeilen nicht in die Datenbank eingetragen werden können, wird eine Meldung ausgegeben, die darüber Auskunft gibt, welche Zeile(n) nicht eingetragen werden konnte(n).  
  
3.  Geben Sie die Daten für die neue Zeile ein. Beim Einfügen aus der Zwischenablage wählen Sie im Menü **Bearbeiten** die Option **Einfügen** aus.  
  
4.  Bewegen Sie den Zeiger aus der Zeile heraus, damit sie in die Datenbank eingetragen wird.  
  
 Falls beim Speichern der Zeile ein Fehler auftritt, zeigt der Abfrage- und Sicht-Designer eine Meldung an und setzt den Zeiger in die Zeile, die Sie in Bearbeitung hatten. Sie können anschließend folgende Aktionen durchführen:  
  
-   Auflösen des Fehlers durch weitere Bearbeitungen der Zeile.  
  
-   Abbrechen der Bearbeitung durch Drücken von ESC. Wenn Sie sich beim Drücken von ESC in einer geänderten Zelle befinden, werden die Änderungen an dieser Zelle abgebrochen. Befinden Sie sich beim Drücken von ESC in einer nicht geänderten Zelle, werden die Änderungen für die gesamte Zeile verworfen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Daten im Ergebnisbereich &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
