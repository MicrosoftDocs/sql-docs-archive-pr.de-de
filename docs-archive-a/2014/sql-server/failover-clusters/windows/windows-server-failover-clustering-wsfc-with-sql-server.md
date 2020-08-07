---
title: Windows Server-Failoverclustering (WSFC), mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Windows Server Failover Clustering (WSFC), with SQL Server
- WSFC, with SQL Server
- quorum [SQL Server]
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 79d2ea5a-edd8-4b3b-9502-96202057b01a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1fec03d7eb7a63353fd8eaea8c1e7051a306049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617552"
---
# <a name="windows-server-failover-clustering-wsfc-with-sql-server"></a>Windows Server-Failoverclustering (WSFC) mit SQL Server
   Bei *Windows Server-Failoverclustering* (WSFC) handelt es sich um eine Gruppe unabhängiger Server, die zur Steigerung der Verfügbarkeit von Anwendungen und Diensten zusammenarbeiten. [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] nutzt WSFC-Dienste und -Funktionen, um [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] - und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanzen zu unterstützen.

 

##  <a name="terms-and-definitions"></a><a name="TermsAndDefs"></a> Begriffe und Definitionen
 Wsfc-Cluster ein Windows Server-Failoverclustering (wsfc)-Cluster ist eine Gruppe unabhängiger Server, die zusammenarbeiten, um die Verfügbarkeit von Anwendungen und Diensten zu erhöhen.

 Die Failoverclusterinstanz ist eine Instanz eines Windows-Diensts, der eine IP-Adress Ressource, eine Netzwerknamen Ressource und zusätzliche Ressourcen verwaltet, die zum Ausführen von mindestens einer Anwendung oder einem Dienst erforderlich sind. Clients können mit den Netzwerknamen auf die Ressourcen in der Gruppe zugreifen. Dies ist vergleichbar mit dem Zugriff auf die Dienste auf einem physischen Server mithilfe eines Computernamens. Da es sich bei einer Failoverclusterinstanz jedoch um eine Gruppe handelt, kann dafür ein Failover zu einem anderen Knoten ohne Auswirkung auf den zugrunde liegenden Namen oder die Adresse ausgeführt werden.

 Knoten ein Microsoft Windows Server-System, das ein aktives oder inaktives Mitglied eines Server Clusters ist.

 Cluster Ressource eine physische oder logische Entität, die im Besitz eines Knotens sein, Online und offline geschaltet, zwischen Knoten verschoben und als Cluster Objekt verwaltet werden kann. Eine Clusterressource kann jeweils nur im Besitz eines einzelnen Knotens sein.

 Ressourcengruppe: eine Sammlung von Cluster Ressourcen, die als einzelnes Cluster Objekt verwaltet werden. In der Regel enthält eine Ressourcengruppe alle Clusterressourcen, die zum Ausführen einer bestimmten Anwendung oder eines Diensts erforderlich sind. Failover und Failback werden immer auf Ressourcengruppen angewendet.

 Ressourcenabhängigkeit eine Ressource, von der eine andere Ressource abhängt. Wenn Ressource A von Ressource B abhängt, dann ist B eine Abhängigkeit von A.

 Netzwerknamen Ressource ein logischer Servername, der als Cluster Ressource verwaltet wird. Eine Netzwerknamenressource muss mit einer IP-Adressressource verwendet werden.

 Bevorzugter Besitzer: ein Knoten, auf dem eine Ressourcengruppe bevorzugt ausgeführt wird. Jede Ressourcengruppe ist einer Liste von bevorzugten Besitzern zugeordnet, die nach Präferenz sortiert ist. Während eines automatischen Failovers wird die Ressourcengruppe in den nächsten bevorzugten Knoten in der Liste der bevorzugten Besitzer verschoben.

 Möglicher Besitzer: ein sekundärer Knoten, auf dem eine Ressource ausgeführt werden kann. Jede Ressourcengruppe ist einer Liste von möglichen Besitzern zugeordnet. Ein Failover für Ressourcengruppen kann nur zu Knoten erfolgen, die als mögliche Besitzer aufgeführt sind.

 Quorum Modus die Quorum Konfiguration in einem Failovercluster, die die Anzahl von Knoten Fehlern bestimmt, die der Cluster unterstützen kann.

 Erzwungenes Quorum: der Prozess zum Starten des Clusters, auch wenn nur eine Minderheit der für das Quorum erforderlichen Elemente kommuniziert.

 Weitere Informationen finden Sie im [Glossar zu Failoverclustern](/previous-versions/windows/desktop/MsCS/server-cluster-glossary)

