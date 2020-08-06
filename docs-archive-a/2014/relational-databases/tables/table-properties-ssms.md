---
title: Tabellen Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618567"
---
# <a name="table-properties"></a>Tabelleneigenschaften
  In diesem Thema werden die Tabelleneigenschaften beschrieben, die im Dialogfeld "Tabelleneigenschaften" in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt werden. Weitere Informationen zum Anzeigen dieser Eigenschaften finden Sie unter [Anzeigen der Tabellendefinition](view-the-table-definition.md).  
  
 **In diesem Thema**  
  
1.  [Seite Allgemein](#GeneralPage)  
  
2.  [Seite "Änderungsnachverfolgung"](#ChangeTracking)  
  
3.  [FileTable-Seite](#FileTable)  
  
4.  [Seite "Speicher"](#Storage)  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> Seite Allgemein  
 **Datenbank**  
 Name der Datenbank, die diese Tabelle enthält.  
  
 **Server**  
 Name der aktuellen Serverinstanz.  
  
 **Benutzer**  
 Name des Benutzers dieser Verbindung.  
  
 **Erstellt am**  
 Datum und Uhrzeit der Erstellung der Tabelle.  
  
 **Name**  
 Der Name der Tabelle.  
  
 **Schema**  
 Schema, das Besitzer der Tabelle ist.  
  
 **Systemobjekt**  
 Gibt an, dass diese Tabelle eine Systemtabelle ist, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Speichern interner Informationen verwendet wird. Benutzer dürfen Systemtabellen nicht direkt ändern bzw. auf sie verweisen.  
  
 **ANSI NULLS**  
 Gibt an, ob das Objekt mit der Option ANSI NULLS auf ON erstellt wurde. Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)  
  
 **Bezeichner in Anführungszeichen**  
 Gibt an, ob das Objekt mit der Option „Bezeichner in Anführungszeichen“ auf ON erstellt wurde. Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
 **Sperrenausweitung**  
 Gibt die Granularität der Sperrenausweitung der Tabelle an. Weitere Informationen zum Sperren in der Datenbank-Engine finden Sie im [Handbuch zu Transaktionssperren und Zeilenversionsverwaltung in SQL Server](https://msdn.microsoft.com/library/jj856598.aspx). Mögliche Werte:  
  
 AUTO  
 Mit dieser Option kann von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die für das Tabellenschema geeignete Granularität der Sperrenausweitung ausgewählt werden.  
  
-   Wenn die Tabelle partitioniert ist, ist die Sperrenausweitung bis zur Heap- oder B-Struktur (HoBT)-Granularität zulässig. Nach der Ausweitung der Sperre auf die HoBT-Ebene wird die Sperrenausweitung nicht bis zur TABLE-Granularität fortgeführt.  
  
-   Wenn die Tabelle nicht partitioniert ist, wird die Sperre bis zur TABLE-Granularität ausgeweitet.  
  
 TABLE  
 Die Sperrenausweitung wird immer mit der Granularität der Tabellenebene ausgeführt, unabhängig davon, ob die Tabelle partitioniert ist. TABLE ist der Standardwert.  
  
 DISABLE  
 Verhindert die Sperrenausweitung in den meisten Fällen. Sperren auf Tabellenebene sind jedoch nicht völlig ausgeschlossen. Wenn Sie z. B. eine Tabelle scannen, die unter der serialisierbaren Isolationsstufe keinen gruppierten Index aufweist, muss [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Tabellensperre zulassen, damit die Datenintegrität gewahrt wird.  
  
 **Die Tabelle ist repliziert**  
 Gibt an, ob die Tabelle mit der Replikationsfunktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in eine andere Datenbank repliziert wurde. Mögliche Werte sind `True` oder `False`.  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a>Änderungsnachverfolgung Seite  
 **Änderungsnachverfolgung**  
 Gibt an, ob die Änderungsnachverfolgung für die Tabelle aktiviert ist. Standardwert: `False`.  
  
 Diese Option ist nur dann verfügbar, wenn die Änderungsnachverfolgung für die Datenbank aktiviert ist.  
  
 Zur Aktivierung der Änderungsnachverfolgung muss die Tabelle einen Primärschlüssel enthalten, und Sie müssen über die Berechtigung zur Änderung der Tabelle verfügen. Sie können die Änderungsnachverfolgung mithilfe von [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)konfigurieren.  
  
 **Aktualisierte Spalten nachverfolgen**  
 Gibt an, ob [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verfolgt, welche Spalten aktualisiert wurden.  
  
 Weitere Informationen zur Änderungsnachverfolgung finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
##  <a name="filetable-page"></a><a name="FileTable"></a>FILETABLE-Seite  
 Zeigt die auf FileTables bezogenen Eigenschaften der Tabelle an. Weitere Informationen finden Sie unter [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).  
  
 **Sortierung der FileTable-Namensspalte**  
 Die Sortierung, die in einer FileTable auf die Spalte **Name** angewendet wird. Die Spalte **Name** enthält Datei- und Verzeichnisnamen.  
  
 **Name des FileTable-Verzeichnisses**  
 Der Stammordner für die FileTable.  
  
 **Aktivierter FileTable-Namespace**  
 Wenn `True`, gibt dieser Wert an, dass die Tabelle eine FileTable ist. Wenn Sie diesen Wert in `False` ändern, ändern Sie die FileTable in eine gewöhnliche Benutzertabelle. Wenn Sie die Tabelle später wieder in eine FileTable ändern möchten, muss die Tabelle eine FileTable-Konsistenzprüfung bestehen, damit die Konvertierung erfolgreich ist.  
  
##  <a name="storage-page"></a><a name="Storage"></a>Seite "Speicher"  
 Zeigt die speicherbezogenen Eigenschaften der ausgewählten Tabelle an.  
  
### <a name="compression"></a>Komprimierung  
 **Komprimierungstyp**  
 Der Komprimierungstyp der Tabelle. Diese Eigenschaft ist nur für nicht partitionierte Tabellen verfügbar. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md).  
  
 **Partitionen mit Seitenkomprimierung**  
 Die Nummern der Partitionen, für die die Seitenkomprimierung verwendet wird. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
 **Nicht komprimierte Partitionen**  
 Die Nummern der nicht komprimierten Partitionen. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
 **Partitionen mit Zeilenkomprimierung**  
 Die Nummern der Partitionen, für die die Zeilenkomprimierung verwendet wird. Diese Eigenschaft ist nur für partitionierte Tabellen verfügbar.  
  
### <a name="filegroup"></a>Dateigruppe  
 **Textdateigruppe**  
 Name der Dateigruppe, die die Textdaten für die Tabelle enthält.  
  
 **Dateigruppe**  
 Der Name der Dateigruppe, die die Tabelle enthält.  
  
 **Die Tabelle ist partitioniert**  
 Mögliche Werte sind `True` und `False`.  
  
 **FILESTREAM-Dateigruppe**  
 Geben Sie den Namen der FILESTREAM-Datendateigruppe an, wenn die Tabelle eine `varbinary(max)`-Spalte mit FILESTREAM-Attribut aufweist. Der Standardwert entspricht der standardmäßigen FILESTREAM-Datendateigruppe.  
  
 Wenn die Tabelle keine FILESTREAM-Daten enthält, ist das Feld leer.  
  
### <a name="general"></a>Allgemein  
 **Das VarDecimal-Speicherformat ist aktiviert.**  
 Wenn `True` der Wert ist, gibt dieser schreibgeschützte Wert an, dass `decimal` `numeric` die Datentypen und mithilfe des vardecimal--Speicher Formats gespeichert werden. Um diese Option zu ändern, verwenden Sie die `vardecimal storage format` Option [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql). Das Vardecimal-Speicherformat ist veraltet. Verwenden Sie stattdessen die ROW-Komprimierung.  
  
 **Indexspeicher**  
 Der Speicherplatz in Megabytes, der von den Indizes in der Tabelle belegt wird. Dieser Wert schließt die Speicherverwendung für den XML-Index der Tabelle nicht mit ein. Verwenden Sie stattdessen [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) , wenn XML-Indizes zur Tabelle gehören.  
  
 **Zeilen Anzahl**  
 Die Anzahl der Zeilen in der Tabelle.  
  
 **Datenspeicher**  
 Der Speicherplatz in Megabytes, der von den Daten in der Tabelle belegt wird.  
  
### <a name="partitioning"></a>Partitionierung  
 Dieser Abschnitt ist nur verfügbar, wenn die Tabelle partitioniert ist. Weitere Informationen finden Sie unter [partitionierte Tabellen und Indizes](../partitions/partitioned-tables-and-indexes.md).  
  
 **Partitionsspalte**  
 Der Name der Spalte, nach der die Tabelle partitioniert ist.  
  
 **Partitionsschema**  
 Der Name des Partitionsschemas, sofern die Tabelle partitioniert ist. Wenn die Tabelle nicht partitioniert ist, ist das Feld leer.  
  
 **Anzahl von Partitionen**  
 Die Anzahl von Partitionen in der Tabelle.  
  
 **FILESTREAM-Partitionsschema**  
 Der Name des FILESTREAM-Partitionsschemas, sofern die Tabelle partitioniert ist. Wenn die Tabelle nicht partitioniert ist, ist das Feld leer.  
  
 Das FILESTREAM-Partitionsschema muss mit dem Schema symmetrisch sein, das in der Option **Partitionsschema** angegeben ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen der Tabellen Definition](view-the-table-definition.md)   
 [Ändern von Spalten &#40;Datenbank-Engine&#41;](../tables/modify-columns-database-engine.md)  
  
  
