---
title: Massen Einfügungs Task-Editor (Seite Optionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722990"
---
# <a name="bulk-insert-task-editor-options-page"></a>Masseneinfügungstask-Editor (Seite Optionen)
  Auf der Seite **Optionen** des Dialogfelds **Masseneinfügungstask-Editor** können Sie Eigenschaften für den Masseneinfügungsvorgang festlegen. Durch den Masseneinfügungstask werden große Datenmengen in eine Tabelle oder Sicht von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] kopiert.  
  
 Weitere Informationen zum Arbeiten mit Masseneinfügungen finden Sie unter [Masseneinfügungstask](control-flow/bulk-insert-task.md) und [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
## <a name="options"></a>Tastatur  
 **CodePage**  
 Geben Sie die Codepage für die in der Datendatei enthaltenen Daten an.  
  
 **DataFileType**  
 Geben Sie den Wert für den Datentyp an, der beim Ladevorgang verwendet werden soll.  
  
 **BatchSize**  
 Geben Sie die Anzahl der Zeilen in einem Batch an. Der Standardwert ist die gesamte Datendatei. Wenn Sie **BatchSize** auf null festlegen, werden die Daten in einem Batch geladen.  
  
 **LastRow**  
 Geben Sie die letzte zu kopierende Zeile an.  
  
 **FirstRow**  
 Geben Sie die erste zu kopierende Zeile an.  
  
 **Optionen**  
 |Begriff|Definition|  
|----------|----------------|  
|**Check-Einschränkungen**|Wählen Sie diese Option aus, um die Einschränkungen für Tabelle und Spalte zu überprüfen.|  
|**NULL-Werte beibehalten**|Wählen Sie diese Option aus, um NULL-Werte während des Masseneinfügungsvorgangs beizubehalten, statt für leere Spalten Standardwerte einzufügen.|  
|**IDENTITY_INSERT aktivieren**|Wählen Sie diese Option aus, um vorhandene Werte in eine Identitätsspalte einzufügen.|  
|**Tabellensperre**|Wählen Sie diese Option aus, um die Tabelle während des Masseneinfügungsvorgangs zu sperren.|  
|**Trigger auslösen**|Wählen Sie diese Option aus, um das Einfügen, Aktualisieren oder Löschen von Triggern für die Tabelle auszulösen.|  
  
 **SortedData**  
 Geben Sie die ORDER BY-Klausel in der BULK INSERT-Anweisung an. Der Name der angegebenen Spalte muss eine gültige Spalte in der Zieltabelle sein. Der Standardwert lautet `false`. Das bedeutet, dass die Daten nicht durch eine ORDER BY-Klausel sortiert werden.  
  
 **MaxErrors**  
 Geben Sie an, wie viele Fehler maximal auftreten müssen, bevor der Masseneinfügungsvorgang abgebrochen wird. Durch den Wert 0 wird gekennzeichnet, dass eine unendliche Anzahl von Fehlern zulässig ist.  
  
> [!NOTE]  
>  Jede Zeile, die beim Massenladevorgang nicht importiert werden kann, zählt als ein Fehler.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Massen Einfügungs Task-Editor &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Massen Einfügungs Task-Editor &#40;Verbindungs Seite&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
