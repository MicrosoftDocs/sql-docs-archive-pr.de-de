---
title: Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615939"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a>Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen
  In diesem Thema wird beschrieben, wie die Latenzzeit gemessen wird und Verbindungen für Transaktionsreplikation in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit Replikationsmonitor, [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder Replikationsverwaltungsobjekten (RMO) überprüft werden. Die Transaktionsreplikation bietet die Überwachungstokenfunktion, die eine praktische Möglichkeit zum Messen der Latenzzeit bei Transaktionsreplikationstopologien und zur Überprüfung der Verbindungen zwischen dem Verleger, dem Verteiler und den Abonnenten darstellt. Ein Token (eine geringe Mange an Daten) wird in das Transaktionsprotokoll der Veröffentlichungsdatenbank geschrieben, wie eine normale replizierte Transaktion gekennzeichnet und über das System gesendet. Auf diese Weise werden die folgenden Berechnungen ermöglicht:  
  
-   Wie viel Zeit zwischen dem Commit einer Transaktion auf dem Verleger und dem Einfügen des zugehörigen Befehls in die Verteilungsdatenbank auf dem Verteiler verstreicht.  
  
-   Wie viel Zeit zwischen dem Einfügen eines Befehls in die Verteilungsdatenbank und dem zugehörigen Commit einer Transaktion auf dem Abonnenten verstreicht.  
  
 Mithilfe dieser Berechnungen können Sie verschiedene Fragen beantworten. Unter anderem diese:  
  
-   Welche Abonnenten benötigen am längsten, um eine Änderung vom Verleger zu empfangen?  
  
-   Welcher der Abonnenten, die Überwachungstoken empfangen sollten, hat keine empfangen?  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So messen Sie die Latenzzeit und überprüfen die Verbindungen mit:**  
  
     [SQL Server-Replikationsmonitor](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Überwachungstoken können sich auch als nützlich erweisen, wenn ein System in den Ruhezustand versetzt wird, da hierfür alle Aktivitäten beendet werden und überprüft wird, ob alle Knoten sämtliche ausstehenden Änderungen empfangen haben. Weitere Informationen finden Sie unter [Versetzen einer Replikationstopologie in einen inaktiven Status &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).  
  
 Zum Verwenden von Überwachungs Token müssen Sie bestimmte Versionen von verwenden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   Der Verteiler muss oder höher sein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] .  
  
-   Der Verleger muss [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher aufweisen, oder es muss sich um einen Oracle-Verleger handeln.  
  
-   Bei Pushabonnements werden Überwachungstokenstatistiken vom Verleger, vom Verteiler und von den Abonnenten gesammelt, wenn der Abonnent [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7,0 oder höher ist.  
  
-   Im Fall von Pullabonnements werden Überwachungstokenstatistiken von Abonnenten gesammelt, sofern der Abonnent [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher aufweist. Wenn der Abonnent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7,0 oder ist [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] , werden Statistiken nur vom Verleger und vom Verteiler gesammelt.  
  
 Es gibt eine Vielzahl anderer Probleme und Einschränkungen, auf die geachtet werden muss:  
  
-   Abonnements müssen aktiv sein, um ein Überwachungstoken zu empfangen. Ein Abonnement ist aktiv, wenn es initialisiert wurde.  
  
-   Durch die erneute Initialisierung werden sämtliche ausstehenden Überwachungstoken für die relevanten Abonnements entfernt.  
  
-   Abonnenten empfangen nur Überwachungstoken, die nach ihrer Erstsynchronisierung erstellt wurden.  
  
-   Überwachungstoken werden nicht von Abonnenten weitergeleitet, die Wiederveröffentlichungen ausführen.  
  
-   Der Replikationsmonitor kann den Namen der Veröffentlichungsinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach einem Failover zu einer sekundären Instanz nicht anpassen und zeigt weiterhin Replikationsinformationen unter dem Namen der ursprünglichen primären Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]an. Nach einem Failover kann kein Überwachungstoken mit dem Replikationsmonitor eingegeben werden, ein mit [!INCLUDE[tsql](../../../includes/tsql-md.md)]auf dem neuen Verleger eingegebenes Überwachungstoken wird jedoch im Replikationsmonitor angezeigt.  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a>Verwenden von SQL Server-Replikation Monitor  
 Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>So fügen Sie ein Überwachungstoken ein und zeigen Informationen zum Token an  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Überwachungstoken** .  
  
3.  Klicken Sie auf **Überwachung einfügen**.  
  
4.  In den folgenden Spalten sehen Sie die für das Überwachungstoken benötigte Zeit: **Verleger zu Verteiler**, **Verteiler zu Abonnent**, **Gesamtlatenzzeit**. Der Wert **Pending** gibt an, dass das Token einen bestimmten Punkt nicht erreicht hat.  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a>So zeigen Sie Informationen zu früher eingefügten Überwachungstoken an  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Überwachungstoken** .  
  
3.  Wählen Sie in der Dropdownliste **Einfügungszeitpunkt** eine Zeit aus.  
  
4.  In den folgenden Spalten sehen Sie die für das Überwachungstoken benötigte Zeit: **Verleger zu Verteiler**, **Verteiler zu Abonnent**, **Gesamtlatenzzeit**. Der Wert **Pending** gibt an, dass das Token einen bestimmten Punkt nicht erreicht hat.  
  
    > [!NOTE]  
    >  Die Informationen von Überwachungstoken werden für denselben Zeitraum wie andere Vergangenheitsdaten beibehalten. Der Zeitraum wird durch die Aufbewahrungsdauer für den Verlauf der Verteilungsdatenbank festgelegt. Weitere Informationen zum Ändern der Eigenschaften der Verteilungsdatenbank finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../view-and-modify-distributor-and-publisher-properties.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a>So stellen Sie ein Überwachungstoken für eine Transaktionsveröffentlichung bereit  
  
1.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) aus. Stellen Sie sicher, dass die Veröffentlichung vorhanden und der Status aktiv ist.  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) aus. Stellen Sie sicher, dass das Abonnement vorhanden und der Status aktiv ist.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql) aus und geben Sie **@publication** an. Notieren Sie den Wert des **@tracer_token_id** Output-Parameters.  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a>So können Sie die Latenzzeit bestimmen und die Verbindungen für eine Transaktionveröffentlichung überprüfen  
  
