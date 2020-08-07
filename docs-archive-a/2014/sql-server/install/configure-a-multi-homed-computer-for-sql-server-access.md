---
title: Konfigurieren eines mehrfach vernetzten Computers für SQL Server-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multi-homed computer
- multi-homed computer [SQL Server] configuring ports
- firewall systems [Database Engine], multi-homed computer
ms.assetid: ba369e5b-7d1f-4544-b7f1-9b098a1e75bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b20fa552e57441ef211049f0e51b4f8d65e6f2e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619564"
---
# <a name="configure-a-multi-homed-computer-for-sql-server-access"></a>Konfigurieren eines mehrfach vernetzten Computers für SQL Server-Zugriff
  In einem Szenario, in dem ein Server eine Verbindung zu mindestens zwei Netzwerken oder Netzwerksubnetzen bereitstellen muss, wird normalerweise ein mehrfach vernetzter Computer verwendet. Häufig befindet sich dieser Computer in einem Umkreisnetzwerk (auch als DMZ, Demilitarized Zone oder überwachtes Subnetz bezeichnet). In diesem Thema wird beschrieben, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows-Firewall mit erweiterter Sicherheit konfiguriert werden, um Netzwerkverbindungen zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer mehrfach vernetzten Umgebung bereitzustellen.  
  
> [!NOTE]  
>  Ein mehrfach vernetzter Computer verfügt über mehrere Netzwerkkarten oder wurde so konfiguriert, dass mehrere IP-Adressen für eine einzelne Netzwerkkarte verwendet werden können. Ein zweifach vernetzter Computer verfügt über zwei Netzwerkkarten oder wurde so konfiguriert, dass zwei IP-Adressen für eine einzelne Netzwerkkarte verwendet werden können.  
  
 Bevor Sie mit diesem Thema fortfahren, sollten Sie mit den Informationen im Thema [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)vertraut sein. Dieses Thema enthält grundlegende Informationen dazu, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten mit der Firewall zusammenarbeiten.  
  
 **Annahmen für dieses Beispiel:**  
  
-   Der Computer verfügt über zwei installierte Netzwerkkarten. Eine oder mehrere Netzwerkkarten können drahtlos sein. Sie können simulieren, dass Sie über zwei Netzwerkkarten verfügen, indem Sie die IP-Adresse für die erste und die IP-Loopbackadresse (127.0.0.1) für die zweite Netzwerkkarte verwenden.  
  
-   Der Einfachheit halber werden in diesem Beispiel IPv4-Adressen verwendet. Die gleichen Prozeduren können jedoch auch mit IPv6-Adressen ausgeführt werden.  
  
    > [!NOTE]  
    >  Bei einer IPv4-Adresse handelt es sich um eine Reihe von vierstelligen Zahlen, die als Oktett bezeichnetet wird. Jede Zahl ist kleiner als 255 und wird durch Punkte getrennt, z. B. 127.0.0.1. Eine IPv6-Adresse ist eine Reihe von acht Hexadezimalzahlen, die durch Doppelpunkte getrennt werden, z. B. fe80:4898:23:3:49a6:f5c1:2452:b994.  
  
-   Die Firewall kann entweder den Zugriff über einen bestimmten Port (wie z. B. Port 1433) oder auf das Programm [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] (sqlservr.exe) zulassen. Beide Methoden sind gleichwertig. Da ein Server in einem Umkreisnetzwerk anfälliger für Angriffe ist als ein Server in einem Intranet, wird für dieses Thema angenommen, dass Sie den Zugriff genauer steuern und die Ports, die Sie öffnen, einzeln auswählen möchten. Es wird daher vorausgesetzt, dass Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfigurieren, um auf einem festen Port zu lauschen. Weitere Informationen über die Ports, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
-   In diesem Beispiel wird der Zugriff auf [!INCLUDE[ssDE](../../includes/ssde-md.md)] unter Verwendung von TCP-Port 1433 konfiguriert. Die anderen Ports, die unterschiedliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten sind, können mithilfe der gleichen allgemeinen Schritte konfiguriert werden.  
  
 **In diesem Beispiel werden die folgenden allgemeinen Schritte beschrieben:**  
  
-   Bestimmen der IP-Adressen des Computers.  
  
-   Konfigurieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sodass auf einem bestimmten TCP-Port gelauscht wird.  
  
-   Konfigurieren der Windows-Firewall mit erweiterter Sicherheit.  
  
## <a name="optional-procedures"></a>Optionale Vorgänge  
 Wenn Sie die verfügbaren IP-Adressen Ihres Computers bereits kennen und diese von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet werden, können Sie diese Vorgänge überspringen.  
  
#### <a name="to-determine-the-ip-addresses-available-on-the-computer"></a>So bestimmen Sie die verfügbaren IP-Adressen des Computers  
  
