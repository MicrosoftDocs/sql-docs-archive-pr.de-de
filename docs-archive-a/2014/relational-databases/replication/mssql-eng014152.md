---
title: MSSQL_ENG014152 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 615b9cf2996653d86c44d6e43a83e01e8287b110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616499"
---
# <a name="mssql_eng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14152|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Replikations-%1!: %2! (Agent) ist für die Wiederholung geplant. %3!|  
  
## <a name="explanation"></a>Erklärung  
 Der angegebene Replikations-Agent ist für die Wiederholung des angeforderten Vorgangs vorgesehen. Der Prozess wird so lange wiederholt, bis die konfigurierte maximale Anzahl der Wiederholungsversuche für den Auftragsschritt erreicht wird.  
  
 Eine Wiederholung wird normalerweise aus einem der folgenden Gründe ausgeführt:  
  
-   Der **QueryTimeout** -Wert wird überschritten.  
  
-   Der **LoginTimeout** -Wert wird überschritten.  
  
-   Der Replikationsvorgang wurde als Deadlockopfer ausgewählt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn die Wiederholungsmeldung nicht häufig angezeigt wird, ist keine Benutzeraktion erforderlich.  
  
 Verwenden Sie [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) , um die aktuelle Einstellung für die maximale Anzahl der Wiederholungen des Schritts **Führt den Agent aus** für den angegebenen Replikations-Agent anzuzeigen. Sie können den- **@retry_attempts** Parameter der gespeicherten Prozedur [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) verwenden, um die Häufigkeit zu ändern, mit der ein Auftrags Schritt erneut versucht wird.  
  
 Wenn die Wiederholungsmeldung häufig wieder angezeigt wird, beheben Sie das Problem anhand der Meldung, durch die die Wiederholung verursacht wird. Prüfen Sie den Verlauf des Agents auf Meldungen, mit denen angegeben wird, warum die Wiederholung ausgeführt werden musste. In einigen Fällen müssen Sie möglicherweise eine detailliertere Protokollierung für Ihren Replikations-Agent aktivieren. Weitere Informationen zur Konfiguration der Protokollierung für die Replikation finden Sie im Microsoft Knowledge Base-Artikel [312292](https://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
