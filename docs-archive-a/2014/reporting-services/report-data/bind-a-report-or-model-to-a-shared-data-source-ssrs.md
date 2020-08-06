---
title: Binden eines Berichts oder Modells an eine freigegebene Datenquelle (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 596caba042d476173b3c49d1ad18e79d0827fe89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697561"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>Binden eines Berichts oder Modells an eine freigegebene Datenquelle (SSRS)
  In einigen Situationen, z. B., wenn Sie einen Bericht oder ein Modell von einem Testserver auf einen Produktionsserver verschieben, möchten Sie die Datei vielleicht auf dem lokalen Computer speichern und anschließend auf einen anderen Berichtsserver hochladen. Wenn Sie den Bericht oder das Modell auf den neuen Server hochladen, müssen Sie ihn oder es erneut an eine freigegebene, auf dem neuen Berichtsserver gespeicherte Datenquelle binden. Wenn Sie den Bericht oder das Modell nicht erneut binden, können sie bei einem Zugriff vom neuen Berichtsserver nicht ordnungsgemäß verwendet werden.  
  
> [!IMPORTANT]  
>  Vor dem erneuten Binden eines Berichts oder Modells an eine freigegebene Datenquelle müssen die Daten bereits auf dem Berichtsserver oder in der SharePoint-Bibliothek vorhanden sein. Weitere Informationen zu Datenquellen finden Sie unter [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>So binden Sie einen Bericht oder ein Modell an eine freigegebene Datenquelle auf einem Berichtsserver im einheitlichen Modus  
  
1.  Klicken Sie in **Berichts-Manager**auf den Namen des Berichts oder Modells, den oder das Sie auf den Server hochladen möchten.  
  
     Die Registerkarte Eigenschaften wird geöffnet.  
  
2.  Klicken Sie auf **Datenquellen**.  
  
3.  Klicken Sie auf **Durchsuchen**, und navigieren Sie dann zu der Datenquelle, an die Sie den Bericht oder das Modell binden möchten.  
  
4.  Wählen Sie die Datenquelle aus, und klicken Sie dann auf **OK**.  
  
5.  Klicken Sie auf **Anwenden**.  
  
     Der Bericht oder das Modell ist nun an die ausgewählte Datenquelle gebunden.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>So binden Sie einen Bericht oder ein Modell an eine freigegebene Datenquelle auf einem Berichtsserver im integrierten SharePoint-Modus  
  
1.  Klicken Sie auf der Schnellstartleiste auf den Namen der Bibliothek, wenn sie nicht bereits geöffnet ist. Wenn der Name der Bibliothek nicht angezeigt wird, klicken Sie auf **Alle Websiteinhalte einblenden**und anschließend auf den Namen der Bibliothek.  
  
2.  Zeigen Sie auf den Bericht oder das Modell, und klicken Sie auf den Pfeil nach unten.  
  
3.  Klicken Sie auf **Datenquellen verwalten**.  
  
4.  Klicken Sie auf **dataSource1**.  
  
5.  Überprüfen Sie im Bereich **Verbindungstyp** , ob **Freigegebene Datenquelle** ausgewählt ist.  
  
6.  Klicken Sie im Bereich **Datenquellenlink** auf die Schaltfläche mit den Auslassungspunkten (...).  
  
7.  Suchen Sie die Datenquelle, die Sie verwenden möchten.  
  
8.  Wählen Sie die Datenquelle aus, und klicken Sie auf **OK**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hochladen einer Datei oder eines Berichts &#40;Berichts-Manager&#41;](../reports/upload-a-file-or-report-report-manager.md)   
 [Hochladen von Dokumenten in eine SharePoint-Bibliothek &#40;Reporting Services im SharePoint-Modus&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Erstellen und Verwalten von freigegebenen Datenquellen &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [Erstellen, löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
