---
title: MSSQLSERVER_10536 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00d08f4555f38b61661a917ba94c023f9dd6c4a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718226"
---
# <a name="mssqlserver_10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10536|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_TOO_MANY_STMTS|  
|Meldungstext|Die Planhinweisliste „%.\*ls“ kann nicht erstellt werden, weil der entsprechende Batch bzw. das Modul für das angegebene `@plan_handle` mehr als 1000 geeignete Anweisungen enthält. Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen `statement_start_offset`-Wert für jede Anweisung an.|  
  
## <a name="explanation"></a>Erklärung  
 Der entsprechende Batch bzw. das Modul für das angegebene `@plan_handle` enthält mehr als 1000 geeignete Anweisungen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erstellen Sie eine Planhinweisliste für jede Anweisung im Batch oder Modul, und geben Sie dabei einen `statement_start_offset`-Wert für jede Anweisung an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
