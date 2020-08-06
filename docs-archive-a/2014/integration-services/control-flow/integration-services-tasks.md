---
title: Integration Services-Tasks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616624"
---
# <a name="integration-services-tasks"></a>Integration Services-Tasks
  Tasks sind Ablaufsteuerungselemente, mit denen Arbeitseinheiten definiert werden, die in einer Paketablaufsteuerung ausgeführt werden. Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket besteht aus mindestens einem Task. Enthält das Paket mehrere Tasks, werden sie in der Ablaufsteuerung durch Rangfolgeneinschränkungen miteinander verbunden und angeordnet.  
  
 Mit einer Programmiersprache, die COM unterstützt, wie z. B. Visual Basic, oder einer .NET-Programmiersprache, wie z. B. C#, können Sie auch benutzerdefinierte Tasks erstellen.  
  
 Der [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Designer ist das grafische Tool in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] für das Arbeiten mit Paketen. Er stellt die Entwurfsoberfläche zum Erstellen von Paketablaufsteuerungen und benutzerdefinierte Editoren zum Konfigurieren von Tasks bereit. Darüber hinaus können Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Objektmodell so programmieren, dass Pakete programmgesteuert erstellt werden.  
  
## <a name="types-of-tasks"></a>Tasktypen  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] schließt die folgenden Arten von Tasks ein.  
  
 Datenflusstask  
 Dieser Task führt Datenflüsse aus, um Daten zu extrahieren, Transformationen auf Spaltenebene anzuwenden und Daten zu laden.  
  
 Datenvorbereitungstasks  
 Mit diesen Tasks werden folgende Prozesse ausgeführt: Kopieren von Dateien und Verzeichnissen, Herunterladen von Dateien und Daten, Ausführen von Webmethoden, Übernehmen von Vorgängen für XML-Dokumente und Datenprofilerstellung zum Reinigen.  
  
 Workflowtasks  
 Diese Tasks kommunizieren mit anderen Prozessen, um Pakete, Programme oder Batchdateien auszuführen, Nachrichten zwischen Paketen zu senden und zu empfangen, E-Mail-Nachrichten zu senden, WMI-Daten (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation) zu lesen und WMI-Ereignisse zu überwachen.  
  
 SQL Server-Tasks  
 Mit diesen Tasks werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekte und -Daten geöffnet, kopiert, eingefügt, gelöscht und geändert.  
  
 Skripttasks  
 Diese Tasks erweitern die Paketfunktionalität mithilfe von Skripts.  
  
 Analysis Services-Tasks  
 Mit diesen Tasks werden [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte erstellt, geändert, gelöscht und verarbeitet.  
  
 Wartungstasks  
 Mit diesen Tasks werden administrative Funktionen ausgeführt, wie z. B. das Sichern und Verkleinern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken, das erneute Erstellen und Organisieren von Indizes sowie das Ausführen von Aufträgen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.  
  
 Benutzerdefinierte Tasks  
 Mit einer Programmiersprache, die COM unterstützt, wie z. B. Visual Basic, oder einer .NET-Programmiersprache, wie z. B. C#, können Sie außerdem benutzerdefinierte Tasks erstellen. Wenn Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer auf benutzerdefinierte Tasks zugreifen möchten, können Sie dafür eine Benutzeroberfläche erstellen und registrieren. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="configuration-of-tasks"></a>Konfiguration von Tasks  
 Ein Paket von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] kann einen einzelnen Task enthalten, wie z. B. einen Task SQL ausführen, der Datensätze in einer Datenbanktabelle löscht, wenn das Paket ausgeführt wird. Pakete enthalten jedoch normalerweise mehrere Tasks, und für jeden Task ist festgelegt, dass er im Kontext der Paketablaufsteuerung ausgeführt wird. Für Ereignishandler, bei denen es sich um Workflows handelt, die als Antwort auf Laufzeitereignisse ausgeführt werden, sind ebenfalls Tasks möglich.  
  
 Weitere Informationen zum Hinzufügen eines Tasks zu einem Paket mit [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](add-or-delete-a-task-or-a-container-in-a-control-flow.md).  
  
 Weitere Informationen zum programmgesteuerten Hinzufügen eines Tasks zu einem Paket finden Sie unter [Programmgesteuertes Hinzufügen von Tasks](../building-packages-programmatically/adding-tasks-programmatically.md).  
  
 Jeder Task kann einzeln mithilfe der benutzerdefinierten Dialogfelder für die verschiedenen Tasks des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers konfiguriert werden oder mithilfe des Eigenschaftenfensters von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. In einem Paket können mehrere Tasks desselben Typs vorhanden sein, z.B. sechs Tasks vom Typ SQL ausführen, wobei jeder Task unterschiedlich konfiguriert sein kann. Weitere Informationen finden Sie unter [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="tasks-connections-and-groups"></a>Tasks "Verbindungen" und "Gruppen"  
 Wenn mehrere Tasks vorhanden sind, werden sie in der Ablaufsteuerung durch Rangfolgeneinschränkungen miteinander verbunden und angeordnet. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](precedence-constraints.md).  
  
 Tasks können gruppiert und als eine einzelne Arbeitseinheit ausgeführt oder in einer Schleife wiederholt werden. Weitere Informationen finden Sie unter [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md)und [Sequence Container](sequence-container.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
