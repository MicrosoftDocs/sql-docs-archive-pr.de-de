---
title: 'Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7b879b2bea4afd58a48cdfc6f0890353fe6758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609309"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a>Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell
  In dieser Aufgabe verwenden Sie den Konvertierungs-Assistenten von Integration Services-Projekt, um das Projekt in das Projektbereitstellungsmodell zu konvertieren.  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a>Konvertieren des Projekts in das Projektbereitstellungsmodell  
  
1.  Klicken Sie im Menü „Projekt“ auf „Paketbereitstellungsmodell konvertieren“.  
  
2.  Überprüfen Sie die Schritte der Konvertierungs-Assistent von Integration Services-Einführungsseite und klicken Sie auf Weiter.  
  
3.  Klicken Sie auf der Seite zur Paketauswahl in die Paketliste, deaktivieren Sie alle Kontrollkästchen außer Lektion 6.dtsx, und klicken Sie dann auf Weiter.  
  
4.  Klicken Sie auf der Projekteigenschaftenseite auf Weiter.  
  
5.  Klicken Sie auf der Seite Task 'Paket ausführen' aktualisieren auf Weiter.  
  
6.  Stellen Sie auf auf der Konfigurationsauswahlseite sicher, dass das Paket Lektion 6.dtsx in der Konfigurationsliste ausgewählt ist, und klicken Sie auf Weiter.  
  
7.  Stellen Sie auf der Seite zum Erstellen von Parametern sicher, dass das Paket Lektion 6.dtsx ausgewählt ist, und der Bereich in der Konfigurationseigenschaftsliste auf Paket festgelegt ist, und klicken Sie dann auf Weiter.  
  
8.  Stellen Sie auf der Seite zur Konfiguration der Parameter sicher, dass die Werte für den Namen und den Wert demselben Namen und Wert entsprechen, den Sie in der Lektion 5 für den Variablen- und Konfigurationswert angegeben haben, und klicken Sie dann auf Weiter.  
  
9. Beachten Sie auf der Überprüfungsseite im Zusammenfassungsbereich, dass der Assistent die Informationen aus der Konfigurationsdatei verwendet hat, um die zu konvertierenden Eigenschaften festzulegen.  
  
10. Klicken Sie auf Konvertieren.  
  
     Beim Abschluss der Konvertierung einer Nachricht wird eine Warnung angezeigt, das die Änderungen nicht gespeichert werden, bis das Projekt in Visual Studio gespeichert wird. Klicken Sie im Warnungsdialogfeld auf OK.  
  
11. Klicken Sie im Konvertierungs-Assistenten des Integration Services-Projekts auf Schließen.  
  
12. Klicken Sie in SQL Server Data Tools auf das Menü "Datei", klicken Sie auf "Speichern", um das konvertierte Paket zu speichern.  
  
13. Klicken Sie auf der Registerkarte "Parameter", und stellen Sie sicher, dass das Paket jetzt einen Parameter für VarFolderName enthält und der Wert denselben Pfad für den Ordner der neuen Beispieldaten aus der Lektion 5-Konfigurationsdatei angegeben ist.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 3: Testen des Pakets aus Lektion 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
