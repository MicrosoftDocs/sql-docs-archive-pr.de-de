---
title: Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- merge replication precomputed partitions [SQL Server replication]
- merge replication precomputed partitions [SQL Server replication], about precomputed partitions
ms.assetid: 85654bf4-e25f-4f04-8e34-bbbd738d60fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ad0a33f0a5951256ff94bc78e7f09a88c05f227
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724518"
---
# <a name="optimize-parameterized-filter-performance-with-precomputed-partitions"></a>Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen
  Vorausberechnete Partitionen dienen der Leistungsoptimierung und können mit gefilterten Mergeveröffentlichungen verwendet werden. Vorausberechnete Partitionen sind darüber hinaus eine Anforderung für die Verwendung logischer Datensätze bei gefilterten Veröffentlichungen. Weitere Informationen zu logischen Datensätzen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](group-changes-to-related-rows-with-logical-records.md).  
  
 Wenn ein Abonnement eine Synchronisierung mit einem Verleger ausführt, muss der Verleger die Filter des Abonnenten auswerten. Dabei werden die Zeilen ermittelt, die zu dieser Abonnentenpartition oder zum Dataset gehören. Dieses Ermitteln der Partitionsmitgliedschaft von Änderungen auf dem Verleger für jeden Abonnenten, der ein gefiltertes Dataset erhält, wird *Partitionsauswertung*genannt. Ohne vorausberechnete Partitionen muss die Partitionsauswertung für jede Änderung an einer gefilterten Spalte ausgeführt werden, die auf dem Verleger vorgenommen wurde, seit der Merge-Agent zuletzt für einen bestimmten Abonnenten ausgeführt wurde. Außerdem muss dieser Vorgang dann für jeden Abonnenten wiederholt werden, der eine Synchronisierung mit dem Verleger ausführt.  
  
 Wenn der Verleger und der Abonnent jedoch unter [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder einer höheren Version ausgeführt werden und Sie Voraus berechnete Partitionen verwenden, wird die Partitions Mitgliedschaft für alle Änderungen auf dem Verleger voraus berechnet und zum Zeitpunkt der Änderungen beibehalten. Als Folge kann ein Abonnent beim Synchronisieren mit dem Verleger sofort mit dem Download von Änderungen beginnen, die seine Partition betreffen, ohne die Partitionsauswertung durchlaufen zu müssen. Das kann zu einer erheblichen Verbesserung der Leistung führen, wenn eine Veröffentlichung eine große Zahl von Änderungen, Abonnenten oder Artikeln aufweist.  
  
 Neben dem Verwenden von vordefinierten Partitionen generieren Sie vorab Momentaufnahmen und/oder ermöglichen Abonnenten das Anfordern der Momentaufnahmegenerierung und -anwendung beim ersten Synchronisieren. Verwenden Sie eine oder beide dieser Optionen, um Momentaufnahmen für Veröffentlichungen bereitzustellen, die parametrisierte Filter verwenden. Wenn Sie keine dieser beiden Optionen angeben, werden die Abonnements mit einer Reihe von SELECT- und INSERT-Anweisungen statt mit dem **bcp** -Hilfsprogramm initialisiert, wodurch sich der Prozess deutlich verlangsamt. Weitere Informationen finden Sie unter [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 **So verwenden Sie vorausberechnete Partitionen**  
  
 Vorausberechnete Partitionen werden standardmäßig für alle neuen und vorhandenen Veröffentlichungen aktiviert, die den oben beschriebenen Richtlinien folgen. Die Einstellung kann mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder programmgesteuert geändert werden. Weitere Informationen finden Sie unter [Optimize Parameterized Row Filters](../publish/optimize-parameterized-row-filters.md).  
  
## <a name="requirements-for-using-precomputed-partitions"></a>Anforderungen für die Verwendung vorausberechneter Partitionen  
 Wenn die folgenden Anforderungen erfüllt sind, werden neue Mergeveröffentlichungen standardmäßig mit vorausberechneten Partitionen aktiviert, und vorhandene Veröffentlichungen werden automatisch für die Verwendung dieser Funktion aktualisiert. Erfüllt eine Veröffentlichung die Anforderungen nicht, kann sie geändert, und anschließend können vorausberechnete Partitionen aktiviert werden. Wenn einige Artikel den Anforderungen entsprechen und andere nicht, können Sie gegebenenfalls zwei Partitionen erstellen, von denen eine für vorausberechnete Partitionen aktiviert wird.  
  
### <a name="requirements-for-filter-clauses"></a>Anforderungen für Filterklauseln  
  
-   Alle in parametrisierten Zeilenfiltern verwendeten Funktionen, wie HOST_NAME() und SUSER_SNAME(), müssen direkt in die parametrisierte Filterklausel eingeschlossen sein und dürfen nicht innerhalb einer Sicht oder dynamischen Funktion geschachtelt sein. Weitere Informationen zu diesen Funktionen finden Sie unter [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql), [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) und [Parametrisierte Zeilenfilter](parameterized-filters-parameterized-row-filters.md).  
  
-   Die nach dem Erstellen der Partition für jeden Abonnenten zurückgegebenen Werte dürfen sich nicht ändern. Wenn Sie z. B. HOST_NAME() in einem Filter verwenden (und den Wert von HOST_NAME() nicht überschreiben), ändern Sie nicht den Computernamen auf dem Abonnenten.  
  
-   Joinfilter dürfen keine dynamischen Funktionen enthalten (Funktionen wie HOST_NAME() und SUSER_SNAME(), die je nach Abonnent, der die Synchronisierung ausführt, zu einem unterschiedlichen Wert ausgewertet werden). Nur parametrisierte Zeilenfilter dürfen dynamische Funktionen enthalten.  
  
-   Nicht deterministische Funktionen können nicht in einer Filterklausel verwendet werden. Weitere Informationen zu nicht deterministischen Funktionen finden Sie unter [Deterministic and Nondeterministic Functions](../../user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
-   Sichten, auf die in Joinklauseln oder parametrisierten Filterklauseln verwiesen wird, dürfen keine dynamischen Funktionen enthalten.  
  
-   In der Veröffentlichung dürfen keine kreisförmigen Joinfilterbeziehungen enthalten sein.  
  
### <a name="database-collation"></a>Datenbanksortierung  
  
-   Wenn vorausberechnete Partitionen verwendet werden, wird stets die Sortierung der Datenbank zu Vergleichen herangezogen und nicht die Sortierung der Tabelle oder Spalte. Betrachten Sie das folgende Szenario:  
  
    -   Eine Datenbank mit einer Sortierung, die Groß- und Kleinschreibung unterscheidet, enthält eine Tabelle mit einer Sortierung ohne Unterscheidung der Groß- und Kleinschreibung.  
  
    -   Die Tabelle enthält eine **ComputerName**-Spalte, die mit dem Hostnamen des Abonnenten in einem parametrisierten Filter verglichen wird.  
  
    -   Die Tabelle enthält eine Spalte mit dem Wert "MYCOMPUTER" und eine Zeile mit dem Wert "mycomputer" in dieser Spalte.  
  
     Wenn der Abonnent mit dem Hostnamen "mycomputer" eine Synchronisierung ausführt, empfängt der Abonnent nur eine Zeile, da bei dem Vergleich Groß- und Kleinschreibung berücksichtigt wird (die Sortierung der Datenbank). Werden keine vorausberechneten Partitionen verwendet, empfängt der Abonnent beide Zeilen, da die Tabelle eine Sortierung aufweist, bei der Groß- und Kleinschreibung nicht berücksichtigt wird.  
  
## <a name="performance-of-precomputed-partitions"></a>Leistung vorausberechneter Partitionen  
 Bei vorausberechneten Partitionen besteht ein geringfügiger Leistungsabfall, wenn Änderungen vom Abonnenten auf den Verleger hochgeladen werden. Der Großteil der Zeit bei der Mergeverarbeitung wird jedoch für die Auswertung von Partitionen und den Download von Änderungen vom Verleger zum Abonnenten aufgewendet. Deshalb kann der Reingewinn noch immer erheblich sein. Der Leistungsvorteil variiert je nach Anzahl der Abonnenten, die gleichzeitig eine Synchronisierung ausführen, und der Anzahl von Updates pro Synchronisierung, bei denen Zeilen zwischen Partitionen verschoben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Parametrisierte Zeilenfilter](parameterized-filters-parameterized-row-filters.md)  
  
  
