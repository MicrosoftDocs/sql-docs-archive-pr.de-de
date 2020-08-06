---
title: Angeben des Abfrageparametrisierungsverhaltens mithilfe von Planhinweislisten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f595b9f0e0a6d7bceffc5cb283c60b6f40e025b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622603"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a>Angeben des Abfrageparametrisierungsverhaltens mithilfe von Planhinweislisten
  Wenn die PARAMETERIZATION-Datenbankoption auf SIMPLE festgelegt ist, kann der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abfrageoptimierer die Abfragen ggf. parametrisieren. Dies bedeutet, dass alle eventuell in einer Abfrage enthaltenen Literalwerte durch Parameter ersetzt werden. Dieses Verfahren wird als einfache Parametrisierung bezeichnet. Wenn die einfache Parametrisierung aktiviert ist, können Sie nicht steuern, welche Abfragen parametrisiert werden sollen und welche nicht. Sie können jedoch angeben, dass alle Abfragen einer Datenbank parametrisiert werden sollen, indem Sie die PARAMETERIZATION-Datenbankoption auf FORCED festlegen. Dieses Verfahren wird als erzwungene Parametrisierung bezeichnet.  
  
 Sie können das Parametrisierungsverhalten einer Datenbank überschreiben, in dem Sie Planhinweislisten verwenden. Es gibt dabei folgende Möglichkeiten:  
  
-   Wenn die PARAMETERIZATION-Datenbankoption auf SIMPLE festgelegt ist, können Sie angeben, dass für eine bestimmte Abfrageklasse die erzwungene Parametrisierung versucht werden soll. Erstellen Sie dazu eine TEMPLATE-Planhinweisliste für die parametrisierte Form der Abfrage, und geben Sie den PARAMETERIZATION FORCED-Abfragehinweis in der gespeicherten Prozedur [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) an. Betrachten Sie diese Art, Planhinweislisten zu verwenden, als Verfahren, die erzwungene Parametrisierung nur für eine bestimmte, jedoch nicht alle Abfrageklassen zu aktivieren.  
  
-   Wenn die PARAMETERIZATION-Datenbankoption auf FORCED festgelegt ist, können Sie angeben, dass für eine bestimmte Abfrageklasse nur die einfache Parametrisierung versucht werden soll, jedoch nicht die erzwungene Parametrisierung. Erstellen Sie dazu eine TEMPLATE-Planhinweisliste für die erzwungene parametrisierte Form der Abfrage, und geben Sie in **sp_create_plan_guide**den PARAMETERIZATION SIMPLE-Abfragehinweis an.  
  
 Betrachten Sie die folgende Abfrage in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank:  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 Als Datenbankadministrator haben Sie bestimmt, dass Sie die erzwungene Parametrisierung nicht für alle Abfragen der Datenbank aktivieren möchten. Sie sind jedoch darauf bedacht, den Aufwand zu vermeiden, alle Abfragen neu zu kompilieren, obwohl sie syntaktisch mit vorherigen Abfragen gleichwertig sind und sich lediglich durch ihre konstanten Literalwerte unterscheiden. Mit anderen Worten möchten Sie solche Abfragen parametrisieren, sodass für diese Art von Abfragen ein Abfrageplan wiederverwendet wird. Führen Sie in diesem Fall die folgenden Schritte aus:  
  
1.  Rufen Sie die parametrisierte Form der Abfrage ab. Die einzig sichere Möglichkeit, diesen Wert zum Verwenden in **sp_create_plan_guide** abzurufen, besteht in der Verwendung der gespeicherten Systemprozedur [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) .  
  
2.  Erstellen Sie die Planhinweisliste für die parametrisierte Form der Abfrage, indem Sie den PARAMETERIZATION FORCED-Abfragehinweis angeben.  
  
    > [!IMPORTANT]  
    >  Im Rahmen der Parametrisierung einer Abfrage weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Parametern, die die Literalwerte ersetzen, abhängig von Wert und Größe der Literalwerte, einen Datentyp zu. Der gleiche Vorgang erfolgt beim Wert der konstanten Literale, die an den **@stmt** Output-Parameter von **sp_get_query_template**übergeben werden. Da der Datentyp, der im- **@params** Argument **sp_create_plan_guide** angegeben ist, mit dem der Abfrage identisch sein muss, wenn er von parametrisiert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie möglicherweise mehr als eine Plan Hinweis Liste erstellen, um den gesamten Bereich möglicher Parameterwerte für die Abfrage abzudecken.  
  
 Verwenden Sie das folgende Skript, um die parametrisierte Abfrage und anschließend eine Planhinweisliste dafür zu erstellen:  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 Auf ähnliche Weise können Sie in einer Datenbank mit bereits aktivierter erzwungener Parametrisierung sicherstellen, dass die Beispielabfrage und andere, mit Ausnahme ihrer konstanten Literalwerte, syntaktisch gleichwertige Abfragen gemäß den Regeln für die einfache Parametrisierung parametrisiert werden. Geben Sie dazu in der OPTION-Klausel PARAMETERIZATION SIMPLE anstelle von PARAMETERIZATION FORCED an.  
  
> [!NOTE]  
>  Durch TEMPLATE-Planhinweislisten wird eine Übereinstimmung zwischen Anweisungen und batchweise übermittelten Abfragen hergestellt, die nur aus einer einzigen Anweisung bestehen. Für Anweisungen innerhalb von Batches mit mehreren Anweisungen können TEMPLATE-Planhinweislisten keine Übereinstimmungen herstellen.  
  
  
