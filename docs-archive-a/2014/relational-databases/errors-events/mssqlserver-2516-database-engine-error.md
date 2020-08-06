---
title: MSSQLSERVER_2516 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696877"
---
# <a name="mssqlserver_2516"></a>MSSQLSERVER_2516
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2516|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|Meldungstext|Die Reparatur hat das differenzielle Bitmuster für die NAME-Datenbank für ungültig erklärt. Die Kette differenzieller Sicherungen ist unterbrochen. Vor einer differenziellen Sicherung müssen Sie eine vollständige Datenbanksicherung ausführen.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Informationsmeldung wird zurückgegeben, wenn Fehler MSSQLEngine_2515 behoben wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie eine vollständige Datenbanksicherung aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
