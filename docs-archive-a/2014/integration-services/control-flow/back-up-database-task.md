---
title: Datenbank sichern (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615504"
---
# <a name="back-up-database-task"></a>Datenbank sichern (Task)
  Der Task Datenbank sichern führt verschiedene Arten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanksicherungen aus. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Mithilfe des Tasks Datenbank sichern kann ein Paket eine einzelne Datenbank oder mehrere Datenbanken sichern. Wenn mit dem Task nur eine einzelne Datenbank gesichert wird, können Sie die Sicherungskomponente auswählen: die Datenbank, oder ihre Dateien und Dateigruppen.  
  
## <a name="supported-recover-models-and-backup-types"></a>Unterstützte Wiederherstellungsmodelle und Sicherungstypen  
 In der folgenden Tabelle sind die Wiederherstellungsmodelle und Sicherungstypen aufgeführt, die vom Task Datenbank sichern unterstützt werden.  
  
|Wiederherstellungsmodell|Datenbank|Datenbank - differenziell|Transaktionsprotokoll|Datei oder differenzielle Datei|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Einfach|Erforderlich|Optional|Nicht unterstützt|Nicht unterstützt|  
|Vollständig|Erforderlich|Optional|Erforderlich|Optional|  
|Massenprotokolliert|Erforderlich|Optional|Erforderlich|Optional|  
  
 Der Task Datenbank sichern kapselt eine BACKUP-Anweisung von Transact-SQL. Weitere Informationen finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
## <a name="configuration-of-the-back-up-database-task"></a>Konfiguration des Tasks "Datenbank sichern"  
 Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen. Dieser Task ist im **-Designer in der** Toolbox **im Abschnitt** Wartungsplantasks [!INCLUDE[ssIS](../../../includes/ssis-md.md)] enthalten.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Task „Datenbank sichern“ &#40;Wartungsplan&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
  
