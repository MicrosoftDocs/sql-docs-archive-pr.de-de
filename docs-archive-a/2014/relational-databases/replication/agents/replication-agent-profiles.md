---
title: Replikations-Agentprofile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, profiles
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- Merge Agent, profiles
- agents [SQL Server replication], profiles
- Queue Reader Agent, profiles
- profiles [SQL Server], replication agents
- Snapshot Agent, profiles
- Log Reader Agent, profiles
ms.assetid: 0e980725-e42f-4283-94cb-d8a6dba5df62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 985d6788d1a8df3ca0c6bfaa463299295ef66102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615956"
---
# <a name="replication-agent-profiles"></a>Replikations-Agent-Profile
  Wenn die Replikation konfiguriert wird, wird ein Satz Agentprofile auf dem Verteiler installiert. Ein Agentprofil enthält eine Reihe Parameter, die bei jeder Ausführung des Agents zur Anwendung kommen: Jeder Agent meldet sich während seines Startprozesses beim Verteiler an und fragt die Parameter in seinem Profil ab. Im Fall von Mergeabonnements, die die Websynchronisierung verwenden, werden Profile heruntergeladen und auf dem Verteiler gespeichert. Wenn das Profil geändert wird, wird das Profil auf dem Verteiler aktualisiert, wenn der Merge-Agent das nächste Mal ausgeführt wird. Weitere Informationen zur Websynchronisierung finden Sie unter [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md).  
  
 Die Replikation stellt ein Standardprofil für jeden Agent und zusätzliche vordefinierte Profile für den Protokolllese-Agent, den Verteilungs-Agent und den Merge-Agent bereit. Neben den bereitgestellten Profilen können Sie Profile erstellen, die sich für Ihre Anwendungsanforderungen eignen. Ein Agentprofil ermöglicht ein einfaches Ändern von Schlüsselparametern für alle Agents, die dem Profil zugeordnet sind. Wenn Sie z. B. 20 Momentaufnahme-Agents haben und den Zeittimeout für Abfragen ändern müssen (den **-QueryTimeout** -Parameter), können Sie das Profil für die Momentaufnahme-Agents aktualisieren. Beim nächsten Ausführen verwenden alle Agents dieses Typs automatisch den neuen Wert.  
  
 Sie können auch verschiedene Profile für unterschiedliche Instanzen eines Agents verwenden. Ein Merge-Agent, der beispielsweise über eine DFÜ-Verbindung mit dem Verleger und dem Verteiler verbunden wird, könnte einen Satz Parameter verwenden, die sich besser für die langsamere Kommunikationsverbindung eignen, indem er das Profil für **langsame Links** verwendet.  
  
> [!NOTE]  
>  Wenn Sie einen Wert für einen Agentparameter in der Befehlszeile angeben, überschreibt dieser Wert den Wert, der für denselben Parameter im Agentprofil festgelegt wurde.  
  
 **So verwenden und ändern Sie Agentprofile**  
  
-   [Arbeiten mit Replikations-Agent-Profilen](replication-agent-profiles.md)  
  
## <a name="snapshot-agent-profiles"></a>Profile des Momentaufnahme-Agents  
 In der folgenden Tabelle werden die Parameter aufgeführt, die im Standardprofil für den Momentaufnahme-Agent definiert sind. Weitere Informationen zu diesen Parametern finden Sie unter [Replication Snapshot Agent](replication-snapshot-agent.md).  
  
||default|  
|-|-------------|  
|**-BcpBatchSize**|100.000|  
|**-HistoryVerboseLevel**|2|  
|**-LoginTimeout**|15|  
|**-QueryTimeout**|1800|  
  
## <a name="log-reader-agent-profiles"></a>Profile des Protokolllese-Agents  
 In der folgenden Tabelle werden die Parameter aufgeführt, die in den Profilen für den Protokolllese-Agent definiert sind. Jede Spalte in der Tabelle steht für ein benanntes Profil. Weitere Informationen zu diesen Parametern finden Sie unter [Replication Log Reader Agent](replication-log-reader-agent.md).  
  
||default|Ausführlicher Verlauf|  
|-|-------------|---------------------|  
|**-HistoryVerboseLevel**|1|2|  
|**-LoginTimeout**|15|15|  
|**-LogScanThreshold**|500000|500000|  
|**-PollingInterval**|5|5|  
|**-QueryTimeout**|1800|1800|  
|**-ReadBatchSize**|500|500|  
  
## <a name="distribution-agent-profiles"></a>Profile des Verteilungs-Agents  
 In der folgenden Tabelle werden die Parameter aufgeführt, die in den Profilen für den Verteilungs-Agent definiert sind. Jede Spalte in der Tabelle steht für ein benanntes Profil. Weitere Informationen zu diesen Parametern finden Sie unter [Replication Distribution Agent](replication-distribution-agent.md).  
  
