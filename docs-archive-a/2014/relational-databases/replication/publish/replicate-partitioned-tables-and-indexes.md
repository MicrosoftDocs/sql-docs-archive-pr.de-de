---
title: Replizieren partitionierter Tabellen und Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/10/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- partitioned indexes [SQL Server], replicating
- partitioned tables [SQL Server], replicating
- replication [SQL Server], partitioned tables
- publishing [SQL Server replication], partitioned tables
- transactional replication, partitioned tables
ms.assetid: c9fa81b1-6c81-4c11-927b-fab16301a8f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 616707bfb11b48b170fc8f0e8872076d2cd09d1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609800"
---
# <a name="replicate-partitioned-tables-and-indexes"></a>Replizieren partitionierter Tabellen und Indizes
  Durch die Partitionierung können große Tabellen oder Indizes einfacher verwaltet werden, da Sie Teilmengen von Daten schnell und effizient verwalten und darauf zugreifen können und gleichzeitig die Integrität einer Datensammlung erhalten können. Weitere Informationen finden Sie unter [partitionierte Tabellen und Indizes](../../partitions/partitioned-tables-and-indexes.md). Die Replikation unterstützt die Partitionierung durch Bereitstellung einer Gruppe von Eigenschaften, die angeben, wie partitionierte Tabellen und Indizes behandelt werden sollen.  
  
## <a name="article-properties-for-transactional-and-merge-replication"></a>Artikeleigenschaften für die Transaktions- und Mergereplikation  
 In der folgenden Tabelle sind die Objekte aufgelistet, die zum Partitionieren von Daten verwendet werden.  
  
|Object|Erstellt mit|  
|------------|----------------------|  
|Partitionierte Tabelle oder partitionierter Index|CREATE TABLE oder CREATE INDEX|  
|Partitionsfunktion|CREATE PARTITION FUNCTION|  
|Partitionsschema|CREATE PARTITION SCHEME|  
  
 Die erste Gruppe von Eigenschaften, die mit der Partitionierung in Zusammenhang stehen, sind Artikelschemaoptionen, die bestimmen, ob Partitionierungsobjekte auf den Abonnenten kopiert werden sollen. Diese Schemaoptionen können folgendermaßen festgelegt werden:  
  
