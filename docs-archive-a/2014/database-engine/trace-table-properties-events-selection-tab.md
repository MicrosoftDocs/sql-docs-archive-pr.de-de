---
title: Eigenschaften der Ablauf Verfolgungs Tabelle (Registerkarte Ereignis Auswahl) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2e72f299c9d83762876ce250f750924430ba2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724890"
---
# <a name="trace-table-properties-events-selection-tab"></a>Eigenschaften der Ablaufverfolgungstabelle (Registerkarte Ereignisauswahl)
  Mithilfe der Registerkarte **Ereignisauswahl** im Dialogfeld **Eigenschaften der Ablaufverfolgungstabelle** können Sie die Ereignisse und Datenspalteneigenschaften der Ablaufverfolgung anzeigen oder Ereignisse bzw. Spalten aus der Ablaufverfolgung entfernen.  
  
 Öffnen Sie mit [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] eine Ablaufverfolgungstabelle, um dieses Fenster anzuzeigen. Klicken Sie dann im Menü **Datei** auf **Eigenschaften**, und klicken Sie dann auf die Registerkarte **Ereignis Auswahl** .  
  
## <a name="options"></a>Tastatur  
 Spalte**Ereignisse**  
 Zeigt verfolgte Ereignisse an, die nach Ereigniskategorien geordnet sind. Die Ereignisse können ausgewählt werden, indem das Kontrollkästchen oder eine Datenspalte für ein Ereignis aktiviert wird. Wenn das Ereigniskästchen aktiviert ist, werden alle für dieses Ereignis verfügbaren Datenspalten ausgewählt. Wenn die Datenspalte für ein Ereignis aktiviert ist, wird das Ereignis automatisch aktiviert und mit ihm alle weiteren erforderlichen Spalten. Wenn Sie eine Ablaufverfolgungsdatei oder -tabelle anzeigen, können Sie per Deaktivierung von Ereignissen oder Datenspalten die Menge der angezeigten Daten im Ablaufverfolgungsfenster zur besseren Übersicht reduzieren. Sie können auch Spaltenfilter ändern, um die Menge der sichtbaren Daten im Ablaufverfolgungsfenster zu reduzieren. Weitere Informationen zu Ereignisklassen finden Sie unter [Ereignisklassen in SQL Server – Referenz](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Sonstige Datenspalten  
 Zeigt Datenspalten der Ablaufverfolgung an. Alle relevanten Datenspalten in der Ablaufverfolgung sind standardmäßig für jedes in die Verfolgung einbezogene Ereignis aktiviert.  
  
 Sie können Filter festlegen, indem Sie auf die Spaltenüberschrift klicken und die Filterkriterien eingeben. Gefilterte Datenspalten sind im Dialogfeld **Filter bearbeiten** links neben der Spaltenbezeichnung durch ein Filtersymbol gekennzeichnet.  
  
 **Alle Ereignisse anzeigen**  
 Zeigt alle verfügbaren Ereignisse an. Standardmäßig werden nur Zeilen im Raster **Ereignisauswahl** angezeigt, die ausgewählt sind. Deaktivieren Sie dieses Kontrollkästchen, um alle nicht ausgewählten Ereignisse im Raster **Ereignisauswahl** auszublenden. Wenn die Option **Alle Ereignisse anzeigen** aktiviert ist und Sie eine Ablaufverfolgungsdatei oder -tabelle anzeigen, werden alle aufgezeichneten Ereignisse in der Ablaufanzeige des Ablaufverfolgungsfensters angezeigt.  
  
 **Alle Spalten anzeigen**  
 Zeigt alle verfügbaren Datenspalten an. Standardmäßig werden nur ausgewählte Datenspalten angezeigt. Deaktivieren Sie dieses Kontrollkästchen, um alle nicht ausgewählten Datenspalten im Raster **Ereignisauswahl** auszublenden.  
  
 **Spaltenfilter**  
 Öffnet das Dialogfeld **Filter** bearbeiten, in dem links neben der Spaltenbezeichnung ein Filtersymbol angezeigt wird. Mithilfe dieses Dialogfelds können Sie Datenspaltenfilter bearbeiten.  
  
 **Spalten organisieren**  
 Klicken Sie nach der Auswahl der zu verfolgenden **Ereignisse** und Datenspalten auf **Spalten organisieren**, um eine Reorganisation der Spalten im Raster des Fensters mit den Ablaufverfolgungsergebnissen zu erzwingen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Öffnen Sie eine Ablauf Verfolgungs Tabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
