---
title: Konfigurieren der Replikation für Always On-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 916458d2d6b8fbba81940257ee85ffe014d1f12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697190"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a>Konfigurieren der Replikation für Always On-Verfügbarkeitsgruppen (SQL Server)
  Das Konfigurieren von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikation und AlwaysOn-Verfügbarkeitsgruppen umfasst sieben Schritte. Jeder dieser Schritte wird in den folgenden Abschnitten detailliert beschrieben.  

##  <a name="1-configure-the-database-publications-and-subscriptions"></a><a name="step1"></a> 1. Konfigurieren der Datenbankveröffentlichungen und Abonnements  

### <a name="configure-the-distributor"></a>Konfigurieren des Verteilers
  
 Der Verteiler sollte kein Host für eine der aktuellen (oder vorgesehenen) Replikate der Verfügbarkeitsgruppe sein, zu der die Veröffentlichungsdatenbank gehört (oder gehören wird).  
  
1.  Konfigurieren Sie Verteilung beim Verteiler. Wenn gespeicherte Prozeduren zur Konfiguration verwendet werden, führen Sie `sp_adddistributor` aus. Verwenden Sie den- *@password* Parameter, um das Kennwort zu identifizieren, das verwendet wird, wenn ein Remote Verleger eine Verbindung mit dem Verteiler herstellt. Das Kennwort wird auch bei jedem Remoteverleger benötigt, wenn der Remoteverteiler eingerichtet wird.  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  Erstellen Sie die Verteilungsdatenbank beim Verteiler. Wenn gespeicherte Prozeduren zur Konfiguration verwendet werden, führen Sie `sp_adddistributiondb` aus.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  Konfigurieren Sie den Remoteverleger. Wenn gespeicherte Prozeduren zur Konfiguration des Verteilers verwendet werden, führen Sie `sp_adddistpublisher` aus. Der- *@security_mode* Parameter wird verwendet, um zu bestimmen, wie die gespeicherte Prozedur zur Verleger Überprüfung, die von den Replikations-Agents ausgeführt wird, eine Verbindung mit dem aktuellen primären Wenn der Parameter auf 1 festgelegt ist, wird die Windows-Authentifizierung verwendet, um eine Verbindung mit dem aktuellen primären Replikat herzustellen. Wenn der Wert auf 0 festgelegt ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird die Authentifizierung mit den angegebenen *@login* Werten für und verwendet *@password* . Die Anmeldedaten und das Kennwort, die angegeben wurden, müssen bei jedem sekundären Replikat gültig sein, damit die gespeicherte Prozedur zur Überprüfung erfolgreich eine Verbindung mit diesem Replikat herstellen kann.  
  
    > [!NOTE]  
    >  Wenn geänderte Replikations-Agents auf einem anderen Computer als dem Verteiler ausgeführt werden, dann ist bei Verwendung der Windows-Authentifizierung zum Herstellen einer Verbindung zum primären Replikat erforderlich, dass die Kerberos-Authentifizierung für die Kommunikation zwischen den Replikathostcomputern konfiguriert wird. Bei Verwendung einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung zum Herstellen einer Verbindung mit dem aktuellen primären Replikat ist keine Kerberos-Authentifizierung erforderlich.  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 Weitere Informationen finden Sie unter [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).  
  
### <a name="configure-the-publisher-at-the-original-publisher"></a>Konfigurieren des Verlegers beim ursprünglichen Verleger
  