##  <a name="overview-of-windows-server-failover-clustering"></a><a name="Overview"></a>Übersicht über Windows Server-Failoverclustering
 Windows Server-Failoverclustering stellt Infrastrukturfunktionen bereit, die Szenarien mit hoher Verfügbarkeit und Notfallwiederherstellung für gehostete Serveranwendungen, z. B. Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und Microsoft Exchange, unterstützen. Wenn ein Clusterknoten oder -dienst fehlschlägt, können die auf diesem Knoten gehosteten Dienste automatisch oder manuell auf einen anderen verfügbaren Knoten übertragen werden. Dieser Prozess wird als *Failover*bezeichnet.

 Die Knoten im WSFC-Cluster wirken zusammen, um diese Arten von Funktionen bereitzustellen:

-   **Verteilte Metadaten und Benachrichtigungen.** Metadaten des WSFC-Diensts und gehosteter Anwendungen sind in jedem Knoten im Cluster enthalten. Diese Metadaten enthalten WSFC-Konfiguration und -Status sowie Einstellungen der gehosteten Anwendung. Änderungen an den Metadaten oder am Status eines Knotens werden automatisch an die anderen Knoten im Cluster weitergegeben.

-   **Ressourcenverwaltung.** Einzelne Knoten im Cluster stellen möglicherweise physische Ressourcen bereit, z. B. direkt angeschlossene Speicher, Netzwerkschnittstellen und Zugriff auf freigegebenen Festplattenspeicher. Gehostete Anwendungen registrieren sich als Clusterressource und konfigurieren möglicherweise Start- und Integritätsabhängigkeiten von anderen Ressourcen.

-   **Systemüberwachung.** Die Integritätsermittlung zwischen den Knoten und des primären Knotens erfolgt durch eine Kombination aus getakteter Netzwerkkommunikation und Ressourcenüberwachung. Die allgemeine Integrität des Clusters wird von den Abstimmungen eines Quorums der Knoten im Cluster bestimmt.

-   **Failoverkoordination.** Jede Ressource wird zum Hosten auf einem primären Knoten konfiguriert und kann automatisch oder manuell an mindestens einen sekundären Knoten übertragen werden. Eine integritätsbasierte Failoverrichtlinie steuert die automatische Übertragung des Ressourcenbesitzes zwischen Knoten. Knoten und gehostete Anwendungen werden benachrichtigt, wenn ein Failover erfolgt, damit sie entsprechend reagieren können.

 Weitere Informationen finden Sie unter [Failovercluster in Windows Server 2008 R2](https://technet.microsoft.com/library/ff182338\(WS.10\).aspx)

##  <a name="sql-server-alwayson-technologies-and-wsfc"></a><a name="AlwaysOnWsfcTech"></a>SQL Server AlwaysOn-Technologien und wsfc
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]*AlwaysOn* ist eine neue Lösung für Hochverfügbarkeit und Notfall Wiederherstellung, die wsfc nutzt. AlwaysOn stellt eine integrierte, flexible Lösung bereit, die die Anwendungsverfügbarkeit erhöht, einen höheren Ertrag bei Hardwareinvestitionen bietet und die Bereitstellung und Verwaltung von Hochverfügbarkeit vereinfacht.

 Sowohl [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] als auch AlwaysOn-Failoverclusterinstanzen verwenden WSFC als Plattformtechnologie und registrieren Komponenten als WSFC-Clusterressourcen.  Verwandte Ressourcen werden in einer *Ressourcengruppe*kombiniert, für die Abhängigkeiten von anderen WSFC-Clusterressourcen festgelegt werden können. Der WSFC-Clusterdienst kann dann die Notwendigkeit eines Neustarts der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz ermitteln und signalisieren oder automatisch ein Failover zu einem anderen Serverknoten im WSFC-Cluster ausführen.

> [!IMPORTANT]
>  Um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn-Technologien voll ausnützen zu können, sollten Sie verschiedene WSFC-bezogene Vorraussetzungen erfüllen.
> 
>  Weitere Informationen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)

