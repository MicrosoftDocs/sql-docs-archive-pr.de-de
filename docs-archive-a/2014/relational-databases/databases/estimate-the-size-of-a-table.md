---
title: Schätzen der Größe einer Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a16d439d3b2bc59479866b7bb36295ec4fc8950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721478"
---
# <a name="estimate-the-size-of-a-table"></a>Schätzen der Größe einer Tabelle
  Mit den folgenden Schritten können Sie den Umfang des Speicherplatzes schätzen, der zum Speichern von Daten in einer Tabelle erforderlich ist:  
  
1.  Berechnen Sie den erforderlichen Speicherplatz für den Heap oder gruppierten Index mithilfe der Anweisungen in den Artikeln [Schätzen der Größe eines Heaps](estimate-the-size-of-a-heap.md) oder [Schätzen der Größe eines gruppierten Indexes](estimate-the-size-of-a-clustered-index.md).  
  
2.  Den für jeden nicht gruppierten Index benötigten Speicherplatz berechnen Sie, indem Sie die Anweisungen ausführen, die Sie unter [Schätzen der Größe eines nicht gruppierten Index](estimate-the-size-of-a-nonclustered-index.md)finden.  
  
3.  Fügen Sie die in den Schritten 1 und 2 berechneten Werte hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schätzen der Größe einer Datenbank](estimate-the-size-of-a-database.md)   
 [Schätzen der Größe eines Heaps](estimate-the-size-of-a-heap.md)   
 [Schätzen der Größe eines gruppierten Indexes](estimate-the-size-of-a-clustered-index.md)   
 [Schätzen der Größe eines nicht gruppierten Index](estimate-the-size-of-a-nonclustered-index.md)  
  
  
