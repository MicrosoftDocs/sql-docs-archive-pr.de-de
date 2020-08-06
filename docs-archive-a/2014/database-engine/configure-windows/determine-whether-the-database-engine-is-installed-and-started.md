---
title: Bestimmen, ob die Datenbank-Engine installiert und gestartet wurde | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724174"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>Bestimmen, ob die Datenbank-Engine installiert und gestartet wurde
  Bei einer erfolgreichen Installation von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] werden Dateien auf dem Dateisystem installiert, Einträge in der Registrierung erstellt und verschiedene Tools installiert. In diesem Thema wird beschrieben, wie bestimmt wird, ob der [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert und in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers gestartet wird.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>Anzeigen und Starten der Datenbank-Engine mithilfe des SQL Server-Konfigurations-Managers  
  
1.  Klicken Sie auf **Start**, wählen Sie **Alle Programme**aus, zeigen Sie auf **Microsoft SQL Server**, auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
     Wenn diese Einträge im Menü **Start** nicht enthalten sind, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht korrekt installiert. Führen Sie das Setup aus, um [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]zu installieren.  
  
2.  Klicken Sie im linken Bereich von **SQL Server-Konfigurations-Manager**auf **SQL Server 2005-Dienste**. Im rechten Bereich werden mehrere Dienste im Zusammenhang mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aufgelistet. Wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert ist, wird der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Dienst als **SQL Server (MSSQLSERVER)** aufgelistet, wenn es sich um die Standardinstanz handelt, oder als **SQL Server (** \<*instance_name*> **)** , wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] als benannte Instanz installiert wurde. Sofern der Instanzname nicht geändert wird, wird [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] als benannte Instanz mit dem Namen **SQLEXPRESS**installiert. Ein grünes Dreieckssymbol weist darauf hin, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgeführt wird. Ein rotes Dreieckssymbol gibt an, dass [!INCLUDE[ssDE](../../includes/ssde-md.md)] beendet wurde.  
  
3.  Um das [!INCLUDE[ssDE](../../includes/ssde-md.md)]zu starten, klicken Sie im rechten Bereich mit der rechten Maustaste auf das [!INCLUDE[ssDE](../../includes/ssde-md.md)]und klicken dann auf **Start**.  
  
> [!NOTE]  
>  Während Setup kann der Benutzer ein Verzeichnis für die Installation der Programmdateien und der Datenbankdateien auswählen. Wenn der Benutzer den Standardspeicherort übernimmt, werden die Dateien unter [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] und C:\Programme\Microsoft SQL Server\MSSQL.*x*installiert, wobei *x* eine Zahl ist.  
  
  
