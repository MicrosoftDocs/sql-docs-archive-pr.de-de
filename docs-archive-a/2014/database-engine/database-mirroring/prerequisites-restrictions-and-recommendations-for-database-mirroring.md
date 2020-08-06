---
title: Voraussetzungen, Einschränkungen und Empfehlungen für die Datenbankspiegelung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dc29dbdc8432a4abd197a2a1a3f15b6ff5f6d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701835"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a>Voraussetzungen, Einschränkungen und Empfehlungen für die Datenbankspiegelung
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
 In diesem Thema werden die Voraussetzungen und Empfehlungen zum Einrichten der Datenbankspiegelung beschrieben. Eine Einführung in die Datenbankspiegelung finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md).  
  
> [!NOTE]  
>  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherformat für Datenträger stimmt in 64-Bit- und in 32-Bit-Umgebungen überein. Aus diesem Grund können für eine Datenbank-Spiegelungssitzung Serverinstanzen, die in einer 32-Bit-Umgebung ausgeführt werden, mit Serverinstanzen, die in einer 64-Bit-Umgebung ausgeführt werden, kombiniert werden.  
  

  
##  <a name="support-for-database-mirroring"></a><a name="DbmSupport"></a>Unterstützung für Daten Bank Spiegelung  
 Informationen zur unterstützten Datenbankspiegelung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] finden Sie unter [Von den SQL Server 2014-Editionen unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Beachten Sie, dass die Datenbankspiegelung mit jedem unterstützten Datenbank-Kompatibilitätsgrad funktioniert. Informationen zu den unterstützten Kompatibilitätsgraden finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  

  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Damit eine Spiegelungssitzung eingerichtet werden kann, müssen die Partner und ggf. der Zeuge unter derselben Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden.  
  
-   Auf beiden Partnern, also Prinzipalserver und Spiegelserver, muss dieselbe Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden. Der Zeuge (falls vorhanden) kann auf einer beliebige Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden, die die Datenbankspiegelung unterstützt.  
  
    > [!NOTE]  
    >  Sie können Serverinstanzen, die Partner in einer Spiegelungssitzung sind, auf eine neuere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisieren. Weitere Informationen finden Sie unter [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).  
  
-   Für die Datenbank muss das vollständige Wiederherstellungsmodell verwendet werden. Die Datenbankspiegelung wird vom einfachen und vom massenprotokollierten Wiederherstellungsmodell nicht unterstützt. Daher werden Massenvorgänge immer vollständig für eine gespiegelte Datenbank protokolliert. Weitere Informationen zu Wiederherstellungsmodellen finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
-   Überprüfen Sie, ob auf dem Spiegelserver genügend Speicherplatz für die Spiegeldatenbank vorhanden ist.  
  
    > [!NOTE]  
    >  Informationen zum Verwenden der Datenbankspiegelung für eine replizierte Datenbank finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md).  
  
-   Stellen Sie beim Erstellen der Spiegeldatenbank auf dem Spiegelserver sicher, dass Sie die Sicherung der Prinzipaldatenbank mit WITH NORECOVERY und demselben Datenbanknamen wiederherstellen. Außerdem müssen Sie alle Protokollsicherungen anwenden, die nach dieser Sicherung ausgeführt wurden – ebenfalls mit der Option WITH NORECOVERY.  
  
    > [!IMPORTANT]  
    >  Wurde die Datenbankspiegelung beendet, bevor Sie einen Neustart ausführen konnten, müssen alle nachfolgend in der Prinzipaldatenbank erstellten Protokollsicherungen auf die Spiegeldatenbank angewendet werden.  
  

  
##  <a name="restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Es können nur Benutzerdatenbanken können gespiegelt werden. Die Datenbanken **master**, **msdb**, **tempdb**und **model** können nicht gespiegelt werden.  
  
-   Eine gespiegelte Datenbank kann während einer Datenbank-Spiegelungssitzung nicht umbenannt werden.  
  
