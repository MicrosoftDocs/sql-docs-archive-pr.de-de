---
title: Servereigenschaften (Seite „Verbindungen“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.connections.f1
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80943bc542209fd34cf83e8db7aa76becd04194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723034"
---
# <a name="server-properties-connections-page"></a>Servereigenschaften (Seite Verbindungen)
  Mithilfe dieser Seite können Sie die Verbindungsoptionen anzeigen und ändern.  
  
## <a name="connections"></a>Verbindungen  
 **Maximale Anzahl von gleichzeitigen Verbindungen (0 = unbegrenzt)**  
 Wenn diese Option auf einen Wert ungleich null festgelegt ist, wird die Anzahl der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugelassenen Verbindungen entsprechend begrenzt.  
  
> [!CAUTION]  
>  Wenn dieser Wert sehr klein ist, z. B. 1 oder 2, könnten dadurch Administratoren daran gehindert werden, eine Verbindung mit dem Server zwecks Verwaltung herzustellen. Die dedizierte Administratorverbindung kann allerdings immer hergestellt werden.  
  
## <a name="default-connection-options"></a>Standardverbindungsoptionen  
 **Default connection options**  
 Gibt die Standardverbindungsoptionen an, die in der folgenden Tabelle beschrieben werden.  
  
|Konfigurationsoption|BESCHREIBUNG|  
|--------------------------|-----------------|  
|**Verzögerte Einschränkungsüberprüfung deaktivieren**|Steuert die zwischenzeitliche oder verzögerte Einschränkungsüberprüfung.|  
|**Implizite Transaktionen**|Steuert den impliziten Start einer Transaktion, wenn eine Anweisung ausgeführt wird.|  
|**Schließen des Cursors nach Commit**|Steuert das Cursorverhalten nach einem Commitvorgang.|  
|**ANSI-Warnungen**|Steuert das Abschneiden und NULL in Aggregatwarnungen.|  
|**ANSI-Auffüllung**|Steuert die Auffüllung bei Variablen fester Länge.|  
|**ANSI NULLS**|Steuert die Behandlung von `NULL` beim Verwenden von Gleichheitsoperatoren.|  
|**Abbruch bei arithmetischem Fehler**|Beendet eine Abfrage, wenn während der Abfrage ein Überlauffehler oder ein Fehler aufgrund einer Division durch Null auftritt.|  
|**Arithmetischen Fehler ignorieren**|Gibt NULL zurück, wenn während der Abfrage ein Überlauffehler oder ein Fehler aufgrund einer Division durch null auftritt.|  
|**Bezeichner in Anführungszeichen**|Unterscheidet beim Auswerten eines Ausdrucks zwischen einfachen und doppelten Anführungszeichen.|  
|**keine Anzahl**|Deaktiviert die Meldung über die Anzahl der betroffenen Zeilen, die am Ende jeder Anweisung zurückgegeben wird.|  
|**'ANSI NULL Default' aktiviert**|Ändert das Sitzungsverhalten so, dass bei der NULL-Zulässigkeit die ANSI-Kompatibilität verwendet wird. Neue Spalten ohne ausdrückliche NULL-Zulässigkeit werden dann so definiert, dass sie NULL-Werte zulassen.|  
|**'ANSI NULL Default' deaktiviert**|Ändert das Sitzungsverhalten so, dass bei der NULL-Zulässigkeit keine ANSI-Kompatibilität verwendet wird. Neue Spalten ohne ausdrückliche NULL-Zulässigkeit werden dann so definiert, dass sie NULL-Werte nicht zulassen.|  
|**Verketten von NULL-Werten ergibt NULL**|Gibt NULL zurück, wenn ein NULL-Wert mit einer Zeichenfolge verkettet wird.|  
|**Abbruch bei numerischem Runden**|Generiert einen Fehler, wenn in einem Ausdruck ein Genauigkeitsverlust auftritt.|  
|**Transaktionsabbruch**|Führt ein Rollback für eine Transaktion aus, wenn eine Transact-SQL-Anweisung einen Laufzeitfehler auslöst.|  
  
 Weitere Informationen zu den Verbindungsoptionen finden Sie, wenn Sie nach der entsprechenden Option in der Onlinedokumentation suchen.  
  
## <a name="remote-server-connections"></a>Remoteserververbindungen  
 **Remoteverbindungen mit diesem Server zulassen**  
 Steuert die Ausführung von gespeicherten Prozeduren von Remoteservern, auf denen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden. Das Aktivieren dieses Kontrollkästchens hat dieselbe Wirkung wie das Festlegen der Option **sp_configure 'remote access'** auf 1. Ist es deaktiviert, wird die Ausführung der gespeicherten Prozeduren von einem Remoteserver verhindert.  
  
 **Timeout für Remoteabfragen (Sekunden, 0 = kein Timeout)**  
 Gibt an, wie viel Zeit (in Sekunden) ein Remotevorgang in Anspruch nehmen kann, bevor das Timeout von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eintritt. Die Standardeinstellung ist 600 Sekunden, was einer Wartezeit von zehn Minuten entspricht.  
  
 **Verteilte Transaktionen für die Kommunikation zwischen Servern verlangen**  
 Schützt die Aktionen einer Server-zu-Server-Prozedur durch eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator-Transaktion (MS DTC). Weitere Informationen finden Sie unter [Konfigurieren der remote Proc Trans Server Configuration Option](configure-the-remote-proc-trans-server-configuration-option.md).  
  
## <a name="property-page-display-options"></a>Anzeigeoptionen der Eigenschaftenseite  
 **Konfigurierte Werte**  
 Zeigt für die Optionen in diesem Bereich konfigurierte Werte an. Wenn Sie diese Werte ändern, klicken Sie anschließend auf **Ausgeführte Werte** , um zu sehen, ob die Änderungen wirksam sind. Sind sie nicht wirksam, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zuerst neu gestartet werden.  
  
 **Ausgeführte Werte**  
 Zeigt die gegenwärtig ausgeführten Werte für die Optionen in diesem Bereich an. Diese Werte sind schreibgeschützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Optionen &#40;Abfrage Ausführung: SQL Server: Seite "erweiterte Seite"&#41;](../options-query-execution-sql-server-advanced-page.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