1.  Klicken Sie auf dem Computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , auf dem installiert ist, auf **Start**, klicken Sie auf **Ausführen**, geben Sie `cmd` und dann ein [!INCLUDE[clickOK](../../includes/clickok-md.md)] .  
  
2.  Geben Sie im Eingabeaufforderungsfenster `ipconfig,` ein, und drücken Sie anschließend die EINGABETASTE, um die auf diesem Computer verfügbaren IP-Adressen aufzulisten.  
  
    > [!NOTE]  
    >  Durch den **ipconfig** -Befehl werden manchmal zahlreiche mögliche Verbindungen aufgelistet, einschließlich getrennter Verbindungen. Der **ipconfig** -Befehl kann sowohl IPv4- als auch IPv6-Adressen auflisten.  
  
3.  Notieren Sie die IPv4- und IPv6-Adressen, die verwendet werden. Die anderen Informationen in der Liste, wie z. B. temporäre Adressen, Subnetzmasken und Standardgateways sind wichtig zum Konfigurieren eines TCP/IP-Netzwerks. Diese Informationen werden in diesem Beispiel jedoch nicht verwendet.  
  
#### <a name="to-determine-the-ip-addresses-and-ports-used-by-ssnoversion"></a>So bestimmen Sie die IP-Adressen und die Ports zur Verwendung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie dann auf **Konfigurationstools**, und klicken Sie dann auf **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager**.  
  
2.  Erweitern Sie in ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**im Konsolen Bereich den Knoten ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Netzwerkkonfiguration**, erweitern Sie **Protokolle \<instance name> für **, und doppelklicken Sie dann auf **TCP/IP**.  
  
3.  Im Dialogfeld **TCP/IP-Eigenschaften** auf der Registerkarte **IP-Adressen** werden mehrere IP-Adressen im Format **IP1**, **IP2**und bis zu **IPAll**angezeigt. Eine dieser Angaben ist die IP-Adresse des Loopbackadapters (127.0.0.1). Für alle IP-Adressen, die auf dem Computer konfiguriert wurden, werden zusätzliche IP-Adressen angezeigt.  
  
