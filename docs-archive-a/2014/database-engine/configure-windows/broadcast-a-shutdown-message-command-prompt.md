---
title: Senden einer Nachricht über das Herunterfahren (Befehlszeile) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 540baada4a78d7b5caf54cbabb9196ce5a79780e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701882"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>Senden einer Nachricht über das Herunterfahren (Befehlszeile)
  In diesem Thema wird beschrieben, wie Sie mit dem Befehl [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] net send **eine Nachricht zum Herunterfahren in** übertragen. Schließen Sie den Zeitpunkt, zu dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beendet wird, in die Nachricht ein, damit alle Benutzer ihre Aufgaben beenden können.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>So senden Sie eine Nachricht über das Herunterfahren  
  
1.  Geben Sie in einer Befehlszeile Folgendes ein:  
  
     **net send /users "Nachricht"**  
  
     Durch die Option **/users** wird angegeben, dass die Nachricht an alle Benutzer gesendet wird, die mit dem Server verbunden sind.  
  
> [!NOTE]  
>  Der Befehl **net send** erfordert, dass der Nachrichtendienst sowohl auf dem sendenden als auch auf den empfangenden Computern ausgeführt wird. Der Nachrichtendienst ist in Windows Server 2003 standardmäßig deaktiviert. Weitere Informationen zu **net send**finden Sie in der Windows-Dokumentation.  
  
 Es könnte im Netzwerk geeigneter sein, die Benutzer per E-Mail oder telefonisch zu verständigen. Verwenden Sie zum Bestimmen, welche Benutzer gerade mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden sind, den Aktivitätsmonitor. Informationen zum Aktivitätsmonitor finden Sie unter [Aktivitätsmonitor](../../relational-databases/performance-monitor/activity-monitor.md) und [Öffnen des Aktivitätsmonitors &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
