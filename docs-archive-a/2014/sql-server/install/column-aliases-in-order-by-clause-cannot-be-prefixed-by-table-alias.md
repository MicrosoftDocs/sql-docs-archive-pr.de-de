---
title: Spalten Aliasen in der ORDER BY-Klausel können keinen Tabellenalias als Präfix aufweisen. Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617493"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a>Spaltenaliase in ORDER BY-Klauseln können nicht vom Tabellenalias als Präfix verwendet werden
  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher können Spaltenaliase in ORDER BY-Klauseln nicht vom Tabellenalias als Präfix verwendet werden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Die folgende Abfrage wird z. B. in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ausgeführt, gibt in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jedoch einen Fehler zurück  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] ordnet `p.l` in der `ORDER BY`-Klausel keiner gültigen Spalte in der Tabelle zu.  
  
### <a name="exception"></a>Ausnahme  
 Wenn der in der ORDER BY-Klausel vorangestellte Spaltenalias ein gültiger Spaltenname in der angegebenen Tabelle ist, wird die Abfrage ohne Fehler ausgeführt. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] kann die Semantik der Anweisung unterschiedlich sein. So ist der Spaltenalias (`id`) in der folgenden Anweisung beispielsweise ein gültiger Spaltenname in der `sysobjects`-Tabelle. In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] wird der `CAST`-Vorgang beim Ausführen der Anweisung durchgeführt, nachdem das Resultset sortiert wurde. Dies bedeutet, dass die `name`-Spalte im Sortiervorgang verwendet wird. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wird der `CAST`-Vorgang vor dem Sortiervorgang ausgeführt. Dies bedeutet, dass die `id`-Spalte der Tabelle im Sortiervorgang verwendet wird und das Resultset in einer unerwarteten Reihenfolge zurückgegeben wird.  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Abfragen, die Spaltenaliase mit vorangestellten Tabellenaliasen in der ORDER BY-Klausel verwenden, auf eine der folgenden Arten:  
  
-   Stellen Sie in der ORDER BY-Klausel nach Möglichkeit kein Präfix vor den Spaltenalias.  
  
-   Ersetzen Sie den Spaltenalias durch den Spaltennamen.  
  
 Die beiden folgenden Abfragen werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] beispielsweise ohne Fehler ausgeführt:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
