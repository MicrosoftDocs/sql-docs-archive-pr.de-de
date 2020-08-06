---
title: Veröffentlichungsinformationen, Überwachungs Token (Transaktions Veröffentlichung, SQL Server 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af84ab9b9122a55367780976056ce95aa597f62a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721301"
---
# <a name="publication-information-tracer-tokens-transactional-publication-sql-server-2005-and-later"></a>Veröffentlichungsinformationen, Überwachungstoken (Transaktionsveröffentlichung, SQL Server 2005 und höher)
  Mithilfe der Registerkarte **Überwachungstoken** können Sie Verbindungen überprüfen und die Latenzzeit eines Systems messen, das die Transaktionsreplikation verwendet. Ein Token (eine geringe Mange an Daten) wird in das Transaktionsprotokoll der Veröffentlichungsdatenbank geschrieben, wie eine normale replizierte Transaktion gekennzeichnet und über das System gesendet. Auf diese Weise werden die folgenden Berechnungen ermöglicht:  
  
-   Wie viel Zeit zwischen dem Commit einer Transaktion auf dem Verleger und dem Einfügen des zugehörigen Befehls in die Verteilungsdatenbank auf dem Verteiler verstreicht.  
  
-   Wie viel Zeit zwischen dem Einfügen eines Befehls in die Verteilungsdatenbank und dem zugehörigen Commit einer Transaktion auf dem Abonnenten verstreicht.  
  
 Mithilfe dieser Berechnungen können Sie verschiedene Fragen beantworten. Unter anderem diese:  
  
-   Welche Abonnenten benötigen am längsten, um eine Änderung vom Verleger zu empfangen?  
  
-   Welcher der Abonnenten, die Überwachungstoken empfangen sollten, hat keine empfangen?  
  
## <a name="options"></a>Tastatur  
 Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren**: Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren** .  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen** .  
  
-   **Filter löschen**: Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Überwachung einfügen**  
 Klicken Sie auf diese Option, um ein Überwachungstoken in das Transaktionsprotokoll auf dem Verleger einzufügen.  
  
 **Einfügungszeitpunkt**  
 Wählen Sie einen Zeitpunkt aus, zu dem ein Überwachungstoken eingefügt wurde, um die Latenzzeitinformationen für diesen Zeitpunkt anzuzeigen. Standardmäßig werden Informationen zum aktuellsten Zeitpunkt angezeigt.  
  
> [!NOTE]  
>  Die Informationen von Überwachungstoken werden für denselben Zeitraum wie andere Vergangenheitsdaten beibehalten. Der Zeitraum wird durch die Aufbewahrungsdauer für den Verlauf der Verteilungsdatenbank festgelegt. Weitere Informationen zum Ändern der Eigenschaften der Verteilungsdatenbank finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md).  
  
 **Abonnement**  
 Der Name jedes Abonnements für die Veröffentlichung.  
  
 **Verleger zu Verteiler**  
 Die verstrichene Zeit zwischen dem Commit einer Transaktion auf dem Verleger und dem Einfügen des zugehörigen Befehls in die Verteilungsdatenbank auf dem Verteiler. Der Wert **Ausstehend** zeigt an, dass der Token noch nicht beim Verteiler angekommen ist. Überprüfen Sie, ob der Protokolllese-Agent ausgeführt wird, wenn der Status Ausstehend fortdauert.  
  
 **Verteiler zu Abonnent**  
 Die verstrichene Zeit zwischen dem Einfügen eines Befehls in die Verteilungsdatenbank und dem zugehörigen Commit einer Transaktion auf dem Abonnenten. Der Wert **Ausstehend** zeigt an, dass der Token noch nicht beim Abonnenten angekommen ist. Überprüfen Sie, ob der Verteilungs-Agent ausgeführt wird, wenn der Status Ausstehend fortdauert.  
  
 **Gesamtlatenz**  
 Die verstrichene Zeit zwischen dem Commit für eine Transaktion auf dem Verleger und dem zugehörigen Commit für die Transaktion auf dem Abonnenten. Dieser Zeitraum stellt die End-to-End-Latenzzeit des Replikationssystems für diesen Abonnenten zu diesem Zeitpunkt dar. Der Wert **Ausstehend** zeigt an, dass der Token noch nicht beim Abonnenten angekommen ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Starten des Replikations Monitors](monitor/start-the-replication-monitor.md)   
 [Messen der Latenzzeit und Überprüfen der Verbindungen für die Transaktions Replikation](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [Leistungsüberwachung mit dem Replikations Monitor](monitor/monitor-performance-with-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)   
 [Übersicht über Replikations-Agents](agents/replication-agents-overview.md)  
  
  
