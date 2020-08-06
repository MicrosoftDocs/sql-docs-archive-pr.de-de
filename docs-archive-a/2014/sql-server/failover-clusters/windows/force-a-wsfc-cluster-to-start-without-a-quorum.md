---
title: Erzwingen des Starts eines WSFC-Clusters ohne Quorum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: 4a121375-7424-4444-b876-baefa8fe9015
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6f2110b706de015d0c7b19475b335908c118267
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617559"
---
# <a name="force-a-wsfc-cluster-to-start-without-a-quorum"></a>Erzwingen des Starts eines Clusters ohne Quorum
  In diesem Thema wird beschrieben, wie der Start eines Windows Server-Failoverclustering-Clusterknotens ohne Quorum erzwungen wird.  Dies ist möglicherweise für die Notfallwiederherstellung sowie in Multisubnetzszenarien erforderlich, um Daten wiederherzustellen die hohe Verfügbarkeit für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] - und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanzen wieder vollständig einrichten zu können.  
  
-   **Vorbereitungen:**  [Empfehlungen](#Recommendations), [Sicherheit](#Security)  
  
-   **So erzwingen Sie den Start eines Clusters ohne Quorum:**  [Verwenden des Failovercluster-Managers](#FailoverClusterManagerProcedure), [Verwenden von PowerShell](#PowerShellProcedure), [Verwenden von Net.exe](#CommandPromptProcedure)  
  
-   **Nachverfolgung:**  [Nachverfolgung: Nach dem Erzwingen des Clusterstarts ohne ein Quorum](#FollowUp)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
 Ohne anderslautende Angaben sind die in diesem Thema beschriebenen Prozeduren anwendbar, wenn sie von einem beliebigen Knoten im WSFC-Cluster ausgeführt werden.  Sie erzielen jedoch u. U. bessere Ergebnisse und vermeiden Netzwerkprobleme, indem Sie diese Schritte von dem Knoten ausführen, von dem aus der Start ohne Quorum erzwungen werden soll.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Der Benutzer muss einem Domänenkonto entsprechen, das Mitglied der lokalen Administratorgruppe an jedem Knoten des WSFC-Clusters ist.  
  
##  <a name="using-failover-cluster-manager"></a><a name="FailoverClusterManagerProcedure"></a>Verwenden von Failovercluster-Manager  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a>So erzwingen Sie den Start eines Clusters ohne Quorum  
  
1.  Öffnen Sie einen Failovercluster-Manager, und stellen Sie eine Verbindung mit dem gewünschten Clusterknoten her, um dessen Onlineschaltung zu erzwingen.  
  
2.  Klicken Sie im **Aktions** Bereich auf **Cluster Start erzwingen**, und klicken Sie dann auf **Ja-eigenen Cluster starten**.  
  
3.  Klicken Sie im linken Bereich in der Struktur **Failovercluster-Manager** auf den Clusternamen.  
  
4.  Stellen Sie im Zusammenfassungsbereich sicher, dass für **Quorumkonfiguration** als aktueller Wert  **Warnung: Der Cluster wird im Status "ForceQuorum" ausgeführt**festgelegt ist.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a>Verwenden von PowerShell  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a>So erzwingen Sie den Start eines Clusters ohne Quorum  
  
1.  Starten Sie eine erhöhte Windows PowerShell mittels **Als Administrator ausführen**.  
  
2.  Importieren Sie das `FailoverClusters` -Modul, um Cluster-Cmdlets zu aktivieren.  
  
3.  Stellen Sie mithilfe von `Stop-ClusterNode` sicher, dass der Clusterdienst beendet wurde.  
  
4.  Verwenden Sie `Start-ClusterNode` mit `-FixQuorum` , um den Start des Clusterdiensts zu erzwingen.  
  
5.  Verwenden Sie `Get-ClusterNode` mit `-Propery NodeWieght = 1` , um den Wert festzulegen, mit dem gewährleistet wird, dass der Knoten ein Abstimmungselement des Quorums ist.  
  
6.  Geben Sie die Clusterknoteneigenschaften in einem lesbaren Format aus.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird der Start des AlwaysOnSrv02-Knotenclusterdiensts ohne Quorum erzwungen. Dabei wird `NodeWeight = 1`festgelegt, und anschließend wird der Clusterknotenstatus vom neu erzwungenen Knoten aus aufgelistet.  
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv02"  
Stop-ClusterNode -Name $node  
Start-ClusterNode -Name $node -FixQuorum  
  
(Get-ClusterNode $node).NodeWeight = 1  
  
$nodes = Get-ClusterNode -Cluster $node  
$nodes | Format-Table -property NodeName, State, NodeWeight
```  
  
##  <a name="using-netexe"></a><a name="CommandPromptProcedure"></a>Verwenden von Net.exe  
  
### <a name="to-force-a-cluster-to-start-without-a-quorum"></a>So erzwingen Sie den Start eines Clusters ohne Quorum  
  
1.  Stellen Sie mittels Remotedesktop eine Verbindung mit dem gewünschten Clusterknoten her, um dessen Onlineschaltung zu erzwingen.  
  
2.  Starten Sie mit **Als Administrator ausführen**eine Eingabeaufforderung mit erweiterten Berechtigungen.  
  
3.  Stellen Sie mithilfe von **net.exe** sicher, dass der lokale Clusterdienst beendet wurde.  
  
4.  Verwenden Sie **net.exe** mit `/forcequorum` , um den Start des lokalen Clusterdiensts zu erzwingen.  
  
### <a name="example-netexe"></a>Beispiel (Net.exe)  
 Im folgenden Beispiel wird der Start eines Knotenclusterdiensts ohne Quorum erzwungen. Dabei wird `NodeWeight = 1`festgelegt, und anschließend wird der Clusterknotenstatus vom neu erzwungenen Knoten aus aufgelistet.  
  
```cmd
net.exe stop clussvc  
net.exe start clussvc /forcequorum  
```  
  
##  <a name="follow-up-after-forcing-cluster-to-start-without-a-quorum"></a><a name="FollowUp"></a>Nachverfolgung: nach dem Erzwingen des Cluster Starts ohne ein Quorum  
  
-   NodeWeight-Werte sind neu zu bewerten und zu konfigurieren, um vor der erneuten Onlineschaltung anderer Knoten ein neues Quorum korrekt erstellen zu können. Andernfalls wird für den Cluster u. U. wieder der Offlinemodus aktiviert.  
  
     Weitere Informationen finden Sie unter [WSFC-Quorummodi und Abstimmungskonfiguration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).  
  
-   Die Prozeduren in diesem Thema stellen nur einen Schritt zur erneuten Onlineschaltung des WSFC-Clusters dar, wenn ein unvorhergesehener Quorumfehler auftreten sollte.  Sie möchten möglicherweise weitere Maßnahmen ergreifen, um zu verhindern, dass andere WSFC-Clusterknoten die neue Quorumkonfiguration stören.  
  
-   Andere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen, wie [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], die Datenbankspiegelung und der Protokollversand, erfordern u. U. zudem weitere Aktionen zur Datenwiederherstellung und vollständigen erneuten Einrichtung der hohen Verfügbarkeit.  
  
     **Weitere Informationen finden Sie unter:**  
  
     [Ausführen eines erzwungenen manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
     [Erzwingen des Diensts in einer Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
  
     [Failover zu einer sekundären Datenbank für den Protokollversand &#40;SQL Server&#41;](../../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Anzeigen von Ereignissen und Protokollen für einen Failovercluster](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))  
  
-   [Get-ClusterLog-Failovercluster-Cmdlet](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wsfc-Notfall Wiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)   
 [Konfigurieren von Cluster-Quorum-nodeweight-Einstellungen](configure-cluster-quorum-nodeweight-settings.md)   
 [Failovercluster-Cmdlets in Windows PowerShell, aufgelistet nach Taskfokus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