||default|Ausführlicher Verlauf|Synchronisierungsverwaltung von Windows|Fortsetzen bei Datenkonsistenzfehlern|Verteilungsprofil für das OLE DB-Streaming|  
|-|-------------|---------------------|-------------------------------------|-----------------------------------------|----------------------------------------------|  
|**-BcpBatchSize**|100.000|100.000|1000|100.000|2147473647|  
|**-CommitBatchSize**|100|100|100|100|100|  
|**-CommitBatchThreshold**|1000|1000|1000|1000|1000|  
|**-HistoryVerboseLevel**|1|2|1|1|1|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|  
|**-MaxBcpThreads**|1|1|1|1|1|  
|**-MaxDeliveredTransactions**|0|0|0|0|0|  
|**-OledbStreamThreshold**|NULL|NULL|NULL|NULL|32768|  
|**-PacketSize**|NULL|NULL|NULL|NULL|32768|  
|**-PollingInterval**|5|5|5|5|5|  
|**-QueryTimeout**|1800|1800|1800|1800|1800|  
|**-SkipErrors**|NULL|NULL|NULL|**-SkipErrors** 2601:2627:20598|NULL|  
|**-TransactionsPerHistory**|100|100|100|100|100|  
|**-UseOledbStreaming**|NULL|NULL|NULL|NULL|**-UseOledbStreaming**|  
  
## <a name="merge-agent-profiles"></a>Profile des Merge-Agents  
 In der folgenden Tabelle werden die Parameter aufgeführt, die in den Profilen für den Merge-Agent definiert sind. Jede Spalte in der Tabelle steht für ein benanntes Profil. Weitere Informationen zu diesen Parametern finden Sie unter [Replication Merge Agent](replication-merge-agent.md).  
  
||default|Ausführlicher Verlauf|Synchronisierungsverwaltung von Windows|Zeilenanzahlüberprüfung|Überprüfung der Zeilenanzahl und Prüfsumme|Langsame Links|Server-zu-Server für hohes Volumen|  
|-|-------------|---------------------|-------------------------------------|-------------------------|--------------------------------------|---------------|------------------------------------|  
|**-BcpBatchSize**|100.000|100.000|1000|100.000|100.000|100.000|100.000|  
|**-ChangesPerHistory**|100|50|50|100|100|100|1000|  
|**-DestThreads**|2|1|1|1|1|1|4|  
|**-DownloadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-DownloadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-DownloadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-FastRowCount**|1|1|1|1|1|1|1|  
|**-HistoryVerboseLevel**|2|3|1|1|2|1|2|  
|**-KeepAliveMessageInterval**|300|300|300|300|300|300|300|  
|**-LoginTimeout**|15|15|15|15|15|15|15|  
|**-MaxDownloadChanges**|0|0|0|0|0|0|0|  
|**-MaxUploadChanges**|0|0|0|0|0|0|0|  
|**-MetadataRetentionCleanup**|1|1|1|1|1|1|1|  
|**-NumDeadlockRetries**|5|5|5|5|5|5|5|  
|**-ParallelUploadDownload**|NULL|NULL|NULL|NULL|NULL|NULL|1|  
|**-PollingInterval**|60|60|60|60|60|60|60|  
|**-QueryTimeout**|300|300|300|300|300|300|600|  
|**-QueueSizeMultiplier**|NULL|NULL|NULL|NULL|NULL|NULL|5|  
|**-SrcThreads**|2|2|2|2|2|1|3|  
|**-StartQueueTimeout**|0|0|0|0|0|0|0|  
|**-UploadGenerationsPerBatch**|50|50|50|50|50|1|500|  
|**-UploadReadChangesPerBatch**|100|100|100|100|100|100|100|  
|**-UploadWriteChangesPerBatch**|100|100|100|100|100|100|100|  
|**-Validate**|0|0|0|1|3|0|0|  
|**-ValidateInterval**|60|60|60|60|60|60|60|  
  
## <a name="queue-reader-agent-profiles"></a>Profile des Warteschlangenlese-Agents  
 In der folgenden Tabelle werden die Parameter aufgeführt, die im Standardprofil für den Warteschlangenlese-Agent definiert sind. Weitere Informationen zu diesen Parametern finden Sie unter [Replication Queue Reader Agent](replication-queue-reader-agent.md).  
  
||default|  
|-|-------------|  
|**-HistoryVerboseLevel**|1|  
|**-LoginTimeout**|15|  
|**-PollingInterval**|5|  
|**-QueryTimeout**|1800|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung des Replikations-Agents](replication-agent-administration.md)   
 [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md)   
 [Ausführbare Konzepte für die Programmierung von Replikations-Agent](../concepts/replication-agent-executables-concepts.md)  
  
  
