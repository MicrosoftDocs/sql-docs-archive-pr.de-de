---
title: MSSQLSERVER_32044 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617073"
---
# <a name="mssqlserver_32044"></a>MSSQLSERVER_32044
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|32044|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQLErrorNum32044|  
|Meldungstext|Die Warnung für 'Spiegelungscommitaufwand' wurde ausgelöst. Der aktuelle Wert von '%d' überschreitet den Threshold '%d'.|  
  
## <a name="explanation"></a>Erklärung  
 Dieses Datenbankspiegelungsereignis wird auf der Prinzipalserverinstanz ausgegeben. Damit soll angegeben werden, dass aufgrund der Datenbankspiegelung mit der gesamten Wartezeit für den Commit ein vom Benutzer angegebener Schwellenwert erreicht oder überschritten wurde. Die Wartezeit ist das Produkt der Anzahl von Transaktionen und der jeweiligen Dauer. In den beiden folgenden Fällen werden z. B. jeweils 1000 Millisekunden Wartezeit erzeugt: 1000 Transaktionen * 1 Millisekunde und 1 Transaktion \* 1000 Millisekunden. Eine erhöhte Commitwartezeit kann durch einen starken Anstieg der Anzahl von Transaktionen, durch Verzögerungen beim Senden des Protokolls oder Verzögerungen beim Leeren des Protokolls auf der Spiegelserverinstanz verursacht werden.  
  
 Der Spiegelungscommitaufwand ist eine Leistungsmetrik, mit der Sie die aktuelle Leistungsauswirkung des synchronen Vorgangs beurteilen können. Diese Metrik ist nur im Modus für hohe Sicherheit relevant. Da der Modus für hohe Sicherheit synchron ausgeführt wird, wartet die Prinzipalserverinstanz darauf, einen Commit für die Transaktion auszuführen, nachdem ein Protokolldatensatz an die Spiegelserverinstanz gesendet wurde, bis eine Bestätigung darüber eingeht, dass der Protokolldatensatz von der Spiegelserverinstanz auf einen Datenträger geschrieben wurde. Der Protokolldatensatz verbleibt auf dem Datenträger der Spiegelserverinstanz, solange auf die Wiederherstellung in der Spiegeldatenbank gewartet wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Prüfen Sie die Auslastung für die Instanzen des Prinzipalservers und des Spiegelservers sowie die entsprechenden Netzwerkverbindungen, um die Ursache zu ermitteln.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Verwenden von Warnungsschwellenwerten und Warnmeldungen für Spiegelungsleistungsmetriken &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
