---
title: MSSQLSERVER_10531 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6230c046a9eb7b900377888c59a3a492f2b89f73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699746"
---
# <a name="mssqlserver_10531"></a>MSSQLSERVER_10531
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10531|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PG_NO_ELIGIBLE_STMT|  
|Meldungstext|Die Planhinweisliste '%.*ls' kann nicht aus dem Cache erstellt werden, weil der Benutzer nicht über die erforderlichen Berechtigungen verfügt. Gewähren Sie dem Benutzer, der die Planhinweisliste erstellt, die VIEW SERVER STATE-Berechtigung.|  
  
## <a name="explanation"></a>Erklärung  
 Der Benutzer verfügt nicht über die erforderlichen Berechtigungen zum Erstellen der angegebenen Planhinweisliste aus dem Plancache.  
  
## <a name="user-action"></a>Benutzeraktion  
 Gewähren Sie dem Benutzer, der die Planhinweisliste erstellt, die Berechtigung „VIEW SERVER STATE“.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Plan Hinweis Listen](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
