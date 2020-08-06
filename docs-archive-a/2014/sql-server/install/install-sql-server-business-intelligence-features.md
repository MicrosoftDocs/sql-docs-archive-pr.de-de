---
title: Installieren von SQL Server 2014-BI-Funktionen
ms.custom: ''
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.date: 10/24/2018
ms.technology: install
ms.openlocfilehash: 9770c8322e203231af6a964bcc9d7320a2ea22d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620171"
---
# <a name="install-sql-server-2014-bi-features"></a>Installieren von SQL Server 2014-BI-Funktionen

  Zu den SQL Server-Funktionen, die Teil der Microsoft Business Intelligence-Plattform sind, zählen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]sowie mehrere Clientanwendungen zum Erstellen von und Arbeiten mit analytischen Daten. Dieser Abschnitt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupdokumentation erklärt, wie diese Funktionen installiert werden.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können als eigenständige Server, in Konfigurationen für horizontales Skalieren oder als gemeinsame Dienstanwendungen in einer SharePoint-Farm installiert werden. Bei der Installation der Dienste in einer Farm werden BI-Funktionen aktiviert, die nur in SharePoint verfügbar sind, einschließlich [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint und [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], der neue interaktive Ad-hoc-Berichts-Designer von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , der auf [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] - oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbanken tabellarischer Modelle läuft.  
  
 Wenn Sie bereits mit den Installationsschritten für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder PowerPivot für SharePoint vertraut sind, können Sie zu den Prüflisten übergehen, die Anhaltspunkte für die Aktivierung bestimmter Szenarien enthalten. Weitere Informationen finden Sie unter [Checklisten für die Installation von BI-Funktionen mit SharePoint](checklists-for-installing-bi-features-with-sharepoint.md).  
  
## <a name="contents"></a>Inhalte

Inhalt dieses Abschnitts:
  
|Link|Aufgabe|  
|----------|----------|  
|[Prüflisten zum Installieren von BI-Features mit SharePoint](checklists-for-installing-bi-features-with-sharepoint.md)|Wenn Sie bereits wissen, was Sie installieren möchten und mit den Installationsschritten für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint vertraut sind, können Sie zu den Prüflisten übergehen, die Anhaltspunkte für die Installationsreihenfolge, Anforderungen für Konten und Berechtigungen sowie die Schritte zur Bereitstellung erweiterter Technologien (einschließlich Bereitstellungen mit mehreren Servern und Funktionen) enthalten.|  
|[Installieren Sie SQL Server BI-Funktionen mit SharePoint &#40;Power Pivot und Reporting Services&#41;](install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)|In diesem Abschnitt wird erläutert, wie Sie SQL Server-Funktionen in einer SharePoint-Umgebung installieren. Es wird aufgezeigt, welche SQL Server-Funktionen für eine bestimmte Version oder Edition von SharePoint verfügbar sind. Außerdem umfasst der Abschnitt Installationsschritte für PowerPivot für SharePoint und Reporting Services im SharePoint-Modus.|  
|[Installieren von Analysis Services im mehrdimensionalen Modus und im Data Mining-Modus](install-analysis-services-in-multidimensional-and-data-mining-mode.md)<br /><br /> [Installieren von Analysis Services im Tabellenmodus](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)<br /><br /> [Installieren von Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)<br /><br /> [Installieren von Integration Services](../../integration-services/install-windows/install-integration-services.md)<br /><br /> [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)<br /><br /> [Installieren des Reporting Services-Berichtsservers im einheitlichen Modus](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)|Dieser Abschnitt enthält Anweisungen zum Installieren von Analysis Services, Integration Services, Master Data Services und Reporting Services, wo Analysis Services und Reporting Services ohne SharePoint installiert sind. Dies wird manchmal als einheitlicher *Modus*bezeichnet und ist das gängigste Installationsszenario für Reporting Services und Analysis Services. In diesem Abschnitt erfahren Sie mehr über Installationsoptionen, die direkten Einfluss auf den operativen Kontext des Servers nehmen. Im Fall von Reporting Services könnte dies ein vorkonfigurierter Server oder ein Server sein, der mehrere Konfigurationsschritte erfordert, bevor er eingesetzt werden kann. Bei Analysis Services hängt es von den ausgewählten Installationsoptionen ab, welchen Projekttyp Sie auf dem Server bereitstellen können.|  
|[Überprüfen oder Behandeln von Installationsproblemen der SQL Server-BI-Funktion](../../../2014/sql-server/install/verify-or-troubleshoot-sql-server-bi-feature-installation-problems.md)|Dieser Abschnitt enthält Schritte zum Überprüfen einer Installation. Außerdem finden Sie hier Links zu Problemlösungen im Internet.|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
|Link|Aufgabe|  
|----------|----------|  
|[Upgrade auf SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)<br /><br /> [Aktualisieren von Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)<br /><br /> [Upgraden von PowerPivot für SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)<br /><br /> [Aktualisieren und Migrieren von Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)|Verwenden Sie die Anweisungen in diesem Abschnitt, um Server und Inhalte von einer früheren Version auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zu aktualisieren.|  
|[Deinstallieren von SQL Server 2014](uninstall-sql-server.md)<br /><br /> [Deinstallieren von PowerPivot für SharePoint](../../../2014/sql-server/install/uninstall-power-pivot-for-sharepoint.md)<br /><br /> [Deinstallieren von Reporting Services](../../../2014/sql-server/install/uninstall-reporting-services.md)|Verwenden Sie die Anweisungen in diesem Abschnitt, um BI-Funktionen zu deinstallieren.|  
  
## <a name="see-also"></a>Weitere Informationen

* [Neues &#40;Reporting Services&#41;](../../../2014/reporting-services/what-s-new-reporting-services.md)

* [Neues in Analysis Services und Business Intelligence](https://docs.microsoft.com/analysis-services/what-s-new-in-analysis-services)

* [Installieren von SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)

* [Upgrade auf SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)
