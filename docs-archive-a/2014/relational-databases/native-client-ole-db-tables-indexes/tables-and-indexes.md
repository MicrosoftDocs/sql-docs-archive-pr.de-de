---
title: Tabellen und Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: rothja
ms.author: jroth
ms.openlocfilehash: abc7c314e433eb9f107bd191738d951706f1b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619080"
---
# <a name="tables-and-indexes"></a>Tabellen und Indizes
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter macht die **IIndexDefinition** -und **ITableDefinition** -Schnittstellen verfügbar und ermöglicht es Consumern, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen und Indizes zu erstellen, zu ändern und zu löschen. Gültige Tabellen- und Indexdefinitionen hängen von der Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab.  
  
 Die Möglichkeit, Tabellen und Indizes zu erstellen oder zu löschen, hängt von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zugriffsrechten des Benutzers der Consumeranwendung ab. Das Löschen einer Tabelle kann durch das Vorhandensein von Beschränkungen der deklarativen referenziellen Integrität oder anderer Faktoren weiter eingeschränkt sein.  
  
 Die meisten Anwendungen, die auf abzielen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden SQL-DMO anstelle dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieter Schnittstellen. SQL-DMO steht für eine Auflistung von OLE-Automatisierungsobjekten, die alle administrativen Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen. Anwendungen, die auf mehrere OLE DB-Anbieter ausgerichtet sind, verwenden diese generischen OLE DB-Schnittstellen, die von den verschiedenen OLE DB-Anbietern unterstützt werden.  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERCOLUMN definiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgende Eigenschaft.  
  
|Eigenschafts-ID|BESCHREIBUNG|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Typ: VT_BSTR<br /><br /> R/W: Schreiben<br /><br /> Default: NULL<br /><br /> Beschreibung: Diese Eigenschaft wird nur in **ITableDefinition** verwendet. Die in dieser Eigenschaft angegebene Zeichenfolge wird beim Erstellen einer [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)-Anweisung verwendet.<br /><br /> verwendet.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen von SQL Server-Tabellen](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Hinzufügen einer Spalte zu einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Entfernen einer Spalte aus einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Löschen einer SQL Server-Tabelle](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Erstellen von SQL Server-Indizes](../../relational-databases/indexes/indexes.md)  
  
-   [Löschen eines SQL Server-Index](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
