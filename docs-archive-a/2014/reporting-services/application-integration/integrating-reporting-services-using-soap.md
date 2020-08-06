---
title: Integrieren von Reporting Services mit SOAP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b6fffd65b22900d7c505c4b50ec290b95fe9ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608411"
---
# <a name="integrating-reporting-services-using-soap"></a>Integrieren von Reporting Services mit SOAP
  Die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP-API verfügt über mehrere Webdienst-Endpunkte zum Entwickeln von benutzerdefinierten Berichtslösungen. Die Endpunkte lassen sich derzeit in zwei Kategorien unterteilen: Verwaltung und Ausführung. Die Verwaltungsfunktionen werden durch die Endpunkte <xref:ReportService2005>, <xref:ReportService2006> und <xref:ReportService2010> verfügbar gemacht. Mit dem <xref:ReportService2005>-Endpunkt wird ein Berichtsserver verwaltet, der im einheitlichen Modus konfiguriert ist, und mit dem <xref:ReportService2006>-Endpunkt wird ein Berichtsserver verwaltet, der für den integrierten SharePoint-Modus konfiguriert ist. Der <xref:ReportService2010>-Endpunkt führt die Funktionen von <xref:ReportService2005> und <xref:ReportService2006> zusammen und kann einen Berichtsserver verwalten, der entweder für den einheitlichen Modus oder integrierten SharePoint-Modus konfiguriert ist.  
  
> [!NOTE]  
>  Der <xref:ReportService2005>-Endpunkt und der <xref:ReportService2006>-Endpunkt sind in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] als veraltet markiert. Der <xref:ReportService2010>-Endpunkt schließt die Funktionen beider Endpunkte ein und beinhaltet zusätzliche Verwaltungsfunktionen.  
  
 Die Ausführungsfunktion wird durch den <xref:ReportExecution2005>-Endpunkt verfügbar gemacht und wird verwendet, wenn der Berichtsserver im einheitlichen Modus oder im integrierten SharePoint-Modus konfiguriert ist. Folgende Themen zeigen, wie diese Endpunkte für die Entwicklung von Berichtslösungen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-, SharePoint- und Webanwendungen verwendet werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden der SOAP-API in einer Windows-Anwendung](integrating-reporting-services-using-soap-windows-application.md)  
 Beschreibt, wie Sie die SOAP-API verwenden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine Windows-Umgebung zu integrieren  
  
 [Verwenden der SOAP-API in einer Webanwendung](integrating-reporting-services-using-soap-web-application.md)  
 Beschreibt, wie Sie die SOAP-API verwenden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine Webumgebung zu integrieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integrieren von Reporting Services in Anwendungen](../application-integration/integrating-reporting-services-into-applications.md)   
 [Berichtsserver-Webdienst](../report-server-web-service/report-server-web-service.md)   
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
