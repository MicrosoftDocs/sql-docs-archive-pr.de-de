---
title: MSSQLSERVER_2508 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11dd1c72c8cae868b7ebcb02e72ef0db81aeafe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699639"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2508|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Meldungstext|Die %.*ls-Anzahl für das "%.\*ls"-Objekt, Index-ID %d, Partitions-ID %I64d, Zuordnungseinheits-ID %I64d (%.\*ls-Typ) ist nicht richtig. Führen Sie DBCC UPDATEUSAGE aus.|  
  
## <a name="explanation"></a>Erklärung  
 In Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist es möglich, dass für die Zeilen- und Seitenanzahl von Tabellen und Indizes falsche Werte entstehen. Datenbanken, die in Versionen vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] erstellt wurden, können falsche Zählwerte enthalten. DBCC CHECKDB wurde verbessert, sodass diese Fehler nun erkannt werden und diese Meldung zurückgegeben wird, wenn der Fehler erkannt wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Führen Sie DBCC UPDATEUSAGE für das angegebene Objekt bzw. den angegeben Index oder für die Datenbank aus, in der das Objekt enthalten ist, um die falsche Anzahl zu korrigieren.  
  
  