### <a name="instance-level-high-availability-with-alwayson-failover-cluster-instances"></a>Hohe Verfügbarkeit auf Instanzebene mit AlwaysOn-Failoverclusterinstanzen
 Eine AlwaysOn- *Failoverclusterinstanz* (FCI) ist eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz, die auf allen Knoten in einem WSFC-Cluster installiert wird. Dieser Instanzentyp besitzt Ressourcenabhängigkeiten für freigegebenen Festplattenspeicher (über Fibre Channel oder iSCSI SAN) und einen virtuellen Netzwerknamen. Der virtuelle Netzwerkname besitzt eine Ressourcenabhängigkeit von mindestens einer virtuellen IP-Adresse in jeweils unterschiedlichen Subnetzen. Der SQL Server-Dienst und der SQL Server-Agent-Dienst werden als Ressourcen registriert, und beide werden von der virtuellen Netzwerknamenressource abhängig gemacht.

 Im Fall eines Failovers überträgt der WSFC-Dienst den Besitz von Ressourcen einer Instanz auf einen festgelegten Failoverknoten. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz wird dann im Failoverknoten neu gestartet, und Datenbanken werden wie gewohnt wiederhergestellt. Nur jeweils ein einzelner Knoten im Cluster kann die FCI und zugrunde liegende Ressourcen hosten.

> [!NOTE]
>  Eine AlwaysOn-Failoverclusterinstanz erfordert symmetrischen freigegebenen Festplattenspeicher, z. B. ein Storage Area Network (SAN) oder eine SMB-Dateifreigabe.  Die freigegebenen Festplattenspeichervolumes müssen für alle potenziellen Failoverknoten im WSFC-Cluster verfügbar sein.

 Weitere Informationen finden Sie unter: [AlwaysOn-Failoverclusterinstanzen](always-on-failover-cluster-instances-sql-server.md)

### <a name="database-level-high-availability-with-sshadr"></a>Hohe Verfügbarkeit auf Datenbankebene mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]
 Eine *Verfügbarkeitsgruppe* ist eine Gruppe von Benutzerdatenbanken, die zusammen ein Failover ausführen. Eine Verfügbarkeitsgruppe besteht aus einem primären *Verfügbarkeitsreplikat* und einem bis vier sekundären Replikaten, die mittels protokollbasierter SQL Server-Datenverschiebung verwaltet werden, um den Datenschutz ohne freigegebenen Speicher zu gewährleisten. Jedes Replikat wird von einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in einem anderen Knoten des WSFC-Clusters gehostet. Die Verfügbarkeitsgruppe und ein entsprechender virtueller Netzwerkname werden als Ressourcen im WSFC-Cluster registriert.

 Ein *Verfügbarkeitsgruppenlistener* im Knoten des primären Replikats reagiert auf eingehende Clientanforderungen zum Herstellen einer Verbindung mit dem virtuellen Netzwerknamen. Auf Grundlage von Attributen in der Verbindungszeichenfolge wird jede Anforderung an die entsprechende [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz umgeleitet.

 Statt im Fall eines Failovers den Besitz von freigegebenen physischen Ressourcen an einen anderen Knoten zu übertragen, wird WSFC dazu genutzt, ein sekundäres Replikat auf einer anderen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz neu zu konfigurieren, sodass es zum primären Replikat der Verfügbarkeitsgruppe wird. Die virtuelle Netzwerknamenressource der Verfügbarkeitsgruppe wird dann auf diese Instanz übertragen.

 Nur eine einzelne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz kann jeweils das primäre Replikat der Datenbanken einer Verfügbarkeitsgruppe hosten. Alle zugeordneten sekundären Replikate müssen sich jeweils auf separaten Instanzen und die einzelnen Instanzen müssen sich in unterschiedlichen physischen Knoten befinden.

> [!NOTE]
>  Für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ist die Bereitstellung einer Failoverclusterinstanz oder die Verwendung von symmetrischem, freigegebenem Speicher (SAN oder SMB) nicht erforderlich.
> 
>  Eine Failoverclusterinstanz (FCI) kann zusammen mit einer Verfügbarkeitsgruppe verwendet werden, um die Verfügbarkeit eines Verfügbarkeitsreplikats zu verbessern. Um potenzielle Racebedingungen im WSFC-Cluster zu verhindern, wird jedoch automatisches Failover der Verfügbarkeitsgruppe zu oder von einem Verfügbarkeitsreplikat, das sich auf einer FCI befindet, nicht unterstützt.

 Weitere Informationen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).

##  <a name="wsfc-health-monitoring-and-failover"></a><a name="AlwaysOnWsfcHealth"></a>Wsfc-Systemüberwachung und-Failover
 Hohe Verfügbarkeit für eine AlwaysOn-Lösung wird durch proaktive Systemüberwachung physischer und logischer WSFC-Clusterressourcen zusammen mit automatischem Failover zu und Neukonfiguration von redundanter Hardware erreicht.  Ein Systemadministrator kann außerdem ein *manuelles Failover* einer Verfügbarkeitsgruppe oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz von einem Knoten zum anderen initiieren.

