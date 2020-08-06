---
title: Anzeigen von Optimierungsempfehlungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d938767d874edd8f14bdaa91c0cf52023478f53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719222"
---
# <a name="viewing-tuning-recommendations"></a>Anzeigen von Empfehlungen für die Optimierung
   In dieser Aufgabe wird die Optimierungssitzung verwendet, die Sie im Abschnitt [Optimieren einer Arbeitsauslastung](lesson-1-1-tuning-a-workload.md) angelegt haben. Nachdem Sie die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Datenbank mit dem Skript MyScript. SQL optimiert haben [!INCLUDE[tsql](../../includes/tsql-md.md)] , zeigt der-Optimierungs Ratgeber die [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ergebnisse auf der Registerkarte **Empfehlungen** an. Mit der folgenden Aufgabe wird die Registerkarte **Empfehlungen** auf der [!INCLUDE[ssDE](../../includes/ssde-md.md)] grafischen Benutzeroberfläche (GUI) des-Optimierungs Ratgebers eingeführt, und Sie werden dazu geführt, welche Informationen über die Ergebnisse der Optimierungs Sitzung bereitgestellt werden.  
  
### <a name="view-tuning-recommendations"></a>Optimierungsempfehlungen anzeigen  
  
1.  Starten Sie den [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber. Weitere Informationen finden Sie unter [Starten des Datenbankoptimierungsratgebers](../../relational-databases/performance/database-engine-tuning-advisor.md). Stellen Sie sicher, dass Sie eine Verbindung mit derselben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz herstellen, die Sie in der Übung [Optimieren einer Arbeitsauslastung](lesson-1-1-tuning-a-workload.md)verwendet haben.  
  
2.  Doppelklicken Sie im Bereich **Sitzungsmonitor** auf **MySession** . [!INCLUDE[ssDE](../../includes/ssde-md.md)]Der-Optimierungs Ratgeber lädt die Sitzungsinformationen aus Ihrer vorherigen Optimierungs Sitzung und zeigt die Registerkarte **Empfehlungen** an. Beachten Sie, dass der-Optimierungs [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ratgeber keine **Partitions Empfehlungen** gegeben hat, da Sie alle Standardeinstellungen für die Optimierungs Option akzeptiert haben und auf der Registerkarte Optimierungs **Optionen** **keine Partitionierung** ausgewählt  
  
3.  Verwenden Sie auf der Registerkarte **Empfehlungen** die Bildlaufleiste unten auf der Seite im Registerformat, um alle Spalten zu **Indexempfehlungen** anzuzeigen. Jede Zeile steht für ein Datenbankobjekt (Indizes oder indizierte Sichten), für das der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber die Empfehlung abgibt, es zu löschen oder anzulegen. Führen Sie einen Bildlauf zur Spalte ganz rechts durch, und klicken Sie auf **Definition**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Der Optimierungsratgeber zeigt das Fenster **SQL-Skriptvorschau** an, in dem das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript angezeigt werden kann, das das Datenbankobjekt in dieser Zeile anlegt oder löscht. Klicken Sie auf **Schließen** , um das Vorschaufenster zu schließen.  
  
     Wenn Sie Probleme haben, eine **Definition** zu finden, die einen Link enthält, klicken Sie am unteren Rand der Seite im Registerformat auf das Kontrollkästchen **Vorhandene Objekte anzeigen** , um es zu deaktivieren. Damit wird die Anzahl dargestellter Zeilen reduziert. Wenn Sie das Kontrollkästchen deaktivieren, zeigt der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber nur die Objekte an, für die eine Empfehlung generiert wurde. Aktivieren Sie das Kontrollkästchen **Vorhandene Objekte anzeigen** , um alle Datenbankobjekte anzuzeigen, die derzeit in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank vorhanden sind. Zum Anzeigen aller Objekte verwenden Sie die Bildlaufleiste rechts auf der Seite im Registerformat.  
  
4.  Klicken Sie mit der rechten Maustaste auf das Raster im Bereich **Indexempfehlungen** . Im daraufhin angezeigten Kontextmenü können Sie Empfehlungen auswählen oder deren Auswahl aufheben. Außerdem können Sie die Schriftart des Rastertexts ändern.  
  
5.  Klicken Sie im Menü **Aktionen** auf **Empfehlungen speichern** , um alle Empfehlungen in einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript zu speichern. Nennen Sie das Skript `MySessionRecommendations.sql`.  
  
     Öffnen Sie das Skript MySessionRecommendations.sql im Abfrage-Editor von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um es anzuzeigen. Sie könnten jetzt die Empfehlungen auf die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] anwenden, indem Sie das Skript im Abfrage-Editor ausführen, aber tun Sie das jetzt nicht. Schließen Sie das Skript im Abfrage-Editor, ohne es auszuführen.  
  
     Optional können Sie die Empfehlungen auch anwenden, indem Sie im Menü **Aktionen** des **-Optimierungsratgebers auf** Empfehlungen anwenden [!INCLUDE[ssDE](../../includes/ssde-md.md)] klicken. Wenden Sie jedoch die Empfehlungen an dieser Stelle in der Übung nicht an.  
  
6.  Wenn auf der Registerkarte **Empfehlungen** mehrere Empfehlungen vorhanden sind, deaktivieren Sie einige der Zeilen, in denen Datenbankobjekte im Raster **Indexempfehlungen** aufgelistet sind.  
  
7.  Klicken Sie im Menü **Aktionen** auf **Empfehlungen bewerten**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Der Optimierungsratgeber erstellt eine neue Optimierungssitzung, in der Sie eine Untergruppe der ursprünglichen Empfehlungen aus MySession auswerten können.  
  
8.  Geben `EvaluateMySession` Sie für den neuen **Sitzungs Namen**ein, und klicken Sie auf der Symbolleiste auf die Schaltfläche **Analyse starten** . Zum Anzeigen der Ergebnisse dieser neuen Optimierungssitzung können Sie die Schritte 2 und 3 wiederholen.  
  
## <a name="summary"></a>Zusammenfassung  
 Sie haben den Inhalt der Registerkarte **Empfehlungen** für die Optimierungssitzung MySession angezeigt und eine Untergruppe der Empfehlungen in der neuen Optimierungssitzung EvaluateMySession ausgewertet.  
  
 Das Auswerten einer Untergruppe von Optimierungsempfehlungen kann erforderlich sein, wenn Sie feststellen, dass Sie nach dem Ausführen einer Sitzung die Optimierungsoptionen noch ändern müssen. Beispiel: Sie legen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Optimierungsratgeber in den Optimierungsoptionen für eine Sitzung fest, dass indizierte Sichten berücksichtigt werden sollen. Nachdem die Empfehlung erstellt wurde, beschließen Sie jedoch, indizierte Sichten nicht zu berücksichtigen. Sie können anschließend im Menü **Aktionen** den **-Optimierungsratgeber mithilfe der Option** Empfehlungen bewerten [!INCLUDE[ssDE](../../includes/ssde-md.md)] anweisen, die Sitzung neu zu bewerten, ohne dabei indizierte Sichten zu berücksichtigen. Wenn Sie die Option **Empfehlungen auswerten** verwenden, werden für die zweite Optimierungssitzung die vorher generierten Empfehlungen hypothetisch auf den aktuellen physischen Entwurf angewendet, um den physischen Entwurf für die zweite Optimierungssitzung zu erstellen.  
  
 Auf der Registerkarte **Berichte** können Sie weitere Ergebnisse der Optimierung anzeigen. Darauf wird in der nächsten Aufgabe dieser Lektion näher eingegangen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Anzeigen von Optimierungsberichten](lesson-1-3-viewing-tuning-reports.md)  
  
  
