---
title: Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619607"
---
# <a name="configure-a-firewall-for-report-server-access"></a>Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserveranwendungen und veröffentlichte Berichte erfolgt über URLs, die eine IP-Adresse, einen Port und ein virtuelles Verzeichnis angeben. Wenn die Windows-Firewall aktiviert ist, ist der Port, für den der Berichtsserver konfiguriert ist, höchstwahrscheinlich geschlossen. Ein Anzeichen dafür, dass der Port geschlossen ist, ist das Erscheinen einer leeren Webseite nach dem Anfordern eines Berichts oder eine leere Seite, wenn Sie versuchen, den Berichts-Manager von einem Remoteclientcomputer aus zu öffnen.  
  
 Um einen Port zu öffnen, müssen Sie das Hilfsprogramm Windows-Firewall auf dem Berichtsservercomputer verwenden. Reporting Services öffnet keine Ports für Sie; Sie müssen diesen Schritt manuell ausführen.  
  
 Standardmäßig lauscht der Berichtsserver HTTP-Anforderungen an Port 80. Die folgenden Anweisungen beinhalten daher Schritte, die diesen Port angeben. Wenn Sie die Berichtsserver-URLs für einen anderen Port konfiguriert haben, müssen Sie die entsprechende Portnummer beim Ausführen der unten stehenden Anweisungen angeben.  
  
 Wenn Sie auf relationale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken auf externen Computern zugreifen oder wenn sich die Berichtsserver-Datenbank auf einer externen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz befindet, müssen Sie Port 1433 und Port 1434 auf dem externen Computer öffnen. Weitere Informationen zur Windows-Firewall finden Sie unter [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation. Weitere Informationen zu den Standardeinstellungen der Windows-Firewall und eine Beschreibung der TCP-Ports, die sich auf das [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]und die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]auswirken, finden Sie unter [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) (Konfigurieren der Windows-Firewall für den SQL Server-Zugriff) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Diese Anweisungen setzen voraus, dass Sie das Dienstkonto bereits konfiguriert, die Berichtsserver-Datenbank erstellt und die URLs für den Berichtsserver-Webdienst und Berichts-Manager konfiguriert haben. Weitere Informationen finden Sie unter [Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus](manage-a-reporting-services-native-mode-report-server.md).  
  
 Außerdem sollten Sie überprüft haben, dass auf den Berichtsserver über eine lokale Webbrowserverbindung mit der lokalen Berichtsserverinstanz zugegriffen werden kann. Dieser Schritt setzt voraus, dass Sie eine Arbeitsinstallation haben. Sie sollten überprüfen, ob die Installation ordnungsgemäß konfiguriert ist, bevor Sie mit dem Öffnen von Ports beginnen. Um diesen Schritt auf Windows Server auszuführen, müssen Sie die Berichtsserversite außerdem zu den vertrauenswürdigen Sites hinzugefügt haben. Weitere Informationen finden Sie unter [Konfigurieren eines Berichtsservers im einheitlichen Modus für die lokale Verwaltung &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Öffnen von Ports in der Windows-Firewall  
 Für verschiedene Versionen der Windows-Firewall gibt es jeweils unterschiedliche Anweisungen.  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a>So öffnen Sie Port 80 unter Windows 7, Windows Server 2008 R2, Windows Server 2012 und 2012 R2  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**und dann auf **System und Sicherheit**und **Windows-Firewall**. Wenn die Systemsteuerung nicht für die Kategorieansicht konfiguriert ist, müssen Sie nur **Windows-Firewall**auswählen.  
  
2.  Klicken Sie auf **Erweiterte Einstellungen**.  
  
3.  Klicken Sie auf **Eingehende Regeln**.  
  
4.  Klicken Sie im Fenster **Aktionen** auf **Neue Regel****.**  
  
5.  Wählen Sie **Port** als **Regeltyp**aus.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Klicken Sie auf der Seite **Protokolle und Ports** auf **TCP**.  
  
8.  Wählen Sie **Bestimmte lokale Ports** aus, und geben Sie den Wert **80**ein.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Klicken Sie auf der Seite **Aktion** auf **Verbindung zulassen**.  
  
11. Klicken Sie auf **Weiter**.  
  
12. Klicken Sie auf der Seite **Profil** auf die entsprechenden Optionen für die Umgebung.  
  
13. Klicken Sie auf **Weiter**.  
  
14. Geben Sie auf der Seite **Name** den Namen**ReportServer (TCP an Port 80)** ein.  
  
15. Klicken Sie auf **Fertig stellen**.  
  
16. Starten Sie den Computer neu.  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a>So öffnen Sie Port 80 unter Windows Vista oder Windows Server 2008  
  
1.  Klicken Sie im **Startmenü** auf **Systemsteuerung**, klicken Sie auf **Sicherheit**, und klicken Sie dann auf **Windows-Firewall**.  
  
2.  Klicken Sie auf **Programm durch die Windows-Firewall kommunizieren lassen**.  
  
3.  Klicken Sie auf **Weiter**.  
  
4.  Klicken Sie auf der Registerkarte Ausnahmen auf **Port hinzufügen**.  
  
5.  Geben Sie unter Name **den Namen Report Server (TCP an Port 80)** ein.  
  
6.  Geben Sie unter Port Nummer den Wert **80**ein.  
  
7.  Überprüfen Sie, ob **TCP** ausgewählt ist.  
  
8.  Klicken Sie auf **Bereich ändern**.  
  
9. Klicken Sie auf eigenes **Netzwerk (Subnetz)**, und klicken Sie dann auf **OK**.  
  
10. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
11. Starten Sie den Computer neu.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nach dem Öffnen des Ports und vor dem Bestätigen, ob Remotebenutzer auf den Berichtsserver über den von Ihnen geöffneten Port zugreifen können, müssen Sie Benutzerzugriff auf den Berichtsserver über Rollenzuweisungen für den Stammordner und auf Siteebene erteilen. Ein Port kann richtig geöffnet sein und dennoch fehlgeschlagene Berichtsserververbindungen verursachen, wenn Benutzer nicht über entsprechende Berechtigungen verfügen. Weitere Informationen finden Sie unter [Gewähren von Benutzerzugriff auf einen Berichtsserver (Berichts-Manager)](../security/grant-user-access-to-a-report-server.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Onlinedokumentation.  
  
 Sie können auch überprüfen, ob der Port richtig geöffnet ist, indem Sie den Berichts-Manager auf einem anderen Computer starten. Weitere Informationen finden Sie unter [Berichts-Manager (einheitlicher SSRS-Modus)](../report-manager-ssrs-native-mode.md) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Erstellen einer Berichts Server-Datenbank &#40;SSRS-Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Manage a Reporting Services Native Mode Report Server (Verwalten eines Berichtsservers von Reporting Services im einheitlichen Modus)](manage-a-reporting-services-native-mode-report-server.md)  
  
  
