---
title: Ausführen von Aufträgen zur Replikationswartung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721401"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Ausführen von Aufträgen zur Replikationswartung (SQL Server Management Studio)
  Bei der Replikation werden folgende Wartungsaufträge verwendet:  
  
-   **Abonnements mit Datenüberprüfungsfehlern neu initialisieren**
-   **Agentverlaufscleanup: Verteilung**
-   **Aktualisierung für die Replikationsüberwachung für Verteilung.**
-   **Überprüfung des Replikations-Agents**
-   **Verteilungscleanup: Verteilung**
-   **Cleanup abgelaufener Abonnements**  
  
 Diese Aufträge können über den Ordner **Aufträge** in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sowie über die Registerkarte **Agents** im Replikationsmonitor gestartet und beendet werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md). Die Eigenschaften der einzelnen Aufträge können im Dialogfeld **Auftragseigenschaften - \<Job>** angezeigt und überprüft werden. Der Zugriff hierauf ist über denselben Ordner/dieselbe Registerkarte verfügbar.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>So starten Sie einen Auftrag zur Replikationswartung in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>So starten Sie einen Auftrag zur Replikationswartung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor eine Verlegergruppe, und wählen Sie dann einen Verleger aus.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>So zeigen Sie Eigenschaften für einen Auftrag zur Replikationswartung in Management Studio an oder ändern sie  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie im Dialogfeld **Auftragseigenschaften - \<Job>** bei Bedarf Eigenschaften, und klicken Sie dann auf **OK**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>So zeigen Sie Eigenschaften für einen Auftrag zur Replikationswartung im Replikationsmonitor an oder ändern sie  
  
1.  Erweitern Sie im Replikationsmonitor eine Verlegergruppe, und wählen Sie dann einen Verleger aus.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Auftrag im Raster, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie im Dialogfeld **Auftragseigenschaften - \<Job>** bei Bedarf Eigenschaften, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Replikations-Agent-Verwaltung](../agents/replication-agent-administration.md)  
  
  
