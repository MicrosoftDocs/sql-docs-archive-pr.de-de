---
title: Angeben von Synchronisierungszeitplänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d752817f7d620b2c6e5fdc5eeb2178c50c42040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722690"
---
# <a name="specify-synchronization-schedules"></a>Angeben von Synchronisierungszeitplänen
  In diesem Thema wird beschrieben, wie Synchronisierungszeitpläne in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) angegeben werden. Während der Erstellung eines Abonnements kann ein Synchronisierungszeitplan definiert werden, der steuert, wann der Replikations-Agent für das Abonnement ausgeführt wird. Wenn Sie keine Zeitplanungsparameter angeben, wird der Standardzeitplan für das Abonnement verwendet.  
  
 Abonnements werden durch den Verteilungs-Agent (für Momentaufnahme- und Transaktionsveröffentlichungen) oder durch den Merge-Agent (für Mergeveröffentlichungen) synchronisiert. Agents können kontinuierlich, bei Bedarf oder nach einem Zeitplan ausgeführt werden.  
  
 **In diesem Thema**  
  
-   **So geben Sie Synchronisierungszeitpläne an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie Synchronisierungszeitpläne im Assistenten für neue Abonnements auf der Seite **Synchronisierungszeitplan** an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Create a Push Subscription](create-a-push-subscription.md) und [Create a Pull Subscription](create-a-pull-subscription.md).  
  
 Ändern Sie die Synchronisierungszeitpläne im Dialogfeld **Eigenschaften des Auftragszeitplans** . Dieses Dialogfeld ist in **über den Ordner** Aufträge [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und im Detailfenster des Agents im Replikationsmonitor verfügbar. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md).  
  
 Wenn Sie die Zeitpläne über den Ordner **Aufträge** angeben, verwenden Sie die folgende Tabelle, um den Auftragsnamen des Agents zu ermitteln.  
  
|Agent|Auftragsname|  
|-----------|--------------|  
|Merge-Agent für Pullabonnements|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|Merge-Agent für Pushabonnements|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|Verteilungs-Agent für Pushabonnements|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup>|  
|Verteilungs-Agent für Pullabonnements|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup>|  
|Verteilungs-Agent für Pushabonnements für Nicht-SQL Server-Abonnenten|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
  
 <sup>1</sup> Für Pushabonnements für Oracle-Veröffentlichungen lautet der Name **\<Publisher>-\<Publisher**> und nicht **\<Publisher>-\<PublicationDatabase>**  
  
 <sup>2</sup> Für Pullabonnements für Oracle-Veröffentlichungen lautet der Name **\<Publisher>-\<DistributionDatabase**> und nicht **\<Publisher>-\<PublicationDatabase>**  
  
#### <a name="to-specify-synchronization-schedules"></a>So geben Sie Synchronisierungszeitpläne an  
  
1.  Wählen Sie im Assistenten für neue Abonnements auf der Seite **Synchronisierungszeitplan** für jedes Abonnement, das Sie erstellen, einen der folgenden Werte aus der Dropdownliste **Agentzeitplan** aus:  
  
    -   **Fortlaufend ausführen**  
  
    -   **Nur bedarfsgesteuert ausführen**  
  
    -   **\<Define Schedule...>**  
  
2.  Geben Sie bei der Auswahl von **\<Define Schedule...>** im Dialogfeld **Eigenschaften des Auftragszeitplans** einen Zeitplan an, und klicken Sie dann auf **OK**.  
  
3.  Schließen Sie den Assistenten ab.  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a>So ändern Sie einen Synchronisierungszeitplan für ein Pushabonnement im Replikationsmonitor  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Details anzeigen**.  
  
4.  Klicken Sie im Fenster ** \< SubscriptionName> Abonnement** auf **Aktion**, und klicken Sie dann auf ** \<AgentName> Auftrags Eigenschaften**.  
  
5.  Klicken Sie im Dialogfeld **Auftragseigenschaften – \<JobName>** auf der Seite **Zeitpläne** auf **Bearbeiten**.  
  
6.  Wählen Sie im Dialogfeld **Eigenschaften des Auftragszeitplans** einen Wert aus der Dropdownliste **Zeitplantyp** aus:  
  
    -   Um eine fortlaufende Ausführung des Agents anzugeben, wählen Sie **Automatisch starten, wenn der SQL Server-Agent startet**aus.  
  
    -   Um eine Ausführung des Agents nach einem Zeitplan anzugeben, wählen Sie **Wiederholt**aus.  
  
    -   Um eine bedarfsgesteuerte Ausführung des Agents anzugeben, wählen Sie **Einmal**aus.  
  
