---
title: Konfigurieren der Windows-Firewall für den Analysis Services Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ports [Analysis Services]
- Windows Firewall [Analysis Services]
- firewall systems [Analysis Services]
ms.assetid: 7673acc5-75f0-4703-9ce2-87425ea39d49
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7d63b392148bf10a6b121dd4d201b7a7c61e0c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698853"
---
# <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a>Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen
  Ein unverzichtbarer erster Schritt beim Verfügbarmachen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] im Netzwerk besteht darin zu bestimmen, ob die Blockierung von Ports in einer Firewall aufgehoben werden muss. Bei den meisten Installationen müssen Sie mindestens eine eingehende Firewallregel erstellen, die Verbindungen mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zulässt.  
  
 Die Anforderungen für die Firewallkonfiguration sind je nach [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Installation unterschiedlich:  
  
-   Öffnen Sie TCP-Port 2383, wenn Sie eine Standardinstanz installieren oder einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Failovercluster erstellen.  
  
-   Öffnen Sie TCP-Anschluss 2382, wenn Sie eine benannte Instanz installieren. Für benannte Instanzen werden dynamische Portzuweisungen verwendet. Als Ermittlungsdienst für Analysis Services lauscht der SQL Server-Browserdienst an TCP-Port 2382 und leitet die Verbindungsanforderung an den derzeit von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwendeten Port um.  
  
-   Öffnen Sie TCP-Port 2382, wenn Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im SharePoint-Modus installieren, um [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 zu unterstützen. In [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 befindet sich die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz außerhalb von SharePoint. Eingehende Anforderungen für die benannte PowerPivot-Instanz stammen von SharePoint-Webanwendungen, die über eine Netzwerkverbindung verbunden sind, und erfordern einen geöffneten Port. Wie bei anderen benannten Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellen Sie eine eingehende Regel für den SQL Server-Browserdienst an TCP-Port 2382, um den Zugriff auf [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]zuzulassen.  
  
-   Öffnen Sie bei [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 keine Ports in der Windows-Firewall. Als SharePoint-Add-In verwendet der Dienst Ports, die für SharePoint konfiguriert sind, und stellt nur lokale Verbindungen mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz her, von der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenmodelle geladen und abgefragt werden.  
  
-   Verwenden Sie für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanzen, die auf Azure-Virtual Machines ausgeführt werden, Alternative Anweisungen zum Konfigurieren des Server Zugriffs. Weitere [Informationen finden Sie unter SQL Server Business Intelligence in Azure Virtual Machines](https://msdn.microsoft.com/library/windowsazure/jj992719.aspx).  
  
 Obwohl die Standard Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an TCP-Port 2383 lauscht, können Sie den Server so konfigurieren, dass er an einem anderen festgelegten Port lauscht und die Verbindung mit dem Server im folgenden Format herstellt: \<servername> : \<portnumber> .  
  
 Von einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz kann jeweils nur ein TCP-Port verwendet werden. Auf Computern, die über mehrere Netzwerkkarten oder mehrere IP-Adressen verfügen, lauscht [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bei allen IP-Adressen, die dem Computer zugewiesen sind oder ihm als Alias zur Verfügung stehen, an einem TCP-Port. Wenn Anforderungen zum Lauschen an mehreren Ports vorliegen, konfigurieren Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für den HTTP-Zugriff. Anschließend können Sie mehrere HTTP-Endpunkte für beliebige Ports einrichten. Weitere Informationen finden Sie unter [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Überprüfen der für Analysis Services verwendeten Port- und Firewalleinstellungen](#bkmk_checkport)  
  
-   [Konfigurieren der Windows-Firewall für eine Standardinstanz von Analysis Services](#bkmk_default)  
  
-   [Konfigurieren des Windows-Firewallzugriffs für eine benannte Instanz von Analysis Services](#bkmk_named)  
  
-   [Portkonfiguration für einen Analysis Services-Cluster](#bkmk_cluster)  
  
-   [Portkonfiguration für PowerPivot für SharePoint](#bkmk_powerpivot)  
  
-   [Verwenden eines festen Ports für eine Standardinstanz oder eine benannte Instanz von Analysis Services](#bkmk_fixed)  
  
 Weitere Informationen zu den Standardeinstellungen der Windows-Firewall und eine Beschreibung der TCP-Ports, die sich auf Datenbank-Engine, Analysis Services, Reporting Services und Integration Services auswirken, finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="check-port-and-firewall-settings-for-analysis-services"></a><a name="bkmk_checkport"></a>Überprüfen Sie die Port-und Firewalleinstellungen für Analysis Services  
 Unter Microsoft Windows-Betriebssystemen, die von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]unterstützt werden, ist die Windows Firewall standardmäßig aktiviert und blockiert Remoteverbindungen. Sie müssen manuell einen Port in der Firewall öffnen, um eingehende Anforderungen für Analysis Services zuzulassen. Das SQL Server-Setup führt diesen Schritt nicht aus.  
  
 Porteinstellungen werden in der Datei msmdsrv.ini und in SQL Server Management Studio auf der Seite Allgemeine Eigenschaften einer Analysis Services-Instanz angegeben. Wenn für `Port` eine positive ganze Zahl festgelegt wird, überwacht der Dienst einen festen Port. Wenn für `Port` der Wert 0 festgelegt wird, überwacht der Dienst den Port 2383, wenn es sich um die Standardinstanz handelt, oder einen dynamisch zugewiesenen Port, wenn es sich um eine benannte Instanz handelt.  
  
 Dynamische Portzuweisungen werden nur von benannten Instanzen verwendet. Der `MSOLAP$InstanceName`-Dienst ermittelt beim Start, welcher Port verwendet werden soll. Sie können die aktuell von einer benannten Instanz verwendete Portnummer auf folgende Weise ermitteln:  
  
-   Starten Sie den Task-Manager, und klicken Sie dann auf **Dienste** , um die PID von zu erhalten `MSOLAP$InstanceName`  
  
-   Führen Sie den Befehl `netstat -ao -p TCP` über die Befehlszeile aus, um die Informationen zum TCP-Port für diese PID anzuzeigen.  
  
-   Überprüfen Sie den Port mithilfe SQL Server Management Studio, und stellen Sie eine Verbindung mit einem Analysis Services Server im folgenden Format her: \<IPAddress> : \<portnumber> .  
  
 Auch wenn eine Anwendung einen bestimmten Port überwacht, können Verbindungen nicht erfolgreich hergestellt werden, wenn eine Firewall den Zugriff blockiert. Damit Verbindungen zu einer benannten Analysis Services-Instanz hergestellt werden können, müssen Sie die Blockierung des Zugriffs auf msmdsrv.exe oder den festen Port, den die Instanz überwacht, in der Firewall aufheben. In den übrigen Abschnitten in diesem Thema finden Sie Anweisungen zur Vorgehensweise.  
  
 Wenn Sie überprüfen möchten, ob bereits Firewalleinstellungen für Analysis Services definiert wurden, verwenden Sie die Windows-Firewall mit erweiterter Sicherheit in der Systemsteuerung. Im Ordner Überwachung auf der Seite Firewall wird eine vollständige Liste der für den lokalen Server definierten Regeln angezeigt.  
  
 Beachten Sie, dass alle Firewallregeln für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]manuell definiert werden müssen. Obwohl [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und der SQL Server-Browser die Ports 2382 und 2383 reservieren, definiert weder das SQL Server-Setupprogramm noch eines der Konfigurationstools Firewallregeln, die den Zugriff auf die Ports oder die ausführbaren Programmdateien zulassen.  
  
##  <a name="configure-windows-firewall-for-a-default-instance-of-analysis-services"></a><a name="bkmk_default"></a>Konfigurieren der Windows-Firewall für eine Standard Instanz von Analysis Services  
 Die Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lauscht an TCP-Port 2383. Wenn Sie die Standardinstanz installiert haben und diesen Port verwenden möchten, müssen Sie lediglich die Blockierung des eingehenden Zugriffs an TCP-Port 2383 in der Windows-Firewall aufheben, um den Remotezugriff auf die Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zuzulassen. Wenn Sie die Standardinstanz installiert haben, den Dienst jedoch für das Überwachen eines festen Ports konfigurieren möchten, lesen Sie [Verwenden eines festen Ports für eine Standardinstanz oder eine benannte Instanz von Analysis Services](#bkmk_fixed) in diesem Thema.  
  
 Überprüfen Sie den Dienstnamen im SQL Server-Konfigurations-Manager, um festzustellen, ob der Dienst als Standardinstanz (MSSQLServerOLAPService) ausgeführt wird. Eine Standardinstanz von Analysis Services wird immer als **SQL Server Analysis Services (MSSQLSERVER)** aufgelistet.  
  
> [!NOTE]  
>  Unter den verschiedenen Windows-Betriebssystemen werden unterschiedliche Tools für die Konfiguration der Windows-Firewall bereitgestellt. Bei den meisten Tools können Sie zwischen dem Öffnen eines bestimmten Ports und eines ausführbaren Programms wählen. Sofern Sie nicht einen besonderen Grund für die Angabe des ausführbaren Programms haben, wird empfohlen, den Port anzugeben.  
  
 Achten Sie beim Angeben einer eingehenden Regel darauf, eine Benennungskonvention zu verwenden, die es Ihnen ermöglicht, die Regeln später einfach zu finden (beispielsweise **SQL Server Analysis Services (TCP eingehend) 2383**).  
  
#### <a name="windows-firewall-with-advanced-security"></a>Windows-Firewall mit erweiterter Sicherheit  
  
1.  Klicken Sie unter Windows 7 oder Windows Vista in der Systemsteuerung auf **System und Sicherheit**, wählen Sie **Windows-Firewall**aus, und klicken Sie dann auf **Erweiterte Einstellungen**. Öffnen Sie unter Windows Server 2008 oder 2008 R2 die Administratortools, und klicken Sie auf **Windows-Firewall mit erweiterter Sicherheit**. Öffnen Sie unter Windows Server 2012 die Seite „Anwendungen“, und geben Sie **Windows-Firewall**ein.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Eingehende Regeln** , und wählen Sie **Neue Regel**aus.  
  
3.  Klicken Sie unter Regeltyp auf `Port` weiter, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie unter Protokoll und Ports die Option **TCP** aus, und geben Sie dann `2383` **bestimmte lokale Ports**ein.  
  
5.  Klicken Sie unter „Aktion“ auf **Verbindung zulassen** , und klicken Sie anschließend auf **Weiter**.  
  
6.  Löschen Sie unter „Profil“ alle nicht zutreffenden Netzwerkspeicherorte, und klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie unter Name einen beschreibenden Namen für diese Regel ein (z. b. `SQL Server Analysis Services (tcp-in) 2383` ), und klicken Sie dann auf **Fertig**stellen.  
  
8.  Um sicherzustellen, dass Remoteverbindungen aktiviert sind, öffnen Sie SQL Server Management Studio oder Excel auf einem anderen Computer, und stellen Sie eine Verbindung mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] her, indem Sie unter **Servername**den Netzwerknamen des Servers angeben.  
  
    > [!NOTE]  
    >  Andere Benutzer erhalten erst Zugriff auf diesen Server, wenn Sie Berechtigungen erteilen. Weitere Informationen finden Sie unter [Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md).  
  
#### <a name="netsh-advfirewall-syntax"></a>Syntax für "Netsh AdvFirewall"  
  
-   Mit dem folgenden Befehl wird eine eingehende Regel erstellt, die eingehende Anforderungen für TCP-Port 2383 zulässt.  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Analysis Services inbound on TCP 2383" dir=in action=allow protocol=TCP localport=2383 profile=domain  
    ```  
  
##  <a name="configure-windows-firewall-access-for-a-named-instance-of-analysis-services"></a><a name="bkmk_named"></a>Konfigurieren des Windows-firewallzugriffs für eine benannte Instanz von Analysis Services  
 Benannte Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lauschen entweder an einem festen Port oder einem dynamisch zugewiesenen Port, über den der SQL Server-Browserdienst die Verbindungsinformationen bereitstellt, die für den Dienst zur Zeit der Verbindung aktuell sind.  
  
 Der SQL Server-Browserdienst lauscht an TCP-Port 2382. UDP wird nicht verwendet. TCP ist das einzige von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwendete Übertragungsprotokoll.  
  
 Wählen Sie einen der folgenden Ansätze, um den Remotezugriff auf eine benannte Instanz von Analysis Services zu aktivieren:  
  
-   Verwenden Sie dynamische Portzuweisungen und den SQL Server-Browser-Dienst. Heben Sie die Blockierung für den vom SQL Server-Browser-Dienst verwendeten Port in der Windows-Firewall auf. Stellen Sie eine Verbindung mit dem Server im folgenden Format her: \<servername> \\<instanceName \> .  
  
-   Verwenden Sie gemeinsam einen festen Port und den SQL Server-Browser-Dienst. Bei diesem Ansatz können Sie die Verbindung mit diesem Format herstellen: \<servername> \\<instanceName \> , identisch mit dem Ansatz für die dynamische Port Zuweisung, mit dem Unterschied, dass der Server in diesem Fall einen festgelegten Port überwacht. In diesem Szenario stellt der SQL Server-Browser-Dienst die Namensauflösung für die Analysis Services-Instanz bereit, die den festen Port überwacht. Um diesen Ansatz zu verwenden, konfigurieren Sie den Server für die Überwachung eines festen Ports. Heben Sie anschließend den Zugriff für diesen Port sowie für den vom SQL Server-Browser-Dienst verwendeten Port auf.  
  
 Der SQL Server-Browser-Dienst wird nur mit benannten Instanzen verwendet, niemals mit der Standardinstanz. Der Dienst wird automatisch installiert und aktiviert, wenn Sie eine beliebige SQL Server-Funktion als benannte Instanz installieren. Wenn Sie einen Ansatz wählen, der den SQL Server-Browser-Dienst erfordert, achten Sie darauf, dass dieser auf dem Server aktiviert und gestartet bleibt.  
  
 Wenn Sie den SQL Server-Browserdienst nicht verwenden können, müssen Sie einen festen Port in der Verbindungszeichenfolge zuweisen, wodurch Sie die Auflösung des Domänennamens umgehen. Ohne SQL Server-Browser-Dienst müssen alle Clientverbindungen die Portnummer in der Verbindungszeichenfolge enthalten (z. B. AW-SRV01:54321).  
  
 **Option 1: Verwenden dynamischer Portzuweisungen und Aufheben der Blockierung des Zugriffs auf den SQL Server-Browser-Dienst**  
  
 Dynamische Portzuweisungen für benannte Instanzen von Analysis Services werden durch `MSOLAP$InstanceName` eingerichtet, wenn der Dienst gestartet wird. Standardmäßig beansprucht der Dienst die erste verfügbare Portnummer, die er findet. Der Dienst verwendet bei jedem erneuten Start eine andere Portnummer.  
  
 Die Instanznamensauflösung wird durch den SQL Server-Browserdienst vorgenommen. Das Aufheben der Blockierung von TCP-Port 2382 für den SQL Server-Browser-Dienst ist immer erforderlich, wenn Sie dynamische Portzuweisungen mit einer benannten Instanz verwenden.  
  
> [!NOTE]  
>  Der SQL Server-Browserdienst überwacht sowohl den UDP-Port 1434 als auch den TCP-Port 2382 für die Datenbank-Engine bzw. Analysis Services. Auch wenn Sie die Blockierung des UDP-Ports 1434 für den SQL Server-Browserdienst bereits aufgehoben haben, müssen Sie dennoch die Blockierung des TCP-Ports 2382 für Analysis Services aufheben.  
  
#### <a name="windows-firewall-with-advanced-security"></a>Windows-Firewall mit erweiterter Sicherheit  
  
1.  Klicken Sie unter Windows 7 oder Windows Vista in der Systemsteuerung auf **System und Sicherheit**, wählen Sie **Windows-Firewall**aus, und klicken Sie dann auf **Erweiterte Einstellungen**. Öffnen Sie unter Windows Server 2008 oder 2008 R2 die Administratortools, und klicken Sie auf **Windows-Firewall mit erweiterter Sicherheit**. Öffnen Sie unter Windows Server 2012 die Seite „Anwendungen“, und geben Sie **Windows-Firewall**ein.  
  
2.  Um die Blockierung des Zugriffs auf den SQL Server-Browser-Dienst aufzuheben, klicken Sie mit der rechten Maustaste auf **Eingehende Regeln** , und wählen Sie **Neue Regel**aus.  
  
3.  Klicken Sie unter Regeltyp auf `Port` weiter, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie unter Protokoll und Ports die Option **TCP** aus, und geben Sie dann `2382` **bestimmte lokale Ports**ein.  
  
5.  Klicken Sie unter „Aktion“ auf **Verbindung zulassen** , und klicken Sie anschließend auf **Weiter**.  
  
6.  Löschen Sie unter „Profil“ alle nicht zutreffenden Netzwerkspeicherorte, und klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie unter Name einen beschreibenden Namen für diese Regel ein (z. b. `SQL Server Browser Service (tcp-in) 2382` ), und klicken Sie dann auf **Fertig**stellen.  
  
8.  Um sicherzustellen, dass Remote Verbindungen aktiviert sind, öffnen Sie SQL Server Management Studio oder Excel auf einem anderen Computer, und stellen Sie eine Verbindung mit dem Analysis Services her, indem Sie den Netzwerknamen des Servers und den Instanznamen im folgenden Format angeben: \<servername> \\<instanceName \> . Beispielsweise lautet auf einem Server mit dem Namen **AW-SRV01** mit einer benannten Instanz von **Finanzen**der Servername **AW-SRV01\Finanzen**.  
  
 **Option 2: Verwenden eines festen Ports für eine benannte Instanz**  
  
 Alternativ können Sie einen festen Port zuweisen und anschließend die Blockierung des Zugriffs auf diesen Port aufheben. Dieser Ansatz bietet bessere Überwachungsmöglichkeiten als das Gewähren des Zugriffs auf die ausführbare Datei des Programms. Aus diesem Grund wird die Verwendung eines festen Ports als Ansatz für den Zugriff auf eine beliebige Instanz von Analysis Services empfohlen.  
  
 Um einen festen Port zuzuweisen, führen Sie die Anweisungen unter [Verwenden eines festen Ports für eine Standardinstanz oder eine benannte Instanz von Analysis Services](#bkmk_fixed) in diesem Thema aus, und kehren Sie dann zu diesem Abschnitt zurück, um den Port zulassen.  
  
#### <a name="windows-firewall-with-advanced-security"></a>Windows-Firewall mit erweiterter Sicherheit  
  
1.  Klicken Sie unter Windows 7 oder Windows Vista in der Systemsteuerung auf **System und Sicherheit**, wählen Sie **Windows-Firewall**aus, und klicken Sie dann auf **Erweiterte Einstellungen**. Öffnen Sie unter Windows Server 2008 oder 2008 R2 die Administratortools, und klicken Sie auf **Windows-Firewall mit erweiterter Sicherheit**. Öffnen Sie unter Windows Server 2012 die Seite „Anwendungen“, und geben Sie **Windows-Firewall**ein.  
  
2.  Um die Blockierung des Zugriffs auf Analysis Services aufzuheben, klicken Sie mit der rechten Maustaste auf **Eingehende Regeln** , und wählen Sie **Neue Regel**aus.  
  
3.  Klicken Sie unter Regeltyp auf `Port` weiter, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie unter „Protokoll und Ports“ die Option **TCP** aus, und geben Sie anschließend den festen Port unter **Bestimmte lokale Ports**ein.  
  
5.  Klicken Sie unter „Aktion“ auf **Verbindung zulassen** , und klicken Sie anschließend auf **Weiter**.  
  
6.  Löschen Sie unter „Profil“ alle nicht zutreffenden Netzwerkspeicherorte, und klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie unter Name einen beschreibenden Namen für diese Regel ein (z. b. `SQL Server Analysis Services on port 54321` ), und klicken Sie dann auf **Fertig**stellen.  
  
8.  Um sicherzustellen, dass Remote Verbindungen aktiviert sind, öffnen Sie SQL Server Management Studio oder Excel auf einem anderen Computer, und stellen Sie eine Verbindung mit dem Analysis Services her, indem Sie den Netzwerknamen des Servers und die Portnummer im folgenden Format angeben: \<servername> : \<portnumber> .  
  
#### <a name="netsh-advfirewall-syntax"></a>Syntax für "Netsh AdvFirewall"  
  
-   Mit den folgenden Befehlen werden eingehende Regeln erstellt, die die Blockierung des TCP-Ports 2382 für den SQL Server-Browser-Dienst sowie eines von Ihnen für die Analysis Services-Instanz angegebenen festen Ports aufheben. Sie können mit beiden Befehlen den Zugriff auf eine benannte Instanz von Analysis Services gewähren.  
  
     In diesem Beispielbefehl ist der Port 54321 der feste Port. Achten Sie darauf, diesen Port durch den auf Ihrem System tatsächlich verwendeten Port zu ersetzen.  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Analysis Services (tcp-in) on 54321" dir=in action=allow protocol=TCP localport=54321 profile=domain  
    ```  
  
    ```  
    netsh advfirewall firewall add rule name="SQL Server Browser Services inbound on TCP 2382" dir=in action=allow protocol=TCP localport=2382 profile=domain  
    ```  
  
##  <a name="use-a-fixed-port-for-a-default-or-named-instance-of-analysis-services"></a><a name="bkmk_fixed"></a>Verwenden Sie einen Fixed-Port für eine Standard Instanz oder eine benannte Instanz von Analysis Services  
 In diesem Abschnitt wird die Konfiguration von Analysis Services für die Überwachung eines festen Ports erläutert. Die Verwendung eines festen Ports ist üblich, wenn Sie Analysis Services als benannte Instanz installiert haben. Sie können diesen Ansatz jedoch auch verwenden, wenn durch Geschäfts- oder Sicherheitsanforderungen festgelegt ist, dass nicht standardmäßige Portzuweisungen verwendet werden.  
  
 Beachten Sie, dass durch die Verwendung eines festen Ports die Syntax der Verbindung für die Standardinstanz dahingehend geändert wird, dass Sie die Portnummer an den Servernamen anfügen müssen. Wenn Sie beispielsweise eine Verbindung mit einer lokalen Standardinstanz von Analysis Services herstellen möchten, die den Port 54321 in SQL Server Management Studio überwacht, müssen Sie in Management Studio im Dialogfeld Verbindung mit Server herstellen als Servernamen "localhost:54321" eingeben.  
  
 Wenn Sie eine benannte Instanz verwenden, können Sie einen festgelegten Port ohne Änderungen an der Angabe des Server namens zuweisen (insbesondere können Sie verwenden, um eine \<servername\instancename> Verbindung mit einer benannten Instanz herzustellen, die einen festgelegten Port überwacht). Dies funktioniert nur, wenn der SQL Server-Browser-Dienst ausgeführt wird und die Blockierung des Ports aufgehoben wurde, der überwacht wird. SQL Server-Browser Dienst stellt die Umleitung zum fixierten Port basierend auf bereit \<servername\instancename> . Solange Sie Ports sowohl für den SQL Server-Browserdienst als auch für die benannte Instanz von Analysis Services öffnen, die einen festen Port überwacht, löst der SQL Server-Browserdienst die Verbindung zu einer benannten Instanz auf.  
  
1.  Ermitteln Sie einen verfügbaren TCP/IP-Port, der verwendet werden soll.  
  
     Eine Liste reservierter und registrierter Ports, die nicht verwendet werden sollten, finden Sie unter [Portnummern (IANA)](https://go.microsoft.com/fwlink/?LinkID=198469). Um eine Liste der Ports anzuzeigen, die in Ihrem System bereits verwendet werden, öffnen Sie ein Fenster zur Eingabeaufforderung, und geben Sie `netstat -a -p TCP` ein, um eine Liste der TCP-Ports anzuzeigen, die im System geöffnet sind.  
  
2.  Nachdem Sie den zu verwendenden Port ermittelt haben, geben Sie den Port entweder durch Bearbeiten der `Port`-Konfigurationseinstellung in der Datei msmdsrv.ini oder in SQL Server Management Studio auf der Seite Allgemeine Eigenschaften einer Analysis Services-Instanz an.  
  
3.  Starten Sie den Dienst neu.  
  
4.  Konfigurieren Sie die Windows-Firewall so, dass die Blockierung des angegebenen TCP-Ports aufgehoben wird. Oder, wenn Sie einen festen Port für eine benannte Instanz verwenden, heben Sie die Blockierung des für die Instanz angegebenen TCP-Ports und des TCP-Ports 2382 für den SQL Server-Browserdienst auf.  
  
5.  Führen Sie eine Überprüfung durch, indem Sie eine lokale Verbindung herstellen (in Management Studio) und anschließend eine Remoteverbindung von einer Clientanwendung auf einem anderen Computer herstellen. Um Management Studio zu verwenden, stellen Sie eine Verbindung mit einer Analysis Services Standard Instanz her, indem Sie einen Servernamen im folgenden Format angeben: \<servername> : \<portnumber> . Geben Sie für eine benannte Instanz den Servernamen als \<servername> \\<instancename an \> .  
  
##  <a name="port-configuration-for-an-analysis-services-cluster"></a><a name="bkmk_cluster"></a>Port Konfiguration für einen Analysis Services Cluster  
 Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Failovercluster lauscht immer an TCP-Port 2383, unabhängig davon, ob er als Standardinstanz oder benannte Instanz installiert wurde. Bei der Installation in einem Windows-Failovercluster verwendet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keine dynamischen Portzuweisungen. Achten Sie darauf, TCP 2383 auf jedem Knoten zu öffnen, auf dem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im Cluster ausgeführt wird. Weitere Informationen zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Clustern finden Sie unter [Gewusst wie: Verwenden von SQL Server Analysis Services in einem Cluster](https://go.microsoft.com/fwlink/p/?LinkId=396548).  
  
##  <a name="port-configuration-for-powerpivot-for-sharepoint"></a><a name="bkmk_powerpivot"></a>Port Konfiguration für PowerPivot für SharePoint  
 Die Serverarchitektur für [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] unterscheidet sich je nach der verwendeten SharePoint-Version grundlegend.  
  
 **SharePoint 2013**  
  
 In SharePoint 2013 werden Anforderungen für Power Pivot-Datenmodelle, die anschließend auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz außerhalb der SharePoint-Umgebung geladen werden, von Excel Services umgeleitet. Die Verbindungen folgen einem typischen Muster, bei dem eine Analysis Services-Clientbibliothek auf einem lokalen Computer eine Verbindungsanforderung an eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Remoteinstanz im selben Netzwerk sendet.  
  
 Da [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] immer als benannte Instanz installiert wird, sollten Sie die Verwendung des SQL Server-Browserdiensts und dynamischer Portzuweisungen in Betracht ziehen. Wie bereits erwähnt, lauscht der SQL Server-Browserdienst bei Verbindungsanforderungen, die an benannte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen gesendet werden, an TCP-Port 2382. Folglich wird die Anforderung an den aktuellen Port umgeleitet.  
  
 Beachten Sie, dass Excel Services in SharePoint 2013 keine Unterstützung für Syntax bieten, mit der feste Portverbindungen definiert werden. Stellen Sie also sicher, dass auf den SQL Server-Browserdienst zugegriffen werden kann.  
  
 **SharePoint 2010**  
  
 Wenn Sie SharePoint 2010 verwenden, müssen Sie keine Ports in der Windows-Firewall öffnen. SharePoint öffnet die Ports nach Bedarf selbst, und Add-Ins wie PowerPivot für SharePoint werden innerhalb der SharePoint-Umgebung ausgeführt. Bei einer Installation von PowerPivot für SharePoint 2010 verwendet der PowerPivot-Systemdienst exklusiv die lokale Instanz des Diensts SQL Server Analysis Services (PowerPivot), die mit ihm auf dem gleichen Computer installiert ist. Dabei werden lokale Verbindungen und keine Netzwerkverbindungen verwendet, um auf den lokalen Analysis Services-Engine-Dienst zuzugreifen, der PowerPivot-Daten auf den SharePoint-Server lädt und sie abfragt und verarbeitet. Um Power Pivot-Daten von Client Anwendungen anzufordern, werden Anforderungen über Ports weitergeleitet, die durch das SharePoint-Setup geöffnet werden (insbesondere werden eingehende Regeln definiert, um den Zugriff auf SharePoint-80, SharePoint-zentral Administration V4, SharePoint-Webdienste und spusercodev4 zuzulassen zu ermöglichen). Da PowerPivot-Webdienste in einer SharePoint-Farm ausgeführt werden, reichen die SharePoint-Firewallregeln für den Remotezugriff auf PowerPivot-Daten in einer SharePoint-Farm aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Browser Dienst &#40;Datenbank-Engine und SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)   
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)   
 [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
  
