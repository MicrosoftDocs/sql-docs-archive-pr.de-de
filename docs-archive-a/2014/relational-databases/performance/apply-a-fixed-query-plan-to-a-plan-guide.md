---
title: Anwenden eines festen Abfrageplans auf eine Planhinweisliste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 318955c4d0550e311873d8b4a6f79f72e04ac8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696746"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>Anwenden eines festen Abfrageplans auf eine Planhinweisliste
  Sie können einen festen Abfrageplan auf eine Planhinweisliste des Typs OBJECT oder SQL anwenden. Planhinweislisten, die einen festen Abfrageplan anwenden, sind hilfreich, wenn Sie wissen, dass ein vorhandener Ausführungsplan für eine bestimmte Abfrage bessere Ergebnisse erzielt als der vom Abfrageoptimierer ausgewählte Ausführungsplan.  
  
 Im folgenden Beispiel wird eine Planhinweisliste für eine einfache Ad-hoc-SQL-Anweisung erstellt. Der gewünschte Abfrageplan für diese Anweisung wird in der Planhinweisliste durch die direkte Angabe des XML-Showplans für die Abfrage im `@hints` -Parameter bereitgestellt. Im Beispiel wird zunächst die SQL-Anweisung ausgeführt, um einen Plan im Plancache zu erzeugen. Dabei wird davon ausgegangen, dass der erzeugte Plan dem gewünschten Plan entspricht und keine weitere Optimierung der Abfrage erforderlich ist. Der XML-Showplan wird durch eine Abfrage der dynamischen Verwaltungssichten `sys.dm_exec_query_stats`, `sys.dm_exec_sql_text`und `sys.dm_exec_text_query_plan` sys.dm_exec_query_stats abgerufen und der Variablen `@xml_showplan` zugewiesen. Die `@xml_showplan` -Variable wird dann im `sp_create_plan_guide` -Parameter an die `@hints` -Anweisung übergeben. Alternativ können Sie die gespeicherte Prozedur [sp_create_plan_guide_from_handle](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) verwenden, um eine Planhinweisliste aus einem Abfrageplan im Plancache zu erstellen.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
