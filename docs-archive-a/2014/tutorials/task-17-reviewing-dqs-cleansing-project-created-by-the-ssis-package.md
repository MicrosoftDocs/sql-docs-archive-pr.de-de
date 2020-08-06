---
title: 'Aufgabe 17: Überprüfen des vom SSIS-Paket erstellten DQS-Bereinigungs Projekts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0876a0b727e810f8834fcf5445958bf9884a87f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694849"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Aufgabe 17: Überprüfung des vom SSIS-Paket erstellten DQS-Bereinigungsprojekts
  In dieser Aufgabe öffnen Sie das DQS-Projekt, das durch das SSIS-Paket in DQS-Client erstellt wurde, prüfen die Ergebnisse des Bereinigungsprozesses, führen optional eine interaktive Bereinigung aus und exportieren die Ergebnisse.  
  
1.  Starten Sie **Data Quality-Client**.  
  
2.  Klicken Sie im Bereich **Verwaltung** auf **Aktivitäts Überwachung** .  
  
3.  Sortieren Sie die Liste basierend auf der **Startzeit der Aktivität** , um den letzten Datensatz anzuzeigen.  
  
4.  Beachten Sie, dass der Name des Projekts im folgenden Format angezeigt wird: **cleanabandcurr. bereinigen Lieferant Data. GUID**.  
  
     ![Von SSIS-Paket erstelltes DQS-Bereinigungsprojekt](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "Von SSIS-Paket erstelltes DQS-Bereinigungsprojekt")  
  
5.  Beachten Sie, dass der Wert im Feld **ist aktiv** **ist.**  
  
6.  Klicken Sie im unteren Bereich auf die Registerkarte **Profiler** , um die Profiler-Statistik für die vom SSIS-Paket ausgeführte Bereinigungs Aktivität anzuzeigen.  
  
7.  Klicken Sie auf **Schließen** , um den **Verwaltungs** Bildschirm zu schließen.  
  
8.  Klicken Sie auf der Hauptseite von **DQS-Client**im Bereich **Data Quality-Projekte** auf **Data Quality-Projekt öffnen** .  
  
9. Wählen Sie in der Liste der Projekte das Projekt aus, das von der SSIS-DQS-Bereinigungskomponente erstellt wird. Der Name des Projekts sollte folgendes Format aufweisen: **cleanabandcurr. bereinigen Sie Supplier Data. GUID (in roter Farbe)**. Möglicherweise müssen Sie die Liste basierend auf der Spalte mit **dem Erstellungsdatum** sortieren und nach dem neuesten Datensatz suchen.  
  
10. Klicken Sie auf **Weiter**.  
  
11. Die Seite **Ergebnisse verwalten und anzeigen** sollte Ihnen aus der interaktiven Bereinigung vertraut sein, die Sie zuvor in diesem Lernprogramm durchgeführt haben.  
  
12. Überprüfen Sie die Bereinigungsergebnisse. Sie können auf der nächsten Seite auch interaktive Bereinigungen ausführen und Ergebnisse in eine Excel-Datei oder eine Datenbank exportieren.  
  
13. Klicken Sie auf **Weiter**. Auf dieser Seite **exportieren** können Sie Ergebnisse in eine Excel-Datei, eine CSV-Datei oder eine SQL-Datenbank exportieren.  
  
14. Klicken Sie auf **Fertig** stellen, um die Aktivität abzuschließen.  
  
15. Klicken Sie im Bereich **Verwaltung** auf der **DQS-Client**-Hauptseite auf **Aktivitäts Überwachung** .  
  
16. Beachten Sie, dass der Wert des Felds **IsActive** für das Projekt jetzt **beendet** ist.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Zusammenfassung](../../2014/tutorials/conclusion.md)  
  
  
