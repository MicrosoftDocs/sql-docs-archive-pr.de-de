---
title: Starten der Daten Verschiebung auf einer sekundären AlwaysOn-Datenbank (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ce4f80b456244cd6e024377383abe75e002057a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724970"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a>Starten der Datenverschiebung auf einer sekundären AlwaysOn-Datenbank (SQL Server)
  Dieses Thema enthält Informationen zum Starten der Datensynchronisierung, nachdem Sie einer AlwaysOn-Verfügbarkeitsgruppe eine Datenbank hinzugefügt haben. Für jedes neue primäre Replikat müssen sekundäre Datenbanken auf den Serverinstanzen vorbereitet werden, die die sekundären Replikate hosten. Dann muss jede dieser sekundären Datenbanken manuell mit der Verfügbarkeitsgruppe verknüpft werden.  
  
> [!NOTE]  
>  Wenn die Dateipfade auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für eine Verfügbarkeitsgruppe hostet, identisch sind, kann der [Assistent für neue Verfügbarkeitsgruppen](use-the-availability-group-wizard-sql-server-management-studio.md), der [Assistent zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)oder der [Assistent zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen](availability-group-add-database-to-group-wizard.md) unter Umständen die Datensynchronisierung automatisch starten.  
  
 Um die Datensynchronisierung manuell zu starten, müssen Sie wiederum eine Verbindung mit jeder Serverinstanz herstellen, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet, und die folgenden Schritte ausführen:  
  
1.  Stellen Sie aktuelle Sicherungen jeder primären Datenbank und ihres Transaktionsprotokolls (mithilfe von RESTORE WITH NORECOVERY) wieder her. Sie können einen der folgenden alternativen Ansätze verwenden:  
  
    -   Stellen Sie manuell mit RESTORE WITH NORECOVERY eine aktuelle Datenbanksicherung der primären Datenbank wieder her, und stellen Sie dann jede nachfolgende Protokollsicherung mit RESTORE WITH NORECOVERY wieder her. Führen Sie diese Wiederherstellungssequenz auf jeder Serverinstanz aus, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet.  
  
         **Weitere Informationen finden Sie unter:**  
  
         [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   Wenn Sie einer Verfügbarkeitsgruppe eine oder mehrere primäre Datenbanken für den Protokollversand hinzufügen, können Sie möglicherweise eine oder mehrere der entsprechenden sekundären Datenbanken für den Protokollversand zu AlwaysOn-Verfügbarkeitsgruppen migrieren. Das Migrieren einer sekundären Datenbank für den Protokollversand erfordert, dass sie den gleichen Datenbanknamen wie die primäre Datenbank verwendet und dass sie sich auf einer Serverinstanz befindet, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet. Weiterhin muss die Verfügbarkeitsgruppe so konfiguriert sein, dass das primäre Replikat für Sicherungen bevorzugt wird und ein Kandidat zum Ausführen von Sicherungen ist (das heißt, eine Sicherungspriorität, die >0 hat). Nachdem der Sicherungsauftrag auf der primären Datenbank ausgeführt wurde, müssen Sie den Sicherungsauftrag deaktivieren, und sobald der Wiederherstellungsauftrag auf einer angegebenen sekundären Datenbank ausgeführt wurde, müssen Sie den Wiederherstellungsauftrag deaktivieren.  
  
        > [!NOTE]  
        >  Nachdem Sie alle sekundären Datenbanken für die Verfügbarkeitsgruppe erstellt haben, sofern Sie Sicherungen auf sekundären Replikaten ausführen möchten, müssen Sie die Voreinstellung zur automatisierten Sicherung der Verfügbarkeitsgruppe neu konfigurieren.  
  
         **Weitere Informationen finden Sie unter:**  
  
         [Voraussetzungen für das Migrieren vom Protokoll Versand zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  Verknüpfen Sie jede neu vorbereitete sekundäre Datenbank sofort mit der Verfügbarkeitsgruppe.  
  
     **Weitere Informationen finden Sie unter:**  
  
     [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> Verwandte Aufgaben  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