1.  Konfigurieren Sie die Remoteverteilung. Wenn gespeicherte Prozeduren zur Konfiguration des Verlegers verwendet werden, führen Sie `sp_adddistributor` aus. Geben Sie den gleichen Wert für an *@password* , der verwendet wurde, als `sp_adddistrbutor` auf dem Verteiler ausgeführt wurde, um die Verteilung einzurichten.  
  
    ```sql
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  Aktivieren Sie die Datenbank für die Replikation. Wenn gespeicherte Prozeduren zur Konfiguration des Verlegers verwendet werden, führen Sie `sp_replicationdboption` aus. Wenn sowohl Transaktions- als auch Mergereplikation für die Datenbank konfiguriert werden sollen, müssen beide aktiviert werden.  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  Erstellen Sie die Replikationsveröffentlichung, Artikel und Abonnements. Weitere Informationen zum Konfigurieren der Replikation finden Sie unter "Veröffentlichen von Daten und Datenbankobjekten".  
  
##  <a name="2-configure-the-alwayson-availability-group"></a><a name="step2"></a>2. Konfigurieren der AlwaysOn-Verfügbarkeits Gruppe  
 Erstellen Sie beim vorgesehenen primären Replikat die Veröffentlichungsgruppe, und ordnen Sie ihr die veröffentlichte (oder zu veröffentlichende) Datenbank als Elementdatenbank zu. Wenn Sie den Verfügbarkeitsgruppen-Assistenten verwenden, können Sie es entweder dem Assistenten erlauben, die sekundären Replikatdatenbanken zum ersten Mal zu synchronisieren, oder Sie können die Initialisierung mit Sicherung und Wiederherstellung manuell ausführen.  
  
 Erstellen Sie einen DNS-Listener für die Verfügbarkeitsgruppe, die von den Replikations-Agents verwendet wird, um eine Verbindung mit dem aktuellen Primären herzustellen. Der angegebene Listenername wird als Umleitungsziel für das aus ursprünglichem Verleger und veröffentlichter Datenbank bestehende Paar verwendet. Wenn Sie die Verfügbarkeitsgruppe beispielsweise mithilfe von DDL konfigurieren, kann das folgende Codebeispiel zur Angabe eines Verfügbarkeitsgruppenlisteners für eine vorhandene Verfügbarkeitsgruppe mit dem Namen `MyAG` verwendet werden:  
  
```sql
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 Weitere Informationen finden Sie unter [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md).  
  
##  <a name="3-insure-that-all-of-the-secondary-replica-hosts-are-configured-for-replication"></a><a name="step3"></a>3. Stellen Sie sicher, dass alle sekundären Replikat Hosts für die Replikation konfiguriert sind  
 Überprüfen Sie bei jedem sekundären Replikathost, ob [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] so konfiguriert wurde, dass die Replikation unterstützt wird. Die folgende Abfrage kann auf jedem sekundären Replikathost ausgeführt werden, um zu bestimmen, ob die Replikation installiert wurde:  
  
```sql
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 Wenn *@installed* den Wert 0 hat, muss die Replikation der-Installation hinzugefügt werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
##  <a name="4-configure-the-secondary-replica-hosts-as-replication-publishers"></a><a name="step4"></a> 4. Konfigurieren des sekundären Replikathosts als Replikationsverleger  
 Ein sekundäres Replikat kann nicht als Replikationsverleger oder Neuverleger fungieren, aber die Replikation kann so konfiguriert werden, dass das sekundäre Replikat nach einem Failover die Rolle übernehmen kann. Konfigurieren Sie beim Verteiler die Verteilung für jeden sekundären Replikathost. Geben Sie die Verteilungsdatenbank und das Arbeitsverzeichnis an, die angegeben wurden, als der ursprüngliche Verleger dem Verteiler hinzugefügt wurde. Wenn Sie gespeicherte Prozeduren zum Konfigurieren der Verteilung verwenden, führen Sie `sp_adddistpublisher` aus, um die Remoteverleger dem Verteiler zuzuordnen. Wenn *@login* und *@password* für den ursprünglichen Verleger verwendet wurden, geben Sie die gleichen Werte an, wenn Sie die sekundären Replikat Hosts als Verleger hinzufügen.  
  
```sql
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 Konfigurieren Sie die Verteilung auf jedem sekundären Replikathost. Identifizieren Sie den Verteiler des ursprünglichen Verlegers als Remoteverteiler. Verwenden Sie das Kennwort, das verwendet wurde, als `sp_adddistributor` ursprünglich auf dem Verteiler ausgeführt wurde. Wenn gespeicherte Prozeduren zum Konfigurieren der Verteilung verwendet werden, wird der- *@password* Parameter von `sp_adddistributor` verwendet, um das Kennwort anzugeben.  
  
```sql
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 Stellen Sie bei jedem sekundären Replikathost sicher, dass die Pushabonnenten der Datenbankveröffentlichungen als Verbindungsserver angezeigt werden. Wenn gespeicherte Prozeduren zum Konfigurieren der Remoteverleger verwendet werden, führen Sie `sp_addlinkedserver` aus, um den Verlegern die Abonnenten (sofern nicht bereits vorhanden) als Verbindungsserver hinzuzufügen.  
  
```sql
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="5-redirect-the-original-publisher-to-the-ag-listener-name"></a><a name="step5"></a> 5. Umleiten des ursprünglichen Verlegers zum Namen des Verfügbarkeitsgruppenlisteners  
 Führen Sie auf dem Verteiler in der Verteilungsdatenbank die gespeicherte Prozedur `sp_redirect_publisher` aus, um den ursprünglichen Verleger und die veröffentlichte Datenbank dem Namen des Verfügbarkeitsgruppenlisteners der Verfügbarkeitsgruppe zuzuordnen.  
  
