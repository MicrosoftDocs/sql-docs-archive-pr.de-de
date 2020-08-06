---
title: Implementierung von untergeordneten Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4fa4fa7c523c55c595341c7aee6a530c5918a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698451"
---
# <a name="implementation-of-child-packages"></a>Implementierung von untergeordneten Paketen
  Wenn Sie mithilfe von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]den Lastenausgleich implementieren, werden die untergeordneten Pakete auf anderen Servern installiert, um die verfügbare CPU bzw. die Serverzeit zu nutzen. Für das Erstellen und Ausführen der untergeordneten Pakete sind die folgenden Schritte erforderlich:  
  
-   Entwerfen der untergeordneten Pakete.  
  
-   Verschieben der Pakete auf den Remoteserver.  
  
-   Erstellen eines Auftrags des SQL Server-Agents auf dem Remoteserver, der einen Schritt zum Ausführen des untergeordneten Pakets enthält.  
  
-   Testen und Debuggen des Auftrags des SQL Server-Agents und der untergeordneten Pakete.  
  
 Beim Entwerfen der untergeordneten Pakete sind die Entwurfsmöglichkeiten unbegrenzt. Dabei können Sie jede beliebige Funktionalität verwenden. Beim Zugriff des Pakets auf die Daten müssen Sie jedoch sicherstellen, dass der Server, mit dem das Paket ausgeführt wird, auf die Daten zugreifen kann.  
  
 Um das übergeordnete Paket zu identifizieren, das untergeordnete Pakete ausführt, klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] mit der rechten Maustaste auf das Paket in Projektmappen-Explorer, und klicken Sie dann auf **Einstiegspunktpaket**.  
  
 Nach dem Entwerfen der untergeordneten Pakete werden diese im nächsten Schritt auf den Remoteservern bereitgestellt.  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a>Verschieben des untergeordneten Pakets auf die Remoteinstanz  
 Es gibt mehrere Möglichkeiten zum Verschieben von Paketen auf andere Server. Es werden die folgenden zwei Methoden vorgeschlagen:  
  
-   Exportieren von Paketen mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   Bereitstellen von Paketen durch Erstellen eines Bereitstellungshilfsprogramms für das Projekt, in dem die bereitzustellenden Pakete enthalten sind, und anschließendes Ausführen des Paketinstallations-Assistenten zum Installieren der Pakete im Dateisystem bzw. in einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Paket Bereitstellung &#40;SSIS-&#41;](packages/legacy-package-deployment-ssis.md).  
  
 Sie müssen die Bereitstellung für jeden zu verwendenden Remoteserver wiederholen.  
  
## <a name="creating-the-sql-server-agent-jobs"></a>Erstellen der Aufträge des SQL Server-Agents  
 Nach dem Bereitstellen der untergeordneten Pakete auf verschiedenen Servern müssen Sie auf jedem Server, auf dem ein untergeordnetes Paket enthalten ist, einen Auftrag des SQL Server-Agents erstellen. Der Auftrag des SQL Server-Agents enthält einen Schritt zum Ausführen der untergeordneten Pakete beim Aufruf des Agentauftrags. Die Aufträge des SQL Server-Agents sind keine geplanten Aufträge. Sie führen die untergeordneten Pakete nur dann aus, wenn Sie vom übergeordneten Paket aufgerufen werden. Die Benachrichtigung über den Erfolg oder Misserfolg des Auftrags an das übergeordnete Paket spiegelt den Erfolg oder Misserfolg des Auftrags des SQL Server-Agents wider und gibt an, ob der Auftrag erfolgreich aufgerufen wurde. Die Benachrichtigung beinhaltet jedoch nicht den Erfolg oder Misserfolg des untergeordneten Pakets bzw. eine Benachrichtigung, ob das Paket ausgeführt wurde.  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a>Debuggen der Aufträge des SQL Server-Agents und der untergeordneten Pakete  
 Sie können die Aufträge des SQL Server-Agents und ihre untergeordneten Pakete testen, indem Sie eine der folgenden Methoden verwenden:  
  
-   Ausführen der einzelnen untergeordneten Pakete im SSIS-Designer, indem Sie auf **Debuggen**  /  **Starten ohne Debugging**klicken.  
  
-   Ausführen der einzelnen Aufträge des SQL Server-Agents auf dem Remotecomputer mithilfe von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], um sicherzustellen, dass die Pakete ausgeführt werden.  
  
 Weitere Informationen zur Fehlerbehebung bei der Ausführung von Paketen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Aufträgen finden Sie unter [SSIS-Paket wird nicht ausgeführt, wenn das SSIS-Paket von einem SQL Server-Agent-Auftrag abgerufen wird](https://support.microsoft.com/kb/918760) in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Knowledge Base für Support.  
  
 Vom SQL Server-Agent wird der Subsystemzugriff für einen Proxy überprüft und der Zugriff auf den Proxy jedes Mal gewährt, wenn der Auftragsschritt ausgeführt wird.  
  
 Sie können einen Proxy in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]erstellen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag zu [SSIS: Zugreifen auf Variablen in einem übergeordneten Paket](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)auf "andyleonard. Blog".  
  
-   Artikel [Paket ausführen (Task](../integration-services/control-flow/execute-package-task.md)).  
  
  
