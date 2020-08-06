---
title: Datenbankübergreifende Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4afbb580a55273ec241005493fd37f99e98ec0e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615387"
---
# <a name="cross-database-queries"></a>Datenbankübergreifende Abfragen
  In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]bieten speicheroptimierte Tabellen keine Unterstützung für datenbankübergreifende Transaktionen. Innerhalb einer Transaktion oder Abfrage, die auf eine speicheroptimierte Tabelle zugreift, können Sie nicht gleichzeitig auf eine andere Datenbank zugreifen. Daten aus einer Tabelle in einer Datenbank können nicht einfach in eine speicheroptimierte Tabelle in einer anderen Datenbank kopiert werden.  
  
 Tabellenvariablen sind nicht transaktional. Daher können speicheroptimierte Tabellenvariablen in datenbankübergreifenden Abfragen verwendet werden, um Daten aus einer Datenbank in speicheroptimierte Tabellen in einer anderen Datenbank zu verschieben. Sie können zwei Transaktionen verwenden. In der ersten Transaktion fügen Sie die Daten aus der Remotetabelle in die Variable ein. In der zweiten Transaktion fügen Sie die Daten aus der Variablen in die lokale speicheroptimierte Tabelle ein.  
  
 Wenn Sie z. b. die Zeile aus Tabelle T1 in Datenbank db1 in Tabelle T2 in DB2 kopieren möchten, verwenden Sie eine Variable @v1 des Typs dbo. TT1, um Folgendes zu verwenden:  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
