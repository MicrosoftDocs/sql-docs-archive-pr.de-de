---
title: SQL Server Profiler Quell Tabelle-Datenbankoptimierungsratgeber-Arbeits Auslastungs Tabelle auswählen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d10899c01df8e7fbc7ee45d108841a18d3248500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616666"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>Tabellen Datenbankoptimierungsratgeber-Arbeits Auslastungs Tabelle für SQL Server Profiler Quelle
  In Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] und im Optimierungsratgeber von [!INCLUDE[ssDE](../includes/ssde-md.md)] dient dieses Dialogfeld zur Auswahl von Tabellen.  
  
 In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] können Sie mithilfe des Dialogfelds **Quelltabelle** eine Quelltabelle für eine Ablaufverfolgungstabelle angeben. Dabei handelt es sich um eine Tabelle, aus der eine Ablaufverfolgung geladen wird. Deren Inhalte können angezeigt oder zur Wiedergabe der Ablaufverfolgung verwendet werden.  
  
 Wählen Sie mithilfe des Dialogfelds [!INCLUDE[ssDE](../includes/ssde-md.md)]Arbeitsauslastungstabelle auswählen **im Optimierungsratgeber von** eine Datenbanktabelle mit Ablaufverfolgungsinformationen von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] aus, die als zu optimierende Arbeitsauslastung oder zur Vorschau der Tabelleninhalte vor dem Starten der Optimierungsanalyse verwendet werden sollen.  
  
## <a name="options"></a>Tastatur  
 **SQL Server**  
 Gibt die Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an, zu der zurzeit eine Verbindung besteht. Dieses Feld wird automatisch ausgefüllt und kann nicht aktualisiert werden.  
  
 **Datenbank**  
 Geben Sie die Datenbank an, in der die Ablaufverfolgungstabelle gespeichert ist.  
  
 **Besitzer**  
 Specifies the owner of the trace table. Dieses Feld wird automatisch mit **dbo**ausgefüllt.  
  
 **Tabelle**  
 Geben Sie den Namen der Ablaufverfolgungstabelle an, aus der die Ablaufverfolgung gelesen werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern von Ablaufverfolgungsergebnissen in einer Tabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Datenbankoptimierungsratgeber](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
