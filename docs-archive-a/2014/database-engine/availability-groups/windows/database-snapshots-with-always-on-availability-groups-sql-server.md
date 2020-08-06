---
title: Daten Bank Momentaufnahmen mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1e4307653b5b8150d71019a373ee073d15123f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721758"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a>Datenbankmomentaufnahmen bei AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Sie können auf einer primären oder sekundären Datenbank in einer Verfügbarkeitsgruppe eine Datenbankmomentaufnahme erstellen. Die Replikatrolle muss entweder PRIMARY oder SECONDARY sein und darf nicht den Status RESOLVING aufweisen.  
  
 Der Datenbanksynchronisierungsstatus sollte SYNCHRONIZING oder SYNCHRONIZED sein, wenn Sie eine Datenbankmomentaufnahme erstellen. Datenbankmomentaufnahmen können jedoch auch erstellt werden, wenn der Datenbanksynchronisierungsstatus NOT SYNCHRONIZING lautet.  
  
 Eine Datenbankmomentaufnahme auf einem sekundären Replikat sollte weiterhin funktionieren, wenn das Replikat mit DISCONNECTED vom primären Replikat getrennt wird.  
  
 Einige [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Bedingungen bewirken, dass sowohl die Quelldatenbank als auch deren Datenbankmomentaufnahmen neu gestartet werden, wobei die Verbindung für Benutzer vorübergehend getrennt wird. Nachfolgend sind diese Bedingungen aufgeführt:  
  
-   Das primäre Replikat ändert Rollen, entweder, weil das aktuelle primäre Replikat offline und dann auf der gleichen Serverinstanz wieder online geschaltet wird, oder weil die Verfügbarkeitsgruppe ein Failover ausführt.  
  
-   Die Datenbank wechselt zur sekundäre Rolle.  
  
 Wenn das Verfügbarkeitsreplikat, das Datenbankmomentaufnahmen hostet, ein Failover ausgeführt hat, bleiben die Datenbankmomentaufnahmen auf der Serverinstanz, auf der sie erstellt wurden. Benutzer können die Momentaufnahmen nach dem Failover weiter verwenden. Wenn die Leistung in Ihrer Umgebung wichtig ist, empfiehlt es sich, dass Sie Datenbankmomentaufnahmen nur auf sekundären Datenbanken erstellen, die von einem sekundären Replikat gehostet werden, das für manuellen Failovermodus konfiguriert ist.  Sollte es je zu einem manuellen Failover der Verfügbarkeitsgruppe zu diesem sekundären Replikat kommen, können Sie auf einem anderen sekundären Replikat einen neuen Satz von Datenbankmomentaufnahmen erstellen, Clients an die neuen Datenbankmomentaufnahmen umleiten und alle Datenbankmomentaufnahmen aus den jetzt primären Datenbanken löschen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Datenbank-Momentaufnahmen &#40;SQL Server&#41;](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
