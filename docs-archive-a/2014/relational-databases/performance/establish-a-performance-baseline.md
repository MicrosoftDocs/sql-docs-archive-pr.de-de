---
title: Festlegen einer Leistungsbasislinie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cb85ae8ad370b816c6240b58aabd247c7593c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696741"
---
# <a name="establish-a-performance-baseline"></a>Festlegen einer Leistungsbasislinie
  Wenn Sie ermitteln möchten, ob das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System einwandfrei arbeitet, sollten Sie die Leistung in regelmäßigen Abständen messen, selbst wenn keine Probleme auftreten, um eine Basislinie für die Serverleistung zu erstellen. Vergleichen Sie jede neue Messreihe mit den zuvor erfassten Messungen.  
  
 Die folgenden Bereiche wirken sich auf die Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aus:  
  
-   Systemressourcen (Hardware)  
  
-   Netzwerkarchitektur  
  
-   Das Betriebssystem  
  
-   Datenbankanwendungen  
  
-   Clientanwendungen  
  
 Es sollten mindestens die folgenden Basislinienmessungen vorgenommen werden:  
  
-   Leistung bei Spitzen- und Normalbetrieb.  
  
-   Antwortzeiten für Produktionsabfragen oder Batchbefehle.  
  
-   Zeiten für das Sichern und Wiederherstellen von Datenbanken.  
  
 Nach dem Erstellen einer Basislinie für die Serverleistung sollten Sie die Basislinienstatistik mit der aktuellen Serverleistung vergleichen. Zahlen, die deutlich über oder unter der Basislinie liegen, sollten näher untersucht werden. Sie können ein Hinweis auf Bereiche, die optimiert oder neu konfiguriert werden müssen, sein. Wenn beispielsweise die Zeitdauer zum Ausführen einer Reihe von Abfragen steigt, sollten Sie die Abfragen untersuchen, um festzustellen, ob sie neu geschrieben werden können oder ob Spaltenstatistiken oder neue Indizes hinzugefügt werden müssen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
