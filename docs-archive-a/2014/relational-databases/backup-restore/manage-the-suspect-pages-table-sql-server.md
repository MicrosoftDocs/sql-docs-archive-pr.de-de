---
title: Verwalten der suspect_pages-Tabelle (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
- restoring pages [SQL Server]
- pages [SQL Server], suspect
- pages [SQL Server], restoring
- suspect_pages system table
- suspect pages [SQL Server]
- restoring [SQL Server], pages
ms.assetid: f394d4bc-1518-4e61-97fc-bf184d972e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dd7aea63ae85a16e23ff532c7e18ace3c376a707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622709"
---
# <a name="manage-the-suspect_pages-table-sql-server"></a>Verwalten der suspect_pages-Tabelle (SQL Server)
  In diesem Thema wird beschrieben, wie Sie die **suspect_pages** -Tabelle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]verwalten. Die **suspect_pages** -Tabelle, die zum Verwalten von Informationen über fehlerverdächtige Seiten verwendet wird, ist hilfreich für die Entscheidung, ob eine Wiederherstellung erforderlich ist. Die [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) -Tabelle befindet sich in der [msdb](../databases/msdb-database.md)-Datenbank.  
  
 Eine Seite wird als "fehlerverdächtig" betrachtet , wenn das [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] bei dem Versuch, eine Datenseite zu lesen, einen der folgenden Fehler findet:  
  
-   Ein [823-Fehler](../errors-events/mssqlserver-823-database-engine-error.md) , der durch eine vom Betriebssystem ausgegebene zyklische Redundanz Prüfung (CRC) verursacht wurde, z. b. ein Datenträger Fehler (bestimmte Hardwarefehler).  
  
-   [824-Fehler](../errors-events/mssqlserver-824-database-engine-error.md), z. b. eine zerrissene Seite (logischer Fehler)  
  
 Die Seiten-ID jeder fehlerverdächtigen Seite wird in der **suspect_pages** -Tabelle aufgezeichnet. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] zeichnet alle fehlerverdächtigen Seiten auf, die während der regulären Verarbeitung auftreten, z. B. bei folgenden Vorgängen:  
  
-   Eine Abfrage muss eine Seite lesen.  
  
-   Während eines DBCC CHECKDB-Vorgangs.  
  
-   Während eines Sicherungsvorgangs.  
  
 Die **suspect_pages** -Tabelle wird ggf. auch während eines Wiederherstellungsvorgangs, eines DBCC-Reparaturvorgangs oder eines Datenbanklöschvorgangs aktualisiert.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So verwalten Sie die "suspect_pages"-Tabelle mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   **In der suspect_pages-Tabelle aufgezeichnete Fehler**  
  
     Die **suspect_pages** -Tabelle enthält eine Zeile für jede Seite mit einem Fehler vom Typ 824 (maximal 1.000 Zeilen). Die folgenden Tabellen enthalten Fehler, die in der **event_type** -Spalte der **suspect_pages** -Tabelle protokolliert werden.  
  
    |Fehlerbeschreibung|**event_type** -Wert|  
    |-----------------------|---------------------------|  
    |Ein Fehler vom Typ 823, der durch einen vom Betriebssystem ausgegebenen CRC-Fehler verursacht wird, oder ein Fehler vom Typ 824, der außer einer fehlerhaften Prüfsumme oder einer zerrissenen Seite z. B. eine fehlerhafte Seiten-ID anzeigt.|1|  
    |Fehlerhafte Prüfsumme|2|  
    |Zerrissene Seite|3|  
    |Wiederhergestellt (die Seite wurde wiederhergestellt, nachdem sie als beschädigt markiert wurde)|4|  
    |Repariert (DBCC, AlwaysOn oder Datenbankspiegelung hat die Seite repariert)|5|  
    |Zuordnung durch DBCC aufgehoben|7|  
  
     In der **suspect_pages** -Tabelle werden auch vorübergehende Fehler aufgezeichnet. Ursachen für vorübergehende Fehler sind beispielsweise E/A-Fehler (z. B. eine fehlende Kabelverbindung) oder eine Seite, die einen wiederholten Prüfsummentest vorübergehend nicht besteht.  
  
-   **Vorgehensweise der Datenbank-Engine beim Aktualisieren der "suspect_pages"-Tabelle**  
  
     [!INCLUDE[ssDE](../../includes/ssde-md.md)] führt folgende Aktionen in der **suspect_pages** -Tabelle aus:  
  
    -   Wenn die Tabelle nicht voll ist, wird sie für jeden Fehler vom Typ 824 aktualisiert, um anzuzeigen, dass ein Fehler aufgetreten ist, und die Fehleranzahl wird erhöht. Wenn eine Seite einen Fehler aufweist, nachdem sie durch eine Reparatur, eine Wiederherstellung oder das Aufheben einer Zuordnung repariert wurde, wird die zugehörige **number_of_errors** -Fehleranzahl erhöht, und die zugehörige **last_update** -Spalte wird aktualisiert.  
  
    -   Nachdem eine aufgelistete Seite durch einen Wiederherstellungs- oder Reparaturvorgang repariert wurde, aktualisiert der Vorgang die **suspect_pages** -Zeile, um anzuzeigen, dass die Seite repariert (**event_type** = 5) oder wiederhergestellt (**event_type** = 4) wurde.  
  
    -   Wenn eine DBCC-Überprüfung ausgeführt wird, markiert die Überprüfung alle fehlerfreien Seiten als repariert (**event_type** = 5) oder als Seiten, deren Zuordnung aufgehoben wurde (**event_type** = 7).  
  
