---
title: Von IntelliSense unterstützte Transact-SQL-Syntax
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL IntelliSense
- IntelliSense [SQL Server], Transact-SQL syntax
ms.assetid: 194e8f4f-fd7e-4f32-a169-f23531128004
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d34fc79dd7817e64b34b61083415477860ce97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717788"
---
# <a name="transact-sql-syntax-supported-by-intellisense"></a>Von IntelliSense unterstützte Transact-SQL-Syntax
  Dieses Thema beschreibt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen und Syntaxelemente, die von IntelliSense in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]unterstützt werden.  
  
## <a name="statements-supported-by-intellisense"></a>Von IntelliSense unterstützte Anweisungen  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]unterstützt IntelliSense nur die am häufigsten verwendeten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen. Einige allgemeine [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Bedingungen könnten verhindern, dass IntelliSense funktioniert. Weitere Informationen finden Sie unter [Problembehandlung von IntelliSense &#40;SQL Server Management Studio&#41;](troubleshooting-intellisense.md).  
  
> [!NOTE]  
>  IntelliSense ist nicht für verschlüsselte Datenbankobjekte verfügbar, z. B. verschlüsselte gespeicherte Prozeduren oder benutzerdefinierte Funktionen. Für Parameter von erweiterten gespeicherten Prozeduren und benutzerdefinierten Typen für die CLR-Integration stehen weder Parameterhilfe noch QuickInfo zur Verfügung.  
  
### <a name="select-statement"></a>SELECT-Anweisung  
 Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor stellt IntelliSense-Unterstützung für die folgenden Syntaxelemente in der SELECT-Anweisung bereit:  
  
|||  
|-|-|  
|SELECT|WHERE|  
|FROM|ORDER BY|  
|HAVING|UNION|  
|FOR|GROUP BY|  
|TOP|OPTION (Hinweis)|  
  
### <a name="additional-transact-sql-statements-that-are-supported"></a>Weitere Transact-SQL-Anweisungen, die unterstützt werden  
 Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor stellt zudem IntelliSense-Unterstützung für die in der folgenden Tabellen aufgeführten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen bereit.  
  
|Transact-SQL-Anweisung|Unterstützte Syntax|  
|-----------------------------|----------------------|  
|[INSERT](/sql/t-sql/statements/insert-transact-sql)|Die gesamte Syntax, mit Ausnahme der *execute_statement* -Klausel.|  
|[UPDATE](/sql/t-sql/queries/update-transact-sql)|Gesamte Syntax.|  
|[DELETE](/sql/t-sql/statements/delete-transact-sql)|Gesamte Syntax.|  
|[DECLARE @local_variable](/sql/t-sql/language-elements/declare-local-variable-transact-sql)|Gesamte Syntax.|  
|[Set@local_variable](/sql/t-sql/language-elements/set-local-variable-transact-sql)|Gesamte Syntax.|  
|[EXECUTE](/sql/t-sql/language-elements/execute-transact-sql)|Ausführung von benutzerdefinierten gespeicherten Prozeduren, gespeicherten Systemprozeduren, benutzerdefinierten Funktionen und Systemfunktionen.|  
|[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)|Gesamte Syntax.|  
|[CREATE VIEW](/sql/t-sql/statements/create-view-transact-sql)|Gesamte Syntax.|  
|[CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql)|Gesamte Syntax mit den folgenden Ausnahmen:<br /><br /> Es gibt keine IntelliSense-Unterstützung für die EXTERNAL NAME-Klausel.<br /><br /> In der AS-Klausel unterstützt IntelliSense nur die Anweisungen und die Syntaxelemente, die in diesem Thema aufgeführt werden.|  
|[ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql)|Gesamte Syntax mit den folgenden Ausnahmen:<br /><br /> Es gibt keine IntelliSense-Unterstützung für die EXTERNAL NAME-Klausel.<br /><br /> In der AS-Klausel unterstützt IntelliSense nur die Anweisungen und die Syntaxelemente, die in diesem Thema aufgeführt werden.|  
|[USE](/sql/t-sql/language-elements/use-transact-sql)|Gesamte Syntax.|  
  
