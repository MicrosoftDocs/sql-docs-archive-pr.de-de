---
title: Wiedergabe Optionen (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
- health monitor [SQL Server]
- Replay Configuration dialog box
ms.assetid: 58761a25-a84f-4a90-9c61-97700bc5ad9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 695a1431145813f0a7829626a380e510d0e602e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722057"
---
# <a name="replay-options-sql-server-profiler"></a>Wiedergabeoptionen (SQL Server Profiler)
  Vor der Wiedergabe einer aufgezeichneten Ablaufverfolgung mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie im Dialogfeld **Wiedergabekonfiguration** Wiedergabeoptionen festlegen. Um dieses Dialogfeld zu starten, öffnen Sie die Datei oder Tabelle für die Ablaufverfolgungswiedergabe in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], und klicken Sie im Menü **Wiedergeben** auf **Starten**. Informationen zu den Berechtigungen, die zum Wiedergeben einer Ablaufverfolgung erforderlich sind, finden Sie unter [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).  
  
 In diesem Thema werden die im Dialogfeld **Wiedergabekonfiguration** angegebenen Optionen beschrieben.  
  
> [!NOTE]  
>  Es empfiehlt sich, zum Wiedergeben einer intensiven OLTP-Anwendung das Distributed Replay Utility (mit zahlreichen aktiven gleichzeitigen Verbindungen oder hohem Durchsatz) zu verwenden. Mit dem Distributed Replay Utility können Sie Ablaufverfolgungsdaten von mehreren Computern wiedergeben, um unternehmenswichtige Arbeitsauslastungen besser zu simulieren. Weitere Informationen finden Sie unter [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).  
  
## <a name="basic-replay-options"></a>Grundlegende Wiedergabeoptionen  
 **Wiedergabeserver**  
 Der Server ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die Sie die Ablaufverfolgung wiedergeben möchten. Der Server muss die unter [Replay Requirements](replay-requirements.md)beschriebenen Anforderungen für die Wiedergabe erfüllen.  
  
 **In Datei speichern**  
 Die Ausgabedatei, in die das Ergebnis aus der Wiedergabe der Ablaufverfolgung geschrieben wird, das zu einem späteren Zeitpunkt angezeigt werden kann. Standardmäßig zeigt [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die Ergebnisse der Wiedergabe der Ablaufverfolgung nur auf dem Bildschirm an.  
  
 **In Tabelle speichern**  
 Die Datenbanktabelle, in die das Ergebnis aus der Wiedergabe der Ablaufverfolgung geschrieben wird, das zu einem späteren Zeitpunkt angezeigt werden kann.  
  
 **Anzahl von Wiedergabethreads**  
 Gibt die Anzahl der Threads an, die gleichzeitig verwendet werden können. Bei einem höheren Wert werden während der Wiedergabe mehr Ressourcen verbraucht, aber die Wiedergabe ist schneller. Die Ereignisreihenfolge wird nicht vollständig beibehalten, wenn mehrere Threads verwendet werden.  
  
 **Ereignisse in der Reihenfolge wiedergeben, in der ihr Ablauf verfolgt wurde**  
 Hiermit können Sie Debugmethoden, wie das Durchlaufen der einzelnen Ablaufverfolgungen, verwenden. Wenn diese Option nicht ausgewählt ist, wird bei der Wiedergabe nicht sichergestellt, dass die Ereignisse in der Reihenfolge, in der sie ursprünglich aufgezeichnet wurden, wiedergegeben werden.  
  
 **Ereignisse mithilfe mehrerer Threads wiedergeben**  
 Optimiert die Leistung und deaktiviert das Debuggen. Die Ereignisse werden in der Reihenfolge wiedergegeben, in der sie für eine bestimmte Serverprozess-ID (SPID) aufgezeichnet wurden, aber die Reihenfolge der SPIDs ist nicht sichergestellt.  
  
 **Wiedergabeergebnisse anzeigen**  
 Hiermit wird das Ergebnis der Wiedergabe angezeigt. Dies ist die Standardoption. Wenn die wiedergegebene Ablaufverfolgung sehr groß ist, sollten Sie diese Option eventuell deaktivieren, um Datenträgerspeicher zu sparen.  
  
> [!NOTE]  
>  Für eine optimale Wiedergabeleistung wird empfohlen, Ereignisse mithilfe mehrerer Threads wiederzugeben und die Wiedergabeergebnisse nicht anzuzeigen.  
  
## <a name="advanced-replay-options"></a>Erweiterte Wiedergabeoptionen  
 **System-SPIDs wiedergeben**  
 Alle System-SPIDs wiedergeben. Dies ist die Standardoption.  
  
 **Nur eine SPID wiedergeben**  
 Gibt die SPID-Nummer wieder, die Sie aus der Liste auswählen.  
  
 **Wiedergabe nach Datum und Zeit beschränken**  
 Gibt die Ablaufverfolgung für die angegebene **Startzeit** und **Beendigungszeit**wieder.  
  
 **Wartezeit für Systemüberwachung**  
 Legt fest, wie lange ein Prozess ausgeführt werden kann, bevor die Systemüberwachung beendet wird.  
  
 **Abrufintervall für Systemüberwachung**  
 Legt fest, wie oft die Systemüberwachung die Kandidaten wegen der Beendigung abruft.  
  
 **Überwachung blockierter SQL Server-Prozesse aktivieren**  
 Legt fest, wie oft die Überwachung blockierter Prozesse nach blockierten oder blockierenden Prozessen sucht.  
  
## <a name="about-the-health-monitor"></a>Informationen zur Systemüberwachung  
 Die Systemüberwachung ist ein Anwendungsthread, der die simulierten Prozesse bei der Wiedergabe einer Ablaufverfolgung überwacht und jene Prozesse beendet, die bei der Wiedergabe blockiert sind. Auf der Registerkarte **Erweiterte Wiedergabeoptionen** des Dialogfelds **Wiedergabekonfiguration** können Sie angeben, nach wie vielen Sekunden die Systemüberwachung einen blockierten Prozess beenden soll (**Wartezeit für Systemüberwachung**). Wenn Sie dieses Intervall auf 0 festlegen, werden simulierte blockierende Prozesse bei der Wiedergabe der Ablaufverfolgung niemals durch die Systemüberwachung beendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [Anforderungen für die Wiedergabe](replay-requirements.md)   
 [Überlegungen zum Wiedergeben von Ablaufverfolgungen &#40;SQL Server Profiler&#41;](considerations-for-replaying-traces-sql-server-profiler.md)  
  
  
