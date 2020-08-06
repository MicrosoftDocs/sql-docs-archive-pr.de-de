---
title: Anzeigen oder Ändern von Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699140"
---
# <a name="view-or-modify-jobs"></a>Anzeigen oder Ändern von Aufträgen
  Jeden Auftrag, den Sie erstellt haben, können Sie anzeigen. Nachdem Sie einen Auftrag ausgeführt haben, können Sie auch den Auftragsverlauf anzeigen. Auf diese Weise erfahren Sie, wann der Auftrag ausgeführt wurde, den Status des Auftrags insgesamt sowie den Status jedes Auftragsschritts. Sie sehen, ob bei dem Auftrag in der Vergangenheit jemals ein Fehler aufgetreten ist, wann der Auftrag zuletzt erfolgreich ausgeführt wurde sowie welche Ausgabe bei jeder Ausführung des Auftrags erstellt wurde. Mitglieder der festen Serverrolle **sysadmin** können jeden Auftrag anzeigen oder ändern, unabhängig vom Besitzer.  
  
> [!NOTE]  
>  Ein Auftrag muss mindestens einmal ausgeführt worden sein, damit ein Auftragsverlauf vorhanden ist. Sie können die Gesamtgröße des Auftragsverlaufsprotokolls und die Größe pro Auftrag begrenzen.  
  
 Schließlich können Sie einen Auftrag an neue Anforderungen anpassen. Sie können Folgendes ändern:  
  
-   Benachrichtigungsoptionen  
  
-   Zeitpläne  
  
-   Auftragsschritte  
  
-   Besitz  
  
-   Auftragskategorie  
  
-   Zielserver (ausschließlich bei Multiserveraufträgen)  
  
 Wenn Sie Änderungen an Multiserveraufträgen vornehmen, müssen Sie die Änderungen der Downloadliste bereitstellen, damit die Zielserver den aktualisierten Auftrag herunterladen können. Um sicherzustellen, dass die Zielserver über die aktuellsten Auftragsdefinitionen verfügen, führen Sie nach dem Aktualisieren des Multiserverauftrags wie folgt eine INSERT-Anweisung aus:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Weitere Informationen finden Sie unter [sp_purge_jobhistory &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).  
  
 Mitglieder der festen Serverrolle **sysadmin** können die Definition oder den Verlauf jedes Auftrags anzeigen und können jeden Auftrag ändern.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Aufträge angezeigt werden.|[View a Job](view-a-job.md)|  
|Beschreibt, wie das Auftragsverlaufsprotokoll des [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agents angezeigt wird.|[Anzeigen des Auftragsverlaufs](view-the-job-history.md)|  
|Beschreibt, wie der Inhalt des Auftragsverlaufsprotokolls des [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agents gelöscht wird.|[Clear the Job History Log](clear-the-job-history-log.md)|  
|Beschreibt, wie Größenbeschränkungen für Auftragsverlaufsprotokolle des [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agents festgelegt werden.|[Resize the Job History Log](resize-the-job-history-log.md)|  
|Beschreibt, wie die Eigenschaften von [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Aufträgen geändert werden.|[Ändern eines Auftrags](modify-a-job.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo.sysJobHistory &#40;Transact-SQL-&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