7.  Geben Sie bei der Auswahl von **Wiederholt**einen Zeitplan für den Agent an.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a>So ändern Sie einen Synchronisierungszeitplan für ein Pushabonnement in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Auftrag für den Verteilungs-Agent oder Merge-Agent, der dem Abonnement zugeordnet ist, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Auftragseigenschaften – \<JobName>** auf der Seite **Zeitpläne** auf **Bearbeiten**.  
  
5.  Wählen Sie im Dialogfeld **Eigenschaften des Auftragszeitplans** einen Wert aus der Dropdownliste **Zeitplantyp** aus:  
  
    -   Um eine fortlaufende Ausführung des Agents anzugeben, wählen Sie **Automatisch starten, wenn der SQL Server-Agent startet**aus.  
  
    -   Um eine Ausführung des Agents nach einem Zeitplan anzugeben, wählen Sie **Wiederholt**aus.  
  
    -   Um eine bedarfsgesteuerte Ausführung des Agents anzugeben, wählen Sie **Einmal**aus.  
  
6.  Geben Sie bei der Auswahl von **Wiederholt**einen Zeitplan für den Agent an.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a>So ändern Sie einen Synchronisierungszeitplan für ein Pullabonnement in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Auftrag für den Verteilungs-Agent oder Merge-Agent, der dem Abonnement zugeordnet ist, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Klicken Sie im Dialogfeld **Auftragseigenschaften – \<JobName>** auf der Seite **Zeitpläne** auf **Bearbeiten**.  
  
5.  Wählen Sie im Dialogfeld **Eigenschaften des Auftragszeitplans** einen Wert aus der Dropdownliste **Zeitplantyp** aus:  
  
    -   Um eine fortlaufende Ausführung des Agents anzugeben, wählen Sie **Automatisch starten, wenn der SQL Server-Agent startet**aus.  
  
    -   Um eine Ausführung des Agents nach einem Zeitplan anzugeben, wählen Sie **Wiederholt**aus.  
  
    -   Um eine bedarfsgesteuerte Ausführung des Agents anzugeben, wählen Sie **Einmal**aus.  
  
6.  Geben Sie bei der Auswahl von **Wiederholt**einen Zeitplan für den Agent an.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können Synchronisierungszeitpläne mit gespeicherten Replikationsprozeduren programmgesteuert definieren. Welche gespeicherten Prozeduren Sie verwenden, hängt vom Typ der Replikation und vom Typ des Abonnements (Pull oder Push) ab.  
  
 Ein Zeitplan wird durch die folgenden Zeitplanungsparameter definiert, deren Verhalten von [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) geerbt wird:  
  
-   **@frequency_type**: der Typ der Häufigkeit, die beim Planen des Agents verwendet wird.  
  
-   **@frequency_interval**-der Wochentag, an dem ein Agent ausgeführt wird.  
  
-   **@frequency_relative_interval**-die Woche eines bestimmten Monats, an der der Agent monatlich ausgeführt werden soll.  
  
-   **@frequency_recurrence_factor**: die Anzahl der Einheiten für den Häufigkeits Wert, die zwischen den Synchronisierungs Einheiten auftreten.  
  
-   **@frequency_subday**-die Häufigkeits Einheit, wenn der Agent mehrmals täglich ausgeführt wird.  
  
-   **@frequency_subday_interval**: die Anzahl der Einheiten für die Häufigkeit zwischen den Ausführungen, wenn der Agent mehrmals täglich ausgeführt wird.  
  
-   **@active_start_time_of_day**: die früheste Uhrzeit an einem bestimmten Tag, zu der eine agenttestlauf gestartet wird.  
  
-   **@active_end_time_of_day**: die letzte Uhrzeit an einem bestimmten Tag, zu der eine agenttestlauf gestartet wird.  
  
-   **@active_start_date**-der erste Tag, an dem der Agentzeitplan in Kraft ist.  
  
-   **@active_end_date**-der letzte Tag, an dem der Agentzeitplan in Kraft ist.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a>So definieren Sie den Synchronisierungszeitplan für ein Pullabonnement für eine Transaktionsveröffentlichung  
  
