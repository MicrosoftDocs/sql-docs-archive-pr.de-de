---
title: Übersicht über SQL Server Wartungs Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6a9fd19b-2367-4908-b638-363b1e929e1e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30610b1a1016b3343c2264e885847de6f2c233fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620724"
---
# <a name="overview-of-sql-server-servicing-installation"></a>Übersicht über die SQL Server-Wartungsinstallation
  Sie können ein Update auf eine beliebige vorhandene [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Komponente mit einem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Wartungsupdate anwenden. Wenn die Versionsebene einer vorhandenen Komponente von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] neuer ist als die Versionsebene des Updates, schließt das Setupprogramm diese Komponente vom Update aus. Weitere Informationen zum Anwenden eines Wartungsupdates finden Sie unter [Installieren von SQL Server 2014-Wartungs Updates](../../database-engine/install-windows/install-sql-server-servicing-updates.md).  
  
 Beim Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Updates gelten die folgenden Überlegungen:  
  
-   Alle Funktionen, die zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gehören, müssen gleichzeitig aktualisiert werden. Wenn Sie beispielsweise [!INCLUDE[ssDE](../../includes/ssde-md.md)]aktualisieren, müssen Sie auch die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Komponente und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponente aktualisieren, sofern diese als Teil derselben Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert sind. Freigegebene Funktionen, wie Verwaltungstools, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] müssen stets mit dem aktuellen Update aktualisiert werden. Wenn eine Komponente oder Instanz in der Funktionsstruktur nicht ausgewählt ist, wird die Komponente oder Instanz nicht aktualisiert.  
  
-   Standardmäßig [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] werden Update Protokolldateien unter% Program Files% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\setup Bootstrap\LOG gespeichert \\ .  
  
-   Es besteht jetzt die Möglichkeit, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup auf den Originalmedien ein Update einzuschließen, sodass die Originalmedien und das Update gleichzeitig ausgeführt werden. Weitere Informationen finden Sie unter [What es New in SQL Server Installation](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md).  
  
