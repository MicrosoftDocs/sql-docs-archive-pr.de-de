---
title: Öffnen des Protokolldatei-Viewers | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616533"
---
# <a name="open-log-file-viewer"></a>Öffnen des Protokolldatei-Viewers
  Sie können mithilfe des Protokolldatei-Viewers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf Informationen zu Fehlern und Ereignissen zugreifen, die in folgenden Protokollen aufgezeichnet wurden:  
  
-   Überwachungsauflistung  
  
-   Datensammlung  
  
-   Datenbank-E-Mail  
  
-   Auftragsverlauf  
  
-   SQL Server  
  
-   SQL Server-Agent  
  
-   Windows-Ereignisse (auf diese Windows-Ereignisse kann auch mithilfe der Ereignisanzeige zugegriffen werden)  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Protokolldateien aus lokalen oder Remoteinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit der Option Registrierte Server anzeigen. Mit Registrierte Server können Sie die Protokolldateien unabhängig davon anzeigen, ob diese online oder offline sind. Weitere Informationen zu Onlinezugriff finden Sie weiter unten in diesem Thema in der Vorgehensweise "So zeigen Sie Onlineprotokolldateien von registrierten Servern an". Weitere Informationen über den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Offlineprotokolldateien finden Sie unter [Anzeigen von Offlineprotokolldateien](view-offline-log-files.md).  
  
 Sie können den Protokolldatei-Viewer auf mehrere Arten öffnen, je nach anzuzeigenden Informationen.  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> Berechtigungen  
 Zum Zugreifen auf Protokolldateien für Onlineinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen Sie Mitglied der festen Serverrolle „securityadmin“ sein.  
  
 Zum Zugreifen auf Protokolldateien für Offlineinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] müssen Sie über Lesezugriff für den WMI-Namespace **Root\Microsoft\SqlServer\ComputerManagement10** und den Ordner mit den Protokolldateien verfügen. Weitere Informationen finden Sie im Abschnitt „Sicherheit“ des Themas [Anzeigen von Offlineprotokolldateien](view-offline-log-files.md).  
  
### <a name="security"></a>Sicherheit  
 Erfordert die Mitgliedschaft in der festen Serverrolle securityadmin.  
  
### <a name="view-log-files"></a>Anzeigen von Protokolldateien  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a>So zeigen Sie Protokolle zu allgemeinen SQL Server-Aktivitäten an  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung**.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie mit der rechten Maustaste auf **SQL Server-Protokolle**, zeigen Sie auf **Sicht**und dann entweder auf **SQL Server-Protokoll** oder **SQL Server- und Windows-Protokoll**.  
  
    -   Erweitern Sie **SQL Server-Protokolle**, klicken Sie mit der rechten Maustaste auf eine der Protokolldateien, und klicken Sie dann auf **SQL Server-Protokoll anzeigen**. Sie können auch auf jede beliebige Protokolldatei doppelklicken.  
  
     Die Protokolle sind **Datenbank-E-Mail**, **SQL Server**, **SQL Server-Agent**und **Windows NT**-Ereignisse.  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a>So zeigen Sie Protokolle zu Aufträgen an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **SQL Server-Agent**, klicken Sie mit der rechten Maustaste auf **Aufträge**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
     Die Protokolle sind **Datenbank-E-Mail**, **Auftragsverlauf**und **SQL Server-Agent**.  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a>So zeigen Sie Protokolle zu Wartungsplänen an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Wartungspläne**, und klicken Sie dann auf **Verlauf anzeigen**.  
  
     Die Protokolle sind **Datenbank-E-Mail**, **Auftragsverlauf**, **Wartungspläne**, **Remotewartungspläne**und **SQL Server-Agent**.  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a>So zeigen Sie Protokolle zu Datensammlungen an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Datensammlung**, und klicken Sie dann auf **Protokolle anzeigen**.  
  
     Die Protokolle sind **Datensammlung**, **Auftragsverlauf**und **SQL Server-Agent**.  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a>So zeigen Sie Protokolle zu Datenbank-E-Mails an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Datenbank-E-Mail**, und klicken Sie dann auf **Datenbank-E-Mail-Protokoll anzeigen**.  
  
     Die Protokolle sind **Datenbank-E-Mail, Auftragsverlauf**, **Wartungspläne**, **Remotewartungspläne**, **SQL Server**, **SQL Server-Agent**und **Windows NT**-Ereignisse.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>So zeigen Sie Protokolle zu Überwachungsauflistungen an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **Sicherheit**, erweitern Sie **Überwachungen**, klicken Sie mit der rechten Maustaste auf eine Überwachung, und klicken Sie dann auf **Überwachungsprotokolle anzeigen**.  
  
     Die Protokolle sind **Überwachungsauflistung** und **Windows NT**.  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a>So zeigen Sie Protokolle zu Überwachungsauflistungen an  
  
-   Erweitern Sie im Objekt-Explorer den Knoten **Sicherheit**, erweitern Sie **Überwachungen**, klicken Sie mit der rechten Maustaste auf eine Überwachung, und klicken Sie dann auf **Überwachungsprotokolle anzeigen**.  
  
     Die Protokolle sind **Überwachungsauflistung** und **Windows NT**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Protokolldatei-Viewer](log-file-viewer.md)   
 [SQL Server Audit &#40;Datenbank-Engine&#41;](../security/auditing/sql-server-audit-database-engine.md)   
 [Anzeigen von Offlineprotokolldateien](view-offline-log-files.md)  
  
  
