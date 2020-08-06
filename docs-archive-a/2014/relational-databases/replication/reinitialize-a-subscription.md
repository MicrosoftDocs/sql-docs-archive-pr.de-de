---
title: Erneutes Initialisieren eines Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f751928c05caa5c4acdcc6c667dc59bb7824021b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725453"
---
# <a name="reinitialize-a-subscription"></a>Erneutes Initialisieren eines Abonnements
  In diesem Thema wird beschrieben, wie ein Abonnement in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) neu initialisiert wird. Einzelne Abonnements können für die erneute Initialisierung markiert werden, sodass während der nächsten Synchronisierung eine neue Momentaufnahme angewendet wird.  
  
 **In diesem Thema**  
  
-   **So initialisieren Sie ein Abonnement erneut mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Das erneute Initialisieren eines Abonnements ist ein zweistufiger Prozess:  
  
1.  Zunächst müssen die Abonnements für eine Veröffentlichung, die erneut initialisiert werden sollen, *gekennzeichnet* werden. Das Kennzeichnen der Abonnements für die erneute Initialisierung erfolgt im Dialogfeld **Abonnements erneut initialisieren**, das über die Ordner **Lokale Veröffentlichungen** und **Lokale Abonnements** in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbar ist. Abonnements können darüber hinaus auch auf der Registerkarte **Alle Abonnements** und über den Veröffentlichungsknoten im Replikationsmonitor als erneut zu initialisieren gekennzeichnet werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md). Beim Kennzeichnen eines Abonnements für die erneute Initialisierung können Sie zwischen den folgenden Optionen auswählen:  
  
     **Aktuelle Momentaufnahme verwenden**  
     Wählen Sie diese Option aus, wenn die aktuelle Momentaufnahme beim nächsten Ausführen des Verteilungs- oder Merge-Agents auf den Abonnenten angewendet werden soll. Wenn keine gültige Momentaufnahme verfügbar ist, kann diese Option nicht ausgewählt werden.  
  
     **Neue Momentaufnahme verwenden**  
     Wählen Sie diese Option aus, wenn das Abonnement mithilfe einer neuen Momentaufnahme erneut initialisiert werden soll. Die Momentaufnahme kann erst auf den Abonnenten angewendet werden, nachdem sie vom Momentaufnahme-Agent generiert wurde. Wenn die Ausführung des Momentaufnahme-Agents auf einem Zeitplan basiert, wird das Abonnement erst nach der nächsten zeitplangesteuerten Ausführung des Momentaufnahme-Agents initialisiert. Wählen Sie die Option **Neue Momentaufnahme jetzt generieren** , um den Momentaufnahme-Agent sofort zu starten.  
  
     **Unsynchronisierte Änderungen am Abonnenten vor der erneuten Initialisierung hochladen**  
     Nur für Mergereplikationen zulässig. Wählen Sie diese Option aus, um alle ausstehenden Änderungen aus der Abonnementdatenbank herunterzuladen, bevor die Daten des Abonnenten durch eine Momentaufnahme überschrieben werden.  
  
     Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  Ein Abonnement wird erneut initialisiert, sobald es wieder synchronisiert wird: Der Verteilungs-Agent (bei einer Transaktionsreplikation) bzw. der Merge-Agent (bei einer Mergereplikation) wendet auf alle Abonnenten mit einem Abonnement, das für eine erneute Initialisierung gekennzeichnet ist, die jeweils neueste Momentaufnahme an. Weitere Informationen zum Synchronisieren von Abonnements finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md) und [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)verfügbar ist.  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a>So kennzeichnen Sie ein einzelnes Push- oder Pullabonnement für die erneute Initialisierung in SQL Server Management Studio (auf dem Verleger)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Erweitern Sie die Veröffentlichung mit dem Abonnement, das erneut initialisiert werden soll.  
  
4.  Klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Erneut initialisieren**.  
  
5.  Wählen Sie im Dialogfeld **Abonnements erneut initialisieren** die gewünschten Optionen aus, und klicken Sie dann auf **Für erneute Initialisierung kennzeichnen**.  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a>So kennzeichnen Sie ein einzelnes Pullabonnement für die erneute Initialisierung in SQL Server Management Studio (auf dem Abonnenten)  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Erneut initialisieren**.  
  
