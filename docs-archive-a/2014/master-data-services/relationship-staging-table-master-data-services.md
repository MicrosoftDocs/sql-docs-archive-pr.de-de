---
title: Stagingtabelle für Beziehungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 529d0521c320ff2e893a2269fe020d191a6ce284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621031"
---
# <a name="relationship-staging-table-master-data-services"></a>Stagingtabelle für Beziehungen (Master Data Services)
  Ändern Sie den Speicherort von Elementen in einer expliziten Hierarchie anhand der Beziehung der Elemente untereinander, indem Sie die Stagingtabelle für Beziehungen (stg.name_Relationship) in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank verwenden.  
  
##  <a name="table-columns"></a><a name="TableColumns"></a>Tabellen Spalten  
 Die folgende Tabelle erklärt, wofür jedes der Felder in der Stagingtabelle für Beziehungen verwendet wird.  
  
|Spaltenname|BESCHREIBUNG|  
|-----------------|-----------------|  
|**ID**|Ein automatisch zugewiesener Bezeichner. Geben Sie in diesem Feld keinen Wert ein. Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**RelationshipType**<br /><br /> Erforderlich|Der festgelegte Beziehungstyp. Mögliche Werte:<br /><br /> **1**: übergeordnet<br /><br /> **2**: gleichgeordnet (auf gleicher Ebene)|  
|**ImportStatus_ID**<br /><br /> Erforderlich|Der Status des Importvorgangs. Mögliche Werte:<br /><br /> **0**geben Sie an, um anzuzeigen, dass der Datensatz für den Stagingprozess bereit ist.<br /><br /> **1**: wird automatisch zugewiesen und gibt an, dass der Stagingprozess für den Datensatz erfolgreich war.<br /><br /> **2**: wird automatisch zugewiesen, und gibt an, dass der Stagingprozess für den Datensatz nicht erfolgreich war.|  
|**Batch_ID**<br /><br /> Wird nur vom Webdienst benötigt|Ein automatisch zugewiesener Bezeichner, der Datensätze für das Staging gruppiert. Alle Elemente im Batch werden diesem Bezeichner zugewiesen, der in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Benutzeroberfläche in der **ID** -Spalte angezeigt wird.<br /><br /> Wenn der Batch nicht verarbeitet wurde, ist dieses Feld leer.|  
|**BatchTag**<br /><br /> Erforderlich, außer vom Webdienst|Ein eindeutiger Name für den Batch (bis zu 50 Zeichen).|  
|**HierarchyName**<br /><br /> Erforderlich|Der explizite Name der Hierarchie. Jedes konsolidierte Element kann nur einer Hierarchie angehören.|  
|**ParentCode**<br /><br /> Erforderlich|Für über- und untergeordnete Beziehungen der Code für das konsolidierte Element, das als übergeordnetes Element des untergeordneten Blattes oder konsolidierten Elements fungiert.<br /><br /> Für gleichgeordnete Beziehungen der Code für eines der gleichgeordneten Elemente.|  
|**ChildCode**<br /><br /> Erforderlich|Für über- und untergeordnete Beziehungen der Code für das konsolidierte Element oder Blattelement, das als untergeordnetes Element fungiert.<br /><br /> Für gleichgeordnete Beziehungen der Code für eines der gleichgeordneten Elemente.|  
|**Sortierreihenfolge**<br /><br /> Optional|Eine ganze Zahl, die die Reihenfolge des Elements im Verhältnis zu den anderen Elementen unter dem übergeordneten Element angibt. Jedes untergeordnete Element sollte über einen eindeutigen Bezeichner verfügen.|  
|**ErrorCode**|Zeigt einen Fehlercode an. Informationen zu Datensätzen mit einer **ImportStatus_ID** von **2**, finden Sie unter [Fehler des Stagingprozesses &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verschieben Sie explizite Hierarchie Elemente mithilfe des Stagingprozesses &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Daten Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Anzeigen von Fehlern, die während des Stagingprozesses auftreten &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Fehler des Stagingprozesses &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
