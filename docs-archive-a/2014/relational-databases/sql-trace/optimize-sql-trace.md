---
title: Optimieren der SQL-Ablaufverfolgung | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 831875218423bdb9106d7d84995af1e788da44db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609040"
---
# <a name="optimize-sql-trace"></a>Optimieren der SQL-Ablaufverfolgung
  Obwohl die SQL-Ablaufverfolgung die Leistung beansprucht, weil Systemressourcen zum Sammeln von Daten verwendet werden, können diese Leistungseinbußen begrenzt werden. Zum Minimieren der Leistungseinbuße durch eine Ablaufverfolgung gibt es folgende Möglichkeiten:  
  
-   Sie können auch die Eingabeaufforderung verwenden, um Ablaufverfolgungen auszuführen. Das Verwenden einer grafischen Benutzeroberfläche beeinträchtigt die Leistung. Weitere Informationen finden Sie unter [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql).  
  
-   Vermeiden Sie das Einbeziehen von Ereignissen, die häufig auftreten. Schränken Sie die Ablaufverfolgung mithilfe spezifischer Klassen und Filter ein. Durch weniger gesammelte Ablaufverfolgungsereignisse werden weniger Systemressourcen für die Unterstützung der Ablaufverfolgung benötigt.  
  
-   Fokussieren Sie die Ablaufverfolgung auf das Sammeln derjenigen Ereignisse, die relevante Daten liefern. Wenn Sie beispielsweise eine Ablaufverfolgung zum Identifizieren von Deadlocks ausführen, beziehen Sie die **Lock:Deadlock** -Ereignisklasse ein, nicht aber **Lock:Acquired** . Wenn Sie beide Ereignisklassen einbeziehen, muss von der Ablaufverfolgung auf jede angeforderte Sperre reagiert werden, was die Ausführungskosten verdoppelt.  
  
-   Vermeiden Sie das Sammeln doppelter Daten. Wenn Sie beispielsweise **SQL:BatchStarted** und **SQL:BatchCompleted**sammeln, können Sie die Größe des Ergebnissatzes durch das ausschließliche Sammeln von Textdaten für die **SQL:BatchStarted** -Ereignisklasse minimieren.  
  
-   Verwenden Sie in der Ablaufverfolgungsdefinition Filter. Wenn Sie beispielsweise wissen, dass ein bestimmter Benutzer eine langsame Ausführung während Ad-hoc-Abfragen berichtet, erstellen Sie einen Filter für **LoginName**. Richten Sie den Filter so ein, dass nur Ereignisse einbezogen werden, in denen **LoginName** mit dem Benutzernamen übereinstimmt.  
  
 Wenn Sie eine Ablaufverfolgung für Ereignisse ausführen müssen, die signifikante Auswirkungen auf die Leistung haben, können Sie mithilfe einer der folgenden Methoden den Leistungsverlust auf dem Server begrenzen:  
  
-   Führen Sie Ablaufverfolgungen für kürzere Zeitspannen durch. Sie können die Dauer der Ausführung einer Ablaufverfolgung steuern, indem Sie eine Beendigungszeit aktivieren. Dies ist besonders wichtig, wenn Sie nicht die Ereignisklassen begrenzen oder ein Ereignis filtern können. Durch das Aktivieren einer Beendigungszeit wird sichergestellt, dass der Leistungsverlust nicht unbegrenzt andauert.  
  
-   Begrenzen Sie die Größe der Ablaufverfolgungsergebnisse. Sie können die Größe der Ablaufverfolgungsergebnisse auf eine maximale Dateigröße beschränken. Durch diese Strategie wird sichergestellt, dass die Leistungseinbußen stoppen, wenn die Dateigrößengrenze erreicht wird (wenn kein Dateirollover aktiviert ist).  
  
-   Schränken Sie die Anzahl der zurückgegebenen Ereignisse ein. Mithilfe von [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] können Sie die Anzahl der zurückgegebenen Ereignisse begrenzen, indem Sie die Ablaufverfolgung in einer Tabelle speichern und die maximale Zeilenanzahl festlegen. Die Ablaufverfolgungsergebnisse werden weiterhin zum [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] -Bildschirm zurückgegeben, nachdem die maximale Zeilenanzahl erreicht wurde, aber die Kosten für das Aufzeichnen der Ergebnisse in einer Tabelle sind ausgeschaltet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filtern einer Ablaufverfolgung](../sql-trace/filter-a-trace.md)  
  
  
