---
title: MSSQLSERVER_1222 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac3fe9314386836633a11f17d6775c75019de93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607812"
---
# <a name="mssqlserver_1222"></a>MSSQLSERVER_1222
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1222|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LK_TIMEOUT|  
|Meldungstext|Das Timeout für Sperranforderung wurde überschritten.|  
  
## <a name="explanation"></a>Erklärung  
 Eine erforderliche Ressource wurde durch eine weitere Transaktion länger gesperrt, als diese Abfrage warten konnte.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie die folgenden Aufgaben aus, um das Problem zu beheben:  
  
1.  Lokalisieren Sie nach Möglichkeit die Transaktion, durch die die erforderliche Ressource gesperrt wird. Verwenden Sie die dynamischen Verwaltungssichten **sys.dm_os_waiting_tasks** und **sys.dm_tran_locks**.  
  
2.  Beenden Sie gegebenenfalls die Transaktion, wenn die Sperre durch die Transaktion weiterhin besteht.  
  
3.  Führen Sie die Abfrage erneut aus.  
  
 Ändern Sie das Sperrtimeout oder die problematischen Transaktionen, sodass die Sperre für eine kürzere Zeit besteht, wenn der Fehler häufiger auftritt.  
  
  