1.  Erstellen Sie ein neues Pullabonnement für eine Transaktionsveröffentlichung. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
2.  Führen Sie auf dem Abonnenten [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** und die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmelde Informationen an, unter denen die Verteilungs-Agent auf dem Abonnenten für **@job_name** und **@password** ausgeführt wird. Geben Sie die oben beschriebenen Synchronisierungsparameter an, mit denen der Zeitplan für den Verteilungs-Agentauftrag zur Synchronisierung des Abonnements definiert wird.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a>So definieren Sie den Synchronisierungszeitplan für ein Pushabonnement für eine Transaktionsveröffentlichung  
  
1.  Erstellen Sie ein neues Pushabonnement für eine Transaktionsveröffentlichung. Weitere Informationen finden Sie unter [Create a Push Subscription](create-a-push-subscription.md).  
  
2.  Führen Sie auf dem Abonnenten [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) aus. Geben Sie **@subscriber** , **@subscriber_db** , **@publication** und die Windows-Anmelde Informationen an, unter denen die Verteilungs-Agent auf dem Abonnenten für und ausgeführt wird **@job_name** **@password** . Geben Sie die oben beschriebenen Synchronisierungsparameter an, mit denen der Zeitplan für den Verteilungs-Agentauftrag zur Synchronisierung des Abonnements definiert wird.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a>So definieren Sie den Synchronisierungszeitplan für ein Pullabonnement für eine Mergeveröffentlichung  
  
1.  Erstellen Sie ein neues Pullabonnement für eine Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
2.  Führen Sie auf dem Abonnenten [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** und die Windows-Anmelde Informationen an, unter denen die Merge-Agent auf dem Abonnenten für und ausgeführt wird **@job_name** **@password** . Geben Sie die oben beschriebenen Synchronisierungsparameter an, mit denen der Zeitplan für den Merge-Agentauftrag zur Synchronisierung des Abonnements definiert wird.  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a>So definieren Sie den Synchronisierungszeitplan für ein Pushabonnement für eine Mergeveröffentlichung  
  
1.  Erstellen Sie ein neues Pushabonnement für eine Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Push Subscription](create-a-push-subscription.md).  
  
2.  Führen Sie auf dem Abonnenten [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)aus. Geben Sie **@subscriber** , **@subscriber_db** , **@publication** und die Windows-Anmelde Informationen an, unter denen die Merge-Agent auf dem Abonnenten für und ausgeführt wird **@job_name** **@password** . Geben Sie die oben beschriebenen Synchronisierungsparameter an, mit denen der Zeitplan für den Merge-Agentauftrag zur Synchronisierung des Abonnements definiert wird.  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Die Replikation verwendet den SQL Server-Agent, um Aufträge für regelmäßig auftretende Aktivitäten wie die Momentaufnahmegenerierung und die Abonnementsynchronisierung zu planen. Sie können Replikationsverwaltungsobjekte (RMO) programmgesteuert verwenden, um Zeitpläne für Replikations-Agentaufträge anzugeben.  
  
> [!NOTE]  
>  Wenn Sie ein Abonnement erstellen und den Wert `false` für `CreateSyncAgentByDefault` (das Standardverhalten für Pullabonnements) angeben, wird der Agentauftrag nicht erstellt und die Zeitplanungseigenschaften werden ignoriert. In diesem Fall muss der Synchronisierungszeitplan von der Anwendung bestimmt werden. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md) und [Create a Push Subscription](create-a-push-subscription.md).  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a>So definieren Sie einen Zeitplan des Replikations-Agents, wenn Sie ein Pushabonnement für eine Transaktionsveröffentlichung erstellen  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransSubscription> -Klasse für das Abonnement, das Sie erstellen. Weitere Informationen finden Sie unter [Create a Push Subscription](create-a-push-subscription.md).  
  
2.  Bevor Sie <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>aufrufen, legen Sie mindestens eines der folgenden Felder der <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> -Eigenschaft fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> &ndash; der Typ der Frequenz (z. B. täglich oder wöchentlich), den Sie beim Planen des Agents verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> &ndash; der Tag der Woche, an dem ein Agent ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> &ndash; die Woche eines gegebenen Monats, in der der Agent einmal monatlich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Synchronisierungen liegen.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> &ndash; die Einheit für die Frequenz, wenn der Agent täglich mehrmals ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Ausführungen liegen, wenn der Agent mehrmals täglich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> &ndash; der früheste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> &ndash; der späteste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> &ndash; der erste Tag, an dem der Agentzeitplan in Kraft ist.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> &ndash; der letzte Tag, an dem der Agentzeitplan in Kraft ist.  
  
    > [!NOTE]  
    >  Wenn Sie keine dieser Eigenschaften angeben, wird ein Standardwert festgelegt.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> -Methode auf, um das Abonnement zu erstellen.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a>So definieren Sie einen Zeitplan des Replikations-Agents, wenn Sie ein Pullabonnement für eine Transaktionsveröffentlichung erstellen  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Klasse für das Abonnement, das Sie erstellen. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
