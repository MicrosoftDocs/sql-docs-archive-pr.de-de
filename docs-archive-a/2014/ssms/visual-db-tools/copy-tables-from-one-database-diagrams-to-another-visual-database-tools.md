---
title: Kopieren von Tabellen von einem Daten Bank Diagramm in ein anderes (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e90c8f324e80f7c59674def06a77e93a5bf0cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695130"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>Kopieren von Tabellen von einem Datenbankdiagramm in ein anderes Datenbankdiagramm (Visual Database Tools)
  Sie können eine Tabelle innerhalb derselben Datenbank von einem Datenbankdiagramm in ein anderes kopieren.  
  
 Durch das Kopieren einer Tabelle von einem Datenbankdiagramm in ein anderes Diagramm wird letzterem ein Verweis auf die Tabelle hinzugefügt. Die Tabelle wird jedoch nicht in die Datenbank dupliziert. Wenn Sie beispielsweise die Tabelle `authors` von einem Datenbankdiagramm in ein anderes kopieren, verweisen beide Diagramme auf dieselbe Tabelle `authors` in der Datenbank.  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>So kopieren Sie eine Tabelle von einem anderen Datenbankdiagramm  
  
1.  Vergewissern Sie sich, dass Sie mit der Datenbank verbunden sind, deren Tabelle Sie kopieren möchten.  
  
2.  Öffnen Sie im Ausgangsdiagramm sowohl das Ausgangs- als auch das Zieldiagramm, und markieren Sie die Tabelle, die in das Zieldiagramm kopiert werden soll.  
  
3.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Kopieren** . Dadurch wird die ausgewählte Tabellendefinition in die Zwischenablage kopiert.  
  
4.  Wechseln Sie zum Zieldiagramm. Dieses Diagramm muss sich in derselben Datenbank befinden wie das Ausgangsdiagramm.  
  
5.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Einfügen** . Der Inhalt der Zwischenablage wird nun an der neuen Stelle angezeigt und bleibt hervorgehoben, bis Sie auf eine andere Stelle klicken. Wenn Beziehungen zwischen den ausgewählten Tabellen und anderen Tabellen im Zieldiagramm bestehen, werden automatisch Beziehungslinien gezogen.  
  
 Wenn Sie die Tabelle in einem der beiden Diagramme bearbeiten, wirken sich die Änderungen auf beide Diagramme aus. Ähnliches gilt für das Speichern der Tabelle. Wenn Sie die Tabelle in einem der beiden Diagramme speichern, gilt sie in beiden Diagrammen nicht mehr als "verändert".  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Daten Bank Diagrammen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Hinzufügen von Tabellen zu Diagrammen &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md)  
  
  
