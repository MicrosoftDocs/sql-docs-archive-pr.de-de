---
title: Editor für den Task Aufträge übertragen (Seite Aufträge) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630711"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Editor für den Task Aufträge übertragen (Seite Aufträge)
  Auf der Seite **Aufträge** des Dialogfelds **Editor für den Task "Aufträge übertragen"** können Sie die Eigenschaften für das Kopieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agentaufträgen von einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in eine andere angeben. Weitere Informationen zum Task Aufträge übertragen finden Sie unter [Transfer Jobs Task](control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Um auf dem Quellserver auf Aufträge zuzugreifen, müssen Benutzer auf dem Server Mitglied mindestens einer festen Serverrolle **SQLAgentUserRole** sein. Um auf dem Zielserver Aufträge erfolgreich zu erstellen, muss der Benutzer Mitglied der festen Datenbankrolle **sysadmin** oder einer der festen Datenbankrollen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents sein. Weitere Informationen zu den festen Datenbankrollen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents und zu deren Berechtigungen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="options"></a>Tastatur  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<New connection...>** , um eine neue Verbindung mit dem Quellserver zu erstellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<New connection...>** , um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **TransferAllJobs**  
 Wählen Sie aus, ob der Task alle oder nur angegebene [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agentaufträge vom Quell- auf den Zielserver kopieren soll.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**True**|Kopiert alle Aufträge.|  
|**False**|Kopiert nur angegebene Aufträge.|  
  
 **JobsList**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , um die zu kopierenden Aufträge auszuwählen. Es muss mindestens ein Auftrag ausgewählt werden.  
  
> [!NOTE]  
>  Geben Sie vor der Auswahl der zu kopierenden Aufträge **SourceConnection** an.  
  
 Die Option **JobsList** ist nicht verfügbar, wenn **TransferAllJobs** auf **True**festgelegt ist.  
  
 **IfObjectExists**  
 Wählen Sie aus, wie der Task Aufträge behandeln soll, die auf dem Zielserver bereits mit demselben Namen vorhanden sind.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**FailTask**|Der Task schlägt fehl, wenn auf dem Zielserver bereits Aufträge mit demselben Namen vorhanden sind.|  
|**Overwrite**|Der Task überschreibt auf dem Zielserver Aufträge mit demselben Namen.|  
|**Skip**|Der Task lässt Aufträge aus, die auf dem Zielserver mit demselben Namen vorhanden sind.|  
  
 **EnableJobsAtDestination**  
 Wählen Sie aus, ob die auf den Zielserver kopierten Aufträge aktiviert werden sollen.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**True**|Aktiviert Jobs auf dem Zielserver.|  
|**False**|Deaktiviert Jobs auf dem Zielserver.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task Aufträge übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