-   Auf der Seite **Artikeleigenschaften** des Assistenten für neue Veröffentlichungen oder im Dialogfeld Veröffentlichungseigenschaften. Um die in der vorherigen Tabelle aufgeführten Objekte zu kopieren, geben Sie `true` den Wert für die Eigenschaften **Tabellen Partitionierungs Schemas kopieren** und **Index Partitionierungs Schemas**kopieren an. Informationen zum Zugriff auf die Seite **Artikeleigenschaften** finden Sie unter [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
-   Mithilfe des Parameters *schema_option* einer der folgenden gespeicherten Prozeduren:  
  
    -   [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) oder [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) für die Transaktionsreplikation  
  
    -   [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) oder [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) für die Mergereplikation  
  
     Geben Sie die entsprechenden Schemaoptionswerte an, um die in der obigen Tabelle aufgelisteten Objekte zu kopieren. Informationen zum Angeben von Schemaoptionen finden Sie unter [Specify Schema Options](specify-schema-options.md).  
  
 Durch die Replikation werden Objekte während der Erstsynchronisierung auf den Abonnenten kopiert. Wenn im Partitionsschema andere Dateigruppen als die PRIMARY-Dateigruppe verwendet werden, müssen diese vor der Erstinitialisierung auf dem Abonnenten vorhanden sein.  
  
 Nachdem der Abonnent initialisiert wurde, werden Datenänderungen an den Abonnenten weitergegeben und auf die entsprechenden Partitionen übertragen. Änderungen am Partitionsschema werden jedoch nicht unterstützt. Bei Transaktions- und Mergereplikationen wird die Replikation der folgenden Befehle nicht unterstützt: ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME bzw. die Anweisung REBUILD WITH PARTITION von ALTER INDEX  Die ihnen zugeordneten Änderungen werden nicht automatisch auf den Abonnenten repliziert. Es liegt in der Zuständigkeit des Benutzers, ähnliche Änderungen manuell für den Abonnenten vorzunehmen.  
  
## <a name="replication-support-for-partition-switching"></a>Replikationsunterstützung für Partitionswechsel  
 Ein wesentlicher Vorteil der Tabellenpartitionierung besteht in der Fähigkeit, Teilmengen von Daten rasch und effizient zwischen Partitionen zu verschieben. Daten werden mit dem Befehl SWITCH PARTITION verschoben. Wenn eine Tabelle für die Replikation aktiviert wurde, werden SWITCH PARTITION-Vorgänge aus folgenden Gründen standardmäßig blockiert:  
  
-   Wenn Daten in eine oder aus einer Tabelle verschoben werden, die auf dem Verleger, aber nicht auf dem Abonnenten vorhanden sind, können die Daten von Verleger und Abonnenten inkonsistent werden. Dieses Problem tritt i. d. R. auf, wenn Daten in eine oder aus einer Stagingtabelle verschoben werden.  
  
-   Wenn der Abonnent über eine andere Definition für die partitionierte Tabelle verfügt als der Verleger, dann schlägt der Verteilungs-Agent fehl, wenn er Änderungen auf dem Abonnenten anzuwenden versucht.  
  
 Trotz dieser potenziellen Probleme können Partitionswechsel für Transaktionsreplikationen aktiviert werden. Bevor Sie Partitionswechsel aktivieren, müssen Sie sicherstellen, dass alle an einem Partitionswechsel beteiligten Tabellen sowohl auf dem Verleger als auch auf dem Abonnenten vorhanden sind und dass die Tabellen- und Partitionsdefinitionen auf dem Verleger und dem Abonnenten identisch sind.  
  
 Wenn Partitionen bei den Verlegern und Abonnenten über das gleiche Partitionsschema verfügen, können Sie *allow_partition_switch* zusammen mit *replication_partition_switch* aktivieren, wodurch nur die "partition switch"-Anweisung für den Abonnenten repliziert wird. Sie können auch *allow_partition_switch* aktivieren, ohne die DDL zu replizieren. Dies ist hilfreich, wenn Sie alte Monate aus der Partition auslagern möchten und die replizierte Partition jedoch für ein weiteres Jahr für Sicherungszwecke auf dem Abonnenten aufbewahren möchten.  
  
 Wenn Sie über die aktuelle Version Partitionswechsel für SQL Server 2008 R2 aktivieren, benötigen Sie möglicherweise schon in naher Zukunft auch Teilungs- und Mergevorgänge. Stellen Sie vor dem Ausführen von Teilungs- oder Mergevorgängen in replizierten Tabellen sicher, dass für die fragliche Partition keine replizierten Befehle ausstehen. Sie sollten außerdem sicherstellen, dass für die Partition während der Teilungs- und Mergevorgänge keine DML-Vorgänge ausgeführt werden. Wenn Transaktionen vorhanden sind, die nicht vom Protokollleser verarbeitet wurden, oder DML-Vorgänge für eine Partition einer replizierten Tabelle ausgeführt werden, während ein Teilungs- oder Mergevorgang stattfindet (an dem die gleiche Partition beteiligt ist), kann das zu einem Verarbeitungsfehler beim Protokolllese-Agent führen. Um den Fehler zu beheben, ist möglicherweise eine erneute Initialisierung des Abonnements erforderlich.  
  
> [!WARNING]  
>  Sie sollten keinen Partitionswechsel für Peer-zu-Peer-Veröffentlichungen aktivieren, da die ausgeblendete Spalte dazu verwendet wird, um Konflikte zu erkennen und aufzulösen.  
  
### <a name="enabling-partition-switching"></a>Aktivieren des Partitionswechsels  
 Die folgenden Eigenschaften von Transaktionsveröffentlichungen ermöglichen es den Benutzern, das Verhalten von Partitionswechseln in einer replizierten Umgebung zu steuern:  
  
-   ** \@ **Wenn Sie auf festgelegt `true` haben, kann Switch Partition für die Veröffentlichungs Datenbank ausgeführt werden. allow_partition_switch  
  
-   ** \@ replicate_partition_switch** bestimmt, ob die Switch Partition DDL-Anweisung auf Abonnenten repliziert werden soll. Diese Option ist nur gültig, wenn ** \@ allow_partition_switch** auf festgelegt ist `true` .  
  
 Sie können diese Eigenschaften beim Erstellen der Veröffentlichung mit [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) oder nach der Erstellung der Veröffentlichung mit [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) festlegen. Wie bereits erwähnt, unterstützen Mergereplikationen keine Partitionswechsel. Entfernen Sie die Tabelle aus der Datenbank, um SWITCH PARTITION für eine Tabelle auszuführen, die für Mergereplikationen aktiviert wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)  
  
  
