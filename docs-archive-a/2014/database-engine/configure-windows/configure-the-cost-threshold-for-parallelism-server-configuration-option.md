---
title: Konfigurieren der Serverkonfigurationsoption „Kostenschwellenwert für Parallelität“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 675055a753e84ace3a4fcb44b41b8c914326c5c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609445"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Kostenschwellenwert für Parallelität
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Kostenschwellenwert für Parallelität** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mit der Option **Kostenschwellenwert für Parallelität** geben Sie den Schwellenwert an, bei dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parallele Pläne für Abfragen erstellt und ausführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt und führt einen parallelen Plan für eine Abfrage nur dann aus, wenn die geschätzten Kosten für das Ausführen eines seriellen Plans für dieselbe Abfrage höher liegen als der Wert, der in **Kostenschwellenwert für Parallelität**festgelegt wurde. Die Kosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen des seriellen Plans bei einer bestimmten Hardwarekonfiguration benötigt wird. Die Option **Kostenschwellenwert für Parallelität** kann auf einen beliebigen Wert zwischen 0 und 32767 festgelegt werden. Der Standardwert ist 5.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Kostenschwelle für Parallelität mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Kostenschwellenwert für Parallelität“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Die Kosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen des seriellen Plans bei einer bestimmten Hardwarekonfiguration benötigt wird. Legen Sie die Option **cost threshold for parallelism** nur auf SMP-Systemen (Symmetric Multiprocessor) fest.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ignoriert den Wert von **Kostenschwellenwert für Parallelität** unter den folgenden Bedingungen:  
  
    -   Ihr Computer verfügt nur über einen logischen Prozessor.  
  
    -   Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] steht wegen der Konfigurationsoption **Affinitätsmaske** nur ein logischer Prozessor zur Verfügung.  
  
    -   Die Option **Max. Grad an Parallelität** ist auf den Wert 1 festgelegt.  
  
 Ein logischer Prozessor ist die grundlegende Einheit von Prozessorhardware, die dem Betriebssystem ermöglicht, einen Task weiterzuleiten oder einen Threadkontext auszuführen. Jeder logische Prozessor kann an einem bestimmten Zeitpunkt nur einen Threadkontext ausführen. Der Prozessorkern ist die Schaltungstechnik, mit der Anweisungen decodiert und ausgeführt werden können. Ein Prozessorkern enthält möglicherweise einen oder mehrere logische Prozessoren. Die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage kann zum Abrufen von CPU-Informationen für das System verwendet werden.  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   In bestimmten Fällen kann ein paralleler Plan ausgewählt werden, obwohl der Kostenplan der Abfrage unter dem aktuellen Wert der Option **Kostenschwellenwert für Parallelität** liegt. Dieser Fall kann eintreten, wenn die Entscheidung zum Verwenden eines parallelen oder seriellen Plans auf einer Kostenabschätzung basiert, die vor dem Abschluss der vollständigen Optimierung zur Verfügung gestellt wurde.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>So konfigurieren Sie die Option Kostenschwelle für Parallelität  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Legen Sie unter **Parallelität**für die Option **CostThresholdForParallelism** den gewünschten Wert fest. Geben Sie einen Wert zwischen 0 und 32767 ein bzw. wählen Sie diesen aus.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>So konfigurieren Sie die Option Kostenschwelle für Parallelität  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `cost threshold for parallelism` auf `10`festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="follow-up-after-you-configure-the-cost-threshold-for-parallelism-option"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Kostenschwellenwert für Parallelität“  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Parallelindexvorgängen](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Abfragehinweise (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql)   
 [Affinitätsmaske (Serverkonfigurationsoption)](affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
