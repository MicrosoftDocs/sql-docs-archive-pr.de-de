---
title: Überwachung (Fenster)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: rothja
ms.author: jroth
ms.openlocfilehash: c2a3db9b095902fcb5620af91fb86d80f773d606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620260"
---
# <a name="watch-window"></a>Überwachung (Fenster)
  Im Fenster **Überwachung** werden Informationen über die Ausdrücke angezeigt, die Sie ausgewählt haben. Es können bis zu vier Überwachungsfenster verfügbar sein: **Überwachen 1**, **Überwachen 2**, Überwachen 3 und **Überwachen 4**. Die Ausdrücke werden innerhalb des Bereichs des aktuellen Aufruflistenrahmens ausgewertet, der im Fenster **Aufrufliste** ausgewählt ist. Sie müssen sich im Debugmodus befinden, um Variablen und Ausdrücke zu beobachten.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf die Überwachungsfenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**, klicken Sie auf **Überwachung**, und klicken Sie dann auf **Überwachung 1**, **Überwachung 2**, **Überwachung 3**oder Überwachung 4.  
  
 **So ändern Sie den Wert eines Ausdrucks**  
  
-   Klicken mit der rechten Maustaste auf den Ausdruck, und wählen Sie anschließend **Wert bearbeiten**aus.  
  
## <a name="columns"></a>Spalten  
 **Name**  
 Die Ausdrücke, die vom [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger aufgelistet werden. Die folgenden Ausdrücke werden unterstützt:  
  
-   Variablen  
  
-   Parameter.  
  
-   Systemfunktionen, deren Name mit „@@“ beginnt.  
  
-   Ausdrücke, die durch Anwenden von Operatoren auf eine oder mehrere Variablen, Parameter oder Systemfunktionen erstellt werden, z.B. "@IntegerCounter + 1" oder "FirstName + LastName"  
  
-   Transact-SQL-Anweisungen, die einen einzelnen Wert zurückgeben, z. B.: "SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1"  
  
 **Wert**  
 Zeigt den Wert an, der zurückgegeben wird, nachdem der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger den in **Name**angegebenen Ausdruck ausgewertet hat.  
  
 Wenn die Länge eines Ausdrucks größer als die Breite der Spalte **Wert** ist, wird der vollständige Wert in einer QuickInfo angezeigt, wenn Sie den Mauszeiger über die **Wertzelle** für diesen Ausdruck bewegen.  
  
 Ein Lupensymbol in einer **Wertzelle** zeigt an, dass die [!INCLUDE[tsql](../../includes/tsql-md.md)] Debuggerschnellansicht verfügbar ist. In der Liste können Sie **Text-Schnellansicht**, **XML-Schnellansicht**oder **HTML-Schnellansicht**angeben. Um eine Debuggerschnellansicht zu starten, klicken Sie auf das Lupensymbol. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger öffnet ein Dialogfeld, in dem die Daten in einem für den Datentyp geeigneten Format angezeigt werden.  
  
 **Typ**  
 Zeigt den Datentyp des Ausdrucks an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)   
 [Lokal (Fenster)](transact-sql-debugger-locals-window.md)   
 [Fenster 'Aufrufliste'](transact-sql-debugger-call-stack-window.md)   
 [Dialogfeld 'Schnellüberwachung'](transact-sql-debugger-quickwatch-dialog-box.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
