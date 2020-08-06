---
title: Festlegen der SQL Server Verbindung für den SQL Server-Agent Dienst (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30f68967d6bdb8b0495cbddb1a5b0bd447cd5168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630477"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie die Verbindung zwischen dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]festlegen. Mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts kann eine Verbindung mit einer lokalen Instanz von SQL Server mit der Windows-Authentifizierung hergestellt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Festlegen der SQL Server-Verbindung für den SQL Server-Agent mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
-   Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]unterstützt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung. Diese Option ist nur beim Verwalten früherer Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für das- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst Konto erforderlich sind, finden [Sie unter Auswählen eines Kontos für den SQL Server-Agent Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>So legen Sie die SQL Server-Verbindung fest  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen, um den Server zu erweitern, für den Sie eine Verbindung mit dem SQL Server-Agent-Dienst einrichten möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie im Dialogfeld **SQL Server-Agent-Eigenschaften** unter **Seite auswählen** auf **Verbindung**.  
  
4.  Wählen Sie unter **SQL Server-Verbindung** die Option **Windows-Authentifizierung verwenden** aus, damit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent beim Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung verwenden kann. Für Verbindungen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher muss die Windows-Authentifizierung verwendet werden.  
  
  
