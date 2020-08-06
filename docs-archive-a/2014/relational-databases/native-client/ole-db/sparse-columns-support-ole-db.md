---
title: Unterstützung für Sparsespalten (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 918574b3-c62e-4937-9e5f-37310dedc8f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d40964b3c433b35b5ab9af2637389a022cc3961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609850"
---
# <a name="sparse-columns-support-ole-db"></a>Unterstützung für Spalten mit geringer Dichte (OLE DB)
  Dieses Thema enthält Informationen über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Unterstützung für Sparsespalten. Weitere Informationen zu Sparsespalten finden Sie unter [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md). Ein Beispiel finden Sie unter [Anzeigen von Spalten- und Katalogmetadaten für Sparsespalten &#40;OLE DB&#41;](../../native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>OLE DB-Anweisungsmetadaten  
 Ab [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]ist ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, verfügbar. Dieser Wert sollte für Spalten festgelegt werden, die `column_set`-Werte sind. Das DBCOLUMNFLAGS-Flag kann über den *dwFlags*-Parameter von IColumnsInfo::GetColumnsInfo und die DBCOLUMN_FLAGS-Spalte des Rowsets abgerufen werden, das von IColumnsRowset::GetColumnsRowset zurückgegeben wird.  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB-Katalogmetadaten  
 Zwei zusätzliche [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Spalten wurden zu DBSCHEMA_COLUMNS hinzugefügt.  
  
|Spaltenname|Datentyp|Wert/Kommentare|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Wenn die Spalte eine Sparsespalte ist, weist sie den Wert VARIANT_TRUE auf, andernfalls den Wert VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Wenn die Spalte die `column_set`-Spalte mit geringer Dichte ist, weist sie den Wert VARIANT_TRUE auf, andernfalls den Wert VARIANT_FALSE.|  
  
 Zwei zusätzliche Schemarowsets wurden ebenfalls hinzugefügt. Diese Rowsets verfügen über die gleiche Struktur wie DBSCHEMA_COLUMNS, geben aber andere Inhalte zurück. DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie Elemente von `column_set` sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten zurück, die Elemente des `column_set` mit geringer Dichte sind.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility-Verhalten  
 Verhalten mit `DataTypeCompatibility=80` (in der Verbindungszeichenfolge) ist mit einem [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Client konsistent:  
  
-   Die neuen Schemarowsets sind nicht sichtbar, und es gibt keine Zeilen für sie im Rowset der Schemarowsets.  
  
-   Neue Spalten im COLUMNS-Rowset sind nicht sichtbar.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET wird nicht für `column_set`-Spalten festgelegt.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED wird für `column_set`-Spalten festgelegt.  
  
## <a name="ole-db-support-for-sparse-columns"></a>OLE DB-Unterstützung für Spalten mit geringer Dichte  
 Die folgenden OLE DB-Schnittstellen wurden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client geändert, um Sparsespalten zu unterstützen:  
  
|Typ oder Elementfunktion|BESCHREIBUNG|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Ein neuer DBCOLUMNFLAGS-Flagwert DBCOLUMNFLAGS_SS_ISCOLUMNSET der für `column_set` Spalten in *dwFlags*festgelegt ist.<br /><br /> DBCOLUMNFLAGS_WRITE wird für `column_set`-Spalten festgelegt.|  
|IColumsRowset::GetColumnsRowset|Ein neuer DBCOLUMNFLAGS-Flagwert, DBCOLUMNFLAGS_SS_ISCOLUMNSET, wird für `column_set`-Spalten in DBCOLUMN_FLAGS festgelegt.<br /><br /> DBCOLUMN_COMPUTEMODE wird für `column_set`-Spalten auf DBCOMPUTEMODE_DYNAMIC festgelegt.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS gibt zwei neue Spalten zurück: SS_IS_COLUMN_SET und SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS gibt nur Spalten zurück, die keine Elemente eines `column_set` sind.<br /><br /> Zwei neue Schemarowsets wurden hinzugefügt: DBSCHEMA_COLUMNS_EXTENDED gibt alle Spalten zurück, unabhängig davon, ob sie eine geringe Dichte aufweisen oder Elemente von `column_set` sind. DBSCHEMA_SPARSE_COLUMN_SET gibt nur Spalten zurück, die Elemente eines `column_set` sind. Diese neuen Rowsets verfügen über die gleichen Spalten und die Einschränkungen wie DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas schließt die GUIDs für die neuen Rowsets DBSCHEMA_COLUMNS_EXTENDED und DBSCHEMA_SPARSE_COLUMN_SET in die Liste verfügbarer Schemarowsets ein.|  
|ICommand::Execute|Wenn **Select \* from** *Table* verwendet wird, werden alle Spalten zurückgegeben, die keine Elemente der geringer Dichte sind `column_set` , sowie eine XML-Spalte, die Werte aller nicht-NULL-Spalten enthält, die Elemente der geringer Dichte sind `column_set` , falls vorhanden.|  
|IOpenRowset::OpenRowset|IOpenRowset::OpenRowset gibt mithilfe einer **SELECT \***-Abfrage für dieselbe Tabelle ein Rowset mit denselben Spalten wie ICommand::Execute zurück.|  
|ITableDefinition|Es gibt keine Änderungen an dieser Schnittstelle für Sparsespalten oder für `column_set`-Spalten. Anwendungen, die Schemaänderungen vornehmen müssen, müssen das entsprechende [!INCLUDE[tsql](../../../includes/tsql-md.md)] direkt ausführen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](sql-server-native-client-ole-db.md)  
  
  
