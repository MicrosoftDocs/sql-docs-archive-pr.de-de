---
title: MSSQLSERVER_8649 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619853"
---
# <a name="mssqlserver_8649"></a>MSSQLSERVER_8649
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8649|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|COST_TOO_HIGH|  
|Meldungstext|Die Abfrage wurde abgebrochen, da die geschätzten Kosten der Abfrage (%d) den konfigurierten Schwellenwert %d überschreiten. Wenden Sie sich an den Systemadministrator.|  
  
## <a name="explanation"></a>Erklärung  
 Die Abfrage wurde abgebrochen, weil die geschätzten Kosten dieser Abfrage den für QUERY_GOVERNOR_COST_LIMIT festgelegten konfigurierten Schwellenwert überschreiten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Setzen Sie die Option QUERY_GOVERNOR_COST_LIMIT auf einen höheren Wert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
