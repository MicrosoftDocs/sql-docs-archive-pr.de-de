---
title: MSSQLSERVER_41396 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699620"
---
# <a name="mssqlserver_41396"></a>MSSQLSERVER_41396
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41396|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|MAX_SORT_ROWS_EXCEEDED|  
|Meldungstext|Das Pufferlimit wurde vom Sortiervorgang überschritten. Die Ausführung der gespeicherten Prozedur wurde abgebrochen. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
 Systemintern kompilierte gespeicherte Prozeduren führen Sortiervorgänge im Arbeitsspeicher aus. Es gibt eine Beschränkung bezüglich der Größe des Sortierungspuffers. Dieser Fehler bewirkt, dass dieser Grenzwert von der Größe des Sortierungspuffers überschritten wird. Der Sortiervorgang und die Ausführung der gespeicherten Prozedur wurden abgebrochen.  
  
 Die Größe jeder Zeile bzw. jedes Eintrags im Sortierungspuffer hängt von der Anzahl der sortierten Zeilen, der Anzahl der Joins sowie von der Anzahl und dem Typ der Aggregatfunktionen in der Abfrage ab. Indem Sie die Abfrage vereinfachen, können Sie die Größe jeder Zeile reduzieren, wodurch mehr Zeilen in den Sortierungspuffer passen. Die Größe der Zeilen in den Basistabellen wirkt sich nicht auf die Größe der einzelnen Zeilen oder Einträge im Sortierungspuffer aus.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wählen Sie weniger Zeilen aus, oder verringern Sie die Komplexität der Abfrage, indem Sie Joins oder Aggregatfunktionen entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
