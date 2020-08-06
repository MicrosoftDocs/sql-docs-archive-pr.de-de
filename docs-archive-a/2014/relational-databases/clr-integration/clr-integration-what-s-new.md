---
title: Neuerungen bei der CLR-Integration in&#39;| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: b51eb5d8bee5ff8e514f294d5e9facca93a30bfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617120"
---
# <a name="what39s-new-in-clr-integration"></a>Neuerungen bei der CLR-Integration&#39;s
  Die folgenden Funktionen sind neue CLR-Integrationsfunktionen in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   In Version 4 der CLR fangen CLR-Datenbankobjekte nicht länger Ausnahmen aufgrund eines beschädigten Status ab. Diese Ausnahmen werden jetzt in der CLR-Integrationshostingebene abgefangen. Diese Ausnahmen können weiterhin von den CLR-Datenbankkomponenten abgefangen werden, indem ein Code-Attribut (-[ \<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)) festgelegt wird. Diese Vorgehensweise wird jedoch nicht empfohlen, da die Ergebnisse nicht zuverlässig sind, wenn eine Ausnahme aufgrund eines beschädigten Status auftritt.  
  
-   Wegen der strengen Sicherheitsanforderungen von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verwenden CLR-Datenbankkomponenten weiterhin das Codezugriffssicherheitsmodell, das in CLR, Version 2.0, definiert wurde.  
  
-   In CLR Version 4 generiert ein Formatfehler in einem `System.TimeSpan`-Wert eine `System.FormatExceptions`. Vor Version 4 der CLR wurde ein Formatfehler in einem `System.TimeSpan`-Wert ignoriert. Datenbankanwendungen, die das Verhalten vor Version 4 der CLR benötigen, sollten mit einem Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) von 100 oder niedriger ausgeführt werden. Weitere Informationen finden Sie unter [<TimeSpan_LegacyFormatMode>-Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Version 4 der CLR unterstützt Unicode 5.1. Sortiervorgänge, die Akzentzeichen und Symbole einschließen, werden verbessert. Wenn die Anwendung das Legacysortierverhalten benötigt, können Kompatibilitätsprobleme auftreten. Um die Legacysortierung zu aktivieren, muss der Datenbank-Kompatibilitätsgrad (`ALTER DATABASE Compatibility Level`) auf 100 oder niedriger festgelegt werden. Damit dies unterstützt wird, installiert [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] sort00001000.dll im .NET Framework 4-Verzeichnis (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Weitere Informationen finden Sie unter [\<CompatSortNLSVersion>Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Die folgenden Spalten wurden zu [sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)hinzugefügt: `total_processor_time_ms` , `total_allocated_memory_kb` und `survived_memory_kb` .  
  
  
