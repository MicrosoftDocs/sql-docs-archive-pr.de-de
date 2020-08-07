---
title: Upgrade auf SQL Server 2014 mit dem Installations-Assistenten (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading Database Engine
- Database Engine [SQL Server], upgrading
ms.assetid: cef118a5-a7ce-4bfa-8b9d-c81996284cfc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 998532fd8cc69a3611ffa2b7d6da37521bb4d363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616143"
---
# <a name="upgrade-to-sql-server-2014-using-the-installation-wizard-setup"></a>Aktualisieren auf SQL Server 2014 mithilfe des Installations-Assistenten (Setup)
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installations-Assistent enthält eine Funktionsstruktur zum Upgrade von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten: Sie können [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auch parallel zu einer früheren Version installieren oder vorhandene Datenbanken und Konfigurationseinstellungen aus einer früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version migrieren und auf eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] anwenden.  
  
 Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md)  
  
-   [Arbeiten mit mehreren Versionen und Instanzen von SQL Server](../../sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
  
-   [Aktualisieren einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)  
  
-   [Installieren von SQL Server 2014 von der Eingabeaufforderung](install-sql-server-from-the-command-prompt.md)  
  
-   [Verwenden des Assistenten zum Kopieren von Datenbanken](../../relational-databases/databases/use-the-copy-database-wizard.md)  
  
> [!NOTE]  
>  Das Upgrade einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wird auf Computern mit [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 nicht unterstützt. Weitere Informationen zu Server Core-Installationen finden Sie unter [Installieren von SQL Server 2014 auf Server Core](install-sql-server-on-server-core.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Sie müssen Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat und ein lokaler Administrator ist.  
  
 Lesen Sie vor dem Upgrade von [!INCLUDE[ssDE](../../includes/ssde-md.md)] die folgenden Themen:  
  
-   [Upgrade auf SQL Server 2014](upgrade-sql-server.md)  
  
-   [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Überprüfen der Parameter für die Systemkonfigurationsprüfung](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../sql-server-database-engine-backward-compatibility.md)  
  
> [!WARNING]  
>  Sie können die zu aktualisierenden Funktionen nicht ändern und während des Aktualisierungsvorgangs keine Funktionen hinzufügen. Weitere Informationen zum Hinzufügen von Funktionen zu einer aktualisierten Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nach Abschluss des Upgradevorgangs finden Sie unter [Hinzufügen von Funktionen zu einer Instanz von SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md).  
  
## <a name="procedure"></a>Verfahren  
  
#### <a name="to-upgrade-to-sscurrent"></a>So aktualisieren Sie auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
1.  Legen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedium ein, und doppelklicken Sie im Stammordner auf Setup.exe. Wenn Sie eine Installation über eine Netzwerkfreigabe ausführen möchten, wechseln Sie in der Freigabe zum Stammordner, und doppelklicken Sie auf Setup.exe.  
  
2.  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationscenter wird vom Installations-Assistenten ausgeführt. Um eine vorhandene Instanz von zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , klicken Sie im linken Navigationsbereich auf **Installation** , und klicken Sie dann auf **Upgrade von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] **.  
  
3.  Aktivieren Sie auf der Seite für den Product Key eine Option, um anzugeben, ob Sie auf eine kostenlose Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisieren oder ob Sie über einen PID-Schlüssel für eine Produktionsversion des Produkts verfügen. Weitere Informationen finden Sie unter [Editionen und Komponenten von SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) und [unterstützte Versions-und Editions Upgrades](supported-version-and-edition-upgrades.md).  
  
4.  Lesen Sie auf der Seite Lizenzbedingungen den Lizenzvertrag, und aktivieren Sie das Kontrollkästchen **Ich akzeptiere die Lizenzbedingungen** , wenn Sie diesen zustimmen. Klicken Sie anschließend auf **Weiter**. Falls Sie zur Verbesserung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beitragen möchten, können Sie auch die Option zur Funktionsverwendung aktivieren und Berichte an [!INCLUDE[msCoName](../../includes/msconame-md.md)]senden.  
  
5.  Im Fenster Globale Regeln wechselt Setup automatisch weiter zum Fenster Produktupdates, sofern keine Regelfehler auftreten.  
  
6.  Die Seite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update wird als Nächstes angezeigt, wenn das Kontrollkästchen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update in Systemsteuerung\Alle Systemsteuerungselemente\Windows Update\Einstellungen ändern nicht aktiviert ist. Wenn Sie die Seite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update mit einem Häkchen markieren, ändern sich die Computereinstellungen, und beim Suchen nach Windows Update werden die neuesten Updates angezeigt.  
  
7.  Auf der Seite für Produktupdates werden die neuesten verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produktupdates angezeigt. Wenn Sie die Updates nicht einschließen möchten, deaktivieren Sie das Kontrollkästchen **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Produktupdates einschließen**. Wenn keine Produktupdates ermittelt wurden, zeigt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup diese Seite nicht an und geht automatisch zur Seite **Setupdateien installieren** über.  
  
8.  Auf der Seite "Setupdateien installieren" wird der Status angezeigt, während die Setupdateien heruntergeladen, extrahiert und installiert werden. Wenn ein Update für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup gefunden und angegeben wird, dass das Update eingeschlossen werden soll, wird dieses Update ebenfalls installiert.  
  
9. Im Fenster Upgradeegeln wechselt Setup automatisch weiter zum Fenster Instanz auswählen, sofern keine Regelfehler auftreten.  
  
10. Geben Sie auf der Seite Instanz auswählen die zu aktualisierende Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an. Zum Aktualisieren der Verwaltungstools und freigegebenen Funktionen wählen Sie **Nur freigegebene Funktionen aktualisieren**.  
  
11. Auf der Seite Funktionen auswählen sind die Funktionen, die aktualisiert werden sollen, bereits markiert. Nach Auswahl des Funktionsnamens wird im rechten Bereich eine Beschreibung für die einzelnen Komponentengruppen angezeigt.  
  
     Die erforderlichen Komponenten für die ausgewählten Funktionen werden im rechten Bereich angezeigt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup installiert die erforderlichen Komponenten, die nicht bereits während des Installationsschritts installiert werden, der im weiteren Verlauf dieser Prozedur beschrieben wird.  
  
    > [!NOTE]  
    >  Wenn Sie sich für das Upgrade der freigegebenen Features entschieden haben, indem Sie **\<Upgrade shared features only>** auf der Seite **Instanz auswählen** ausgewählt haben, sind auf der Seite „Featureauswahl“ alle freigegebenen Features vorab ausgewählt. Alle freigegebenen Komponenten werden gleichzeitig aktualisiert.  
  
12. Geben Sie auf der Instanzkonfigurationsseite die Instanz-ID für die Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an.  
  
     **Instanz-ID** – Standardmäßig wird der Instanzname als Instanz-ID verwendet. So werden Installationsverzeichnisse und Registrierungsschlüssel für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]identifiziert. Dies ist der Fall für Standardinstanzen und benannte Instanzen. Bei einer Standardinstanz lauten Instanzname und Instanz-ID MSSQLSERVER. Wenn Sie nicht die Standard-Instanz-ID verwenden möchten, geben Sie im Textfeld **Instanz-ID** einen Wert an.  
  
     Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Service Packs und Updates werden für jede Komponente einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]übernommen.  
  
     **Installierte Instanzen**: Im Raster werden Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt, die sich auf dem Computer befinden, auf dem das Setup ausgeführt wird. Wenn bereits eine Standardinstanz auf dem Computer installiert ist, muss eine benannte Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]installiert werden.  
  
