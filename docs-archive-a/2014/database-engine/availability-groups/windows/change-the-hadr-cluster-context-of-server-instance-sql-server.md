---
title: Ändern des HADR-Clusterkontexts der Serverinstanz (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbc29fa2ebaaf2bbc9e577b5bd303e8a0dd0ec4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724997"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a>Ändern des HADR-Clusterkontexts der Serverinstanz (SQL Server)
  In diesem Thema wird beschrieben, wie der HADR-Clusterkontext einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] und höheren Versionen gewechselt wird. Der *HADR-Clusterkontext* bestimmt, welcher Windows Server Failover Clustering-Cluster (WSFC) die Metadaten für von der Serverinstanz gehostete Verfügbarkeitsreplikate verwaltet.  
  
 Wechseln Sie den HADR-Clusterkontext nur während einer clusterübergreifenden Migration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] zu einer Instanz von [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] auf einem neuen WSFC-Cluster. Die Kreuzclustermigration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt ein Betriebssystemupgrade auf [!INCLUDE[win8](../../../includes/win8-md.md)] oder [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] mit minimalen Ausfallzeiten der Verfügbarkeitsgruppen. Weitere Informationen finden Sie unter [Clusterübergreifende Migration von AlwaysOn-Verfügbarkeitsgruppen für Betriebssystemupgrade](https://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
> [!CAUTION]  
>  Wechseln Sie den HADR-Clusterkontext nur während der clusterübergreifenden Migration von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Bereitstellungen.  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie können mit dem HADR-Clusterkontext nur vom lokalen WSFC-Cluster zu einem Remotecluster und dann zurück vom Remotecluster zum lokalen Cluster wechseln. Sie können den HADR-Clusterkontext nicht von einem Remotecluster zu einem anderen Remotecluster umschalten.  
  
-   Der HADR-Clusterkontext kann nur dann zu einem Remotecluster umgeschaltet werden, wenn die Instanz von SQL-Server keine Verfügbarkeitsreplikate hostet.  
  
-   Ein Remote-HADR-Clusterkontext kann jederzeit zurück zum lokalen Cluster wechseln. Der Kontext kann jedoch nicht erneut gewechselt werden, solange die Serverinstanz Verfügbarkeitsreplikate hostet.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Die Serverinstanz, auf der Sie den HADR-Clusterkontext ändern, muss [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] oder höher (ab Enterprise Edition) ausführen.  
  
-   Die Serverinstanzen muss für AlwaysOn aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Damit eine Serverinstanz von einem lokalen Clusterkontext auf einen Remotecluster umgeschaltet werden kann, darf sie keine Verfügbarkeitsreplikate hosten. Die [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) -Katalogsicht sollte keine Zeilen zurückgeben.  
  
     Wenn auf der Serverinstanz Verfügbarkeitsreplikate vorhanden sind, bevor Sie den HADR-Clusterkontext ändern können, müssen Sie einen der folgenden Schritte ausführen:  
  
    |Replikatrolle|Aktion|Link|  
    |------------------|------------|----------|  
    |Primär|Schaltet die Verfügbarkeitsgruppe offline.|[Offlineschalten einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)|  
    |Secondary|Entfernen des Replikats aus der Verfügbarkeitsgruppe|[Entfernen einer sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   Bevor Sie von einem Remotecluster zum lokalen Cluster wechseln können, müssen alle Replikate mit synchronem Commit SYNCHRONIZED sein.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Es wird empfohlen, dass Sie den vollständigen Domänennamen angeben. Der Grund hierfür ist, dass ALTER SERVER CONFIGURATION die Ziel-IP-Adresse eines Kurznamens mithilfe einer DNS-Auflösung sucht. In einigen Fällen, abhängig von der DNS-Suchreihenfolge, kann die Verwendung eines Kurznamens Verwirrung verursachen. Betrachten Sie zum Beispiel den folgenden Befehl, der für einen Knoten in der Domäne `abc` ausgeführt wird: (`node1.abc.com`). Der vorgesehene Zielcluster ist der `CLUS01` -Cluster in der Domäne `xyz` (`clus01.xyz.com`). Die lokale Domäne hostet jedoch auch einen Cluster mit dem Namen `CLUS01` (`clus01.abc.com`).  
  
     Wenn der Kurzname des Zielclusters, `CLUS01`, angegeben wird, kann die DNS-Namensauflösung die IP-Adresse des falschen Clusters, `clus01.abc.com`, zurückgeben. Um derartige Verwirrungen zu vermeiden, geben Sie den vollständigen Namen des Zielclusters an, wie im folgende Beispiel dargestellt:  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
  
-   **SQL Server-Anmeldung**  
  
     Erfordert die CONTROL SERVER-Berechtigung.  
  
-   **SQL Server Dienst Konto**  
  
     Das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto der Serverinstanz muss über Folgendes verfügen:  
  
    -   Berechtigung zum Öffnen des WSFC-Zielclusters.  
  
    -   Remote-WSFC-Lese-/Schreibzugriff.  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie den WSFC-Clusterkontext eines Verfügbarkeitsreplikats**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die entweder das primäre Replikat oder ein sekundäres Replikat der Verfügbarkeitsgruppe hostet.  
  
2.  Verwenden Sie die SET HADR CLUSTER CONTEXT-Klausel der [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) -Anweisung, wie nachfolgend aufgeführt:  
  
     Alter Server Configuration Set HADR-Cluster Kontext **=** { **' *`windows_cluster`* '** | Nah  
  
     Erläuterungen:  
  
     *Windows-Cluster*  
     Der Clusterobjektname (CON) eines WSFC-Clusters. Sie können entweder den Kurznamen oder den vollständigen Domänennamen angeben. Es wird empfohlen, dass Sie den vollständigen Domänennamen angeben. Weitere Informationen finden Sie weiter oben in diesem Thema unter [Empfehlungen](#Recommendations).  
  
     LOCAL  
     Der lokale WSFC-Cluster.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der HADR-Clusterkontext in einen anderen Cluster geändert. Im Beispiel wird der vollständige Clusterobjektname, `clus01`, angegeben, um den Ziel-WSFC-Cluster `clus01.xyz.com`anzugeben.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 Im folgenden Beispiel wird der HADR-Clusterkontext in den lokalen WSFC-Cluster geändert.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a> Nachverfolgung: Nach dem Wechseln des Clusterkontexts eines Verfügbarkeitsreplikats  
 Der neue HADR-Clusterkontext wird sofort wirksam, ohne die Serverinstanz neu starten zu müssen. Die Einstellung für den HADR-Clusterkontext ist eine persistente Einstellung auf Instanzebene, die unverändert bleibt, wenn die Serverinstanz neu gestartet wird.  
  
 Bestätigen Sie den neuen HADR-Clusterkontext, indem Sie die dynamische Verwaltungssicht [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) wie folgt abfragen:  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 Diese Abfrage sollte den Namen des Clusters zurückgeben, auf den Sie den HADR-Clusterkontext festgelegt haben.  
  
 Wenn der HADR-Clusterkontext zu einem neuen Cluster gewechselt wird:  
  
-   Die Metadaten werden für alle Verfügbarkeitsreplikate bereinigt, die gerade von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz gehostet werden.  
  
-   Alle Datenbanken, die zuvor zu einem Verfügbarkeitsreplikat gehörten, befinden sich jetzt im Status RESTORING.  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Entfernen eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](remove-an-availability-group-listener-sql-server.md)  
  
-   [Offlineschalten einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
-   [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Entfernen einer sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Technische Artikel zu SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server AlwaysOn-Teamblog: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server-Failoverclustering &#40;wsfc-&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
