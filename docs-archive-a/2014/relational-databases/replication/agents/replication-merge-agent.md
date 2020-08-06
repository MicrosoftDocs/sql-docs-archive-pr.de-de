---
title: Replikationsmerge-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Merge Agent, executables
- Merge Agent, parameter reference
- agents [SQL Server replication], Merge Agent
- command prompt [SQL Server replication]
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b3d74dcc6be62ae8a01d911a8404c7bc32fd651
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609157"
---
# <a name="replication-merge-agent"></a>Replikationsmerge-Agent
  Der Replikationsmerge-Agent ist ein Hilfsprogramm in Form einer ausführbaren Datei, die die in den Datenbanktabellen enthaltene Anfangsmomentaufnahme auf die Abonnenten anwendet. Er führt außerdem inkrementelle Datenänderungen zusammen, die nach der Erstellung der Anfangsmomentaufnahme auf dem Verleger ausgeführt wurden, und löst Konflikte entweder entsprechend den von Ihnen konfigurierten Regeln oder mithilfe eines von Ihnen erstellten benutzerdefinierten Konfliktlösers.  
  
> [!NOTE]  
>  Parameter können in beliebiger Reihenfolge angegeben werden. Wenn keine optionalen Parameter angegeben werden, werden Werte von vordefinierten Registrierungseinstellungen auf dem lokalen Computer verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      replmerg [-?]   
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Publicationpublication-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database  
[-AltSnapshotFolderalt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-DestThreadsnumber_of_destination_threads]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatchdownload_generations_per_batch]  
[-DownloadReadChangesPerBatchdownload_read_changes_per_batch]  
[-DownloadWriteChangesPerBatchdownload_write_changes_per_batch]  
[-DynamicSnapshotLocationdynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]  
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogininternet_login]  
[-InternetPasswordinternet_password]  
[-InternetProxyLogininternet_proxy_login]  
[-InternetProxyPasswordinternet_proxy_password]  
[-InternetProxyServerinternet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeoutinternet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MakeGenerationIntervalmake_generation_interval_seconds]  
[-MaxBcpThreadsnumber_of_threads]  
[-MaxDownloadChangesnumber_of_download_changes]  
[-MaxUploadChangesnumber_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSizepacket_size]   
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOutquery_time_out_seconds]  
[-SrcThreadsnumber_of_source_threads]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatchupload_generations_per_batch]  
[-UploadReadChangesPerBatchupload_read_changes_per_batch]  
[-UploadWriteChangesPerBatchupload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateIntervalvalidate_interval]  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Druckt alle verfügbaren Parameter.  
  
 **-Publisher** _server_name_[ **\\** _instance_name_]  
 Der Name des Verlegers. Geben Sie den *server_name* für die Standardinstanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie _server_name_ **\\** _instance_name_ für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-PublisherDB** _publisher_database_  
 Der Name der Verlegerdatenbank.  
  
 **-Publication** _publication_  
 Der Name der Veröffentlichung. Dieser Parameter ist nur gültig, wenn die Veröffentlichung so festgelegt ist, dass sie immer eine Momentaufnahme für neue oder neu initialisierte Abonnements zur Verfügung hat.  
  
 **-Subscriber** _server_name_[ **\\** _instance_name_]  
 Der Name des Abonnenten. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie _server_name_ **\\** _instance_name_ für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-SubscriberDB** _subscriber_database_  
 Der Name der Abonnentendatenbank.  
  
 **-AltSnapshotFolder** _alt_snapshot_folder_path_  
 Der Pfad zu dem Ordner, der die Anfangsmomentaufnahme für ein Abonnement enthält.  
  
 **-Continuous**  
 Gibt an, ob der Agent fortlaufend versucht, replizierte Transaktionen abzurufen. Wenn dieses Argument angegeben ist, ruft der Agent replizierte Transaktionen in festgelegten Abrufintervallen aus der Quelle ab, selbst wenn keine ausstehenden Transaktionen vorhanden sind.  
  
 **-DestThreads** _number_of_destination_threads_  
 Gibt die Anzahl von Zielthreads an, die der Merge-Agent verwendet, um Änderungen auf das Ziel anzuwenden. Das Ziel ist während des Hochladens der Verleger und während des Herunterladens der Abonnent. Der Standardwert ist 4.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Der Pfad der Agentdefinitionsdatei. Eine Agentdefinitionsdatei enthält Eingabeaufforderungsargumente für den Agent. Der Inhalt der Datei wird als ausführbare Datei analysiert. Verwenden Sie doppelte Anführungszeichen ("), um Argumentwerte anzugeben, die beliebige Zeichen enthalten.  
  
 **-Distributor** _server_name_[ **\\** _instance_name_]  
 Der Name des Verteilers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie _server_name_ **\\** _instance_name_ für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Bei der Verteilung durch den Verteiler (Push) wird als Standardwert der Name der Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf dem lokalen Computer verwendet.  
  
 **-DistributorLogin** _distributor_login_  
 Der Anmeldename des Verteilers.  
  
 **-DistributorPassword** _distributor_password_  
 Das Verteilerkennwort.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verteilers an. Der Wert **0** steht für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierungsmodus (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-DownloadGenerationsPerBatch** _download_generations_per_batch_  
 Die Anzahl von Generierungen, die in einem einzigen Batch verarbeitet werden sollen, während Änderungen vom Verleger auf den Abonnenten heruntergeladen werden. Eine Generierung ist als logische Gruppe von Änderungen pro Artikel definiert. Der Standardwert für eine zuverlässige Kommunikationsverbindung beträgt 100. Der Standardwert für eine unzuverlässige Kommunikationsverbindung beträgt 10.  
  
 **-DownloadReadChangesPerBatch** _download_read_changes_per_batch_  
 Die Anzahl von Änderungen, die in einem einzigen Batch gelesen werden sollen, während Änderungen vom Verleger auf den Abonnenten heruntergeladen werden. Der Standardwert ist 100.  
  
 **-DownloadWriteChangesPerBatch** _download_write_changes_per_batch_  
 Die Anzahl von Änderungen, die in einem einzigen Batch angewendet werden sollen, während Änderungen vom Verleger auf den Abonnenten heruntergeladen werden. Der Standardwert ist 100.  
  
 **-DynamicSnapshotLocation** _dynamic_snapshot_location_  
 Der Speicherort der gefilterten Datenmomentaufnahmedateien, wenn die Veröffentlichung parametrisierte Zeilenfilter verwendet.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Die Ebene der SSL-Verschlüsselung (Secure Sockets Layer), die vom Merge-Agent beim Herstellen von Verbindungen verwendet wird.  
  
|Wert von EncryptionLevel|BESCHREIBUNG|  
|---------------------------|-----------------|  
|**0**|Gibt an, dass SSL nicht verwendet wird.|  
|**1**|Gibt an, dass SSL verwendet wird, der Agent jedoch nicht überprüft, ob das SSL-Serverzertifikat von einem vertrauenswürdigen Aussteller signiert wurde.|  
|**2**|Gibt an, dass SSL verwendet und das Zertifikat überprüft wird.|  

 > [!NOTE]  
 >  Ein gültiges SSL-Zertifikat wird mit dem vollqualifizierten Domänennamen der SQL Server-Instanz definiert. Damit der Agent die Verbindung erfolgreich herstellen kann, wenn „-EncryptionLevel“ auf 2 festgelegt ist, sollten Sie einen Alias auf der lokalen SQL Server-Instanz erstellen. Der Parameter „Alias Name“ sollte den Servernamen enthalten, und für den Parameter „Server“ sollte der vollqualifizierte Name der SQL Server-Instanz festgelegt werden.
  
 Weitere Informationen finden Sie unter [SQL Server-Replikation-Sicherheit](../security/view-and-modify-replication-security-settings.md).  
  
 **-ExchangeType** [ **1**| **2**| **3**]  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Um Uploads einzuschränken, verwenden Sie stattdessen `@subscriber_upload_options` von `sp_addmergearticle`.  
  
 Gibt den Typ des Datenaustauschs während der Synchronisierung an. Folgende Typen sind möglich:  
  
|Wert von ExchangeType|BESCHREIBUNG|  
|------------------------|-----------------|  
|**1**|Der Agent soll Datenänderungen vom Abonnenten auf den Verleger hochladen.|  
|**2**|Der Agent soll Datenänderungen vom Verleger auf den Abonnenten herunterladen.|  
|**3** (Standardwert)|Der Agent soll zunächst Datenänderungen vom Abonnenten auf den Verleger hochladen und dann Datenänderungen vom Verleger auf den Abonnenten herunterladen. Sie müssen diese Option bei der Websynchronisierung verwenden.|  
  
 Anhand von nur herunterladbaren Artikeln können Sie das Synchronisierungsverhalten einzelner Artikel in einer Veröffentlichung steuern und zugleich einen Leistungsvorteil erzielen. Weitere Informationen finden Sie unter [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 Wenn Sie `ExchangeType` verwenden, um die Upload- und Downloadphase einer Mergereplikation in separate Sitzungen zu unterteilen, müssen Sie den Merge-Agent zuerst mit `ExchangeType` festgelegt auf den Wert 1 und anschließend mit dem Wert 2 ausführen. Wenn Sie den Merge-Agent nicht mit beiden Parametern ausführen, werden die Metadaten gelöscht, und Sie müssen das Abonnement (ohne Upload) erneut initialisieren.  
  
 **-FastRowCount** [**0**|**1**]  
 Gibt an, welcher Methodentyp für die Berechnung der Zeilenanzahl zur Zeilenanzahlüberprüfung verwendet werden soll. Der Wert **1** (Standard) gibt die schnelle Methode an. Der Wert **0** gibt die Methode für die vollständige Zeilenanzahl an.  
  
 **-FileTransferType** [**0**|**1**]  
 Gibt den Dateiübertragungstyp an. Der Wert **0** steht für UNC (Universal Naming Convention), der Wert **1** für FTP (File Transfer Protocol).  
  
 **-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **Subscriber**| **Both**)]  
 Gibt die Konvergenzebene an, die der Merge-Agent verwenden soll. Die folgenden Werte sind möglich:  
  
|Wert von ForceConvergenceLevel|BESCHREIBUNG|  
|---------------------------------|-----------------|  
|**0** (Standardwert)|Standard. Führt einen standardmäßigen Mergevorgang ohne zusätzliche Konvergenz aus.|  
|**1**|Erzwingt die Konvergenz für alle Generierungen.|  
|**2**|Erzwingt die Konvergenz für alle Generierungen und korrigiert beschädigte Herkunftsangaben. Wenn Sie diesen Wert festlegen, geben Sie an, ob Herkunftsangaben auf dem Verleger, auf dem Abonnenten oder sowohl auf dem Verleger als auch auf dem Abonnenten korrigiert werden sollen.|  
  
 **-FtpAddress** _ftp_address_  
 Die Netzwerkadresse des FTP-Diensts für den Verteiler. Wenn keine Netzwerkadresse angegeben wird, wird **Distributor** verwendet.  
  
 **-FtpPassword** _ftp_password_  
 Das Benutzerkennwort, mit dem eine Verbindung zum FTP-Dienst hergestellt wird.  
  
 **-FtpPort** _ftp_port_  
 Die Anschlussnummer des FTP-Diensts für den Verteiler. Wenn keine Portnummer angegeben wird, wird die Standardportnummer für den FTP-Dienst (21) verwendet.  
  
 **-FtpUserName** _ftp_user_name_  
 Der Benutzername, mit dem eine Verbindung zum FTP-Dienst hergestellt wird. Wenn kein Benutzername angegeben wird, wird anonymous verwendet.  
  
 **-HistoryVerboseLevel** [**1**|**2**|**3**]  
 Gibt den Umfang des Verlaufs an, der während eines Mergevorgangs protokolliert wird. Sie können die negativen Auswirkungen der Verlaufsprotokollierung auf die Leistung minimieren, indem Sie den Wert **1**auswählen.  
  
|Wert von <legacyBold>HistoryVerboseLevel</legacyBold>|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|**0**|Protokolliert die abschließende Agent-Statusmeldung, abschließende Sitzungsdetails und ggf. aufgetretene Fehler.|  
|**1**|Protokolliert zusätzlich zur abschließenden Agent-Statusmeldung, zu abschließenden Sitzungsdetails und ggf. aufgetretenen Fehlern inkrementelle Sitzungsdetails zu jedem Sitzungsstatus, u. a. den Prozentsatz der Fertigstellung.|  
|**2**|Standard. Protokolliert zusätzlich zur abschließenden Agent-Statusmeldung, zu abschließenden Sitzungsdetails und ggf. aufgetretenen Fehlern sowohl inkrementelle Sitzungsdetails zu jedem Sitzungsstatus als auch Sitzungsdetails auf Artikelebene, u. a. den Prozentsatz der Fertigstellung. Agent-Statusmeldungen werden ebenfalls protokolliert.|  
|**3**|Identisch mit **-HistoryVerboseLevel** = **2**, allerdings werden mehr Agent-Statusmeldungen protokolliert.|  
  
 **-Hostname** _host_name_  
 Der Netzwerkname des lokalen Computers. Der Standardwert ist der Name des lokalen Computers.  
  
 **-InteractiveResolution** [**0**|**1**]  
 Gibt an, ob die interaktive Konfliktlösung verwendet wird, wenn während der Synchronisierung ein Konflikt auftritt. Der Standardwert ist **0**. Dieser gibt an, dass die interaktive Konfliktlösung nicht verwendet wird.  
  
 **-InternetLogin** _internet_login_  
 Gibt den Anmeldenamen an, der beim Herstellen einer Verbindung mit einer Authentifizierung erfordernden ISAPI-DLL-Datei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsüberwachung verwendet wird.  
  
 **-InternetPassword** _internet_password_  
 Gibt das Kennwort an, das beim Herstellen einer Verbindung mit einer Authentifizierung erfordernden ISAPI-DLL-Datei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsüberwachung verwendet wird.  
  
 **-InternetProxyLogin**  *internet_proxy_login*  
 Gibt den Anmeldenamen an, der beim Herstellen einer Verbindung mit einem Authentifizierung erfordernden Proxyserver (in *internet_proxy_server*definiert) verwendet wird.  
  
 **-InternetProxyPassword**  *internet_proxy_password*  
 Gibt das Kennwort an, das beim Herstellen einer Verbindung mit einem Authentifizierung erfordernden Proxyserver (in *internet_proxy_server*definiert) verwendet wird.  
  
 **-InternetProxyServer** *internet_proxy_server*  
 Gibt den Proxyserver an, der für den Zugriff auf die in *internet_url*angegebene HTTP-Ressource zu verwenden ist.  
  
 **-InternetSecurityMode** [**0**|**1**]  
 Gibt den IIS-Sicherheitsmodus an, der beim Herstellen einer Verbindung mit dem Webserver während der Websynchronisierung verwendet wird. Der Wert **0** steht für die Standardauthentifizierung, der Wert **1** für die integrierte Windows-Authentifizierung (Standard).  
  
 **-InternetTimeout** _internet_timeout_  
 Die Anzahl von Sekunden, bevor bei einer Verbindung mit der ISAPI-DLL-Datei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsüberwachung ein Timeout auftritt.  
  
 **-InternetURL** _internet_url_  
 Gibt die URL an, die verwendet wird, um eine Verbindung mit der ISAPI-DLL-Datei für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsüberwachung herzustellen. Diese Eigenschaft muss angegeben werden.  
  
 **-KeepAliveMessageInterval** _keep_alive_message_interval_seconds_  
 Die Anzahl von Sekunden, bevor vom Verlaufsthread geprüft wird, ob bestehende Verbindungen auf eine Antwort vom Server warten. Dieser Wert kann verringert werden, damit der Merge-Agent vom Überprüfungs-Agent nicht als fehlerverdächtig markiert wird, wenn ein lang andauernder Batch ausgeführt wird. Die Standardeinstellung ist **300** Sekunden.  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Anmeldung eintritt. Der Standardwert ist **15** Sekunden.  
  
 **-MakeGenerationInterval** _make_generation_interval_seconds_  
 Die Anzahl der Wartezeit in Sekunden zwischen dem Erstellen von Generierungen oder Änderungsbatches zum Herunterladen auf den Client. Der Standardwert beträgt **1** Sekunde.  
  
 Makegeneration ist der Prozess, der Verlegeränderungen für das Herunterladen auf den Abonnenten vorbereitet. Während des Herunterladens kann dies ein Leistungsengpass sein. Wenn der makegeneration-Prozess bereits mit dem durch **-MakeGenerationInterval**angegebenen Intervall ausgeführt wurde, wird der Prozess für die aktuelle Synchronisierungssitzung übersprungen. Dies kann hilfreich für die Synchronisierungsparallelität sein, und zwar insbesondere dann, wenn Abonnenten nicht damit rechnen, Änderungen herunterzuladen.  
  
 **-MaxBcpThreads** _number_of_threads_  
 Gibt die Anzahl von Massenkopiervorgängen an, die parallel ausgeführt werden können. Die maximale Anzahl von Threads und gleichzeitig vorhandenen ODBC-Verbindungen entspricht entweder **MaxBcpThreads** oder der Anzahl von Massenkopieranforderungen, die in der Veröffentlichungsdatenbank in der **sysmergeschemachange** -Systemtabelle enthalten sind. Dabei gilt der jeweils kleinere Wert. Der Wert von**MaxBcpThreads** muss größer als 0 sein. Es ist keine hartcodierte Obergrenze vorhanden. Der Standardwert lautet **1**.  
  
 **-MaxDownloadChanges** _number_of_download_changes_  
 Gibt die maximale Anzahl von geänderten Zeilen an, die vom Verleger auf den Abonnenten heruntergeladen werden sollen. Die tatsächliche Anzahl heruntergeladener Zeilen kann über dem angegebenen Maximalwert liegen. Dies kann daran liegen, dass vollständige Generierungen verarbeitet werden und dass parallele Zielthreads ausgeführt werden, von denen jeder beim ersten Durchlauf mindestens 100 Änderungen verarbeitet. Standardmäßig werden alle Änderungen gesendet, die zum Herunterladen bereit sind.  
  
 **-MaxUploadChanges** _number_of_upload_changes_  
 Gibt die maximale Anzahl von geänderten Zeilen an, die vom Abonnenten auf den Verleger hochgeladen werden sollen. Die tatsächliche Anzahl hochgeladener Zeilen kann über dem angegebenen Maximalwert liegen. Dies kann daran liegen, dass vollständige Generierungen verarbeitet werden und dass parallele Zielthreads ausgeführt werden, von denen jeder beim ersten Durchlauf mindestens 100 Änderungen verarbeitet. Standardmäßig werden alle Änderungen gesendet, die zum Hochladen bereit sind.  
  
 **-MetadataRetentionCleanup** [**0**|**1**]  
 Gibt an, ob basierend auf der für die Veröffentlichung festgelegten Beibehaltungsdauer Metadaten aus [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)und [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) entfernt werden. Der Standardwert ist **1**. Dieser gibt an, dass ein Cleanup ausgeführt werden soll. Der Wert **0** gibt an, dass nicht automatisch ein Cleanup ausgeführt werden soll.  
  
 **-Output** _output_path_and_file_name_  
 Der Pfad der Agentausgabedatei. Wenn kein Dateiname angegeben ist, wird die Ausgabe an die Konsole gesendet. Wenn eine Datei mit dem angegebenen Namen vorhanden ist, wird die Ausgabe an diese Datei angefügt.  
  
 **-OutputVerboseLevel** [**0**|**1**|**2**]  
 Gibt an, ob die Ausgabe ausführlich sein soll. Wenn die Meldungsstufe **0**beträgt, werden nur Fehlermeldungen gedruckt. Wenn die Meldungsstufe **1**beträgt, werden alle Statusberichtsmeldungen gedruckt. Wenn die Meldungsstufe **2** (Standard) beträgt, werden alle Fehlermeldungen und Statusberichtsmeldungen gedruckt, was beim Debuggen nützlich ist.  
  
 **-ParallelUploadDownload** [**0**|**1**]  
 Gibt an, ob der Merge-Agent auf den Verleger hochgeladene Änderungen und auf den Abonnenten heruntergeladene Änderungen parallel verarbeiten soll. Dies ist in Umgebungen mit hohem Volumen und hoher Netzwerkbandbreite hilfreich. Wenn **ParallelUploadDownload** auf den Wert **1**festgelegt ist, ist die Parallelverarbeitung aktiviert.  
  
 **-PacketSize**  
 Die Paketgröße in Bytes. Der Standardwert ist 4096 (Bytes).  
  
 **-PollingInterval** _polling_interval_  
 Gibt an, wie häufig Datenänderungen vom Verleger oder Abonnenten abgefragt werden (in Sekunden). Der Standardwert ist 60 Sekunden.  
  
 **-ProfileName** _profile_name_  
 Gibt ein Agentprofil an, das für Agentparameter verwendet werden soll. Wenn **ProfileName** den Wert NULL aufweist, wird das Agentprofil deaktiviert. Wenn **ProfileName** nicht angegeben ist, wird das Standardprofil für den Agenttyp verwendet. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance_name_]  
 Gibt die Failoverpartnerinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die an einer Datenbank-Spiegelungssitzung mit der Veröffentlichungsdatenbank teilnimmt. Weitere Informationen finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** _publisher_login_  
 Der Anmeldename des Verlegers. Wenn **PublisherSecurityMode** auf **0** festgelegt ist (für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung), muss dieser Parameter angegeben werden.  
  
 **-PublisherPassword** _publisher_password_  
 Das Kennwort des Verlegers. Wenn **PublisherSecurityMode** auf **0** festgelegt ist (für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung), muss dieser Parameter angegeben werden.  
  
 **-PublisherSecurityMode** [**0**|**1**]  
 Gibt den Sicherheitsmodus des Verlegers an. Der Wert **0** steht für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Abfrage eintritt. Der Standardwert ist 300 Sekunden. Der Merge-Agent ermittelt anhand des Werts von `QueryTimeout` außerdem, wie lange auf die Generierung einer partitionierten Momentaufnahme gewartet wird, wenn dieser Wert 1800 übersteigt.  
  
 **-SrcThreads** _number_of_source_threads_  
 Gibt die Anzahl von Quellthreads an, die der Merge-Agent verwendet, um Änderungen von der Quelle aufzuzählen. Die Quelle ist während des Hochladens der Abonnent und während des Herunterladens der Verleger. Der Standardwert ist **3**.  
  
 **-StartQueueTimeout** _start_queue_timeout_seconds_  
 Die maximale Anzahl von Sekunden, die der Merge-Agent wartet, wenn die Anzahl gleichzeitiger Mergeprozesse den Grenzwert erreicht, der durch die- **@max_concurrent_merge** Eigenschaft **sp_addmergepublication**festgelegt wird. Wenn der Merge-Agent nach Verstreichen der maximalen Anzahl von Sekunden immer noch wartet, wird der Agent beendet. Der Wert 0 bedeutet, dass der Agent unbegrenzt wartet, der Vorgang jedoch abgebrochen werden kann.  
  
 **-SubscriberDatabasePath** _subscriber_database_path_  
 Der Pfad der Jet-Datenbank (MDB-Datei), wenn **SubscriberType** auf **2** festgelegt ist. (Dadurch wird eine Verbindung mit einer Jet-Datenbank ohne ODBC-DSN (Data Source Name) möglich.)  
  
 **-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]  
 Gibt an, ob eine Abonnentendatenbank vorhanden ist.  
  
