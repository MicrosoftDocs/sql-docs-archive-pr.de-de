---
title: Separates Speichern von Showplan XML-Ereignissen (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Showplan XML events
- saving Showplan XML events
- events [SQL Server], Showplan XML
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 240fb408bb3ed8585ecc915ba4829ac21285d241
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622037"
---
# <a name="save-showplan-xml-events-separately-sql-server-profiler"></a>Separates Speichern von Showplan XML-Ereignissen (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie **Showplan XML** -Ereignisse, die in Ablaufverfolgungen erfasst sind, mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]in separaten .SQLPlan-Dateien gespeichert werden können. Sie können die **Showplan XML** -Ereignisdateien in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]öffnen, sodass Sie den grafischen Ausführungsplan für die einzelnen Ereignisse betrachten können.  
  
### <a name="to-save-showplan-xml-events-separately"></a>So speichern Sie Showplan XML-Ereignisse separat  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung zu einer Instanz von SQL Server her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Dialogfeld **Ablaufverfolgungseigenschaften** im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Wählen Sie in der Liste **Vorlage verwenden** eine Ablaufverfolgungsvorlage als Basis für die Ablaufverfolgung aus, oder wählen Sie **Leer** aus, wenn Sie keine Vorlage verwenden möchten.  
  
4.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Aktivieren Sie das Kontrollkästchen**In Datei speichern** , um die Ablaufverfolgung in einer Datei aufzuzeichnen. Geben Sie einen Wert für **Maximale Dateigröße festlegen**an. Optional aktivieren Sie die Kontrollkästchen **Dateirollover aktivieren** und **Ablaufverfolgungsdaten von Serverprozessen** .  
  
    -   Aktivieren Sie das Kontrollkästchen**In Tabelle speichern** , um die Ablaufverfolgung in einer Datenbanktabelle aufzuzeichnen. Klicken Sie optional auf **Maximale Zeilen Anzahl festlegen**, und geben Sie einen Wert an.  
  
5.  Aktivieren Sie optional das Kontrollkästchen **Beendigungszeit für Ablaufverfolgung aktivieren** , und geben Sie das Datum und die Uhrzeit zum Beenden der Ablaufverfolgung an.  
  
6.  Klicken Sie auf die Registerkarte **Ereignisauswahl**.  
  
7.  Geben Sie im Dialogfeld **Ereignisse**die Ereigniskategorie **Leistung**, und aktivieren Sie dann das Kontrollkästchen **Showplan XML**. Wenn die **Performance** -Ereigniskategorie nicht verfügbar ist, aktivieren Sie zum Anzeigen dieser Ereigniskategorie das Kontrollkästchen **Alle Ereignisse anzeigen** .  
  
     Das Dialogfeld **Ereignisextraktionseinstellungen**wird dem Dialogfeld **Ablaufverfolgungseigenschaften**hinzugefügt.  
  
8.  Klicken Sie im Menü **Ereignisextraktionseinstellungen**auf **XML-Showplanereignisse separat speichern**.  
  
9. Geben Sie in das Dialogfeld **Speichern unter** den Namen der Datei ein, in die die **Showplan XML** -Ereignisse gespeichert werden sollen.  
  
10. Klicken Sie auf **Alle XML-Showplanbatches in einer einzelnen Datei** , wenn alle **Showplan XML** -Ereignisse in einer einzigen XML-Datei gespeichert werden sollen, bzw. auf **Jeder XML-Showplanbatch in einer eigenen Datei**, um so je eine neue XML-Datei für die einzelnen **Showplan XML** -Ereignisse anlegen zu lassen.  
  
11. Um die **Showplan XML** -Ereignisdatei in SQL Server Management Studio anzeigen zu lassen, zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie auf **Datei**. Navigieren Sie zu dem Verzeichnis, in dem Sie die **Showplan XML** -Ereignisdatei(en) gespeichert hatten, wählen Sie eine Datei aus, und öffnen Sie diese. **Showplan XML** -Ereignisdateien besitzen die Dateierweiterung .SQLPlan.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysieren von Abfragen mit SHOWPLAN-Ergebnissen in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  
