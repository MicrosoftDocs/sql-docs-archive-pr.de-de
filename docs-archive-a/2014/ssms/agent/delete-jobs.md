---
title: Löschen von Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722201"
---
# <a name="delete-jobs"></a>Löschen von Aufträgen
  Ein Auftrag besteht aus einer festgelegten Folge von Operationen, die der SQL Server-Agent der Reihenfolge nach ausführt. Standardmäßig werden Aufträge nicht gelöscht, wenn die Ausführung beendet wird. Sie können einen oder mehrere [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentaufträge unabhängig davon löschen, ob der Auftrag erfolgreich war. Außerdem können Sie den [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum automatischen Löschen von Aufträgen konfigurieren, wenn diese erfolgreich sind, einen Fehler erzeugen oder abgeschlossen werden.  
  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** die [sp_delete_job &#40;gespeicherten Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) -System Prozedur ausführen, um einen Auftrag zu löschen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_delete_job** ausführen, um einen beliebigen Auftrag zu löschen. Ein Benutzer, der kein Mitglied der festen Serverrolle **sysadmin** ist, kann nur Aufträge löschen, deren Besitzer er ist.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Es wird beschrieben, wie Sie einen oder mehrere [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentaufträge löschen.|[Löschen eines oder mehrerer Aufträge](delete-one-or-more-jobs.md)|  
|Es wird die Vorgehensweise zum Konfigurieren des [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents für das automatische Löschen von Aufträgen beschrieben, wenn diese erfolgreich sind, einen Fehler erzeugen oder abgeschlossen werden.|[Automatically Delete a Job](automatically-delete-a-job.md)|  
  
  