```sql
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="6-run-the-replication-validation-stored-procedure-to-verify-the-configuration"></a><a name="step6"></a> 6. Ausführen der gespeicherten Prozedur zur Replikationsüberprüfung, um die Konfiguration zu überprüfen  
 Führen Sie auf dem Verteiler in der Verteilungsdatenbank die gespeicherte Prozedur `sp_validate_replica_hosts_as_publishers` aus, um zu überprüfen, ob alle Replikathosts bereits so konfiguriert worden sind, um als Verleger für die veröffentlichte Datenbank zu fungieren.  
  
```sql
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 Die gespeicherte Prozedur `sp_validate_replica_hosts_as_publishers` sollte von einer Anmeldung mit ausreichender Autorisierung bei jedem Verfügbarkeitsgruppenreplikathost ausgeführt werden, um Informationen zur Verfügbarkeitsgruppe abzufragen. Im Gegensatz zu `sp_validate_redirected_publisher` verwendet Sie die Anmelde Informationen des Aufrufers und verwendet nicht die in msdb. dbo. MSdistpublishers beibehaltene Anmeldung, um eine Verbindung mit den Verfügbarkeits Gruppen Replikaten herzustellen.  
  
> [!NOTE]  
>  Die Überprüfung sekundärer Replikathosts, die keinen Lesezugriff zulassen oder die Angabe der Leseabsicht erfordern, schlägt bei `sp_validate_replica_hosts_as_publishers` mit dem folgenden Fehler fehl.  
>   
>  Meldung 21899, Ebene 11, Status 1, Prozedur `sp_hadr_verify_subscribers_at_publisher`, Zeile 109  
>   
>  Die Abfrage beim umgeleiteten Verleger „MyReplicaHostName“ zur Bestimmung, ob sysserver-Einträge für die Abonnenten des ursprünglichen Verlegers „MyOriginalPublisher“ vorliegen, ist mit Fehler 976 und folgender Meldung fehlgeschlagen: „Fehler 976, Stufe 14, Status 1, Meldung: The target database, 'MyPublishedDB', is participating in an availability group and is currently not accessible for queries. (Die Zieldatenbank „MyPublishedDB“ ist an einer Verfügbarkeitsgruppe beteiligt, und Abfragen können derzeit nicht darauf zugreifen.) Entweder die Datenverschiebung wurde angehalten, oder für das Verfügbarkeitsreplikat wurde kein Schreibzugriff aktiviert. Um schreibgeschützten Zugriff auf diese und andere Datenbanken in der Verfügbarkeitsgruppe zuzulassen, aktivieren Sie den Lesezugriff auf mindestens ein sekundäres Verfügbarkeitsreplikat in der Gruppe.  Weitere Informationen finden Sie im Thema zur `ALTER AVAILABILITY GROUP`-Anweisung in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
>   
>  Es sind ein oder mehrere Verlegerüberprüfungsfehler für Replikathost 'MyReplicaHostName' aufgetreten.  
  
 Dieses Verhalten wird erwartet. Sie müssen das Vorhandensein der Abonnentenservereinträge bei diesen sekundären Replikathosts überprüfen, indem Sie die sysserver-Einträge im Host direkt abfragen.  
  
##  <a name="7-add-the-original-publisher-to-replication-monitor"></a><a name="step7"></a> 7. Hinzufügen des ursprünglichen Verlegers zum Replikationsmonitor  
 Fügen Sie dem Replikationsmonitor bei jedem Verfügbarkeitsgruppenreplikat den ursprünglichen Verleger hinzu.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **Replikation**  
  
-   [Warten einer AlwaysOn-Veröffentlichungs Datenbank &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [Häufig gestellte Fragen für Replikationsadministratoren](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 **So erstellen und konfigurieren Sie eine Verfügbarkeitsgruppe**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen: Interoperabilität (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [SQL Server-Replikation](../../../relational-databases/replication/sql-server-replication.md)  
