---
title: Angeben einer Breakpointaktion
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint action
- Transact-SQL debugger, breakpoint when hit action
ms.assetid: f97f0097-6f51-40c1-b2e0-294a93ce1e1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b3c445e738752400e716538e038349e04e7bd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618623"
---
# <a name="specify-a-breakpoint-action"></a>Angeben einer Breakpointaktion
  Die Breakpointaktion **Bei Treffer** gibt einen benutzerdefinierten Task an, den der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger für einen Breakpoint ausführt. Wenn die angegebene Trefferanzahl erreicht ist und alle angegebenen Breakpointbedingungen erfüllt sind, führt der Debugger die für den Breakpoint angegebene Aktion aus.  
  
##  <a name="action-considerations"></a><a name="BKMK_ActionConsiderations"></a> Überlegungen zur Aktion  
 Die Standardaktion für einen Breakpoint besteht darin, die Ausführung zu unterbrechen, wenn die Trefferanzahl- und die Breakpointbedingung erfüllt sind. Der primäre Zweck einer **Bei Treffer** -Aktion im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger ist es hingegen, durch Angeben einer Ausgabemeldung Informationen in das Debuggerausgabefenster **auszugeben**.  
  
 Ausgabemeldungen werden mit der Option **Meldung drucken** festgelegt und als Textzeichenfolge angegeben, die Ausdrücke mit Informationen aus dem zu debuggenden [!INCLUDE[tsql](../../includes/tsql-md.md)] enthalten. Mögliche Ausdrücke:  
  
-   Ein [!INCLUDE[tsql](../../includes/tsql-md.md)]-Ausdruck in geschweiften Klammern ({}). Die Ausdrücke können [!INCLUDE[tsql](../../includes/tsql-md.md)] -Variablen, -Parameter und integrierte Funktionen enthalten. Beispiele hierfür sind {@MyVariable}, {@NameParameter}, {@@SPID} oder {SERVERPROPERTY('ProcessID')}.  
  
-   Eines der folgenden Schlüsselwörter:  
  
    1.  $ADDRESS gibt den Namen der gespeicherten Prozedur oder benutzerdefinierten Funktion zurück, in der der Breakpoint festgelegt ist. Wenn der Breakpoint im Editorfenster festgelegt wird, gibt $ADDRESS den Namen der Skriptdatei zurück, die bearbeitet wird. $ADDRESS und $FUNCTION geben im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger die gleichen Informationen zurück.  
  
    2.  $CALLER gibt den Namen der Einheit des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Codes zurück, in der eine gespeicherte Prozedur oder eine Funktion aufgerufen wurde. Wenn sich der Breakpoint im Editor Fenster befindet, wird $Caller zurückgegeben \<No caller available> . Wenn sich der Breakpoint in einer gespeicherten Prozedur oder benutzerdefinierten Funktion befindet, die vom Code im Editorfenster aufgerufen wird, gibt $CALLER den Namen der Datei zurück, die bearbeitet wird. Wenn sich der Breakpoint in einer gespeicherten Prozedur oder benutzerdefinierten Funktion befindet, die von einer anderen gespeicherten Prozedur oder Funktion aufgerufen wird, gibt $CALLER den Namen der aufrufenden Prozedur bzw. Funktion zurück.  
  
    3.  $CALLSTACK gibt die Aufrufliste von Funktionen in der Kette zurück, die die aktuelle gespeicherte Prozedur oder benutzerdefinierte Funktion aufgerufen haben. Wenn sich der Breakpoint im Editorfenster befindet, gibt $CALLSTACK den Namen der Skriptdatei zurück, die bearbeitet wird.  
  
    4.  $FUNCTION gibt den Namen der gespeicherten Prozedur oder benutzerdefinierten Funktion zurück, in der der Breakpoint festgelegt ist. Wenn der Breakpoint im Editorfenster festgelegt wird, gibt $FUNCTION den Namen der Skriptdatei zurück, die bearbeitet wird.  
  
    5.  $PID und $PNAME geben die ID und den Namen des Betriebssystemprozesses zurück, der die Instanz der Datenbank-Engine ausführt, in der das [!INCLUDE[tsql](../../includes/tsql-md.md)] ausgeführt wird. $PID gibt die gleiche ID wie SERVERPROPERTY('ProcessID') zurück, jedoch ist $PID ein Hexadezimalwert, während SERVERPROPERTY('ProcessID') ein Dezimalwert ist.  
  
    6.  $TID und $TNAME geben die ID und den Namen des Betriebssystemthreads zurück, der den [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batch ausführt. Der Thread ist dem Prozess zugeordnet, der die Instanz der Datenbank-Engine ausführt. $TID gibt den gleichen Wert wie SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID zurück, mit dem einzigen Unterschied, dass $TID ein Hexadezimalwert und kpid ein Dezimalwert ist.  
  
-   Sie können auch den umgekehrten Schrägstrich (\\) als Escapezeichen verwenden, um geschweifte Klammern und umgekehrte Schrägstriche in der Meldung zuzulassen: \\{, \\} und \\\\.  
  
#### <a name="to-specify-a-when-hit-action"></a>So geben Sie eine Bei Treffer-Aktion an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bei Treffer** .  
  
     Oder  
  
     Klicken Sie im **Breakpointfenster** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bei Treffer** .  
  
2.  Wählen Sie im Dialogfeld **Beim Erreichen eines Haltepunktes** das gewünschte Verhalten aus:  
  
    1.  Wählen Sie **Meldung drucken** aus, um im Debuggerausgabefenster eine Meldung auszugeben, wenn der Breakpoint erreicht wird.  
  
    2.  Die Option **Makro ausführen** ist im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger nicht verfügbar und wird abgeblendet dargestellt.  
  
    3.  Wählen Sie **Ausführung fortsetzen** aus, wenn die Ausführung nicht am Breakpoint unterbrochen werden soll. Diese Option ist nur aktiviert, wenn Sie die Option **Meldung drucken** ausgewählt haben.  
  
3.  Klicken Sie auf **OK** , um die Änderungen zu implementieren, oder auf **Abbrechen** , um den Vorgang zu beenden, ohne die Änderungen zu übernehmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben einer Breakpointbedingung](specify-a-breakpoint-condition.md)   
 [Angeben einer Trefferanzahl](specify-a-hit-count.md)  
