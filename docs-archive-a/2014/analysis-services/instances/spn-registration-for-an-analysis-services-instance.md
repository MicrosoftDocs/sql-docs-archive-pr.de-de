---
title: SPN-Registrierung für eine Analysis Services Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9e78dc37-a3f0-415d-847c-32fec69efa8c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3146a581e3cc0b434d2e5b153718f1f31cd903d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725158"
---
# <a name="spn-registration-for-an-analysis-services-instance"></a>SPN-Registrierung für eine Analysis Services-Instanz
  Durch einen Dienstprinzipalnamen (Service Principal Name, SPN) wird eine Dienstinstanz in einer Active Directory-Domäne eindeutig identifiziert, wenn Kerberos zur gegenseitigen Authentifizierung von Client- und Dienstidentitäten verwendet wird. Ein SPN ist dem Anmeldekonto zugeordnet, unter dem die Dienstinstanz ausgeführt wird.  
  
 Bei Clientanwendungen, die über die Kerberos-Authentifizierung eine Verbindung mit Analysis Services herstellen, wird von den Analysis Services-Clientbibliotheken ein SPN erstellt. Dieser basiert auf der Verbindungszeichenfolge und anderen bekannten Variablen wie der Dienstklasse, die in der jeweiligen Analysis Services-Version fest definiert sind.  
  
 Damit die gegenseitige Authentifizierung funktioniert, müssen die vom Client erstellten SPNs einem SPN-Objekt für einen Active Directory-Domänencontroller (DC) entsprechen. Deshalb müssen möglicherweise mehrere SPNs für eine einzelne Analysis Services-Instanz registriert werden, um sämtliche Varianten abzudecken, wie der Hostname in einer Verbindungszeichenfolge von einem Benutzer angegeben werden kann. Beispielsweise benötigen Sie wahrscheinlich zwei SPNs, um sowohl den vollqualifizierten Domänennamen (FQDN) eines Servers als auch den kürzeren Computernamen zu unterstützen. Die richtige Registrierung des Analysis Services-SPNs ist wichtig für eine erfolgreiche Verbindung. Wenn der SPN nicht oder doppelt vorhanden ist bzw. ein falsches Format aufweist, tritt ein Verbindungsfehler auf.  
  
 Die SPN-Registrierung wird manuell vom Analysis Services-Administrator ausgeführt. Im Gegensatz zur SQL Server-Datenbank-Engine wird der SPN von Analysis Services beim Dienststart nie automatisch registriert. Die manuelle Registrierung ist erforderlich, wenn Analysis Services unter dem virtuellen Standardkonto, einem Domänenbenutzerkonto oder einem integriertem Konto (einschließlich einer Pro-Dienst-SID) ausgeführt wird.  
  
 Die SPN-Registrierung ist nicht erforderlich, wenn der Dienst unter einem vordefinierten, verwalteten Dienstkonto ausgeführt wird, das von einem Domänenadministrator erstellt wird. Je nach Funktionsumfang der Domäne können für die Registrierung eines SPNs Domänenadministratorberechtigungen erforderlich sein.  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos-Konfigurations-Manager für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** ist ein Diagnosetool zur Behebung Kerberos-bezogener Verbindungsprobleme bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Microsoft Kerberos-Konfigurations-Manager für SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