4.  Klicken Sie im angezeigten Bestätigungsdialogfeld auf **Ja**.  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a>So kennzeichnen Sie alle Abonnements für die erneute Initialisierung in SQL Server Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung mit den Abonnements, die erneut initialisiert werden sollen, und klicken Sie dann auf **Alle Abonnements erneut initialisieren**.  
  
4.  Wählen Sie im Dialogfeld **Abonnements erneut initialisieren** die gewünschten Optionen aus, und klicken Sie dann auf **Für erneute Initialisierung kennzeichnen**.  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a>So kennzeichnen Sie ein einzelnes Push- oder Pullabonnement für die erneute Initialisierung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das Abonnement, das Sie erneut initialisieren möchten, und klicken Sie dann auf **Abonnement erneut initialisieren**.  
  
4.  Wählen Sie im Dialogfeld **Abonnements erneut initialisieren** die gewünschten Optionen aus, und klicken Sie dann auf **Für erneute Initialisierung kennzeichnen**.  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a>So kennzeichnen Sie alle Abonnements für die erneute Initialisierung im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung mit den Abonnements, die erneut initialisiert werden sollen, und klicken Sie dann auf **Alle Abonnements erneut initialisieren**.  
  
3.  Wählen Sie im Dialogfeld **Abonnements erneut initialisieren** die gewünschten Optionen aus, und klicken Sie dann auf **Für erneute Initialisierung kennzeichnen**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Abonnements können mithilfe von gespeicherten Replikationsprozeduren programmgesteuert erneut initialisiert werden. Welche gespeicherte Prozedur verwendet wird, hängt dem Typ des Abonnements (d. h. Push- oder Pullabonnement) und vom Typ der Veröffentlichung ab, zu der das Abonnement gehört.  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a>So initialisieren Sie ein Pullabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql) aus. Geben Sie **@publisher** , **@publisher_db** und an **@publication** . Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
2.  (Optional) Starten Sie den Verteilungs-Agent auf dem Abonnenten, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a>So initialisieren Sie ein Pushabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Führen Sie auf dem Verleger [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql) aus. Geben Sie **@publication** , **@subscriber** und an **@destination_db** . Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
2.  (Optional) Starten Sie den Verteilungs-Agent auf dem Verteiler, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a>So initialisieren Sie ein Pullabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql) aus. Geben Sie **@publisher** , **@publisher_db** und an **@publication** . Wenn vor der erneuten Initialisierung Änderungen vom Abonnenten hochgeladen werden sollen, geben Sie den Wert `true` für an **@upload_first** . Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Merge-Agents markiert.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  (Optional) Starten Sie den Merge-Agent auf dem Abonnenten, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a>So initialisieren Sie ein Pushabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Führen Sie auf dem Verleger [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql) aus. Geben Sie **@publication** , **@subscriber** und an **@subscriber_db** . Wenn vor der erneuten Initialisierung Änderungen vom Abonnenten hochgeladen werden sollen, geben Sie den Wert `true` für an **@upload_first** . Damit wird das Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents markiert.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
2.  (Optional) Starten Sie den Merge-Agent auf dem Verteiler, um das Abonnement zu synchronisieren. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a>So legen Sie die Neuinitialisierungsrichtlinie während der Erstellung einer neuen Mergeveröffentlichung fest  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)unter Angabe eines der folgenden Werte für **@automatic_reinitialization_policy**aus:  
  
    -   **1** &ndash; Änderungen werden vom Abonnenten hochgeladen, bevor eine automatische Neuinitialisierung des Abonnements durchgeführt wird, die durch eine Änderung an der Veröffentlichung erforderlich wurde.  
  
    -   **0** &ndash; Änderungen am Abonnenten werden verworfen, bevor eine automatische Neuinitialisierung des Abonnements durchgeführt wird, die durch eine Änderung an der Veröffentlichung erforderlich wurde.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
     Weitere Informationen finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a>So ändern Sie die Neuinitialisierungsrichtlinie für eine vorhandene Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)unter Angabe von **automatic_reinitialization_policy** für **@property** und einem der folgenden Werte für **@value**aus:  
  
    -   **1** &ndash; Änderungen werden vom Abonnenten hochgeladen, bevor eine automatische Neuinitialisierung des Abonnements durchgeführt wird, die durch eine Änderung an der Veröffentlichung erforderlich wurde.  
  
    -   **0** &ndash; Änderungen am Abonnenten werden verworfen, bevor eine automatische Neuinitialisierung des Abonnements durchgeführt wird, die durch eine Änderung an der Veröffentlichung erforderlich wurde.  
  
    > [!IMPORTANT]  
    >  Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
     Weitere Informationen finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Einzelne Abonnements können für die erneute Initialisierung markiert werden, sodass während der nächsten Synchronisierung eine neue Momentaufnahme angewendet wird. Abonnements können mithilfe von Replikationsverwaltungsobjekten (RMO) programmgesteuert erneut initialisiert werden. Die zu verwendenden Klassen hängen Typ der Veröffentlichung, zu der das Abonnement gehört, und dem Typ des Abonnements ab (d. h. Push- oder Pullabonnement).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a>So initialisieren Sie ein Pullabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Klasse, und legen Sie <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>sowie die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
    > [!NOTE]  
    >  Wenn diese Methode `false` zurückgibt, wurden die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pullabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> -Methode auf. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
