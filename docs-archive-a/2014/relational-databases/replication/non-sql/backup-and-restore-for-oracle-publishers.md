---
title: Sichern und Wiederherstellen bei Oracle-Verlegern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6b994c34e4f4bebc010fe6d71bbd43f6e557cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608556"
---
# <a name="backup-and-restore-for-oracle-publishers"></a>Sichern und Wiederherstellen bei Oracle-Verlegern
  Beachten Sie beim Sichern und Wiederherstellen die folgenden Hinweise:  
  
-   Stellen Sie sicher, dass der Protokolllese-Agent nicht ausgeführt wird und dass es beim Sichern des Verlegers zu keiner anderen Datenbankaktivität in den veröffentlichten Tabellen kommt.  
  
-   Sichern Sie den Verleger und den Verteiler gleichzeitig.  
  
-   Wenn der Verleger oder der Verteiler wiederhergestellt wird, initialisieren Sie alle Abonnements erneut.  
  
-   Zum Wiederherstellen eines Abonnenten aus einer Sicherung (ohne dabei die Abonnements erneut initialisieren zu müssen) müssen die Transaktionen, die nach der letzten vollständigen Sicherung der Abonnementdatenbank an die Verteilungsdatenbank geliefert wurden, noch verfügbar sein. Wie lange Transaktionen verfügbar sind, hängt von den Beibehaltungsdauereinstellungen für die Verteilung ab. Informationen finden Sie unter [Abonnementablauf und -deaktivierung](../subscription-expiration-and-deactivation.md).  
  
-   Wenn der Verleger oder der Verteiler nach einer Datenbankwiederherstellung nicht mehr synchronisiert ist, protokollieren die Replikations-Agents Fehlermeldungen. In diesem Fall müssen Sie alle relevanten Veröffentlichungen und Abonnements löschen und erneut erstellen:  
  
    1.  Erstellen Sie ein Skript für die Definition der Veröffentlichungen und Abonnements. Weitere Informationen finden Sie unter [Scripting Replication](../scripting-replication.md).  
  
         Wenn sich die Definition der Veröffentlichungen zwischen den Statusversionen des Verlegers und des Verteilers geändert hat, müssen Sie die Skripts entsprechend ändern.  
  
    2.  Löschen Sie die Veröffentlichungen und Abonnements.  
  
    3.  Führen Sie die in Schritt 1 erstellten Skripts aus.  
  
     Wenn der Verleger gelöscht und erneut konfiguriert werden muss, löschen Sie das öffentliche **MSSQLSERVERDISTRIBUTOR** -Synonym und den konfigurierten Oracle-Replikationsbenutzer mit der **CASCADE** -Option, um alle Replikationsobjekte vom Oracle-Verleger zu entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von replizierten Datenbanken](../administration/back-up-and-restore-replicated-databases.md)   
 [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md)   
 [Veröffentlichungen mit Oracle (Übersicht)](oracle-publishing-overview.md)  
  
  
