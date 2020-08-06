---
title: Konfigurationsoptionen für den Serverarbeitsspeicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Virtual Memory Manager
- max server memory option
- virtual memory [SQL Server]
- VMM
- server memory options [SQL Server]
- servers [SQL Server], memory
- buffer pools [SQL Server]
- min server memory option
- manual memory options [SQL Server]
- memory [SQL Server], servers
ms.assetid: 29ce373e-18f8-46ff-aea6-15bbb10fb9c2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a4bb354b78d25c6667e9ff67c6eda697a0369e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723058"
---
# <a name="server-memory-configuration-options"></a>Konfigurationsoptionen für den Serverarbeitsspeicher
  Mit den beiden Arbeitsspeicheroptionen für den Server, **Min. Serverarbeitsspeicher** und **Max. Serverarbeitsspeicher**, können Sie die Größe des Arbeitsspeichers (in Megabytes) umkonfigurieren, der vom SQL Server-Speicher-Manager für einen von einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendeten SQL Server-Prozess verwaltet wird.  
  
 Die Standardeinstellung für **Min. Serverarbeitsspeicher** ist 0, die für **Max. Serverarbeitsspeicher** 2147483647 MB. Standardmäßig können die Arbeitsspeicheranforderungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anhand der verfügbaren Systemressourcen dynamisch geändert werden.  
  
> [!NOTE]  
> Wenn die Option **Max. Serverarbeitsspeicher** auf den Minimalwert festgelegt ist, kann dies die Leistung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erheblich einschränken und sogar den Start von SQL Server verhindern. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nach dem Ändern dieser Option nicht gestartet werden kann, müssen Sie den Start mithilfe der Startoption **-f** durchführen und die Option **Max. Serverarbeitsspeicher** auf ihren vorherigen Wert zurücksetzen. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md).  
  
 Bei dynamischer Verwendung des Arbeitsspeichers von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird der im System verfügbare Arbeitsspeicher in regelmäßigen Abständen abgefragt. Bei Beibehaltung dieses freien Arbeitsspeichers werden Auslagerungsvorgänge durch das Betriebssystem verhindert. Wenn weniger freier Arbeitsspeicher vorhanden ist, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arbeitsspeicher für das Betriebssystem frei. Wenn mehr Arbeitsspeicher frei ist, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auch mehr Speicher reservieren. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fügt Arbeitsspeicher nur dann hinzu, wenn durch die Arbeitsauslastung mehr Arbeitsspeicher erforderlich ist. Bei einem ruhenden Server wird die Größe seines virtuellen Adressraums nicht vergrößert.  
  
 Beispiel B enthält eine Abfrage, welche den derzeit verwendeten Arbeitsspeicher zurückgibt. **Max. Serverarbeitsspeicher** steuert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Speicherzuweisung, einschließlich Pufferpool, Arbeitsspeicherkompilierung, alle Caches, Arbeitsspeicherzuweisungen, Sperren-Manager-Speicher und Clr-Speicher (im Wesentlichen alle Arbeitsspeicherclerks in **sys.dm_os_memory_clerks**). Arbeitsspeicher für Threadstapel, Arbeitsspeicherheaps, andere verknüpfte Serveranbieter als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]und durch Nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -DLL zugewiesener Speicher werden nicht von max. Serverarbeitsspeicher kontrolliert.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet die Arbeitsspeicherbenachrichtigungs-API **querymemoryresourcenotifizierung** , um zu bestimmen, wann der SQL Server Speicher-Manager Arbeitsspeicher zuweisen und Speicher freigeben kann.  
  
 Grundsätzlich empfiehlt es sich, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine dynamische Verwendung des Arbeitsspeichers zuzulassen. Sie können die Speicheroptionen jedoch auch manuell festlegen und den Umfang des für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifbaren Arbeitsspeichers einschränken. Bevor Sie den Umfang des Arbeitsspeichers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]festlegen, sollten Sie die geeignete Arbeitsspeichereinstellung ermitteln. Ziehen Sie dazu vom gesamten physischen Speicher den Arbeitsspeicher ab, der für das Betriebssystem und alle weiteren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlich ist. (Falls der Computer nicht vollständig für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]reserviert ist, müssen Sie zusätzlich auch den für andere Verwendungen des Systems benötigten Arbeitsspeicher abziehen.) Die Differenz entspricht der maximalen Arbeitsspeichergröße, die Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zuweisen können.  
  
