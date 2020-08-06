---
title: MSSQLSERVER_1904 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617076"
---
# <a name="mssqlserver_1904"></a>MSSQLSERVER_1904
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1904|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|KEYCOUNT|  
|Meldungstext|Das %S_MSG-Objekt '%.*ls' in der '%.\*ls'-Tabelle weist %d Spaltennamen in der %S_MSG-Schlüsselliste auf. Die maximale Anzahl für Spaltenlisten von Index- oder Statistikschlüsseln beträgt % d.|  
  
## <a name="explanation"></a>Erklärung  
 Die Schlüsselspaltenliste für den angegebenen Index bzw. die angegebenen Statistiken überschreitet die maximal zulässige Anzahl von Spalten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Ändern Sie die Schlüsselspaltenliste, sodass nur die maximal zulässige Anzahl von Spalten eingeschlossen wird.  
  
 Ziehen Sie bei nicht gruppierten Indizes die Verwendung der INCLUDE-Klausel in der CREATE INDEX-Anweisung in Betracht, um dem Index Spalten als Nichtschlüsselspalten hinzuzufügen. Auf diese Weise können Sie vermeiden, dass die aktuelle Größenbeschränkung des Indexes von maximal 16 Schlüsselspalten überschritten wird. Weitere Informationen finden Sie unter [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
