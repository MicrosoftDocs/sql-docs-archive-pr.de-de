---
title: MSSQLSERVER_15404 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beb854c866256728574e06f8c9efb50fb354e15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620947"
---
# <a name="mssqlserver_15404"></a>MSSQLSERVER_15404
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|15404|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_NTGRP_ERROR|  
|Meldungstext|Die Informationen über Windows NT-Gruppe oder -Benutzer *user*, Fehlercode *code* konnten nicht abgerufen werden.|  
  
## <a name="explanation"></a>Erklärung  
 Wenn ein ungültiger Prinzipal angegeben wird, wird 15404 bei der Authentifizierung verwendet. Oder der Identitätswechsel eines Windows-Kontos schlägt fehl, weil keine vollständige Vertrauensstellung zwischen dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto und der Domäne des Windows-Kontos besteht.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie, ob der Windows-Prinzipal vorhanden und nicht falsch geschrieben ist.  
  
 Wenn dieser Fehler aus einer fehlenden vollständigen Vertrauensstellung zwischen dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto und der Domäne des Windows-Kontos resultiert, kann er durch eine der folgenden Aktionen behoben werden:  
  
-   Verwenden Sie für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst ein Konto, das aus derselben Domäne wie der Windows-Benutzer stammt.  
  
-   Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Computerkonto wie Netzwerkdienst oder Lokales System verwendet, muss der Computer von der Domäne, in der der Windows-Benutzer enthalten ist, als vertrauenswürdig eingestuft werden.  
  
-   Verwenden Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konto.  
  
  
