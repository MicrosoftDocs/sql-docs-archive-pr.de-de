---
title: MSSQLSERVER_847 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 847 (Database Engine error)
ms.assetid: 67208b7c-bd8d-48a1-9f70-a6488e0f5f9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b2d5c0a35533700606a44867d2a51cf9087e399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619862"
---
# <a name="mssqlserver_847"></a>MSSQLSERVER_847
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|847|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|–|  
|Meldungstext|Timeout beim Warten auf einen Latch: Klasse „%ls“, ID „%p“, Typ „%d“, Task „0x%p“ : „%d“, Wartezeit „%d“, Flags „0x%I64x“, besitzender Task „0x%p“. Der Wartevorgang wird fortgesetzt.|  
  
## <a name="explanation"></a>Erklärung  
 Möglicherweise reagiert ein Computer nicht mehr, oder ein Timeout bzw. eine andere Unterbrechung des regulären Betriebs tritt auf, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gleichzeitig Pufferlatchfehler in das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll schreibt.  
  
 Wenn im STAT-Feld in der Meldung der Wert 0x04 aktiviert ist, wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein E/A-Vorgang erwartet. Zudem wird möglicherweise die Meldung [MSSQLSERVER_833](mssqlserver-833-database-engine-error.md) im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerprotokoll ausgegeben.  
  
 Wenn im STAT-Feld in der Meldung der Wert 0x04 deaktiviert ist, bestehen für eine Seite schwerwiegende Konflikte. Wenn es sich bei dem Objekt um eine Datenseite handelt, kann dies auf ineffiziente Codeentwürfe zurückzuführen sein. Wenn die Seite keine Daten darstellt, wird der Fehler möglicherweise durch Serverengpässe wie unzureichende Hardwareressourcen verursacht.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie dieses Problem umgehen möchten, werden die Fehlermeldungen in Abhängigkeit von Ihrer Umgebung durch einen oder mehrere der folgenden Schritte möglicherweise reduziert oder behoben:  
  
-   Ermitteln Sie, ob Hardware-Engpässe vorliegen. Rüsten Sie gegebenenfalls Ihre Hardware auf, sodass die Konfigurations-, Abfrage- und Ladeanforderungen Ihrer Umgebung unterstützt werden. Weitere Informationen zu Engpässen finden Sie unter [Identifizieren von Engpässen](../performance/identify-bottlenecks.md).  
  
-   Überprüfen Sie alle protokollierten Fehler, und führen Sie alle von Ihrem Hardwarehersteller bereitgestellten Diagnosen aus.  
  
-   Stellen Sie sicher, dass Ihre Laufwerke nicht komprimiert sind. Das Speichern von Daten bzw. Protokolldateien auf komprimierten Laufwerken wird nicht unterstützt. Weitere Informationen zu Dateien und Dateigruppen finden Sie unter [Database Files and Filegroups](../databases/database-files-and-filegroups.md).  
  
-   Prüfen Sie, ob die Fehlermeldungen behoben werden, wenn Sie folgende Optionen deaktivieren:  
  
    -   SQL Server-Prioritätserhöhung (Konfigurationsoption)  
  
    -   Lightweightpooling (Fibermodus), Option  
  
    -   Festgelegte Workingsetgröße (Option)  
  
    > [!NOTE]  
    >  Die vorherigen Einstellungen können häufig kontraproduktiv sein, wenn Sie die Standardeinstellung OFF ändern. Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
-   Optimieren Sie die Abfragen, um die für das System verwendeten Ressourcen zu reduzieren. Durch Leistungsoptimierung kann die Belastung für ein System reduziert und die Reaktionszeit für einzelne Abfragen verbessert werden.  
  
-   Legen Sie die Option AUTO_SHRINK auf OFF fest, um den Aufwand für Änderungen an der Datenbankgröße zu verringern.  
  
-   Stellen Sie sicher, dass Sie die Option FILEGROWTH auf Inkremente festlegen, die groß genug sind und somit nicht häufig auftreten. Planen Sie einen Auftrag, um den verfügbaren Speicherplatz in den Datenbanken zu überprüfen, und erhöhen Sie dann die Datenbankgröße außerhalb der Spitzenzeiten.  
  
  