-   **Automatische Updates der "suspect_pages"-Tabelle**  
  
     Die **suspect_pages** -Tabelle wird von einem Datenbank-Spiegelungspartner oder AlwaysOn-Verfügbarkeitsreplikat aktualisiert, nachdem bei einem Versuch, eine Seite aus einer Datendatei zu lesen, aus einem der folgenden Gründe ein Fehler aufgetreten ist:  
  
    -   Fehler vom Typ 823, der von einem durch das Betriebssystem ausgegebenen CRC-Fehler verursacht wird.  
  
    -   Fehler vom Typ 824 (logische Beschädigung, z. B. eine zerrissene Seite).  
  
     Die folgenden Aktionen aktualisieren auch automatisch Zeilen in der **suspect_pages** -Tabelle.  
  
    -   DBCC CHECKDB REPAIR_ALLOW_DATA_LOSS aktualisiert die **suspect_pages** -Tabelle, um jede Seite anzugeben, deren Zuordnung aufgehoben wurde oder die repariert wurde.  
  
    -   Eine vollständige, Datei- oder Seitenwiederherstellung markiert die Seiteneinträge als wiederhergestellt.  
  
     Die folgenden Aktionen löschen automatisch Zeilen aus der **suspect_pages** -Tabelle.  
  
    -   ALTER DATABASE REMOVE FILE  
  
    -   DROP DATABASE  
  
-   **Verwaltungsrolle des Datenbankadministrators**  
  
     Datenbankadministratoren sind zuständig für das Verwalten der Tabelle, insbesondere indem sie alte Zeilen löschen. Die Größe der **suspect_pages** -Tabelle ist beschränkt, und wenn sie voll ist, werden keine neuen Fehler mehr protokolliert. Um zu verhindern, dass sich diese Tabelle füllt, muss der Datenbankadministrator oder Systemadministrator durch das Löschen von Zeilen die alten Einträge manuell aus der Tabelle löschen. Aus diesem Grund wird empfohlen, Zeilen mit einem wiederhergestellten oder reparierten **event_type** -Objekt oder Zeilen mit einem alten **last_update** -Wert regelmäßig zu löschen bzw. zu archivieren.  
  
     Sie können die [Database Suspect Data Page-Ereignsklasse](../event-classes/database-suspect-data-page-event-class.md)verwenden, um die Aktivität in der suspect_pages-Tabelle zu überwachen. Der **suspect_pages** -Tabelle werden aufgrund vorübergehender Fehler manchmal Zeilen hinzugefügt. Wenn der Tabelle viele Zeilen hinzugefügt werden, liegt möglicherweise bereits ein Fehler in Bezug auf das E/A-Subsystem vor. Wenn Sie feststellen, dass die Anzahl der Tabelle hinzugefügter Zeilen plötzlich ansteigt, sollten Sie die möglichen Ursachen hierfür in Ihrem E/A-Subsystem untersuchen.  
  
     Ein Datenbankadministrator kann auch Datensätze einfügen oder aktualisieren. Das Aktualisieren einer Zeile ist z. B. sinnvoll, wenn der Datenbankadministrator weiß, dass eine bestimmte fehlerverdächtige Seite tatsächlich intakt ist, den Datensatz jedoch für eine Weile erhalten möchte.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Jeder mit Zugriff auf **msdb** kann die Daten in der Tabelle **suspect_pages** lesen. Jeder mit UPDATE-Berechtigung für die suspect_pages-Tabelle kann ihre Datensätze aktualisieren. Mitglieder der festen Datenbankrolle **db_owner** auf **msdb** oder der festen Serverrolle **sysadmin** können Datensätze einfügen, aktualisieren und löschen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-manage-the-suspect_pages-table"></a>So verwalten Sie die "suspect_pages"-Tabelle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]her, erweitern Sie diese Instanz und dann **Datenbanken**.  
  
2.  Erweitern Sie **Systemdatenbanken**, **msdb**, **Tabellen**und anschließend **Systemtabellen**.  
  
3.  Erweitern Sie **dbo.suspect_pages** , und klicken Sie mit der rechten Maustaste auf **Die ersten 200 Zeilen bearbeiten**.  
  
4.  Bearbeiten, aktualisieren oder löschen Sie im Abfragefenster die gewünschten Zeilen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-manage-the-suspect_pages-table"></a>So verwalten Sie die "suspect_pages"-Tabelle  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie die folgenden Beispiele, fügen Sie sie in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel werden einige Zeilen aus der `suspect_pages` -Tabelle gelöscht.  
  
```  
-- Delete restored, repaired, or deallocated pages.  
DELETE FROM msdb..suspect_pages  
   WHERE (event_type = 4 OR event_type = 5 OR event_type = 7);  
GO  
  
```  
  
 In diesem Beispiel werden die ungültigen Seiten in der Tabelle `suspect_pages` zurückgegeben.  
  
```  
-- Select nonspecific 824, bad checksum, and torn page errors.  
SELECT * FROM msdb..suspect_pages  
   WHERE (event_type = 1 OR event_type = 2 OR event_type = 3);  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql)   
 [Wiederherstellung von Seiten &#40;SQL Server&#41;](restore-pages-sql-server.md)   
 [suspect_pages &#40;Transact-SQL-&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql)   
 [MSSQLSERVER_823](../errors-events/mssqlserver-823-database-engine-error.md)   
 [MSSQLSERVER_824](../errors-events/mssqlserver-824-database-engine-error.md)  
  
  
