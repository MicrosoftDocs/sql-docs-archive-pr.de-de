---
title: Trace File Close-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34075f9c3a664198999873f2dc95f02b19799712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608691"
---
# <a name="trace-file-close-event-class"></a>Trace File Close-Ereignisklasse
  Die **Trace File Close** -Ereignisklasse weist darauf hin, dass eine Ablaufverfolgungsdatei während eines Rollovers für Ablaufverfolgungsdateien geschlossen wurde.  
  
## <a name="trace-file-close-event-class-data-columns"></a>Trace File Close-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Ereignistyp = 150.|27|Nein|  
|**EventSequence**|**int**|Eindeutiger Timestamp des Ereignisses, das während der Ablaufverfolgung ausgelöst wurde. Diese Zahl erhöht sich bei jedem ausgelösten Ereignis gleichmäßig.|51|Nein|  
|**FileName**|**nvarchar**|Logischer Name der geschlossenen Ablaufverfolgungsdatei.|36|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, NULL = Benutzer. Bei dieser Ereignisklasse beläuft sich der Wert immer auf 1.|60|Ja|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username). Bei dieser Ereignisklasse lautet der Wert immer "sa".|11|Ja|  
|**ObjectID**|**int**|Vom System zugewiesene ID der Ablaufverfolgung.|22|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
