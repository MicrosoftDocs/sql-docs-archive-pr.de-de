---
title: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], connections
- connections [Reporting Services], report server
- registering report servers
- report servers [Reporting Services], registering
ms.assetid: c875ff87-ee7d-443a-a702-bdb4b6c27c6e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 25f8ba668ba06fc47d25de1f7089ee5a0579801b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724437"
---
# <a name="connect-to-a-report-server-in-management-studio"></a>Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] stellt einen Objekt-Explorer bereit, mit dem Sie eine Verbindung zu einem beliebigen Server der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Familie herstellen und dessen Inhalte grafisch durchsuchen können. Für Reporting Services können Sie den Objekt-Explorer verwenden, um Folgendes durchzuführen:  
  
-   Aktivieren von Berichtsserverfunktionen.  
  
-   Festlegen von Serverstandards und Konfigurieren von Rollendefinitionen.  
  
-   Verwalten von ausgeführten Aufträgen.  
  
-   Verwalten von Auftragszeitplänen  
  
 Sie können eine Verbindung zu einem Berichtsserver, der im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, herstellen. Die Verbindungssyntax und die Vorgangsarten, die Sie durchführen können, variieren je nach Servermodus des Berichtsservers und Ihren Berechtigungen. Wenn Sie keine Verbindung zu einem Berichtsserver herstellen oder bestimmte Tasks nicht ausführen können, liegt dies möglicherweise daran, dass Sie über unzureichende Berechtigungen verfügen oder den Namen des Berichtsservers nicht korrekt angegeben haben. Weitere Informationen zu Berechtigungen und zur Verbindungssyntax finden Sie in der Tabelle am Ende dieses Themas.  
  
 Beachten Sie, dass Sie mit dem Objekt-Explorer den Berichtsserverinhalt nicht anzeigen oder verwalten können. Die Inhaltsverwaltung erfolgt über den Berichts-Manager, wenn der Berichtsserver im einheitlichen Modus ausgeführt wird, oder über eine SharePoint-Website, wenn der Berichtsserver im integrierten SharePoint-Modus ausgeführt wird.  
  
 Mit dem Objekt-Explorer können Sie Verbindungen zu mehreren Serverinstanzen im selben Arbeitsbereich herstellen, solange die Server in derselben Servergruppe registriert sind. Bevor Sie eine Verbindung mit einem Berichtsserver in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]herstellen können, muss der Server registriert werden. Wenn der Berichtsserver bereits registriert ist, können Sie diesen Schritt überspringen. Anweisungen zum Registrieren von Berichtsservern finden Sie am Ende dieses Themas.  
  
### <a name="to-connect-to-a-native-mode-report-server"></a>So stellen Sie eine Verbindung mit einem Berichtsserver im einheitlichen Modus her  
  
1.  Wenn der Objekt-Explorer noch nicht geöffnet ist, wählen Sie ihn im Menü Ansicht aus.  
  
2.  Klicken Sie auf **Verbinden** , um die Liste der Servertypen anzuzeigen, und wählen Sie dann **Reporting Services**.  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** den Namen der Berichtsserverinstanz ein. Die Namen von Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanznamen. Standardmäßig ist der Instanzname eines lokalen Berichtsservers der Computername. Wenn Sie den Berichts Server als benannte Instanz installiert haben, verwenden Sie diese Syntax, um den Server anzugeben: * \<servername> [ \\<instanceName \> ]*.  
  
4.  Wählen Sie den Authentifizierungstyp aus. Wenn Sie die Windows-Authentifizierung verwenden, müssen Sie die Verbindung mit Ihren Anmeldeinformationen herstellen. Wenn Sie die Standardauthentifizierung oder die Formularauthentifizierung auswählen, geben Sie das Konto und das Kennwort ein.  
  
5.  Klicken Sie auf **Verbinden**. Der Berichtsserver wird im Objekt-Explorer angezeigt.  
  
6.  Klicken Sie mit der rechten Maustaste auf den Serverknoten, um Systemeigenschaften und Standardeinstellungen für den Server festzulegen. Weitere Informationen finden Sie unter [Festlegen von Berichtsservereigenschaften (Management Studio)](set-report-server-properties-management-studio.md).  
  
### <a name="to-connect-to-a-sharepoint-integrated-mode-report-server"></a>So stellen Sie eine Verbindung mit einem Berichtsserver im integrierten SharePoint-Modus her  
  
1.  Wenn der Objekt-Explorer noch nicht geöffnet ist, wählen Sie ihn im Menü Ansicht aus.  
  
2.  Klicken Sie auf Verbinden , um die Liste der Servertypen anzuzeigen, und wählen Sie dann **Reporting Services**.  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** eine URL zu einer SharePoint-Website ein. Im folgenden Beispiel wird die Syntax veranschaulicht: http:// \<web server> /Sites/ \<site> .  
  
4.  Wählen Sie den Authentifizierungstyp aus. Wenn Sie die Windows-Authentifizierung verwenden, müssen Sie die Verbindung mit Ihren Anmeldeinformationen herstellen. Wenn Sie die Standardauthentifizierung oder die Formularauthentifizierung auswählen, geben Sie das Konto und das Kennwort ein.  
  
5.  Klicken Sie auf **Verbinden**. Der Berichtsserver wird im Objekt-Explorer angezeigt.  
  
6.  Klicken Sie mit der rechten Maustaste auf den Serverknoten, um Systemeigenschaften und Standardeinstellungen für den Server festzulegen. Weitere Informationen finden Sie unter [Festlegen von Berichtsservereigenschaften (Management Studio)](set-report-server-properties-management-studio.md).  
  
### <a name="to-register-a-report-server"></a>So registrieren Sie einen Berichtsserver  
  
