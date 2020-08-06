---
title: Lokal (Fenster)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622002"
---
# <a name="locals-window"></a>Lokalfenster
  Im Fenster **Lokal** werden Informationen über die lokalen Ausdrücke im aktuellen Bereich des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debuggers angezeigt. Der Bereich wird auf den aktuellen Aufruflistenrahmen festgelegt, der im Fenster **Aufrufliste** ausgewählt ist. Sie müssen sich im Debugmodus befinden, um die lokalen Ausdrücke anzuzeigen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Fenster Lokal zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Lokal**.  
  
 **So ändern Sie den Wert eines Ausdrucks**  
  
-   Klicken mit der rechten Maustaste auf den Ausdruck, und wählen Sie anschließend **Wert bearbeiten**aus.  
  
## <a name="columns"></a>Spalten  
 **Name**  
 Der Name des lokalen Ausdrucks. Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debugger führt Variablen, Parameter und die Systemfunktionen, deren Namen mit @@ beginnen, auf.  
  
 **Wert**  
 Zeigt den Wert an, der dem lokalen Ausdruck derzeit zugewiesen ist. Diese Spalte ist leer, wenn dem Ausdruck kein Wert zugewiesen wurde.  
  
 Wenn die Länge eines Ausdrucks größer als die Breite der Spalte **Wert** ist, wird der vollständige Wert in einer QuickInfo angezeigt, wenn Sie den Mauszeiger über die **Wertzelle** für diesen Ausdruck bewegen.  
  
 Ein Lupensymbol in einer **Wertzelle** zeigt an, dass die [!INCLUDE[tsql](../../includes/tsql-md.md)] Debuggerschnellansicht verfügbar ist. In der Liste können Sie **Text-Schnellansicht**, **XML-Schnellansicht**oder **HTML-Schnellansicht**angeben. Um eine Debuggerschnellansicht zu starten, klicken Sie auf das Lupensymbol. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger öffnet ein Dialogfeld, in dem die Daten in einem für den Datentyp geeigneten Format angezeigt werden.  
  
 **Typ**  
 Zeigt den Datentyp des Ausdrucks an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)   
 [Überwachung (Fenster)](transact-sql-debugger-watch-window.md)   
 [Fenster 'Aufrufliste'](transact-sql-debugger-call-stack-window.md)   
 [Dialogfeld 'Schnellüberwachung'](transact-sql-debugger-quickwatch-dialog-box.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
