---
title: Angeben von Bedingungen für Gruppen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
ms.openlocfilehash: da9bc1b70fbfae8bf2a68a3a3ba332020020f310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607476"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a>Angeben von Bedingungen für Gruppen (Visual Database Tools)
  Sie können die Anzahl der in einer Abfrage aufgeführten Gruppen begrenzen, indem Sie eine Bedingung angeben, die für Gruppen als Ganzes gilt – eine HAVING-Klausel. Die Bedingungen der HAVING-Klausel werden angewendet, nachdem alle Daten gruppiert und aggregiert wurden. Nur die Gruppen werden in die Abfrage aufgenommen, die die Bedingungen erfüllen.  
  
 Angenommen, Sie möchten den Durchschnittspreis aller Bücher der einzelnen Herausgeber in der Tabelle `titles` anzeigen lassen, wenn dieser höher als 10,00 ist. In diesem Fall kann eine HAVING-Klausel mit folgender Bedingung angegeben werden: `AVG(price) > 10`.  
  
> [!NOTE]  
>  In einigen Fällen kann es sinnvoll sein, vor Anwendung einer Bedingung auf Gruppen als Ganzes einzelne Zeilen aus den Gruppen auszuschließen. Weitere Informationen finden Sie unter [Verwenden von HAVING- und WHERE-Klauseln in derselben Abfrage &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Sie können komplexe Bedingungen für eine HAVING-Klausel erstellen, indem Sie Bedingungen mit AND und OR verknüpfen. Weitere Informationen zum Verwenden von AND und OR in Suchbedingungen finden Sie unter [Angeben mehrerer Suchbedingungen für eine Spalte &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).  
  
### <a name="to-specify-a-condition-for-a-group"></a>So geben Sie eine Bedingung für eine Gruppe an  
  
1.  Geben Sie die Gruppen für die Abfrage an. Weitere Informationen finden Sie unter [Gruppieren von Zeilen in Abfrageergebnissen &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).  
  
2.  Fügen Sie dem [Kriterienbereich](criteria-pane-visual-database-tools.md) die Spalte hinzu, auf der die Bedingung basieren soll, sofern sie dort nicht bereits vorhanden ist. (Meistens enthält die Bedingung eine bereits gruppierte bzw. zusammengefasste Spalte.) Spalten, die weder einer Aggregatfunktion noch der GROUP BY-Klausel angehören, können nicht verwendet werden.  
  
3.  Geben Sie die Bedingung für die Gruppe in der Spalte **Filter** an.  
  
     Der [Abfrage- und Sicht-Designer](query-and-view-designer-tools-visual-database-tools.md) erstellt automatisch eine HAVING-Klausel in der Anweisung im [SQL-Bereich](sql-pane-visual-database-tools.md). Beispiel:  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  Wiederholen Sie die Schritte 2 und 3 für jede weitere Bedingung, die angegeben werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)  
  
  