## <a name="setting-the-memory-options-manually"></a>Manuelles Festlegen der Arbeitsspeicheroptionen  
Sie können die Serveroptionen **Min. Serverarbeitsspeicher** und **Max. Serverarbeitsspeicher** so festlegen, dass ein großer Bereich von Arbeitsspeicherwerten überdeckt wird. Diese Methode ist vor allem dann sinnvoll, wenn der System- oder Datenbankadministrator eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Abhängigkeit von den Arbeitsspeicheranforderungen anderer Anwendungen oder weiterer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die auf demselben Computer ausgeführt werden, konfigurieren möchte.

> [!NOTE]
> Bei **min server memory** und **max server memory** handelt es sich um erweiterte Optionen. Wenn Sie diese Einstellungen mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie diese nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Diese Einstellungen treten sofort ohne Neustart des Servers in Kraft.  
  
<a name="min_server_memory"></a> Mithilfe der Konfigurationsoption **min_server_memory** wird sichergestellt, dass für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicher-Manager einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Mindestmenge an Arbeitsspeicher verfügbar ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Allerdings wird die unter **Min. Serverarbeitsspeicher** angegebene Arbeitsspeichermenge von nicht gleich beim Start zugeordnet. Sobald der Wert für die Speicherauslastung aufgrund der Clientauslastung erreicht ist, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur dann Arbeitsspeicher freigeben, wenn der Wert für **Min. Serverarbeitsspeicher** reduziert wird. Wenn beispielsweise mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gleichzeitig auf dem gleichen Host ausgeführt werden können, legen Sie den Parameter „min_server_memory“ anstelle von „max_server_memory“ fest, um Arbeitsspeicher für eine Instanz zu reservieren. Ferner ist das Festlegen eines Werts für „min_server_memory“ in einer virtualisierten Umgebung entscheidend, um sicherzustellen, dass Arbeitsspeichermangel beim zugrundeliegenden Host nicht zu dem Versuch führt, Arbeitsspeicher aus dem Pufferpool eines virtuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Gastcomputers jenseits dessen abzuzweigen, was für eine vertretbare Leistung erforderlich ist.
 
> [!NOTE]  
> Allerdings kann nicht sichergestellt werden, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die in **min server memory** angegebene Arbeitsspeichermenge zuordnet. Wenn die in **min server memory**angegebene Arbeitsspeichermenge aufgrund der Serverlast zu keinem Zeitpunkt zugeordnet werden muss, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit weniger Arbeitsspeicher ausgeführt.  
  
<a name="max_server_memory"></a> Verwenden Sie **max_server_memory**, um sicherzustellen, dass beim Betriebssystem kein nachteiliger Arbeitsspeichermangel eintritt. Um den maximalen Serverarbeitsspeicher zu konfigurieren, überwachen Sie den Gesamtverbrauch des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozesses, um die Arbeitsspeicheranforderungen zu bestimmen. Hier folgen genauere Angaben für diese Berechnungen für eine Einzelinstanz:
 -  Reservieren Sie vom gesamten Arbeitsspeicher des Betriebssystems 1 GB–4 GB für das Betriebssystem selbst.
 -  Subtrahieren Sie dann das Äquivalent von potenziellen Speicher Belegungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] außerhalb der **maximalen Server Speicher** Kontrolle, die aus der **_Stapelgröße <sup>1</sup> \* berechnete maximale Arbeitsthreads <sup>2</sup> +-g Startparameter <sup>3</sup> _** besteht (oder standardmäßig 256 MB, wenn *-g* nicht festgelegt ist). Der Rest sollte die Einstellung „max_server_memory“ für die Einrichtung einer einzelnen Instanz bilden.
 
<sup>1</sup> Informationen zu den Threadstapelgrößen der einzelnen Architekturen finden Sie im [Handbuch zur Architektur der Speicherverwaltung](https://docs.microsoft.com/sql/relational-databases/memory-management-architecture-guide#stacksizes).

<sup>2</sup> Informationen zu den standardmäßig berechneten Arbeitsthreads für eine bestimmte Anzahl kategorisierter CPUs auf dem aktuellen Host finden Sie auf der Dokumentationsseite zum [Konfigurieren der Serverkonfigurationsoption Maximale Anzahl von Arbeitsthreads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md).

<sup>3</sup> Informationen zum Startparameter *-g* finden Sie auf der Dokumentationsseite zu [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md?view=sql-server-2014). Gilt nur für 32-Bit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] bis [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).

