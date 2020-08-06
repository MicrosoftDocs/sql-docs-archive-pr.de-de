---
title: Veröffentlichungsinformationen, Alle Abonnements (Mergeveröffentlichung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251e4c6e2e2adc60c838c7875d5d7d99aee64b54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724502"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a>Veröffentlichungsinformationen, Alle Abonnements (Mergeveröffentlichung)
   Auf der Registerkarte **Alle Abonnements** werden Informationen zu allen Abonnements der ausgewählten Mergeveröffentlichung angezeigt.  
  
## <a name="options"></a>Tastatur  
 Ausführliche Informationen und eine Liste der Aufträge für ein Abonnement können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Abonnements klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren**: Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren** .  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen** .  
  
-   **Filter löschen**: Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Anzeigen**  
 Nur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Wählen Sie die Abonnementstatus aus, die für Abonnements des ausgewählten Typs angezeigt werden sollen. Sie können z. B. auswählen, dass nur die Abonnements angezeigt werden, die einen Fehler aufweisen.  
  
 **Status**  
 Der Status der einzelnen Abonnements, der durch den Status des Merge-Agents bestimmt wird.  
  
 Standardmäßig wird das Raster mit den Abonnementinformationen nach den Werten in der **Status** -Spalte sortiert (bei Abonnements mit demselben Status wird nach den Werten unter **Leistung** sortiert). In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt).  
  
-   Fehler  
  
-   Leistung ist kritisch (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   Langer Mergevorgang (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   Läuft demnächst ab/Abgelaufen (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   Nicht initialisiertes Abonnement (nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen)  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   Wird synchronisiert  
  
-   Synchronisierung wird nicht ausgeführt  
  
 Die Sortierreihenfolge bestimmt auch, welcher Wert angezeigt wird, wenn ein Abonnement mehr als einen Statuswert aufweist. Wenn ein Abonnement z. B. einen Fehler aufweist und bald abläuft, dann wird in der **Status** -Spalte der Eintrag **Fehler**angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Langer Mergevorgang**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiertes Abonnement** stellen Warnungen dar. Wenn eine Warnung angezeigt wird, wird unter **Status** auch angezeigt, ob ein Agent synchronisiert wird. Der Status kann also beispielsweise **Wird synchronisiert, Leistungskritisch**sein.  
  
 Die Statuswerte **Läuft demnächst ab/Abgelaufen** und **Langer Mergevorgang** können nur angezeigt werden, wenn Schwellenwerte festgelegt sind. Der Statuswert **Leistung ist kritisch** kann nur angezeigt werden, nachdem fünf Synchronisierungen mit demselben Verbindungstyp (DFÜ oder LAN) stattgefunden haben. Informationen zu Leistungsmessungen und zum Festlegen von Schwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md) und [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name des jeweiligen Abonnements in folgendem Format:*SubscriberName: SubscriptionDatabaseName*.  
  
 **Anzeigename**  
 Nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Die Beschreibung der einzelnen Abonnements. Die Beschreibung wird im Dialogfeld **Abonnementeigenschaften** eingegeben oder mit dem **@description** -Parameter von [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) oder [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)angezeigt. Benutzer verwenden die Beschreibung häufig als Anzeigename oder Spitzname des Abonnements.  
  
 **Leistung**  
 Nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Die Leistungsbewertung für die einzelnen Abonnements auf der Grundlage der neuesten Messungen der Übermittlungsrate mithilfe des Replikationsmonitors. Die Bewertung wird bestimmt, indem die Leistung der einzelnen Abonnements mit der durchschnittlichen bisherigen Leistung der Veröffentlichungsabonnements mit dem gleichen Verbindungstyp (DFÜ oder LAN) verglichen wird. Der Replikationsmonitor zeigt einen Wert an, nachdem fünf Synchronisierungen mit jeweils mindestens 50 Änderungen über denselben Verbindungstyp stattgefunden haben. Falls weniger als fünf Synchronisierungen mit mindestens 50 Änderungen stattgefunden haben, oder wenn die letzte Synchronisierung nicht mindestens 50 Änderungen umfasst hat, ist diese Spalte leer.  
  
> [!NOTE]  
>  Die Leistung basiert auf dem in der **Verbindung** -Spalte angezeigten Verbindungstyp. Deshalb ist es möglich, dass für ein Abonnement mit einer geringeren Übermittlungsrate eine bessere Leistungsbewertung angezeigt wird, als für ein anderes Abonnement, wenn das erste Abonnement über eine langsamere Verbindung synchronisiert wird.  
  
 Die folgenden Werte sind für die Leistungsbewertung möglich:  
  
-   Ausgezeichnet  
  
-   Gut  
  
-   Mittelmäßig  
  
-   Schlecht  
  
 Weitere Informationen zur Definition von Leistungsbewertungen und zum Festlegen von Leistungsschwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md).  
  
 **Übermittlungsrate**  
 Die Anzahl an Zeilen, die pro Sekunde vom Merge-Agent verarbeitet werden.  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung von Merge-Agent. Während dieser Synchronisierung können Änderungen verarbeitet worden sein oder nicht. Wenn sich eine Synchronisierung in Bearbeitung befindet, wird ein vollständiger Prozentwert angezeigt.  
  
 **Duration**  
 Der Zeitraum der Ausführung von Merge-Agent während der letzten Synchronisierung. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit synchronisierten Merge-Agents oder die Gesamtzeit des zuvor synchronisierten Merge-Agents an.  
  
 **Connection**  
 Nur in[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Die Art der Verbindung zwischen dem Abonnenten und dem Verleger. Die Werte **LAN**, **DFÜ**und **Internet**sind möglich. Der Wert **Internet** wird angezeigt, wenn für das Abonnement die Websynchronisierung verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikations Monitors](monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)   
 [Websynchronisierung für die Mergereplikation](web-synchronization-for-merge-replication.md)  
  
  