1.  Stellen Sie mithilfe der vorherigen Prozedur ein Überwachungstoken für die Veröffentlichung bereit.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)aus und geben Sie **@publication** an. Dadurch wird eine Liste aller für die Veröffentlichung bereitgestellten Überwachungstoken zurückgegeben. Beachten Sie die gewünschte **tracer_id** im Resultset.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql) aus, wobei Sie **@publication** und die Überwachungstoken-ID aus Schritt 2 für **@tracer_id** angeben. Dadurch werden Latenzzeitinformationen für das ausgewählte Überwachungstoken zurückgegeben.  
  
#### <a name="to-remove-tracer-tokens"></a>So entfernen Sie Überwachungstoken  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)aus und geben Sie **@publication** an. Dadurch wird eine Liste aller für die Veröffentlichung bereitgestellten Überwachungstoken zurückgegeben. Beachten Sie die **tracer_id** für das zu löschende Überwachungstoken im Resultset.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql) aus, wobei Sie **@publication** und die ID des zu löschenden Überwachungstokens aus Schritt 2 für **@tracer_id** angeben.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel wird ein Überwachungstoken-Datensatz bereitgestellt, und dann werden mithilfe der zurückgegebenen ID des bereitgestellten Überwachungstokens Latenzinformationen angezeigt.  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a>So stellen Sie ein Überwachungstoken für eine Transaktionsveröffentlichung bereit  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication>-Klasse.  
  
3.  Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> -Eigenschaft und die <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> -Eigenschaft für die Veröffentlichung fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 3 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> -Methode auf. Mit dieser Methode wird ein Überwachungstoken in das Transaktionsprotokoll der Veröffentlichung eingefügt.  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a>So können Sie die Latenzzeit bestimmen und die Verbindungen für eine Transaktionveröffentlichung überprüfen  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.PublicationMonitor>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>und <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder den in Schritt 3 genannten Eigenschaften der Klasse PublicationMonitor falsche Werte zugewiesen, oder die Veröffentlichung ist nicht vorhanden.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -Methode auf. Wandeln Sie das zurückgegebene <xref:System.Collections.ArrayList> -Objekt in ein Array von <xref:Microsoft.SqlServer.Replication.TracerToken> -Objekten um.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> -Methode auf. Übergeben Sie einen Wert <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> für ein Überwachungstoken aus Schritt 5. Dadurch werden Latenzzeitinformationen für das ausgewählte Überwachungstoken als <xref:System.Data.DataSet> -Objekt zurückgegeben. Wenn alle Informationen des Überwachungstokens zurückgegeben wurden, besteht die Verbindung zwischen dem Verleger und dem Verteiler sowie die Verbindung zwischen dem Verteiler und dem Abonnenten, und die Replikationstopologie ist funktionsfähig.  
  
#### <a name="to-remove-tracer-tokens"></a>So entfernen Sie Überwachungstoken  
  
1.  Erstellen Sie eine Verbindung mit dem Verteiler, indem Sie die <xref:Microsoft.SqlServer.Management.Common.ServerConnection> -Klasse verwenden.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.PublicationMonitor>-Klasse.  
  
3.  Legen Sie die Eigenschaften <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>und <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> fest, und legen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung fest.  
  
4.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> -Methode auf, um die Eigenschaften des Objekts abzurufen. Wenn diese Methode `false` zurückgibt, wurden entweder den in Schritt 3 genannten Eigenschaften der Klasse PublicationMonitor falsche Werte zugewiesen, oder die Veröffentlichung ist nicht vorhanden.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -Methode auf. Wandeln Sie das zurückgegebene <xref:System.Collections.ArrayList> -Objekt in ein Array von <xref:Microsoft.SqlServer.Replication.TracerToken> -Objekten um.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> -Methode auf. Übergeben Sie einen der folgenden Werte:  
  
    -   <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> für ein Überwachungstoken aus Schritt 5. Dadurch werden die Informationen für ein ausgewähltes Token gelöscht.  
  
    -   Ein <xref:System.DateTime>-Objekt. Dadurch werden die Informationen für alle Token gelöscht, die älter sind als das angegebene Datum und die angegebene Uhrzeit.  
  
###  <a name="PShellExample"></a>  
