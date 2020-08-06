---
title: Implementieren von Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af1e804e029dae77fb7836577aa8d4a45ad20109
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630548"
---
# <a name="implementing-a-delivery-extension"></a>Implementieren von Übermittlungserweiterungen
  Mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Benutzer Berichte erstellen und veröffentlichen, die anschließend an diverse Orte übermittelt werden. Außerdem enthält [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verschiedene Übermittlungserweiterungen und eine Übermittlungs-API, mit der Entwickler zusätzliche Übermittlungserweiterungen erstellen können, um die Übermittlungsfunktionen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] noch zu erweitern.  
  
 Eine Beispielimplementierung einer Übermittlungserweiterung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über Übermittlungs Erweiterungen] Delivery-Extensions-Overview.MD)  
 Erläutert, wie eine benutzerdefinierte Übermittlungserweiterung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geschrieben wird.  
  
 [Preparing to Implement a Delivery Extension (Vorbereiten der Implementierung von Übermittlungserweiterungen)](preparing-to-implement-a-delivery-extension.md)  
 Beschreibt die verfügbaren Schnittstellen und Klassen beim Implementieren einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung sowie die Themen, die vor der Implementierung berücksichtigt werden sollten.  
  
 [Creating a Delivery Extension Library (Erstellen einer Bibliothek für Übermittlungserweiterungen)](creating-a-delivery-extension-library.md)  
 Beschreibt die Zuordnung eines Namespace für die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung und die Kompilierung der Übermittlungserweiterung in eine DLL-Bibliothek.  
  
 [Implementing the IDeliveryExtension Interface for a Delivery Extension (Implementieren der IDeliveryExtension-Schnittstelle für Übermittlungserweiterungen)](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Beschreibt die Attribute einer Übermittlungserweiterung und die Art der Implementierung einer eigenen Klasse für die Übermittlungserweiterung.  
  
 [Using a Notification Class for a Delivery Extension (Verwenden einer Notification-Klasse für eine Übermittlungserweiterung)](using-a-notification-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Notification**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Using the Setting Class for a Delivery Extension (Verwenden der Setting-Klasse für eine Übermittlungserweiterung)](using-the-setting-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Setting**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Verwenden der IDeliveryReportServerInformation-Schnittstelle für Übermittlungserweiterungen](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **IDeliveryReportServerInformation**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Verwenden der Report-Klasse für eine Übermittlungserweiterung](using-the-report-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Report**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **RenderedOutputFile**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Implementieren der ISubscriptionBaseUIUserControl-Schnittstelle für eine Übermittlungserweiterung](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 Beschreibt die Attribute eines Steuerelements für die Übermittlungserweiterung und die Art der Implementierung einer eigenen Schnittstelle für das Abonnement.  
  
 [Bereitstellen von Übermittlungserweiterungen](deploying-a-delivery-extension.md)  
 Beschreibt, wie Sie eine Übermittlungserweiterung anwenden  
  
 [Debuggen von Übermittlungserweiterungscode](debugging-delivery-extension-code.md)  
 Beschreibt, wie Sie Code in der Übermittlungserweiterung debuggen  
  
 [Entfernen einer Übermittlungserweiterung](removing-a-delivery-extension.md)  
 Beschreibt, wie Sie eine Übermittlungserweiterung von einem Berichtsserver entfernen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Erweiterungen](../reporting-services-extensions.md)   
 [Reporting Services-Erweiterungsbibliothek](../reporting-services-extension-library.md)  
  
  
