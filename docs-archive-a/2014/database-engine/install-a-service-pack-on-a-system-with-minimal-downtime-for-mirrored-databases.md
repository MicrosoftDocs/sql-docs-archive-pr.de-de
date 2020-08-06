---
title: Installieren eines Service Packs auf einem System mit minimalen Ausfallzeiten für gespiegelte Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e878d31ec926f8b2cc460854f422b4d01d32d414
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718694"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a>Installieren eines Service Packs auf einem System mit minimaler Downtime der gespiegelten Datenbanken
  In diesem Thema wird beschrieben, wie beim Installieren von Service Packs und Hotfixes die Ausfallzeit von gespiegelten Datenbanken minimiert werden kann. Dieser Prozess umfasst ein sequenzielles Upgrade der Instanzen von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], die von der Datenbankspiegelung betroffen sind. Diese Art von Update, das als paralleles *Update*bezeichnet wird, reduziert Ausfallzeiten auf nur ein einzelnes Failover. Unter Umständen ist das parallele Update nicht für Sitzungen im hochleistungsfähigen Modus geeignet, bei denen sich der Spiegelserver und der Prinzipalserver an unterschiedlichen geografischen Orten befinden.  
  
 Ein paralleles Update ist ein mehrstufiger Prozess, der aus den folgenden Phasen besteht:  
  
-   Schützen Sie die Daten.  
  
