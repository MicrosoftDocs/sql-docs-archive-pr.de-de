---
title: Speichern von Deadlockdiagrammen (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], saving deadlock graphs
- graphs [SQL Server]
- saving deadlock graphs
ms.assetid: bf1fc906-abd6-4a89-842e-da0d66b2defe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cdd0bd808ba4b934e5b2d91c9079909acf6e3997
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619774"
---
# <a name="save-deadlock-graphs-sql-server-profiler"></a>Speichern von Deadlockdiagrammen (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie ein Deadlock Graph mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]gespeichert wird. Deadlock Graphs werden als XML-Dateien gespeichert.  
  
### <a name="to-save-deadlock-graph-events-separately"></a>So speichern Sie Deadlock Graph-Ereignisse separat  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung zu einer Instanz von SQL Server her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Dialogfeld „Ablaufverfolgungseigenschaften“ im Feld**Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Wählen Sie in der Liste **Vorlage verwenden** eine Ablaufverfolgungsvorlage als Basis für die Ablaufverfolgung aus, oder wählen Sie **Leer** aus, wenn Sie keine Vorlage verwenden möchten.  
  
4.  Führen Sie eines der folgenden Verfahren aus:  
  
    -   Aktivieren Sie das Kontrollkästchen**In Datei speichern** , um die Ablaufverfolgung in einer Datei aufzuzeichnen. Geben Sie einen Wert für **Maximale Dateigröße festlegen**an.  
  
         Aktivieren Sie optional die Kontrollkästchen **Dateirollover aktivieren** und **Ablaufverfolgungsdaten von Serverprozessen**.  
  
    -   Aktivieren Sie das Kontrollkästchen **In Tabelle speichern** , um die Ablaufverfolgung in einer Datenbanktabelle aufzuzeichnen.  
  
         Klicken Sie optional auf **Maximale Zeilenzahl festlegen**, und geben Sie einen Wert an.  
  
5.  Aktivieren Sie optional das Kontrollkästchen **Beendigungszeit für Ablaufverfolgung aktivieren** , und geben Sie das Datum und die Uhrzeit zum Beenden der Ablaufverfolgung an.  
  
6.  Klicken Sie auf die Registerkarte **Ereignisauswahl**.  
  
7.  Erweitern Sie in der Datenspalte **Ereignisse**die Ereigniskategorie **Sperren**, und aktivieren Sie das Kontrollkästchen **Deadlock Graph**. Falls die Ereigniskategorie „Sperren“ nicht verfügbar ist, aktivieren Sie **Alle Ereignisse anzeigen** , damit sie angezeigt wird.  
  
     Das Dialogfeld **Ereignisextraktionseinstellungen**wird dem Dialogfeld **Ablaufverfolgungseigenschaften**hinzugefügt.  
  
8.  Aktivieren Sie auf der Registerkarte **Ereignisextraktionseinstellungen**das Kontrollkästchen **Deadlock-XML-Ereignisse separat speichern**.  
  
9. Geben Sie im Dialogfeld **Speichern unter** den Namen der Datei ein, in der die Deadlock Graph-Ereignisse gespeichert werden sollen.  
  
10. Klicken Sie auf **Alle Deadlock-XML-Batches in einer einzelnen Datei** , um alle Deadlock Graph-Ereignisse in einer einzigen XML-Datei zu speichern, oder klicken Sie auf **Jeder Deadlock-XML-Batch in einer eigenen Datei**, um für jedes Deadlockdiagramm eine neue XML-Datei zu erstellen.  
  
 Nach dem Speichern der Deadlockdatei können Sie sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]öffnen. Weitere Informationen finden Sie unter [Öffnen, anzeigen und Drucken einer Deadlockdatei &#40;SQL Server Management Studio&#41;](open-view-and-print-a-deadlock-file-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysieren von Deadlocks mit SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)  
  
  
