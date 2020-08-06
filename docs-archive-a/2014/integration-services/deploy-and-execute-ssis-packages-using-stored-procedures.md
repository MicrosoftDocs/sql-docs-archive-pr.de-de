---
title: Bereitstellen und Ausführen von SSIS-Paketen mit gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1570207dca6e944b54c553a1d83256d8f4fa3244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724006"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a>Bereitstellen und Ausführen von SSIS-Paketen mithilfe von gespeicherten Prozeduren
  Wenn Sie ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt für die Verwendung des Projektbereitstellungsmodells konfigurieren, können Sie gespeicherte Prozeduren im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Katalog verwenden, um das Projekt bereitzustellen und die Pakete auszuführen. Informationen zum Projektbereitstellungsmodell finden Sie unter [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Sie können auch [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] zum Bereitstellen des Projekts und zum Ausführen der Pakete verwenden. Weitere Informationen finden Sie in den im Abschnitt **Siehe auch** aufgeführten Themen.  
  
> [!TIP]
>  Die Transact-SQL-Anweisungen für die im nachstehenden Verfahren aufgelisteten gespeicherten Prozeduren – mit Ausnahme von catalog.deploy_project – können problemlos generiert werden, indem Sie folgende Schritte ausführen:  
> 
>  1.  Erweitern Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]den Knoten **Integration Services-Kataloge** im Objekt-Explorer und navigieren Sie zu dem Paket, das Sie ausführen möchten.  
> 2.  Klicken Sie mit der rechten Maustaste auf das Paket, und klicken Sie dann auf **Ausführen**.  
> 3.  Legen Sie nach Bedarf Parameterwerte, Verbindungs-Manager-Eigenschaften und Optionen auf der Registerkarte **Erweitert** fest, zum Beispiel den Protokolliergrad.  
> 
>      Weitere Informationen zu Protokolliergraden finden Sie unter [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).  
> 4.  Bevor Sie auf **OK** klicken, um das Paket auszuführen, klicken Sie auf **Skript**. Die Transact-SQL-Anweisung wird in einem Fenster des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]angezeigt.  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a>So stellen Sie ein Paket mit gespeicherten Prozeduren bereit und führen es aus  
  
1.  Rufen Sie [catalog.deploy_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) auf, um das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt bereitzustellen, das das Paket für den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server enthält.  
  
     Um den binären Inhalt der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Projekt Bereitstellungs Datei abzurufen, verwenden Sie für den * \@ project_stream* -Parameter eine SELECT-Anweisung mit der OPENROWSET-Funktion und dem BULK-Rowsetanbieter. Der BULK-Rowsetanbieter ermöglicht es Ihnen, Daten aus einer Datei zu lesen. Das SINGLE_BLOB-Argument für den BULK-Rowsetanbieter gibt den Inhalt der Datendatei als einzeiliges, einspaltiges Rowset vom Typ "varbinary(max)" zurück. Weitere Informationen finden Sie unter [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
     Im folgenden Beispiel wird das SSISPackages_ProjectDeployment-Projekt im Ordner „SSIS-Pakete“ auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitgestellt. Die Binärdaten werden aus der Projektdatei (SSISPackage_ProjectDeployment. ispac) gelesen und im * \@ projectbinary* -Parameter vom Typ "varbinary (max)" gespeichert. Der * \@ projectbinary* -Parameterwert wird dem * \@ project_stream* -Parameter zugewiesen.  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  Rufen Sie [catalog.create_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) auf, um eine Instanz der Paketausführung zu erstellen, und rufen Sie optional [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) auf, um Laufzeitparameterwerte festzulegen.  
  
     Im folgenden Beispiel erstellt catalog.create_execution eine Ausführungsinstanz für package.dtsx, das im SSISPackage_ProjectDeployment-Projekt enthalten ist. Das Projekt befindet sich im Ordner "SSIS-Pakete". Die von der gespeicherten Prozedur zurückgegebene execution_id wird im Aufruf von catalog.set_execution_parameter_value verwendet. Die zweite gespeicherte Prozedur legt den LOGGING_LEVEL-Parameter auf 3 (ausführliche Protokollierung) und einen Paketparameter namens Parameter1 auf den Wert 1 fest.  
  
     Für Parameter wie LOGGING_LEVEL hat object_type den Wert 50. Für Paketparameter hat object_type den Wert 30.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  Rufen Sie [catalog.start_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) auf, um das Paket auszuführen.  
  
     Im folgenden Beispiel wird der Transact-SQL-Anweisung ein Aufruf von catalog.start_execution hinzugefügt, um die Paketausführung zu starten. Dabei wird die von der gespeicherten Prozedur catalog.create_execution zurückgegebene execution_id verwendet.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a>So stellen Sie ein Projekt mithilfe von gespeicherten Prozeduren zwischen Servern bereit  
 Sie können mit den gespeicherten Prozeduren [catalog.get_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) und [catalog.deploy_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) ein Projekt von Server zu Server bereitstellen.  
  
 Bevor Sie die gespeicherten Prozeduren ausführen, müssen Sie die folgenden Schritte ausführen.  
  
-   Erstellen Sie ein Verbindungsserverobjekt. Weitere Informationen finden Sie unter [Erstellen von Verbindungsservern &#40;SQL Server-Datenbank-Engine&#41;](../database-engine/sql-server-database-engine-overview.md).  
  
     Legen Sie auf der Seite **Serveroptionen** des Dialogfelds **Eigenschaften des Verbindungsservers** die Optionen **RPC** und **RPC-Ausgabe** auf **True**fest. Legen Sie außerdem **Höherstufung von verteilten Transaktionen für RPC aktivieren** auf **False**fest.  
  
-   Aktivieren Sie dynamische Parameter für den Anbieter, den Sie für den Verbindungsserver ausgewählt haben, indem Sie im Objekt-Explorer unter **Verbindungsserver** den Knoten **Anbieter** erweitern, mit der rechten Maustaste auf den Anbieter klicken und dann auf **Eigenschaften**klicken. Wählen Sie **Aktivieren** neben **Dynamischer Parameter**aus.  
  
-   Überprüfen Sie, ob der Distributed Transaction Coordinator (DTC) auf beiden Servern gestartet ist.  
  
 Rufen Sie catalog.get_project auf, um die Binärdatei für das Projekt zurückzugeben, und rufen Sie dann catalog.deploy_project auf. Der von catalog.get_project zurückgegebene Wert wird in eine Tabellenvariable des Typs "varbinary(max)" eingefügt. Der Verbindungsserver kann keine Ergebnisse vom Typ „varbinary(max)“ zurückgeben.  
  
 Im folgenden Beispiel gibt catalog.get_project eine Binärdatei für das SSISPackages-Projekt auf dem Verbindungsserver zurück. Das catalog.deploy_project stellt das Projekt auf dem lokalen Server im Ordner DestFolder bereit.  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen von Projekten auf Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Ausführen eines Pakets in SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md)   
 [Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