-   Wenn an der Sitzung ein Zeuge beteiligt ist, sollten Sie den Zeugen entfernen. Andernfalls hängt die Datenbankverfügbarkeit von dem Zeugen ab, der weiterhin mit der Prinzipalserverinstanz verbunden bleibt, wenn die Spiegelserverinstanz aktualisiert wird. Nachdem Sie einen Zeugen entfernt haben, ist ein Update jederzeit während des parallelen Updateprozesses möglich, ohne Gefahr zu laufen, dass die Datenbank ausfällt.  
  
    > [!NOTE]  
    >  Weitere Informationen finden Sie unter [Quorum: Auswirkungen eines Zeugen auf die Datenbankverfügbarkeit &#40;Datenbankspiegelung&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
-   Ändern Sie den Betriebsmodus in den Modus für hohe Sicherheit, wenn eine Sitzung im Modus für hohe Leistung ausgeführt wird.  
  
-   Aktualisieren Sie jede Serverinstanz, die von der Datenbankspiegelung betroffen ist. Beim parallelen Update wird auch die Serverinstanz aktualisiert, die derzeit als Spiegelserver fungiert. Dabei wird ein manuelles Failover der gespiegelten Datenbanken ausgeführt und die Serverinstanz aktualisiert, die zunächst als Prinzipalserver fungiert hat (und nun der neue Spiegelserver ist). Zu diesem Zeitpunkt müssen Sie die Spiegelung fortsetzen.  
  
    > [!NOTE]  
    >  Vor der Ausführung eines parallelen Updates sollten Sie zu Übungszwecken ein manuelles Failover in mindestens einer Spiegelungssitzung ausführen.  
  
-   Kehren Sie ggf. in den Modus für hohe Leistung zurück.  
  
-   Fügen Sie ggf. den Zeugen wieder der Spiegelungssitzung hinzu.  
  
 Die Vorgehensweisen für die einzelnen Phasen werden hier beschrieben.  
  
> [!IMPORTANT]  
>  Eine Serverinstanz kann bei gleichzeitigen Spiegelungssitzungen verschiedene Spiegelungsrollen (Prinzipalserver, Spiegelserver oder Zeuge) ausführen. In diesem Fall müssen Sie den grundlegenden Prozess für das parallele Update entsprechend anpassen.  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a>So schützen Sie Daten vor einem Update (bewährte Methode)  
  
1.  Führen Sie für jede Prinzipaldatenbank eine vollständige Datenbanksicherung aus.  
  
     **So sichern Sie eine Datenbank**  
  
    -   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
2.  Führen Sie den [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)-Befehl für jede Prinzipaldatenbank aus.  
  
### <a name="to-remove-a-witness-from-a-session"></a>So entfernen Sie einen Zeugen aus einer Sitzung  
  
1.  Wenn ein Zeuge an einer Spiegelungssitzung beteiligt ist, sollte der Zeuge vor der Ausführung eines parallelen Updates entfernt werden.  
  
     **So entfernen Sie den Zeugen**  
  
    -   [Entfernen des Zeugen aus einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>So ändern Sie den Modus einer Sitzung vom Modus für hohe Leistung in den Modus für hohe Sicherheit  
  
1.  Ändern Sie den Betriebsmodus vor der Ausführung eines parallelen Updates in den Modus für hohe Sicherheit ohne automatisches Failover, wenn sich eine Spiegelungssitzung im Modus für hohe Leistung befindet. Verwenden Sie eine der folgenden Methoden:  
  
    -   In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Ändern Sie im Dialogfeld **Datenbankeigenschaften** auf der Seite **Spiegelung** die Option [Betriebsmodus](../relational-databases/databases/database-properties-mirroring-page.md) in **Hohe Sicherheit ohne automatisches Failover (synchron)** . Informationen über den Zugriff auf diese Seite finden Sie unter [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).  
  
    -   In [!INCLUDE[tsql](../includes/tsql-md.md)]: Legen Sie die Transaktionssicherheit auf FULL fest. Weitere Informationen finden Sie unter [Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).  
  
### <a name="to-perform-the-rolling-update"></a>So führen Sie das parallele Update aus  
  
1.  Zur Minimierung der Downtime wird Folgendes empfohlen: Starten Sie das parallele Update mit dem Aktualisieren aller Spiegelungspartner, die aktuell als Spiegelserver in allen Spiegelungssitzungen fungieren. Möglicherweise müssen an dieser Stelle mehrere Serverinstanzen aktualisiert werden.  
  
    > [!NOTE]  
    >  Ein Zeuge kann jederzeit während der Ausführung des parallelen Updates aktualisiert werden. Wenn beispielsweise eine Serverinstanz in Sitzung 1 als Spiegelserver und in Sitzung 2 als Zeuge fungiert, können Sie die Serverinstanz nun aktualisieren.  
  
     Welche Serverinstanz zuerst aktualisiert wird, hängt von der aktuellen Konfiguration der Spiegelungssitzungen ab:  
  
    -   Wenn bereits eine Serverinstanz als Spiegelserver in allen Spiegelungssitzungen fungiert, installieren Sie das Service Pack bzw. den Hotfix auf dieser Serverinstanz.  
  
    -   Wenn alle Server Instanzen aktuell als Prinzipal Server in allen Spiegelungs Sitzungen fungieren, wählen Sie eine Serverinstanz aus, die zuerst aktualisiert werden soll. Führen Sie dann ein manuelles Failover für alle Prinzipaldatenbanken aus, und aktualisieren Sie die Serverinstanz, indem Sie das Service Pack bzw. das Hotfix installieren.  
  
     Nach dem Update nimmt eine Serverinstanz automatisch wieder an den zugehörigen Spiegelungssitzungen teil.  
  
     **So führen Sie ein manuelles Failover aus**  
  
    -   [Manueller Failover für eine Datenbank-Spiegelungssitzung &#40;SQL Server Management Studio&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Manuelles Failover für eine Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).  
  
     Informationen zum Verwalten des potenziellen Datenverlusts finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
2.  Warten Sie bei jeder Spiegelungssitzung, deren Spiegelserverinstanz gerade aktualisiert wurde, die Synchronisierung der Sitzung ab. Stellen Sie dann eine Verbindung mit der Prinzipalserverinstanz her, und führen Sie manuell ein Failover zur Sitzung aus. Bei einem Failover wird die aktualisierte Serverinstanz zum Prinzipal Server dieser Sitzung, und der frühere Prinzipal Server wird zum Spiegel Server.  
  
     Ziel dieses Schritts ist es, dass eine andere Serverinstanz zum Spiegelserver in jeder Spiegelungssitzung wird, an der sie als Partner beteiligt ist.  
  
3.  Nach dem Failover sollten Sie den [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) -Befehl für die Prinzipaldatenbank ausführen.  
  
4.  Installieren Sie das Service Pack bzw. den Hotfix auf allen Serverinstanzen, die nun als Spiegelserver in allen Spiegelungssitzungen fungieren, an denen sie als Partner beteiligt sind. Möglicherweise müssen an dieser Stelle mehrere Server aktualisiert werden.  
  
    > [!IMPORTANT]  
    >  Es ist möglich, dass in einer komplexen Spiegelungskonfiguration manche Serverinstanz nach wie vor der ursprüngliche Prinzipalserver in mindestens einer Spiegelungssitzung ist. Wiederholen Sie die Schritte 2-4 für diese Server Instanzen, bis alle beteiligten Instanzen aktualisiert wurden.  
  
5.  Setzen Sie die Spiegelungssitzung fort.  
  
    > [!NOTE]  
    >  Ein automatisches Failover funktioniert erst, nachdem der Zeuge aktualisiert wurde.  
  
6.  Installieren Sie die Service Packs bzw. Hotfixes auf allen übrigen Serverinstanzen, die als Zeuge in allen Spiegelungssitzungen fungieren. Nachdem ein aktualisierter Zeuge wieder an einer Spiegelungssitzung teilnimmt, ist das Ausführen eines automatischen Failovers wieder möglich. Möglicherweise müssen an dieser Stelle mehrere Server aktualisiert werden.  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>So ändern Sie den Modus einer Sitzung wieder in den Modus für hohe Leistung  
  
1.  Sie haben die folgenden Möglichkeiten, um den Modus einer Sitzung wieder in den Modus für hohe Leistung zu ändern:  
  
    -   In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Ändern Sie im Dialogfeld **Datenbankeigenschaften** auf der Seite **Spiegelung** die Option [Betriebsmodus](../relational-databases/databases/database-properties-mirroring-page.md) in **Hohe Leistung (asynchron)** .  
  
    -   In [!INCLUDE[tsql](../includes/tsql-md.md)] : Verwenden Sie [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) , um die Transaktionssicherheit auf OFF festzulegen.  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a>So fügen Sie einen Zeugen wieder einer Spiegelungssitzung hinzu  
  
1.  Im Modus für hohe Sicherheit können Sie den Zeugen in jeder Spiegelungssitzung wiederherstellen.  
  
     **So stellen Sie den Zeugen wieder her**  
  
    -   [Hinzufügen oder Ersetzen eines Datenbank-Spiegelungszeugen &#40;SQL Server Management Studio&#41;](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Hinzufügen eines Zeugen für die Datenbankspiegelung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE-Datenbankspiegelung &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md)   
 [Betriebsmodi der Datenbankspiegelung](database-mirroring/database-mirroring-operating-modes.md)   
 [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Anzeigen des Status einer gespiegelten Datenbank &#40;SQL Server Management Studio&#41;](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
