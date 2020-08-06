---
title: Verwenden der Report-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630530"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Verwenden der Report-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse stellt einen Bericht in der Berichtsserver-Datenbank dar. Jedes Abonnement wird einem bestimmten Bericht zugeordnet. Der Bericht ist in der Benachrichtigung enthalten. Die Übermittlungserweiterung kann das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt verwenden, das Bestandteil der Benachrichtigung zum Rendern des Berichts ist. Das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt enthält auch berichtsspezifische Eigenschaften, wie die URL zum Bericht auf dem Server und den Namen des Berichts. Diese Eigenschaften können alle als Teil des Übermittlungsanbieters verwendet werden.  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A>-Methode der <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse kann zum Rendern eines Berichts verwendet werden. Die <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A>-Methode gibt ein Array von einem oder mehreren <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekten zurück, die zusammen einen gerenderten Bericht ausmachen. Das erste <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt ist der gerenderte Bericht. Alle anderen <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekte sind Ressourcen, die zusammen mit den Berichtsdaten geliefert werden müssen (z. B. eine HTML-Datei und zugehörige Bilder). Renderingerweiterungen mit einem einzigen Datenstrom (IMAGE, PDF, MHTML und Excel) geben nur ein <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt im Array zurück.  
  
 Das <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt, das den Berichtsdatenstrom enthält, kann als Teil einer Übermittlung enthalten sein.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services-Erweiterungsbibliothek](../reporting-services-extension-library.md)   
 [Using the RenderedOutputFile Class for a Delivery Extension (Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung)](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