|Wert von SubscriberDBAddOption|BESCHREIBUNG|  
|---------------------------------|-----------------|  
|**0**|Die vorhandene Datenbank wird verwendet (Standard).|  
|**1**|Eine neue, leere Abonnentendatenbank wird erstellt.|  
|**2**|Eine neue Datenbank wird erstellt und an die angegebene Datei angefügt.|  
|**3**|Eine neue Datenbank wird erstellt und angefügt, und alle Abonnements, die ggf. in der Datei vorhanden sind, werden aktiviert.|  
  
> [!NOTE]  
>  Bei Verwendung der Werte **2** und **3**muss in der **SubscriberDatabasePath** -Option der Datenbankpfad für den Abonnenten angegeben werden.  
  
 **-SubscriberLogin** _subscriber_login_  
 Der Anmeldename des Abonnenten. Wenn **SubscriberSecurityMode** auf **0** festgelegt ist (für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung), muss dieser Parameter angegeben werden.  
  
 **-SubscriberPassword** _subscriber_password_  
 Das Kennwort des Abonnenten. Wenn **SubscriberSecurityMode** auf **0** festgelegt ist (für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung), muss dieser Parameter angegeben werden.  
  
 **-SubscriberSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Abonnenten an. Der Wert **0** steht für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-SubscriberConflictClean** [ **0**| **1**]  
 Gibt an, ob während der Synchronisierung ein Cleanup für die Konflikttabellen auf dem Abonnenten ausgeführt wird. Der Wert **1** gibt an, dass für die Konflikttabellen auf dem Abonnenten ein Cleanup ausgeführt wird. Dieser Parameter wird nur für Abonnements von Veröffentlichungen mit dezentralisierter Konfliktprotokollierung verwendet.  
  
 **-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]  
 Gibt den Typ der vom Merge-Agent verwendeten Abonnentenverbindung an. Für diesen Parameter wird nur der Standardwert **0** unterstützt.  
  
 **-SubscriptionType**[ **0**| **1**| **2**]  
 Gibt den Abonnementtyp für die Verteilung an. Der Wert **0** steht für ein Pushabonnement (Standard), der Wert **1** für ein Pullabonnement und der Wert **2** für ein anonymes Abonnement.  
  
 **-SyncToAlternate** [ **0|1**]  
 Gibt an, ob der Merge-Agent eine Synchronisierung zwischen einem Abonnenten und einem alternativen Verleger ausführt. Der Wert **1** gibt an, dass es sich um einen alternativen Verleger handelt. Die Standardeinstellung ist **0**.  
  
 **-UploadGenerationsPerBatch** _upload_generations_per_batch_  
 Die Anzahl von Generierungen, die in einem einzigen Batch verarbeitet werden sollen, während Änderungen vom Abonnenten auf den Verleger hochgeladen werden. Eine Generierung ist als logische Gruppe von Änderungen pro Artikel definiert. Der Standardwert für eine zuverlässige Kommunikationsverbindung beträgt **100**. Der Standardwert für eine unzuverlässige Kommunikationsverbindung beträgt **1**.  
  
 **-UploadReadChangesPerBatch** _upload_read_changes_per_batch_  
 Die Anzahl von Änderungen, die in einem einzigen Batch gelesen werden sollen, während Änderungen vom Abonnenten auf den Verleger hochgeladen werden. Der Standardwert ist **100**.  
  
 **-UploadWriteChangesPerBatch** _upload_write_changes_per_batch_  
 Die Anzahl von Änderungen, die in einem einzigen Batch angewendet werden sollen, während Änderungen vom Abonnenten auf den Verleger hochgeladen werden. Der Standardwert ist **100**.  
  
 **-UseInprocLoader**  
 Verbessert die Leistung der Anfangsmomentaufnahme, indem der Merge-Agent veranlasst wird, beim Anwenden von Momentaufnahmedateien auf dem Abonnenten den BULK INSERT-Befehl zu verwenden. Dieser Parameter ist veraltet, da er mit dem XML-Datentyp nicht kompatibel ist. Wenn Sie keine XML-Daten replizieren, können Sie diesen Parameter verwenden. Dieser Parameter kann nicht mit Momentaufnahmen im Zeichenmodus verwendet werden. Wenn Sie den Parameter verwenden, muss das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto auf dem Abonnenten über Leseberechtigungen für das Verzeichnis verfügen, in dem sich die BCP-Datendateien der Momentaufnahmen befinden. Wenn der Parameter nicht verwendet wird, liest der vom Agent geladene ODBC-Treiber aus den Dateien, sodass der Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkontos nicht verwendet wird.  
  
 **-Validate** [**0**|**1**|**2**|**3**]  
 Gibt an, ob am Ende der Mergesitzung eine Überprüfung ausgeführt werden soll, und gibt ggf. den Typ der Überprüfung an. Der Wert **3** wird empfohlen.  
  
