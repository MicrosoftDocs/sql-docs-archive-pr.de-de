---
title: Exportieren und Importieren von Data Mining-Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01e8651dd7e9d59012b0ba065bccb9ea62a1ee54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620054"
---
# <a name="export-and-import-data-mining-objects"></a>Exportieren und Importieren von Data Mining-Objekten
  Zusätzlich zu den in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbaren Funktionen zum Sichern, Wiederherstellen und Migrieren von Lösungen bietet SQL Server Data Mining die Möglichkeit, Data Mining-Strukturen und -Modelle mithilfe von Data Mining-Erweiterungen (Data Mining Extensions, DMX) zügig zwischen verschiedenen Servern zu übertragen.  
  
 Wenn die Data Mining-Lösung relationale Daten statt einer multidimensionalen Datenbank verwendet, ist die Übertragung von Modellen mit `EXPORT` und `IMPORT` wesentlich schneller und einfacher, als die Datenbankwiederherstellung zu verwenden oder eine vollständige Lösung bereitzustellen.  
  
 Dieser Abschnitt enthält eine Übersicht über die Übertragung von Data Mining-Strukturen und Modellen mithilfe von DMX-Anweisungen. Details zur Syntax sowie Beispiele finden Sie unter [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) und [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).  
  
> [!NOTE]  
>  Sie müssen Datenbank- oder Serveradministrator sein, damit Sie Objekte aus einer bzw. in eine Datenbank von Microsoft SQL Server Analysis Services exportieren bzw. importieren können.  
  
## <a name="exporting-data-mining-structures"></a>Exportieren von Data Mining-Strukturen  
 Wenn Sie eine Miningstruktur exportieren, exportiert die EXPORT-Anweisung automatisch alle zugeordneten Modelle. Wenn Sie die Objekte kontrollieren möchten, die exportiert werden, müssen Sie jedes Objekt mit Namen angeben.  
  
 Wenn die Miningstruktur dem Standardverhalten beim Exportieren der Miningstruktur entsprechend verarbeitet wurde und die Ergebnisse zwischengespeichert wurden, enthält die Definition eine Zusammenfassung der Daten, auf denen die Struktur basiert. Um diese Zusammenfassung zu entfernen, müssen Sie den mit der Miningstruktur verknüpften Cache löschen, indem Sie einen `Process Clear Structure`-Vorgang ausführen. Weitere Informationen finden Sie unter [Process a Mining Structure](process-a-mining-structure.md).  
  
### <a name="exporting-data-mining-models"></a>Exportieren von Data Mining-Modellen  
 Mit dem `WITH DEPENDENCIES`-Schlüsselwort können Sie die Datenquelle und die Datenquellensichtdefinition zusammen mit dem Miningmodell und seiner Struktur exportieren.  
  
 Wenn Sie ein Miningmodell exportieren, ohne seine Abhängigkeiten zu exportieren, exportiert die EXPORT-Anweisung zwar die Definition des Miningmodells und der zugehörigen Miningstruktur, jedoch nicht die Definition der Datenquellen. Nach dem Importieren können Sie das Modell daher sofort durchsuchen. Wenn Sie das Miningmodell auf dem Zielserver jedoch erneut verarbeiten oder Abfragen für die zugrunde liegenden Daten ausführen möchten, müssen Sie eine entsprechende Datenquelle auf dem Zielserver erstellen.  
  
## <a name="importing-data-mining-structures-and-models"></a>Importieren von Data Mining-Strukturen und -Modellen  
 Beim Importieren eines Data Mining-Objekts wird das Objekt auf den Server und in die Datenbank importiert, mit dem bzw. der Sie beim Ausführen der IMPORT-Anweisung verbunden sind. Wenn die Importdatei eine Datenbank enthält, die auf dem Server nicht vorhanden ist, wird die Datenbank erstellt.  
  
 Sie können eine Miningstruktur oder ein Miningmodell auch mit dem `Restore`-Befehl importieren. Die Modelle oder Strukturen werden in der Datenbank wiederhergestellt, die den gleichen Namen trägt, wie die Datenbank, aus der sie exportiert wurden. Weitere Informationen finden Sie unter [Restore Options](../multidimensional-models/restore-options.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können ein Modell oder eine Struktur nicht auf einen Server importieren, wenn bereits ein Modell oder eine Struktur mit dem gleichen Namen vorhanden ist. Sie können auch kein Data Mining-Objekt exportieren und anschließend den Namen dieses Objekts in der Exportdatei ändern. Wenn Namenskonflikte zu erwarten sind, sollten Sie daher entweder das Data Mining-Objekt auf dem Zielserver löschen oder das Data Mining-Objekt umbenennen, bevor Sie die Definition exportieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von Data Mining-Lösungen und -Objekten](management-of-data-mining-solutions-and-objects.md)  
  
  
