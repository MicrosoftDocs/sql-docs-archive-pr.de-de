---
title: Erstellen einer Verfügbarkeitsgruppe (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57a494af168a8f5572bafe93f8fb47b22a954a19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727133"
---
# <a name="create-an-availability-group-transact-sql"></a>Erstellen einer Verfügbarkeitsgruppe (Transact-SQL)
  In diesem Thema wird beschrieben, wie [!INCLUDE[tsql](../../../includes/tsql-md.md)] zum Erstellen und Konfigurieren einer Verfügbarkeitsgruppe für Instanzen von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit aktivierter [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Funktion verwendet wird. Eine *Verfügbarkeitsgruppe* definiert einen Satz von Benutzerdatenbanken, für die als eine einzelne Einheit ein Failover ausgeführt wird, sowie einen Satz von Failoverpartnern, die als *Verfügbarkeitsreplikate*bezeichnet werden, die Failover unterstützen.  
  
> [!NOTE]  
>  Eine Einführung zu Verfügbarkeitsgruppen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  

> [!NOTE]  
>  Als Alternative zur Verwendung von [!INCLUDE[tsql](../../../includes/tsql-md.md)]können Sie den Assistenten zum Erstellen einer Verfügbarkeitsgruppe oder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Cmdlets verwenden. Weitere Informationen finden Sie unter [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)[Verwenden des Dialogfelds „Neue Verfügbarkeitsgruppe“ &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)[Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 Es wird dringend empfohlen, dass Sie diesen Abschnitt lesen, bevor Sie versuchen, Ihre erste Verfügbarkeitsgruppe zu erstellen.  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a>Voraussetzungen, Einschränkungen und Empfehlungen  
  
-   Überprüfen Sie vor dem Erstellen einer Verfügbarkeitsgruppe, ob sich die Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die Verfügbarkeitsreplikate hosten, auf verschiedenen WSFC-Konten (Windows Server Failover Clustering) des gleichen WSFC-Failoverclusters befinden. Stellen Sie außerdem sicher, dass alle Serverinstanzen alle anderen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Voraussetzungen erfüllen. Wenn Sie weitere Informationen wünschen, sollten Sie unbedingt [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) lesen.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.  
  
###  <a name="summary-of-tasks-and-corresponding-transact-sql-statements"></a><a name="SummaryTsqlStatements"></a> Zusammenfassung von Tasks und entsprechenden Transact-SQL-Anweisungen  
 In der folgenden Tabelle sind die grundlegenden Tasks aufgeführt, die zum Erstellen und Konfigurieren einer Verfügbarkeitsgruppe erforderlich sind, und es ist angegeben, welche [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen für diese Tasks zu verwenden sind. Die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Tasks müssen in der Reihenfolge ausgeführt werden, in der sie in der Tabelle dargestellt sind.  
  
|Aufgabe|Transact-SQL-Anweisung(en)|Wo der Task auszuführen ist**<sup>*</sup>**|  
|----------|----------------------------------|-------------------------------------------|  
|Erstellen eines Datenbankspiegelungs-Endpunkts (einmal pro [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz)|[Endpunkt](/sql/t-sql/statements/create-endpoint-transact-sql) *EndpointName* erstellen... für DATABASE_MIRRORING|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der der Datenbankspiegelungs-Endpunkt fehlt.|  
|Erstellen der Verfügbarkeitsgruppe|[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)|Führen Sie diesen Task auf der Serverinstanz aus, auf der das anfängliche primäre Replikat gehostet werden soll.|  
|Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe|[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *Gruppenname* JOIN|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der ein sekundäres Replikat gehostet wird.|  
|Vorbereiten der sekundären Datenbank|[Sichern](/sql/t-sql/statements/backup-transact-sql) und [Wiederherstellen](/sql/t-sql/statements/restore-statements-transact-sql).|Erstellen Sie Sicherungen auf der Serverinstanz, auf der das primäre Replikat gehostet wird.<br /><br /> Stellen Sie mit RESTORE WITH NORECOVERY Sicherungen auf jeder Serverinstanz wieder her, auf der ein sekundäres Replikat gehostet wird.|  
|Starten der Datensynchronisierung durch Hinzufügen der einzelnen sekundären Datenbanken zur Verfügbarkeitsgruppe|[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *Datenbankname* SET HADR AVAILABILITY GROUP = *Gruppenname*|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der ein sekundäres Replikat gehostet wird.|  
  
 **<sup>*</sup>** Stellen Sie eine Verbindung mit der angegebenen Serverinstanz her, um eine bestimmte Aufgabe auszuführen.  
  
##  <a name="using-transact-sql-to-create-and-configure-an-availability-group"></a><a name="TsqlProcedure"></a>Verwenden von Transact-SQL zum Erstellen und Konfigurieren einer Verfügbarkeits Gruppe  
  
> [!NOTE]  
>   Eine Vorgehensweise für eine Beispielkonfiguration mit Codebeispielen für jede dieser [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen finden Sie in [Beispiel: Konfigurieren einer Verfügbarkeitsgruppe, die die Windows-Authentifizierung verwendet](#ExampleConfigAGWinAuth).  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, auf der das primäre Replikat gehostet werden soll.  
  
2.  Erstellen Sie die Verfügbarkeits Gruppe mithilfe der [Create Availability Group](/sql/t-sql/statements/create-availability-group-transact-sql) - [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisung.  
  
3.  Verknüpfen Sie das neue sekundäre Replikat mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)mit einer Always On-Verfügbarkeitsgruppe verknüpft wird.  
  
4.  Erstellen Sie für jede Datenbank in der Verfügbarkeitsgruppe eine sekundäre Datenbank, indem Sie letzte Sicherungen der primären Datenbank mit RESTORE WITH NORECOVERY wiederherstellen. Weitere Informationen finden Sie unter [Beispiel: Einrichten einer Verfügbarkeitsgruppe mithilfe der Windows-Authentifizierung (Transact-SQL)](create-an-availability-group-transact-sql.md)ab dem Schritt, in dem die Datenbanksicherung wiederhergestellt wird.  
  
5.  Verknüpfen Sie alle neuen sekundären Datenbanken mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)mit einer Always On-Verfügbarkeitsgruppe verknüpft wird.  
  
##  <a name="example-configuring-an-availability-group-that-uses-windows-authentication"></a><a name="ExampleConfigAGWinAuth"></a> Beispiel: Konfigurieren einer Verfügbarkeitsgruppe, die die Windows-Authentifizierung verwendet  
 In diesem Beispiel wird eine Beispiel- [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Konfigurationsprozedur erstellt, die [!INCLUDE[tsql](../../../includes/tsql-md.md)] zum Einrichten von Datenbankspiegelungs-Endpunkten, die die Windows-Authentifizierung verwenden, sowie zum Erstellen und Konfigurieren einer Verfügbarkeitsgruppe und deren sekundärer Datenbanken verwendet.  
  
 Dieses Beispiel enthält folgende Abschnitte:  
  
-   [Voraussetzungen für die Verwendung der Beispiel Konfigurations Prozedur](#PrerequisitesForExample)  
  
-   [Beispielkonfigurationsprozedur](#SampleProcedure)  
  
-   [Vollständiges Codebeispiel für Beispielkonfigurationsprozedur](#CompleteCodeExample)  
  
###  <a name="prerequisites-for-using-the-sample-configuration-procedure"></a><a name="PrerequisitesForExample"></a> Erforderliche Komponenten für die Verwendung der Beispielkonfigurationsprozedur  
 Diese Beispielprozedur weist die folgenden Anforderungen auf:  
  
-   Die Serverinstanzen müssen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]unterstützen. Weitere Informationen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Zwei Beispieldatenbanken, *MyDb1* und *MyDb2*, müssen auf der Serverinstanz vorhanden sein, die das primäre Replikat hostet. In den folgenden Codebeispielen werden diese beiden Datenbanken erstellt und konfiguriert, und es wird eine vollständige Sicherung jeder Datenbank erstellt. Führen Sie diese Codebeispiele auf der Serverinstanz aus, auf der Beispielverfügbarkeitsgruppe erstellt werden soll. Auf dieser Serverinstanz wird das ursprüngliche primäre Replikat der Beispielverfügbarkeitsgruppe gehostet.  
  
    1.  Im folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Beispiel werden diese Datenbanken erstellt und so geändert, dass das vollständige Wiederherstellungsmodell verwendet wird:  
  
        ```sql
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  Im folgenden Codebeispiel wird eine vollständige Datenbanksicherung von *MyDb1* und *MyDb2*erstellt. In diesem Codebeispiel wird eine fiktive Sicherungs Freigabe verwendet: \\ \\ *File Server* \\ *sqlbackups*.  
  
        ```sql
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO
        ```  
  
###  <a name="sample-configuration-procedure"></a><a name="SampleProcedure"></a> Beispielkonfigurationsprozedur  
 In dieser Beispielkonfiguration wird das Verfügbarkeitsreplikat auf zwei eigenständigen Serverinstanzen erstellt, deren Dienstkonten unter unterschiedlichen – aber vertrauenswürdigen – Domänen (`DOMAIN1` und `DOMAIN2`) ausgeführt werden.  
  
 In der folgenden Tabelle finden Sie eine Zusammenfassung der in dieser Beispielkonfiguration verwendeten Werte.  
  
|Ursprüngliche Rolle|System|Hosten der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz|  
|------------------|------------|---------------------------------------------|  
|Primär|`COMPUTER01`|`AgHostInstance`|  
|Secondary|`COMPUTER02`|Standardinstanz|  
  
1.  Erstellen Sie einen Datenbankspiegelungs-Endpunkt namens *dbm_endpoint* auf der Serverinstanz, auf der Sie die Verfügbarkeitsgruppe erstellen möchten (dies ist eine Instanz namens `AgHostInstance` auf `COMPUTER01`). Dieser Endpunkt verwendet Port 7022. Beachten Sie, dass die Serverinstanz, auf der Sie die Verfügbarkeitsgruppe erstellen, das primäre Replikat hostet.  
  
    ```sql
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
2.  Erstellen Sie einen Endpunkt *dbm_endpoint* auf der Serverinstanz, die das sekundäre Replikat hostet (dies ist die Standardserverinstanz auf `COMPUTER02`). Dieser Endpunkt verwendet Port 5022.  
  
    ```sql
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
3.  > [!NOTE]  
    >  Wenn die Dienstkonten der Serverinstanzen, auf denen die Verfügbarkeitsreplikate gehostet werden sollen, unter dem gleichen Domänenkonto ausgeführt wurden, ist dieser Schritt nicht erforderlich. Überspringen Sie den Schritt, und fahren Sie gleich mit dem nächsten Schritt fort.  
  
     Wenn die Dienstkonten der Serverinstanzen unter unterschiedlichen Domänenbenutzern ausgeführt werden, erstellen Sie auf jeder Serverinstanz eine Anmeldung für die andere Serverinstanz, und gewähren Sie dieser Anmeldung Berechtigungen zum Zugreifen auf den lokalen Datenbankspiegelungs-Endpunkt.  
  
     Im folgenden Codebeispiel sind die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen zum Erstellen einer Anmeldung und zum Gewähren der Berechtigung für einen Endpunkt für die Anmeldung dargestellt. Das Domänenkonto der Remoteserverinstanz wird hier als *domain_name*\\*user_name*dargestellt.  
  
    ```sql
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  Erstellen Sie auf der Serverinstanz, auf der sich die Benutzerdatenbanken befinden, die Verfügbarkeitsgruppe.  
  
     Im folgenden Codebeispiel wird eine Verfügbarkeitsgruppe mit dem Namen *MyAG* auf der Serverinstanz erstellt, auf der die Beispieldatenbanken *MyDb1* und *MyDb2*erstellt wurden. Die lokale Serverinstanz `AgHostInstance`auf *COMPUTER01* wird zuerst angegeben. Diese Instanz hostet das ursprüngliche primäre Verfügbarkeitsreplikat. Eine Remoteserverinstanz, die Standardserverinstanz auf *COMPUTER02*, wird angegeben, um ein sekundäres Replikat zu hosten. Beide Verfügbarkeitsreplikate werden konfiguriert, um den Modus mit asynchronem Commit mit manuellem Failover zu verwenden (für Replikate mit asynchronem Commit bedeutet manuelles Failover erzwungenes Failover mit möglichem Datenverlust).  
  
    ```sql
    -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     Weitere [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Codebeispiele zur Erstellung einer Verfügbarkeitsgruppe finden Sie unter [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).  
  
5.  Verknüpfen Sie auf der Serverinstanz, die das sekundäre Replikat hostet, das sekundäre Replikat mit der Verfügbarkeitsgruppe.  
  
     Im folgenden Codebeispiel wird das sekundäre Replikat auf `COMPUTER02` mit der `MyAG` -Verfügbarkeitsgruppe verknüpft.  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  Auf der Serverinstanz, die das sekundäre Replikat hostet, erstellen Sie die sekundären Datenbanken.  
  
     Im folgenden Codebeispiel werden die sekundären Datenbanken *MyDb1* und *MyDb2* erstellt, indem Datenbanksicherungen mit RESTORE WITH NORECOVERY wiederhergestellt werden.  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO
    ```  
  
7.  Sichern Sie auf der Serverinstanz, die das primäre Replikat hostet, das Transaktionsprotokoll zu jeder der primären Datenbanken.  
  
    > [!IMPORTANT]  
    >  Wenn Sie eine echte Verfügbarkeitsgruppe konfigurieren, wird empfohlen, dass Sie vor Verwendung dieser Protokollsicherung Protokollsicherungstasks für die primären Datenbanken anhalten, bis Sie die entsprechenden sekundären Datenbanken mit der Verfügbarkeitsgruppe verknüpft haben.  
  
     Im folgenden Codebeispiel wird eine Transaktionsprotokollsicherung in MyDb1 und MyDb2 erstellt.  
  
    ```sql
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO
    ```  
  
    > [!TIP]  
    >  In der Regel muss für jede primäre Datenbank eine Protokollsicherung erstellt und dann in der entsprechenden sekundären Datenbank (mithilfe von WITH NORECOVERY) wiederhergestellt werden. Diese Protokollsicherung ist jedoch möglicherweise nicht erforderlich, wenn die Datenbank erst kürzlich erstellt wurde und bisher keine Protokollsicherung vorgenommen wurde oder wenn das Wiederherstellungsmodell soeben von SIMPLE in FULL geändert wurde.  
  
8.  Wenden Sie auf der Serverinstanz, die das sekundäre Replikat hostet, Protokollsicherungen für die sekundären Datenbanken an.  
  
     Im folgenden Codebeispiel werden Sicherungen auf die sekundären Datenbanken *MyDb1* und *MyDb2* angewendet, indem Datenbanksicherungen mit RESTORE WITH NORECOVERY wiederhergestellt werden.  
  
    > [!IMPORTANT]  
    >  Wenn Sie eine echte sekundäre Datenbank vorbereiten, müssen Sie jede Protokollsicherung anwenden, die seit der Datenbanksicherung erstellt wurde, aus der Sie die sekundäre Datenbank erstellt haben. Sie müssen dabei immer mit der frühesten Sicherung beginnen und RESTORE WITH NORECOVERY verwenden. Wenn Sie sowohl vollständige als auch differenzielle Datenbanksicherungen wiederherstellen, müssten Sie natürlich nur die nach der differenziellen Sicherung erstellten Protokollsicherungen anwenden.  
  
    ```sql
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. Verknüpfen Sie auf der Serverinstanz, die das sekundäre Replikat hostet, die neue sekundäre Datenbank mit der Verfügbarkeitsgruppe.  
  
     Im folgenden Codebeispiel wird die sekundäre Datenbank *MyDb1* und dann die sekundäre Datenbank *MyDb2* mit der *MyAG* -Verfügbarkeitsgruppe verknüpft.  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO
    ```  
  
###  <a name="complete-code-example-for-sample-configuration-procedure"></a><a name="CompleteCodeExample"></a> Vollständiges Codebeispiel für Beispielkonfigurationsprozedur  
 Im folgenden Beispiel werden die Codebeispiele aus allen Schritten der Beispielkonfigurationsprozedur zusammengeführt. In der folgenden Tabelle werden die in diesem Codebeispiel verwendeten Platzhalterwerte zusammengefasst. Weitere Informationen zu den Schritten in diesem Codebeispiel finden Sie unter [Erforderliche Komponenten für die Verwendung der Beispielkonfigurationsprozedur](#PrerequisitesForExample) und [Beispielkonfigurationsprozedur](#SampleProcedure)weiter oben in diesem Thema.  
  
|Platzhalter|BESCHREIBUNG|  
|-----------------|-----------------|  
|\\\\*FILESERVER*\\*SQLbackups*|Fiktive Sicherungsfreigabe.|  
|\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*|Sicherungsdatei für MyDb1.|  
|\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*|Sicherungsdatei für MyDb2.|  
|*7022*|Jedem Datenbankspiegelungs-Endpunkt zugewiesene Portnummer.|  
|*COMPUTER01\AgHostInstance*|Serverinstanz, die das ursprüngliche primäre Replikat hostet.|  
|*COMPUTER02*|Serverinstanz, die das ursprüngliche sekundäre Replikat hostet. Dies ist die Standardserverinstanz auf `COMPUTER02`.|  
|*dbm_endpoint*|Für jeden Datenbankspiegelungs-Endpunkt angegebener Name.|  
|*MyAG*|Der Name der Beispielsverfügbarkeitsgruppe.|  
|*MyDb1*|Der Name der ersten Beispieldatenbank.|  
|*MyDb2*|Der Name der zweiten Beispieldatenbank.|  
|*DOMAIN1\user1*|Dienstkonto der Serverinstanz, auf der das ursprüngliche primäre Replikat gehostet werden soll.|  
|*DOMAIN2\user2*|Dienstkonto der Serverinstanz, auf der das ursprüngliche primäre sekundäre Replikat gehostet werden soll.|  
|TCP://*COMPUTER01.Adventure-Works.com*:*7022*|Endpunkt-URL der AgHostInstance-Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf COMPUTER01.|  
|TCP://*COMPUTER02.Adventure-Works.com*:*5022*|Endpunkt-URL der Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf COMPUTER02.|  
  
> [!NOTE]  
>  Weitere [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Codebeispiele zur Erstellung einer Verfügbarkeitsgruppe finden Sie unter [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).  
  
```sql
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So konfigurieren Sie Verfügbarkeitsgruppen- und Replikateigenschaften**  
  
-   [Ändern des Verfügbarkeitsmodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Ändern des Failovermodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen für ein automatisches Failover (AlwaysOn-Verfügbarkeitsgruppen)](configure-flexible-automatic-failover-policy.md)  
  
-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Ändern des Sitzungstimeouts für ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **So schließen Sie die Konfiguration von Verfügbarkeitsgruppen ab**  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Alternative Möglichkeiten zum Erstellen einer Verfügbarkeitsgruppe**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeitsgruppe &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
 **So aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **So konfigurieren Sie einen Datenbankspiegelungs-Endpunkt**  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Problembehandlung für die AlwaysOn-Verfügbarkeitsgruppenkonfiguration**  
  
-   [Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfiguration (SQL Server) gelöscht](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [AlwaysON - HADRON-Lernreihe: Nutzung des Arbeitsthreadpools für HADRON-fähige Datenbanken](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos:**  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit hoher Verfügbarkeit](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 2: Erstellen einer unternehmenswichtigen Lösung für hohe Verfügbarkeit mit AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper:**  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
