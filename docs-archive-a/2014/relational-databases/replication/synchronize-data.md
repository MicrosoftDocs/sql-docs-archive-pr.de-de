---
title: Synchronisieren von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c92cc4d1ae8e836f169a731ecf3c37c81f3dbf10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701013"
---
# <a name="synchronize-data"></a>Synchronisieren von Daten
  Das Synchronisieren von Daten bezieht sich auf den Prozess des Weitergebens von Daten- und Schemaänderungen zwischen dem Verleger und Abonnenten, nachdem die Anfangsmomentaufnahme auf dem Abonnenten angewendet wurde. Die Synchronisierung kann auf verschiedene Weise ausgeführt werden:  
  
-   Fortlaufend, was typisch für die Transaktionsreplikation ist.  
  
-   Bedarfsgesteuert, was typisch für die Mergereplikation ist.  
  
-   Nach einem Zeitplan, was typisch für die Momentaufnahmereplikation ist.  
  
 Wenn ein Abonnement synchronisiert wird, werden basierend auf dem verwendeten Replikationstyp verschiedene Prozesse ausgeführt:  
  
-   Momentaufnahmereplikation. Synchronisieren bedeutet, dass der Verteilungs-Agent die Momentaufnahme erneut auf dem Abonnenten anwendet, sodass Schema und Daten in der Abonnementdatenbank mit der Veröffentlichungsdatenbank übereinstimmen.  
  
     Wenn Änderungen an den Daten oder dem Schema auf dem Verleger vorgenommen wurden, muss für die Weitergabe der Änderungen an den Abonnenten eine neue Momentaufnahme generiert werden.  
  
-   Transaktionsreplikation. Synchronisieren bedeutet, dass der Verteilungs-Agent Updates, Einfügungen, Löschungen und andere Änderungen von der Verteilungsdatenbank auf den Abonnenten überträgt.  
  
-   Mergereplikation. Synchronisieren bedeutet, dass der Merge-Agent Änderungen vom Abonnenten auf den Verleger hochlädt und dann die Änderungen vom Verleger auf den Abonnenten herunterlädt. Eventuelle Konflikte werden erkannt und gelöst. Die Daten werden konvergiert, sodass der Verleger und die Abonnenten schließlich die gleichen Datenwerte aufweisen. Wenn Konflikte erkannt und gelöst wurden, bedeutet das, dass Arbeiten, die einige der Benutzer ausgeführt haben, so geändert worden sind, dass der Konflikt entsprechend der von Ihnen definierten Richtlinien gelöst wurde.  
  
 Durch Momentaufnahmeveröffentlichungen wird das Schema auf dem Abonnenten bei jeder Synchronisierung vollständig aktualisiert, sodass alle Schemaänderungen auf den Abonnenten angewendet werden. Auch die Transaktions- und die Mergereplikation unterstützen die häufigsten Schemaänderungen. Weitere Informationen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](publish/make-schema-changes-on-publication-databases.md).  
  
 Informationen zum Synchronisieren eines Pushabonnements finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
 Informationen zum Synchronisieren eines Pullabonnements finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
 Informationen zum Festlegen von Synchronisierungszeitplänen finden Sie unter [Specify Synchronization Schedules](specify-synchronization-schedules.md).  
  
 **So zeigen Sie Synchronisierungskonflikte an und lösen Sie die Konflikte**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Anzeigen und Lösen von Datenkonflikten für Mergeveröffentlichungen &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Anzeigen von Datenkonflikten für Transaktionsveröffentlichungen &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## <a name="executing-code-during-synchronization"></a>Ausführen von Code während der Synchronisierung  
 Die Replikation unterstützt zwei Methoden zum Ausführen von Code während der Synchronisierung.  
  
-   Das bedarfsgesteuerte Ausführen von Skripts wird für die Transaktions- und die Mergereplikation unterstützt. Beim bedarfsgesteuerten Ausführen von Skripts können Sie angeben, dass ein SQL-Skript während der Synchronisierung ausgeführt wird. Das Skript wird auf den Abonnenten kopiert und mithilfe von **sqlcmd** am Anfang des Synchronisierungsvorgangs ausgeführt. Das Skript hat keinen Zugriff auf die replizierten Änderungen, wenn diese auf den Abonnenten angewendet werden. Weitere Informationen finden Sie unter [Ausführen von Skripts während der Synchronisierung &#40;Replikationsprogrammierung mit Transact-SQL&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Geschäftslogikhandler werden für die Mergereplikation unterstützt. Das Geschäftslogikhandler-Framework ermöglicht es Ihnen, eine verwaltete Codeassembly zu schreiben, die während der Mergesynchronisierung aufgerufen wird. Die Assembly enthält Geschäftslogik, die auf viele Bedingungen während der Synchronisierung reagieren kann: Datenänderungen, Konflikte und Fehler. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](merge/execute-business-logic-during-merge-synchronization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erkennen und Auflösen von Konflikten bei der Mergereplikation](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
