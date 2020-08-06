---
title: Beschränken der Größe von Ablaufverfolgungsdatei und -tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7795dfdadb8fb3bbaa1b55dcd5c962d24a7ba29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619761"
---
# <a name="limit-trace-file-and-table-sizes"></a>Beschränken der Größe von Ablaufverfolgungsdatei und -tabelle
  Abhängig von den in der Ablaufverfolgung enthaltenen Ereignisklassen und der Verwendungsweise des [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann der Umfang der Ergebnisse der SQL-Ablaufverfolgung variieren. Wenn Sie eine Ablaufverfolgung für häufig auftretende Ereignisklassen durchführen, können Sie die dabei gesammelten Daten minimieren, indem Sie die maximale Dateigröße und die maximale Anzahl von Zeilen festlegen. Durch Angabe der maximalen Dateigröße oder der maximalen Zeilen können Sie sicherstellen, dass die Ablaufverfolgungsdatei oder -tabelle nicht über das angegebene Limit hinaus anwächst.  
  
> [!NOTE]  
>  Beim Speichern von Ablaufverfolgungsdaten in einer bereits vorhandenen Datei können Sie Daten an die Datei anfügen oder die Datei überschreiben. Wenn Sie Daten an die Datei anfügen und die Ablaufverfolgungsdatei die angegebene maximale Dateigröße bereits erreicht oder überschreitet, werden Sie benachrichtigt. Sie haben dann die Möglichkeit, den Wert für die maximale Dateigröße zu erweitern oder eine neue Datei anzugeben. Dasselbe gilt für Ablaufverfolgungstabellen.  
  
## <a name="maximum-file-size"></a>Maximale Dateigröße  
 Eine Ablaufverfolgung mit einer maximalen Dateigröße speichert keine weiteren Ablaufverfolgungsinformationen in der Datei, wenn die maximale Dateigröße erreicht wurde. Mit dieser Option können Sie Ereignisse in kleineren, leichter zu verwaltenden Dateien gruppieren. Darüber hinaus erhöht eine Beschränkung der Dateigröße die Sicherheit bei der Ausführung unbeaufsichtigter Ablaufverfolgungen, da die Ablaufverfolgung beendet wird, wenn die maximale Datengröße erreicht wurde. Sie können die maximale Dateigröße für erstellte Ablaufverfolgungen entweder mit gespeicherten Prozeduren von Transact-SQL oder mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]festlegen.  
  
 Die höchste Grenze für die maximale Dateigröße ist 1 Gigabyte (GB). Standardmäßig beträgt die maximale Dateigröße 5 Megabyte (MB).  
  
### <a name="enabling-file-rollover"></a>Aktivieren des Dateirollovers  
 Die Dateirolloveroption führt dazu, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die aktuelle Datei schließt und eine neue Datei erstellt, wenn die maximale Dateigröße erreicht ist. Der Name der neuen Datei stimmt mit dem der vorigen Datei überein, wird jedoch durch eine angefügte ganze Zahl ergänzt, um die Position der Datei in der Sequenz anzuzeigen. Lautet der Name der ursprünglichen Ablaufverfolgungsdatei z. B. filename_1.trc, wird die nächste Datei mit filename_2.trc benannt usw. Wird der einer neuen Rolloverdatei zugewiesene Name bereits von einer vorhandenen Datei verwendet, wird die vorhandene Datei überschrieben, es sei denn, die Datei ist schreibgeschützt. Die Dateirolloveroption ist standardmäßig aktiviert, wenn Sie Ablaufverfolgungsdaten in einer Datei speichern.  
  
> [!NOTE]  
>  Bei aktivierter Dateirolloveroption wird die Ablaufverfolgung fortgesetzt, bis sie auf andere Weise beendet wird. Um die Ablaufverfolgung zu beenden, nachdem die Dateigrößenbeschränkung erreicht wurde, deaktivieren Sie die Dateirolloveroption.  
  
 **So legen Sie die maximale Dateigröße für eine Ablaufverfolgungsdatei fest**  
  
 [Festlegen einer maximalen Dateigröße für eine Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a>Maximale Zeilenanzahl  
 Eine Ablaufverfolgung mit einer maximalen Zeilenzahl speichert keine weiteren Ablaufverfolgungsinformationen in einer Tabelle, wenn die maximale Zeilenzahl erreicht wurde. Jedes Ereignis bildet eine Zeile, sodass dieser Parameter eine Beschränkung für die Anzahl der gesammelten Ereignisse festlegt. Das Festlegen der maximalen Zeilenzahl erleichtert die Ausführung unbeaufsichtigter Ablaufverfolgungen. Sie können z. B. eine Ablaufverfolgung starten, bei der die Ablaufverfolgungsdaten in einer Tabelle gespeichert werden, und die Ablaufverfolgung automatisch beenden lassen, wenn die Tabelle zu groß wird.  
  
 Wenn die maximale Zeilenzahl angegeben und diese Zahl erreicht wurde, wird die Ablaufverfolgung fortgesetzt, während [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ausgeführt wird, aber es werden keine Ablaufverfolgungsinformationen mehr aufgezeichnet. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] weiterhin angezeigt, bis die Ablaufverfolgung angehalten wird.  
  
 **So legen Sie die maximale Zeilenzahl für eine Ablaufverfolgung fest**  
  
 [Festlegen der maximalen Tabellengröße für eine Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
  
