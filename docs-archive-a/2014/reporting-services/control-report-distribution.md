---
title: Steuern der Berichts Verteilung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- subscriptions [Reporting Services], e-mail
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- subscriptions [Reporting Services], security
- mail [Reporting Services]
ms.assetid: 8f15e2c6-a647-4b05-a519-1743b5d8654c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de8a27801ef89f10bf303cee17d1c2d0e1081c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607552"
---
# <a name="control-report-distribution"></a>Steuern der Berichtsverteilung
  Sie können einen Berichtsserver so konfigurieren, dass die Sicherheitsrisiken im Zusammenhang mit der Verteilung per E-Mail und Dateifreigabe minimiert werden.  
  
## <a name="securing-reports"></a>Sichern von Berichten  
 Der erste Schritt beim Steuern der Berichtsverteilung besteht im Sichern des Berichts vor unbefugtem Zugriff. Wenn ein Bericht in einem Abonnement verwendet werden soll, muss er gespeicherte Anmeldeinformationen verwenden, die für alle Übermittlungen identisch sind. Jeder Benutzer mit Zugriff auf den Bericht im Berichtsserver kann diesen ausführen und möglicherweise verteilen. Um dies zu verhindern, müssen Sie den Zugriff auf den Bericht auf die erforderlichen Benutzer beschränken. Weitere Informationen finden Sie unter [Sichern von Berichten und Ressourcen](security/secure-reports-and-resources.md) und [sicheren Ordnern](security/secure-folders.md).  
  
 Streng vertrauliche Berichte, die den Zugriff mithilfe der Datenbanksicherheit autorisieren, können nicht mit einem Abonnement verteilt werden.  
  
> [!IMPORTANT]  
>  Berichte werden als Dateien transportiert. Die Risiken und Sicherheitsmaßnahmen im Zusammenhang mit Dateien gelten auch für Berichte, die auf einem Datenträger gespeichert oder als Anlagen gesendet werden. Jeder Benutzer mit Zugriff auf eine Datei kann diese nach seinem Ermessen verteilen oder verwenden.  
  
## <a name="controlling-e-mail-delivery"></a>Steuern der E-Mail-Übermittlung  
 Sie können einen Berichtsserver so konfigurieren, dass die E-Mail-Verteilung auf bestimmte Hostdomänen beschränkt wird. Beispielsweise können Sie verhindern, dass ein Berichtsserver einen Bericht an alle Domänen übermittelt, außer an jene, die in der RSReportServer-Konfigurationsdatei aufgeführt sind.  
  
 Darüber hinaus können Sie mithilfe von Konfigurationseinstellungen das Feld **An** in einem Abonnement ausblenden. In diesem Fall werden Berichte nur an den Benutzer übermittelt, den das Abonnement definiert. Wenn jedoch ein Bericht an einen Benutzer gesendet wurde, können Sie nicht verhindern, dass der Bericht weitergeleitet wird.  
  
 Die effizienteste Möglichkeit zum Steuern der Berichtsverteilung besteht darin, einen Berichtsserver so konfigurieren, dass nur eine Berichtsserver-URL gesendet wird. Der Berichtsserver verwendet die Windows-Authentifizierung und das rollenbasierte Autorisierungsmodell, um den Zugriff auf einen Bericht zu steuern. Falls ein Benutzer versehentlich per E-Mail einen Bericht erhält, für den er keine Anzeigeberechtigung hat, zeigt der Berichtsserver den Bericht nicht an.  
  
## <a name="controlling-file-share-delivery"></a>Steuern der Dateifreigabeübermittlung  
 Mit der Dateifreigabeübermittlung wird ein Bericht an eine Datei auf einer Festplatte gesendet. Nachdem die Datei auf den Datenträger gespeichert wurde, unterliegt sie nicht mehr dem rollenbasierten Sicherheitsmodell, mit dem der Berichtsserver den Benutzerzugriff steuert. Um einen Bericht zu sichern, der an einen Datenträger übermittelt wurde, können Sie Zugriffssteuerungslisten (ACLs, Access Control Lists) in der Datei selbst oder im Ordner, in dem die Datei gespeichert ist, platzieren. Je nach Betriebssystem sind möglicherweise zusätzliche Sicherheitsoptionen verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Berichts Servers für die e-Mail-Übermittlung &#40;SSRS-Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Create and Manage Subscriptions for Native Mode Report Servers (Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus)](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)  
  
  
