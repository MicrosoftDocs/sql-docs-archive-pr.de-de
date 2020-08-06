---
title: MSSQLSERVER_8996 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d0cb5f0294ea471a6e300adbabc0f7b55632994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620877"
---
# <a name="mssqlserver_8996"></a>MSSQLSERVER_8996
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8996|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP|  
|Meldungstext|Die IAM-Seite P_ID für Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (TYPE-Typ) steuert Seiten in Dateigruppe FG_ID1, die in Dateigruppe FG_ID2 vorhanden sein müssen.|  
  
## <a name="explanation"></a>Erklärung  
 IAM-Seite (Index Allocation Map) *P_ID* in der Dateigruppe *FG_ID1* enthält fälschlicherweise Erweiterungen aus der Dateigruppe *FG_ID2*. Alle Blöcke für eine IAM-Seite sollten sich in der gleichen Dateigruppe wie die IAM-Seite selbst befinden.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Nicht zutreffend Dieser Fehler kann nicht repariert werden. Wenn Sie die Datenbank nicht mithilfe einer Sicherung wiederherstellen können, wenden Sie sich an den Kundenservice und -support von [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
