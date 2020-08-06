---
title: sqlagent90-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 290cb69f39aa3b08bb290c210b2d37977614a1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615724"
---
# <a name="sqlagent90-application"></a>sqlagent90 (Anwendung)
  Mit der Anwendung **sqlagent90** wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über die Eingabeaufforderung gestartet. Normalerweise sollte der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder mithilfe von SQL-SMO-Methoden in einer Anwendung gestartet werden. Führen Sie **sqlagent90** nur dann über die Eingabeaufforderung aus, wenn Sie Probleme im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent diagnostizieren, oder wenn Sie von Ihrem primären Anbieter für technischen Support dazu aufgefordert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlagent90  
-c [-v] [-iinstance_name]  
```  
  
## <a name="arguments"></a>Argumente  
 **-c**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent über die Eingabeaufforderung ausgeführt wird und unabhängig vom Microsoft Windows-Dienststeuerungs-Manager ist. Wenn **-c** verwendet wird, kann der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent weder über die Anwendung Dienste in der Verwaltung noch über den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager gesteuert werden. Dieses Argument ist verbindlich.  
  
 **-v**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent im ausführlichen Modus ausgeführt wird und dass Diagnoseinformationen im Eingabeaufforderungsfenster ausgegeben werden sollen. Die Diagnoseinformationen sind mit den Informationen identisch, die in das Fehlerprotokoll des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agents geschrieben werden.  
  
 **-i** *Instanzname*  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent eine Verbindung mit der benannten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellt, die mit *Instanzname*angegeben wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Nach dem Anzeigen einer Copyrightmeldung zeigt **sqlagent90** Ausgaben nur dann im Eingabeaufforderungsfenster an, wenn der Schalter **-v** angegeben ist. Zum Beenden von **sqlagent90**drücken Sie STRG+C an der Eingabeaufforderung. Schließen Sie das Eingabeaufforderungsfenster nicht, bevor Sie **sqlagent90**beendet haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Automatisierte Administrationstasks &#40;SQL Server-Agent&#41;](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  
