---
title: Anzeigen und Auflösen von Daten Konflikten für Mergeveröffentlichungen (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616473"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a>Anzeigen und Lösen von Datenkonflikten für Mergeveröffentlichungen (SQL Server Management Studio)
  Konflikte bei der Mergereplikation werden anhand des für den jeweiligen Artikel angegebenen Konfliktlösers gelöst. Standardmäßig werden Konflikte ohne Benutzereingriff gelöst. Konflikte können jedoch im Replikationskonflikt-Viewer von [!INCLUDE[msCoName](../../includes/msconame-md.md)] angezeigt und das Ergebnis der Konfliktlösung kann geändert werden.  
  
 Die Konfliktdaten sind im Replikationskonflikt-Viewer für den Zeitraum verfügbar, der als Beibehaltungsdauer der Konflikte (bei einer Standardeinstellung von 14 Tagen) angegeben wurde. Zum Festlegen der Beibehaltungsdauer der Konflikte haben Sie folgende Möglichkeiten:  
  
-   Geben Sie einen Beibehaltungs Wert für den **@conflict_retention** Parameter [sp_addmergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)an.  
  
-   Geben Sie den Wert **conflict_retention** für den **@property** -Parameter und einen Beibehaltungs Wert für den- **@value** Parameter [sp_changemergepublication &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)an.  
  
 Standardmäßig werden Konfliktinformationen an den folgenden Orten gespeichert:  
  
-   Auf dem Verleger und Abonnenten, wenn die Veröffentlichung mindestens einen Kompatibilitätsgrad von 90RTM aufweist.  
  
-   Auf dem Verleger, wenn die Veröffentlichung einen geringeren Kompatibilitätsgrad als 80RTM aufweist.  
  
-   Auf dem Verleger, wenn auf den Abonnenten [!INCLUDE[ssEW](../../includes/ssew-md.md)]ausgeführt wird. Konfliktdaten dürfen nicht auf Abonnenten mit [!INCLUDE[ssEW](../../includes/ssew-md.md)] gespeichert werden.  
  
 Das Speichern von Konfliktinformationen wird von der **conflict_logging** -Veröffentlichungseigenschaft gesteuert. Weitere Informationen finden Sie unter [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) und [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).  
  
 Konflikte können während der Synchronisierung auch mit dem interaktiven [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Replikationskonfliktlöser gelöst werden. Der interaktive Konfliktlöser ist über die Synchronisierungsverwaltung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows verfügbar. Weitere Informationen finden Sie unter [Synchronisieren eines Abonnements mithilfe der Synchronisierungsverwaltung von Windows &#40;Synchronisierungsverwaltung von Windows&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a>So zeigen Sie Konflikte von Mergeveröffentlichungen an und lösen Sie die Konflikte  
  
1.  Stellen Sie in eine Verbindung mit dem Verleger (oder ggf. dem Abonnenten) her [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und erweitern Sie dann den Server Knoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie die Konflikte anzeigen möchten, und klicken Sie dann auf **Konflikte anzeigen**.  
  
    > [!NOTE]  
    >  Wenn für die **conflict_logging** -Eigenschaft der Wert **'subscriber'** angegeben wurde, ist die Menüoption **Konflikte anzeigen** nicht verfügbar. Starten Sie zum Anzeigen von Konflikten ConflictViewer.exe von der Eingabeaufforderung aus. ConflictViewer.exe befindet sich standardmäßig im folgenden Verzeichnis: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Eine Liste der gültigen Startparameter erhalten Sie, wenn Sie ConflictViewer.exe -? ausführen.  
  
4.  Wählen Sie im Dialogfeld **Konflikttabelle auswählen** eine Datenbank, eine Veröffentlichung und eine Tabelle aus, für die Sie die Konflikte anzeigen möchten.  
  
5.  Im Replikationskonflikt-Viewer können Sie folgende Aktionen ausführen:  
  
    -   Filtern Sie Zeilen mit den Schaltflächen rechts vom oberen Raster.  
  
    -   Wählen Sie eine Zeile im oberen Raster aus, um Informationen zur Zeile im unteren Raster anzuzeigen.  
  
    -   Wählen Sie eine oder mehrere Zeilen im oberen Raster aus, und klicken Sie auf **Entfernen**, was dem Klicken auf die Schaltfläche **Gewinner absenden** entspricht (ohne Änderungen an den Daten vorzunehmen).  
  
    -   Klicken Sie auf die Schaltfläche mit den Eigenschaften (**...**), um weitere Informationen zu einer in einem Konflikt beteiligten Spalte anzuzeigen.  
  
    -   Bearbeiten Sie Daten in den Spalten **Konfliktgewinner** oder **Konfliktverlierer** , bevor Sie die Daten absenden (bei einer grauen Spalte sind die Daten schreibgeschützt).  
  
    -   Klicken Sie auf **Gewinner absenden** , um die als Gewinner des Konflikts ausgewiesene Spalte zu akzeptieren.  
  
    -   Klicken Sie auf **Verlierer absenden** , um die Konfliktlösung zu überschreiben und den als Verlierer des Konflikts ausgewiesenen Wert an alle Knoten der Topologie zu senden.  
  
    -   Aktivieren Sie **Details dieses Konflikts protokollieren** , um Konfliktdaten in einer Datei zu protokollieren. Um einen Speicherort für die Datei anzugeben, zeigen Sie auf das Menü **Ansicht** , und klicken Sie dann auf **Optionen**. Geben Sie einen Wert ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten (**...**), und wechseln Sie in das entsprechende Verzeichnis. Klicken Sie auf **OK** , um das Dialogfeld **Optionen** zu beenden.  
  
6.  Schließen Sie den Replikationskonflikt-Viewer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Angeben eines Mergeartikelkonfliktlösers](publish/specify-a-merge-article-resolver.md)  
  
  
