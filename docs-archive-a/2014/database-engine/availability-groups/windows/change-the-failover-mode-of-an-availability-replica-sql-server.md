---
title: Ändern des Failovermodus eines Verfügbarkeitsreplikats (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724998"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a>Ändern des Failovermodus eines Verfügbarkeitsreplikats (SQL Server)
  In diesem Thema wird beschrieben, wie der Failovermodus eines Verfügbarkeitsreplikats in einer AlwaysOn-Verfügbarkeitsgruppe in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]oder PowerShell geändert wird. Der Failovermodus ist eine Replikateigenschaft, die den Failovermodus für Replikate bestimmt, die im Verfügbarkeitsmodus mit synchronem Commit ausgeführt werden. Weitere Informationen finden Sie unter [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md) und [Verfügbarkeitsmodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](availability-modes-always-on-availability-groups.md).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> Voraussetzungen und Einschränkungen  
  
-   Dieser Task wird nur für primäre Replikate unterstützt. Sie müssen mit der Serverinstanz verbunden sein, die das primäre Replikat hostet.  
  
-   SQL Server-Failoverclusterinstanzen (FCIs) unterstützen kein automatisches Failover durch Verfügbarkeitsgruppen. Daher können die Verfügbarkeitsreplikate, die von einer FCI gehostet werden, nur für manuelles Failover konfiguriert werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So ändern Sie den Failovermodus eines Verfügbarkeitsreplikats**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Serverinstanz her, die das primäre Verfügbarkeitsreplikat hostet, und erweitern Sie die Serverstruktur.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
3.  Klicken Sie auf die Verfügbarkeitsgruppe, deren Replikat geändert werden soll.  
  
4.  Klicken Sie mit der rechten Maustaste auf das Replikat, und klicken Sie auf **Eigenschaften**.  
  
5.  Verwenden Sie im Dialogfeld **Eigenschaften des Verfügbarkeitsreplikats** die Dropdownliste **Failovermodus** , um den Failovermodus für dieses Replikat zu ändern.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie den Failovermodus eines Verfügbarkeitsreplikats**  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Verwenden Sie die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) -Anweisung wie folgt:  
  
     ALTER AVAILABILITY GROUP *Gruppenname* MODIFY REPLICA ON '*Servername*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     }  )  
  
     Hierbei gilt:  
  
    -   *Gruppenname* ist der Name der Verfügbarkeitsgruppe.  
  
    -   { '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }  
  
         Gibt die Adresse der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die das Verfügbarkeitsreplikat hostet, das geändert werden soll. Diese Adresse weist die folgenden Komponenten auf:  
  
         *system_name*  
         Ist der NetBIOS-Name des Computersystems, auf dem sich eine eigenständige Serverinstanz befindet.  
  
         *FCI_network_name*  
         Ist der Netzwerkname, der verwendet wird, um auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster zuzugreifen, in dem eine Zielserverinstanz ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverpartner (eine FCI) ist.  
  
         *instance_name*  
         Ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die das Zielverfügbarkeitsreplikat hostet. Bei einer Standardserverinstanz ist *instance_name* optional.  
  
     Weitere Informationen zu diesen Parametern finden Sie unter [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).  
  
     Im folgenden Beispiel, eingegeben im primären Replikat der *MyAG* -Verfügbarkeitsgruppe, wird der Failovermodus für das Verfügbarkeitsreplikat, das sich auf der Standardserverinstanz auf dem Computer *COMPUTER01*befindet, in automatisches Failover geändert.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Verwenden von PowerShell  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a>So ändern Sie den Failovermodus eines Verfügbarkeitsreplikats
  
1.  Ändern Sie das Verzeichnis (`cd`) zur Serverinstanz, die das primäre Replikat hostet.  
  
2.  Verwenden Sie das `Set-SqlAvailabilityReplica`-Cmdlet mit dem `FailoverMode`-Parameter. Wenn Sie ein Replikat auf automatisches Failover festlegen, müssen Sie möglicherweise den `AvailabilityMode`-Parameter verwenden, um das Replikat in den Verfügbarkeitsmodus mit synchronem Commit zu ändern.  
  
     Beispielsweise wird durch diesen Befehl das Replikat `MyReplica` in der Verfügbarkeitsgruppe `MyAg` so geändert, dass der Verfügbarkeitsmodus für synchrone Commits verwendet und automatische Failover unterstützt werden.  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
Informationen zum Einrichten und Verwenden des SQL Server PowerShell Anbieters finden Sie unter [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
 [Verfügbarkeits Modi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](availability-modes-always-on-availability-groups.md)   
 [Failover-und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md) 
