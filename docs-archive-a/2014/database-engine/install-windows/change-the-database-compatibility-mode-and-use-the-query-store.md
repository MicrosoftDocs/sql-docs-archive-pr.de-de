---
title: Migrieren von Abfrage Plänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dafd3a5f8a460bb08e63919c2cb853ad74dc2f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718685"
---
# <a name="migrate-query-plans"></a>Migrieren von Abfrageplänen
  Im Allgemeinen führt das Upgrade einer Datenbank auf die aktuellste Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu einer besseren Abfrageleistung. Bei unternehmenswichtigen Abfragen, deren Leistung sorgfältig optimiert wurde, möchten Sie jedoch möglicherweise vor dem Upgrade die entsprechenden Abfragepläne aufzeichnen. Zu diesem Zweck können Sie für jede Abfrage eine Planhinweisliste erstellen. Falls der Abfrageoptimierer nach der Aktualisierung für immer mehr Abfragen einen weniger effizienten Plan wählt, können Sie die Planhinweislisten aktivieren und den Abfrageoptimierer zwingen, die alten Pläne zu verwenden.  
  
 Führen Sie die folgenden Schritte durch, um vor der Aktualisierung Planhinweislisten zu erstellen:  
  
1.  Zeichnen Sie den aktuellen Plan für jede unternehmenskritische Abfrage auf, indem Sie die gespeicherte Prozedur [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) verwenden und den Abfrageplan im Use Plan-Abfrage Hinweis angeben.  
  
2.  Vergewissern Sie sich, dass die Planhinweisliste auf die Abfrage angewendet wird.  
  
3.  Aktualisieren Sie die Datenbank auf die neuere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Die Pläne werden in der aktualisierten Datenbank in den Planhinweislisten persistent gespeichert und können gegebenenfalls herangezogen werden, falls es nach dem Upgrade zu einer Regression bei der Planverwendung kommt.  
  
     Wir empfehlen jedoch, die Planhinweislisten nicht sofort nach der Aktualisierung zu aktivieren, da Sie sonst eventuell nicht die Vorzüge besserer Pläne in der neuen Version oder die Vorteile von Neukompilierungen aufgrund aktualisierter Statistiken nutzen können.  
  
4.  Falls nach der Aktualisierung weniger effiziente Pläne gewählt werden, können Sie alle oder einen Teil der Planhinweislisten aktivieren, um die neuen Pläne zu überschreiben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie vor der Aktualisierung durch Erstellen einer Planhinweisliste den Plan für eine Abfrage aufzeichnen können.  
  
### <a name="step-1-collect-the-plan"></a>Schritt 1: Abrufen des Plans  
 Der in der Planhinweisliste aufgezeichnete Abfrageplan muss im XML-Format vorliegen. Abfragepläne im XML-Format können auf folgende Weise erstellt werden:  
  
-   [Mit SET SHOWPLAN_XML](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [SET STATISTICS XML](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   Abfragen der query_plan Spalte der dynamischen Verwaltungsfunktion [sys. dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) .  
  
-   Die [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Ereignis Klassen [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)und [Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) .  
  
 Im folgenden Beispiel wird der Abfrageplan für die Anweisung `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` abgerufen, indem dynamische Verwaltungssichten abgefragt werden.  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a>Schritt 2: Erstellen des Planhinweises zum Erzwingen des Plans  
 Fügen Sie den in der Planhinweisliste enthaltenen (und mit einer der oben beschriebenen Methoden bezogenen) Abfrageplan im XML-Format als Zeichenfolgenliteral in den USE PLAN-Abfragehinweis ein, der in der OPTION-Klausel von sp_create_plan_guide angegeben ist.  
  
 Grenzen Sie alle im XML-Plan enthaltenen Anführungszeichen (') durch ein zweites Anführungszeichen ab, bevor Sie die Planhinweisliste erstellen. Ein Plan, der `WHERE A.varchar = 'This is a string'` enthält, muss z. B. abgegrenzt werden, indem der Code zu `WHERE A.varchar = ''This is a string''` geändert wird.  
  
 Im folgenden Beispiel wird eine Planhinweisliste für den in Schritt 1 abgerufenen Abfrageplan erstellt und der XML-Showplan für die Abfrage in den `@hints`-Parameter eingefügt. Aus Platzgründen ist im Beispiel nur ein Teil des Showplans angegeben.  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a>Schritt 3: Überprüfen, ob die Planhinweisliste auf die Abfrage angewendet wird  
 Führen Sie die Abfrage noch einmal aus, und überprüfen Sie den erzeugten Abfrageplan. Dieser Plan sollte mit dem in der Planhinweisliste angegebenen Plan übereinstimmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Abfragehinweise (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Planhinweislisten](../../relational-databases/performance/plan-guides.md)  
  
  
