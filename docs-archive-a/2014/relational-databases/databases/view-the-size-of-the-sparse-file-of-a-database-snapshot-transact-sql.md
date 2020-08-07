---
title: Anzeigen der Größe der Datei mit geringer Dichte einer Datenbank-Momentaufnahme (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720002"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a>Anzeigen der Größe der Datei mit geringer Dichte einer Datenbank-Momentaufnahme (Transact-SQL)
  In diesem Thema wird beschrieben, wie Sie mit [!INCLUDE[tsql](../../includes/tsql-md.md)] überprüfen, ob eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankdatei eine Sparsedatei ist, und wie Sie die tatsächliche und maximale Größe ermitteln. Dateien mit geringer Dichte, die in Verbindung mit dem NTFS-Dateisystem vorkommen, werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankmomentaufnahmen verwendet.  
  
> [!NOTE]  
>  Beim Erstellen von Datenbankmomentaufnahmen werden Sparsedateien mithilfe der Dateinamen in der CREATE DATABASE-Anweisung erstellt. Diese Dateinamen werden in der Spalte **physical_name** in **sys.master_files** gespeichert. In **sys.database_files** (sowohl in der Quelldatenbank wie auch in einer Momentaufnahme) enthält die Spalte **physical_name** immer die Namen der Quelldatenbankdateien.  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a>Überprüfen, ob eine Datenbankdatei eine Datei mit geringer Dichte ist  
  
1.  Auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
     Wählen Sie entweder in der Datenbank-Momentaufnahme unter **sys.database_files** oder in **sys.master_files** die Spalte **is_sparse**aus. Der Wert gibt wie folgt an, ob die Datei eine Sparsedatei ist:  
  
     1 = Die Datei ist eine Sparsedatei.  
  
     0 = Die Datei ist keine Sparsedatei.  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a>Ermitteln der tatsächlichen Größe einer Datei mit geringer Dichte  
  
> [!NOTE]  
>  Sparsedateien wachsen in 64-KB-Schritten, weshalb die Größe einer Sparsedatei auf dem Datenträger immer einem Vielfachen von 64 KB entspricht.  
  
 Um die Anzahl der Bytes anzuzeigen, die die einzelnen sparsedateien einer Momentaufnahme zurzeit auf dem Datenträger verwenden, Fragen Sie die **size_on_disk_bytes** Spalte der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dynamischen Verwaltungs Sicht [sys. dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) ab.  
  
 Zum Anzeigen des Speicherplatzes, der durch eine Sparsedatei in Anspruch genommen wird, klicken Sie in Microsoft Windows mit der rechten Maustaste auf **Eigenschaften**, und lesen Sie den Wert unter **Größe auf Datenträger** ab.  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a>Ermitteln der maximalen Größe einer Datei mit geringer Dichte  
 Eine Datei mit geringer Dichte kann maximal die Größe der Quelldatenbankdatei erreichen, die zum Zeitpunkt der Momentaufnahmeerstellung festgelegt wurde. Zur Ermittlung dieser Größe stehen Ihnen die folgenden Alternativen zur Auswahl:  
  
-   Verwenden der Windows-Eingabeaufforderung:  
  
    1.  Verwenden Sie die **dir** -Befehle an der Eingabeaufforderung von Windows.  
  
    2.  Wählen Sie die Datei mit geringer Größe aus, öffnen Sie in Windows das Dialogfeld **Eigenschaften** der Datei, und lesen Sie den Wert für die **Größe** ab.  
  
-   Auf der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
     Wählen Sie entweder in **sys.database_files** in der Datenbank-Momentaufnahme oder in **sys.master_files** die **size**-Spalte aus. Der Wert in der **size** -Spalte gibt den maximal durch eine Momentaufnahme verwendbaren Speicherplatz in SQL-Seiten an. Dieser Wert entspricht dem Feld **Größe** in Windows. Der einzige Unterschied besteht darin, dass hierbei die Anzahl der SQL-Seiten in der Datei angegeben wird. Die Größe in Bytes kann daraus wie folgt errechnet werden:  
  
     ( *Seitenanzahl* * 8192)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Momentaufnahmen &#40;SQL Server&#41;](database-snapshots-sql-server.md)   
 [sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql)   
 [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
