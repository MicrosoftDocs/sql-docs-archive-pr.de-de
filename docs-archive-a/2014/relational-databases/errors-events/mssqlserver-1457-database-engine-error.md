---
title: MSSQLSERVER_1457 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1457 (Database Engine error)
ms.assetid: 28434ba1-b033-4866-ab41-111fccef45a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c30ee6149c95d93bdaf1d2877f5fe1871a575ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620957"
---
# <a name="mssqlserver_1457"></a>MSSQLSERVER_1457
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1457|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_PAGE_UNDO_PENDING|  
|Meldungstext|Die Synchronisierung der '%.*ls'-Spiegeldatenbank wurde unterbrochen, und die Datenbank weist nun einen inkonsistenten Status auf. Der ALTER DATABASE-Befehl ist fehlgeschlagen. Stellen Sie sicher, dass die Spiegeldatenbank wieder online ist. Stellen Sie dann erneut eine Verbindung mit der Spiegelserverinstanz her, und warten Sie, bis die Synchronisierung der Spiegeldatenbank beendet ist.|  
  
## <a name="explanation"></a>Erklärung  
 Mit dieser Meldung wird angegeben, dass mit der ALTER DATABASE *Datenbank_Name* SET PARTNER OFF-Anweisung ein Fehler ausgelöst wurde. Durch den Fehler beim Versuch, die Datenbankspiegelung zu entfernen, wurde die Synchronisierung der Spiegeldatenbank unterbrochen. Die Datenbank weist nun einen inkonsistenten Status auf.  
  
## <a name="user-action"></a>Benutzeraktion  
 So können Sie diesen Fehler mit einer der folgenden Aktionen beheben:  
  
-   Stellen Sie die Verbindung zwischen dem Spiegelserver und dem Prinzipalserver wieder her, um eine Synchronisierung der Spiegeldatenbank zu ermöglichen.  
  
-   Löschen Sie die Spiegeldatenbank.  
  
     Nach dem Löschvorgang können Sie aus den Sicherungen eine neue Spiegeldatenbank erstellen.  
  
    > [!NOTE]  
    >  Solange die Spiegelung noch aktiviert ist, können Sie die Spiegeldatenbank nur nach einem Fehler bei der SET PARTNER OFF-Anweisung löschen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)   
 [Entfernen der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)   
 [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
  
