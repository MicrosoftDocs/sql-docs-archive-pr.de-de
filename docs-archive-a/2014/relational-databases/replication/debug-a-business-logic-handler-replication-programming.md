---
title: Debuggen eines Geschäftslogik Handlers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b255407783b1e52a376e562ec910f8b123e42c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609142"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a>Debuggen eines Geschäftslogikhandlers (Replikationsprogrammierung)
  Verwenden Sie einen Geschäftslogikhandler, um eine benutzerdefinierte Geschäftslogik aufzurufen, wenn ein Mergeabonnement synchronisiert wird. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](merge/execute-business-logic-during-merge-synchronization.md).  
  
 Die Mergereplikationssynchronisierung (replrec.dll) ruft die Assembly mit verwaltetem Code auf, die die Geschäftslogik enthält. In den meisten Fällen werden die Datei replrec.dll und die benutzerdefinierte Geschäftslogik auf dem Computer ausgeführt, auf dem der Merge-Agent ausgeführt wird (bei einem Pullabonnement auf dem Abonnenten und bei einem Pushabonnement auf dem Verteiler). Bei der Websynchronisierung oder bei einem [!INCLUDE[ssEW](../../includes/ssew-md.md)] -Abonnenten werden die Synchronisierung und die benutzerdefinierte Geschäftslogik auf dem Webserver ausgeführt.  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a>So debuggen Sie einen Geschäftslogikhandler auf einem lokalen Computer  
  
1.  Konfigurieren Sie die Veröffentlichung und Verteilung, erstellen Sie eine Veröffentlichung, und erstellen Sie ein Abonnement für die Veröffentlichung. Weitere Informationen finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md) und [Create a Publication (Erstellen einer Veröffentlichung)](publish/create-a-publication.md).  
  
2.  Erstellen und registrieren Sie einen Geschäftslogikhandler. Weitere Informationen finden Sie unter [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  Erstellen Sie ein RMO-Projekt (Replication Management Objects, Replikationsverwaltungsobjekte) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, das den Merge-Agent programmgesteuert synchron startet. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
4.  Legen Sie, entweder in der zu debuggenden Methode oder im Klassenkonstruktor, einen Breakpoint im Code des Geschäftslogikhandlers fest. Weitere Informationen zu den Methoden, die in einem Geschäftslogikhandler implementiert werden können, finden Sie in den Themen zu den <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Methoden.  
  
5.  Erstellen Sie den Geschäftslogikhandler im Debugmodus, und stellen Sie die Assembly und die Debugsymboldatei (PDB-Datei) an dem Speicherort bereit, der in Schritt 1 registriert wurde.  
  
    > [!NOTE]  
    >  Um den Debugvorgang zu vereinfachen, erstellen Sie eine einzelne Visual Studio .NET-Lösung, die sowohl das Projekt für den Geschäftslogikhandler als auch das Projekt enthält, das das Abonnement synchronisiert. Legen Sie das Synchronisierungsprojekt in diesem Fall als Startprojekt fest, und konfigurieren Sie die Buildumgebung so, dass die Geschäftslogikassembly an dem Speicherort bereitgestellt wird, der in Schritt 1 beim Debuggen registriert wurde.  
  
6.  Führen Sie Einfüge-, Update- oder Löschbefehle an der Abonnement- oder Veröffentlichungsdatenbank aus. Der Speicherort für Befehle und Ausführung hängt von der Methode ab, die gedebuggt wird.  
  
7.  Starten Sie das Projekt aus Schritt 3 im Debugmodus, um das Abonnement zu synchronisieren.  
  
8.  Die Ausführung stoppt, wenn sie den Breakpoint im Geschäftslogikhandler erreicht, falls keine anderen Breakpoints festgelegt und die richtigen Befehle repliziert wurden.  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a>So debuggen Sie einen Geschäftslogikhandler auf einem Webserver mit der Websynchronisierung oder für einen Abonnenten von SQL Server Compact  
  
1.  Konfigurieren Sie die Veröffentlichung und Verteilung, erstellen Sie eine Veröffentlichung, und erstellen Sie ein Pullabonnement für die Veröffentlichung. Die Veröffentlichung muss die Websynchronisierung oder Abonnenten von [!INCLUDE[ssEW](../../includes/ssew-md.md)] unterstützen.  
  
2.  Erstellen und registrieren Sie einen Geschäftslogikhandler. Weitere Informationen finden Sie unter [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  Legen Sie, entweder in der zu debuggenden Methode oder im Klassenkonstruktor, einen Breakpoint im Code des Geschäftslogikhandlers fest. Weitere Informationen zu den Methoden, die in einem Geschäftslogikhandler implementiert werden können, finden Sie in den Themen zu den <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> -Methoden.  
  
4.  Erstellen Sie den Geschäftslogikhandler im Debugmodus, und stellen Sie die Assembly und die Debugsymboldatei (PDB-Datei) auf dem Webserver an dem Speicherort bereit, der in Schritt 1 registriert wurde.  
  
    > [!NOTE]  
    >  Falls der Geschäftslogikhandler nicht erstellt werden kann, weil die Assembly verwendet wird, geben Sie den Befehl `iisreset` an der Eingabeaufforderung auf dem Webserver ein, um den Webserver zurückzusetzen.  
  
5.  Synchronisieren Sie das Abonnement mit aktivierter Websynchronisierung. Während der Synchronisierung lädt der Webserver die registrierte Assembly.  
  
6.  Fügen Sie mit dem Debugger von Visual Studio .NET einen der folgenden Prozesse auf dem Webserver an.  
  
    -   w3wp.exe &ndash; Windows Server 2003.  
  
    -   inetinfo.exe &ndash; Windows 2000 und Windows XP.  
  
7.  Prüfen Sie im Fenster **Ausgabe** die Debugausgabe, um festzustellen, ob die Symbole für die registrierte Assembly ordnungsgemäß geladen wurden. Wenn die Symbole nicht geladen wurden, stellen Sie sicher, dass die richtige PDB-Datei in Schritt 4 kopiert wurde, und wiederholen Sie Schritt 5.  
  
8.  Führen Sie Einfüge-, Update- oder Löschbefehle an der Abonnement- oder Veröffentlichungsdatenbank aus. Der Speicherort für Befehle und Ausführung hängt von der Methode ab, die gedebuggt wird.  
  
9. Hängen Sie den w3wp.exe-Prozess mit dem Debugger von Visual Studio an.  
  
10. Synchronisieren Sie das Abonnement erneut mit der Websynchronisierung.  
  
11. Die Ausführung stoppt, wenn sie den Breakpoint im Geschäftslogikhandler erreicht, falls keine anderen Breakpoints festgelegt und die richtigen Befehle repliziert wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren eines Geschäftslogikhandlers für einen Mergeartikel](implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