|Betriebssystemtyp|Mindestens zulässiger Arbeitsspeicher für **Max. Server Arbeitsspeicher**|  
|-------------|----------------------------------------------------------------|  
|32 Bit|64 MB|  
|64 Bit|128 MB| 

## <a name="how-to-configure-memory-options-using-sql-server-management-studio"></a>So konfigurieren Sie Speicheroptionen mit SQL Server Management Studio  
 Mit den beiden Arbeitsspeicheroptionen für den Server, **Min. Serverarbeitsspeicher** und **Max. Serverarbeitsspeicher**, können Sie den vom SQL Server-Speicher-Manager für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwalteten Umfang des Arbeitsspeichers (in MB) umkonfigurieren. Standardmäßig können die Arbeitsspeicheranforderungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anhand der verfügbaren Systemressourcen dynamisch geändert werden.  
  
### <a name="procedure-for-configuring-a-fixed-amount-of-memory"></a>Vorgehensweise beim Konfigurieren eines festen Arbeitsspeichers  
 **So legen Sie eine feste Arbeitsspeichergröße fest:**  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Speicher** -Knoten.  
  
3.  Geben Sie unter **Arbeitsspeicheroptionen für den Server**den gewünschten Wert für **Minimaler Serverarbeitsspeicher** und **Maximaler Serverarbeitsspeicher**ein.  
  
     Verwenden Sie die Standardeinstellungen, damit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Arbeitsspeicheranforderungen auf der Grundlage der verfügbaren Systemressourcen dynamisch ändert. Die Standardeinstellung für **Min. Server Arbeitsspeicher** ist 0, und die Standardeinstellung für **Max. Server Arbeitsspeicher** beträgt 2147483647 Megabyte (MB).  
  
## <a name="maximize-data-throughput-for-network-applications"></a>Maximieren des Datendurchsatzes in Netzwerkanwendungen  
 Um die Nutzung des Systemspeichers für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu optimieren, sollten Sie den Arbeitsspeicher einschränken, der vom System zur Zwischenspeicherung von Dateien verwendet wird. Stellen Sie zum Einschränken des Dateisystemcache sicher, dass die Option **Datendurchsatz für Dateifreigabe maximieren** deaktiviert ist. Sie können den kleinsten Dateisystemcache angeben, indem Sie **Verwendeten Arbeitsspeicher minimieren** oder **Lastenausgleich durchführen**auswählen.  
  
#### <a name="to-check-the-current-setting-on-your-operating-system"></a>So überprüfen Sie die aktuellen Einstellungen des Betriebssystems  
  
1.  Klicken Sie im **Startmenü**auf **Systemsteuerung**, doppelklicken Sie auf **Netzwerkverbindungen**, und doppelklicken Sie dann auf **LAN-Verbindung**.  
  
2.  Klicken Sie auf der Registerkarte **Allgemein** auf **Eigenschaften**, wählen Sie **Datei- und Druckerfreigabe für Microsoft-Netzwerke**aus, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wenn die Option **Datendurchsatz für Netzwerkanwendungen maximieren** ausgewählt ist, wählen Sie ggf. weitere Optionen aus. Klicken Sie auf **OK**, und schließen Sie alle noch geöffneten Dialogfelder.  
  
## <a name="lock-pages-in-memory"></a>Sperren von Seiten im Speicher  
 Mit dieser Windows-Richtlinie werden die Konten bestimmt, die einen Prozess zum Speichern von Daten im physischen Speicher verwenden können, um das systemgesteuerte Auslagern der Daten in den virtuellen Arbeitsspeicher zu vermeiden. Durch Sperren von Seiten im Arbeitsspeicher können Sie die Reaktionsfähigkeit des Servers möglicherweise auch nach Auslagerung von Arbeitsspeicherdaten auf die Festplatte aufrechterhalten. Die Option SQL Server **Lock pages in Memory** ist in 32-Bit-und 64-Bit-Instanzen der Standard Edition und höher auf ON festgelegt, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Wenn dem Konto mit den Berechtigungen zum Ausführen sqlservr.exe das Windows-Benutzerrecht "Locked pages in Memory" (lpim) erteilt wurde. In früheren Versionen von SQL Server ist beim Festlegen der Option zum Sperren von Seiten für eine 32-Bit-Instanz von SQL Server erforderlich, dass das Konto mit den Privilegien zum Ausführen von "sqlservr.exe" das LPIM-Benutzerrecht besitzt und die awe_enabled-Konfigurationsoption auf ON festgelegt wird.  
  
 Entfernen Sie zum Deaktivieren der Option **Sperren von Seiten im Speicher** für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benutzerrecht "Locked pages in Memory" für das SQL Server Start Konto.  
  
