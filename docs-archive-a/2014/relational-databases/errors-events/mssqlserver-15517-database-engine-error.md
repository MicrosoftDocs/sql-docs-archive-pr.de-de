---
title: MSSQLSERVER_15517 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620946"
---
# <a name="mssqlserver_15517"></a>MSSQLSERVER_15517
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|15517|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_CANNOTEXECUTEASUSER|  
|Meldungstext|Die Ausführung als Datenbankprinzipal ist nicht möglich, weil der Prinzipal „*principal*“ nicht vorhanden ist, für diesen Typ von Prinzipal kein Identitätswechsel möglich ist, oder Sie nicht die erforderliche Berechtigung haben.|  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie den Namen eines vorhandenen Prinzipals, oder rufen Sie die IMPERSONATE-Berechtigung für den betreffenden Prinzipal ab.  
  
 15517 kann zudem nach dem Anfügen und Wiederherstellen einer Datenbank durch eine Person auftreten, die nicht mit dem ursprünglichen Datenbankbesitzer identisch ist. Ändern Sie zum Beheben dieses Fehlers den db_owner in eine Anmeldung auf Ihrem Server, indem Sie den folgenden Befehl ausführen:  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
