---
title: Abfragen der Data Mining-Schemarowsets (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620677"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a>Abfragen der Data Mining-Schemarowsets (Analysis Services – Data Mining)
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]werden viele der bestehenden OLE DB Data Mining-Schemarowsets als Gruppe von Systemtabellen verfügbar gemacht, die Sie mit DMX (Data Mining Extensions)-Anweisungen abfragen können. Durch das Erstellen von Queries für das Data Mining-Schemarowset können Sie die zur Verfügung stehenden Services identifizieren, Statusupdates für Ihre Modelle und Strukturen erhalten und Details über den Inhalt des Modells oder Parameter erfahren. Eine Beschreibung des Data Mining-Schemarowsets finden Sie unter [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
> [!NOTE]  
>  Sie können auch das Data Mining-Schemarowset mithilfe von XMLA abfragen. Weitere Informationen dazu, wie Sie dies in SQL Server Management Studio tun, finden Sie unter [Erstellen einer Data Mining-Abfrage mit XMLA](create-a-data-mining-query-by-using-xmla.md).  
  
## <a name="list-of-data-mining-schema-rowsets"></a>Liste der Data Mining-Schemarowsets  
 In der folgenden Tabelle werden die Data Mining-Schemarowsets, die möglicherweise zum Abfragen und Überwachen nützlich sind, aufgelistet.  
  
|Rowsetname|BESCHREIBUNG|  
|-----------------|-----------------|  
|DMSCHEMA_MINING_MODELS-Rowset|Listet alle Miningmodelle im aktuellen Kontext auf.<br /><br /> Beinhaltet Informationen wie das Erstellungsdatum, Parameter, die zur Erstellung des Modells verwendet wurden, und die Größe des Trainingsatzes.|  
|DMSCHEMA_MINING_COLUMNS|Listet alle in Miningmodellen verwendeten Spalten im aktuellen Kontext auf.<br /><br /> Zu den Informationen gehören das Zuordnen der Quellspalte der Miningstruktur, der Datentyp, die Genauigkeit und Vorhersagefunktionen, die mit der Spalte verwendet werden können.|  
|DMSCHEMA_MINING_STRUCTURES|Listet alle Miningstrukturen im aktuellen Kontext auf.<br /><br /> Hierzu gehören Informationen darüber, ob die Struktur Daten enthält, das Datum der letzten Verarbeitung der Struktur und gegebenenfalls die Definition des zurückgehaltenen Datasets.|  
|DMSCHEMA_MINING_STRUCTURE_COLUMNS|Listet alle in Miningstrukturen verwendeten Spalten im aktuellen Kontext auf.<br /><br /> Zu den Informationen gehören Inhaltstyp und Datentyp, NULL-Zulässigkeit und ob die Spalte geschachtelte Tabellendaten enthält.|  
|DMSCHEMA_MINING_SERVICES|Listet alle Miningdienste oder Algorithmen, die auf dem angegebenen Server verfügbar sind, auf.<br /><br /> Informationen enthalten unterstützte Modellierungsflags, Eingabetypen und unterstützte Datenquellentypen.|  
|DMSCHEMA_MINING_SERVICE_PARAMETERS|Listet alle Parameter für die Miningdienste, die auf der angegebenen Instanz verfügbar sind, auf.<br /><br /> Die Informationen enthalten den Datentyp für jeden Parameter, die Standardwerte und die oberen und unteren Grenzen.|  
|DMSCHEMA_MODEL_CONTENT|Gibt den Inhalt des Modells zurück, wenn das Modell verarbeitet wurde.<br /><br /> Weitere Informationen finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).|  
|DBSCHEMA_CATALOGS|Listet alle Datenbanken (Kataloge) in der aktuellen Instanz von Analysis Services auf.|  
|MDSCHEMA_INPUT_DATASOURCES|Listet alle Datenquellen in der aktuellen Instanz von Analysis Services auf.|  
  
> [!NOTE]  
>  Die Liste in der Tabelle ist nicht vollständig; es werden nur die Rowsets angezeigt, die für die Problembehandlung am wichtigsten sein könnten.  
  
## <a name="examples"></a>Beispiele  
 Der folgende Abschnitt enthält einige Beispiele für Abfragen gegen die Data Mining-Schemarowsets.  
  
### <a name="example-1-list-data-mining-services"></a>Beispiel 1: Auflisten von Data Mining-Diensten  
 Die folgende Abfrage gibt eine Liste der Miningdienste zurück, die auf dem aktuellen Server zur Verfügung stehen, d. h. die aktivierten Algorithmen. Die für jeden Miningdienst bereitgestellten Spalten beinhalten die Modellierungsflags und Inhaltstypen, die von jedem Algorithmus verwendet werden können, die GUID für jeden Dienst und jegliche Vorhersagenbeschränkungen, die für jeden Dienst hinzugefügt worden sein könnten.  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a>Beispiel 2: Auflisten von Miningmodellparametern  
 Das folgende Beispiel gibt die Parameter zurück, die verwendet wurden, um ein bestimmtes Miningmodell zu erstellen.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a>Beispiel 3: Auflisten aller Rowsets  
 Im folgenden Beispiel wird eine umfassende Liste der Rowsets, die auf dem aktuellen Server verfügbar sind, zurückgegeben:  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte zur Problembehandlung (Analysis Services &amp;ndash; Data Mining)](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
