---
title: Entwickler&#39;s Guide (Reporting Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf880db543c891a0ffccab932fddc614df34e17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719477"
---
# <a name="developer39s-guide-reporting-services"></a>Entwickler&#39;s Guide (Reporting Services)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält mehrere Programmierschnittstellen, die Sie in Ihre eigenen Anwendungen einbauen können. Sie können die vorhandenen Funktionen und Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verwenden, um benutzerdefinierte Berichts- und Verwaltungstools in Websites und Windows-Anwendungen zu erstellen, oder Sie können die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Plattform erweitern.  
  
 Das Erweitern der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Plattform umfasst die Erstellung neuer Komponenten und Ressourcen, die für den Datenzugriff, die Berichtsübermittlung und vieles mehr verwendet werden können. Sie können diese Komponenten und Ressourcen in den Unternehmen vermarkten, die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in ihrer Organisation verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Integration von Reporting Services in Anwendungen](application-integration/integrating-reporting-services-into-applications.md)  
 Gibt eine Übersicht darüber, wie die Berichterstellung mithilfe von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in benutzerdefinierte Anwendungen integriert werden kann. Beschreibt, wann der direkte URL-Zugriff und wann der Webdienst für den Zugriff auf den Berichtsserver verwendet werden sollte.  
  
 [Report Server Web Service (Report Server-Webdienst)](report-server-web-service/report-server-web-service.md)  
 Über den Berichtsserver-Webdienst erhalten Sie Zugriff auf die kompletten Funktionen des Berichtsservers. Der Webdienst verwendet SOAP über HTTP und wurde als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver konzipiert. Der Webdienst und seine Methoden stellen die Funktionen des Berichtsservers zur Verfügung und ermöglichen die Erstellung benutzerdefinierter Tools für jeden Teil des gesamten Berichtslebenszyklus, von der Verwaltung bis zur Ausführung.  
  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt einen vollständige Satz URL-basierter Anforderungen, über die Sie schnell und problemlos auf die Berichtsnavigation und -anzeige zugreifen können. Sie können diese Technologie zusammen mit dem Berichtsserver-Webdienst verwenden, um eine vollständige Berichtslösung in Ihre vorhandenen Geschäftsanwendungen zu integrieren. Der URL-Zugriff ist dann besonders sinnvoll, wenn Sie Berichte als Teil eines Internetportals integrieren oder wenn Sie Berichte über einen Webbrowser anzeigen.  
  
 [Erweiterungen für Reporting Services](extensions/reporting-services-extensions.md)  
 Die modulare Architektur von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ermöglicht Erweiterungen. Eine verwaltete Code-API steht zur Verfügung, sodass Sie problemlos Erweiterungen entwickeln, installieren und verwalten können, die von vielen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Komponenten benötigt werden. Sie können Assemblys mithilfe [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] von erstellen und neue [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Funktionen für Rendering, Sicherheit, Übermittlung und Datenverarbeitung hinzufügen, um die sich entwickelnden geschäftlichen Anforderungen zu erfüllen.  
  
 [Custom Report Items](custom-report-items/custom-report-items.md)  
 Beschreibt, wie Sie benutzerdefinierte Elemente erstellen, um Funktionen zu RDL hinzuzufügen, oder wie Sie vorhandene Steuerelemente erweitern.  
  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](custom-assemblies/using-custom-assemblies-with-reports.md)  
 Beschreibt, wie benutzerdefinierte Assemblys mit Berichten verwendet werden, indem Codeverweise in die Berichtsdefinition aufgenommen werden.  
  
 [Zugreifen auf den Reporting Services-WMI-Anbieter](tools/access-the-reporting-services-wmi-provider.md)  
 Beschreibt, wie Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -WMI-Anbieter zum Verwalten von Berichtsserverbereitstellungen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services &#40;SSRS-&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Berichts Definitions Sprache &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)   
 [Technische Referenz &#40;SSRS&#41;](technical-reference-ssrs.md)   
 [Sichere Entwicklung (Reporting Services)](extensions/secure-development/secure-development-reporting-services.md)  
  
  