-   FILESTREAM wird von der Datenbankspiegelung nicht unterstützt. Eine FILESTREAM-Dateigruppe kann nicht auf dem Prinzipalserver erstellt werden. Die Datenbankspiegelung kann nicht für eine Datenbank konfiguriert werden, die FILESTREAM-Dateigruppen enthält.  
  
-   Unter einem 32-Bit-System unterstützt die Datenbankspiegelung aufgrund der Anzahl der Arbeitsthreads, die von jeder Datenbankspiegelungssitzung beansprucht werden, bis zu rund 10 Datenbanken pro Serverinstanz.  
  
-   Die Datenbankspiegelung wird weder für datenbankübergreifende Transaktionen noch für verteilte Transaktionen unterstützt. Weitere Informationen finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).  
  

  
##  <a name="recommendations-for-configuring-partner-servers"></a><a name="RecommendationsForPartners"></a>Empfehlungen zum Konfigurieren von Partner Servern  
  
-   Die Partner sollten auf vergleichbaren Systemen ausgeführt werden, die identische Arbeitsauslastungen bewältigen können.  
  
    > [!NOTE]  
    >  Wenn die Verwendung des Modus für hohe Sicherheit mit automatischem Failover vorgesehen ist, sollte die normale Auslastung für jeden Failoverpartner weniger als 50 Prozent der CPU-Auslastung betragen. Wird die CPU überlastet, kann es vorkommen, dass ein Failoverpartner nicht in der Lage ist, die anderen Serverinstanzen innerhalb der Spiegelungssitzung zu pingen. Dies verursacht ein unnötiges Failover. Wenn Sie die CPU-Auslastung nicht unter 50 Prozent halten können, wird die Verwendung des Modus für hohe Sicherheit ohne automatisches Failover oder des Modus für hohe Leistung empfohlen.  
  
-   Wenn möglich sollte der Pfad (einschließlich des Laufwerkbuchstabens) der Spiegeldatenbank mit dem Pfad der Prinzipaldatenbank identisch sein. Sie müssen die Option MOVE in die RESTORE-Anweisung einbeziehen, wenn sich die Dateilayouts unterscheiden müssen. Beispiel: Die Prinzipaldatenbank befindet sich auf Laufwerk F:, auf dem Spiegelungssystem ist jedoch kein Laufwerk F: vorhanden.  
  
    > [!IMPORTANT]  
    >  Falls Sie die Datenbankdateien bei der Erstellung der Spiegeldatenbank verschieben, können Sie der Datenbank später u. U. keine Dateien hinzufügen, ohne dass die Spiegelung unterbrochen wird.  
  
-   Alle Serverinstanzen in einer Spiegelungssitzung sollten dieselbe Mastercodepage und Sortierung verwenden. Unterschiede können zu einem Problem während des Einrichtens der Spiegelung führen.  
  
