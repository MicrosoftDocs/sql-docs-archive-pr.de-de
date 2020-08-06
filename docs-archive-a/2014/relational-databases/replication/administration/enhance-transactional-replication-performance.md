---
title: Verbessern der Leistung der Transaktionsreplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725553"
---
# <a name="enhance-transactional-replication-performance"></a>Verbessern der Leistung der Transaktionsreplikation
  Ziehen Sie nach der Erwägung der allgemeinen Leistungstipps, die unter [Enhancing General Replication Performance](enhance-general-replication-performance.md)aufgeführt sind, auch die nachfolgenden Aspekte, die sich speziell auf die Transaktionsreplikation beziehen, in Betracht.  
  
## <a name="database-design"></a>Datenbankentwurf  
  
-   Minimieren Sie den Transaktionsumfang in Ihrem Datenbankentwurf.  
  
     Standardmäßig werden bei der Transaktionsreplikation Änderungen gemäß den Transaktionsgrenzen weitergegeben. Bei Transaktionen geringeren Umfangs ist die Wahrscheinlichkeit geringer, dass der Verteilungs-Agent Transaktionen aufgrund von Netzwerkproblemen erneut übermitteln muss. Wenn der Agent eine Transaktion erneut übermitteln muss, ist der Umfang der gesendeten Daten geringer.  
  
## <a name="distributor-configuration"></a>Konfiguration des Verteilers  
  
-   Konfigurieren Sie den Verteiler auf einem dedizierten Server.  
  
     Durch die Konfiguration eines Remoteverteilers kann der Verarbeitungsaufwand auf dem Verleger reduziert werden. Weitere Informationen finden Sie unter [Configure Distribution](../configure-distribution.md).  
  
-   Richten Sie eine angemessene Größe für die Verteilungsdatenbank ein.  
  
     Testen Sie die Replikation unter der typischen Auslastung des Systems, um den Speicherbedarf für Befehle zu ermitteln. Stellen Sie sicher, dass die Datenbank ausreichend Speicherkapazität für Befehle aufweist, um die häufige automatische Vergrößerung zu verhindern. Weitere Informationen zum Ändern der Größe einer Datenbank finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="publication-design"></a>Veröffentlichungsentwurf  
  
-   Replizieren Sie die Ausführung gespeicherter Prozeduren bei der Ausführung von Batchupdates für veröffentlichte Tabellen.  
  
     Wenn Batchupdates vorhanden sind, die gelegentlich eine große Anzahl von Zeilen auf dem Abonnenten betreffen, sollten Sie in Erwägung ziehen, die veröffentlichte Tabelle mithilfe einer gespeicherten Prozedur zu aktualisieren und die Ausführung der gespeicherten Prozedur zu veröffentlichen. Statt ein Update zu übermitteln oder jede betroffene Zeile zu löschen, führt der Verteilungs-Agent dieselbe Prozedur auf dem Abonnenten mit denselben Parameterwerten auf. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Verteilen Sie Artikel auf mehrere Veröffentlichungen.  
  
     Wenn die Verwendung des weiter unten erläuterten **-SubscriptionStreams** -Parameters nicht möglich ist, ziehen Sie die Erstellung mehrerer Veröffentlichungen in Betracht. Durch das Verteilen von Artikeln auf diese Veröffentlichungen können bei der Replikation Änderungen parallel auf Abonnenten angewendet werden.  
  
## <a name="subscription-considerations"></a>Überlegungen zu Abonnements  
  
-   Wenn Sie auf einem einzigen Verleger über mehrere Veröffentlichungen verfügen, verwenden Sie unabhängige Agents anstelle freigegebener Agents (dies ist die Standardeinstellung im Assistenten für neue Veröffentlichung).  
  
