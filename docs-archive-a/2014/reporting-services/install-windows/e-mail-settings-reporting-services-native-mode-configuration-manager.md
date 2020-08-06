---
title: E-Mail-Einstellungen-Configuration Manager (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700845"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>E-Mail-Einstellungen – Konfigurations-Manager (einheitlicher SSRS-Modus)
  Verwenden Sie diese Seite, um die SMTP (Simple Mail Transport Protocol)-Einstellungen anzugeben, mit denen die E-Mail-Übermittlung des Berichtsservers aktiviert wird. Mit der E-Mail-Übermittlungserweiterung des Berichtsservers können Sie Berichte oder Benachrichtigungen über Berichtsverarbeitungen mithilfe von E-Mail-Abonnements verteilen. Für die Berichtsserver-E-Mail-Übermittlungserweiterung sind ein SMTP-Server und eine E-Mail-Adresse erforderlich, die im Feld "Von:" verwendet wird.  
  
 Es können zusätzliche Konfigurationseinstellungen verwendet werden, um die E-Mail-Abonnements weiter anzupassen, einschließlich Einstellungen, welche die Verfügbarkeit von Mailserverhosts und Renderingerweiterungen einschränken. Diese Einstellungen können nicht im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager angegeben werden. Zum Konfigurieren der zusätzlichen Einstellungen müssen Sie die Datei RSReportServer.config manuell bearbeiten. Weitere Informationen finden Sie unter [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) und [Reporting Services von Konfigurationsdateien](../report-server/reporting-services-configuration-files.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
 Um diese Seite zu öffnen, starten Sie den Konfigurations-Manager für Reporting Services, und klicken Sie im Navigationsbereich auf **e-Mail-Einstellungen** . Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.  
  
## <a name="options"></a>Tastatur  
 **Absenderadresse**  
 Gibt die E-Mail-Adresse an, die im Feld Von: einer generierten E-Mail verwendet werden soll. Sie müssen ein Benutzerkonto angeben, das über die Berechtigung zum Senden von E-Mails vom SMTP-Server verfügt.  
  
 **Aktuelle SMTP-Übermittlungsmethode**  
 Gibt an, ob die Berichtsserver-E-Mail über einen SMTP-Server geleitet wird. Dies ist die einzige Übermittlungsmethode, die Sie im Reporting Services-Konfigurations-Manager angeben können.  
  
 Eine andere Übermittlungsmethode soll ein lokales Abholverzeichnis eines SMTP-Dienstes verwenden. Sie können diese Übermittlungsmethode verwenden, wenn kein SMTP-Netzwerkdienst zur Verfügung steht. Um ein lokales Abholverzeichnis für den SMTP-Dienst anzugeben, müssen Sie die RSReportServer.config-Datei bearbeiten. Wenn Sie die Konfigurationsdatei so bearbeiten, dass ein lokales Abhol Verzeichnis für den SMTP-Dienst verwendet wird, legt das Konfigurations-Manager für Reporting Services die Option Übermittlungs **Methode** auf *Benutzer* definiert fest, um anzugeben, dass die Übermittlungs Methode in der Konfigurationsdatei angegeben ist.  
  
 In der Konfigurationsdatei ist die Übermittlungsmethode über die `SendUsing`-Konfigurationseinstellung festgelegt. Weitere Informationen zum Festlegen der `SendUsing` Einstellung finden Sie unter [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **SMTP-Server**  
 Geben Sie den zu verwendenden SMTP-Server oder -Gateway an. Sie können einen lokalen Server oder einen SMTP-Server in Ihrem Netzwerk verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
