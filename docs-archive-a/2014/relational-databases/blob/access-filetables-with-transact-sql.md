---
title: Zugreifen auf FileTables mit Transact-SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c47751ef34747e1b3742accf5040846ecde074f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721501"
---
# <a name="access-filetables-with-transact-sql"></a>Zugreifen auf FileTables mit Transact-SQL
  Beschreibt, wie die Befehle der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Datenbearbeitungssprache (Data Manipulation Language, DML) mit FileTables funktionieren.  
  
##  <a name="insert-operations-on-filetables"></a><a name="BasicsInsert"></a> INSERT-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **INSERT** -Vorgänge in FileTables:  
  
-   Alle Dateiattributspalten besitzen NOT NULL-Einschränkungen. Wenn Werte nicht explizit festgelegt werden, werden entsprechende Standardwerte angegeben.  
  
-   Systemdefinierte Einschränkungen werden erzwungen, wenn die INSERT-Anweisung **name**, **path_locator**, **parent_path_locator**oder Dateiattribute festlegt.  
  
-   Die Anwendung kann **path_locator** für eine Datei oder ein Verzeichnis abrufen, indem in der Funktion [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) der Dateisystempfad angegeben wird.  
  
##  <a name="update-operations-on-filetables"></a><a name="BasicsUpdate"></a> UPDATE-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **UPDATE** -Vorgänge in FileTables:  
  
-   Aktualisierungen an benutzerdefinierten Daten sind zulässig.  
  
-   Systemdefinierte Einschränkungen werden erzwungen, wenn die INSERT-Anweisung **name**, **path_locator**, **parent_path_locator**oder Dateiattribute festlegt.  
  
-   Aktualisierungen können an den FILESTREAM-Daten in der Spalte **file_stream** ohne Auswirkungen auf die anderen Spalten, einschließlich Timestamps, vorgenommen werden.  
  
##  <a name="delete-operations-on-filetables"></a><a name="BasicsDelete"></a> DELETE-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **DELETE** -Vorgänge in FileTables:  
  
-   Durch Löschen einer Zeile wird auch die entsprechende Datei oder das entsprechende Verzeichnis aus dem Dateisystem entfernt.  
  
-   Das Löschen einer Zeile schlägt fehl, wenn die Zeile einem Verzeichnis entspricht, das andere Dateien oder Verzeichnisse enthält.  
  
##  <a name="constraints-that-are-enforced-for-dml-operations-on-filetables"></a><a name="BasicsConstraints"></a> Einschränkungen, die für DML-Vorgänge in FileTables erzwungen werden  
 Systemdefinierte Einschränkungen stellen sicher, dass DML-Aktionen nicht die Integrität der Dateinamespacehierarchie beeinträchtigen. Zu den Einschränkungen, die erzwungen werden, gehören Folgende:  
  
-   Wenn Sie **name** der Datei oder des Verzeichnisses festgelegt oder geändert haben:  
  
    -   Die Windows-Benennungskonventionen für Dateien und Verzeichnisse werden erzwungen.  
  
    -   Die Eindeutigkeit des Namens im übergeordneten Verzeichnis wird erzwungen.  
  
-   Wenn Sie den Speicherort einer Datei oder eines Verzeichnisses durch Festlegen oder Ändern von **path_locator** oder **parent_path_locator**festgelegt oder geändert haben:  
  
    -   Eindeutigkeit wird erzwungen.  
  
    -   Die Konsistenz der hierarchischen Struktur von Verzeichnissen und Dateien wird erzwungen, einschließlich der Konsistenz der Werte **path_locator** und **parent_path_locator** .  
  
-   Der Wert für **is_directory** kann nicht auf TRUE festgelegt werden, wenn die **file_stream** -Spalte nicht NULL ist. Daten in der **file_stream** -Spalte geben an, dass die Zeile eine Datei und nicht ein Verzeichnis darstellt.  
  
-   Spalten mit Dateiattributen können nicht NULL sein. NOT NULL-Einschränkungen werden mit Standardwerten erzwungen.  
  
-   Der Wert **last_access_time** kann nicht vor **last_write_time** und **creation_time**liegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Laden von Dateien in FileTables](load-files-into-filetables.md)   
 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)   
 [Zugreifen auf FileTables mit Datei-E/A-APIs](access-filetables-with-file-input-output-apis.md)   
 [FileTable-DDL, Funktionen, gespeicherte Prozeduren und Sichten](../views/views.md)  
  
  
