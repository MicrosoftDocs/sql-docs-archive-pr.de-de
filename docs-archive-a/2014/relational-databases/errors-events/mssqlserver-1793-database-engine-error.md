---
title: MSSQLSERVER_1793 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699692"
---
# <a name="mssqlserver_1793"></a>MSSQLSERVER_1793
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1793|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Meldungstext|Das Löschen des Indexes '%.*ls' ist nicht möglich, da kein Partitionsschema für FILESTREAM-Daten angegeben wurde.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung wird angezeigt, wenn Sie versuchen, einen gruppierten Index für eine Tabelle zu löschen, die FILESTREAM-Daten enthält, und eine **MOVE TO**-Klausel für die Basisdaten angeben, dabei aber keine **FILESTREAM_ON**-Klausel für die FILESTREAM-Daten bereitstellen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie beim Löschen eines gruppierten Indexes in einer Tabelle, die FILESTREAM-Daten enthält, eine der folgenden Optionen:  
  
-   Geben Sie sowohl eine **MOVE TO**-Klausel für die Basisdaten als auch eine **FILESTREAM_ON**-Klausel für die FILESTREAM-Daten an.  
  
-   Geben Sie nicht entweder eine **MOVE TO**-Klausel für die Basisdaten oder eine **FILESTREAM_ON**-Klausel für die FILESTREAM-Daten an.  
  
 Im folgenden Beispiel tritt ein Fehler auf, da ein Partitionsschema für die Basisdaten angegeben ist, jedoch nicht für die FILESTREAM-Daten.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 Das folgende Beispiel ist erfolgreich, da sowohl eine **MOVE TO**-Klausel für die Basisdaten als auch eine **FILESTREAM_ON**-Klausel für die FILESTREAM-Daten angegeben wird.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 Das folgende Beispiel ist auch erfolgreich, da weder eine **MOVE TO**-Klausel für die Basisdaten noch eine **FILESTREAM_ON**-Klausel für die FILESTREAM-Daten angegeben wird.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
