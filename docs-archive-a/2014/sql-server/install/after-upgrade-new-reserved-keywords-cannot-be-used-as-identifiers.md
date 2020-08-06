---
title: Nach dem Upgrade können neue reservierte Schlüsselwörter nicht als Bezeichner verwendet werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 36f7f8cadcba5e114feee4a3c42de6f40070ce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617537"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a>Nach dem Upgrade können neue reservierte Schlüsselwörter nicht als Bezeichner verwendet werden
  Der Upgrade Advisor hat die Verwendung von Wörtern erkannt, die als Schlüsselwörter reserviert sind. Ein reserviertes Schlüsselwort kann nicht als Bezeichner oder Objektname verwendet werden, es sei denn, der Name ist mit Trennzeichen versehen.  
  
## <a name="component"></a>Komponente  
 Datenbank-Engine  
  
## <a name="description"></a>BESCHREIBUNG  
 Bei Kompatibilitätsgrad 90 oder niedriger sind die folgenden Wörter keine reservierten Schlüsselwörter und können in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripts als Bezeichner oder Objektnamen verwendet werden. Bei Kompatibilitätsgrad 100 sind diese Wörter vollständig reservierte Schlüsselwörter und sollten nicht als Bezeichner oder Objektnamen verwendet werden.  
  
-   EXTERNAL  
  
-   MERGE  
  
-   PIVOT  
  
-   REVERT  
  
-   STOPLIST  
  
-   TABLESAMPLE  
  
-   UNPIVOT  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Es wird empfohlen, das Objekt umzubenennen. Falls dies vor dem Upgrade nicht möglich ist, können Sie eine der folgenden Methoden verwenden, bis der Name geändert werden kann:  
  
-   Behalten Sie die Einstellung von 90 oder niedriger für den Datenbankkompatibilitätsgrad bei.  
  
-   Verweisen Sie mit Begrenzungsbezeichnern auf das Objekt. Beispielsweise verwendet die-Anweisung eckige `CREATE TABLE [MERGE] ([MERGE] int);` Klammern, um den Objektnamen Merge zu begrenzen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 [Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)  
  
 [Begrenzungsbezeichner (Datenbank-Engine)](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
