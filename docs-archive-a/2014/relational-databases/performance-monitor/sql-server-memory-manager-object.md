---
title: SQL Server, Speicher-Manager-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06b58b9b6bb8a5c13e0b220ba9eeea5818682abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609827"
---
# <a name="sql-server-memory-manager-object"></a>SQL Server, Speicher-Manager-Objekt
  Das **Speicher-Manager** -Objekt in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die gesamte Speicherauslastung des Servers überwachen können. Das Überwachen der gesamten Speicherauslastung des Servers zur Messung der Benutzeraktivität und der Ressourcennutzung kann Ihnen dabei helfen, Leistungsengpässe zu erkennen. Durch Überwachen des Arbeitsspeichers, der von einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, können Sie Folgendes ermitteln:  
  
-   Ob es zu Engpässen kommt, da nicht genügend Arbeitsspeicher vorhanden ist, um Daten, auf die häufig zugegriffen wird, im Cache zu speichern. In diesem Fall muss [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Daten vom Datenträger abrufen.  
  
-   Ob die Abfrageleistung durch Hinzufügen von Arbeitsspeicher oder durch Zuordnen von zusätzlichem Arbeitsspeicher für den Datencache bzw. für interne Strukturen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbessert werden kann.  
  
## <a name="memory-manager-counters"></a>Speicher-Manager-Leistungsindikatoren  
 In dieser Tabelle werden die Leistungsindikatoren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-**Speicher-Managers** beschrieben.  
  
|Speicher-Manager-Leistungsindikatoren von SQL Server|BESCHREIBUNG|  
|----------------------------------------|-----------------|  
|**Verbindungsspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Aufrechterhaltung von Verbindungen verwendet.|  
|**Datenbankcachespeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für den Datenbankseitencache verwendet.|  
|**Freier Arbeitsspeicher (KB)**|Gibt den Umfang des zugesicherten Arbeitsspeichers an, der derzeit nicht vom Server verwendet wird.|  
|**Zugewiesener Arbeitsbereichsspeicher (KB)**|Gibt den Gesamtumfang des Arbeitsspeichers an, der derzeit dem Ausführen von Prozessen, z. B. Hash-, Sortier-, Massenkopier- und Indexerstellungsvorgängen, zugewiesen ist.|  
|**Sperrblöcke**|Gibt die aktuelle Anzahl der Sperrblöcke an, die auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrblock stellt eine einzelne gesperrte Ressource, wie z. B. eine Tabelle, Seite oder Zeile, dar.|  
|**Zugeordnete Sperrblöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrblöcke an. Beim Starten des Servers hängen die Anzahl der zugeordneten Sperrblöcke und die Anzahl der zugeordneten Sperrenbesitzerblöcke von der Konfigurationsoption **Sperren** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab. Wenn mehr Sperrblöcke benötigt werden, steigt der Wert.|  
|**Sperrspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für Sperren verwendet.|  
|**Sperrenbesitzerblöcke**|Gibt die Anzahl der Sperrenbesitzerblöcke an, die zurzeit auf dem Server verwendet werden. Wird regelmäßig aktualisiert. Ein Sperrenbesitzerblock stellt den Besitz einer Sperre für ein Objekt durch einen einzelnen Thread dar. Wenn also drei Threads jeweils über eine freigegebene Sperre (S) für eine Seite verfügen, liegen drei Sperrenbesitzerblöcke vor.|  
|**Zugeordnete Sperrenbesitzerblöcke**|Gibt die aktuelle Anzahl der zugeordneten Sperrenbesitzerblöcke an. Beim Starten des Servers hängen die Anzahl der zugeordneten Sperrenbesitzerblöcke und die Anzahl der zugeordneten Sperrblöcke von der Konfigurationsoption **Sperren** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab. Wenn mehr Sperrenbesitzerblöcke benötigt werden, steigt der Wert dynamisch an.|  
|**Maximaler Arbeitsbereichsspeicher (KB)**|Gibt den maximalen Umfang des Arbeitsspeichers an, der für das Ausführen von Prozessen, z. B. Hash-, Sortier,- Massenkopier- und Indexerstellungsvorgängen, zur Verfügung steht.|  
|**Ausstehende Speicherzuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die erfolgreich eine Zuweisung für Arbeitsbereichsspeicher erhalten haben.|  
|**Ausstehende Speicherzuweisungen**|Gibt die Gesamtanzahl der Prozesse an, die auf eine Zuweisung von Arbeitsbereichsspeicher warten.|  
|**Optimiererspeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für die Abfrageoptimierung verwendet.|  
|**Reservierter Serverarbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server für die zukünftige Verwendung reserviert hat. Dieser Leistungsindikator gibt den derzeit nicht verwendeten Umfang des ursprünglich zugewiesenen Arbeitsspeichers an, der in **Erteilter Arbeitsbereichsspeicher (KB)** angezeigt wird.|  
|**SQL-Cachespeicher (KB)**|Gibt den Gesamtumfang des dynamischen Arbeitsspeichers an, den der Server für den dynamischen SQL-Cache verwendet.|  
|**Gestohlener Serverarbeitsspeicher (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server derzeit für andere Zwecke als Datenbankseiten verwendet.|  
|**Zielserverspeicher (KB)**|Gibt den idealen Umfang des Arbeitsspeichers an, den der Server belegen kann.|  
|**Serverspeicher gesamt (KB)**|Gibt den Umfang des Arbeitsspeichers an, den der Server mit dem Speicher-Manager zugesichert hat.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, Puffer-Manager-Objekt](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
