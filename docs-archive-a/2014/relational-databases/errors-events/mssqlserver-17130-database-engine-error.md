---
title: MSSQLSERVER_17130 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699704"
---
# <a name="mssqlserver_17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17130|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NOLOCKSPACE|  
|Meldungstext|Nicht genügend Arbeitsspeicher für die konfigurierte Anzahl von Sperren. Das Starten wird mit einer kleineren Sperrhashtabelle versucht. Dies kann Auswirkungen auf die Leistung haben. Bitten Sie den Datenbankadministrator, mehr Arbeitsspeicher für diese Instanz der Datenbank-Engine zu konfigurieren.|  
  
## <a name="explanation"></a>Erklärung  
 Nicht genug Arbeitsspeicher für die gewünschte Hashtabellengröße des Sperren-Managers.  Es wird versucht, eine kleinere Hashtabelle zuzuordnen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die Konfigurationsparameter des Serverarbeitsspeichers (minimaler/maximaler Serverarbeitsspeicher) und die Arbeitsspeicherauslastung. Stellen Sie für SQL Server mehr Arbeitsspeicher zur Verfügung.  
  
  
