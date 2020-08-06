---
title: Neue Peerinitialisierung (Peer-zu-Peer-Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.init.f1
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26658fdfbcf0d3d3a88bedbace4102cda6cee9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620284"
---
# <a name="new-peer-initialization-peer-to-peer-replication"></a>Neue Peerinitialisierung (Peer-zu-Peer-Replikation)
  Auf der Seite **Neue Peerinitialisierung** können Sie angeben, wie Peerdatenbanken initialisiert wurden. (Peers müssen initialisiert werden, bevor Sie diesen Assistenten ausführen.) Peers werden manuell oder mithilfe der Funktionalität **initialisieren with Backup** initialisiert, die von der Transaktions Replikation bereitgestellt wird. (Die Peer-zu-Peer-Transaktions Replikation unterstützt die Initialisierung von Peers mithilfe einer Momentaufnahme nicht.) Wenn verschiedene Peers mithilfe unterschiedlicher Methoden initialisiert werden müssen, müssen Sie die Peers separat hinzufügen, indem Sie den Assistenten mehrmals ausführen.  
  
## <a name="options"></a>Tastatur  
 **Geben Sie an, wie die neuen Peerdatenbanken initialisiert wurden**  
 Das Schema und die Daten aller veröffentlichten Objekte müssen für jeden Peer vorliegen. Wählen Sie eine der folgenden Optionen aus:  
  
-   Wählen Sie die erste Option aus, wenn Sie das Schema für veröffentlichte Objekte manuell erstellt haben oder eine Sicherung wiederhergestellt haben und seit der Sicherung an der Veröffentlichungsdatenbank keine Änderungen vorgenommen wurden. Wenn Sie das Schema manuell erstellt haben, müssen Sie sicherstellen, dass alle erforderlichen Daten für die einzelnen Peers vorliegen. Diese Option entspricht dem Wert **replication support only** für die **sync_type**-Abonnementeigenschaft.  
  
-   Wählen Sie die zweite Option aus, wenn Sie eine Sicherung wiederhergestellt haben und seit der Sicherung an der ersten Veröffentlichungsdatenbank Änderungen vorgenommen wurden. Die Replikation muss nun Änderungen übermitteln, die an der ersten Veröffentlichungsdatenbank vorgenommen wurden, und die nicht in der Sicherung enthalten sind. Diese Option entspricht dem Wert **initialize with backup** für die **sync_type**-Abonnementeigenschaft.  
  
     Wenn eine Veröffentlichung für die Peer-zu-Peer-Replikation aktiviert ist, wird die Veröffentlichungseigenschaft **allow_initialize_from_backup** festgelegt. Die Replikation beginnt sofort mit der Nachverfolgung von Änderungen in der ersten Veröffentlichungsdatenbank. Daher können diese Änderungen an eine wiederhergestellte Datenbank für einen oder mehrere Peers übermittelt werden, wenn die Option **initialize with backup** ausgewählt ist. Klicken Sie auf die Schaltfläche **Durchsuchen** , um nach der verwendeten Sicherung zu suchen. Die Replikation liest die Protokollfolgenummer (Log Sequence Number, LSN) aus der Sicherung. Alle Änderungen in der ersten Veröffentlichungsdatenbank mit einer höheren LSN werden an alle Peers übermittelt.  
  
     Diese Option ist möglicherweise nicht verfügbar, wenn Sie eine Topologie erstellen, die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]umfasst, oder einer solchen Topologie Knoten hinzufügen. Die folgende Tabelle zeigt, ob die Option beim Hinzufügen eines Knotens zu einer vorhandenen Topologie verfügbar ist.  
  
    |Neuer Knoten|Erster Knoten|Weitere Knoten|Option|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Keine|Disabled|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Disabled|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Keine|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Keine|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Aktiviert|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Keine|Aktiviert|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikationsprogrammierung mit Transact-SQL&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)  
  
  
