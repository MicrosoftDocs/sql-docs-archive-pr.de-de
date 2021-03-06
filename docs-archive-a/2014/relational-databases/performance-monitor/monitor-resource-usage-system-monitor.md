---
title: Überwachen der Ressourcenverwendung (Systemmonitor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], resource usage
- System Monitor [SQL Server], about Windows System Monitor
- resource usage monitoring [SQL Server]
- System Monitor [SQL Server]
- counters [SQL Server], resource usage subjects
- performance counters [SQL Server], resource usage subjects
- Windows System Monitor [SQL Server], about Windows System Monitor
- monitoring [SQL Server], server resource usage
- monitoring resource usage [SQL Server]
- Windows System Monitor [SQL Server]
- database monitoring [SQL Server], resource usage
- database performance [SQL Server], resource usage
- tuning databases [SQL Server], resource usage
- server performance [SQL Server], resource usage
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d691091a41e3161c733902824bf439b6788cc4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622043"
---
# <a name="monitor-resource-usage-system-monitor"></a>Überwachen der Ressourcenverwendung (Systemmonitor)
  Wenn Sie das Microsoft Windows-Serverbetriebssystem ausführen, können Sie das grafische Tool Systemmonitor verwenden, um die Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu messen. Es ist möglich, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte, Leistungsindikatoren und das Verhalten anderer Objekte anzuzeigen, wie z. B. Prozessoren, Arbeitsspeicher, Cache, Threads und Prozesse. Jedes dieser Objekte verfügt über eine zugeordnete Gruppe von Leistungsindikatoren, durch die die Geräteverwendung, Länge von Warteschlangen, Wartezeiten sowie andere Indikatoren für den Durchsatz und die interne Auslastung ermittelt werden können.  
  
> [!NOTE]  
>  Der Systemmonitor wurde nach Windows NT 4.0 grundlegend aktualisiert.  
  
## <a name="benefits-of-system-monitor"></a>Vorteile des Systemmonitors  
 Der Systemmonitor kann dazu genutzt werden, die Leistungsindikatoren des Windows-Betriebssystems und von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gleichzeitig zu überwachen, um Zusammenhänge zwischen der Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows zu ermitteln. Wenn Sie beispielsweise die Datenträger-E/A-Leistungsindikatoren von Windows und die Leistungsindikatoren des Puffer-Managers von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gleichzeitig überwachen, können Sie sich einen Überblick über das Verhalten des gesamten Systems verschaffen.  
  
 Mit dem Systemmonitor können Sie Statistiken über die aktuelle Aktivität und Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abrufen. Der Systemmonitor ermöglicht Folgendes:  
  
-   Gleichzeitiges Anzeigen von Daten einer beliebigen Anzahl von Computern  
  
-   Anzeigen und Ändern von Diagrammen, um die aktuelle Aktivität wiederzugeben, sowie Anzeigen von Leistungsindikatorwerten, die in der vom Benutzer definierten Häufigkeit aktualisiert werden  
  
-   Exportieren von Daten aus Diagrammen, Protokollen, Warnungsprotokollen und Berichten in Tabellen- oder Datenbankanwendungen, um sie weiter zu bearbeiten oder zu drucken  
  
-   Hinzufügen von Systemwarnungen, die ein Ereignis im Warnungsprotokoll einfügen und über die Sie durch das Ausgeben einer Netzwerkwarnung benachrichtigt werden können  
  
-   Ausführen einer vordefinierten Anwendung, wenn ein Leistungsindikatorwert zum ersten Mal einen benutzerdefinierten Wert über- bzw. unterschreitet oder jedes Mal, wenn dies geschieht  
  
-   Erstellen von Protokolldateien, die Daten über verschiedene Objekte von unterschiedlichen Computern enthalten  
  
-   Anfügen von ausgewählten Abschnitten aus anderen bestehenden Protokolldateien an eine Datei, um ein Langzeitarchiv zu erstellen  
  