> [!TIP]  
>  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos-Konfigurations-Manager für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** ist ein Diagnosetool zur Behebung Kerberos-bezogener Verbindungsprobleme bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Microsoft Kerberos-Konfigurations-Manager für SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Wenn die SPN-Registrierung erforderlich ist](#bkmk_scnearios)  
  
 [SPN-Format für Analysis Services](#bkmk_SPNSyntax)  
  
 [SPN-Registrierung für ein virtuelles Konto](#bkmk_virtual)  
  
 [SPN-Registrierung für ein Domänenkonto](#bkmk_domain)  
  
 [SPN-Registrierung für ein integriertes Konto](#bkmk_builtin)  
  
 [SPN-Registrierung für eine benannte Instanz](#bkmk_spnNamed)  
  
 [SPN-Registrierung für einen SSAS-Cluster](#bkmk_spnCluster)  
  
 [SPN-Registrierung für SSAS-Instanzen, konfiguriert für den HTTP-Zugriff](#bkmk_spnHTTP)  
  
 [SPN-Registrierung für SSAS-Instanzen, die an festen Ports lauschen](#bkmk_spnFixedPorts)  
  
##  <a name="when-spn-registration-is-required"></a><a name="bkmk_scnearios"></a> Wann die SPN-Registrierung erforderlich ist  
 Jede Client Verbindung, die "SSPI = Kerberos" in der Verbindungs Zeichenfolge angibt, führt SPN-Registrierungsanforderungen für eine Analysis Services-Instanz ein.  
  
 Die SPN-Registrierung ist in folgenden Situationen erforderlich. Ausführlichere Informationen finden Sie unter [Configure Analysis Services for Kerberos constrained delegation](configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
-   Die Identitätsdelegierung ist erforderlich, um die Benutzeridentität von der Clientanwendung oder dem Dienst der mittleren Ebene an Analysis Services zu übertragen. Die Identitätsdelegierung wird normalerweise verwendet, wenn benutzerspezifische Berechtigungen oder Filter für bestimmte Objekte definiert werden.  
  
     Ein häufiges Szenario für die Identitätsdelegierung besteht darin, Dienste mittlerer Ebene, z. B. Excel Services oder Reporting Services, für die eingeschränkte Delegierung konfigurieren, damit beim Abrufen von Daten in Analysis Services eine Benutzeridentität angenommen werden kann. Um dieses Verhalten zu unterstützen, müssen Sie einen Analysis Services-SPN als Zieldienst bereitstellen, wenn Sie Excel Services oder Reporting Services für die eingeschränkte Delegierung konfigurieren.  
  
-   Analysis Services delegiert eine Benutzeridentität, wenn Daten aus einer relationalen SQL Server-Datenbank mithilfe des DirectQuery-Modus für tabellarische Datenbanken abgerufen werden. Dies ist das einzige Szenario, bei dem Analysis Services die Benutzeridentität an einen anderen Dienst delegiert.  
  
##  <a name="spn-format-for-analysis-services"></a><a name="bkmk_SPNSyntax"></a>SPN-Format für Analysis Services  
 Verwenden Sie **setspn** , um einen SPN zu registrieren. Unter neueren Betriebssystemen wird **setspn** als Systemhilfsprogramm installiert. Weitere Informationen finden Sie unter [SetSPN](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx).  
  
 In der folgenden Tabelle werden die einzelnen Bestandteile des Analysis Services-SPNs beschrieben.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Dienstklasse|MSOLAPSvc.3 identifiziert den Dienst als Analysis Services-Instanz. Die " .3" ist ein Verweis auf die Version des XMLA-over-TCP/IP Protokolls, das für Analysis Services-Übertragungen verwendet wird. Die Zahl hat keinen Bezug zur Produktversion. Daher ist MSOLAPSvc.3 die richtige Dienstklasse für SQL Server 2005, 2008, 2008, 2012 R2 und jede zukünftige Version von Analysis Services, bis das Protokoll selbst überarbeitet wird.|  
|Hostname|Identifiziert den Computer, auf dem der Dienst ausgeführt wird. Das kann ein vollqualifizierter Domänenname oder ein NetBIOS-Name sein. Sie sollten einen SPN für beide Namen registrieren.<br /><br /> Wenn Sie einen SPN für den NetBIOS-Namen eines Servers registrieren, sollten Sie anhand von `SetupSPN -S` doppelte Registrierungseinträge suchen. NetBIOS-Namen sind innerhalb einer Gesamtstruktur nicht unbedingt eindeutig, und eine doppelte SPN-Registrierung führt zu einem Verbindungsfehler.<br /><br /> Bei Analysis Services-Clustern mit Lastenausgleich sollte der Hostname dem virtuellen Namen entsprechen, der dem Cluster zugewiesen ist.<br /><br /> Ein SPN sollte nie anhand der IP-Adresse erstellt werden. Kerberos verwendet die DNS-Auflösungsfunktionen der Domäne. Das wird umgangen, indem eine IP-Adresse angegeben wird.|  
|Portnummer|Obwohl die Portnummer Teil der SPN-Syntax ist, geben Sie bei der Registrierung eines Analysis Services-SPNs nie eine Portnummer an. Der Doppelpunkt (:), der in der SPN-Standardsyntax normalerweise zur Angabe einer Portnummer dient, wird von Analysis Services für den Instanznamen verwendet. Bei einer Analysis Services-Instanz wird davon ausgegangen, dass der Port dem Standardport (TCP 2383) oder einem Port entspricht, der vom SQL Server-Browserdienst (TCP 2382) zugewiesen wird.|  
|Instanzname|Analysis Services ist ein replizierbarer Dienst, der mehrmals auf demselben Computer installiert werden kann. Jede Instanz wird über den Instanznamen identifiziert.<br /><br /> Dem Instanznamen wird ein Doppelpunkt (:) vorangestellt. Bei einem Hostcomputer mit dem Namen "SRV01" und der benannten Instanz "SSAS-Tabular" sollte der SPN beispielsweise "SRV01:SSAS-Tabular" lauten.<br /><br /> Beachten Sie, dass sich die Syntax zum Angeben einer benannten Analysis Services-Instanz von der Syntax unterscheidet, die von anderen SQL Server-Instanzen verwendet wird. Andere Dienste verwenden einen umgekehrten Schrägstrich (\), um den Instanznamen in einem SPN anzufügen.|  
|Dienstkonto|Dies ist das Startkonto des Windows-Diensts **MSSQLServerOLAPService** . Es kann sich um ein Windows-Domänenbenutzerkonto, ein virtuelles Konto, ein verwaltetes Dienstkonto (MSA) oder ein integriertes Konto handeln, wie z. B. Pro-Dienst-SID, NetworkService oder LocalSystem. Ein Windows-Domänen Benutzerkonto kann als Domäne \ Benutzer oder formatiert werden user@domain .|  
  
##  <a name="spn-registration-for-a-virtual-account"></a><a name="bkmk_virtual"></a> SPN-Registrierung für ein virtuelles Konto  
 Virtuelle Konten sind der Standardkontotyp für SQL Server-Dienste. Das virtuelle Konto ist **NT service\msolapservice** für eine Standard Instanz und **NT service\msolap $** \<instance-name> für eine benannte Instanz.  
  
 Wie der Name bereits aussagt, sind diese Konten nicht in Active Directory enthalten. Ein virtuelles Konto ist nur auf dem lokalen Computer vorhanden. Bei der Verbindung mit externen Diensten, Anwendungen oder Geräten wird die Verbindung über das lokale Computerkonto hergestellt. Wenn der SPN also für eine Analysis Services-Instanz registriert wird, die unter einem virtuellen Konto ausgeführt wird, handelt es sich tatsächlich um eine SPN-Registrierung für das Computerkonto.  
  
 **Beispielsyntax für eine Standardinstanz, die als "NT Service\MSOLAPService" ausgeführt wird**  
  
 In diesem Beispiel wird die **setspn** -Syntax für eine Analysis Services-Standardinstanz veranschaulicht, die unter dem virtuellen Standardkonto ausgeführt wird. In diesem Beispiel lautet der Computerhostname **AW-SRV01**. Wie bereits erwähnt, muss für die SPN-Registrierung das *Computerkonto* und nicht das virtuelle Konto **NT Service\MSOLAPService**angegeben werden.  
  
```  
Setspn -s MSOLAPSvc.3/AW-SRV01.AdventureWorks.com AW-SRV01  
```  
  
> [!NOTE]  
>  Denken Sie daran, zwei SPN-Registrierungen zu erstellen, eine für den NetBIOS-Hostnamen und einen zweiten für einen vollqualifizierten Domänennamen des Hosts. Unterschiedliche Clientanwendungen verwenden verschiedene Hostnamenskonventionen, wenn sie eine Verbindung mit Analysis Services herstellen. Durch die Erstellung beider SPN-Registrierungen wird sichergestellt, dass beide Versionen des Hostnamens berücksichtigt werden.  
  
 **Beispiel Syntax für eine benannte Instanz, die als NT service\msolap $ ausgeführt wird\<instance-name>**  
  
 In diesem Beispiel wird die **setspn** -Syntax für eine benannte Instanz veranschaulicht, die unter dem virtuellen Standardkonto ausgeführt wird. Der Computerhostname lautet in diesem Fall **AW-SRV02** und der Instanzname **AW-FINANCE**. Auch hier ist das für den SPN angegebene Computer Konto und nicht das virtuelle Konto **NT service\msolap $** \<instance-name> .  
  
```  
Setspn -s MSOLAPSvc.3/AW-SRV02.AdventureWorks.com:AW-FINANCE AW-SRV02  
```  
  
##  <a name="spn-registration-for-a-domain-account"></a><a name="bkmk_domain"></a>SPN-Registrierung für ein Domänen Konto  
 Üblicherweise wird zum Ausführen einer Analysis Services-Instanz ein Domänenkonto verwendet.  
  
 Für Analysis Services-Instanzen, die in einem Netzwerk oder Cluster mit Hardwarelastenausgleich ausgeführt werden, ist ein Domänenkonto erforderlich, wobei jede Instanz des Clusters unter demselben Domänenkonto ausgeführt wird.  
  
 **Beispielsyntax für eine Standardinstanz, die als Domänenbenutzer ausgeführt wird**  
  
 In diesem Beispiel wird die **setspn** -Syntax für eine Analysis Services-Standardinstanz veranschaulicht, die in der Domäne AdventureWorks unter dem Domänenbenutzerkonto **SSAS-Service**ausgeführt wird.  
  
```  
Setspn -s msolapsvc.3\AW-SRV01.Adventureworks.com AdventureWorks\SSAS-Service  
```  
  
> [!TIP]  
>  Überprüfen Sie, ob der SPN für den Analysis Services-Server erstellt wurde, indem Sie je nach SPN-Registrierung `Setspn -L <domain account>` oder `Setspn -L <machinename>`ausführen. In der Liste sollte "msolapsvc. 3/" angezeigt werden \<hostname> .  
  
##  <a name="spn-registration-for-a-built-in-account"></a><a name="bkmk_builtin"></a> SPN-Registrierung für ein integriertes Konto  
 Obwohl diese Vorgehensweise nicht empfohlen wird, sind ältere Analysis Services-Installationen manchmal für die Ausführung unter integrierten Konten wie Netzwerkdienst, Lokaler Dienst oder Lokales System konfiguriert.  
  
 **Beispielsyntax für eine Standardinstanz, die unter einem integrierten Konto ausgeführt wird**  
  
 Die SPN-Registrierung für einen Dienst, der unter einem integrierten Konto oder einer Pro-Dienst-SID ausgeführt wird, weist die gleiche SPN-Syntax wie für das virtuelle Konto auf. Verwenden Sie anstelle des Kontonamens das Computerkonto:  
  
```  
Setspn -s MSOLAPSvc.3/AW-SRV01.AdventureWorks.com AW-SRV01  
```  
  
##  <a name="spn-registration-for-a-named-instance"></a><a name="bkmk_spnNamed"></a>SPN-Registrierung für eine benannte Instanz  
 Für benannte Instanzen von Analysis Services werden dynamische Portzuweisungen verwendet, die vom SQL Server-Browserdienst erkannt werden. Registrieren Sie einen SPN bei Verwendung einer benannten Instanz sowohl für den SQL Server-Browserdienst als auch für die benannte Analysis Services-Instanz. Weitere Informationen finden Sie unter [Ein SPN für den SQL Server-Browser-Dienst ist erforderlich, wenn Sie eine Verbindung zu einer benannten Instanz von SQL Server Analysis Services oder von SQL Server herstellen](https://support.microsoft.com/kb/950599).  
  
 **SPN-Beispielsyntax für den SQL-Browserdienst, der als LocalService ausgeführt wird**  
  
 Der Name der Dienstklasse ist **MSOLAPDisco.3**. Dieser Dienst wird standardmäßig als NT AUTHORITY\LocalService ausgeführt, d. h., der SPN wurde für das Computerkonto registriert. In diesem Beispiel weist das Computerkonto den Namen **AW-SRV01**auf, der dem Computernamen entspricht.  
  
```  
Setspn -S MSOLAPDisco.3/AW-SRV01.AdventureWorks.com AW-SRV01  
```  
  
##  <a name="spn-registration-for-an-ssas-cluster"></a><a name="bkmk_spnCluster"></a>SPN-Registrierung für einen SSAS-Cluster  
 Bei Analysis Services-Failoverclustern sollte der Hostname dem virtuellen Namen entsprechen, der dem Cluster zugewiesen ist. Dies ist der SQL Server-Netzwerkname, der während des Setups von SQL Server angegeben wurde, wenn Sie Analysis Services auf einem vorhandenen WSFC installiert haben. Sie finden diesen Namen in Active Directory. Sie finden ihn auch auf **Failovercluster-Manager**  |  **Role**  |  Registerkarte Rollen**Ressourcen** . Der Servername auf der Registerkarte "Ressourcen" sollte als "virtueller Name" im SPN-Befehl verwendet werden.  
  
 **SPN-Syntax für einen Analysis Services-Cluster**  
  
```  
Setspn -s msolapsvc.3/<virtualname.FQDN > <domain user account>  
```  
  
 Beachten Sie, dass für Knoten in einem Analysis Services-Cluster der Standardport (TCP 2383) verwendet werden muss und dass die Knoten unter demselben Domänenbenutzerkonto ausgeführt werden müssen, sodass jeder Knoten über dieselbe SID verfügt. Weitere Informationen finden Sie unter [How to Cluster SQL Server Analysis Services](https://msdn.microsoft.com/library/dn736073.aspx) (in englischer Sprache).  
  
##  <a name="spn-registration-for-ssas-instances-configured-for-http-access"></a><a name="bkmk_spnHTTP"></a> SPN-Registrierung für SSAS-Instanzen, die für den HTTP-Zugriff konfiguriert sind  
 Je nach den Anforderungen der Lösung kann es erforderlich sein, Analysis Services für den HTTP-Zugriff zu konfigurieren. Wenn die Lösung IIS als Komponente der mittleren Ebene umfasst und die Kerberos-Authentifizierung von der Lösung vorausgesetzt wird, muss ein SPN ggf. manuell für IIS registriert werden. Weitere Informationen finden Sie unter "Konfigurieren der Einstellungen auf dem Computer, auf dem IIS ausgeführt wird" unter [Konfigurieren von SQL Server 2008 Analysis Services und SQL Server 2005 Analysis Services, um die Kerberos-Authentifizierung zu verwenden](https://support.microsoft.com/kb/917409).  
  
 Bei der SPN-Registrierung für die Analysis Services-Instanz macht es keinen Unterschied, ob eine Instanz für TCP oder HTTP konfiguriert ist. Wenn von IIS mithilfe der MSMDPUMP-ISAPI-Erweiterung eine Verbindung mit Analysis Services hergestellt wird, basiert diese immer auf TCP.  
  
 Das bedeutet, dass Sie bei der SPN-Registrierung die Anweisungen der vorherigen Abschnitte für Standardinstanzen oder benannte Instanzen verwenden können. Achten Sie beim Angeben des Hostnamens darauf, den Hostnamen zu verwenden, den Sie bei der Konfiguration des Dienstes für den HTTP-Zugriff in der Datei msmdpump.ini angegeben haben.  
  
 Weitere Informationen zum HTTP-Zugriff finden Sie unter [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
##  <a name="spn-registration-for-ssas-instances-listening-on-fixed-ports"></a><a name="bkmk_spnFixedPorts"></a>SPN-Registrierung für SSAS-Instanzen, die an Festlegungs Ports lauschen  
 Bei einer SPN-Registrierung für Analysis Services kann keine Portnummer angegeben werden. Wenn Sie Analysis Services als Standardinstanz installiert und für das Lauschen an einem festen Port konfiguriert haben, müssen Sie Analysis Services jetzt für das Lauschen am Standardport (TCP 2383) konfigurieren. Bei benannten Instanzen müssen Sie den SQL Server-Browserdienst und dynamische Portzuweisungen verwenden.  
  
 Eine Analysis Services-Instanz kann nur an einem einzelnen Port lauschen. Die Verwendung mehrerer Ports wird nicht unterstützt. Weitere Informationen zur Portkonfiguration finden Sie unter [Configure the Windows Firewall to Allow Analysis Services Access](configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft BI-Authentifizierung und Identitäts Delegierung](https://go.microsoft.com/fwlink/?LinkID=286576)   
 [Gegenseitige Authentifizierung mithilfe von Kerberos](https://go.microsoft.com/fwlink/?LinkId=299283)   
 [Konfigurieren von SQL Server 2008 Analysis Services und SQL Server 2005 Analysis Services für die Verwendung der Kerberos-Authentifizierung](https://support.microsoft.com/kb/917409)   
 [Setspn-Syntax für Dienst Prinzipal Namen (SPNs) (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx)   
 [Welchen SPN verwende ich, und wie erhalte ich ihn?](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx)   
 [Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx)   
 [Schritt-für-Schritt-Anleitung für Dienst Konten](https://technet.microsoft.com/library/dd548356\(WS.10\).aspx)   
 [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Verwenden von SPNs bei der Konfiguration von Webanwendungen, die auf Internetinformationsdienste gehostet werden](https://support.microsoft.com/kb/929650)   
 [Neues in Dienst Konten](https://technet.microsoft.com/library/dd367859\(WS.10\).aspx)   
 [Konfigurieren der Kerberos-Authentifizierung für SharePoint 2010-Produkte (Whitepaper)](https://technet.microsoft.com/library/ff829837.aspx)  
  
  