|Wert von Validate|BESCHREIBUNG|  
|--------------------|-----------------|  
|**0** (Standardwert)|Keine Überprüfung.|  
|**1**|Nur Überprüfung der Zeilenanzahl.|  
|**2**|Überprüfung der Zeilenanzahl und der Prüfsumme.|  
|**3**|Überprüfung der Zeilenanzahl und der binären Prüfsumme.|  
  
> [!NOTE]  
>  Die Überprüfung durch binäre Prüfsummen oder Prüfsummen kann dann fälschlicherweise einen Fehler ausgeben, wenn auf dem Abonnenten andere Datentypen vorhanden sind als auf dem Verleger. Weitere Informationen finden Sie im Abschnitt „Überlegungen zur Datenüberprüfung“ unter [Überprüfen von replizierten Daten](../validate-data-at-the-subscriber.md).  
  
 **-ValidateInterval** _validate_interval_  
 Gibt an, wie häufig das Abonnement im kontinuierlichen Modus überprüft wird (in Minuten). Die Standardeinstellung beträgt **60** Minuten.  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!IMPORTANT]  
>  Wenn Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent so installiert haben, dass er unter einem lokalen Systemkonto und nicht unter einem Domänenbenutzerkonto (Standard) ausgeführt wird, kann der Dienst nur auf den lokalen Computer zugreifen. Wenn der Merge-Agent, der unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, so konfiguriert ist, dass beim Anmelden bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]der Windows-Authentifizierungsmodus verwendet wird, schlägt der Merge-Agent fehl. Die Standardeinstellung ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung.  
  
 Führen Sie zum Starten des Merge-Agents von der Eingabeaufforderung **replmerg.exe** aus. Informationen hierzu finden Sie im [Abschnitt zu den ausführbaren Dateien von Replikations-Agents](../concepts/replication-agent-executables-concepts.md).  
  
 Der Merge-Agent-Verlauf für die aktuelle Sitzung wird im kontinuierlichen Modus nicht entfernt. Ein lang ausgeführter Agent kann zu vielen Einträgen in den Merge-Verlaufstabellen führen, was sich auf die Leistung auswirken kann. Wechseln Sie zur Behebung dieses Problems zum geplanten Modus, oder verwenden Sie weiterhin den kontinuierlichen Modus. Erstellen Sie dann jedoch einen dedizierten Auftrag, um den Merge-Agent in regelmäßigen Abständen neu zu starten, oder reduzieren Sie die Ausführlichkeit der Verlaufsebene, um die Anzahl der Zeilen und damit die Auswirkungen auf die Leistung zu reduzieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations-Agent-Verwaltung](replication-agent-administration.md)  
  
  