5.  Synchronisieren Sie das Pullabonnement. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a>So initialisieren Sie ein Pushabonnement für eine Transaktionsveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransSubscription> -Klasse, und legen Sie <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>sowie die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
    > [!NOTE]  
    >  Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pushabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> -Methode auf. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
5.  Synchronisieren Sie das Pushabonnement. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a>So initialisieren Sie ein Pullabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Klasse, und legen Sie <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>sowie die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
    > [!NOTE]  
    >  Wenn diese Methode `false` zurückgibt, wurden die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pullabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> -Methode auf. Übergeben Sie den Wert `true`, wenn vor der erneuten Initialisierung Änderungen beim Abonnenten hochgeladen werden sollen, oder übergeben Sie den Wert `false`, wenn sofort erneut initialisiert und Änderungen beim Abonnenten nicht gespeichert werden sollen. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
    > [!NOTE]  
    >  Änderungen können nicht hochgeladen werden, wenn das Abonnement abgelaufen ist. Weitere Informationen finden Sie unter [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Synchronisieren Sie das Pullabonnement. Weitere Informationen finden Sie unter [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a>So initialisieren Sie ein Pushabonnement mit einer Mergeveröffentlichung erneut  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeSubscription> -Klasse, und legen Sie <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>sowie die Verbindung aus Schritt 1 für <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>fest.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen.  
  
    > [!NOTE]  
    >  Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 2 falsch definiert, oder das Pushabonnement ist nicht vorhanden.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> -Methode auf. Übergeben Sie den Wert `true`, wenn vor der erneuten Initialisierung Änderungen beim Abonnenten hochgeladen werden sollen, oder übergeben Sie den Wert `false`, wenn sofort erneut initialisiert und Änderungen beim Abonnenten nicht gespeichert werden sollen. Diese Methode markiert das Abonnement für die erneute Initialisierung.  
  
    > [!NOTE]  
    >  Änderungen können nicht hochgeladen werden, wenn das Abonnement abgelaufen ist. Weitere Informationen finden Sie unter [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).  
  
5.  Synchronisieren Sie das Pushabonnement. Weitere Informationen finden Sie unter [Synchronize a Push Subscription](synchronize-a-push-subscription.md).  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Beispiele (RMO)  
 Im folgenden Beispiel wird ein Pullabonnement für eine Transaktionsveröffentlichung erneut initialisiert.  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 In diesem Beispiel wird ein Pullabonnement für eine Transaktionsveröffentlichung erneut initialisiert, nachdem Änderungen beim Abonnenten hochgeladen wurden.  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren von Abonnements](reinitialize-subscriptions.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)  
  
  
