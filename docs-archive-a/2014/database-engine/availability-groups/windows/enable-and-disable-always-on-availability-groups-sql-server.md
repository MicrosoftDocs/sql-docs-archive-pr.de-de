---
title: Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609454"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a>Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] muss aktiviert werden, damit eine Serverinstanz Verfügbarkeitsgruppen verwenden kann. Bevor Sie eine beliebige Verfügbarkeitsgruppe erstellen und konfigurieren können, muss die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] für jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aktiviert worden sein, auf der ein Verfügbarkeitsreplikat für mindestens eine Verfügbarkeitsgruppe gehostet wird.  
  
> [!IMPORTANT]  
>  Wenn Sie einen WSFC-Cluster löschen und neu erstellen, müssen Sie die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] für jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deaktivieren und erneut aktivieren, auf der auf dem ursprünglichen WSFC-Cluster ein Verfügbarkeitsreplikat gehostet wurde.  
  
-   **Vorbereitungen:**  
  
     [Voraussetzungen](#Prerequisites)  
  
     [Security](#Security)  
  
-   **So wird es gemacht:**  
  
    -   [Bestimmen, ob AlwaysOn-Verfügbarkeitsgruppen aktiviert sind](#IsEnabled)  
  
    -   [Aktivieren von AlwaysOn-Verfügbarkeitsgruppen](#EnableAOAG)  
  
    -   [AlwaysOn-Verfügbarkeitsgruppen deaktivieren](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a>Voraussetzungen für das Aktivieren von AlwaysOn-Verfügbarkeitsgruppen  
  
-   Die Serverinstanz muss sich auf einem WSFC-Knoten (Windows Server Failover Clustering) befinden.  
  
-   Auf der Serverinstanz muss eine Edition von SQL Server ausgeführt werden, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]unterstützt. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   AlwaysOn-Verfügbarkeitsgruppen sollten jeweils nur für eine Serverinstanz aktiviert werden. Warten Sie nach der Aktivierung von AlwaysOn-Verfügbarkeitsgruppen, bis der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst neu gestartet wurde, bevor Sie mit einer anderen Serverinstanz fortfahren.  
  
 Weitere Informationen zu den zusätzlichen Voraussetzungen für das Erstellen und Konfigurieren von Verfügbarkeits Gruppen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Während AlwaysOn-Verfügbarkeitsgruppen auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]aktiviert sind, verfügt die Serverinstanz über Vollzugriff auf den WSFC-Cluster.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert auf dem lokalen Computer die Mitgliedschaft in der Gruppe **Administrator** und Vollzugriff auf den WSFC-Cluster. Wenn Sie AlwaysOn mit PowerShell aktivieren, öffnen Sie das Eingabeaufforderungsfenster unter Verwendung der Option **Als Administrator ausführen** .  
  
 Erfordert, dass von Active Directory Objekte erstellt und Objektberechtigungen verwaltet werden.  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a>Bestimmen, ob AlwaysOn-Verfügbarkeitsgruppen aktiviert ist  
  
-   [SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> Verwenden von SQL Server Management Studio  
 **So bestimmen Sie, ob AlwaysOn-Verfügbarkeitsgruppen aktiviert sind**  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Serverinstanz, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Servereigenschaften** auf die Seite **Allgemein** . Die Eigenschaft **Ist HADR-aktiviert** zeigt einen der folgenden Werte an:  
  
    -   **True**, wenn AlwaysOn-Verfügbarkeitsgruppen aktiviert sind.  
  
    -   **False**, wenn AlwaysOn-Verfügbarkeitsgruppen deaktiviert sind.  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> Verwenden von Transact-SQL  
 **So bestimmen Sie, ob AlwaysOn-Verfügbarkeitsgruppen aktiviert sind**  
  
1.  Verwenden Sie die folgende [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) -Anweisung:  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     Die Einstellung der Servereigenschaft `IsHadrEnabled` gibt folgendermaßen an, ob eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für AlwaysOn-Verfügbarkeitsgruppen aktiviert wird:  
  
    -   Falls `IsHadrEnabled` = 1, sind AlwaysOn-Verfügbarkeitsgruppen aktiviert.  
  
    -   Wenn `IsHadrEnabled` gleich 0 ist, sind AlwaysOn-Verfügbarkeitsgruppen deaktiviert.  
  
    > [!NOTE]  
    >  Weitere Informationen zur `IsHadrEnabled` Server Eigenschaft finden Sie unter [SERVERPROPERTY &#40;Transact-SQL-&#41;](/sql/t-sql/functions/serverproperty-transact-sql).  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> Verwenden von PowerShell  
 **So bestimmen Sie, ob AlwaysOn-Verfügbarkeitsgruppen aktiviert sind**  
  
1.  Legen Sie Default ( `cd` ) auf die Serverinstanz fest (z. b. `\SQL\NODE1\DEFAULT` ), auf der Sie bestimmen möchten, ob [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aktiviert ist.  
  
2.  Geben Sie den folgenden PowerShell-`Get-Item`-Befehl ein:  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a> AlwaysOn-Verfügbarkeitsgruppen aktivieren  
 **Aktivieren von AlwaysOn mit:**  
  
-   [SQL Server-Konfigurations-Manager](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
 **So aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen**  
  
1.  Stellen Sie eine Verbindung mit dem Windows Server Failover Clustering (WSFC)-Knoten her, auf dem die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz gehostet wird, auf der Sie AlwaysOn-Verfügbarkeitsgruppen aktivieren möchten.  
  
2.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server Konfigurations-Manager**.  
  
3.  Klicken Sie in **SQL Server-Konfigurations-Manager**auf **SQL Server Dienste**, klicken Sie mit der rechten Maustaste auf SQL Server (** < *`instance name`*>)**, wobei **<*`instance name`*>** der Name einer lokalen Server Instanz ist, für die Sie AlwaysOn-Verfügbarkeitsgruppen aktivieren möchten, und klicken Sie auf **Eigenschaften.**  
  
4.  Wählen Sie die Registerkarte **Hohe Verfügbarkeit (immer aktiviert)** aus.  
  
5.  Überprüfen Sie, ob das Feld **Name des Windows-Failoverclusters** den Namen des lokalen Failoverclusters enthält. Wenn dieses Feld leer ist, wird [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]von dieser Serverinstanz derzeit nicht unterstützt. Der lokale Computer ist kein Clusterknoten, der WSFC-Cluster wurde geschlossen oder diese Edition von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]nicht.  
  
6.  Aktivieren Sie das Kontrollkästchen **AlwaysOn-Verfügbarkeitsgruppen aktivieren** , und klicken Sie auf **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfigurations-Manager speichert die Änderung. Dann müssen Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst manuell neu starten. Dies ermöglicht die Auswahl einer für die Geschäftsanforderungen optimalen Neustartzeit. Wenn der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst neu gestartet wird, wird AlwaysOn aktiviert, und die Servereigenschaft `IsHadrEnabled` wird auf 1 festgelegt.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> SQL Server PowerShell  
 **So aktivieren Sie AlwaysOn**  
  
1.  Ändern Sie das Verzeichnis (`cd`) zu einer Serverinstanz, die Sie für AlwaysOn-Verfügbarkeitsgruppen aktivieren möchten.  
  
2.  Verwenden Sie das `Enable-SqlAlwaysOn`-Cmdlet, um AlwaysOn-Verfügbarkeitsgruppen zu aktivieren.  
  
     Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
    > [!NOTE]  
    >  Informationen dazu, wie Sie steuern `Enable-SqlAlwaysOn` können, ob das Cmdlet den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst neu startet, finden Sie unter Wann startet [ein Cmdlet den SQL Server-Dienst neu?](#WhenCmdletRestartsSQL)weiter unten in diesem Thema.  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> Beispiel: Enable-SqlAlwaysOn  
 Durch den folgenden PowerShell-Befehl wird [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf einer Instanz von SQL Server (*Computer*\\*Instanz*) aktiviert.  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a>Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen  
  
-   **Vor dem Deaktivieren von AlwaysOn:**  
  
     [Empfehlungen](#Recommendations)  
  
-   **Deaktivieren von AlwaysOn mit:**  
  
    -   [SQL Server-Konfigurations-Manager](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **Nachverfolgung:**  [Nach dem Deaktivieren von AlwaysOn](#FollowUp)  
  
> [!IMPORTANT]  
>  Deaktivieren Sie AlwaysOn auf jeweils nur einer Serverinstanz. Warten Sie nach der Deaktivierung von AlwaysOn-Verfügbarkeitsgruppen, bis der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst neu gestartet wurde, bevor Sie mit einer anderen Serverinstanz fortfahren.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
 Bevor Sie AlwaysOn auf einer Serverinstanz deaktivieren, sollten Sie wie folgt vorgehen:  
  
1.  Wenn das primäre Replikat einer Verfügbarkeitsgruppe, die beibehalten werden soll, derzeit auf einer Serverinstanz gehostet wird, sollten Sie nach Möglichkeit manuell ein Failover für die Verfügbarkeitsgruppe zum synchronisierten sekundären Replikat ausführen. Weitere Informationen finden Sie unter [Ausführen eines geplanten manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
2.  Entfernen Sie alle lokalen sekundären Replikate. Weitere Informationen finden Sie unter [Entfernen eines sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
 **So deaktivieren Sie AlwaysOn**  
  
1.  Stellen Sie eine Verbindung mit dem Windows Server Failover Clustering (WSFC)-Knoten her, auf dem die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz gehostet wird, auf der Sie AlwaysOn-Verfügbarkeitsgruppen deaktivieren möchten.  
  
2.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
3.  Klicken Sie in **SQL Server-Konfigurations-Manager**auf **SQL Server Dienste**, klicken Sie mit der rechten Maustaste auf SQL Server (** < *`instance name`*>)**, wobei **<*`instance name`*>** der Name einer lokalen Server Instanz ist, für die Sie AlwaysOn-Verfügbarkeitsgruppen deaktivieren möchten, und klicken Sie auf **Eigenschaften**.  
  
4.  Deaktivieren Sie auf der Registerkarte**AlwaysOn hohe Verfügbarkeit**das Kontrollkästchen **AlwaysOn-Verfügbarkeitsgruppen aktivieren** , und klicken Sie auf **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfigurations-Manager speichert die Änderung und startet den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst neu. Beim Neustart des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Diensts wird AlwaysOn deaktiviert. Zudem wird die Servereigenschaft `IsHadrEnabled` auf 0 festgelegt, um anzugeben, dass AlwaysOn-Verfügbarkeitsgruppen deaktiviert werden.  
  
5.  Es empfiehlt sich, dass Sie die Informationen unter [Nachverfolgung: Nach dem Deaktivieren von AlwaysOn](#FollowUp)später in diesem Thema lesen.  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> SQL Server PowerShell  
 **So deaktivieren Sie AlwaysOn**  
  
1.  Wechseln `cd` Sie in das Verzeichnis () zu einer derzeit aktivierten Serverinstanz, die Sie für AlwaysOn-Verfügbarkeitsgruppen deaktivieren möchten.  
  
2.  Verwenden Sie das `Disable-SqlAlwaysOn`-Cmdlet, um AlwaysOn-Verfügbarkeitsgruppen zu aktivieren.  
  
     Mit dem folgenden Befehl werden z. b. AlwaysOn-Verfügbarkeitsgruppen auf einer Instanz von SQL Server (*Computer* \\ *Instanz*) deaktiviert.  Dieser Befehl erfordert einen Neustart der Instanz, und Sie werden aufgefordert, diesen Neustart zu bestätigen.  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  Informationen dazu, wie Sie steuern `Disable-SqlAlwaysOn` können, ob das Cmdlet den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst neu startet, finden Sie unter Wann startet [ein Cmdlet den SQL Server-Dienst neu?](#WhenCmdletRestartsSQL)weiter unten in diesem Thema.  
  
     Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a>Nachverfolgung: nach dem Deaktivieren von AlwaysOn  
 Nachdem Sie AlwaysOn-Verfügbarkeitsgruppen deaktiviert haben, muss die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu gestartet werden. Die Serverinstanz wird vom SQL-Konfigurations-Manager automatisch neu gestartet. Wenn Sie jedoch das `Disable-SqlAlwaysOn`-Cmdlet verwendet haben, müssen Sie die Serverinstanz manuell neu starten. Weitere Informationen finden Sie unter [sqlservr Application](../../../tools/sqlservr-application.md).  
  
 Auf der neu gestarteten Serverinstanz:  
  
-   Verfügbarkeitsdatenbanken werden bei SQL Server-Start nicht gestartet. Daher kann nicht auf sie zugegriffen werden.  
  
-   Die einzige unterstützte AlwaysOn- [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung ist [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql). Die Optionen CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP und SET HADR von ALTER DATABASE werden nicht unterstützt.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Metadaten und [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Konfigurationsdaten in WSFC sind von der Deaktivierung der AlwaysOn-Verfügbarkeitsgruppen nicht betroffen.  
  
 Wenn Sie AlwaysOn-Verfügbarkeitsgruppen dauerhaft auf jeder Serverinstanz deaktivieren, die ein Verfügbarkeitsreplikat für eine oder mehrere Verfügbarkeitsgruppen hostet, empfiehlt es sich, dass Sie die folgenden Schritte ausführen:  
  
1.  Wenn Sie die lokalen Verfügbarkeitsreplikate nicht vor dem Deaktivieren von AlwaysOn entfernt haben, löschen Sie jede Verfügbarkeitsgruppe, für die die Serverinstanz ein Verfügbarkeitsreplikat hostet. Informationen zum Löschen einer Verfügbarkeitsgruppe finden Sie unter [Entfernen einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).  
  
2.  Um die zurückgelassenen Metadaten zu entfernen, löschen Sie jede betroffene Verfügbarkeitsgruppe auf einer Serverinstanz, die Teil des ursprünglichen WSFC-Clusters ist.  
  
3.  Auf die primären Datenbanken kann weiterhin anhand aller Verbindungen außer der Datensynchronisierung zwischen der primären und der sekundären Datenbank zugegriffen werden.  
  
4.  Die sekundären Datenbanken übernehmen den Status RESTORING. Sie können sie entweder löschen oder sie mit RESTORE WITH RECOVERY wiederherstellen. Wiederhergestellte Datenbanken nehmen jedoch nicht mehr an der Datensynchronisierung für Verfügbarkeitsgruppen teil.  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> Wann startet ein Cmdlet den SQL Server-Dienst neu?  
 Auf einer gerade ausgeführten Serverinstanz kann die Verwendung von `Enable-SqlAlwaysOn` oder `Disable-SqlAlwaysOn` zum Ändern der aktuellen AlwaysOn-Einstellung zu einem Neustart des SQL Server-Diensts führen. Das Neustartverhalten hängt von den folgenden Bedingungen ab:  
  
|-NoServiceRestart-Parameter angegeben|-Force-Parameter angegeben|Wurde der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst neu gestartet?|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|Nein|Nein|Standardmäßig. Aber das Cmdlet fordert Sie folgendermaßen auf:<br /><br /> **Um diese Aktion abzuschließen, müssen wir den SQL Server-Dienst für die Serverinstanz "<instance_name>" neu starten. Möchten Sie den Vorgang fortsetzen?**<br /><br /> **[Y] Ja  [N] Nein  [S] Anhalten  [?] Hilfe (Standard ist „Y"):**<br /><br /> Wenn Sie **N** oder **S**angeben, wird der Dienst nicht neu gestartet.|  
|Nein|Ja|Der Dienst wird neu gestartet.|  
|Ja|Nein|Der Dienst wird nicht neu gestartet.|  
|Ja|Ja|Der Dienst wird nicht neu gestartet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)  
