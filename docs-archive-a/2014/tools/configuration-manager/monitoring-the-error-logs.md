---
title: Überwachen der Fehlerprotokolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617338"
---
# <a name="monitoring-the-error-logs"></a>Überwachen der Fehlerprotokolle
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] protokolliert bestimmte Systemereignisse und benutzerdefinierte Ereignisse im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll. Beide Protokolle versehen alle aufgezeichneten Ereignisse automatisch mit einem Zeitstempel. Sie können die Informationen im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll für die Problembehandlung bezüglich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.  
  
 Das Windows-Anwendungsprotokoll bietet eine Gesamtübersicht der Ereignisse, die im Windows-Betriebssystem auftreten, sowie der Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents. Verwenden Sie die Windows-Ereignisanzeige, um das Windows-Anwendungsprotokoll anzuzeigen und die Informationen zu filtern. So können Sie beispielsweise Ereignisse, wie Informationen, Warnung, Fehler, Erfolgsüberwachung und Fehlerüberwachung, filtern.  
  
## <a name="comparing-error-and-application-log-output"></a>Vergleichen der Ausgabe des Fehler- und Anwendungsprotokolls  
 Sie können sowohl das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll als auch das Windows-Anwendungsprotokoll verwenden, um die Ursache von Problemen zu identifizieren. Möglicherweise erhalten Sie während der Überwachung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokolls Fehlermeldungen, die keine Informationen zu den Ursachen enthalten. Durch Vergleichen der Daten und Zeiten der Ereignisse zwischen diesen Protokollen können Sie die Liste der wahrscheinlichen Ursachen eingrenzen. Der Protokolldatei-Viewer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ermöglicht die Integration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents und des Windows-Protokolls in eine einzelne Liste. Auf diese Weise können Sie zugehörige Serverereignisse und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignisse besser nachvollziehen. Weitere Informationen finden Sie im Thema zum Protokolldatei-Viewer in der SQL Server-Onlinedokumentation.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Anzeigen des SQL Server-Fehlerprotokolls](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|Enthält Informationen zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll und beschreibt das Anzeigen dieses Fehlerprotokolls.|  
|[Anzeigen des Windows-Anwendungsprotokolls](viewing-the-windows-application-log.md)|Enthält Informationen zum Windows-Fehlerprotokoll und beschreibt das Anzeigen dieses Fehlerprotokolls.|  
  
  