-   Schätzen Sie optional die Zeit für das Failover einer Datenbank, um sicherzustellen, dass die Systemkonfiguration die erforderliche Leistung aufbringt. Weitere Informationen finden Sie unter [Einschätzen der Unterbrechung des Diensts während des Rollenwechsels &#40;Datenbankspiegelung&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)ausgetauscht werden.  
  
-   Für eine optimale Leistung sollten Sie einen dedizierten Netzwerkadapter (NIC, Network Interface Card, Netzwerkschnittstellenkarte) für die Spiegelung verwenden.  
  
-   Es wird bewusst auf Stellungnahmen zum Zuverlässigkeitsgrad von WANs (Wide-Area Networks) für die Datenbankspiegelung im Hochsicherheitsmodus verzichtet. Wenn Sie sich jedoch für die Verwendung der Datenbankspiegelung im Hochsicherheitsmodus über ein WAN entschieden haben, sollten Sie vorsichtig sein, wenn Sie einer Sitzung einen Zeugen hinzufügen, da ein automatisches Failover auftreten kann. Weitere Informationen hierzu finden Sie unter [Empfehlungen für das Bereitstellen der Datenbankspiegelung](#RecommendationsForDeploying)weiter unten in diesem Thema.  
  

  
##  <a name="recommendations-for-deploying-database-mirroring"></a><a name="RecommendationsForDeploying"></a>Empfehlungen für die Bereitstellung der Daten Bank  
 Eine optimale Leistung bei der Datenbankspiegelung wird über den asynchronen Betrieb erzielt. Bei einer Spiegelungssitzung, die im synchronen Betrieb ausgeführt wird, treten Leistungsverzögerungen auf, wenn große Mengen an Transaktionsprotokolldaten generiert werden.  
  
 In Testumgebungen ist es sinnvoll, alle Betriebsmodi zu überprüfen, um das Verhalten der Datenbankspiegelung beurteilen zu können. Bevor Sie jedoch die Spiegelung in einer Produktionsumgebung bereitstellen, müssen Sie sicherstellen, dass Sie wissen, wie das Netzwerk in der Realität funktioniert.  
  
 Der Modus für hohe Sicherheit mit automatischem Failover wurde für ein Netzwerk mit hoher Verfügbarkeit mit einer dedizierten Verbindung oder einer verhältnismäßig einfachen Netzwerkkonfiguration entwickelt, wodurch mögliche Netzwerkfehlerquellen minimiert werden. Eine solche hochwertige Netzwerkumgebung ist für den Modus für hohe Sicherheit mit automatischem Failover erforderlich und wird für alle Datenbank-Spiegelungssitzungen empfohlen. Der Modus für hohe Leistung und der Modus für hohe Sicherheit ohne automatisches Failover sind jedoch deutlich weniger von der Netzwerkzuverlässigkeit betroffen.  
  
 Für Produktionsumgebungen wird deshalb die Einhaltung dieser Bereitstellungsrichtlinien empfohlen:  
  
1.  Beginnen Sie mit der Ausführung im asynchronen Modus für hohe Leistung. Dieser Modus reagiert weniger empfindlich auf die Netzwerkumgebung und stellt die beste Konfiguration bereit, um die Funktionsweise der Spiegelung kennen zu lernen. Die asynchrone Ausführung des Systems wird so lange empfohlen, bis Sie sicher sind, dass Ihre Bandbreite die Spiegelung unterstützt und Sie Kenntnisse für das Einrichten der Spiegelung und die Leistung des asynchronen Modus in Ihrer Umgebung aufbauen konnten. Weitere Informationen finden Sie unter [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).  
  
    > [!IMPORTANT]  
    >  Während der Testphase wird empfohlen, die Sitzungen auf Netzwerkfehler, die zu Problemen bei der Datenbankspiegelung führen, zu überwachen. Weitere Informationen zu möglichen Fehlerquellen finden Sie unter [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md). Weitere Informationen zur Überwachung der Datenbankspiegelung finden Sie unter [Überwachung der Datenbankspiegelung &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md).  
  
2.  Wenn Sie sicher sind, dass der asynchrone Betrieb die Anforderungen Ihres Unternehmens erfüllt, können Sie den synchronen Betrieb ausprobieren, um den Schutz der Daten zu verbessern. Beim Testen der Funktion der synchronen Spiegelung in Ihrer Umgebung wird empfohlen, den Modus für hohe Sicherheit zunächst ohne automatisches Failover zu testen. Der Hauptzweck dieses Tests besteht darin, die Auswirkungen des synchronen Betriebs auf die Datenbankleistung kennen zu lernen. Weitere Informationen finden Sie unter [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).  
  
3.  Aktivieren Sie das automatische Failover erst, wenn Sie überzeugt sind, dass der Modus für hohe Sicherheit ohne automatisches Failover die Anforderungen des Unternehmens erfüllt und dass Netzwerkfehler keine Ausfälle zur Folge haben. Weitere Informationen finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)herunter.  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md)   
 [Transport Sicherheit für Daten Bank Spiegelung und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Problembehandlung für die Datenbankspiegelungskonfiguration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
