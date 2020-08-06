---
title: Datenbank (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb8f1841e980279d6051e3393efdf06df238f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622420"
---
# <a name="database-ssrs-native-mode"></a>Datenbank (einheitlicher SSRS-Modus)
  Auf der Seite Setup der Datenbank können Sie die Berichtsserver-Datenbanken erstellen und konfigurieren, die den internen Speicher für eine oder mehrere Berichtsserverinstanzen bereitstellen. Wenn Sie einen Berichtsserver für eine Remoteberichtsserver-Datenbank konfigurieren, müssen Sie die Datenbank mithilfe des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Managers erstellen.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.  
  
 Das Erstellen einer Berichtsserver-Datenbank und die Konfiguration der Verbindung erfolgt in mehreren Schritten. Diese Seite enthält für jeden Tasktyp einen Assistenten, der Sie durch diese Schritte leitet. Berechtigungen und Anmeldungen werden automatisch für Sie erstellt oder aktualisiert. Sie können den Status jedes Schritts auf der Seite Status überwachen. Wenn ein Fehler auftritt, können Sie auf den Fehler klicken, um Informationen zur Fehlerbehebung zu erhalten.  
  
 Eine Berichtsserver-Datenbank muss einen bestimmten Servermodus unterstützen. Der Standardmodus ist der einheitliche Modus; Sie können aber auch eine Berichtsserver-Datenbank für den integrierten SharePoint-Modus erstellen, wenn Sie einen Berichtsserver in einer größeren Bereitstellung eines SharePoint-Produkts oder einer SharePoint-Technologie ausführen. Weitere Informationen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Um diese Seite zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und klicken Sie im Navigationsbereich auf **Datenbank** . Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **SQL Server Name**  
 In der aktuellen Berichtsserverdatenbank gibt **Name des SQL-Servers** den Namen der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] an, auf der die Berichtsserverdatenbank ausgeführt wird. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden.  
  
 **Database Name**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert.  
  
 **Berichtsserver-Modus**  
 Zeigt an, ob die Berichtsserver-Datenbank den einheitlichen Modus oder den integrierten SharePoint-Modus unterstützt. Weitere Informationen finden Sie unter [Reporting Services Berichts Servers](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Datenbank ändern**  
 Starten Sie einen Assistenten, der Sie durch alle Schritte führt, die zur Erstellung oder Auswahl einer Berichtsserver-Datenbank erforderlich sind.  
  
 **Typ der Anmeldeinformationen**  
 Gibt die Anmeldeinformationen an, die vom Berichtsserver zum Herstellen der Verbindung zur Berichtsserver-Datenbank verwendet werden. Zu den Anmeldeinformationen, die Sie angeben können, gehören das Dienstkonto, ein Windows-Domänenbenutzer, ein lokaler Windows-Benutzer oder die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankanmeldung. Weitere Informationen zum Auswählen von Anmelde Informationen finden Sie unter [Konfigurieren einer Verbindung mit der Berichts Server-Datenbank &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Benutzername**  
 Gibt ein Domänenbenutzerkonto an, wenn Sie Windows-Anmeldeinformationen verwenden, bzw. einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen, wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldeinformationen verwenden. Wenn Sie Windows-Anmelde Informationen verwenden, geben Sie diese im folgenden Format an: * \<domain> \\<Konto \> *.  
  
 **Kennwort**  
 Gibt das Kennwort für das Konto an.  
  
 **Anmelde Informationen ändern**  
 Starten Sie einen Assistenten, der Sie durch alle Schritte führt, die zur Auswahl eines anderen Kontos oder zum Aktualisieren des Kennworts für das Konto erforderlich sind, über das Sie die Verbindung zur Berichtsserver-Datenbank herstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Berichts Server-Datenbank im einheitlichen Modus &#40;SSRS-Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Berichts Server-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