-   Es wird empfohlen, vor dem Ausführen eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Wartungsupdates eine Sicherung der Daten in Erwägung zu ziehen.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Updates stehen über [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update zur Verfügung. Es wird empfohlen, regelmäßig nach Updates zu suchen, damit Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stets aktuell und sicher ist. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 wird als vollständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation bereitgestellt. Anstatt das Service Pack im ausführbaren Standardpatchpaket bereitzustellen, das auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RTM-Instanzen angewendet wird, ist für diese Version ein (aus zwei Dateien bestehendes) Installationspaket verfügbar. Bei der Ausführung des Pakets wird eine neue Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit vorinstalliertem SP1 installiert.  
  
## <a name="requirements-and-known-issues"></a>Anforderungen und bekannte Probleme  
 Der empfohlene erforderliche Speicherplatz beträgt etwa das 2,5-fache der Paketgröße, um das Paket installieren, herunterladen und extrahieren zu können. Nach dem Installieren eines Service Packs können Sie das heruntergeladene Paket entfernen. Die temporären Dateien werden automatisch entfernt.  
  
 **Erfahren Sie mehr über bekannte Probleme:** Weitere Informationen zu den bekannten Problemen in der aktuellen Version entnehmen Sie bitte den entsprechenden Versionshinweisen unter: [Versionsanmerkungen für SQL Server](https://msdn.microsoft.com/f617a0af-92dd-47aa-82c3-f51b1346bcd8).  
  
## <a name="installation-overview"></a>Übersicht über die Installation  
 In diesem Abschnitt wird die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installation für kumulierte Updates und Service Packs einschließlich der folgenden Themen beschrieben:  
  
-   Vorbereiten einer Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates  
  
-   Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates  
  
-   Neustarten von Diensten und Anwendungen  
  
### <a name="prepare-for-a-sscurrent-update-installation"></a>Vorbereiten einer Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates  
 Es wird dringend empfohlen, dass Sie wie folgt vorgehen, bevor Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates installieren:  
  
-   **Sichern der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Datenbanken** : Sichern Sie vor der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates die `master` `msdb` `model` Datenbanken, und. Durch die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates werden diese Datenbanken geändert. Sie werden damit inkompatibel mit früheren Versionen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Sicherungen dieser Datenbanken sind erforderlich, wenn Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ohne diese Updates erneut installieren möchten.  
  
     Das Sichern der Benutzerdatenbanken ist ebenfalls empfehlenswert.  
  
    > [!IMPORTANT]  
    >  Wenn Sie Updates auf Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anwenden, die Teil einer Replikationstopologie sind, müssen Sie vor dem Anwenden der Updates die replizierten Datenbanken zusammen mit den Systemdatenbanken sichern.  
  
-   **Sichern der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbanken, der Konfigurationsdatei und des Repository** : vor dem Aktualisieren einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sollten Sie Folgendes sichern:  
  
    -   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken. Diese werden standardmäßig unter "c:\Programme \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \msas12. \<InstanceID> " installiert. \OLAP\Data \\ . Für die wow-Installation ist der Standardpfad c:\ProgramFiles (x86) \ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \msas12. \<InstanceID> . \OLAP\Data \\ .  
  
    -   Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Konfigurationseinstellung in der Konfigurationsdatei msmdsrv.ini. Standardmäßig befindet sich diese Datei im Verzeichnis "c:\Programme \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \msas12. \<InstanceID> ". Verzeichnis \olap\config\.  
  
    -   (Optional) Die Datenbank, die das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Repository enthält. Dieser Schritt ist nur erforderlich, wenn [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Verwendung der Decision Support Objects (DSO)-Bibliothek konfiguriert wurde.  
  
    > [!NOTE]  
    >  Ohne eine Sicherung der Datenbanken, der Konfigurationsdatei und des Repositorys von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist es nicht möglich, eine aktualisierte Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf die vorherige Version zurückzusetzen.  
  
-   Stellen Sie sicher **, dass die System Datenbanken über ausreichend freien Speicherplatz verfügen** . wenn die Option für die automatische Vergrößerung nicht für die `master` -und die- `msdb` Systemdatenbank ausgewählt ist, müssen diese Datenbanken jeweils mindestens 500 KB freien Speicherplatz aufweisen. Führen Sie die gespeicherte Systemprozedur `sp_spaceused` für die Datenbanken `master` und `msdb` aus, um zu überprüfen, ob die Datenbanken über genügend Speicherplatz verfügen. Falls der nicht zugeordnete Speicherplatz in einer der Datenbanken weniger als 500 KB beträgt, sollten Sie die Datenbank vergrößern.  
  
-   **Dienste und Anwendungen** verhindern: um einen möglichen Neustart des Systems zu vermeiden, müssen Sie vor der Installation von Updates alle Anwendungen und Dienste, die Verbindungen mit den zu aktualisierenden Instanzen von herstellen, Abbrechen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Dazu gehören [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [Starten, Beenden, Anhalten, Fortsetzen und Neustarten von SQL Server-Diensten](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
    > [!NOTE]  
    >  In einer Failoverclusterumgebung können Sie keine Dienste beenden. Weitere Informationen hierzu finden Sie weiter unten in diesem Thema im Abschnitt zur Failoverclusterinstallation.  
  
-   Damit der Computer nach der Installation des Updates nicht neu gestartet werden muss, zeigt das Setup eine Liste der Prozesse an, die Dateien sperren. Wenn das Setupprogramm für das Update während der Installation einen Dienst beenden muss, wird der Dienst nach Abschluss der Installation neu gestartet.  
  
-   Wenn vom Setup festgestellt wird, dass Dateien während der Installation blockiert werden, müssen Sie den Computer möglicherweise nach dem Fertigstellen der Installation erneut starten. Gegebenenfalls werden Sie aufgefordert, den Computer neu zu starten.  
  
### <a name="install-sscurrent-updates"></a>Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Updates  
 In diesem Abschnitt wird der Installationsvorgang beschrieben.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Updates müssen unter einem Konto installiert werden, das über Administratorrechte auf dem Computer verfügt, auf dem diese installiert werden. Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.  
  
#### <a name="starting-a-sscurrent-update"></a>Starten eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Updates  
 Um ein [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Update zu installieren, führen Sie die selbst extrahierende Paketdatei aus.  
  
 Kumulatives Update Paket (Cu): \<SQLServer2014> -KBXXXXXX-*PPP*. exe  
  
 Service Pack-Paket (PCU): \<SQLServer2014> \<SPx> -KBxxxxxx-PPP-LLL.exe  
  
-   x gibt die Nummer des Service Packs an.  
  
-   PPP gibt die spezifische Plattform an.  
  
-   "LLL" steht für die Abkürzung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sprache, z. B. "ENU" im Fall von Englisch.  
  
 Informationen zum Anwenden von Updates auf Komponenten von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], die Teil eines Failoverclusters sind, finden Sie im Abschnitt zur Failoverclusterinstallation. Weitere Informationen zum Ausführen einer Update Installation im unbeaufsichtigten Modus finden Sie unter [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
####  <a name="product-updates-in-sscurrent-installation"></a><a name="Slipstream"></a>Produkt Updates bei der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation  
 Produktupdate ist eine Funktion in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setup. Mit ihr werden die neuesten Produktupdates in die Installation des Hauptprodukts integriert, sodass das Hauptprodukt und geeignete Updates gleichzeitig installiert werden. Product Update kann [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, Windows Server Update Services (WSUS), einen lokalen Ordner oder eine Netzwerkfreigabe nach anwendbaren Updates durchsuchen.  Nachdem Setup die neuesten Versionen der anwendbaren Updates gefunden hat, lädt es diese herunter und integriert sie in den aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsvorgang. Das Produktupdate kann ein kumulatives Update, Service Pack oder Service Pack plus kumulatives Update einziehen. Die Produktupdatefunktionalität ist eine Erweiterung der Slipstream-Funktionalität, die in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1 verfügbar war.  
  
## <a name="updating-a-prepared-image-of-ssnoversion"></a>Aktualisieren eines vorbereiteten Images von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Sie können ein Update auf eine nicht konfigurierte vorbereitete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anwenden, ohne die Konfiguration der vorbereiteten Instanz abzuschließen. Im Folgenden werden verschiedene Methoden für die Anwendung eines Updates auf eine vorbereitete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erklärt:  
  
-   Aktualisieren einer zuvor vorbereiteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
     Updates für eine vorbereitete Instanz können vor der Konfiguration angewendet werden. Das Updatepaket erkennt, dass die Instanz im vorbereiteten Status ist und wendet den Patch für die vorbereitete Instanz an, ohne die Konfiguration abzuschließen.  
  
-   Updates für eine vorbereitete Instanz mittels [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update:  
  
     Sie können Updates auf eine vorbereitete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mittels [!INCLUDE[msCoName](../../includes/msconame-md.md)] Updates anwenden. Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update-Paket erkennt, dass die Instanz im vorbereiteten Status ist, und wendet den Patch für die vorbereitete Instanz an, ohne die Konfiguration abzuschließen.  
  
 Wenn Sie ein vorbereitetes Image von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisieren, müssen Sie den InstanceID-Parameter angeben. Weitere Informationen und eine Beispielsyntax finden Sie unter [Installing Updates from the Command Prompt](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md).  
  
## <a name="updating-a-completed-image-of-ssnoversion"></a>Aktualisieren eines abgeschlossenen Images von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Beim Update einer abgeschlossenen und konfigurierten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die gleichen Prozesse angewendet wie für jede andere installierte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="rebuilding-a-sscurrent-failover-cluster-node"></a>Neuerstellen eines [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Failoverclusterknotens  
 Führen Sie die folgenden Schritte aus, wenn Sie einen Knoten im Failovercluster nach der Anwendung von Updates neu erstellen müssen:  
  
1.  Erstellen Sie den Knoten im Failovercluster neu. Weitere Informationen zum Neuerstellen eines Knotens finden Sie unter [Recover from Failover Cluster Instance Failure](../failover-clusters/windows/recover-from-failover-cluster-instance-failure.md).  
  
2.  Führen Sie das ursprüngliche [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Setupprogramm aus, um [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf dem Failoverclusterknoten zu installieren.  
  
3.  Führen Sie das Setup für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates auf dem hinzugefügten Knoten aus.  
  
## <a name="restart-services-and-applications"></a>Neustarten von Diensten und Anwendungen  
 Nach Abschluss des Setups werden Sie möglicherweise aufgefordert, den Computer neu zu starten. Nach dem Neustart des Systems oder nach Abschluss des Setups ohne erforderlichen Neustart können Sie den Knoten **Dienste** in der Systemsteuerung verwenden, um die Dienste neu zu starten, die Sie vor dem Anwenden der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Updates beendet haben. Dazu gehören Dienste wie Distributed Transaction Coordinator und die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search-Dienste oder entsprechende instanzenspezifische Dienste.  
  
 Starten Sie die Anwendungen erneut, die Sie vor dem Ausführen des Setups für das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Update beendet haben. Es ist auch sinnvoll, sofort nach der erfolgreichen Installation eine weitere Sicherung der aktualisierten Datenbanken `master`, `msdb` und `model` zu erstellen.  
  
## <a name="uninstalling-updates-from-sscurrent"></a>Deinstallieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Updates  
 Kumulative Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder Service Packs können in der Systemsteuerung mithilfe der Option **Programme und Funktionen** deinstalliert werden. Um die Liste der installierten Updates anzuzeigen, öffnen Sie **Installierte Updates** , indem Sie auf die Schaltfläche **Start**, auf **Systemsteuerung**, **Programme**und dann unter **Programme und Funktionen**auf Installierte Updates anzeigen klicken. Die kumulativen Updates werden einzeln aufgelistet. Wenn jedoch ein Service Pack installiert wird, das höher als die kumulativen Updates ist, werden die Einträge der kumulativen Updates ausgeblendet und stehen nur zur Verfügung, wenn das Service Pack deinstalliert wird.  
  
 Um alle Service Packs und Updates zu deinstallieren, müssen Sie mit dem aktuellen Update oder Service Pack, das auf die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewendet wurde, beginnen und anschließend die niedrigeren Versionen deinstallieren. In den folgenden Beispielen verfügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Schluss über das kumulative Update 1, nachdem die Deinstallation der anderen Service Packs und Updates abgeschlossen wurde:  
  
-   Bei einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , auf der das kumulative Update 1 und SP1 installiert sind, müssen Sie SP1 deinstallieren.  
  
-   Bei einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , auf der das kumulative Update 1, SP1 und das kumulative Update 2 installiert sind, deinstallieren Sie zunächst das kumulative Update 2 und anschließend SP1.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Installieren von SQL Server 2014-Wartungs Updates](../../database-engine/install-windows/install-sql-server-servicing-updates.md)   
 [Überprüfen einer SQL Server-Installation](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
