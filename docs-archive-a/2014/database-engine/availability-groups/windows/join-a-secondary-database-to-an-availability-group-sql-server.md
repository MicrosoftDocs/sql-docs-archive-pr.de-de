---
title: Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617268"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe (SQL Server)
  In diesem Thema wird beschrieben, wie eine sekundäre Datenbank in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]oder PowerShell mit einer AlwaysOn-Verfügbarkeitsgruppe verknüpft wird. Nachdem Sie eine sekundäre Datenbank auf ein sekundäres Replikat vorbereitet haben, müssen Sie die Datenbank so schnell wie möglich mit der Verfügbarkeitsgruppe verknüpfen. So wird die Datenverschiebung aus der entsprechenden primären Datenbank in die sekundäre Datenbank gestartet.  
  
-   **Vorbereitungen:**  
  
     [Voraussetzungen](#Prerequisites)  
  
     [Security](#Security)  
  
-   **So bereiten Sie eine sekundäre Datenbank vor mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  Informationen dazu, was geschieht, nachdem eine sekundäre Datenbank der Gruppe angehört, finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Sie müssen mit der Serverinstanz verbunden sein, auf der das sekundäre Replikat gehostet wird.  
  
-   Das sekundäre Replikat muss bereits mit der Verfügbarkeitsgruppe verknüpft sein. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)mit einer Always On-Verfügbarkeitsgruppe verknüpft wird.  
  
-   Die sekundäre Datenbank muss vor kurzem vorbereitet worden sein. Weitere Informationen finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)erstellt und konfiguriert wird.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So verknüpfen Sie eine sekundäre Datenbank mit einer Verfügbarkeitsgruppe**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das sekundäre Replikat hostet, und erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Erweitern Sie die Verfügbarkeitsgruppe, die Sie ändern möchten, und erweitern Sie den Knoten **Verfügbarkeitsdatenbanken** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die Datenbank, und klicken Sie auf **Verfügbarkeitsgruppe beitreten**.  
  
5.  Das Dialogfeld **Datenbanken mit Verfügbarkeitsgruppe verknüpfen** wird geöffnet. Überprüfen Sie den Namen der Verfügbarkeitsgruppe, der in der Titelleiste angezeigt wird, und den im Raster angezeigten Datenbanknamen bzw. andere Namen, und klicken Sie auf **OK**, oder klicken Sie auf **Abbrechen**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So verknüpfen Sie eine sekundäre Datenbank mit einer Verfügbarkeitsgruppe**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das sekundäre Replikat hostet.  
  
2.  Verwenden Sie die [SET HADR-Klausel der ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) -Anweisung wie folgt:  
  
     ALTER DATABASE *Datenbankname* SET HADR AVAILABILITY GROUP = *Gruppenname*,  
  
     dabei ist *Datenbankname* der Name einer hinzuzufügenden Datenbank und *Gruppenname* der Name der Verfügbarkeitsgruppe.  
  
     Im folgenden Beispiel wird die sekundäre Datenbank `Db1` mit dem lokalen sekundären Replikat der `MyAG`-Verfügbarkeitsgruppe verknüpft.  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  Unter [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) können Sie die Verwendung dieser [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung im Kontext sehen.  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Verwenden von PowerShell  
 **So verknüpfen Sie eine sekundäre Datenbank mit einer Verfügbarkeitsgruppe**  
  
1.  Ändern Sie das Verzeichnis (`cd`) in die Serverinstanz, die das sekundäre Replikat hostet.  
  
2.  Verwenden Sie das `Add-SqlAvailabilityDatabase`-Cmdlet, um eine oder mehrere sekundäre Datenbanken mit der Verfügbarkeitsgruppe zu verknüpfen.  
  
     Beispielsweise wird durch den folgenden Befehl die sekundäre Datenbank `Db1`mit der Verfügbarkeitsgruppe `MyAG` in einer der Serverinstanzen verknüpft, von denen ein sekundäres Replikat gehostet wird.  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfigurations &#40;SQL Server&#41;gelöscht](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
