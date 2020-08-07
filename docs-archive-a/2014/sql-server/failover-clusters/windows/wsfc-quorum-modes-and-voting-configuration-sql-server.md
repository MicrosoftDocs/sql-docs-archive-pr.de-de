---
title: WSFC-Quorummodi und Abstimmungskonfiguration (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: ca0d59ef-25f0-4047-9130-e2282d058283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1d5ad992c59f252f485f2d65451a72f150bef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617550"
---
# <a name="wsfc-quorum-modes-and-voting-configuration-sql-server"></a>WSFC-Quorummodi und Abstimmungskonfiguration (SQL Server)
  Sowohl [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] als auch AlwaysOn-Failoverclusterinstanzen (FCIs) nutzen Windows Server Failover Clustering (WSFC) als Plattformtechnologie.  WSFC verwendet einen auf Quorum basierenden Ansatz zum Überwachen des Gesamtclusterzustands und Maximieren der Fehlertoleranz auf Knotenebene. Umfassende Kenntnisse in Bezug auf WSFC-Quorummodi und die Knotenabstimmungskonfiguration sind sehr wichtig für das Entwerfen, Betreiben und Warten (Fehlerbehandlung) der AlwaysOn-Lösung für Hochverfügbarkeit und für die Notfallwiederherstellung.  
  
 **In diesem Thema:**  
  
-   [Clusterzustandserkennung von Quorum](#ClusterHealthDetectionbyQuorum)  
  
-   [Quorum Modi](#QuorumModes)  
  
-   [Abstimmungsknoten und Nicht-Abstimmungsknoten](#VotingandNonVotingNodes)  
  
-   [Empfohlene Anpassungen an der Quorumabstimmung](#RecommendedAdjustmentstoQuorumVoting)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="cluster-health-detection-by-quorum"></a><a name="ClusterHealthDetectionbyQuorum"></a>Cluster Integritäts Erkennung durch Quorum  
 Jeder Knoten in einem WSFC-Cluster nimmt an regelmäßiger getakteter Kommunikation teil, um den Integritätsstatus des Knotens für die anderen Knoten freizugeben. Bei nicht reagierenden Knoten wird der Status als fehlerhaft betrachtet.  
  
 Ein *Quorum* knotensatz wird aus der Mehrheit der Abstimmungsknoten und -zeugen im WSFC-Cluster gebildet. Die allgemeine Integrität und der Status eines WSFC-Clusters wird mithilfe einer regelmäßigen *Quorumabstimmung*ermittelt.  Das Vorhandensein eines Quorums bedeutet, dass der Cluster fehlerfrei ist und die Fehlertoleranz auf Knotenebene bereitstellen kann.  
  
 Die Abwesenheit eines Quorums gibt an, dass der Cluster nicht fehlerfrei ist.  Der Gesamtzustand des WSFC-Clusters muss aufrechterhalten werden, um sicherzustellen, dass fehlerfreie sekundäre Knoten für das Failover von Primärknoten verfügbar sind.  Wenn die Quorumabstimmung negativ ausfällt, wird der WSFC-Cluster als Vorsichtsmaßnahme in den Offlinezustand versetzt.  Dies führt auch dazu, dass alle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanzen, die beim Cluster registriert sind, beendet werden.  
  
> [!IMPORTANT]  
>  Wenn ein WSFC-Cluster aufgrund eines Quorumfehlers in den Offlinezustand versetzt wird, ist ein manueller Eingriff erforderlich, um den Onlinezustand wiederherzustellen.  
>   
>  Weitere Informationen finden Sie unter [wsfc-Notfall Wiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).  
  
##  <a name="quorum-modes"></a><a name="QuorumModes"></a>Quorum Modi  
 Ein *Quorummodus* wird auf der WSFC-Clusterebene konfiguriert, mit dem die Methodik für die Quorumabstimmung vorgegeben wird.  Das Failovercluster-Manager-Hilfsprogramm empfiehlt basierend auf der Anzahl von Knoten im Cluster einen Quorummodus.  
  
 Die folgenden Quorummodi können verwendet werden, um zu bestimmen, woraus sich ein Quorum von Abstimmungen zusammensetzt:  
  
-   **Knoten Mehrheit:** Mehr als die Hälfte der Abstimmungsknoten im Cluster müssen positiv abstimmen, damit der Cluster als fehlerfrei eingestuft wird.  
  
-   **Knoten-und Dateifreigabe Mehrheit.** Dies ähnelt dem Knotenmehrheit-Quorummodus, jedoch mit der Ausnahme, dass eine Remotedateifreigabe auch als Abstimmungszeuge konfiguriert wird und die Konnektivität von Knoten zu dieser Freigabe auch als positive Abstimmung gezählt wird.  Mehr als die Hälfte der möglichen Abstimmungen muss positiv ausfallen, damit der Cluster als fehlerfrei angesehen wird.  
  
     Als bewährte Methode sollte sich die Zeugendateifreigabe nicht auf einem Knoten im Cluster befinden und für alle Knoten im Cluster sichtbar sein.  
  
-   **Knoten-und Datenträger Mehrheit.** Ähnelt dem Knotenmehrheit-Quorummodus, jedoch mit der Ausnahme, dass eine Clusterressource für einen freigegebenen Datenträger auch als Abstimmungszeuge festgelegt wird und die Konnektivität von Knoten zu diesem freigegebenen Datenträger auch als positive Abstimmung betrachtet wird.  Mehr als die Hälfte der möglichen Abstimmungen muss positiv ausfallen, damit der Cluster als fehlerfrei angesehen wird.  
  
-   **Nur Datenträger:** Eine Clusterressource für einen freigegebenen Datenträger wird als Zeuge festgelegt, und die Konnektivität von Knoten zu diesem freigegebenen Datenträger wird als positive Abstimmung betrachtet.  
  
> [!TIP]  
>  Beim Verwenden einer asymmetrische Speicherkonfiguration für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]sollten Sie den Knotenmehrheit-Quorummodus generell verwenden, wenn Sie über eine ungerade Zahl von Abstimmungsknoten verfügen, oder den Quorummodus Knoten- und Dateifreigabemehrheit, wenn Sie über eine gerade Zahl von Abstimmungsknoten verfügen.  
  
##  <a name="voting-and-non-voting-nodes"></a><a name="VotingandNonVotingNodes"></a>Abstimmungs Knoten und nicht-Abstimmungs Knoten  
 Standardmäßig wird jeder Knoten im WSFC-Cluster als Mitglied des Clusterquorums einbezogen. Jeder Knoten verfügt bei der Ermittlung des Gesamtclusterzustands über eine (1) Stimme, und jeder Knoten versucht ununterbrochen, ein Quorum zu erzielen.  Die Quorumdiskussion hat zu diesem Zeitpunkt eine sorgfältige Qualifizierung des Satzes an WSFC-Clusterknoten durchgeführt, die als *Abstimmungsknoten*über den Clusterzustand abstimmen.  
  
 Kein einzelner Knoten in einem WSFC-Cluster kann definitiv bestimmen, dass der Cluster als Ganzes fehlerfrei oder nicht fehlerfrei ist.  Aus Sicht der einzelnen Knoten können einige andere Knoten jederzeit offline sein, sich in einem Failoverprozess befinden oder aufgrund eines Netzwerkkommunikationsfehlers nicht reagieren.  Eine Hauptfunktion der Quorumabstimmung ist die Ermittlung, ob der scheinbare Status der einzelnen Knoten im WSFC-Cluster tatsächlich dem Ist-Zustand dieser Knoten entspricht.  
  
 Für alle Quorummodelle mit Ausnahme von „Nur Datenträger“ hängt die Effektivität einer Quorumabstimmung von einer zuverlässigen Kommunikation zwischen allen Abstimmungsknoten im Cluster ab. Die Netzwerkkommunikation zwischen Knoten in demselben physischen Subnetz sollte als zuverlässig angesehen werden. Die Quorumabstimmung sollte als vertrauenswürdig eingestuft werden.  
  
 Wenn ein Knoten in einem anderen Subnetz für eine Quorumabstimmung jedoch als nicht reagierend angesehen wird, während der Knoten eigentlich online und auch sonst fehlerfrei ist, liegt dies in den meisten Fällen an einem Netzwerkkommunikationsfehler zwischen Subnetzen.  Je nach Clustertopologie, Quorummodus und Konfiguration der Failoverrichtlinien kann bei dem Netzwerkkommunikationsfehler ggf. mehr als ein Satz (oder eine Teilmenge) mit Abstimmungsknoten erstellt werden.  
  
 Wenn mehr als eine Teilmenge mit Abstimmungsknoten selbständig ein Quorum erzielen kann, wird dies als *Split-Brain-Szenario*bezeichnet.  Bei solch einem Szenario kann es vorkommen, dass sich die Knoten in den einzelnen Quoren unterschiedlich verhalten und in Konflikt miteinander stehen.  
  
> [!NOTE]  
>  Das Split-Brain-Szenario ist nur möglich, wenn ein Systemadministrator manuell einen erzwungenen Quorumvorgang ausführt, oder in sehr seltenen Fällen bei einem erzwungenen Failover, bei dem der Quorumknotensatz explizit unterteilt wird.  
  
 Um die Quorum Konfiguration zu vereinfachen und die Betriebszeit zu erhöhen, empfiehlt es sich, die *nodeweight* -Einstellung der einzelnen Knoten anzupassen, damit die Stimme des Knotens nicht zum Quorum gezählt wird.  
  
> [!IMPORTANT]  
>  Um NodeWeight-Einstellungen zu verwenden, muss der folgende Hotfix im WSFC-Cluster für alle Server übernommen werden:  
>   
>  [KB2494036](https://support.microsoft.com/kb/2494036): ein Hotfix ist verfügbar, mit dem Sie einen Cluster Knoten konfigurieren können, der keine Quorum Abstimmung in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] und in hat.[!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
##  <a name="recommended-adjustments-to-quorum-voting"></a><a name="RecommendedAdjustmentstoQuorumVoting"></a>Empfohlene Anpassungen an der Quorum Abstimmung  
 Beachten Sie beim Aktivieren oder Deaktivieren der Stimmberechtigung eines bestimmten WSFC-Knotens folgende Richtlinien:  
  
-   **Standardmäßig keine Stimme.** Die einzelnen Knoten benötigen eine ausdrückliche Berechtigung, um stimmberechtigt zu sein.  
  
-   **Alle primären Replikate einschließen.** Jeder WSFC-Knoten, der das primäre Replikat einer Verfügbarkeitsgruppe hostet oder als bevorzugter Besitzer einer Failoverclusterinstanz fungiert, sollte über eine Stimme verfügen.  
  
-   **Schließen Sie mögliche Besitzer von automatischen Failovers ein.** Jeder Knoten, der nach einem automatischen Failover einer Verfügbarkeitsgruppe oder einem FCI-Failover zum Host eines primären Replikats werden kann, sollte über eine Stimme verfügen. Wenn der WSFC-Cluster nur eine Verfügbarkeitsgruppe umfasst und Verfügbarkeitsreplikate nur von eigenständigen Instanzen gehostet werden, bezieht sich diese Regel nur auf das sekundäre Replikat, das als automatisches Failoverziel fungiert.  
  
-   **Schließen Sie sekundäre Websiteknoten aus.** Generell sollten Sie WSFC-Knoten, die sich an einem sekundären Standort für die Notfallwiederherstellung befinden, keine Stimme geben.  Es ist nicht wünschenswert, dass Knoten auf der sekundären Website an einer Entscheidung beteiligt sind, bei der es um das Versetzen des Clusters in den Offlinezustand geht, wenn für die primäre Website kein Fehler vorliegt.  
  
-   **Ungerade Zahl von Abstimmungen:** Fügen Sie dem Cluster bei Bedarf eine Zeugendateifreigabe, einen Zeugenknoten oder einen Zeugendatenträger hinzu, und passen Sie den Quorummodus an, um mögliche Gleichstände bei der Quorumabstimmung zu verhindern.  
  
-   **Bewerten Sie die Stimmenzuweisungen nach einem Failover neu.** Es ist nicht wünschenswert, ein Failover in eine Clusterkonfiguration auszuführen, die kein fehlerfreies Quorum unterstützt.  
  
> [!IMPORTANT]
>  Bei der Überprüfung der Konfiguration der WSFC-Quorumabstimmung zeigt der AlwaysOn-Verfügbarkeitsgruppen-Assistent eine Warnung an, wenn eine der folgenden Bedingungen zutrifft:  
> 
>  -   Der Clusterknoten, von dem das primäre Replikat gehostet wird, verfügt über keine Stimme.  
> -   Ein sekundäres Replikat ist für das automatische Failover konfiguriert, und der zugehörige Clusterknoten verfügt über keine Stimme.  
> -   [KB2494036](https://support.microsoft.com/kb/2494036) ist nicht auf allen Clusterknoten installiert, die Verfügbarkeitsreplikate hosten. Das Patch ist erforderlich, um Clusterknoten in standortübergreifenden Bereitstellungen Stimmen zu gewähren bzw. Stimmen zu entziehen. In Bereitstellungen mit einem Standort ist das Patch in der Regel nicht erforderlich, und die Warnung kann ignoriert werden.  
> 
> [!TIP]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Es werden mehrere dynamische Verwaltungssichten (DMVs) für das System verfügbar gemacht, mit denen Sie Einstellungen in Bezug auf die WSFC-Clusterkonfiguration und die Knotenquorumabstimmung verwalten können.  
> 
>  Weitere Informationen finden Sie unter  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Anzeigen von Cluster-Quorum-NodeWeight-Einstellungen](view-cluster-quorum-nodeweight-settings.md)  
  
-   [Konfigurieren von Cluster-Quorum-NodeWeight-Einstellungen](configure-cluster-quorum-nodeweight-settings.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Quorum vote configuration check in AlwaysOn Availability Group Wizards](https://blogs.msdn.com/b/sqlalwayson/archive/2012/03/13/quorum-vote-configuration-check-in-alwayson-availability-group-wizards-andy-jing.aspx)  
  
-   [Windows Server-Technologien: Failovercluster](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)  
  
-   [Schritt-für-Schritt-Anleitung für Failovercluster: Konfigurieren des Quorums in einem Failovercluster](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wsfc-Notfall Wiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)   
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