1.  Wenn Sie keine Verbindung zu einem Berichtsserver herstellen können, verfügen Sie nicht über die Berechtigungen zum Zugriff darauf, oder er muss registriert werden. Klicken Sie zum Registrieren des Servers im Menü Ansicht auf **Registrierte Server** .  
  
2.  Klicken Sie auf das Symbol Reporting Services.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Reporting Services**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Serverregistrierung**. Das Dialogfeld **Neue Serverregistrierung** wird angezeigt.  
  
4.  Geben Sie für **Servername**einen Wert ein. Der einzugebende Wert ist abhängig vom Servermodus:  
  
    -   Geben Sie für einen Berichtsserver im einheitlichen Modus den Namen der Berichtsserverinstanz ein. Die Namen von Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanznamen. Standardmäßig ist der Instanzname eines lokalen Berichtsservers der Computername. Wenn Sie den Berichts Server als benannte Instanz installiert haben, verwenden Sie diese Syntax, um den Server anzugeben: * \<servername> [ \\<instanceName \> ]*.  
  
    -   Bei einem Server, der im integrierten SharePoint-Modus ausgeführt wird, müssen Sie eine Verbindung mit der SharePoint-Website herstellen, mit der der Berichtsserver verbunden ist. Die Verbindung mit der SharePoint-Website ist notwendig, damit Sie die Berechtigungsebenen überprüfen können, mit denen der Berichtsserverinhalt und die Berichtsservervorgänge gesteuert werden. Sie können eine beliebige Site in der Siteauflistung angeben. Das folgende Beispiel veranschaulicht die Syntax: http://mysharepointsite.  
  
5.  Wählen Sie für **Authentifizierung**den Authentifizierungsmodus aus, der für den Zugriff auf den Webserver verwendet wird. Sie müssen den Authentifizierungsmodus auswählen, der bereits vom Berichtsserver verwendet wird.  
  
    -   Wenn Sie die Standardsicherheit verwenden, wählen Sie **Windows-Authentifizierung**aus.  
  
    -   Wenn eine benutzerdefinierte Sicherheitserweiterung installiert und bereitgestellt wurde, wählen Sie **Formularauthentifizierung**aus.  
  
    -   Wenn Sie den Berichtsserver für die Standardauthentifizierung konfiguriert haben, wählen Sie **Standardauthentifizierung**.  
  
    -   Wenn der Berichtsserver für den integrierten SharePoint-Modus konfiguriert ist, wählen Sie **Windows-Authentifizierung**.  
  
6.  Klicken Sie auf **Testen** , um die Verbindung zu überprüfen.  
  
7.  Klicken Sie bei Aufforderung auf **OK**, und klicken Sie dann auf **Speichern**.  
  
## <a name="connection-syntax-and-permissions"></a>Verbindungssyntax und Berechtigungen  
 In der folgenden Tabelle werden die Verbindungssyntax, Vorgänge und Berechtigungen zusammengefasst, die zum Ausführen bestimmter Vorgänge erforderlich sind.  
  
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als Servertyp im Dialogfeld **Verbindung mit Server herstellen** angeben, können Sie einen Berichtsservernamen oder einen Endpunkt zum Webdienst festlegen.  
  
|Verbinden mit|Aufgaben|Berechtigungen|  
|----------------|-----------|-----------------|  
|Berichtsserver im einheitlichen Modus, verbunden als Standard- oder benannte Instanz:<br /><br /> \<server name>\<_instance><br /><br /> Die Verbindung zum Berichtsserver wird durch den Berichtsserver-WMI-Anbieter hergestellt.|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Gemeinsame Zeitpläne erstellen und verwalten.<br /><br /> Rollendefinitionen erstellen, ändern oder löschen.|Der Systemadministratorrolle zugewiesen.|  
|Berichtsserver im einheitlichen Modus, verbunden als Standard- oder benannte Instanz über den Endpunkt zum Report Server-Webdienst:<br /><br /> http:// \<servername> /ReportServer<br /><br /> Das Angeben einer URL zum Berichtsserver ist eine alternative Möglichkeit, eine Verbindung mit dem Berichtsserver herzustellen.|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Gemeinsame Zeitpläne erstellen und verwalten.<br /><br /> Rollendefinitionen erstellen, ändern oder löschen.|Der Systemadministratorrolle zugewiesen.|  
|Berichtsserver im integrierten SharePoint-Modus, konfiguriert über die SharePoint-Website:<br /><br /> http://\<webserver>/\<SharePointSite>|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.<br /><br /> Gemeinsame Zeitpläne, die für die verbundene Website definiert sind, erstellen und verwalten.<br /><br /> Berechtigungsstufen für die verbundene Website anzeigen.|Berechtigungs-Vollzugriffsebene für die verbundene SharePoint-Website.|  
|Berichtsserver im integrierten SharePoint-Modus, verbunden über den Namen der Berichtsserverinstanz:<br /><br /> \<server name>\<_instance>|Servereigenschaften und -standardeinstellungen anzeigen und festlegen.<br /><br /> Aufträge anzeigen und abbrechen.|Berechtigungs-Vollzugriffsebene für die SharePoint-Website, die in den Berichtsserver integriert ist.<br /><br /> Beachten Sie, dass bei der Verbindung mit dem Berichtsserver statt mit der SharePoint-Website die Anzahl der Tasks, die Sie durchführen können, erheblich reduziert ist. Dies ist darauf zurückzuführen, dass der Berichtsserver nur Anwendungsdaten zurückgeben kann, die in der Berichtsserver-Datenbank gespeichert oder verwaltet werden, jedoch nicht auf die in den SharePoint-Konfigurations- und -Inhaltsdatenbanken.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Reporting Services in SQL Server Management Studio (SSRS)](reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
