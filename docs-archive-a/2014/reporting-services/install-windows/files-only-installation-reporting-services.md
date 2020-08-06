---
title: „Nur-Datei“-Installation (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ec5c595dce3e292d37117453ccbbc6d19f8b87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700832"
---
# <a name="files-only-installation-reporting-services"></a><span data-ttu-id="d8cf1-102">Ausschließliche Datei-Installation (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="d8cf1-102">Files-Only Installation (Reporting Services)</span></span>
  <span data-ttu-id="d8cf1-103">Die*Nur-Dateien-Installation* bezieht sich auf eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation, bei der Setup Folgendes ausführt: Die Ordnerstruktur für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Programmdateien wird erstellt, die Dateien werden auf den Datenträger kopiert, der Berichtsserverdienst wird auf dem lokalen Computer registriert, das Dienstkonto wird konfiguriert, die Dateien erhalten Berechtigungen für das Dienstkonto, und der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Anbieter wird registriert.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-103">*Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI provider.</span></span>  
  
 <span data-ttu-id="d8cf1-104">Eine Nur-Dateien-Installationsdatei umfasst folgende [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Funktionen: Berichtsserver-Dienst (hostet den Berichtsserver-Webdienst, Hintergrundverarbeitungsanwendung und Berichts-Manager), Berichts-Generator, das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationstool und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Befehlszeilenhilfsprogramme (rsconfig.exe, rskeymgmt.exe und rs.exe).</span><span class="sxs-lookup"><span data-stu-id="d8cf1-104">A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe).</span></span> <span data-ttu-id="d8cf1-105">Sie umfasst keine freigegebenen Funktionen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die zur Installation als separate Elemente angegeben werden müssen.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-105">It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which must be specified as separate items if you want to install them.</span></span>  
  
 <span data-ttu-id="d8cf1-106">Im Gegensatz zu anderen Installationsarten ist ein Berichtsserver, der ausschließlich mit Dateien installiert wird, nicht funktionsfähig, wenn das Setup beendet ist.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-106">In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished.</span></span> <span data-ttu-id="d8cf1-107">Eine zusätzliche Konfiguration ist nötig, damit der Berichtsserver mithilfe von [Konfigurations-Manager für Reporting Services (einheitlicher Modus)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) online geschaltet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-107">Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="when-to-select-files-only-installation-mode"></a><span data-ttu-id="d8cf1-108">Sinnvoller Einsatz einer ausschließlichen Datei-Installation</span><span class="sxs-lookup"><span data-stu-id="d8cf1-108">When to Select Files-Only Installation Mode</span></span>  
 <span data-ttu-id="d8cf1-109">Eine ausschließliche Datei-Installation muss ausgeführt werden, wenn:</span><span class="sxs-lookup"><span data-stu-id="d8cf1-109">A files-only installation must be performed when:</span></span>  
  
-   <span data-ttu-id="d8cf1-110">Sie eine Verbindung zwischen Berichtsserverinstanz und einer Remoteberichtsserver-Datenbank herstellen möchten</span><span class="sxs-lookup"><span data-stu-id="d8cf1-110">You want to connect the report server to a remote report server database.</span></span>  
  
-   <span data-ttu-id="d8cf1-111">Sie den Berichtsserver als benannte Instanz installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-111">You want to install the report server as a named instance.</span></span>  
  
-   <span data-ttu-id="d8cf1-112">Sie Anwendungserfordernisse haben, die benutzerdefinierte Einstellungen oder Funktionen umfassen, und wenn Sie Zeitpunkt und Art der Serverkonfiguration komplett steuern möchten.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-112">You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.</span></span>  
  
-   <span data-ttu-id="d8cf1-113">Installieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusters, der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]beinhaltet</span><span class="sxs-lookup"><span data-stu-id="d8cf1-113">Installing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="how-to-perform-a-files-only-installation"></a><span data-ttu-id="d8cf1-114">Vorgehensweise: Ausführen der ausschließlichen Datei-Installation</span><span class="sxs-lookup"><span data-stu-id="d8cf1-114">How to Perform a Files-Only Installation</span></span>  
 <span data-ttu-id="d8cf1-115">Die ausschließliche Datei-Installation ist die Standardvorgabe für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8cf1-115">Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d8cf1-116">Sie können die ausschließliche Datei-Installation über die Befehlszeile oder im Installations-Assistenten angeben.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-116">You can specify a files-only installation through the command line or in the Installation wizard.</span></span> <span data-ttu-id="d8cf1-117">Folgende Themen enthalten Schritt-für-Schritt-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="d8cf1-117">The following topics provide step-by-step instructions:</span></span>  
  
-   <span data-ttu-id="d8cf1-118">[Installieren Sie SQL Server 2014 aus dem Installations-Assistenten &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span><span class="sxs-lookup"><span data-stu-id="d8cf1-118">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="d8cf1-119">[Installieren Sie SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span><span class="sxs-lookup"><span data-stu-id="d8cf1-119">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
#### <a name="example-command-line-script"></a><span data-ttu-id="d8cf1-120">Beispiel eines Befehlszeilenskripts:</span><span class="sxs-lookup"><span data-stu-id="d8cf1-120">Example Command Line Script</span></span>  
 <span data-ttu-id="d8cf1-121">Aus Gründen der Klarheit umfasst das Beispiel den /RSINSTALLMODE = "FilesOnlyMode".</span><span class="sxs-lookup"><span data-stu-id="d8cf1-121">For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode".</span></span> <span data-ttu-id="d8cf1-122">Da der ausschließliche Dateimodus jedoch als Standardinstallationsmodus verwendet wird, können Sie diesen Schritt weglassen. Es erfolgt trotzdem eine ausschließliche Datei-Installation.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-122">However, because files-only mode is the default, you can omit this and still get a files-only mode installation.</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a><span data-ttu-id="d8cf1-123">Installations-Assistent</span><span class="sxs-lookup"><span data-stu-id="d8cf1-123">Installation Wizard</span></span>  
 <span data-ttu-id="d8cf1-124">Wenn Sie auf der Seite Funktionsauswahl die Option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auswählen, öffnet das Setup die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsseite, auf der Sie den Installationsmodus angeben können.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-124">When you select [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page that enables you to specify the installation mode.</span></span> <span data-ttu-id="d8cf1-125">Um anzugeben, dass nur Dateien installiert werden, wählen Sie auf der Seite **-Konfiguration die Option** Berichtsserver installieren, aber nicht konfigurieren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aus.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-125">To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8cf1-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d8cf1-126">See Also</span></span>  
 <span data-ttu-id="d8cf1-127">[Überprüfen einer Installation von Reporting Services](verify-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-127">[Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) </span></span>  
 <span data-ttu-id="d8cf1-128">[Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-128">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="d8cf1-129">[Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-129">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="d8cf1-130">[Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-130">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="d8cf1-131">[Reporting Services Installation im SharePoint-Modus &#40;SharePoint 2010 und SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-131">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="d8cf1-132">[Installieren des Reporting Services-Berichtsservers im einheitlichen Modus](install-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d8cf1-132">[Install Reporting Services Native Mode Report Server](install-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="d8cf1-133">Reporting Services-Tools</span><span class="sxs-lookup"><span data-stu-id="d8cf1-133">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  