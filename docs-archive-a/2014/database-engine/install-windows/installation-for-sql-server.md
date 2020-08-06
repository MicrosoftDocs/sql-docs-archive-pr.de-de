---
title: Installation für SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 62630400f276b00de8acfa875244558cdb39e47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697109"
---
# <a name="installation-for-sql-server-2014"></a>Installation für SQLServer 2014
 ## <a name="download-sql-server-2014-express"></a>[Download SQL Server 2014 Express](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **Vielen Dank, dass [Scott Hanselman](http://www.hanselman.com/) alle installerpaketverknüpfungen an einem Ort sammelt!**
  
  Der Installations-Assistent für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält eine einzelne Funktionsstruktur für die Installation aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   Verwaltungstools  
  
-   Konnektivitätskomponenten  
  
 Sie können jede Komponente einzeln installieren oder eine Kombination der oben aufgelisteten Komponenten auswählen. Informationen zu den in verfügbaren Editionen und Komponenten finden Sie unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Editionen und Komponenten von SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) und Features, [die von den Editionen von SQL Server 2014 unterstützt](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)werden. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist als 32- und 64-Bit-Edition verfügbar.
 
 **Probieren Sie es aus:**  
  
-   Sie haben ein Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2014 Service Pack 1 (SP1) bereits installiert ist. Weitere Informationen zu SQL Server 2014 (SP1) finden Sie unter [SQL Server 2014 Service Pack 1 Release Information](https://support.microsoft.com/kb/3058865).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Unabhängig davon, ob Sie die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder über die Eingabeaufforderung vornehmen, umfasst das Setup immer folgende Schritte:  
  
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)  
 Beschreibt, wie der Computer auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vorbereitet wird:  
  
-   Hardware- und Softwareanforderungen  
  
-   Anforderungen für die Systemkonfigurationsprüfung sowie Blockadefaktoren.  
  
-   Überlegungen zur Sicherheit.  
  
 [Installieren von SQL Server 2014](install-sql-server.md)  
 Beschreibt Installationsoptionen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Upgrade auf SQL Server 2014](upgrade-sql-server.md)  
 Beschreibt Optionen zum Aktualisieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Deinstallieren von SQL Server 2014](../../sql-server/install/uninstall-sql-server.md)  
 Beschreibt Verfahren zum Deinstallieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
 [SQL Server-Failoverclusterinstallation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 In diesem Abschnitt der Dokumentation zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup wird die Installation und Konfiguration von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclustern beschrieben.  
  
 [Installieren von SQL Server 2014-BI-Funktionen](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funktionen, die Teil der Microsoft BI-Plattform darstellen, sind [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]sowie mehrere Clientanwendungen, die zum Erstellen von oder Arbeiten mit analytischen Daten verwendet werden. In diesem Abschnitt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupdokumentation wird erläutert, wie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Themen zu Vorgehensweisen für die Installation](../../sql-server/install/installation-how-to-topics.md)  
 Enthält Links zu verfahrensspezifischen Themen für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit dem Installations-Assistenten, über die Eingabeaufforderung, unter Verwendung von Konfigurationsdateien sowie mithilfe von "SysPrep".  
  
 [Installieren Sie SQL Server BI-Funktionen mit SharePoint &#40;Power Pivot und Reporting Services&#41;](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 In diesem Abschnitt wird erläutert, wie Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen in einer SharePoint-Umgebung installieren. Es wird angegeben, welche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen für eine bestimmte Version oder Edition von SharePoint verfügbar sind. Außerdem umfasst der Abschnitt Installationsschritte für PowerPivot für SharePoint und Reporting Services im SharePoint-Modus.  
  
 [Installieren der SQL Server-Beispiele und -Beispieldatenbanken](https://sqlserversamples.codeplex.com/)  
 Beschreibt, wie Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Beispiele und -Beispieldatenbanken installieren und konfigurieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuerungen bei der SQL Server Installation](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
