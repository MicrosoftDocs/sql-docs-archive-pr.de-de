---
title: Konfigurieren von Schweregraden für DQS-Protokolldateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 46fb9de1fbe1e3e59b20bb2ac7afeebe19ba2da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696090"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a>Konfigurieren von Schweregraden für DQS-Protokolldateien
  In diesem Thema wird beschrieben, wie Schweregrade für verschiedene Aktivitäten und Module in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) mit [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]konfiguriert werden. Schweregrade definieren die Intensität von Ereignissen, die in DQS auftreten. DQS-Ereignisse verfügen über die folgenden Schweregrade, angefangen mit dem höchsten Schweregrad:  
  
-   **Schwerwiegend**: Kritische Laufzeitfehler, die schwerwiegende/unerwartete Ergebnisse verursachen können.  
  
-   **Fehler**: Andere Laufzeitfehler.  
  
-   **Warnen**: Warnung vor Ereignissen, die zu einem Fehler führen können.  
  
-   **Info**: Informationen zu allgemeinen Ereignissen, die weder ein Fehler noch eine Warnung sind. Beispiel: Ein DQS-Prozess wurde gestartet.  
  
-   **Debuggen**: Detaillierte (ausführliche) Informationen zum Ereignis.  
  
 Indem Sie Schweregrade für verschiedene DQS-Aktivitäten und -Module konfigurieren, filtern Sie die Informationen, die protokolliert und in die DQS-Protokolldatei für die entsprechende DQS-Aktivität oder das entsprechende DQS-Modul geschrieben werden sollen. Wenn Sie z. B. den Schweregrad einer DQS-Aktivität auf **Warnen**festlegen, werden nur Warnungen und Meldungen mit einem höheren Schweregrad ("Fehler" und "Schwerwiegend") der DQS-Aktivität zugeordnet und protokolliert.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die dqs_administrator-Rolle in der DQS_MAIN-Datenbank verfügen, um die Einstellungen für Protokollschweregrade zu konfigurieren.  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a>Konfigurieren von Schweregraden auf Aktivitäts Ebene  
 Sie können die Einstellungen für Protokollschweregrade für die folgenden Aktivitäten in DQS konfigurieren: Domänenverwaltung, Wissensermittlung, Abgleichsrichtlinien, Datenbereinigung, Datenabgleich und Verweisdatendienste. Gehen Sie hierzu wie folgt vor:  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Konfiguration**.  
  
3.  Klicken Sie anschließend auf die Registerkarte **Protokoll Einstellungen** . Die folgenden DQS-Aktivitäten werden aufgelistet, für die Sie einen Schweregrad auswählen können: **Domänen Verwaltung**, **Wissens**Ermittlung, Bereinigungs **Projekt (ex. RDS)**, abgleichsrichtlinie und abgleichsprojekt und **RDS**. **Matching Policy and Matching Project**  
  
4.  Wählen Sie für eine DQS-Aktivität den Schweregrad für die Protokollierung aus. Die folgenden Optionen stehen zur Auswahl: **Schwerwiegend**, **Fehler**, **Warnen**, **Info**und **Debuggen**. Wenn z. B. nur schwerwiegende Meldungen in die DQS-Protokolldateien für die Wissensermittlungsaktivität geschrieben werden sollen, wählen Sie für die Aktivität **Wissensermittlung** in der Dropdownliste die Option **Schwerwiegend** aus.  
  
    > [!NOTE]  
    >  Standardmäßig ist **Fehler** für jede Aktivität ausgewählt. Diese Einstellung bedeutet, dass für jede Aktivität standardmäßig Fehler und schwerwiegende Meldungen in die DQS-Protokolldateien geschrieben werden.  
  
5.  Klicken Sie auf **Schließen**.  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a>Konfigurieren von Schweregraden auf Modulebene (erweitert)  
 Im Abschnitt **Erweitert** auf der Registerkarte **Protokolleinstellungen** können Sie die Einstellungen für Protokollschweregrade auf Modulebene konfigurieren. Module sind DQS-Systemassemblys, die verschiedene Funktionen innerhalb einer Funktion in DQS implementieren. Die Domänenverwaltungsaktivität enthält z. B. verschiedene Funktionen, wie z. B. das Definieren von Domänenregeln, Regelbedingungen, domänenübergreifenden Regeln für Verbunddomänen usw.  
  
 In einigen Fällen ist die Granularitätsebene auf Aktivitätsebene nicht ausreichend. Angenommen, Sie möchten ein Problem untersuchen, das in einem bestimmten Modul innerhalb einer Aktivität auftritt. In dem Fall ist eine Option hilfreich, mit der Protokollschweregrade auf Modulebene konfiguriert werden können, um das Problem zu isolieren und genauer nachzuverfolgen.  
  
 Die auf Aktivitätsebene festgelegte Einstellung für den Protokollschweregrad bestimmt die Einstellung für den Protokollschweregrad aller Module, aus denen sich die Aktivität zusammensetzt. Wenn jedoch ein Konflikt zwischen den Einstellungen für den Protokollschweregrad auf Aktivitäts- und Modulebene besteht, werden die Schweregradeinstellungen auf Modulebene verwendet.  
  
> [!NOTE]
>  -   Das Modul **Microsoft.Ssdqs.Core.Startup** ist im Bereich **Erweitert** standardmäßig mit dem Schweregrad **Info**vorkonfiguriert. Diese Einstellung wurde gewählt, um die Protokollierung von Ereignissen mit dem Schweregrad Info und höher (Warnen, Fehler und Schwerwiegend) zu ermöglichen, die mit dem Starten und Beenden von DQS-Diensten in Verbindung stehen.  
> -   Sie sollten Protokollschweregrade nur auf Modulebene konfigurieren, wenn Sie über fortgeschrittene Kenntnisse zu DQS verfügen und mit DQS-Systemassemblys vertraut sind.  
  
 So konfigurieren Sie Schweregrade auf Modulebene:  
  
1.  Klicken Sie auf der Registerkarte **Protokolleinstellungen** auf den Pfeil nach unten neben **Erweitert** , um den Bereich anzuzeigen.  
  
2.  Wählen Sie im angezeigten Raster aus der Dropdownliste in der Spalte **Modul** einen Modulnamen aus.  
  
3.  Wählen Sie als Nächstes aus der Dropdownliste in der Spalte **Schweregrad** einen Schweregrad für das Modul aus. Die folgenden Optionen stehen zur Auswahl: **Schwerwiegend**, **Fehler**, **Warnen**, **Info**und **Debuggen**.  
  
     Sie können z. B. in der Domänenverwaltungsaktivität für die Funktionalitäten der Domänenregeldefinition eine Granularitätsebene festlegen, die sich von der Einstellung für die Domänenverwaltungsaktivität unterscheidet, indem Sie das Modul **Microsoft.Ssdqs.DomainRules.Define** auswählen und einen anderen Protokollschweregrad auswählen. Dementsprechend können Sie eine andere Granularitätsebene für die Funktionalität der domänenübergreifenden Regel festlegen, indem Sie das Modul **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** auswählen und einen anderen Protokollschweregrad auswählen.  
  
4.  Wiederholen Sie ggf. Schritt 2 und 3 für die anderen Module. Sie können außerdem Zeilen im Raster hinzufügen oder löschen, indem Sie auf das Symbol **Modul hinzufügen** bzw. **Modul entfernen** klicken.  
  
5.  Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der erweiterten Einstellungen für DQS-Protokolldateien](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
