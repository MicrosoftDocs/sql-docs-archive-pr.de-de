---
title: Der Protokoll Versand wird nach dem Upgrade nicht ausgeführt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2af60743cb2cbf9bf455397fe052c4e81f5a06d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622402"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>Protokollversand wird nach Update nicht ausgeführt
  Der Upgrade Advisor hat festgestellt, dass Sie den Protokollversand verwenden. Der Protokollversand in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ist nicht mit dem Protokollversand in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] kompatibel und kann nicht direkt aktualisiert werden. Konfigurieren Sie nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]den Protokollversand mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mithilfe gespeicherter Prozeduren neu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent Protokoll Versand-Auftrags Kategorie bewirkt, dass das Upgrade fehlschlägt](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Beim Upgrade wird das SQL Server-Agent Benutzer Proxy Konto in das temporäre UpgradedProxyAccount geändert.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