4.  Wenn das Dialogfeld **Dynamische TCP-Ports** für eine IP-Adresse eine **0**enthält, weist dies darauf hin, dass das [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf dynamischen Ports lauscht. In diesem Beispiel werden feste Ports anstatt dynamischer Ports, die sich bei einem Neustart ändern können, verwendet. Löschen Sie daher die 0, wenn das Dialogfeld **Dynamische TCP-Ports** eine **0**enthält.  
  
5.  Notieren Sie den TCP-Port, der für jede IP-Adresse aufgelistet ist, die Sie konfigurieren möchten. Für dieses Beispiel wird angenommen, dass beide IP-Adressen den Standardport 1433 überwachen.  
  
6.  Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einige der verfügbaren Ports nicht verwenden soll, ändern Sie auf der Registerkarte **Protokoll** den Wert **Alle lauschen** zu **Nein**, und ändern Sie auf der Registerkarte **IP-Adressen** für die IP-Adressen, die Sie nicht verwenden möchten, den Wert **Aktiv** zu **Nein** .  
  
## <a name="configuring-windows-firewall-with-advanced-security"></a>Windows-Firewall mit erweiterter Sicherheit konfigurieren  
 Nachdem Sie nun die vom Computer verwendeten IP-Adressen und die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendeten Ports kennen, können Sie Firewallregeln erstellen und diese Regeln anschließend für bestimmte IP-Adressen konfigurieren.  
  
#### <a name="to-create-a-firewall-rule"></a>So erstellen Sie eine Firewallregel  
  
1.  Melden Sie sich als Administrator auf dem Computer an, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.  
  
2.  Klicken Sie im **Startmenü**auf **Ausführen**, geben Sie ein `wf.msc` , und klicken Sie auf **OK**.  
  
3.  Klicken Sie im Dialogfeld **Benutzerkontensteuerung** auf **Weiter** , um unter Verwendung der Administratoranmeldeinformationen das Snap-In der Windows-Firewall mit erweiterter Sicherheit zu öffnen.  
  
4.  Bestätigen Sie auf der Seite **Übersicht** , dass die Windows-Firewall aktiv ist.  
  
5.  Klicken Sie im linken Bereich auf **Eingehende Regeln**.  
  
6.  Klicken Sie mit der rechten Maustaste auf **Eingehende Regeln**, und klicken Sie anschließend auf **Neue Regel** , um den **Assistenten für neue eingehende Regel**zu öffnen.  
  
7.  Sie können eine Regel für das Programm [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen. Da in diesem Beispiel jedoch ein fester Port verwendet wird, wählen Sie **Port**aus, und klicken Sie anschließend auf **Weiter**.  
  
8.  Wählen Sie auf der Seite **Protokolle und Ports** die Option **TCP**aus.  
  
9. Wählen Sie **Angegebene lokale Ports**aus. Geben Sie die durch Kommas getrennten Portnummern ein, und klicken Sie anschließend auf **Weiter**. In diesem Beispiel konfigurieren Sie den Standardport, geben Sie daher `1433` ein.  
  
10. Überprüfen Sie die Optionen auf der Seite **Aktion** . In diesem Beispiel verwenden Sie nicht die Firewall, um sichere Verbindungen zu gewährleisten. Klicken Sie daher auf **Verbindung zulassen**und anschließend auf **Weiter**.  
  
    > [!NOTE]  
    >  Möglicherweise sind für die Umgebung sichere Verbindungen erforderlich. Wenn Sie eine der Optionen für sichere Verbindungen auswählen, müssen Sie möglicherweise ein Zertifikat und die Option **Verschlüsselung erzwingen** konfigurieren. Weitere Informationen zu sicheren Verbindungen finden Sie unter [Aktivieren von verschlüsselten Verbindungen mit der Datenbank-Engine &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)[Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine & #40; SQL Server-Konfigurations-Manager & #41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
11. Wählen Sie auf der Seite **Profil** mindestens ein Profil für die Regel aus. Wenn Sie mit Firewallprofilen nicht vertraut sind, klicken Sie im Firewallprogramm auf den Link **Weitere Informationen zu Profilen** .  
  
    -   Wenn der Computer ein Server und nur dann verfügbar ist, wenn er mit einer Domäne verbunden ist, wählen Sie **Domäne**aus, und klicken Sie anschließend auf **Weiter**.  
  
    -   Wenn es sich bei dem Computer um ein mobiles Gerät (z. B. um einen Laptop) handelt, verwendet er wahrscheinlich mehrere Profile, um eine Verbindung mit unterschiedlichen Netzwerken herzustellen. Bei einem mobilen Computer können Sie unterschiedliche Zugriffsmöglichkeiten für verschiedene Profile konfigurieren. Zum Beispiel können Sie einen Zugriff gewähren, wenn der Computer das Domänenprofil verwendet, und verweigern, wenn er das öffentliche Profil verwendet.  
  
12. Geben Sie auf der Seite **Name** einen Namen und eine Beschreibung für die Regel ein, und klicken Sie dann auf **Fertig stellen**.  
  
13. Wiederholen Sie diese Prozedur, um für jede IP-Adresse, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, eine weitere Regel zu erstellen.  
  
 Nachdem Sie eine oder mehrere Regeln erstellt haben, führen Sie die folgenden Schritte aus, um jede IP-Adresse auf dem Computer zu konfigurieren und eine Regel zu verwenden.  
  
#### <a name="to-configure-the-firewall-rule-for-a-specific-ip-addresses"></a>So konfigurieren Sie die Firewallregel für eine bestimmte IP-Adresse  
  
1.  Klicken Sie in der **Windows-Firewall mit erweiterter Sicherheit** auf der Seite **Eingehende Regeln**mit der rechten Maustaste auf die Regel, die Sie gerade erstellt haben, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Wählen Sie im Dialogfeld **Regeleigenschaften** die Registerkarte **Bereich** aus.  
  
3.  Wählen Sie im Bereich **Lokale IP-Adresse** die Option **Diese IP-Adressen**aus, und klicken Sie dann auf **Hinzufügen**.  
  
4.  Wählen Sie im Dialogfeld **IP-Adresse** die Option **Diese IP-Adresse oder Subnetz**aus, und geben Sie anschließend eine der IP-Adressen ein, die Sie konfigurieren möchten.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Wählen Sie im Bereich **Remote-IP-Adresse** die Option **Diese IP-Adressen**aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
7.  Verwenden Sie das Dialogfeld **IP-Adresse** , um die Konnektivität für die ausgewählte IP-Adresse des Computers zu konfigurieren. Sie können Verbindungen zu angegebenen IP-Adressen, Bereichen von IP-Adressen, ganzen Subnetzen oder bestimmten Computern aktivieren. Um diese Option ordnungsgemäß zu konfigurieren, müssen Sie sich mit dem Netzwerk gut auskennen. Informationen über das Netzwerk erhalten Sie vom Netzwerkadministrator.  
  
8.  Um das Dialogfeld **IP-Adresse** zu schließen, klicken Sie auf **OK**, und klicken Sie dann auf **OK** , um das Dialogfeld **Regeleigenschaften** zu schließen.  
  
9. Um die anderen IP-Adressen auf einem mehrfach vernetzten Computer zu konfigurieren, wiederholen Sie diesen Vorgang mit einer anderen IP-Adresse und einer anderen Regel.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Browserdienst &#40;Datenbank-Engine und SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)   
 [Verbindungsaufbau mit SQL Server über einen Proxyserver &#40;SQL Server-Konfigurations-Manager&#41;](../../relational-databases/sql-server-configuration-manager.md)  
  
  