### <a name="failover-policies-for-nodes-failover-cluster-instances-and-availability-groups"></a>Failoverrichtlinien für Knoten, Failoverclusterinstanzen und Verfügbarkeitsgruppen
 Eine *Failoverrichtlinie* wird auf Ebene der WSFC-Clusterknoten, der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz (FCI) und der Verfügbarkeitsgruppe konfiguriert.  Diese Richtlinien können auf Grundlage des Schweregrads, der Dauer und Häufigkeit eines fehlerhaften Clusterressourcenstatus und eines fehlerhaften Knotenreaktionsverhaltens einen Dienstneustart oder ein *automatisches Failover* von Clusterressourcen von einem Knoten zum anderen auslösen. Außerdem kann die Verschiebung eines primären Verfügbarkeitsgruppenreplikats von einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz zu einer anderen ausgelöst werden.

 Failover eines Verfügbarkeitsgruppenreplikats wirkt sich nicht auf die zugrunde liegende [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz aus.  Bei einem Failover von einer FCI werden die gehosteten Verfügbarkeitsgruppenreplikate mit der Instanz verschoben.

 Weitere Informationen finden Sie unter [Failoverrichtlinie für Failoverclusterinstanzen](failover-policy-for-failover-cluster-instances.md) .

### <a name="wsfc-resource-health-detection"></a>WSFC-Ressourcenintegritätserkennung
 Jede Ressource in einem WSFC-Clusterknoten kann in regelmäßigen Abständen oder bedarfsgesteuert Status und Integrität melden. Verschiedene Umstände deuten möglicherweise auf Ressourcenfehler hin, z. B. Stromausfall, Datenträger- oder Arbeitsspeicherfehler, Netzwerkkommunikationsfehler oder nicht reagierende Dienste.

 WSFC-Clusterressourcen wie Netzwerke, Speicher oder Dienste können so konfiguriert werden, dass sie voneinander abhängig sind. Die kumulierte Integrität einer Ressource wird ermittelt, indem für die Integrität nacheinander ein Rollup mit der Integrität jeder ihrer Ressourcenabhängigkeiten ausgeführt wird.

### <a name="wsfc-inter-node-health-detection-and-quorum-voting"></a>WSFC-Integritätsermittlung zwischen Knoten und Quorumabstimmung
 Jeder Knoten in einem WSFC-Cluster nimmt an regelmäßiger getakteter Kommunikation teil, um den Integritätsstatus des Knotens für die anderen Knoten freizugeben. Bei nicht reagierenden Knoten wird der Status als fehlerhaft betrachtet.

 Ein *Quorum* knotensatz wird aus der Mehrheit der Abstimmungsknoten und -zeugen im WSFC-Cluster gebildet. Die allgemeine Integrität und der Status eines WSFC-Clusters wird mithilfe einer regelmäßigen *Quorumabstimmung*ermittelt. Das Vorhandensein eines Quorums bedeutet, dass der Cluster fehlerfrei ist und die Fehlertoleranz auf Knotenebene bereitstellen kann.

 Ein *Quorummodus* wird auf WSFC-Clusterebene konfiguriert, die die Methodik für die Quorumabstimmung vorgibt und bestimmt, wann ein automatisches Failover ausgeführt oder der Cluster offline geschaltet wird.

> [!TIP]
>  Es wird immer empfohlen eine ungerade Anzahl an Quorumstimmen in einem WSFC-Cluster empfohlen.  Für den Zweck der Quorumabstimmung muss [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht auf allen Knoten im Cluster installiert sein. Ein zusätzlicher Server kann als Quorumelement dienen. Alternativ kann das WSFC-Quorummodell zur Verwendung einer Remotedateifreigabe als Tiebreaker konfiguriert werden.
> 
>  Weitere Informationen finden Sie unter [wsfc-Quorum Modi und Abstimmungs Konfiguration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)

### <a name="disaster-recovery-through-forced-quorum"></a>Notfallwiederherstellung durch erzwungenes Quorum
 Abhängig vom Betriebsverfahren und von der WSFC-Clusterkonfiguration können Sie sowohl automatische als auch manuelle Failovers auslösen und dennoch eine stabile, fehlertolerante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn-Lösung betreiben. Falls jedoch ein Quorum der freigegebenen Abstimmungsknoten im WSFC-Cluster nicht kommunizieren kann oder bei der Integritätsüberprüfung des WSFC-Clusters ein anderer Fehler zurückgegeben wird, wird der WSFC-Cluster möglicherweise offline geschaltet.

 Wird der WSFC-Cluster wegen eines nicht geplanten Notfalls oder aufgrund eines persistenten Hardware- oder Kommunikationsfehlers offline geschaltet, ist manueller Eingriff durch den Administrator erforderlich, um ein *Quorum zu erzwingen* und die überdauernden Clusterknoten in einer nicht fehlertoleranten Konfiguration wieder online zu schalten.

 Danach muss außerdem eine Reihe von Schritten ausgeführt werden, um den WSFC-Cluster neu zu konfigurieren, die betroffenen Datenbankreplikate wiederherzustellen und ein neues Quorum einzurichten.

 Informationen zur Erzwingung des Quorums finden Sie unter [WSFC-Notfallwiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).

##  <a name="relationship-of-sql-server-alwayson-components-to-wsfc"></a><a name="AlwaysOnWsfcRelationship"></a>Beziehung zwischen SQL Server AlwaysOn-Komponenten und wsfc
 Zwischen den Funktionen und Komponenten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn und WSFC liegen verschiedene Beziehungsstufen vor.

 AlwaysOn-Verfügbarkeitsgruppen werden auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanzen gehostet.
Eine Clientanforderung, in der zum Herstellen einer Verbindung mit einer primären oder sekundären Datenbank ein logischer Netzwerkname für einen Verfügbarkeitsgruppenlistener angegeben wird, wird an den entsprechenden Instanznetzwerknamen der zugrunde liegenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz umgeleitet.

 SQL Server-Instanzen werden aktiv in einem einzelnen Knoten gehostet.
Eine eigenständige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz (sofern vorhanden) befindet sich immer in einem einzelnen Knoten mit einem statischen Instanznetzwerknamen.  Eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz (sofern vorhanden) ist für einen von mindestens zwei möglichen Failoverknoten mit einem virtuellen Instanznetzwerknamen aktiv.

 Knoten sind Mitglieder eines WSFC-Clusters.
Metadaten und Status der WSFC-Konfiguration für alle Knoten werden in jedem Knoten gespeichert. Jeder Server kann asymmetrischen Speicher oder freigegebene Speichervolumes (SAN) für Benutzer- oder Systemdatenbanken bereitstellen. Jeder Server besitzt mindestens eine physische Netzwerkschnittstelle in mindestens einem IP-Subnetz.

 Der WSFC-Dienst überwacht die Integrität und verwaltet die Konfiguration für eine Gruppe von Servern.
Der Dienst Windows Server-Failovercluster (WSFC) gibt Änderungen an den Metadaten und am Status der WSFC-Konfiguration an alle Knoten im Cluster weiter. Partielle Metadaten und Zustände können auf einer WSFC-Remotedateifreigabe (Quorumfreigabe) gespeichert werden. Zwei oder mehr aktive Knoten oder Zeugen bilden ein Quorum zum Bestimmen der Integrität des WSFC-Clusters.

 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Registrierungsschlüssel sind Unterschlüssel des WSFC-Clusters.
Wenn Sie einen WSFC-Cluster löschen und neu erstellen, müssen Sie die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf jeder Serverinstanz, die auf dem ursprünglichen WSFC-Cluster für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aktiviert war, deaktivieren und erneut aktivieren. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

 ![Abbildung zum SQL Server Always On-Komponentenkontext](../../../database-engine/media/alwaysoncomponentcontextdiagram.gif "Abbildung zum SQL Server Always On-Komponentenkontext")

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben

-   [Anzeigen von Cluster-Quorum-NodeWeight-Einstellungen](view-cluster-quorum-nodeweight-settings.md)

-   [Konfigurieren von Cluster-Quorum-NodeWeight-Einstellungen](configure-cluster-quorum-nodeweight-settings.md)

-   [Erzwingen des Starts eines Clusters ohne Quorum](force-a-wsfc-cluster-to-start-without-a-quorum.md)

##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte

-   [Windows Server-Technologien: Failovercluster](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)

-   [Failovercluster in Windows Server 2008 R2](https://technet.microsoft.com/library/ff182338\(WS.10\).aspx)

-   [Anzeigen von Ereignissen und Protokollen für einen Failovercluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)

-   [Get-ClusterLog-Failovercluster-Cmdlet](https://technet.microsoft.com/library/ee461045.aspx)

## <a name="see-also"></a>Weitere Informationen
 [AlwaysOn-Failoverclusterinstanzen (SQL Server)](always-on-failover-cluster-instances-sql-server.md) [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) [wsfc-Quorum Modi und Abstimmungs Konfiguration &#40;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) SQL Server&#41;[Failoverrichtlinie für Failoverclusterinstanzen](failover-policy-for-failover-cluster-instances.md) [wsfc-Notfall Wiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)


