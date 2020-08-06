---
title: Wählen Sie die Datenquelle aus. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697434"
---
# <a name="select-the-data-source"></a>Auswählen der Datenquelle
  Auf dieser Seite des Berichts-Assistenten können Sie eine Datenquelle für den Bericht definieren.  
  
## <a name="options"></a>Tastatur  
 **Freigegebene Datenquelle**  
 Wählen Sie **Freigegebene Datenquelle** aus, um eine vordefinierte Datenquelle zu verwenden, die bereits über die zu verwendenden Datenquellen-Verbindungsinformationen verfügt. Die Liste enthält alle freigegebenen Datenquellen, die in dem Projekt enthalten sind.  
  
 **Neue Datenquelle**  
 Wählen Sie **Neue Datenquelle** aus, um eine neue Datenquelle zu definieren. Die Datenquelleninformationen werden nur mit dem aktuellen Bericht verwendet.  
  
 **Name**  
 Geben Sie einen Namen für die Verbindung mit der Datenquelle ein. Der Datenquellenname muss innerhalb des Berichts eindeutig sein.  
  
 **Type**  
 Wählen Sie den Typ der verwendeten Datenquelle aus (wenn Sie z [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . b. eine Datenbank verwenden, wählen Sie) aus [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge für die Datenquelle ein. Weitere Informationen zu Verbindungs Zeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungs](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)Zeichenfolgen in Reporting Services.  
  
 Klicken Sie auf **Bearbeiten** , um den Datenquellenserver im Dialogfeld **Verbindungseigenschaften** anzugeben. Sie können eine lokale oder Remotedatenquelle angeben.  
  
 Klicken Sie auf **Anmeldeinformationen** , um Datenbankanmeldeinformationen anzugeben. Die Anmeldeinformationen müssen für Sie ausreichend sein, um zu Berichtsentwurfszwecken eine Verbindung mit der Datenquelle herzustellen. Wenn der Bericht auf einem Berichtsserver bereitgestellt wird, müssen die Datenbankanmeldeinformationen alle Benutzer des Berichts enthalten. Wenn Sie z.B. möchten, dass alle Berichtsbenutzer mithilfe ihrer Anmeldeinformationen eine Verbindung mit der Datenquelle herstellen, wählen Sie **Windows-Authentifizierung verwenden (integrierte Sicherheit)** aus. Die von Ihnen angegebenen Anmeldeinformationen müssen für die Datenquelle gültig sein. Wenn Sie also die Windows-Authentifizierung wählen, müssen Sie sicherstellen, dass die Datenquelle die Verbindungen von allen Benutzerkonten annimmt, die den Bericht ausführen. Die Datenbankanmeldeinformationen können getrennt vom Bericht verwaltet werden. Weitere Informationen finden Sie unter [Verwalten von Berichtsdatenquellen](report-data/manage-report-data-sources.md).  
  
 **Als freigegebene Datenquelle festlegen**  
 Wählen Sie diese Option aus, um die Datenquelle im Projekt als freigegebene Datenquelle, statt im Bericht zu speichern. Auf diese Weise können Sie sie als Datenquelle für andere Berichte im Projekt nutzen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eingebettete und freigegebene Datenverbindungen oder Datenquellen &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services Berichts Server](../../2014/reporting-services/reporting-services-report-server.md)   
 [RSReportDesigner-Konfigurationsdatei](report-server/rsreportdesigner-configuration-file.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Hilfe des Berichts-Assistenten](../../2014/reporting-services/report-wizard-help.md)  
  
  
