---
title: MSSQLSERVER_41030 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b137b739d4c1641b88983708df62d2e52fd0eab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721477"
---
# <a name="mssqlserver_41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41030|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|OPEN_CLUSTER_SUB_KEY|  
|Meldungstext|Fehler beim Öffnen des WSFC (Windows Server Failover Clustering)-Registrierungsunterschlüssels '%.*ls' (Fehlercode %d).  Der übergeordnete Schlüssel ist der Clusterstammschlüssel.  Der WSFC-Dienst wird möglicherweise nicht ausgeführt, der Zugriff auf den Dienst ist möglicherweise im aktuellen Zustand nicht möglich, oder die angegebenen Argumente sind ungültig. Wurde die entsprechende Verfügbarkeitsgruppe gelöscht, wird dieser Fehler erwartet. Informationen zu diesem Fehlercode finden Sie in der Dokumentation für die Windows-Entwicklung im Abschnitt zu Systemfehlercodes.|  
  
## <a name="explanation"></a>Erklärung  
 Wenn ein WSFC-Cluster zerstört wird, werden alle auf [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] bezogenen Registrierungsschlüssel entfernt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Nach dem Neuerstellen eines WSFC-Clusters deaktivieren und aktivieren Sie dann AlwaysOn auf jedem Clusterknoten erneut, auf dem eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz für AlwaysOn aktiviert wird. Sie können für diese Aufgabe den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren und deaktivieren Sie AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
