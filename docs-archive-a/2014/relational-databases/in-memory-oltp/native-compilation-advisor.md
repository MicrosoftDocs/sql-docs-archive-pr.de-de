---
title: Ratgeber für native Kompilierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: b2182d89489af5da8bc3b85b89484fbbf72e4dfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725745"
---
# <a name="native-compilation-advisor"></a>Ratgeber für native Kompilierung
  Das Tool Transaktions Leistungsberichte (siehe [ermitteln, ob eine Tabelle oder eine gespeicherte Prozedur zu in-Memory OLTP portiert werden soll](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informiert Sie darüber, welche interpretierten gespeicherten Prozeduren in der Datenbank von einer Portierung zur systeminternen Kompilierung profitieren. Nachdem Sie eine gespeicherte Prozedur identifiziert haben, die Sie zur Verwendung der systeminternen Kompilierung portieren möchten, können Sie den Ratgeber für die systeminterne Kompilierung verwenden, um die Migration der interpretierten gespeicherten Prozedur zur systeminternen Kompilierung zu vereinfachen. Weitere Informationen zu systemintern kompilierten gespeicherten Prozeduren finden Sie unter [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).  
  
 Stellen Sie zunächst eine Verbindung mit der Instanz her, die die interpretierte gespeicherte Prozedur enthält. Die Verbindung kann mit einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] hergestellt werden. Wenn Sie jedoch einen Migrationsvorgang mit dem Ratgeber ausführen möchten, müssen Sie eine Verbindung mit einer [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Instanz herstellen, für die In-Memory OLTP aktiviert ist. Weitere Informationen zu den Anforderungen für In-Memory OLTP finden Sie unter [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).  
  
 Weitere Informationen zu Migrationsmethoden finden Sie unter [In-Memory OLTP - Common Workload Patterns and Migration Considerations (In-Memory-OLTP: Allgemeine Workloadmuster und Überlegungen zur Migration)](https://msdn.microsoft.com/library/dn673538.aspx).  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a>Exemplarische Vorgehensweise: Ratgeber für native Kompilierung  
 Klicken Sie im **Objekt-Explorer**mit der rechten Maustaste auf die gespeicherte Prozedur, die Sie konvertieren möchten, und wählen Sie **Ratgeber für native Kompilierung**aus. Daraufhin wird die Willkommensseite für **Ratgeber für die native Kompilierung gespeicherter Prozeduren**angezeigt. Klicken Sie auf zum Fortfahren auf **Weiter**.  
  
### <a name="stored-procedure-validation"></a>Überprüfung der gespeicherten Prozedur  
 Auf dieser Seite wird angezeigt, ob die gespeicherte Prozedur Konstrukte verwendet, die mit der nativen Kompilierung nicht kompatibel sind. Klicken Sie auf **Weiter** , um weitere Details anzuzeigen. Wenn Konstrukte vorhanden sind, die nicht mit der nativen Kompilierung kompatibel sind, können Sie durch Klicken auf **Weiter** zusätzliche Details abrufen.  
  
### <a name="stored-procedure-validation-result"></a>Überprüfungsergebnis der gespeicherten Prozedur  
 Wenn Konstrukte vorhanden sind, die nicht mit der nativen Kompilierung kompatibel sind, werden auf der Seite **Überprüfungsergebnis der gespeicherten Prozedur** detaillierte Informationen angezeigt. Sie können (durch Klicken auf **Bericht generieren**) einen Bericht generieren, den **Ratgeber für native Kompilierung**beenden und den Code aktualisieren, sodass er mit der nativen Kompilierung kompatibel ist.  
  
## <a name="code-sample"></a>Codebeispiel  
 Im folgenden Beispiel werden eine interpretierte gespeicherte Prozedur und die äquivalente gespeicherte Prozedur für die systeminterne Kompilierung erläutert. Das in diesem Beispiel verwendete Verzeichnis ist c:\data.  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
