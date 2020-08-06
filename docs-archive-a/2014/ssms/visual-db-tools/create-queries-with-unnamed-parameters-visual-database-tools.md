---
title: Erstellen von Abfragen mit unbenannten Parametern (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ea53afd1fa4d44390f5805d6b28494428608b90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608200"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Erstellen von Abfragen mit unbenannten Parametern (Visual Database Tools)
  Sie können eine Abfrage mit einem unbenannten Parameter erstellen, indem Sie ein Fragezeichen (?) als Platzhalter für den Literalwert angeben. Der Abfrage- und Sicht-Designer weist dann einen temporären Namen zu. In der Abfrage können beliebig viele unbenannte Parameter festgelegt werden.  
  
 Wenn Sie die Abfrage im Abfrage- und Sicht-Designer ausführen, wird das Dialogfeld Abfrageparameter mit dem temporären Namen angezeigt.  
  
### <a name="to-specify-an-unnamed-parameter"></a>So geben Sie einen unbenannten Parameter an  
  
1.  Fügen Sie dem [Kriterienbereich](visual-database-tools.md)die Spalten oder Ausdrücke hinzu, nach denen gesucht werden soll. Wenn in den Abfrageergebnissen keine Suchspalten bzw. Suchausdrücke angezeigt werden sollen, entfernen Sie die entsprechenden Ausgabespalten.  
  
2.  Wechseln Sie zu der Zeile, die die Datenspalte oder den Ausdruck für die Suche enthält, und geben Sie in der Datenblattspalte **Filter** ein Fragezeichen (?) ein.  
  
     Der Abfrage- und Sicht-Designer fügt standardmäßig den Operator "=" hinzu. Sie können die Zelle jedoch so bearbeiten, dass dafür ">", "<" oder ein beliebiger anderer SQL-Vergleichsoperator eingesetzt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Abfragen mit Parametern &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md)  
  
  
