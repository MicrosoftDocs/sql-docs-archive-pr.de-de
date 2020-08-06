---
title: 'Vorgehensweise: Bereitstellen einer Datenverarbeitungserweiterung für einen Berichtsserver | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725294"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a>Gewusst wie: Bereitstellen einer Datenverarbeitungserweiterung für einen Berichtsserver
  Berichtsserver verwenden Datenverarbeitungserweiterungen zum Abrufen und Verarbeiten von Daten in gerenderten Berichten. Sie sollten Ihre Assembly für Datenverarbeitungserweiterungen auf dem Berichtsserver als private Assembly bereitstellen. Sie müssen auch einen Eintrag in der Konfigurationsdatei des Berichtsservers RSReportServer.config vornehmen.  
  
## <a name="procedures"></a>Prozeduren  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>So stellen Sie eine Assembly für Datenverarbeitungserweiterungen bereit  
  
1.  Kopieren Sie die Assembly aus dem Bereitstellungsverzeichnis in das BIN-Verzeichnis des Berichtsservers, auf dem Sie die Datenverarbeitungserweiterung verwenden möchten. Der Standard Speicherort für das bin-Verzeichnis des Berichts Servers lautet%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<*Instance Name*> \Reporting Services\ReportServer\bin.  
  
    > [!NOTE]  
    >  Dieser Schritt verhindert ein Upgrade auf eine neuere Instanz von SQL Server. Weitere Informationen finden Sie unter [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Nachdem die Assemblydatei kopiert wurde, öffnen Sie die Datei RSReportServer.config. Die Datei RSReportServer.config befindet sich im Verzeichnis "ReportServer". Sie müssen einen Eintrag in der Konfigurationsdatei für die Datei Ihrer Datenverarbeitungserweiterungsassembly vornehmen. Sie können die Konfigurationsdatei mit Visual Studio oder mit einem einfachen Text-Editor wie dem Microsoft-Editor öffnen.  
  
3.  Suchen Sie das `Data`-Element in der Datei RSReportServer.config. In folgendem Verzeichnis muss ein Eintrag für Ihre neu erstellte Datenverarbeitungserweiterung erstellt werden:  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Fügen Sie einen Eintrag für die Datenverarbeitungserweiterung hinzu. Der Eintrag sollte ein `Extension` Element mit Werten für `Name` und enthalten `Type` und könnte wie folgt aussehen:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     Der Wert für `Name` ist der eindeutige Name der Datenverarbeitungserweiterung. Der Wert für `Type` ist eine durch Trennzeichen getrennte Liste, die einen Eintrag für den vollqualifizierten Namespace der Klasse enthält, welche die Schnittstellen <xref:Microsoft.ReportingServices.Interfaces.IExtension> und <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> implementiert, gefolgt vom Namen der Assembly (ohne die Dateierweiterung .dll). Standardmäßig sind Datenverarbeitungserweiterungen sichtbar. Um eine Erweiterung in Benutzeroberflächen wie dem Berichts-Manager auszublenden, fügen Sie das `Visible`-Attribut zum `Extension`-Element hinzu und setzen es auf `false`.  
  
5.  Fügen Sie eine Codegruppe für die benutzerdefinierte Assembly hinzu, die die Berechtigung `FullTrust` für die Erweiterung erteilt. Hierzu fügen Sie die Codegruppe der rssrvpolicy.config Datei hinzu, die sich standardmäßig in%ProgramFiles%\Microsoft SQL Server \\<MSRS10_50 befindet. \<*Instance Name*> \Reporting Services\ReportServer. Die Codegruppe kann folgendermaßen aussehen:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 Die URL-Mitgliedschaft ist eine der vielen Mitgliedschaftsbedingungen, die Sie für die Datenverarbeitungserweiterung auswählen können. Weitere Informationen zur Codezugriffssicherheit in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] finden Sie unter [Sichere Entwicklung &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Überprüfen der Bereitstellung  
 Sie können prüfen, ob Ihre Datenverarbeitungserweiterung erfolgreich auf dem Berichtsserver bereitgestellt wurde, indem Sie die Webdienstmethode <xref:ReportService2010.ReportingService2010.ListExtensions%2A> verwenden. Sie können auch den Berichts-Manager öffnen und prüfen, ob die Erweiterung in der Liste der verfügbaren Datenquellen enthalten ist. Weitere Informationen zu Berichts-Manager und Datenquellen finden Sie unter [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von Datenverarbeitungserweiterungen](deploying-a-data-processing-extension.md)   
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
