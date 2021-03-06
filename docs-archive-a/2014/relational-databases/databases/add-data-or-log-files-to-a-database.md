---
title: Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], files
- adding data files
- adding files
- adding log files
- file additions [SQL Server], steps
- files [SQL Server], adding
- data additions [SQL Server]
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: stevestein
ms.author: sstein
ms.openlocfilehash: f72e00f9dab422652237b4b85579c544d0cda9fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725918"
---
# <a name="add-data-or-log-files-to-a-database"></a>Hinzufügen von Daten- oder Protokolldateien zu einer Datenbank
  In diesem Thema wird beschrieben, wie Daten- oder Protokolldateien in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]einer Datenbank hinzugefügt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So fügen Sie einer Datenbank Daten- oder Protokolldateien hinzu mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie können keine Dateien hinzufügen oder entfernen, während eine BACKUP-Anweisung ausgeführt wird.  
  
-   Für jede Datenbank können maximal 32.767 Dateien und 32.767 Dateigruppen angegeben werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a>So fügen Sie einer Datenbank Daten- oder Protokolldateien hinzu  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, klicken Sie mit der rechten Maustaste auf die Datenbank, der die Dateien hinzugefügt werden sollen, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie im Dialogfeld **Datenbankeigenschaften** die Seite **Dateien** aus.  
  
4.  Zum Hinzufügen einer Daten- oder Transaktionsprotokolldatei klicken Sie auf **Hinzufügen**.  
  
5.  Geben Sie im Bereich **Datenbankdateien** einen logischen Namen für die Datei ein. Der Dateiname muss innerhalb der Datenbank eindeutig sein.  
  
6.  Wählen Sie den Dateityp aus: Daten- oder Protokolldatei.  
  
7.  Wählen Sie für eine Datendatei in der Liste die Dateigruppe aus, in die die Datei eingeschlossen werden soll, oder wählen Sie **\<new filegroup>** aus, um eine neue Dateigruppe zu erstellen. Transaktionsprotokolle können nicht in Dateigruppen platziert werden.  
  
8.  Geben Sie die Anfangsgröße der Datei an. Legen Sie die Datendatei so groß wie möglich aus. Orientieren Sie sich dabei an dem maximal zu erwartenden Umfang der Datei, die in der Datenbank gespeichert werden soll.  
  
9. Klicken Sie auf ( **…** ) in der Spalte **Automatische Vergrößerung**, um anzugeben, wie die Datei wachsen soll. Sie können zwischen folgenden Optionen wählen:  
  
    1.  Um ein Anwachsen der aktuell ausgewählten Datei zuzulassen, wenn mehr Datenspeicherplatz benötigt wird, aktivieren Sie das Kontrollkästchen **Automatische Vergrößerung aktivieren** , und wählen Sie dann eine der folgenden Optionen aus:  
  
    2.  Wählen Sie **In Megabyte** aus, um anzugeben, dass die Datei in festen Schritten größer werden soll, und geben Sie einen Wert an.  
  
    3.  Wählen Sie **In Prozent** aus, um anzugeben, dass die Datei um einen Prozentsatz der aktuellen Dateigröße größer werden soll, und geben Sie einen Wert an.  
  
10. Um die maximale Dateigröße anzugeben, aktivieren Sie eine der folgenden Optionen:  
  
    1.  Wählen Sie **Beschränkt vergrößerbar (MB)** aus, um die maximale Größe für die Datei anzugeben, und geben Sie einen Wert an.  
  
    2.  Um ein Anwachsen der Datei bei Bedarf zuzulassen, wählen Sie **Unbeschränkt vergrößerbar**aus.  
  
    3.  Um die Vergrößerung der Datei zu verhindern, deaktivieren Sie das Kontrollkästchen **Automatische Vergrößerung aktivieren** . Die Größe der Datei steigt dann nicht über den in der Spalte **Anfangsgröße (MB)** angegebenen Wert hinaus.  
  
    > [!NOTE]  
    >  Die maximale Dateigröße ergibt sich aus dem verfügbaren Speicherplatz und den von der verwendeten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festgelegten Lizenzierungslimits.  
  
11. Geben Sie den Pfad für den Dateispeicherort an. Der angegebene Pfad muss vorhanden sein, bevor die Datei hinzugefügt wird.  
  
    > [!NOTE]  
    >  Standardmäßig werden die Daten und Transaktionsprotokolle auf demselben Laufwerk und unter demselben Pfad gespeichert, um Systeme mit nur einem Datenträger zu berücksichtigen. Diese Variante kann jedoch für bestimmte Produktionsumgebungen nicht optimal sein. Weitere Informationen finden Sie unter [Datenbankdateien und Dateigruppen](database-files-and-filegroups.md).  
  
12. Klicken Sie auf **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-add-data-or-log-files-to-a-database"></a>So fügen Sie einer Datenbank Daten- oder Protokolldateien hinzu  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird eine Dateigruppe mit zwei Dateien einer Datenbank hinzugefügt. Im Beispiel wird die Dateigruppe `Test1FG1` in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank erstellt, und der Dateigruppe werden zwei 5-MB-Dateien hinzugefügt.  
  
 [!code-sql[DatabaseDDL#AlterDatabase2](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase2)]  
  
 Weitere Beispiele finden Sie unter [ALTER DATABASE-Optionen Datei und Dateigruppe &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Database Files and Filegroups](database-files-and-filegroups.md)   
 [Löschen von Daten- oder Protokolldateien aus einer Datenbank](delete-data-or-log-files-from-a-database.md)   
 [Erhöhen der Größe einer Datenbank](increase-the-size-of-a-database.md)  
  
  
