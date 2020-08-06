---
title: Anzeigen der Ereignisse für registrierte Pakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5e3665a695bd3f40407a8680872c9b0dc79fbc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622810"
---
# <a name="view-the-events-for-registered-packages"></a>Anzeigen der Ereignisse für registrierte Pakete
  Bevor Sie eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events-Sitzung erstellen, sollten Sie zunächst herausfinden, welche Ereignisse in den registrierten Paketen verfügbar sind. Weitere Informationen finden Sie unter [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
 Um diese Aufgabe auszuführen, müssen Sie mit dem Abfrage-Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] den folgenden Vorgang durchführen.  
  
 Nach Abschluss der Anweisungen in dieser Prozedur werden auf der Registerkarte **Ergebnisse** des Abfrage-Editors die folgenden Spalten angezeigt:  
  
-   name. Der Paketname.  
  
-   event. Der Ereignisname.  
  
-   keyword. Ein Schlüsselwort, das von einer internen numerischen Zuordnungstabelle abgeleitet wird.  
  
-   channel. Die Zielgruppe für ein Ereignis.  
  
-   description. Die Beschreibung des Ereignisses.  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a>So zeigen Sie die Ereignisse für registrierte Pakete mittels Abfrage-Editor an  
  
-   Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server von Paketen für erweiterte Ereignisse](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