-   Anzeigen von aktuellen Aktivitätsberichten oder Erstellen von Berichten anhand bestehender Protokolldateien  
  
-   Sichern von einzelnen Diagramm-, Warnungs-, Protokoll- oder Berichtseinstellungen oder der gesamten Einrichtung des Arbeitsbereichs für die spätere Wiederverwendung  
  
    > [!NOTE]  
    >  Ab Windows NT 4.0 wurde der Leistungsindikator durch den Systemmonitor ersetzt. Diese Tasks können Sie mit dem Systemmonitor oder mit dem Leistungsindikator ausführen.  
  
## <a name="system-monitor-performance"></a>Leistung des Systemmonitors  
 Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Betriebssystem Microsoft Windows überwachen, um Leistungsprobleme näher zu untersuchen, sollten Sie sich dabei zunächst auf drei Hauptbereiche konzentrieren:  
  
-   Datenträgeraktivität  
  
-   Prozessorauslastung  
  
-   Speicherauslastung  
  
 Die Überwachung eines Computers, auf dem der Systemmonitor ausgeführt wird, kann die Computerleistung geringfügig beeinträchtigen. Sie sollten deshalb die Daten des Systemmonitors auf einem anderen Datenträger oder einem anderen Computer protokollieren, damit die Auswirkungen auf den überwachten Computer reduziert werden. Oder führen Sie den Systemmonitor von einem Remotecomputer aus. Darüber hinaus sollten Sie nur die Leistungsindikatoren überwachen, an denen Sie interessiert sind. Wenn Sie zu viele Leistungsindikatoren überwachen, wird der Überwachungsprozess um den Verwaltungsaufwand der Ressourcenverwendung erhöht und die Leistung des überwachten Computers beeinträchtigt.  
  
## <a name="system-monitor-tasks"></a>Tasks des Systemmonitors  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt die Verwendung des Systemmonitors und erläutert den Leistungsaufwand beim Einsatz des Systemmonitors.|[Ausführen des Systemmonitors](run-system-monitor.md)|  
|Beschreibt die Überwachung der Leistungsindikatoren eines Datenträgers zur Ermittlung der Datenträgeraktivität und der Menge von E/A, die von den SQL Server-Komponenten generiert wird.|[Überwachen der Datenträgerverwendung](monitor-disk-usage.md)|  
|Beschreibt die Überwachung einer Instanz von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Feststellung, ob sich die CPU-Nutzungsraten im Normalbereich bewegen.|[Überwachen der CPU-Auslastung](monitor-cpu-usage.md)|  
|Beschreibt die Überwachung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Bestätigung einer Speicherauslastung im normalen Bereich.|[Überwachen der Speicherauslastung](monitor-memory-usage.md)|  
|Beschreibt das Erstellen einer Warnung, die ausgelöst wird, sobald ein Schwellenwert für einen Leistungsindikator des Systemmonitors erreicht wird.|[Erstellen einer SQL Server-Datenbankwarnung](create-a-sql-server-database-alert.md)|  
|Beschreibt das Erstellen von Diagrammen, Warnungen, Protokollen und Berichten für die Überwachung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Erstellen von Diagrammen, Warnungen, Protokollen und Berichten](create-charts-alerts-logs-and-reports.md)|  
|Führt Objekte und Leistungsindikatoren auf, die der Systemmonitor zur Überwachung der Aktivität von Computern, die eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausführen, nutzt.|[Verwenden von SQL Server-Objekten](use-sql-server-objects.md)|  
|Enthält eine Liste der Objekte und Leistungsindikatoren, die vom Systemmonitor zur Überwachung von In-Memory OLTP-Aktivitäten verwendet werden.|[XTP-&#40;in-Memory-OLTP&#41; Leistungsindikatoren](../../integration-services/performance/performance-counters.md)|  
  
  