## <a name="intellisense-in-supported-statements"></a>IntelliSense in unterstützten Anweisungen  
 IntelliSense im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor unterstützt die folgenden Syntaxelemente, wenn sie in einer der unterstützten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden:  
  
-   Alle Jointypen, einschließlich APPLY.  
  
-   PIVOT und UNPIVOT.  
  
-   Verweise auf die folgenden Datenbankobjekte:  
  
    -   Datenbanken und Schemas  
  
    -   Tabellen, Sichten, Tabellenwertfunktionen und Tabellenausdrücke  
  
    -   Spalten  
  
    -   Prozeduren und Prozedurparameter  
  
    -   Skalare Funktionen und Skalarausdrücke  
  
    -   Lokale Variablen  
  
    -   Allgemeine Tabellenausdrücke (CTE)  
  
-   Datenbankobjekte, auf die nur in der CREATE-Anweisung oder der ALTER-Anweisung im Skript oder im Batch verwiesen wird, die aber nicht in der Datenbank vorhanden sind, da das Skript bzw. der Batch noch nicht ausgeführt wurde. Nachfolgend sind diese Objekte aufgeführt:  
  
    -   Tabellen und Prozeduren, die in einer CREATE TABLE-Anweisung oder CREATE PROCEDURE-Anweisung im Skript oder Batch angegeben wurden.  
  
    -   Änderungen an Tabellen und Prozeduren, die in einer ALTER TABLE-Anweisung oder ALTER PROCEDURE-Anweisung im Skript oder Batch angegeben wurden.  
  
    > [!NOTE]  
    >  IntelliSense ist nicht verfügbar für die Spalten einer CREATE VIEW-Anweisung, solange die CREATE VIEW-Anweisung nicht ausgeführt wurde.  
  
 IntelliSense wird für die zuvor genannten Elemente nicht bereitgestellt, wenn sie in anderen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden. Es ist z. B. IntelliSense-Unterstützung für Spaltennamen verfügbar, die in einer SELECT-Anweisung verwendet werden, nicht jedoch für Spaltennamen, die in der CREATE FUNCTION-Anweisung verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 In einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript oder -Batch unterstützt IntelliSense im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor nur die Anweisungen und Syntaxelemente, die in diesem Thema aufgeführt werden. Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Codebeispiele zeigen, welche Anweisungen und Syntaxelemente von IntelliSense unterstützt werden. Beispielsweise ist im folgenden Batch IntelliSense verfügbar für die `SELECT` -Anweisung, wenn diese eigencodiert ist, aber nicht, wenn `SELECT` in einer `CREATE FUNCTION` -Anweisung enthalten ist.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE Name LIKE N'Road-250%' and Color = N'Red';  
GO  
CREATE FUNCTION Production.ufn_Red250 ()  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT Name  
    FROM AdventureWorks2012.Production.Product  
    WHERE Name LIKE N'Road-250%'  
      AND Color = N'Red'  
);GO  
```  
  
 Diese Funktionalität gilt auch für die Sätze von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen in der AS-Klausel einer CREATE PROCEDURE-Anweisung oder ALTER PROCEDURE-Anweisung.  
  
 In einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript oder -Batch unterstützt IntelliSense Objekte, die in einer CREATE-Anweisung oder ALTER-Anweisung angegeben sind. Allerdings sind diese Objekte nicht in der Datenbank vorhanden, da die Anweisungen nicht ausgeführt wurden. Sie können z. B. den folgenden Code im Abfrage-Editor eingeben:  
  
```  
USE MyTestDB;  
GO  
CREATE TABLE MyTable  
    (PrimaryKeyCol   INT PRIMARY KEY,  
    FirstNameCol      NVARCHAR(50),  
   LastNameCol       NVARCHAR(50));  
GO  
SELECT   
```  
  
 Wenn Sie `SELECT`eingegeben haben, listet IntelliSense **PrimaryKeyCol**, **FirstNameCol**und **LastNameCol** als mögliche Elemente in der Auswahlliste auf, auch wenn das Skript nicht ausgeführt wurde und `MyTable` noch nicht in `MyTestDB`vorhanden ist.  
  
  
