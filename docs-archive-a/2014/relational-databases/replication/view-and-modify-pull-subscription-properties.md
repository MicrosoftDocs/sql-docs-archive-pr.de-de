---
title: Anzeigen und Ändern der Eigenschaften von Pullabonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b847a22d31bbf3ea7540c55339fe27531134125
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608506"
---
# <a name="view-and-modify-pull-subscription-properties"></a>Anzeigen und Ändern der Eigenschaften von Pullabonnements
  In diesem Thema wird beschrieben, wie die Eigenschaften von Pullabonnements in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) angezeigt und geändert werden.  
  
 **In diesem Thema**  
  
-   **So können Sie Eigenschaften von Pullabonnements anzeigen und ändern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Das Anzeigen der Eigenschaften von Pullabonnements vom Verleger oder Abonnenten aus ist über das Dialogfeld **Abonnementeigenschaften – \<Publisher>: \<PublicationDatabase>** möglich, das in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbar ist. Weitere Eigenschaften können vom Abonnenten aus angezeigt werden, und das Ändern der Eigenschaften ist auf dem Abonnenten möglich. Das Anzeigen von Eigenschaften ist vom Verleger aus über die Registerkarte **Alle Abonnements** möglich, die im Replikationsmonitor verfügbar ist. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a>So zeigen Sie Eigenschaften von Pullabonnements vom Verleger aus in Management Studio an  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Erweitern Sie die entsprechende Veröffentlichung, klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Zeigen Sie die Eigenschaften an, und klicken Sie dann auf **OK**.  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a>So zeigen Sie Eigenschaften von Pullabonnements vom Abonnent aus in Management Studio an und ändern sie  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a>So zeigen Sie Eigenschaften von Pullabonnements vom Verleger aus im Replikationsmonitor an  
  
1.  Erweitern Sie im linken Bereich des Replikationsmonitors eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf ein Abonnement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Zeigen Sie die Eigenschaften an, und klicken Sie dann auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Pullabonnements können geändert und auf ihre Eigenschaften kann mithilfe gespeicherter Replikationsprozeduren programmgesteuert zugegriffen werden. Welche gespeicherten Prozeduren verwendet werden, hängt vom Typ der Veröffentlichung ab, zu der das Abonnement gehört.  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften eines Pullabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung an  
  
1.  Führen Sie auf dem Abonnenten [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** und an **@publication** . Dadurch werden Informationen über das Abonnement zurückgegeben, das in Systemtabellen beim Abonnenten gespeichert ist.  
  
2.  Führen Sie auf dem Abonnenten [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** und einen der folgenden Werte für an **@publication_type** :  
  
    -   **0** &ndash; Das Abonnement gehört zu einer Transaktionsveröffentlichung  
  
    -   **1** &ndash; Das Abonnement gehört zu einer Momentaufnahmeveröffentlichung.  
  
3.  Führen Sie auf dem Verleger [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)aus. Geben Sie **@publication** und an **@subscriber** .  
  
4.  Führen Sie [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)auf dem Verleger aus, und geben Sie an **@subscriber** . Dadurch werden Informationen zu dem Abonnenten angezeigt.  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So ändern Sie die Eigenschaften eines Pullabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Abonnenten [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql)aus, **@publisher** und geben Sie dabei, **@publisher_db** , **@publication** , den Wert **0** (transaktional) oder **1** (Momentaufnahme) für **@publication_type** , die zu ändernde Abonnement Eigenschaft als **@property** und den neuen Wert als **@value** .  
  
2.  (Optional) Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql)aus. Geben Sie die ID des Verteilungs-Agent Auftrags für **@jobid** und die folgenden DTS-Paket Eigenschaften (Data Transformation Services) an:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Dadurch werden die DTS-Paketeigenschaften eines Abonnements geändert.  
  
    > [!NOTE]  
    >  Die Auftrag-ID erhalten Sie, wenn Sie [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)ausführen.  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a>So zeigen Sie die Eigenschaften eines Pullabonnements für eine Mergeveröffentlichung an  
  
1.  Führen Sie auf dem Abonnenten [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** und an **@publication** .  
  
2.  Führen Sie auf dem Abonnenten [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , und den **@publication** Wert 2 für an **@publication_type** .  
  
3.  Führen Sie auf dem Verleger [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) aus, um Abonnementinformationen anzuzeigen. Zum Zurückgeben von Informationen zu einem bestimmten Abonnement müssen Sie **@publication** , **@subscriber** und den Wert **Pull** für angeben **@subscription_type** .  
  
4.  Führen Sie [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)auf dem Verleger aus, und geben Sie an **@subscriber** . Dadurch werden Informationen zu dem Abonnenten angezeigt.  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a>So ändern Sie die Eigenschaften eines Pullabonnements für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Abonnenten [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql)aus. Geben **@publication** **@publisher** Sie,, **@publisher_db** , die zu ändernde Abonnement Eigenschaft als **@property** und den neuen Wert als **@value** .  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Die RMO-Klassen, mit denen Sie die Eigenschaften von Pullabonnements anzeigen oder ändern, hängen vom Typ der Veröffentlichung ab, für die das Pullabonnement erstellt wird.  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>So zeigen Sie die Eigenschaften eines Pullabonnements für eine Momentaufnahme- oder eine Transaktionsveröffentlichung an oder ändern sie  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPullSubscription>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>und <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> fest.  
  
4.  Legen Sie die Verbindung aus Schritt 1 für die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 3 falsch definiert, oder das Abonnement ist auf dem Server nicht vorhanden.  
  
6.  (Optional) Zum Ändern der Eigenschaften legen Sie einen neuen Wert für eine der <xref:Microsoft.SqlServer.Replication.TransPullSubscription> -Eigenschaften fest, die definiert werden können, und rufen Sie dann die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> -Methode auf.  
  
7.  (Optional) Um die neuen Einstellungen anzuzeigen, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> -Methode auf, um die Eigenschaften für den Artikel erneut zu laden.  
  
8.  Trennen Sie alle Verbindungen.  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a>So zeigen Sie die Eigenschaften eines Pullabonnements für eine Mergeveröffentlichung an oder ändern sie  
  
1.  Erstellen Sie eine Verbindung mit dem Abonnenten, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePullSubscription>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>und <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> fest.  
  
4.  Legen Sie die Verbindung aus Schritt 1 für die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft fest.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder die Abonnementeigenschaften in Schritt 3 falsch definiert, oder das Abonnement ist auf dem Server nicht vorhanden.  
  
6.  (Optional) Zum Ändern der Eigenschaften legen Sie einen neuen Wert für eine der <xref:Microsoft.SqlServer.Replication.MergePullSubscription> -Eigenschaften fest, die definiert werden können, und rufen Sie dann die <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> -Methode auf.  
  
7.  (Optional) Um die neuen Einstellungen anzuzeigen, rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> -Methode auf, um die Eigenschaften für den Artikel erneut zu laden.  
  
8.  Trennen Sie alle Verbindungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