### <a name="to-disable-lock-pages-in-memory"></a>So deaktivieren Sie die Option "Sperren von Seiten im Speicher"  
 **So deaktivieren Sie die Option "Sperren von Seiten im Speicher":**  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**. Geben Sie im Feld **Öffnen** den Text ein `gpedit.msc` .  
  
     Das Dialogfeld **Gruppenrichtlinie** wird geöffnet.  
  
2.  Erweitern Sie in der Konsole **Gruppenrichtlinie** die Option **Computerkonfiguration**und dann **Windows-Einstellungen**.  
  
3.  Erweitern Sie **Sicherheitseinstellungen**und dann **Lokale Richtlinien**.  
  
4.  Wählen Sie den Ordner **Zuweisen von Benutzerrechten** aus.  
  
     Die Richtlinien werden im Detailbereich angezeigt.  
  
5.  Doppelklicken Sie im Detailbereich auf **Sperren von Seiten im Speicher**.  
  
6.  Wählen Sie im Dialogfeld **Lokale Sicherheitseinstellung** das Konto mit Privilegien zum Ausführen von "sqlservr.exe", und klicken Sie auf **Entfernen**.  
  
## <a name="virtual-memory-manager"></a>Manager für virtuellen Arbeitsspeicher  
 Die 32-Bit-Betriebssysteme bieten Zugriff auf einen virtuellen Adressraum von 4 GB. 2 GB des virtuellen Arbeitsspeichers sind für einzelne Prozesse reserviert und für Anwendungen verfügbar. 2 GB sind für die Verwendung durch das Betriebssystem reserviert. Alle Betriebssystemeditionen enthalten einen Schalter, mit dem Anwendungen der Zugriff auf einen virtuellen Adressraum von bis zu 3 GB gewährt und das Betriebssystem auf 1 GB beschränkt werden kann. Weitere Informationen zur Verwendung der Arbeitsspeicherkonfiguration mithilfe des Schalters finden Sie in der Windows-Dokumentation zur 4-GB-Optimierung (4 Gigabyte Tuning, 4GT). Wenn die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem 64-Bit-Betriebssystem ausgeführt wird, steht Benutzern der vollständige virtuelle Adressraum von 4 GB zur Verfügung.  
  
 Die zugesicherten Bereiche des Adressraums werden vom Windows-Manager für virtuellen Arbeitsspeicher (VMM, Virtual Memory Manager) dem verfügbaren physischen Arbeitsspeicher zugeordnet.  
  
 Weitere Informationen zur von anderen Betriebssystemen unterstützten Größe des physischen Speichers finden Sie in der Windows-Dokumentation "Arbeitsspeichergrenzwerte für Windows-Versionen" (möglicherweise in englischer Sprache).  
  
 Mit virtuellen Speichersystemen kann mehr physischer Arbeitsspeicher zugesichert werden, als tatsächlich vorhanden ist, sodass das Verhältnis von virtuellem zu physischem Arbeitsspeicher das Verhältnis 1:1 überschreiten kann. Auf diese Weise können größere Programme auf Computern mit verschiedenen Konfigurationen des physischen Arbeitsspeichers ausgeführt werden. Wenn jedoch deutlich mehr virtueller Arbeitsspeicher verwendet wird, als die kombinierten durchschnittlichen Workingsets aller Prozesse verwenden, kann dies zu einem ungünstigen Leistungsverhalten führen.  
  
 Bei **min server memory** und **max server memory** handelt es sich um erweiterte Optionen. Wenn Sie diese Einstellungen mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie diese nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Diese Einstellungen treten sofort ohne Neustart des Servers in Kraft.  
  
## <a name="running-multiple-instances-of-sql-server"></a>Ausführen mehrerer Instanzen von SQL Server  
 Wenn Sie mehrere Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]ausführen, stehen Ihnen zum Verwalten des Arbeitsspeichers drei Möglichkeiten zur Verfügung:  
  
-   Steuern Sie die Speicherauslastung mithilfe von **max server memory** . Richten Sie für jede Instanz Maximaleinstellungen ein, und achten Sie darauf, dass der gesamte zugeordnete Arbeitsspeicher nicht größer ist als der insgesamt auf dem Computer verfügbare physische Speicher. Es empfiehlt sich, den jeder Instanz zugeordneten Arbeitsspeicher proportional zur erwarteten Arbeitsauslastung oder Datenbankgröße zu bemessen. Dieser Ansatz hat den Vorteil, dass beim Starten neuer Prozesse oder Instanzen sofort freier Arbeitsspeicher für die Prozesse oder Instanzen zur Verfügung steht. Der Nachteil ist, wenn nicht alle Instanzen ausgeführt werden, dass keine der laufenden Instanzen den verbleibenden freien Arbeitsspeicher nutzen kann.  
  
