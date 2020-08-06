---
title: Arbeiten mit Replikations-Agent-Profilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc20451edfb1096fca7e468effb14df78b51f758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609145"
---
# <a name="work-with-replication-agent-profiles"></a>Arbeiten mit Replikations-Agent-Profilen
  In diesem Thema wird beschrieben, wie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) mit Replikations-Agentprofilen gearbeitet wird. Das Verhalten der einzelnen Replikations-Agents wird durch eine Reihe von Parametern gesteuert, die über Agentprofile festgelegt werden können. Jeder Agent weist ein Standardprofil auf, und einige Agents besitzen weitere vordefinierte Profile, wobei für einen Agent jeweils immer nur ein Profil aktiv ist.  
  
 **In diesem Thema**  
  
-   **So arbeiten Sie mit Replikations-Agentprofilen mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
    -   Auf das Dialogfeld Agentprofile zugreifen  
  
    -   Ein Profil für einen Agent angeben  
  
    -   Ein Profil erstellen  
  
    -   Ein Profil ändern  
  
    -   Ein Profil löschen  
  
     [Transact-SQL](#TsqlProcedure)  
  
    -   Ein Profil erstellen  
  
    -   Ein Profil ändern  
  
    -   Ein Profil löschen  
  
    -   Agentprofile während der Synchronisierung verwenden  
  
    -   Beispiel für Transact-SQL  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
    -   Ein Profil erstellen  
  
    -   Ein Profil ändern  
  
    -   Ein Profil löschen  
  
-   **Nachverfolgung:**  [Nach dem Ändern der Agentparameter](#FollowUp)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> So greifen Sie auf das Dialogfeld Agentprofile in SQL Server Management Studio zu  
  
1.  Klicken Sie im Dialogfeld **Verteilereigenschaften - \<Distributor>** auf der Seite **Allgemein** auf **Profilstandards**.  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a>So greifen Sie über den Replikationsmonitor auf das Dialogfeld Agentprofile zu  
  
-   Um das Dialogfeld für alle Agents zu öffnen, klicken Sie mit der rechten Maustaste auf einen Verleger, und klicken Sie dann auf **Agentprofile**.  
  
-   Gehen Sie folgendermaßen vor, um das Dialogfeld für einen Agent zu öffnen:  
  
    1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
    2.  Klicken Sie bei Verteilungs-Agent- oder Merge-Agent-Profilen auf der Registerkarte **Alle Abonnements** mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Agentprofil**. Klicken Sie bei anderen Agents auf der Registerkarte **Agents** mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**.  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> So geben Sie ein Profil für einen Agent an  
  
1.  Wenn im Dialogfeld **Agentprofile** Profile für mehrere Agents angezeigt werden, wählen Sie einen Agent aus.  
  
2.  Wählen Sie im Raster **Agentprofile** in der **Default for new** -Spalte ein Profil aus. Standardmäßig wird das Profil nur auf Agents für neue Veröffentlichungen und Abonnements angewendet.  
  
3.  Wenn Sie angeben möchten, dass dieses Profil von allen Agents des ausgewählten Typs für vorhandene Veröffentlichungen oder Abonnements verwendet werden soll, klicken Sie auf **Vorhandene Agents ändern**.  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> So zeigen Sie einem Profil zugeordnete Parameter an und bearbeiten Sie die Parameter  
  
1.  Wenn im Dialogfeld **Agentprofile** Profile für mehrere Agents angezeigt werden, wählen Sie einen Agent aus.  
  
2.  Klicken Sie auf die Eigenschaftenschaltfläche ( **…** ) neben einem Profil.  
  
3.  Im Dialogfeld **\<ProfileName>-Profileigenschaften** werden die Parameter und Werte angezeigt.  
  
    -   Parameter in benutzerdefinierten Profilen können bearbeitet werden; Parameter in vordefinierten Systemprofilen können nicht bearbeitet werden.  
  
    -   Um alle Parameter für einen Agent anzuzeigen, deaktivieren Sie das Kontrollkästchen **Nur die in diesem Profil verwendeten Parameter anzeigen** . Informationen zu den Agentparametern finden Sie unter den Links am Ende dieses Themas.  
  
4.  Klicken Sie auf **Schließen**.  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> So erstellen Sie ein benutzerdefiniertes Profil  
  
1.  Wenn im Dialogfeld **Agentprofile** Profile für mehrere Agents angezeigt werden, wählen Sie einen Agent aus.  
  
2.  Klicken Sie auf **Neu**.  
  
3.  Wählen Sie im Initialisierungsdialogfeld **Neues Agentprofil** ein vorhandenes Profil aus, auf dem das neue Profil basieren soll.  
  
4.  Geben Sie im Dialogfeld **Neues Agentprofil** Werte in die Textfelder **Name** und **Beschreibung** ein.  
  
5.  Ändern Sie die Parameter in dem gewünschten Profil entsprechend. Um alle Parameter für einen Agent anzuzeigen, deaktivieren Sie das Kontrollkästchen **Nur die in diesem Profil verwendeten Parameter anzeigen** . Informationen zu den Agentparametern finden Sie unter den Links am Ende dieses Themas.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> So löschen Sie ein benutzerdefiniertes Profil  
  
1.  Wenn im Dialogfeld **Agentprofile** Profile für mehrere Agents angezeigt werden, wählen Sie einen Agent aus.  
  
2.  Wenn ein Profil einem oder mehreren Agents zugeordnet ist, ändern Sie das Profil für diese Agents:  
  
    1.  Wählen Sie im Raster **Agentprofile** ein anderes Profil aus.  
  
    2.  Klicken Sie auf **Vorhandene Agents ändern**.  
  
        > [!NOTE]  
        >  Dadurch wird das Profil nicht nur für die Agents geändert, deren Profil Sie löschen möchten, sondern für alle Agents des ausgewählten Typs für vorhandene Veröffentlichungen oder Abonnements.  
  
3.  Wählen Sie das zu löschende Profil aus, und klicken Sie dann auf **Löschen**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> So erstellen Sie ein neues Agentprofil  
  
1.  Führen Sie auf dem Verteiler [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql) aus. Geben Sie **@name** , den Wert **1** für **@profile_type** und einen der folgenden Werte für an **@agent_type** :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Wenn dieses Profil zum neuen Standardprofil für den zugehörigen Typ von Replikations-Agent wird, geben Sie einen Wert **1** für **@default**. Der Bezeichner für das neue Profil wird mithilfe des **@profile_id** Output-Parameters zurückgegeben. Dadurch wird ein neues Profil mit einem Satz von Profilparametern erstellt, das auf dem Standardprofil des bestimmten Agenttyps basiert.  
  
2.  Nach der Erstellung des neuen Profils können Sie Standardparameter hinzufügen, entfernen oder ändern, um das Profil anzupassen.  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> So ändern Sie ein vorhandenes Agentprofil  
  
1.  Führen Sie auf dem Verteiler [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) aus. Geben Sie einen der folgenden Werte für an **@agent_type** :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Dadurch werden alle Profile für den angegebenen Agenttyp zurückgegeben. Beachten Sie den Wert **profile_id** im Resultset für das zu ändernde Profil.  
  
2.  Führen Sie auf dem Verteiler [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql) aus. Geben Sie den Bezeichner des Profils aus Schritt 1 für an **@profile_id** . Dadurch werden alle Parameter für das Profil zurückgegeben. Beachten Sie den Namen der zu ändernden Parameter bzw. der aus dem Profil zu entfernenden Parameter.  
  
3.  Führen Sie [sp_change_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql) aus, um den Wert eines Parameters in einem Profil zu ändern. Geben Sie den Bezeichner des Profils aus Schritt 1 für **@profile_id** , den Namen des Parameters, der geändert **@property** werden soll, und einen neuen Wert für den Parameter für an **@value** .  
  
    > [!NOTE]  
    >  Es ist nicht möglich, ein vorhandenes Agentprofil in das Standardprofil für einen Agent zu ändern. Stattdessen müssen Sie ein neues Profil als Standardprofil erstellen, wie in der vorherigen Prozedur beschrieben.  
  
4.  Führen [sp_drop_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql) aus, um einen Parameter von einem Profil zu entfernen. Geben Sie den Bezeichner des Profils aus Schritt 1 für **@profile_id** und den Namen des Parameters an, der entfernt werden soll **@parameter_name** .  
  
5.  Sie müssen die folgenden Schritte ausführen, um einem Profil einen neuen Parameter hinzuzufügen:  
  
    -   Fragen Sie die Tabelle [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) auf dem Verteiler ab, um die Profilparameter zu bestimmen, die für die einzelnen Agenttypen festgelegt werden können.  
  
    -   Führen Sie auf dem Verteiler [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql) aus. Geben Sie den Bezeichner des Profils aus Schritt 1 für **@profile_id** , den Namen eines gültigen Parameters, der hinzugefügt **@parameter_name** werden soll, und den Wert des Parameters für an **@parameter_value** .  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> So löschen Sie ein Agentprofil  
  
1.  Führen Sie auf dem Verteiler [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) aus. Geben Sie einen der folgenden Werte für an **@agent_type** :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Dadurch werden alle Profile für den angegebenen Agenttyp zurückgegeben. Beachten Sie den Wert **profile_id** im Resultset für das zu entfernende Profil.  
  
2.  Führen Sie auf dem Verteiler [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql) aus. Geben Sie den Bezeichner des Profils aus Schritt 1 für an **@profile_id** .  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> So verwenden Sie während der Synchronisierung Agentprofile  
  
1.  Führen Sie auf dem Verteiler [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql) aus. Geben Sie einen der folgenden Werte für an **@agent_type** :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Dadurch werden alle Profile für den angegebenen Agenttyp zurückgegeben. Notieren Sie den Wert `profile_name` im Resultset für das zu verwendende Profil.  
  
2.  Wenn der Agent von einem Agentauftrag aus gestartet wird, bearbeiten Sie den Auftrags Schritt, mit dem der Agent gestartet wird, um den Wert von zu bestimmen, der `profile_name` in Schritt 1 nach dem-Profile Name **-** Befehlszeilenparameter abgerufen wurde. Weitere Informationen finden Sie unter [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).  
  
3.  Wenn Sie den-Agent von der Eingabeaufforderung aus starten, geben Sie den Wert von an, der `profile_name` in Schritt 1 nach dem-Profile Name **-** Befehlszeilenparameter abgerufen wurde.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel werden ein benutzerdefiniertes Profil für den Merge-Agent mit der Bezeichnung **custom_merge**erstellt, der Wert des **-UploadReadChangesPerBatch** -Parameters geändert, ein neuer **-ExchangeType** -Parameter hinzugefügt und Informationen zu dem Profil, das erstellt wird, zurückgegeben.  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> Verwenden von RMO  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> So erstellen Sie ein neues Agentprofil  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie eine Instanz der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.AgentProfile>-Klasse.  
  
3.  Legen Sie die folgenden Eigenschaften für das Objekt fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - der Name des Profils.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - ein <xref:Microsoft.SqlServer.Replication.AgentType> -Wert, der den Typ des Replikations-Agents angibt, für den das Profil erstellt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - die in Schritt 1 erstellte <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
    -   (Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - eine Beschreibung des Profils.  
  
    -   (Optional) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> - Legen Sie diese Eigenschaft auf `true` fest, wenn alle neuen Agentaufträge für diesen <xref:Microsoft.SqlServer.Replication.AgentType> dieses Profil standardmäßig verwenden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> -Methode auf, um das Profil auf dem Server zu erstellen.  
  
5.  Sobald das Profil auf dem Server vorhanden ist, können Sie es anpassen, indem Sie Werte für die Parameter für Replikations-Agents hinzufügen, entfernen oder ändern.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> -Methode auf, um das Profil einem vorhandenen Auftrag des Replikations-Agents zuzuordnen. Übergeben Sie den Namen der Verteilungsdatenbank für *distributionDBName* und die ID des Auftrags für *agentID*.  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> So ändern Sie ein vorhandenes Agentprofil  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie eine Instanz der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.ReplicationServer>-Klasse. Übergeben Sie das in Schritt 1 erstellte <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Objekt.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf. Überprüfen Sie, ob der Verteiler vorhanden ist, wenn diese Methode `false` zurückgibt.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> -Methode auf. Übergeben Sie einen <xref:Microsoft.SqlServer.Replication.AgentType> -Wert, um die zurückgegebenen Profile für einen bestimmten Typ von Replikations-Agent einzugrenzen.  
  
5.  Rufen Sie das gewünschte <xref:Microsoft.SqlServer.Replication.AgentProfile> -Objekt von der zurückgegebenen <xref:System.Collections.ArrayList>ab, wobei die <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> -Eigenschaft des Objekt mit dem Profilnamen übereinstimmt.  
  
6.  Rufen Sie eine der folgenden Methoden von <xref:Microsoft.SqlServer.Replication.AgentProfile> auf, um das Profil zu ändern:  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - fügt dem Profil einen unterstützten Parameter hinzu, wobei *name* der Name des Parameters für den Replikations-Agent und *value* der angegebene Wert ist. Rufen Sie zum Aufzählen aller unterstützten Agentparameter für einen bestimmten Agenttyp die <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> -Methode auf. Diese Methode gibt eine <xref:System.Collections.ArrayList> von <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> -Objekten zurück, die alle unterstützten Parameter darstellen.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - entfernt einen vorhandenen Parameter aus dem Profil, wobei *name* der Name des Parameters für den Replikations-Agent ist. Rufen Sie zum Aufzählen aller aktuellen Agentparameter, die für das Profil definiert sind, die <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> -Methode auf. Diese Methode gibt eine <xref:System.Collections.ArrayList> von <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> -Objekten zurück, die den vorhandenen Parameter für dieses Profil darstellen.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - ändert die Einstellung eines vorhandenen Parameters im Profil, wobei *name* der Name des Agentparameters und *newValue* der Wert ist, in den der Parameter geändert wird. Rufen Sie zum Aufzählen aller aktuellen Agentparameter, die für das Profil definiert sind, die <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> -Methode auf. Diese Methode gibt eine <xref:System.Collections.ArrayList> von <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> -Objekten zurück, die den vorhandenen Parameter für dieses Profil darstellen. Rufen Sie zum Aufzählen aller unterstützten Einstellungen für den Agentparameter die <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> -Methode auf. Diese Methode gibt eine <xref:System.Collections.ArrayList> von <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> -Objekten zurück, die die unterstützten Werte für alle Parameter darstellen.  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> So löschen Sie ein Agentprofil  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie eine Instanz der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.AgentProfile>-Klasse. Legen Sie den Namen des Profils für <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> und <xref:Microsoft.SqlServer.Management.Common.ServerConnection> aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf. Wenn diese Methode `false` zurückgibt, wurde ein falscher Name angegeben, oder das Profil ist auf dem Server nicht vorhanden.  
  
4.  Stellen Sie sicher, dass die <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> -Eigenschaft auf <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>festgelegt ist, womit ein Kundenprofil angegeben wird. Entfernen Sie kein Profil, das einen Wert <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> für <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>aufweist.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> -Methode auf, um das benutzerdefinierte Profil, das durch dieses Objekt dargestellt wird, vom Server zu entfernen.  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Ändern der Agentparameter  
 Die Änderungen der Agentparameter treten in Kraft, wenn der Agent das nächste Mal gestartet wird. Wenn der Agent ständig ausgeführt wird, müssen Sie den Agent beenden und neu starten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations-Agent-Profile](replication-agent-profiles.md)   
 [Replication Snapshot Agent](replication-snapshot-agent.md)   
 [Replication Log Reader Agent](replication-log-reader-agent.md)   
 [Replication Distribution Agent](replication-distribution-agent.md)   
 [Replication Merge Agent](replication-merge-agent.md)   
 [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
  
