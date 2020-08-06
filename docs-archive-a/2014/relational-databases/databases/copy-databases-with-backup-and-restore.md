---
title: Kopieren von Datenbanken durch Sichern und Wiederherstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], back up and restore
- restoring databases [SQL Server], previous SQL Server versions
- database restores [SQL Server], copying databases
- restoring databases [SQL Server], onto another server instance
- restoring [SQL Server], onto another server instance
- backing up databases [SQL Server], copying databases
- database backups [SQL Server], copying databases
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8ffed36767f961f7482aa0dccf755118c80c019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699764"
---
# <a name="copy-databases-with-backup-and-restore"></a>Kopieren von Datenbanken durch Sichern und Wiederherstellen
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]können Sie eine neue Datenbank erstellen, indem Sie die Sicherung einer Benutzerdatenbank wiederherstellen, die mithilfe von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version erstellt wurde. Sicherungen der **master**-, **model** - und **msdb** -Datenbank, die mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt wurden, können von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]nicht wiederhergestellt werden. Außerdem können [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Sicherungen nicht mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wiederhergestellt werden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet im Vergleich zu früheren Versionen einen anderen Standardpfad. Daher muss zur Wiederherstellung von Sicherungen einer Datenbank, die im Standardverzeichnis früherer Versionen erstellt wurden, die MOVE-Option verwendet werden. Informationen zum neuen Standardpfad finden Sie unter [Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md). Weitere Informationen zum Verschieben von Datenbankdateien finden Sie weiter unten in diesem Thema unter "Verschieben der Datenbankdateien".  
  
## <a name="general-steps-for-using-backup-and-restore-to-copy-a-database"></a>Allgemeine Schritte zum Verwenden der Sicherung und Wiederherstellung zum Kopieren einer Datenbank  
 Wenn Sie durch Sichern und Wiederherstellen eine Datenbank in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kopieren, kann es sich beim Quell- und Zielcomputer um eine beliebige Plattform handeln, auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 Dies sind die allgemeinen Schritte:  
  
1.  Sichern Sie die Quelldatenbank, die in einer Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher vorhanden sein kann. Der Computer, auf dem diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, ist der *Quellcomputer*.  
  
2.  Stellen Sie auf dem Computer, auf den Sie die Datenbank kopieren möchten (der *Zielcomputer*), eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, auf der Sie die Datenbank wiederherstellen möchten. Erstellen Sie bei Bedarf in der Zielserverinstanz dieselben Sicherungsmedien, die zum Sichern der Quelldatenbanken verwendet wurden.  
  
3.  Stellen Sie die Sicherung der Quelldatenbank auf dem Zielserver wieder her. Durch das Wiederherstellen der Datenbank werden automatisch alle Datenbankdateien erstellt.  
  
 In den folgenden Themen werden zusätzliche Überlegungen behandelt, die diesen Vorgang beeinflussen können.  
  
## <a name="before-you-restore-database-files"></a>Vor dem Wiederherstellen der Datenbankdateien  
 Beim Wiederherstellen einer Datenbank werden automatisch die Datenbankdateien erstellt, die für die wiederherzustellende Datenbank benötigt werden. Standardmäßig verwenden die während des Wiederherstellungsvorgangs von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellten Dateien dieselben Namen und Pfade wie die Sicherungsdateien aus der Originaldatenbank auf dem Quellcomputer.  
  
 Wenn Sie die Datenbank wiederherstellen, können Sie bei Bedarf die Gerätezuordnung, Dateinamen oder den Pfad für die wiederherzustellende Datenbank angeben (optional). Dies kann in den folgenden Situationen erforderlich sein:  
  
-   Die Verzeichnisstruktur oder Laufwerkzuordnung, die von der Datenbank auf dem ursprünglichen Computer verwendet wurde, ist auf dem anderen Computer nicht vorhanden. Vielleicht enthält die Sicherung zum Beispiel eine Datei, die standardmäßig auf Laufwerk E wiederhergestellt werden soll, doch auf dem Zielcomputer ist kein Laufwerk mit dem Buchstaben E vorhanden.  
  
-   Am Zielort ist möglicherweise nicht genügend Speicherplatz vorhanden.  
  
-   Sie verwenden erneut einen Datenbanknamen, der am Wiederherstellungsziel bereits vorhanden ist, und wenn eine der Dateien den gleichen Namen wie eine Datenbankdatei im Sicherungssatz erhält, bestehen folgende Möglichkeiten:  
  
    -   Wenn die vorhandene Datenbankdatei überschrieben werden kann, wird sie überschrieben (dies würde sich nicht auf eine Datei auswirken, die zu einem anderen Datenbanknamen gehört).  
  
    -   Wenn die vorhandene Datei nicht überschrieben werden kann, würde ein Wiederherstellungsfehler auftreten.  
  
 Um Fehler und unbeabsichtigte Folgen, vor dem Wiederherstellungsvorgang, zu vermeiden, können Sie anhand der [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) -Verlaufstabelle die Datenbank und die Protokolldateien in der Sicherung ermitteln, die Sie wiederherstellen möchten.  
  
## <a name="moving-the-database-files"></a>Verschieben der Datenbankdateien  
 Wenn die Dateien in der Datenbanksicherung aus den oben genannten Gründen nicht auf dem Zielcomputer wiederhergestellt werden können, ist es notwendig, die Dateien während des Wiederherstellens an einen neuen Standort zu verschieben. Beispiel:  
  
-   Sie möchten eine Datenbank aus Sicherungen wiederherstellen, die am Standardspeicherort der früheren Version erstellt wurden.  
  
-   Aus Kapazitätsgründen kann es notwendig sein, einige Datenbankdateien der Sicherung auf einem anderen Laufwerk wiederherzustellen. Dieser Fall kann häufiger eintreten, da die meisten Computer in einem Unternehmen nicht die gleiche Anzahl und Größe der Datenträgerlaufwerke oder identische Softwarekonfigurationen aufweisen.  
  
-   Für Testzwecke kann es notwendig sein, eine Kopie einer vorhandenen Datenbank auf demselben Computer zu erstellen. In diesem Fall sind die Datenbankdateien für die Originaldatenbank bereits vorhanden, deshalb müssen andere Dateinamen angegeben werden, wenn die Datenbankkopie während des Wiederherstellungsvorgangs erstellt wird.  
  
 Weitere Informationen finden Sie weiter unten in diesem Thema unter "So stellen Sie Dateien oder Dateigruppen an einem neuen Speicherort wieder her".  
  
## <a name="changing-the-database-name"></a>Ändern des Datenbanknamens  
 Der Name der Datenbank kann beim Wiederherstellen auf dem Zielcomputer geändert werden, ohne zuerst die Datenbank erstellen zu müssen und dann anschließend den Namen manuell zu ändern. So kann es sich beispielsweise als notwendig erweisen, den Datenbanknamen von **Sales** in **SalesCopy** zu ändern, um anzuzeigen, dass es sich um die Kopie einer Datenbank handelt.  
  
 Der explizit beim Wiederherstellen einer Datenbank bereitgestellte Name wird automatisch als neuer Datenbankname verwendet. Da der Datenbankname noch nicht vorhanden ist, wird ein neuer Name mithilfe der Dateien in der Sicherung erstellt.  
  
## <a name="when-upgrading-a-database-by-using-restore"></a>Beim Aktualisieren einer Datenbank mit Wiederherstellen  
 Beim Wiederherstellen von Sicherungen einer früheren Version ist es hilfreich, vorher zu wissen, ob der Pfad (Laufwerk und Verzeichnis) jedes Volltextkatalogs in einer Sicherung auf dem Zielcomputer vorhanden ist. Zum Auflisten der logischen und physischen Namen (Pfad und Dateiname) jeder Datei in einer Sicherung, einschließlich der Katalogdateien, verwenden Sie eine RESTORE FILELISTONLY FROM *<Sicherungsmedium>* -Anweisung. Weitere Informationen finden Sie unter [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).  
  
 Falls auf dem Zielcomputer nicht der gleiche Pfad vorhanden ist, haben Sie zwei Möglichkeiten:  
  
-   Erstellen Sie die entsprechende Laufwerk/Verzeichnis-Zuordnung auf dem Zielcomputer.  
  
-   Verschieben Sie die Katalogdateien während des Wiederherstellungsvorgangs an einen neuen Speicherort, indem Sie die WITH MOVE-Klausel in der RESTORE DATABASE-Anweisung verwenden. Weitere Informationen finden Sie unter [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)nicht wiederhergestellt werden.  
  
 Informationen zu Alternativen zum Upgrade von Volltextindizes finden Sie unter [Upgrade der Volltextsuche](../search/upgrade-full-text-search.md).  
  
## <a name="database-ownership"></a>Datenbankbesitz  
 Wenn eine Datenbank auf einem anderen Computer wiederhergestellt wird, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename oder der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzer, der den Wiederherstellungsvorgang initiiert, automatisch zum Besitzer der neuen Datenbank. Nach dem Wiederherstellen der Datenbank kann der Systemadministrator oder der neue Datenbankbesitzer den Datenbankbesitz ändern. Verwenden Sie Kennwörter für Medien- oder Sicherungssätze, um das unbefugte Wiederherstellen einer Datenbank zu verhindern.  
  
## <a name="managing-metadata-when-restoring-to-another-server-instance"></a>Verwalten von Metadaten beim Wiederherstellen auf einer anderen Serverinstanz  
 Wenn Sie eine Datenbank auf einer anderen Serverinstanz wiederherstellen, müssen Sie möglicherweise einige oder alle Metadaten, wie Anmeldenamen und Aufträge, für die Datenbank auf der anderen Serverinstanz erneut erstellen, um für Konsistenz für Benutzer und Anwendungen zu sorgen. Weitere Informationen finden Sie unter [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).  
  
 **So zeigen Sie die Daten und Protokolldateien in einem Sicherungssatz an**  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
 **So stellen Sie Dateien und Dateigruppen an einem neuen Speicherort wieder her**  
  
-   [Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 **So stellen Sie Dateien und Dateigruppen über vorhandene Dateien her**  
  
-   [Wiederherstellen von Dateien und Dateigruppen über vorhandene Dateien &#40;SQL Server&#41;](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 **So stellen Sie eine Datenbank mit einem neuen Namen wieder her**  
  
-   [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 **So starten Sie einen unterbrochenen Wiederherstellungsvorgang neu**  
  
-   [Neustarten eines unterbrochenen Wiederherstellungsvorgangs Operation &#40;Transact-SQL&#41;](../backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 **So ändern Sie den Besitzer einer Datenbank**  
  
-   [sp_changedbowner &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedbowner-transact-sql)  
  
 **So kopieren Sie eine Datenbank mithilfe von SQL Server Management Objects (SMO)**  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kopieren von Datenbanken auf andere Server](copy-databases-to-other-servers.md)   
 [Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