2.  Bevor Sie <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>aufrufen, legen Sie mindestens eines der folgenden Felder der <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> -Eigenschaft fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> &ndash; der Typ der Frequenz (z. B. täglich oder wöchentlich), den Sie beim Planen des Agents verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> &ndash; der Tag der Woche, an dem ein Agent ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> &ndash; die Woche eines bestimmten Monats, in der der Agent einmal monatlich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Synchronisierungen liegen.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> &ndash; die Einheit für die Frequenz, wenn der Agent täglich mehrmals ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Ausführungen liegen, wenn der Agent mehrmals täglich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> &ndash; der früheste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> &ndash; der späteste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> &ndash; der erste Tag, an dem der Agentzeitplan in Kraft ist.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> &ndash; der letzte Tag, an dem der Agentzeitplan in Kraft ist.  
  
    > [!NOTE]  
    >  Wenn Sie keine dieser Eigenschaften angeben, wird ein Standardwert festgelegt.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> -Methode auf, um das Abonnement zu erstellen.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a>So definieren Sie einen Zeitplan des Replikations-Agents, wenn Sie ein Pullabonnement für eine Mergeveröffentlichung erstellen  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Klasse für das Abonnement, das Sie erstellen. Weitere Informationen finden Sie unter [Create a Pull Subscription](create-a-pull-subscription.md).  
  
2.  Bevor Sie <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>aufrufen, legen Sie mindestens eines der folgenden Felder der <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> -Eigenschaft fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> &ndash; der Typ der Frequenz (z. B. täglich oder wöchentlich), den Sie beim Planen des Agents verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> &ndash; der Tag der Woche, an dem ein Agent ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> &ndash; die Woche eines bestimmten Monats, in der der Agent einmal monatlich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Synchronisierungen liegen.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> &ndash; die Einheit für die Frequenz, wenn der Agent täglich mehrmals ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Ausführungen liegen, wenn der Agent mehrmals täglich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> &ndash; der früheste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> &ndash; der späteste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> &ndash; der erste Tag, an dem der Agentzeitplan in Kraft ist.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> &ndash; der letzte Tag, an dem der Agentzeitplan in Kraft ist.  
  
    > [!NOTE]  
    >  Wenn Sie keine dieser Eigenschaften angeben, wird ein Standardwert festgelegt.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> -Methode auf, um das Abonnement zu erstellen.  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a>So definieren Sie einen Zeitplan des Replikations-Agents, wenn Sie ein Pushabonnement für eine Mergeveröffentlichung erstellen  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeSubscription> -Klasse für das Abonnement, das Sie erstellen. Weitere Informationen finden Sie unter [Create a Push Subscription](create-a-push-subscription.md).  
  
2.  Bevor Sie <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>aufrufen, legen Sie mindestens eines der folgenden Felder der <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> -Eigenschaft fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> &ndash; der Typ der Frequenz (z. B. täglich oder wöchentlich), den Sie beim Planen des Agents verwenden.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> &ndash; der Tag der Woche, an dem ein Agent ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> &ndash; die Woche eines bestimmten Monats, in der der Agent einmal monatlich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Synchronisierungen liegen.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> &ndash; die Einheit für die Frequenz, wenn der Agent täglich mehrmals ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> &ndash; die Anzahl der Einheiten für die Frequenz, die zwischen den einzelnen Ausführungen liegen, wenn der Agent mehrmals täglich ausgeführt wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> &ndash; der früheste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> &ndash; der späteste Zeitpunkt an einem bestimmten Tag, zu dem eine Agent-Ausführung gestartet wird.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> &ndash; der erste Tag, an dem der Agentzeitplan in Kraft ist.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> &ndash; der letzte Tag, an dem der Agentzeitplan in Kraft ist.  
  
    > [!NOTE]  
    >  Wenn Sie keine dieser Eigenschaften angeben, wird ein Standardwert festgelegt.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> -Methode auf, um das Abonnement zu erstellen.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> Beispiel (RMO)  
 In diesem Beispiel werden ein Pushabonnement für eine Mergeveröffentlichung erstellt und der Zeitplan angegeben, mit dem das Abonnement synchronisiert wird.  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)   
 [Synchronisieren eines Pushabonnements](synchronize-a-push-subscription.md)   
 [Synchronisieren eines Pullabonnements](synchronize-a-pull-subscription.md)   
 [Synchronisieren von Daten](synchronize-data.md)  
  
  
