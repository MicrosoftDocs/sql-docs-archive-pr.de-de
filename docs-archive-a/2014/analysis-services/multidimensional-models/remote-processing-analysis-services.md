---
title: Remote Verarbeitung (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e0d6ade25f5a321e49c748692a961abc369efad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619406"
---
# <a name="remote-processing-analysis-services"></a>Remoteverarbeitung (Analysis Services)
  Sie können die geplante oder unbeaufsichtigte Verarbeitung auf einer Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ausführen, wobei die Verarbeitungsanforderung von einem Computer stammt, jedoch auf einem anderen Computer im selben Netzwerk ausgeführt wird.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Wenn Sie unterschiedliche Versionen von SQL Server auf den Computern ausführen, müssen die Clientbibliotheken mit der Version der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz übereinstimmen, die das Modell verarbeitet. Wenn die Verarbeitung zum Beispiel auf einer [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] -Instanz erfolgt, muss der Computer, von dem die Anforderung stammt, über die Clientbibliothek verfügen, die [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]entspricht. Weitere Informationen finden Sie unter [Für Analysis Services-Verbindungen verwendete Datenanbieter](../instances/data-providers-used-for-analysis-services-connections.md).  
  
-   Auf dem Remoteserver muss die Option **Remoteverbindungen mit diesem Computer zulassen** aktiviert sein, und das Konto, von dem die Verarbeitungsanforderung ausgegeben wird, muss als zulässiger Benutzer aufgeführt sein.  
  
-   Windows-Firewallregeln müssen so konfiguriert sein, dass eingehende Verbindungen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zulässig sind. Überprüfen Sie, dass Sie eine Verbindung mit der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]herstellen können. Siehe [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   Beheben Sie alle bestehenden lokalen Verarbeitungsprobleme, bevor Sie eine Remoteverarbeitung anwenden. Stellen Sie sicher, dass bei einer lokalen Verarbeitungsanforderung die Daten erfolgreich aus der externen relationalen Datenquelle abgerufen werden können. Anweisungen zum Angeben der Anmeldeinformationen für das Abrufen der Daten finden Sie unter [Festlegen von Identitätswechseloptionen &#40;SSAS – mehrdimensional&#41;](set-impersonation-options-ssas-multidimensional.md).  
  
## <a name="on-demand-remote-processing"></a>Bedarfsgesteuerte Remoteverarbeitung  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] akzeptiert Verarbeitungsanforderungen von Benutzer- oder Anwendungskonten mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administratorberechtigungen. Wenn Sie Administrator sind, stellen Sie sicher, dass Sie eine Verbindung zur Remoteinstanz herstellen und die Datenbank manuell über die Remoteverbindung verarbeiten können.  
  
1.  Starten Sie auf dem Computer, der zum Planen der Verarbeitung verwendet wird, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung zur Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Verarbeiten**aus, zeigen Sie auf **Skript** , und wählen Sie **Skript für Aktion in Fenster „Neue Abfrage“ schreiben**aus. Im Abfragefenster werden Befehle zum Aufrufen der Verarbeitung angezeigt.  
  
3.  Klicken Sie auf **OK** , um mit der Verarbeitung zu beginnen.  
  
     Beim erfolgreichen Abschluss dieser Aufgabe erhalten Sie eine XMLA-Abfrage, die Sie in einen geplanten Auftrag einbetten können. Außerdem wird bestätigt, dass keine Verbindungsprobleme bestehen.  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a>Planen der Remoteverarbeitung mit dem SQL Server-Agent-Dienst  
 Standardmäßig wird der SQL Server-Agent-Dienst unter einem virtuellen Konto ausgeführt, wobei Netzwerkverbindungen über das Computerkonto hergestellt werden. Um zu vermeiden, dass einem Computerkonto Administratorrechte für die Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zugewiesen werden müssen, sollten Sie das SQL Server-Agent-Dienstkonto so ändern, dass es als ein Domänenbenutzerkonto mit geringsten Rechten ausgeführt wird.  
  
 Achten Sie darauf, dass Sie alle notwendigen Berechtigungen erteilen, einschließlich **sysadmin** -Rechte für die Datenbank-Engine-Instanz, die den Dienst bereitgestellt.  
  
 Verwenden Sie zum Festlegen von Berechtigungen die folgenden Links:  
  
-   [Konfigurieren des SQL Server-Agents](../../ssms/agent/configure-sql-server-agent.md)  
  
-   [SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) schlägt alternative feste Serverrollen vor, wenn das Gewähren von **sysadmin** -Berechtigungen nicht möglich ist.  
  
 Fahren Sie nach dem Konfigurieren der Kontoberechtigungen mit den folgenden Schritten fort.  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a>Gewähren von SSAS-Berechtigungen für den SQL Server-Agent-Kontoadministrator  
  
1.  Stellen Sie über [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung zur Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Servernamen, klicken Sie auf**Eigenschaften**, und klicken Sie dann auf **Sicherheit**.  
  
3.  Klicken Sie auf **Hinzufügen** , um das SQL Server-Agent-Konto hinzuzufügen.  
  
#### <a name="create-the-job"></a>Erstellen des Auftrags  
  
1.  Stellen Sie in Management Studio eine Verbindung zur lokalen Datenbank-Engine-Instanz her. Der SQL Server-Agent ist das letzte Element im Objekt-Explorer. Starten Sie den Dienst bei Bedarf.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Auftrag**, klicken Sie auf **Neuer Auftrag** , und geben Sie dann einen Namen ein.  
  
3.  Klicken Sie unter "Schritte" auf **Neu** , und geben Sie dann einen Namen ein.  
  
4.  Wählen Sie unter "Typ" die Option **SQL Server Analysis Services-Befehl**aus.  
  
5.  Geben Sie unter "Server" den Namen der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein.  
  
6.  Fügen Sie unter "Befehl" den XMLA-Befehl für die Verarbeitung der Datenbank ein. Dies ist das XMLA-Skript, das Sie im Überprüfungsschritt für die bedarfsgesteuerte Remoteverarbeitung generiert haben. Klicken Sie auf **OK** , um den Auftrag zu speichern.  
  
#### <a name="start-sql-server-profiler"></a>Starten von SQL Server Profiler  
  
1.  Starten Sie auf dem Remotecomputer den SQL Server Profiler. Stellen Sie eine Verbindung zur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz her, und klicken Sie auf **Ausführen** , um die Ablaufverfolgung mit den Standardereignissen zu starten.  
  
     Sie verwenden den SQL Server Profiler zum Überwachen der Verarbeitungsereignissen, während sie auftreten.  
  
2.  Optional können Sie die Ablaufverfolgungseigenschaften so festlegen, dass die Ablaufverfolgung an eine Datei oder eine Tabelle in einer Datenbank gesendet wird.  
  
#### <a name="run-the-job"></a>Ausführung des Auftrags.  
  
1.  Stellen Sie auf dem Computer, der zum Ausführen des Auftrags verwendet wird, sicher, dass der Auftrag den grundlegenden Vorgang durchführen kann. Erweitern Sie im Objekt-Explorer unter „SQL Server-Agent“ die Option **Aufträge**, klicken Sie mit der rechten Maustaste auf das Projekt, das Sie gerade erstellt haben, und klicken Sie auf **Auftrag starten bei Schritt**. Der Auftrag wird sofort gestartet. Sie können den Fortschritt im SQL Server Profiler überwachen.  
  
2.  Ändern Sie als letzten Schritt den Auftrag so, dass er nach einem von Ihnen definierten Zeitplan ausgeführt wird. Fügen Sie dabei alle notwendigen Warnungen oder Benachrichtigungen hinzu, die zum Verwalten des Auftrags erforderlich sind. Sie können das Verarbeitungsskript außerdem noch genauer konfigurieren oder mehrere Schritte im Auftrag erstellen, um Objekte einzeln zu verarbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent Komponenten](../../ssms/agent/sql-server-agent.md#Components)   
 [Planen von administrativen SSAS-Tasks mit SQL Server-Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)   
 [Batch Verarbeitung &#40;Analysis Services&#41;](batch-processing-analysis-services.md)   
 [Objekt Verarbeitung für mehrdimensionale Modelle](processing-a-multidimensional-model-analysis-services.md)   
 [Verarbeiten von Objekten &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
