---
title: Warteschlangenlese-Agent der Microsoft SQL Server-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 854c425db3fbaa346dab5eb2c41bd58cf03f65c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609156"
---
# <a name="replication-queue-reader-agent"></a>Warteschlangenlese-Agent der Microsoft SQL Server-Replikation
  Der Replikationswarteschlangenlese-Agent ist eine ausführbare Datei, die in einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Warteschlange oder einer [!INCLUDE[msCoName](../../../includes/msconame-md.md)]-Nachrichtenwarteschlange gespeicherte Nachrichten liest und diese Nachrichten dann auf den Verleger anwendet. Der Warteschlangenlese-Agent wird bei Momentaufnahme- und Transaktionsveröffentlichungen verwendet, die das verzögerte Update über eine Warteschlange gestatten.  
  
> [!NOTE]  
>  Parameter können in beliebiger Reihenfolge angegeben werden. Wenn keine optionalen Parameter angegeben werden, werden vordefinierte Werte auf Grundlage des Standardagentprofils verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Zeigt Informationen zur Nutzung an.  
  
 **-Continuous**  
 Gibt an, ob der Agent fortlaufend versucht, Transaktionen in der Warteschlange zu verarbeiten. Wenn dieses Argument angegeben ist, setzt der Agent die Ausführung auch dann fort, wenn in der Warteschlange keine ausstehenden Transaktionen von einem der Abonnenten vorhanden sind.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Der Pfad der Agentdefinitionsdatei. Eine Agentdefinitionsdatei enthält Befehlszeilenargumente für den Agent. Der Inhalt der Datei wird als ausführbare Datei analysiert. Verwenden Sie doppelte Anführungszeichen ("), um Argumentwerte anzugeben, die beliebige Zeichen enthalten.  
  
 **-Distributor** _server_name_[ **\\** _instance_name_]  
 Der Name des Verteilers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie *server_name*\\*instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Wenn kein Name angegeben wird, wird als Standardwert der Name der Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf dem lokalen Computer verwendet.  
  
 **-DistributionDB** _distribution_database_  
 Die Verteilungsdatenbank.  
  
 **-DistributorLogin** _distributor_login_  
 Der Anmeldename des Verteilers.  
  
 **-DistributorPassword** _distributor_password_  
 Das Verteilerkennwort.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verteilers an. Der Wert **0** steht für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierungsmodus (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Die Ebene der SSL-Verschlüsselung (Secure Sockets Layer), die vom Warteschlangenlese-Agent beim Herstellen von Verbindungen verwendet wird.  
  
|Wert von EncryptionLevel|BESCHREIBUNG|  
|---------------------------|-----------------|  
|**0**|Gibt an, dass SSL nicht verwendet wird.|  
|**1**|Gibt an, dass SSL verwendet wird, der Agent jedoch nicht überprüft, ob das SSL-Serverzertifikat von einem vertrauenswürdigen Aussteller signiert wurde.|  
|**2**|Gibt an, dass SSL verwendet und das Zertifikat überprüft wird.|  

 > [!NOTE]  
 >  Ein gültiges SSL-Zertifikat wird mit dem vollqualifizierten Domänennamen der SQL Server-Instanz definiert. Damit der Agent die Verbindung erfolgreich herstellen kann, wenn „-EncryptionLevel“ auf 2 festgelegt ist, sollten Sie einen Alias auf der lokalen SQL Server-Instanz erstellen. Der Parameter „Alias Name“ sollte den Servernamen enthalten, und für den Parameter „Server“ sollte der vollqualifizierte Name der SQL Server-Instanz festgelegt werden.
  
 Weitere Informationen finden Sie unter [SQL Server-Replikation-Sicherheit](../security/view-and-modify-replication-security-settings.md).  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 Gibt den Umfang des Verlaufs an, der während eines Vorgangs des Warteschlangenlese-Agents protokolliert wird. Sie können die negativen Auswirkungen der Verlaufsprotokollierung auf die Leistung minimieren, indem Sie den Wert **1**auswählen.  
  
|Wert von <legacyBold>HistoryVerboseLevel</legacyBold>|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|**0**|Keine Verlaufsprotokollierung (nicht empfohlen).|  
|**1**|Standard. Aktualisieren Sie immer eine vorherige Verlaufsmeldung mit dem gleichen Status (Start, Status, Erfolg usw.). Wenn kein vorheriger Datensatz mit dem gleichen Status vorhanden ist, fügen Sie einen neuen Datensatz ein.|  
|**2**|Fügen Sie neue Verlaufsdatensätze ein, einschließlich Leerlaufmeldungen oder Meldungen zu Aufträgen mit langer Ausführungszeit.|  
|**3**|Fügen Sie neue Verlaufsdatensätze ein, die weitere Details enthalten, die möglicherweise für die Problembehandlung nützlich sind.|  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Anmeldung eintritt. Der Standardwert ist 15 Sekunden.  
  
 **-Output** _output_path_and_file_name_  
 Der Pfad der Agentausgabedatei. Wenn kein Dateiname angegeben ist, wird die Ausgabe an die Konsole gesendet. Wenn eine Datei mit dem angegebenen Namen vorhanden ist, wird die Ausgabe an diese Datei angefügt.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Gibt an, ob die Ausgabe ausführlich sein soll. Wenn die Meldungsstufe **0**beträgt, werden nur Fehlermeldungen gedruckt. Wenn die Meldungsstufe **1**beträgt, werden alle Statusberichtsmeldungen gedruckt. Wenn die Meldungsstufe **2** (Standard) beträgt, werden alle Fehlermeldungen und Statusberichtsmeldungen gedruckt, was beim Debuggen nützlich ist.  
  
 **-PollingInterval** _polling_interval_  
 Ist nur relevant, um Abonnements zu aktualisieren, die auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basierende Warteschlangen verwenden. Gibt an, wie oft die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Warteschlange nach anstehenden Transaktionen abgefragt wird (in Sekunden). Der Wert kann zwischen 0 und 240 Sekunden liegen. Die Standardeinstellung ist 5 Sekunden.  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]  
 Gibt die Failoverpartnerinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die an einer Datenbank-Spiegelungssitzung mit der Veröffentlichungsdatenbank teilnimmt. Weitere Informationen finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-ProfileName** _agent_profile_name_  
 Der Name eines Agentprofils, das zum Bereitstellen von Standardwerten an den Agent verwendet wird. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Abfrage eintritt. Die Standardeinstellung ist 1800 Sekunden.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Gibt an, wie Konflikte bei verzögertem Update über eine Warteschlange gelöst werden. Der Wert **1** gibt an, dass der Verleger den Konflikt gewinnt und für die aktuelle Transaktion in der Warteschlage, bei der der Konflikt aufgetreten ist, auf dem Verleger und dem ursprünglichen Updateabonnenten ein Rollback ausgeführt wird. Die Verarbeitung der folgenden Transaktionen in der Warteschlange wird fortgesetzt. Der Wert **2** gibt an, dass der Abonnent den Konflikt gewinnt und durch die Transaktion in der Warteschlange die Werte auf dem Verleger überschrieben werden. Der Wert **3** gibt an, dass jeder Konflikt zu einer erneuten Initialisierung des Abonnenten führt. Der Verleger gewinnt den Konflikt, die Verarbeitung der folgenden Transaktionen in der Warteschlange wird beendet, und das Abonnement wird erneut initialisiert. Die Standardeinstellung für Transaktionsveröffentlichungen lautet **1** , für Momentaufnahmeveröffentlichungen **3** .  
  
## <a name="remarks"></a>Bemerkungen  
 Führen Sie zum Starten des Warteschlangenlese-Agents von der Eingabeaufforderung **qrdrsvc.exe** aus. Informationen hierzu finden Sie im [Abschnitt zu den ausführbaren Dateien von Replikations-Agents](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations-Agent-Verwaltung](replication-agent-administration.md)  
  
  
