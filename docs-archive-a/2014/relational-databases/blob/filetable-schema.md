---
title: FileTable-Schema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], table schema
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fa6a6d3d033633a136f51437c415a2998c075859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723930"
---
# <a name="filetable-schema"></a>FileTable-Schema
  Beschreibt das vordefinierte und feste Schema einer FileTable.  
  
|Name des Dateiattributs|type|Size|Standard|BESCHREIBUNG|Barrierefreiheit für das Dateisystem|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path_locator**|`hierarchyid`|-Variable|Ein `hierarchyid`, der die Position dieses Elements identifiziert.|Die Position dieses Knotens im hierarchischen FileNamespace.<br /><br /> Primärschlüssel für die Tabelle.|Kann durch Festlegen der Windows-Pfadwerte erstellt und geändert werden.|  
|**stream_id**|**[uniqueidentifier] rowguidcol**||Ein von der `NEWID()`-Funktion zurückgegebener Wert.|Eine eindeutige ID für die FILESTREAM-Daten.|Nicht zutreffend|  
|**file_stream**|`varbinary(max)`<br /><br /> `filestream`|Variable|NULL|Enthält die FILESTREAM-Daten.|Nicht zutreffend|  
|**file_type**|`nvarchar(255)`|Variable|NULL.<br /><br /> Durch einen Erstellungs- bzw. Umbenennungsvorgang im Dateisystem wird der Dateierweiterungswert aus dem Namen übernommen.|Stellt den Typ der Datei dar.<br /><br /> Diese Spalte kann als `TYPE COLUMN` verwendet werden, wenn Sie einen Volltextindex erstellen.<br /><br /> **file_type** ist eine persistente berechnete Spalte.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**Name**|`nvarchar(255)`|Variable|GUID-Wert.|Der Datei- oder Verzeichnisname.|Kann mit Windows-APIs erstellt oder geändert werden.|  
|**parent_path_locator**|`hierarchyid`|-Variable|Ein `hierarchyid`, der das Verzeichnis identifiziert, das dieses Element enthält.|Der `hierarchyid` des enthaltenden Verzeichnisses.<br /><br /> **parent_path_locator** ist eine persistente berechnete Spalte.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**cached_file_size**|`bigint`|||Die Größe der FILESTREAM-Daten in Byte.<br /><br /> **cached_file_size** ist eine persistente berechnete Spalte.|Obwohl die zwischengespeicherte Dateigröße automatisch auf dem aktuellen Stand gehalten wird, kann sie unter außergewöhnlichen Umständen möglicherweise nicht synchronisiert sein. Verwenden Sie die `DATALENGTH()`-Funktion, um die genaue Größe zu berechnen.|  
|**creation_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit der Erstellung der Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**last_write_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit des letzten Updates der Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**last_access_time**|`datetime2(4)`<br /><br /> `not null`|8 Byte|Aktuelle Zeit.|Datum und Uhrzeit des letzten Zugriffs auf die Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_directory**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Gibt an, ob die Zeile ein Verzeichnis darstellt. Dieser Wert wird automatisch berechnet und kann nicht festgelegt werden.|Automatisch berechnet. Kann nicht festgelegt werden.|  
|**is_offline**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für Offlinedatei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_hidden**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für ausgeblendete Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_readonly**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für schreibgeschützte Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_archive**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Archivattribut.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_system**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für Systemdatei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
|**is_temporary**|`bit`<br /><br /> `not null`|1 Byte|FALSE|Attribut für temporäre Datei.|Automatisch berechnet. Kann auch mit Windows-APIs festgelegt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen, Ändern und Löschen von FileTables](create-alter-and-drop-filetables.md)  
  
  