13. Der Ablauf für die weiteren Vorgänge dieses Themas ist von den Funktionen abhängig, die Sie für die Installation angegeben haben. Je nach Auswahl werden möglicherweise nicht alle Seiten angezeigt.  
  
14. Auf der Seite „Serverkonfiguration – Dienstkonten“ werden die Standarddienstkonten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste angezeigt. Welche Dienste tatsächlich auf dieser Seite konfiguriert werden, ist von den zu aktualisierenden Funktionen abhängig.  
  
     Authentifizierung und Anmeldeinformationen werden aus der vorherigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz übernommen. Sie können allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten dasselbe Anmeldekonto zuweisen, oder Sie können jedes Dienstkonto einzeln konfigurieren. Außerdem können Sie angeben, ob Dienste automatisch starten sollen, manuell gestartet werden oder deaktiviert sind. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, die Dienstkonten einzeln zu konfigurieren, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten die Berechtigungen zu gewähren, die mindestens erforderlich sind, um ihre Tasks auszuführen. Weitere Informationen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../configure-windows/configure-windows-service-accounts-and-permissions.md)betreffen.  
  
     Um für alle Dienstkonten in dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dasselbe Anmeldekonto anzugeben, geben Sie im Feld unten auf dieser Seite die entsprechenden Anmeldeinformationen ein.  
  
     **Sicherheitshinweis:** [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
     Wenn Sie die Angabe der Anmeldeinformationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste abgeschlossen haben, klicken Sie auf **Weiter**.  
  
15. Geben Sie auf der Seite Upgradeoptionen für die Volltextsuche die Upgradeoptionen für die zu aktualisierenden Datenbanken an. Weitere Informationen finden Sie unter [Upgradeoptionen für die Volltextsuche](../../sql-server/install/full-text-search-upgrade-options.md).  
  
16. Im Fenster Funktionsregeln wird automatisch fortgefahren, wenn alle Regeln gültig sind.  
  
17. Auf der Seite Das Upgrade kann jetzt ausgeführt werden wird eine Strukturansicht der Installationsoptionen angezeigt, die während des Setups angegeben wurden. Klicken Sie zum Fortsetzen des Vorgangs auf **Installieren**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup installiert zuerst die erforderlichen Komponenten für die ausgewählten Funktionen und dann die Funktionen.  
  
18. Während der Installation wird auf der Seite Installationsstatus der Status angezeigt, sodass Sie während der Installation den Installationsstatus überwachen können.  
  
19. Nach der Installation bietet die Seite Abgeschlossen einen Link zur zusammenfassenden Protokolldatei für die Installation und andere wichtige Hinweise. Klicken Sie auf **Schließen**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Installation von abzuschließen.  
  
20. Starten Sie den Computer neu, falls Sie dazu aufgefordert werden. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen zu Setupprotokolldateien finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](view-and-read-sql-server-setup-log-files.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Führen Sie nach dem Aktualisieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die folgenden Tasks aus:  
  
-   **Registrieren Sie Ihre Server**: Beim Upgrade werden die Registrierungseinträge für die frühere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz entfernt. Nach dem Aktualisieren müssen Sie die Server neu registrieren.  
  
-   **Aktualisieren Sie die Statistiken**: Zum Optimieren der Abfrageleistung wird empfohlen, nach dem Upgrade die Statistiken für alle Datenbanken zu aktualisieren. Aktualisieren Sie mithilfe der gespeicherten Prozedur `sp_updatestats` die Statistiken in benutzerdefinierten Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken.  
  
-   **Konfigurieren Sie Ihre neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation**: Zur Verringerung der Angriffsfläche eines Systems werden zentrale Dienste und Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selektiv installiert und aktiviert. Weitere Informationen zur Oberflächenkonfiguration finden Sie in der Infodatei für diese Version.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Upgrade auf SQL Server 2014](upgrade-sql-server.md)   
 [Abwärtskompatibilität](../../getting-started/backward-compatibility.md)  
  
  
