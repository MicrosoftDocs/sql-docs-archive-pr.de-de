---
title: FILESTREAM-Kompatibilität mit anderen SQL Server-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], other SQL Server features and
- FILESTREAM [SQL Server], limitations
ms.assetid: d2c145dc-d49a-4f5b-91e6-89a2b0adb4f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53bb99ea094261fd96f2a821dfaa5203e9796d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607842"
---
# <a name="filestream-compatibility-with-other-sql-server-features"></a>FILESTREAM-Kompatibilität mit anderen SQL Server-Funktionen
  Da sich die FILESTREAM-Daten im Dateisystem befinden, werden in diesem Thema Informationen, Richtlinien und Einschränkungen in Bezug auf die Verwendung von FILESTREAM mit den folgenden Funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beschrieben.  
  
-   [SQL Server Integration Services (SSIS)](#ssis)  
  
-   [Verteilte Abfragen und Verbindungsserver](#distqueries)  
  
-   [Verschlüsselung](#encryption)  
  
-   [Datenbank-Momentaufnahmen](#DatabaseSnapshot)  
  
-   [Replikation](#Replication)  
  
-   [Protokollversand](#LogShipping)  
  
-   [Datenbankspiegelung](#DatabaseMirroring)  
  
-   [Volltextindizierung](#FullText)  
  
-   [Failoverclustering](#FailoverClustering)  
  
-   [SQL Server Express](#SQLServerExpress)  
  
-   [Eigenständige Datenbanken](#contained)  
  
##  <a name="sql-server-integration-services-ssis"></a><a name="ssis"></a> SQL Server Integration Services (SSIS)  
 SQL Server Integration Services (SSIS) behandelt FILESTREAM-Daten im Datenfluss wie andere BLOB-Daten mit dem DT_IMAGE SSIS-Datentyp.  
  
 Sie können die Transformation für das Importieren von Spalten verwenden, um Dateien aus dem Dateisystem in eine FILESTREAM-Spalte zu laden. Sie können auch die Transformation für das Exportieren von Spalten verwenden, um Dateien aus einer FILESTREAM-Spalte in einen anderen Speicherplatz im Dateisystem zu extrahieren.  
  
##  <a name="distributed-queries-and-linked-servers"></a><a name="distqueries"></a> Verteilte Abfragen und Verbindungsserver  
 Sie können mit FILESTREAM-Daten über verteilte Abfragen und Verbindungs Server arbeiten, indem Sie Sie als `varbinary(max)` Daten behandeln. Sie können die FILESTREAM-Funktion **PathName()** nicht in verteilten Abfragen nutzen, bei denen ein vierteiliger Name verwendet wird. Dies gilt auch, wenn der Name auf einen lokalen Server verweist. Sie können **PathName()** jedoch in der inneren Abfrage einer Pass-Through-Abfrage nutzen, bei der **OPENQUERY()** verwendet wird.  
  
##  <a name="encryption"></a><a name="encryption"></a> Verschlüsselung  
 FILESTREAM-Daten werden nicht verschlüsselt, auch dann nicht, wenn die transparente Datenverschlüsselung aktiviert ist.  
  
##  <a name="database-snapshots"></a><a name="DatabaseSnapshot"></a> Datenbank-Momentaufnahmen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine [Datenbankmomentaufnahmen](../databases/database-snapshots-sql-server.md) für FILESTREAM-Dateigruppen. Wenn eine FILESTREAM-Dateigruppe in eine CREATE DATABASE ON-Klausel eingeschlossen wird, schlägt die Anweisung fehl, und ein Fehler wird ausgelöst.  
  
 Wenn Sie FILESTREAM verwenden, können Sie Datenbankmomentaufnahmen von Standarddateigruppen (nicht-FILESTREAM) erstellen. Die FILESTREAM-Dateigruppen werden für diese Datenbankmomentaufnahmen als offline markiert.  
  
 Eine SELECT-Anweisung, die für eine FILESTREAM-Tabelle in einer Momentaufnahme-Datenbank ausgeführt wird, darf keine FILESTREAM-Spalte enthalten, da sonst die folgende Fehlermeldung zurückgegeben wird:  
  
 `Could not continue scan with NOLOCK due to data movement.`  
  
##  <a name="replication"></a><a name="Replication"></a> Replication  
 Eine `varbinary(max)`-Spalte, für die das FILESTREAM-Attribut auf dem Verleger aktiviert ist, kann für einen Abonnenten mit oder ohne FILESTREAM-Attribut repliziert werden. Verwenden Sie das Dialogfeld **Artikeleigenschaften – \<Article>** oder den @schema_option-Parameter von [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) oder [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), um die Methode für die Replikation der Spalte anzugeben. Daten, die in einer `varbinary(max)`-Spalte ohne FILESTREAM-Attribute repliziert werden, dürfen den 2 GB-Grenzwert für diesen Datentyp nicht überschreiten, da anderenfalls ein Laufzeitfehler ausgelöst wird. Es wird empfohlen, dass Sie das FILESTREAM-Attribut replizieren, es sei denn, die Replikation von Daten auf [!INCLUDE[ssVersion2005](../../includes/ssversion2000-md.md)] Abonnenten wird unabhängig von der angegebenen Schema Option nicht unterstützt.  
  
> [!NOTE]  
>  Das Replizieren von großen Datenwerten von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nach [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] -Abonnenten ist auf maximal 256 MB beschränkt. Weitere Informationen finden Sie unter [Maximum Capacity Specifications](https://go.microsoft.com/fwlink/?LinkId=103810).  
  
### <a name="considerations-for-transactional-replication"></a>Überlegungen zur Transaktionsreplikation  
 Wenn Sie FILESTREAM-Spalten in Tabellen verwenden, die zur Transaktionsreplikation veröffentlicht werden, beachten Sie Folgendes:  
  
-   Wenn einige Tabellen Spalten mit dem FILESTREAM-Attribut enthalten, können Sie keine Werte für *database snapshot* oder *database snapshot character* für die @sync_method-Eigenschaft von [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) verwenden.  
  
-   Die max text repl size-Option gibt die maximale Datenmenge an, die in eine Spalte eingefügt werden kann, die zur Replikation veröffentlicht wird. Diese Option kann verwendet werden, um die Größe von FILESTREAM-Daten zu kontrollieren, die repliziert werden.  
  
-   Wenn Sie die Schemaoption für die Replikation des FILESTREAM-Attributs angeben, aber die von FILESTREAM benötigte `uniqueidentifier`-Spalte herausfiltern oder angeben, dass die UNIQUE-Einschränkung für die Spalte nicht repliziert werden soll, wird das FILESTREAM-Attribut bei der Replikation nicht repliziert. Die Spalte wird nur als `varbinary(max)`-Spalte repliziert.  
  
### <a name="considerations-for-merge-replication"></a>Überlegungen hinsichtlich der Mergereplikation  
 Wenn Sie FILESTREAM-Spalten in Tabellen verwenden, die zur Mergereplikation veröffentlicht werden, beachten Sie Folgendes:  
  
-   Sowohl die Mergereplikation als auch FILESTREAM erfordern eine Spalte des Datentyps `uniqueidentifier`, um die einzelnen Zeilen in einer Tabelle zu identifizieren. Die Mergereplikation fügt automatisch eine Spalte hinzu, wenn die Tabelle sie nicht besitzt. Die Mergereplikation erfordert es, dass die ROWGUIDCOL-Eigenschaft für die Spalte festgelegt ist und der Standardwert NEWID() oder NEWSEQUENTIALID() lautet. Zusätzlich zu diesen Anforderungen erfordert es FILESTREAM, dass eine UNIQUE-Einschränkung für die Spalte definiert wird. Diese Anforderungen bringen Folgendes mit sich:  
  
    -   Wenn Sie eine FILESTREAM-Spalte einer Tabelle hinzufügen, die bereits zur Mergereplikation veröffentlicht wurde, vergewissern Sie sich, dass die `uniqueidentifier`-Spalte über eine UNIQUE-Einschränkung verfügt. Wenn sie über keine UNIQUE-Einschränkung verfügt, fügen Sie der Tabelle in der Veröffentlichungsdatenbank eine benannte Einschränkung hinzu. Standardmäßig veröffentlicht die Mergreplikation diese Schemaänderung, die dann auf jede Abonnentendatenbank angewendet wird.  
  
         Wenn Sie eine UNIQUE-Einschränkung manuell wie beschrieben hinzufügen und die Mergereplikation entfernen möchten, müssen Sie zuerst die UNIQUE-Einschränkung entfernen, da die Replikation ansonsten nicht entfernt wird.  
  
    -   Standardmäßig verwendet die Mergereplikation NEWSEQUENTIALID(), da ihre Leistungsfähigkeit gegenüber NEWID() höher ist. Wenn Sie eine `uniqueidentifier`-Spalte einer Tabelle hinzufügen, die für die Mergereplikation veröffentlicht wird, geben Sie NEWSEQUENTIALID() als Standardwert an.  
  
-   Die Mergereplikation schließt eine Optimierung zum Replizieren von Typen großer Objekte ein. Diese Optimierung wird durch den @stream_blob_columns-Parameter von [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) gesteuert. Wenn Sie die Schemaoption auf die Replikation des FILESTREAM-Attributs festlegen, wird der Wert des @stream_blob_columns-Parameters auf `true` festgelegt. Diese Optimierung kann mit [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)überschrieben werden. Mit dieser gespeicherten Prozedur können Sie @stream_blob_columns auf `false` festlegen. Wenn Sie eine FILESTREAM-Spalte einer Tabelle hinzufügen, die bereits für die Mergereplikation veröffentlicht wurde, sollten Sie die Option mit sp_changemergearticle auf `true` festlegen.  
  
-   Die Aktivierung der Schemaoption für FILESTREAM, nachdem ein Artikel erstellt wurde, kann zum Fehlschlagen der Replikation führen, wenn die Daten in der FILESTREAM-Spalte 2 GB übersteigen und während der Replikation ein Konflikt auftritt. Wenn Sie Grund zur Annahme haben, dass diese Situation eintritt, sollten Sie den Tabellenartikel löschen und mit der entsprechenden FILESTREAM-Schemaoption, die bei Erstellung aktiviert war, neu erstellen.  
  
-   Die Mergereplikation kann FILESTREAM-Daten über eine HTTPS-Verbindung durch [Websynchronisierung](../replication/merge/merge-replication.md)synchronisieren. Diese Daten dürfen die 50 MB-Grenze für die Websynchronisierung nicht übersteigen, andernfalls wird ein Laufzeitfehler generiert.  
  
##  <a name="log-shipping"></a><a name="LogShipping"></a> Protokollversand  
 Der[Protokollversand](../../database-engine/log-shipping/about-log-shipping-sql-server.md) unterstützt FILESTREAM. Sowohl auf dem primären als auch auf dem sekundären Server muss [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]oder eine spätere Version ausgeführt werden und FILESTREAM aktiviert sein.  
  
##  <a name="database-mirroring"></a><a name="DatabaseMirroring"></a> Datenbankspiegelung  
 FILESTREAM wird von der Datenbankspiegelung nicht unterstützt. Eine FILESTREAM-Dateigruppe kann nicht auf dem Prinzipalserver erstellt werden. Die Datenbankspiegelung kann nicht für eine Datenbank konfiguriert werden, die FILESTREAM-Dateigruppen enthält.  
  
##  <a name="full-text-indexing"></a><a name="FullText"></a> Volltextindizierung  
 Die [Volltextindizierung](../indexes/indexes.md) funktioniert mit einer FILESTREAM-Spalte genauso wie mit einer- `varbinary(max)` Spalte. Die FILESTREAM-Tabelle muss eine Spalte aufweisen, die die Dateinamenerweiterung für jeden FILESTREAM BLOB enthält. Weitere Informationen finden Sie unter [Abfragen mit Volltextsuche](../search/query-with-full-text-search.md),[Konfigurieren und Verwalten von Filtern für die Suche](../search/configure-and-manage-filters-for-search.md) und [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).  
  
 Die Volltext-Engine indiziert den Inhalt der FILESTREAM-BLOBs. Dateien wie beispielsweise Images zu indizieren, ist möglicherweise nicht nützlich. Wenn ein FILESTREAM BLOB aktualisiert wird, wird er neu indiziert.  
  
##  <a name="failover-clustering"></a><a name="FailoverClustering"></a> Failoverclustering  
 Für das Failoverclustering müssen FILESTREAM-Dateigruppen auf einem freigegebenen Datenträger abgelegt werden. FILESTREAM muss auf jedem Knoten im Cluster aktiviert werden, das die FILESTREAM-Instanz hostet. Weitere Informationen finden Sie unter [Einrichten von FILESTREAM auf einem Failovercluster](set-up-filestream-on-a-failover-cluster.md).  
  
##  <a name="sql-server-express"></a><a name="SQLServerExpress"></a> SQL Server Express  
 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] unterstützt FILESTREAM. Im Grenzwert für die Datenbankgröße von 10 GB ist der FILESTREAM-Datencontainer nicht inbegriffen.  
  
##  <a name="contained-databases"></a><a name="contained"></a> Eigenständige Datenbanken  
 Die FILESTREAM-Funktion erfordert etwas Konfiguration außerhalb der Datenbank. Daher sind Datenbanken, die FILESTREAM oder FileTable verwenden, nicht vollständig eigenständig.  
  
 Sie können den Einschlusstyp der Datenbank auf PARTIAL festlegen, wenn Sie bestimmte Funktionen eigenständiger Datenbanken verwenden möchten, z. B. eigenständige Benutzer. In diesem Fall müssen Sie jedoch beachten, dass einige Datenbankeinstellungen nicht in der Datenbank enthalten sind und nicht automatisch mit der Datenbank verschoben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Binary Large Object &#40;Blob&#41; Daten &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md)  
  
  