-   Steuern Sie die Speicherauslastung mithilfe von **min server memory** . Richten Sie für jede Instanz Minimaleinstellungen ein, sodass die Summe dieser Mindestwerte 1 bis 2 GB unterhalb des gesamten physischen Speichers auf dem Computer liegt. Auch bei dieser Methode empfiehlt es sich, die Werte proportional zu der für die jeweilige Instanz erwarteten Arbeitsauslastung zu bemessen. Dieser Ansatz hat den Vorteil, dass die laufenden Instanzen den verbleibenden freien Arbeitsspeicher nutzen können, wenn nicht alle Instanzen gleichzeitig ausgeführt werden. Diese Vorgehensweise ist auch dann sinnvoll, wenn auf dem Computer ein weiterer speicherintensiver Prozess vorhanden ist, da sichergestellt ist, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zumindest eine angemessene Menge an Arbeitsspeicher erhält. Der Nachteil besteht darin, dass es beim Starten einer neuen Instanz (oder eines anderen Prozesses) ggf. etwas dauern kann, bis die laufenden Instanzen Speicher freigeben. Dies trifft vor allem dann zu, wenn die Instanzen zuerst noch geänderte Seiten in ihre jeweiligen Datenbanken zurückschreiben müssen.  
  
-   Unternehmen Sie nichts (dies wird nicht empfohlen). Die ersten Instanzen, denen eine Arbeitslast zugewiesen wird, weisen sich den gesamten Arbeitsspeicher zu. Instanzen im Leerlauf oder Instanzen, die später gestartet werden, müssen in dieser Situation u. U. mit einer minimalen Menge an Arbeitsspeicher auskommen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht nicht, die Speicherauslastung über mehrere Instanzen hinweg auszugleichen. Alle Instanzen antworten jedoch auf Signale der Windows-Arbeitsspeicherbenachrichtigung, um ihren Speicherbedarf anzupassen. Windows nimmt keinen Speicherausgleich bei Anwendungen vor, die über eine Arbeitsspeicherbenachrichtigungs-API verfügen. Es erfolgt lediglich eine globale Rückmeldung über die Verfügbarkeit von Arbeitsspeicher auf dem System.  
  
 Sie können diese Einstellungen ohne Neustart der Instanzen ändern. Dadurch können Sie problemlos mit verschiedenen Einstellungen experimentieren, um die für Ihr Nutzungsmuster am besten geeigneten Einstellungen herauszufinden.  
  
## <a name="providing-the-maximum-amount-of-memory-to-sql-server"></a>Bereitstellen der maximalen Menge von Arbeitsspeicher für SQL Server  
  
||32-Bit|64 Bit|  
|-|-------------|-------------|  
|Konventioneller Arbeitsspeicher|Bis zu der für den virtuellen Prozessadressraum geltenden Beschränkung in allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> 2 GB<br /><br /> 3 GB mit **/3GB** -Startparameter *<br /><br /> 4 GB auf WOW64\*\*|Bis zu der für den virtuellen Prozessadressraum geltenden Beschränkung in allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> 8 TB in einer x64-Architektur|  
  
 ***/3GB** ist ein Startparameter des Betriebssystems. Weitere Informationen finden Sie in der [MSDN Library](https://go.microsoft.com/fwlink/?LinkID=10257&clcid=0x409).  
  
 * * WOW64 (Windows unter Windows 64) ist ein Modus, in dem 32-Bit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem 64-Bit-Betriebssystem ausgeführt wird. Weitere Informationen finden Sie in der [MSDN Library](https://go.microsoft.com/fwlink/?LinkID=10257&clcid=0x409).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="example-a"></a>Beispiel A  
 Im folgenden Beispiel wird die Option `max server memory` auf 4 GB festgelegt.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'max server memory', 4096;  
GO  
RECONFIGURE;  
GO  
```  
  
### <a name="example-b-determining-current-memory-allocation"></a>Beispiel B: Bestimmen der aktuellen Speicherbelegung  
 Mit der folgenden Abfrage werden Informationen zur aktuellen Speicherbelegung zurückgegeben.  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
