---
title: Unterschiedliche Abfragedefinitionen (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9a39d5d6b739fa4ab1a96ea95b513ecb7f6682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720767"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a>Unterschiedliche Abfragedefinitionen (Dialogfeld) (Visual Database Tools)
  In diesem Dialogfeld werden Sie darauf hingewiesen, dass die Abfrage in den Bereichen Diagramm und Kriterien grafisch nicht dargestellt und daher nur im SQL-Bereich bearbeitet werden kann.  
  
 Dieses Dialogfeld wird angezeigt, wenn Sie eine SQL-Anweisung im SQL-Bereich eingeben oder bearbeiten, dann zu einem anderen Bereich wechseln, die Abfrage überprüfen oder versuchen, sie auszuführen, und gleichzeitig eine der folgenden Bedingungen zutrifft:  
  
-   Die SQL-Anweisung ist unvollständig oder enthält mindestens einen Syntaxfehler.  
  
-   Die SQL-Anweisung ist gültig, wird aber von den grafischen Bereichen nicht unterstützt (z. B. eine Union-Abfrage).  
  
-   Die SQL-Anweisung ist gültig, enthält aber Syntax, die nur für die verwendete Datenverbindung gilt.  
  
> [!TIP]  
>  Sie können die Gültigkeit einer Anweisung auf der Symbolleiste **Abfrage** mithilfe der Schaltfläche **Analysieren** überprüfen.  
  
 Das Dialogfeld zeigt eine Meldung mit dem Hinweis an, dass die SQL-Anweisung nicht dargestellt werden kann. Geben Sie an, wie Sie weiter vorgehen möchten.  
  
> [!NOTE]  
>  Das Dialogfeld **Unterschiedliche Abfragedefinitionen** wird nicht angezeigt, wenn die Bereiche „Diagramm“ und „Kriterien“ ausgeblendet sind.  
  
## <a name="options"></a>Tastatur  
 **Schaltfläche Ignorieren**  
 Mit dieser Schaltfläche können Sie die SQL-Anweisung übernehmen, um sie weiter zu bearbeiten oder auszuführen. Wenn Sie die Anweisung übernehmen, werden die Bereiche Diagramm und Kriterien abgeblendet, um anzuzeigen, dass die Anweisung im SQL-Bereich darin nicht dargestellt wird.  
  
 **Schaltfläche Rückgängig**  
 Mit dieser Schaltfläche können Sie die im SQL-Bereich vorgenommenen Änderungen verwerfen.  
  
> [!NOTE]  
>  Wenn die Anweisung richtig ist, aber vom Abfrage- und Sicht-Designer nicht grafisch unterstützt wird, können Sie sie ausführen, obwohl sie nicht in den Bereichen Diagramm und Kriterien dargestellt wird. Wenn Sie beispielsweise eine Union-Abfrage eingeben, kann die Anweisung ausgeführt, aber nicht in den anderen Bereichen dargestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tools im Abfrage- und Sicht-Designer &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
