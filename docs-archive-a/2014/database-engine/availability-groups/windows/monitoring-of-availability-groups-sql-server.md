---
title: Überwachen von Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da41c6d629ffb57749ae9c13e715f535e98aa3da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616186"
---
# <a name="monitoring-of-availability-groups-sql-server"></a>Überwachen von Verfügbarkeitsgruppen (SQL Server)
  Zum Überwachen der Eigenschaften und des Status einer AlwaysOn-Verfügbarkeitsgruppe können Sie die folgenden Tools verwenden.  
  
|Tool|Kurzbeschreibung|Links|  
|----------|-----------------------|-----------|  
|Systemcenter-Überwachungspaket für SQL Server|Das Überwachungspaket für SQL Server (SQLMP) ist die empfohlene Lösung, mit der IT-Administratoren Verfügbarkeitsgruppen sowie Verfügbarkeitsreplikate und Verfügbarkeitsdatenbanken überwachen. Die auf [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] abgestimmten Überwachungsfunktionen umfassen:<br /><br /> Automatische Erkennung von Verfügbarkeitsgruppen, Verfügbarkeitsreplikaten und Verfügbarkeitsdatenbank unter Hunderten von Computern. Dies ermöglicht Ihnen die einfache Nachverfolgung des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Inventars.<br /><br /> Umfassende Warnungs- und Tickererstellungsfunktionen durch den System Center Operations Manager (SCOM). Diese Funktionen liefern detaillierte Informationen zur schnelleren Behebung eines Problems.<br /><br /> Eine benutzerdefinierte Erweiterung der AlwaysOn-Systemüberwachung unter Verwendung der richtlinienbasierten Verwaltung.<br /><br /> Integritätsrollups von Verfügbarkeitsdatenbanken auf Verfügbarkeitsreplikate.<br /><br /> Benutzerdefinierte Aufgaben zur Verwaltung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] über die System Center Operations Manager-Konsole.|Hier können Sie das Überwachungspaket (SQLServerMP.msi) und das *SQL Server Management Pack-Handbuch für System Center Operations Manager* (SQLServerMPGuide.doc) herunterladen:<br /><br /> [Systemcenter-Überwachungspaket für SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Katalog und dynamische Verwaltungssichten stellen zahlreiche Informationen zu den Verfügbarkeitsgruppen und deren Replikaten, Datenbanken, Listenern und zur WSFC-Clusterumgebung bereit.|[Überwachen von Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Der Bereich **Details zum Objekt-Explorer** zeigt grundlegende Informationen zu den Verfügbarkeitsgruppen an, die auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet werden, mit der eine Verbindung besteht.<br /><br /> Tipp: Verwenden Sie diesen Bereich, um mehrere Verfügbarkeitsgruppen, Replikate oder Datenbanken auszuwählen und routinemäßige administrative Aufgaben auf den ausgewählten Objekten auszuführen, beispielsweise das Entfernen von mehreren Verfügbarkeitsreplikaten oder Datenbanken aus einer Verfügbarkeitsgruppe.|[Verwenden der Details zum Objekt-Explorer zum Überwachen von Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|**Eigenschaftendialogfelder** ermöglichen es, die Eigenschaften von Verfügbarkeitsgruppen, Replikaten oder Listenern anzuzeigen und, in einigen Fällen, deren Werte zu ändern.|[Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)<br /><br /> [Anzeigen von Verfügbarkeitsreplikateigenschaften &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)<br /><br /> [Anzeigen von Eigenschaften des Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)|  
|Systemmonitor|Das Leistungsobjekt **SQL Server:Verfügbarkeitsreplikat** enthält Leistungsindikatoren, die Informationen zu Verfügbarkeitsreplikaten bereitstellen.|[SQL Server, Verfügbarkeitsreplikat](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Systemmonitor|Das Leistungsobjekt **SQL Server:Datenbankreplikat** beinhaltet Leistungsindikatoren, die Informationen zu den sekundären Verfügbarkeitsdatenbanken eines bestimmten sekundären Replikats bereitstellen.<br /><br /> Das **SQLServer:Databases** -Objekt in SQL Server enthält u. a. Leistungsindikatoren zum Überwachen von Transaktionsprotokollaktivitäten. Die folgenden Indikatoren sind besonders für die Überwachung der Transaktionsprotokollaktivität von Verfügbarkeitsdatenbanken relevant: **Schreibdauer für Protokollleerungen (ms)** , **Protokollleerungen/Sekunde**, **Protokollpool-Cachefehlversuche/Sekunde**, **Protokollpool-Lesevorgänge auf dem Datenträger/Sekunde**und **Protokollpoolanforderungen/Sekunde**.|[SQL Server, Datenbankreplikat](../../../relational-databases/performance-monitor/sql-server-database-replica.md) und [SQL Server, Datenbank-Objekt](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Das AlwaysOn-Zustandsmodell Teil 1 – Zustandsmodellarchitektur](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-1-health-model-architecture)  
  
     [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
     [Überwachen des AlwaysOn-Zustands mit PowerShell - Teil 1: Übersicht über grundlegende Cmdlets](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
     [Überwachen des AlwaysOn-Zustands mit PowerShell - Teil 2: Verwendung erweiterter Cmdlets](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-2-advanced-cmdlet-usage)  
  
     [Überwachen des AlwaysOn-Zustands mit PowerShell - Teil 3: Eine einfache Überwachungsanwendung](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
     [Überwachen des AlwaysOn-Zustands mit PowerShell - Teil 4: Integration in SQL Server-Agent](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen Katalog Sichten &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql)   
 [AlwaysOn-Verfügbarkeitsgruppen dynamischen Verwaltungs Sichten und-Funktionen &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions)   
 [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeits Gruppe &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Automatische Seiten Reparatur &#40;für Verfügbarkeits Gruppen und Daten Bank Spiegelung&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
