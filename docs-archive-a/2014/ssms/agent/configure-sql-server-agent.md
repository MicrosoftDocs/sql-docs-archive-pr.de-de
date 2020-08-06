---
title: Konfigurieren des SQL Server-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81c78faf733fac5ffb9a6e74dbf03f8caaff03d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617363"
---
# <a name="configure-sql-server-agent"></a>Konfigurieren des SQL Server-Agents
  In diesem Thema wird beschrieben, wie Sie einige Konfigurationsoptionen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent während der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angeben. Die vollständigen Konfigurationsoptionen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent sind nur in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) oder den gespeicherten Prozeduren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents verfügbar.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [Sie konfigurieren Sie den SQL Server-Agent](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Klicken Sie im Objekt-Explorer von **auf** SQL Server-Agent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um Aufträge, Operatoren, Warnungen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst zu verwalten. Der Objekt-Explorer zeigt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Knoten jedoch nur dann an, wenn Sie die Berechtigung haben, ihn zu verwenden.  
  
-   Für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst sollte in Failoverclusterinstanzen kein automatischer Neustart aktiviert werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen, die für das- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst Konto erforderlich sind, finden [Sie unter Auswählen eines Kontos für den SQL Server-Agent Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>Sie konfigurieren Sie den SQL Server-Agent  
  
1.  Klicken Sie auf die Schaltfläche **Start** und anschließend im Menü **Start**  auf **Systemsteuerung**.  
  
2.  Klicken Sie in der Systemsteuerung unter **System und Sicherheit**auf **Verwaltung**, und wählen Sie dann **Lokale Sicherheitsrichtlinie**aus.  
  
3.  Klicken Sie in Lokale Sicherheitsrichtlinie auf das Chevron, um den Ordner **Sicherheitsrichtlinien** zu erweitern, und klicken Sie dann auf den Ordner **Zuweisen von Benutzerrechten** .  
  
4.  Klicken Sie mit der rechten Maustaste auf eine Berechtigung, die Sie zur Verwendung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfigurieren möchten, und wählen Sie **Eigenschaften**aus.  
  
5.  Überprüfen Sie im Eigenschaftendialogfeld der Berechtigung, ob das Konto aufgeführt ist, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird. Falls dies nicht der Fall ist, klicken Sie auf **Benutzer oder Gruppe hinzufügen**, geben Sie im Dialogfeld zum Auswählen von Benutzern, Computern, Dienstkonten oder Gruppen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**das Konto ein, unter dem der** -Agent ausgeführt wird, und klicken Sie dann auf **OK**.  
  
6.  Wiederholen Sie diese Schritte für jede Berechtigung, die Sie für die Ausführung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent hinzufügen möchten. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
