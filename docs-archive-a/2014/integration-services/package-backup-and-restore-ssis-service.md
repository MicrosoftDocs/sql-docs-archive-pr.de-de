---
title: Paket Sicherung und-Wiederherstellung (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621585"
---
# <a name="package-backup-and-restore-ssis-service"></a>Paketsicherung und -wiederherstellung (SSIS-Dienst)
    
> [!IMPORTANT]  
>  In diesem Thema wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Pakete können im Dateisystem oder in msdb, einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Systemdatenbank, gespeichert werden. In „msdb“ gespeicherte Pakete können mit den Sicherungs- und Wiederherstellungsfunktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gesichert und wiederhergestellt werden.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Sichern und Wiederherstellen der msdb-Datenbank zu erhalten:  
  
-   [Sichern und Wiederherstellen von SQL Server-Datenbanken](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] enthält das Eingabeaufforderungs-Hilfsprogramm **dtutil** (dtutil.exec), das Sie zum Verwalten von Paketen verwenden können. Weitere Informationen finden Sie unter [dtutil Utility](dtutil-utility.md).  
  
## <a name="configuration-files"></a>Konfigurationsdateien  
 Alle im Paket enthaltenen Konfigurationsdateien werden im Dateisystem gespeichert. Diese Dateien werden nicht gesichert, wenn Sie die msdb-Datenbank sichern. Deshalb müssen Sie sicherstellen, dass die Konfigurationsdateien regelmäßig im Rahmen Ihres Plans zur Sicherung von in „msdb“ gespeicherten Paketen gesichert werden. Um Konfigurationen in das Sichern der msdb-Datenbank einzubeziehen, sollten Sie erwägen, anstelle von dateibasierten Konfigurationen den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurationstyp zu verwenden.  
  
## <a name="packages-stored-in-the-file-system"></a>Im Dateisystem gespeicherte Pakete  
 Die im Dateisystem gespeicherte Sicherung von Paketen sollte in den Sicherungsplan einbezogen werden, mit dem das Dateisystem des Servers gesichert wird. Die Konfigurationsdatei des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts, deren Standardname MsDtsSrvr.ini.xml lautet, enthält eine Aufstellung der Ordner auf dem Server, die vom Dienst überwacht werden. Sie sollten sicherstellen, dass diese Ordner gesichert werden. Außerdem können Pakete in anderen Ordnern auf dem Server gespeichert werden. Sie sollten sicherstellen, dass diese Ordner in den Sicherungsprozess einbezogen werden.  
  
  
