---
title: Verleger Informationen, Überwachungsliste für Abonnements (Momentaufnahme Veröffentlichung, SQL Server 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701049"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a>Verlegerinformationen, Überwachungsliste für Abonnements (Momentaufnahmeveröffentlichung, SQL Server 2005 und höher)
   Die Registerkarte **Überwachungsliste für Abonnements** ist für Verteiler verfügbar, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen ausgeführt werden. Sie ist dafür konzipiert, Informationen zu Abonnements von allen Veröffentlichungen anzuzeigen, die für den ausgewählten Verleger verfügbar sind. Sie können die Liste der Abonnements filtern, um Fehler, Warnungen und Abonnements mit schlechter Leistung anzuzeigen. Diese Registerkarte stellt einen einzelnen Speicherort für Administratoren bereit, um alle Replikationsaktivitäten bei einem Verleger zu überwachen: Der Replikationsmonitor zeigt alle Abonnements an, die Aufmerksamkeit erfordern. Grundlage hierfür ist der ausgewählte Replikationstyp und die im Dropdownlistenfeld **Anzeigen** ausgewählte Option. Da die auf dieser Registerkarte angezeigten Elemente auf den aktuellen Daten für Status und Leistung basieren, werden auf dieser Seite nur Abonnements angezeigt, die mit der Option im Listenfeld **Anzeigen** zum aktuellen Zeitpunkt übereinstimmen.  
  
## <a name="options"></a>Tastatur  
 Ausführliche Informationen und eine Liste der Aufträge für ein Abonnement können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Abonnements klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren**: Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren** .  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen** .  
  
-   **Filter löschen**: Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Momentaufnahmeabonnements anzeigen**  
 Wählen Sie den Typ der Abonnements (Transaktionsreplikation, Momentaufnahme oder Mergereplikation) aus, die für den ausgewählten Verleger angezeigt werden sollen.  
  
 **Anzeigen**  
 Wählen Sie die Abonnementstatus aus, die für Abonnements des ausgewählten Typs angezeigt werden sollen. Sie können z. B. auswählen, dass nur die Abonnements angezeigt werden, die einen Fehler aufweisen.  
  
 **Status**  
 Der Status jedes Abonnements, der vom Status des Momentaufnahme-Agents oder des Verteilungs-Agents bestimmt wird (der Status mit der höheren Priorität wird angezeigt).  
  
 Standardmäßig wird das Raster mit den Abonnementinformationen nach der **Status** -Spalte sortiert. In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt).  
  
-   Fehler  
  
-   Läuft demnächst ab/Abgelaufen  
  
-   Nicht initialisiertes Abonnement  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   Wird synchronisiert  
  
-   Synchronisierung wird nicht ausgeführt  
  
 Die Sortierreihenfolge bestimmt auch, welcher Wert angezeigt wird, wenn ein Abonnement mehr als einen Statuswert aufweist. Wenn ein Abonnement z. B. einen Fehler aufweist und bald abläuft, dann wird in der **Status** -Spalte der Eintrag **Fehler**angezeigt.  
  
 Die Statuswerte **Läuft demnächst ab/Abgelaufen** und **Nicht initialisiertes Abonnement** stellen Warnungen dar. Wenn eine Warnung angezeigt wird, wird unter **Status** auch angezeigt, ob ein Agent ausgeführt wird. Der Status kann beispielsweise **Wird ausgeführt, Läuft demnächst ab/Abgelaufen**lauten.  
  
 Der Statuswert **Läuft demnächst ab/Abgelaufen** wird nur angezeigt, wenn ein Schwellenwert festgelegt wird. Informationen zum Festlegen von Schwellenwerten finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Abonnement**  
 Der Name des jeweiligen Abonnements in folgendem Format: *SubscriberName: SubscriptionDatabaseName*.  
  
 **Veröffentlichung**  
 Der Name der Veröffentlichung, mit der ein Abonnement synchronisiert wird, in folgendem Format: *PublicationDatabaseName: PublicationName*.  
  
 **Letzte Synchronisierung**  
 Der Zeitpunkt der letzten Ausführung des Verteilungs-Agents. Wenn eine Synchronisierung ausgeführt wird, wird **Vorgang wird ausgeführt** angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikations Monitors](monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
