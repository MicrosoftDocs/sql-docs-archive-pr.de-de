---
title: Plan Guide Successful (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Plan Guide Successful event class
ms.assetid: fecfbb6c-56c9-4db4-84d3-00d6e338355a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b521c230d1789b031903aecdf8f42f9be3ffc0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619810"
---
# <a name="plan-guide-successful-event-class"></a>Plan Guide Successful (Ereignisklasse)
  Die Plan Guide Successful-Ereignisklasse zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine Abfrage oder einen Batch mit Planhinweisliste einen Ausführungsplan erzeugt hat. Dieses Ereignis wird ausgelöst, wenn die folgenden Voraussetzungen erfüllt sind:  
  
-   Der Batch bzw. das Modul in der Planhinweislisten-Definition stimmt mit dem derzeit ausgeführten Batch bzw. Modul überein.  
  
-   Die Abfrage in der Planhinweislisten-Definition stimmt mit der ausgeführten Abfrage überein.  
  
-   Die Hinweise in der Planhinweislisten-Definition, einschließlich des USE PLAN-Hinweises, wurden auf die Abfrage angewendet. Das heißt, dass der kompilierte Abfrageplan die angegebenen Hinweise beachtet.  
  
## <a name="plan-guide-successful-event-class-data-columns"></a>Datenspalten der Plan Guide Successful-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten gefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine angegebene Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 214.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung|51|Nein|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis in einem Systemprozess oder einem Benutzerprozess aufgetreten ist: 1 = System, 0 = Benutzer.|60|Ja|  
|LoginName|`nvarchar`|Anmelde Name des Benutzers (Anmeldung der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmelde Informationen im Format Domäne \\ *Benutzername*).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Sie finden diese Informationen in der [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) -Katalogsicht bzw. in der [sys.sql_logins](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|ObjectID|`int`|Objekt-ID des Moduls, das kompiliert wurde, als die Planhinweisliste angewendet wurde. Falls die Planhinweisliste auf kein Modul angewendet wurde, wird diese Spalte auf NULL festgelegt.|22|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`ntext`|Name der Planhinweisliste.|1|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Guide-fehlerhafte Ereignisklasse](plan-guide-unsuccessful-event-class.md)   
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
