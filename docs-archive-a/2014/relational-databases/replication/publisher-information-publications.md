---
title: Dialogfeld "Herausgeber Informationen" SQL Server-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3797ae4f9fe8f42b4abec715c63bc627c2a62cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697887"
---
# <a name="sql-server-replication-publisher-information-dialog-box"></a>Dialogfeld ' Verleger Informationen ' SQL Server-Replikation
  Die Registerkarte **Veröffentlichungen** enthält Zusammenfassungsinformationen zu allen Veröffentlichungen auf dem Verleger, die Sie im linken Bereich ausgewählt haben.  
  
## <a name="options"></a>Tastatur  
 Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren**: Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren** .  
  
-   **Anzuzeigende Spalten auswählen**: Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern**: Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen** .  
  
-   **Filter löschen**: Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 **Status**  
 Status der einzelnen Veröffentlichungen, der anhand des höchsten Prioritätsstatus der Abonnements bestimmt wird. Standardmäßig wird das Raster mit den Veröffentlichungsinformationen nach der **Status** -Spalte sortiert. In der folgenden Liste werden die möglichen Statuswerte und ihre Sortierreihenfolge aufgeführt (Fehler werden z. B. immer oben im Raster angezeigt):  
  
-   Fehler  
  
-   Leistung ist kritisch  
  
-   fehlerhafter Befehl wird wiederholt  
  
-   OK  
  
 Der Statuswert **Leistungskritisch** ist für Transaktionsabonnements und für Mergeabonnements relevant. Er kann nur angezeigt werden, wenn ein Schwellenwert festgelegt ist. Informationen zu Leistungsmessungen und zum Festlegen von Schwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md) und [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Veröffentlichung**  
 Der Name der jeweiligen Veröffentlichung im Format *PublicationDatabaseName: PublicationName*.  
  
 **Abonnements**  
 Die Anzahl der Abonnements pro Veröffentlichung.  
  
 **Wird synchronisiert**  
 Die Anzahl der Abonnements pro Veröffentlichung, die gerade synchronisiert werden:  
  
-   Bei Transaktionsreplikationen bedeutet "Wird synchronisiert", dass zwar der Verteilungs-Agent ausgeführt wird, aber nicht unbedingt Daten repliziert werden.  
  
-   Bei Mergereplikationen bedeutet "Wird synchronisiert", dass der Merge-Agent ausgeführt wird und gerade Daten repliziert werden.  
  
-   Bei Momentaufnahmereplikationen bedeutet "Wird synchronisiert", dass der Verteilungs-Agent ausgeführt wird und gerade Daten repliziert werden.  
  
 **Aktuelle Durchschnittsleistung** und **Die derzeit schlechteste Leistung**  
 Nur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Die Bewertung für die aktuelle Durchschnittsleistung und die Bewertung für die derzeit schlechteste Leistung gelten jeweils für alle Abonnements einer Veröffentlichung. Die Bewertungen basieren auf den neuesten Messungen des Replikationsmonitors und spiegeln nicht die Leistung eines Abonnements über einen längeren Zeitraum wider.  
  
 Bei Transaktionsreplikationen zeigt der Replikationsmonitor einen Wert nur für Veröffentlichungen an, für die Leistungsschwellenwerte definiert sind. Sind für eine Veröffentlichung keine Leistungsschwellenwerte definiert, wird in dieser Spalte **Nicht aktiviert**angezeigt. Bei Mergereplikationen zeigt der Replikationsmonitor einen Wert an, nachdem fünf Synchronisierungen mit jeweils mindestens 50 Änderungen über denselben Verbindungstyp (DFÜ oder LAN) stattgefunden haben. Falls weniger als fünf Synchronisierungen mit mindestens 50 Änderungen stattgefunden haben, oder wenn die letzte Synchronisierung nicht mindestens 50 Änderungen umfasst hat, ist diese Spalte leer.  
  
 Die folgenden Werte sind für die Leistungsbewertung möglich:  
  
-   Hervorragend  
  
-   Gut  
  
-   Durchschnittlich  
  
-   Schlecht  
  
-   Kritisch  
  
 Weitere Informationen zur Definition von Leistungsbewertungen und zum Festlegen von Leistungsschwellenwerten finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
