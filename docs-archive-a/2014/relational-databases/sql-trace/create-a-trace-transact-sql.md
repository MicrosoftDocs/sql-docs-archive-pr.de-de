---
title: Erstellen einer Ablaufverfolgung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], example
- traces [SQL Server], creating
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 35644891b2dca8359d6dc68fbddb67288d241cb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619049"
---
# <a name="create-a-trace-transact-sql"></a>Erstellen einer Ablaufverfolgung (Transact-SQL)
  In diesem Thema werden Vorgehensweisen zum Verwenden gespeicherter Prozeduren zum Erstellen einer Ablaufverfolgung beschrieben.  
  
### <a name="to-create-a-trace"></a>So erstellen Sie eine Ablaufverfolgung  
  
1.  Führen Sie **sp_trace_create** mit den notwendigen Parametern aus, um eine neue Ablaufverfolgung zu erstellen. Der Status der neuen Ablaufverfolgung besagt, dass sie beendet ist (*Status* ist **0**).  
  
2.  Führen Sie **sp_trace_setevent** mit den notwendigen Parametern aus, um die zu verfolgenden Ereignisse und Spalten auszuwählen.  
  
3.  Führen Sie wahlweise **sp_trace_setfilter** aus, um beliebige Filter oder eine Kombination aus Filtern festzulegen.  
  
     **sp_trace_setevent** und **sp_trace_setfilter** können nur für vorhandene, beendete Ablaufverfolgungen ausgeführt werden.  
  
    > [!IMPORTANT]  
    >  Im Gegensatz zu regulären gespeicherten Prozeduren werden die Parameter für alle gespeicherten Prozeduren von SQL Server Profiler (<strong>sp_trace_*xx*</strong>) genau eingegeben und unterstützen die automatische Datentypkonvertierung nicht. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird das Erstellen einer Ablaufverfolgung mit [!INCLUDE[tsql](../../includes/tsql-md.md)]veranschaulicht. Der Code ist in drei Abschnitte unterteilt: Erstellen der Ablaufverfolgung, Auffüllen der Ablaufverfolgungsdatei und Beenden der Ablaufverfolgung. Passen Sie die Ablaufverfolgung an, indem Sie die Ereignisse hinzufügen, die Sie aufzeichnen möchten. Die Liste der Ereignisse und Spalten finden Sie unter [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)veranschaulicht.  
  
 Mit dem folgenden Code wird eine Ablaufverfolgung erstellt, anschließend werden dieser Ereignisse hinzugefügt, und sie wird gestartet.  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## <a name="example"></a>Beispiel  
 Nachdem nun die Ablaufverfolgung erstellt und gestartet worden ist, führen Sie den folgenden Code aus, um die Ablaufverfolgung mit Aktivität aufzufüllen.  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## <a name="example"></a>Beispiel  
 Die Ablaufverfolgung kann jederzeit beendet und neu gestartet werden. Führen Sie in diesem Beispiel den folgenden Code aus, um die Ablaufverfolgung zu beenden und zu schließen und die Ablaufverfolgungsdefinition zu löschen.  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## <a name="example"></a>Beispiel  
 Öffnen Sie zum Untersuchen der Ablaufverfolgungsdatei die Datei SampleTrace.trc mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)   
 [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)  
  
  
