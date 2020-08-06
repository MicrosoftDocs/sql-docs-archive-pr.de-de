---
title: Umschalten zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630635"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a>Umschalten zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement
  In diesem Thema wird beschrieben, wie zwischen Updatemodi für ein aktualisierbares Transaktionsabonnement in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]umgeschaltet wird. Geben Sie im Assistenten für neue Abonnements den Modus für aktualisierbare Abonnements an. Weitere Informationen zum Festlegen des Modus bei der Verwendung dieses Assistenten finden Sie unter [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../view-and-modify-pull-subscription-properties.md).  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie können jederzeit ein Failover vom sofortigen Aktualisieren zum verzögerten Aktualisieren ausführen. Danach können Sie erst wieder zum sofortigen Aktualisieren wechseln, wenn der Abonnent und der Verleger verbunden sind und der Warteschlangenlese-Agent alle ausstehenden Nachrichten in der Warteschlange auf den Verleger angewendet hat.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Wenn ein Abonnement mit Aktualisierung mit einer Transaktionsveröffentlichung ein Failover von einem Aktualisierungsmodus zu einem anderen unterstützt, können Sie programmgesteuert den Aktualisierungsmodus wechseln, um Situationen zu bewältigen, in denen sich die Verbindung für eine kurze Zeitdauer ändert. Der Updatemodus kann mithilfe gespeicherter Replikationsprozeduren programm- und bedarfsgesteuert festgelegt werden. Weitere Informationen finden Sie unter [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
> [!NOTE]  
>  Damit der Updatemodus nach dem Erstellen des Abonnements geändert werden kann, muss beim Erstellen des Abonnements die **update_mode** -Eigenschaft auf **failover** (ermöglicht das Umschalten vom sofortigen Update auf das verzögerte Update) oder auf **queued failover** (ermöglicht das Umschalten vom verzögerten Update auf das sofortige Update) festgelegt werden. Diese Eigenschaften werden im Assistenten für neue Abonnements automatisch festgelegt.  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a>So legen Sie den Update für ein Pushabonnement fest  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Abonnenten her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Abonnements** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das Abonnement, für das Sie den Updatemodus festlegen möchten, und klicken Sie dann auf **Updatemethode festlegen**.  
  
4.  Wählen Sie im Dialogfeld **Updatemethode festlegen - \<Subscriber>: \<SubscriptionDatabase>** die Option **Sofortiges Aktualisieren** oder **Verzögertes Aktualisieren über eine Warteschlange** aus.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a>So legen Sie den Updatemodus für ein Pullabonnement fest  
  
1.  Wählen Sie im Dialogfeld **Abonnementeigenschaften - \<Publisher>: \<PublicationDatabase>** für die Option **Updatemethode für Abonnent** den Wert **Änderungen sofort replizieren** oder **Änderungen in Warteschlange einreihen** aus.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 Weitere Informationen zum Zugreifen auf das Dialogfeld **Abonnementeigenschaften - \<Publisher>: \<PublicationDatabase>** finden Sie unter [Anzeigen und Ändern der Eigenschaften von Pullabonnements](../view-and-modify-pull-subscription-properties.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-switch-between-update-modes"></a>So wechseln Sie den Updatemodus  
  
1.  Stellen Sie sicher, dass die Veröffentlichung das Failover unterstützt, indem Sie bei Pullabonnements [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) und bei Pushabonnements [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) ausführen. Wenn der Wert des **Updatemodus** im Resultset **3** oder **4**ist, wird das Failover unterstützt.  
  
2.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql)aus. Geben Sie **@publisher** , **@publisher_db** , **@publication** und einen der folgenden Werte für an **@failover_mode** :  
  
    -   **queued** - Failover zum verzögerten Aktualisieren, wenn die Verbindung vorübergehend unterbrochen wurde.  
  
    -   **immediate** - Failover zum sofortigen Aktualisieren, wenn die Verbindung wiederhergestellt wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
