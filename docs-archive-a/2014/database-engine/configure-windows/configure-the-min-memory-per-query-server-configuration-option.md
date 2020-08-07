---
title: Konfigurieren des min. Arbeitsspeichers pro Abfrage (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 56d85f36840f0900c8b5e986334a99ba610d3930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619337"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Min. Arbeitsspeicher pro Abfrage
  In diesem Thema wird beschrieben, wie die `min memory per query` Server Konfigurationsoption in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von oder konfiguriert wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] . Die `min memory per query` Option gibt die minimale Arbeitsspeicher Menge (in Kilobytes) an, die für die Ausführung einer Abfrage zugeordnet wird. Wenn z. b. `min memory per query` auf 2.048 KB festgelegt ist, wird sichergestellt, dass die Abfrage mindestens den gesamten Arbeitsspeicher erhält. Der Standardwert ist 1.024 KB. 512 KB ist der Minimalwert, und 2.147.483.647 KB (2 GB) ist der Maximalwert.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Min. Arbeitsspeicher pro Abfrage mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Min. Arbeitsspeicher pro Abfrage“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Der minimale Arbeitsspeicher pro Abfrage hat Vorrang vor der [Option Speicher für Indexerstellung](configure-the-index-create-memory-server-configuration-option.md). Wenn Sie beide Optionen ändern und der Wert von „index create memory“ (Speicher für Indexerstellung) den Wert von „min memory per query“ (Min. Arbeitsspeicher pro Abfrage) unterschreitet, werden die Werte zwar festgelegt, es wird jedoch eine Warnmeldung ausgegeben. Beim Ausführen der Abfrage wird eine ähnliche Warnung ausgegeben.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Der Abfrageprozessor von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht, den optimalen Umfang an Speicher zu bestimmen, der von einer Abfrage belegt werden soll. Mit der Option Min. Arbeitsspeicher pro Abfrage kann der Administrator den Umfang an Speicher angeben, der für eine einzelne Abfrage mindestens zur Verfügung gestellt wird. Abfragen erhalten im Allgemeinen mehr Speicher als hier angegeben, wenn Hash- und Sortiervorgänge für umfangreiche Datenmengen ausgeführt werden. Durch die Erhöhung des Werts für Min. Arbeitsspeicher pro Abfrage kann es bei einigen Abfragen mit geringem bis mittlerem Umfang zur Leistungssteigerung, jedoch auch zu stärkerem Wettbewerb um Speicherressourcen kommen. Die Option „Min. Arbeitsspeicher pro Abfrage“ schließt den für die Sortierung zugeordneten Arbeitsspeicher ein.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>So konfigurieren Sie die Option Min. Arbeitsspeicher pro Abfrage  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Speicher** -Knoten.  
  
3.  Geben Sie in das Feld **Minimaler Arbeitsspeicher pro Abfrage** die Mindestmenge an Arbeitsspeicher (in KB) ein, die für das Ausführen einer Abfrage zugeordnet wird.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>So konfigurieren Sie die Option Min. Arbeitsspeicher pro Abfrage  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `min memory per query` auf `3500` KB festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Min. Arbeitsspeicher pro Abfrage“  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Konfigurieren der Serverkonfigurationsoption Speicher für Indexerstellung](configure-the-index-create-memory-server-configuration-option.md)  
  
  
