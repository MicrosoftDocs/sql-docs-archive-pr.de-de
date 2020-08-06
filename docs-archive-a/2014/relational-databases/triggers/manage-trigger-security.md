---
title: Verwalten der Triggersicherheit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: fdc176dcad50c3bf28f058c3724a01267975bfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621917"
---
# <a name="manage-trigger-security"></a>Verwalten der Triggersicherheit
  Standardmäßig werden sowohl DML- als auch DDL-Trigger im Kontext des Benutzers ausgeführt, der den Trigger aufruft. Genauer ist der Benutzer, der den Trigger aufruft, derjenige Benutzer, der die Anweisung ausführt, die zum Ausführen des Triggers führt. Wenn die Benutzerin **Mary** beispielsweise eine DELETE-Anweisung ausführt, die dazu führt, dass der DML-Trigger **DML_trigMary** ausgeführt wird, wird der Code in **DML_trigMary** im Kontext der Privilegien für **Mary**ausgeführt. Dieses Standardverhalten kann von Benutzern ausgenutzt werden, die bösartigen Code in die Datenbank oder Serverinstanz einschleusen möchten. Beispielsweise wird der folgende DDL-Trigger vom Benutzer `JohnDoe`erstellt:  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 Dieser Trigger bewirkt Folgendes: Sobald ein Benutzer mit der Berechtigung, `GRANT CONTROL SERVER` -Anweisungen auszuführen, wie z. B. ein Mitglied der festen Serverrolle **sysadmin** , eine `ALTER TABLE` -Anweisung ausführt, wird `JohnDoe` die `CONTROL SERVER` -Berechtigung erteilt. Mit anderen Worten heißt dies, dass `JohnDoe` zwar die `CONTROL SERVER` -Berechtigung nicht sich selbst erteilen darf, jedoch den Triggercode aktivieren kann, der ihm diese Berechtigung verschafft. Sowohl DML- als auch DDL-Trigger sind diesen Sicherheitsrisiken ausgesetzt.  
  
## <a name="trigger-security-best-practices"></a>Bewährte Methoden für die Triggersicherheit  
 Sie können folgende Maßnahmen ergreifen, um zu vermeiden, dass Triggercode mit ausgeweiteten Privilegien ausgeführt wird:  
  
-   Eruieren Sie die in der Datenbank und der Serverinstanz vorhandenen DML- und DDL-Trigger, indem Sie die Katalogsichten [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) und [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) abfragen. Die folgende Abfrage gibt alle DML-Trigger und DDL-Trigger auf Datenbankebene der aktuellen Datenbank zurück, sowie alle DDL-Trigger auf Serverebene der Serverinstanz:  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   Verwenden Sie [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) , um die Trigger zu deaktivieren, die die Integrität der Datenbank oder des Servers beeinträchtigen können, falls sie mit ausgeweiteten Privilegien ausgeführt werden. Die folgende Anweisung deaktiviert alle DDL-Trigger auf Datenbankebene in der aktuellen Datenbank:  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     Die folgende Anweisung deaktiviert alle DDL-Trigger auf Serverebene in der Serverinstanz:  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     Die folgende Anweisung deaktiviert alle DML-Trigger in der aktuellen Datenbank:  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [DML-Trigger](../triggers/dml-triggers.md)   
 [DDL-Trigger](../triggers/ddl-triggers.md)  
  
  
