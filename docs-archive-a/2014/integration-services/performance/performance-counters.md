---
title: Leistungsindikatoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b20ac056894066114883153030943bec1c05963
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617159"
---
# <a name="performance-counters"></a>Leistungsindikatoren
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert eine Reihe von Leistungsindikatoren, mit denen Sie die Leistung der Datenfluss-Engine überwachen können. Sie können beispielsweise den Indikator "Gespoolte Puffer" überwachen, um zu bestimmen, ob Datenpuffer vorübergehend auf den Datenträger geschrieben werden, während ein Paket ausgeführt wird. Diese Auslagerung reduziert die Leistung und weist darauf hin, dass der Computer nicht genügend Arbeitsspeicher hat.  
  
> [!NOTE]  
>  Wenn Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf einem Computer installieren, auf dem [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]ausgeführt wird, und anschließend ein Upgrade des betreffenden Computers auf [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]ausführen, werden beim Upgradeprozess die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Leistungsindikatoren vom Computer entfernt. Zum Wiederherstellen der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Leistungsindikatoren auf dem Computer führen Sie Setup von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Reparaturmodus aus.  
  
 In der folgenden Tabelle sind diese Leistungsindikatoren beschrieben.  
  
|Leistungsindikator|BESCHREIBUNG|  
|-------------------------|-----------------|  
|Gelesene BLOB-Bytes|Die Anzahl der Bytes der BLOB-Daten (Binary Large Object), die die Datenfluss-Engine in allen Datenquellen gelesen hat.|  
|Geschriebene BLOB-Bytes|Die Anzahl der Bytes der BLOB-Daten (Binary Large Object), die die Datenfluss-Engine in alle Ziele geschrieben hat.|  
|Verwendete BLOB-Dateien|Die Anzahl von BLOB-Dateien, die die Datenfluss-Engine zurzeit zum Spoolen verwendet.|  
|Pufferspeicher|Die zurzeit verwendete Arbeitsspeichermenge. Hier kann sowohl der physische als auch der virtuelle Speicher enthalten sein. Wenn diese Zahl den physischen Speicher übersteigt, vergrößert sich der Wert für **Gespoolte Puffer** , um anzuzeigen, dass Speicherauslagerungsvorgänge zunehmen. Umfangreiche Speicherauslagerungsvorgänge beeinträchtigen die Leistung der Datenfluss-Engine.|  
|Verwendete Puffer|Die Anzahl von Pufferobjekten aller Typen, die alle Datenflusskomponenten und die Datenfluss-Engine zurzeit verwenden.|  
|Gespoolte Puffer|Der Anzahl von zurzeit auf den Datenträger geschriebenen Puffern. Wenn der Datenfluss-Engine nur wenig physischer Speicher zur Verfügung steht, werden die Puffer, die zurzeit nicht verwendet werden, auf den Datenträger geschrieben und anschließend, falls erforderlich, neu geladen.|  
|Flatpufferspeicher|Die Gesamtanzahl der Bytes des Speichers, der von allen Flatpuffern verwendet wird. Als Flatpuffer werden Speicherblöcke bezeichnet, die von einer Komponente zum Speichern von Daten verwendet werden. Ein Flatpuffer ist ein großer Byteblock, auf den byteweise zugegriffen wird (also ein Byte nach dem anderen).|  
|Verwendete Flatpuffer|Die Anzahl der von der Datenfluss-Engine verwendeten Flatpuffer. Alle Flatpuffer sind private Puffer.|  
|Privater Pufferspeicher|Der Gesamtspeicher, der von allen privaten Puffern verwendet wird. Ein Puffer ist nicht privat, wenn die Datenfluss-Engine ihn zur Unterstützung des Datenflusses erstellt. Ein Puffer wird als privat bezeichnet, wenn er von einer Transformation für temporäre Arbeitsvorgänge verwendet wird. Private Puffer werden beispielsweise von der Aggregationstransformation verwendet.|  
|Private verwendete Puffer|Die Anzahl der von Transformationen verwendeten Puffer.|  
|Gelesene Zeilen|Die Anzahl der Zeilen, die von einer Quelle erstellt werden. In dieser Anzahl sind die von der Transformation für Suche aus Verweistabellen gelesenen Zeilen nicht enthalten.|  
|Geschriebene Zeilen|Die Anzahl der Zeilen, die für ein Ziel verfügbar gemacht werden. In dieser Anzahl sind die in den Zieldatenspeicher geschriebenen Zeilen nicht enthalten.|  
  
 Verwenden Sie das Leistungs-Snap-In von Microsoft Management Console (MMC), um ein Protokoll zu erstellen, in dem die Leistungsindikatoren aufgezeichnet werden.  
  
 Weitere Informationen zur Verbesserung der Leistung finden Sie unter [Funktionen für die Datenflussleistung](../data-flow/data-flow-performance-features.md).  
  
## <a name="obtain-performance-counter-statistics"></a>Abrufen von Leistungsindikatorstatistiken  
 Für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekte, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server bereitgestellt werden, können Sie Leistungsindikatorstatistiken mithilfe der Funktion [dm_execution_performance_counters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/functions-dm-execution-performance-counters) abrufen.  
  
 Im folgenden Beispiel gibt die Funktion Statistiken für eine aktive Ausführung mit einer ID von 34 zurück.  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 Im folgenden Beispiel gibt die Funktion Statistiken für alle Ausführungen zurück, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server ausgeführt werden.  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  Wenn Sie ein Mitglied der `ssis_admin`-Datenbankrolle sind, werden Leistungsstatistiken für alle aktiven Ausführungen zurückgegeben.  Wenn Sie kein Mitglied der `ssis_admin`-Datenbankrolle sind, werden Leistungsstatistiken zu den aktiven Ausführungen zurückgegeben, für die Sie Leseberechtigungen haben.  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Tool, [SSIS Performance Visualization für Business Intelligence Development Studio (CodePlex-Projekt)](https://go.microsoft.com/fwlink/?LinkId=146626)auf codeplex.com.  
  
-   Video [Messen und Verstehen der Leistung der SSIS-Pakete in Enterprise (SQL Server-Video)](https://go.microsoft.com/fwlink/?LinkId=150497)auf msdn.microsoft.com.  
  
-   Supportartikel [Der SSIS-Leistungsindikator ist im Systemmonitor nicht mehr verfügbar, wenn Sie ein Upgrade auf Windows Server 2008 ausführen](https://go.microsoft.com/fwlink/?LinkId=235319)auf support.microsoft.com.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführung von Projekten und Paketen](../packages/run-integration-services-ssis-packages.md)  
  
  
