---
title: Abrufen gespeicherter Prozeduren (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: rothja
ms.author: jroth
ms.openlocfilehash: d98d623dbbb4701bb59c95df502d0063d528d0d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617936"
---
# <a name="call-stored-procedures-odbc"></a>Aufrufen von gespeicherten Prozeduren (ODBC)
  Wenn eine SQL-Anweisung eine gespeicherte Prozedur mithilfe der ODBC-Aufruf-Escape-Klausel aufruft, sendet der Microsoft SQL Server Treiber die Prozedur mit dem RPC-Mechanismus (remote gespeicherte Prozedur Aufruf) an SQL Server. RPC-Anforderungen umgehen größtenteils das Analysieren der Anwendungen und die Parameterverarbeitung in SQL Server und sind schneller als die Transact-SQL EXECUTE-Anweisung.  
  
 Eine Beispielanwendung, die diese Funktion veranschaulicht, finden Sie unter [Verarbeiten von Rückgabe Codes und Ausgabeparametern &#40;ODBC-&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>So führen Sie eine Prozedur als RPC aus  
  
1.  Erstellen Sie eine SQL-Anweisung, die die ODBC-Escapesequenz verwendet. Die Anweisung verwendet Parametermarkierungen für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (falls zutreffend):  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Rufen Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (sofern vorhanden) auf.  
  
3.  Führen Sie die Anweisung mit [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)aus.  
  
> [!NOTE]  
>  Wenn eine Anwendung eine Prozedur mit der Transact-SQL EXECUTE-Syntax (statt mit der ODBC CALL-Escapesequenz) übermittelt, gibt der SQL Server ODBC-Treiber den Prozeduraufruf an SQL Server als SQL-Anweisung statt als RPC weiter. Darüber hinaus werden Ausgabeparameter nicht zurückgegeben, wenn die Transact SQL EXECUTE-Anweisung verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst-wie-Themen zur Ausführung gespeicherter Prozeduren &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Batch Verarbeitung von gespeicherten Prozedur aufrufen](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Gespeicherte Prozeduren](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Aufrufen einer gespeicherten Prozedur](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Vorgehensweisen](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