-   Führen Sie Agents fortlaufend statt häufig aus.  
  
     Wenn Sie die Agents für die fortlaufende Ausführung konfigurieren, statt Zeitpläne für die häufige Ausführung (z. B. jede Minute) zu erstellen, führt dies zu einer verbesserten Leistung der Replikation, da der jeweilige Agent nicht gestartet und beendet werden muss. Wenn Sie für den Verteilungs-Agent die fortlaufende Ausführung festlegen, erfolgt die Propagierung von Änderungen auf andere Server, mit denen in der Topologie eine Verbindung besteht, mit geringer Latenzzeit. Weitere Informationen finden Sie unter  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [Angeben von Synchronisierungszeitplänen](../specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Parameter für den Verteilungs-Agent und Protokolllese-Agent  
  
-   Um versehentliche, einmalige Engpässe aufzulösen, verwenden Sie den **-MaxCmdsInTran-** Parameter für die Protokolllese-Agent.  
  
     Der **-MaxCmdsInTran-** Parameter gibt die maximale Anzahl von Anweisungen an, die in einer Transaktion gruppiert werden, wenn der Protokoll Leser Befehle in die Verteilungs Datenbank schreibt. Mithilfe dieses Parameters können der Protokolllese-Agent und der Verteilungs-Agent beim Anwenden von Befehlen auf dem Abonnenten umfangreiche Transaktionen (die aus zahlreichen Befehlen bestehen) auf dem Verleger in mehrere kleinere Transaktionen aufteilen. Durch die Angabe dieses Parameters kommt es auf dem Verteiler möglicherweise zu weniger Konflikten, und die Latenzzeit zwischen Verleger und Abonnent kann reduziert werden. Da die ursprüngliche Transaktion in kleineren Einheiten angewendet wird, kann der Abonnent vor Ende der ursprünglichen Transaktion auf Zeilen einer umfangreichen logischen Verleger-Transaktion zugreifen; dies widerspricht der strikten Unteilbarkeit von Transaktionen. **0**ist der Standardwert, durch den die Transaktionsgrenzen des Verlegers beibehalten werden. Dieser Parameter gilt nicht für Oracle-Verleger.  
  
    > [!WARNING]  
    >  `MaxCmdsInTran` ist nicht auf die dauerhafte Aktivierung ausgelegt. Der Parameter ist als Umgehungslösung für den Fall konzipiert, dass versehentlich eine große Anzahl von DML-Vorgängen in einer einzelnen Transaktion ausgeführt wird (was zu einer verzögerten Verteilung der Befehle führen kann, bis sich die gesamte Transaktion in der Verteilungsdatenbank befindet, Sperren aufrecht erhalten werden usw.). Wenn diese Situation häufiger auftritt, sollten Sie Ihre Anwendungen überarbeiten und nach Möglichkeiten suchen, die Transaktionsgröße zu verringern.  
  
-   Verwenden Sie den Parameter " **-abonneptionstreams** " für die Verteilungs-Agent.  
  
     Der Parameter " **-abonneptionstreams** " kann den Aggregat Replikations Durchsatz erheblich verbessern. Er ermöglicht es mehreren Verbindungen mit dem Abonnenten, Batches für Änderungen parallel anzuwenden und eine Vielzahl der Transaktionseigenschaften beizubehalten, die bei Verwendung eines Singlethreads vorhanden waren. Wenn eine der Verbindungen oder ein Commit hierfür nicht ausgeführt werden kann, wird der aktuelle Batch von allen Verbindungen verworfen, und der Agent versucht mithilfe eines einzigen Datenstroms, die fehlgeschlagenen Batches zu wiederholen. Vor dem Abschluss dieser Wiederholungsphase kann es auf dem Abonnenten vorübergehend zur Transaktionsinkonsistenzen kommen. Nach dem erfolgreichen Ausführen (Commit) der fehlgeschlagenen Batches wird der Abonnent wieder in einen Zustand der Transaktionskonsistenz versetzt.  
  
     Ein Wert für diesen Agentparameter kann mithilfe der Abonnement Daten ** \@ Ströme** von [sp_addsubscription &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)angegeben werden.  
  
-   Erhöhen Sie den Wert des **-ReadBatchSize** -Parameters für den Protokolllese-Agent.  
  
     Der Protokolllese- und der Verteilungs-Agent unterstützen Batchgrößen für Transaktionslese- und Commitoperationen. Die Batchgrößen werden standardmäßig auf 500 Transaktionen festgelegt. Der Protokolllese-Agent liest die angegebene Anzahl von Transaktionen aus dem Protokoll, unabhängig davon, ob sie für die Replikation markiert wurden. Wenn eine große Anzahl von Transaktionen in eine Veröffentlichungsdatenbank geschrieben werden, aber nur ein kleiner Teil dieser Transaktionen für die Replikation markiert wurde, sollten Sie mit dem **-ReadBatchSize** -Parameter die Lesebatchgröße des Protokolllese-Agents steigern. Dieser Parameter gilt nicht für Oracle-Verleger.  
  
-   Erhöhen Sie den Wert des **-CommitBatchSize** -Parameters für den Verteilungs-Agent.  
  
     Das Ausführen (Commit) eines Satzes an Transaktionen führt zu einem bestimmten Verwaltungsaufwand; wenn eine größere Anzahl an Transaktionen mit größerem Zeitabstand ausgeführt werden (Commit), verteilt sich der Verwaltungsaufwand auf einen größeren Datenumfang. Der Vorteil des Verringerns dieses Parameters wird geringer, wenn die Kosten der Anwendung von Änderungen durch andere Faktoren beeinträchtigt werden, beispielsweise der maximalen E/A des Datenträgers, auf dem das Protokoll enthalten ist. Zudem muss folgende Austauschbeziehung beachtet werden: Durch jeden Fehler, der dazu führt, dass der Verteilungs-Agent von vorn beginnt, muss für eine größere Anzahl an Transaktionen ein Rollback ausgeführt sowie die erneute Anwendung vorgenommen werden. Bei unzuverlässigen Netzwerken kann ein geringerer Wert zu weniger Fehler führen, und im Falle eines Fehlers muss das Rollback bzw. die erneute Anwendung für eine geringere Anzahl an Transaktionen ausgeführt werden.  
  
-   Verringern Sie den Wert des **-PollingInterval** -Parameters für den Protokolllese-Agent.  
  
     Über den **-PollingInterval** -Parameter wird angegeben, wie oft das Transaktionsprotokoll einer veröffentlichten Datenbank hinsichtlich Transaktionen für die Replikation abgefragt wird. Die Standardeinstellung ist 5 Sekunden. Wenn Sie diesen Wert verringern, wird das Protokoll häufiger abgefragt. Dies kann zu einer geringeren Latenzzeit bei der Übermittlung von Transaktionen von der Veröffentlichungsdatenbank an die Verteilungsdatenbank führen. Sie sollten jedoch um ein Gleichgewicht zwischen einer geringeren Latenzzeit und der erhöhten Last auf dem Server durch häufigeres Abfragen bemüht sein.  
  
 Agentparameter können in den Agentprofilen und in der Befehlszeile angegeben werden. Weitere Informationen finden Sie unter  
  
-   [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md)  
  
-   [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [Ausführbare Konzepte für die Programmierung von Replikations-Agent](../concepts/replication-agent-executables-concepts.md)  
  
  
