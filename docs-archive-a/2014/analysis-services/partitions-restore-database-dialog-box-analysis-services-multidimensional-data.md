---
title: Partitionen (Dialog Feld Datenbank wiederherstellen) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621224"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a>Partitionen (Dialogfeld Datenbank wiederherstellen) (Analysis Services – Mehrdimensionale Daten)
  Auf der Seite **Partitionen** des Dialogfelds **Datenbank wiederherstellen** können Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] den Speicherort zum Wiederherstellen der lokalen Partitionen angeben. Darüber hinaus können Sie angeben, ob Remotepartitionen wiederhergestellt werden sollen und welche Remotesicherungsdateien beim Wiederherstellen der Remotepartitionen verwendet werden sollen.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung „Vollzugriff“ (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
 **So zeigen Sie die Seite Partitionen im Dialogfeld Datenbank wiederherstellen an**  
  
-   Klicken Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste entweder auf den Ordner **Datenbanken** einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder auf eine Datenbank im **Objekt-Explorer**, klicken Sie auf **Wiederherstellen**, und klicken Sie anschließend unter **Seite auswählen**auf **Partitionen**.  
  
## <a name="options"></a>Tastatur  
 **Skript**  
 Erstellt ein Wiederherstellungsskript, das auf den im Dialogfeld aktivierten Optionen basiert. Das Wiederherstellungsskript wird in der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptsprache (ASSL) geschrieben.  
  
 Wenn Sie auf das Symbol **Skript** klicken, wird das Wiederherstellungsskript standardmäßig an ein neues Abfragefenster gesendet.  
  
 Durch Klicken auf den Pfeil neben **Skript** wird ein Menü angezeigt, in dem Sie auswählen können, wohin das Wiederherstellungsskript geschickt werden soll:  
  
-   An ein neues Abfragefenster (Standard)  
  
-   An eine Datei  
  
-   An die Zwischenablage  
  
-   An einen Auftrag  
  
 **An ursprünglichen Speicherorten wiederherstellen**  
 Wählen Sie diese Option aus, um die in der Sicherungsdatei enthaltenen lokalen Partitionen an deren ursprünglichen Speicherorten wiederherzustellen.  
  
 **Andere Speicherorte auswählen**  
 Wählen Sie diese Option aus, um verschiedene Speicherorte anzugeben, an welchen lokale Partitionen wiederhergestellt werden.  
  
> [!NOTE]  
>  Den Wiederherstellungsordner einer lokalen Partition können Sie nur ändern, wenn für die Partition im Cube ein anderer als der Standardspeicherort angegeben wurde.  
  
 Das folgende Raster, das bei Auswahl dieser Option aktiviert ist, wird verwendet, um für jede lokale Partition einen Wiederherstellungsordner anzugeben:  
  
|Spalte|BESCHREIBUNG|  
|------------|-----------------|  
|**Cube**|Zeigt den Namen des Cubes mit der lokalen Partition an.|  
|**Measuregruppe**|Zeigt den Namen der Measuregruppe mit der lokalen Partition an.|  
|**Partition**|Zeigt den Namen der lokalen Partition an.|  
|**Größe (MB)**|Zeigt die Größe der lokalen Partition in Megabytes an.|  
|**Ursprünglicher Ordner**|Zeigt den Namen des Ordners an, in dem die lokale Partition ursprünglich gespeichert war.|  
|**Wiederherstellungsordner**|Geben Sie den Namen des Wiederherstellungsordners für die lokale Partition ein, oder klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**...**), um das Dialogfeld **Nach Remoteordner suchen** anzuzeigen, und wählen Sie den Pfad des Ordners aus, der verwendet werden soll. Weitere Informationen zum Dialogfeld **Nach Remoteordner suchen** finden Sie unter [Dialogfeld „Nach Remoteordner suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
 **Remotepartitionen wiederherstellen**  
 Wählen Sie diese Option aus, um in Remotesicherungsdateien gespeicherte Remotepartitionen wiederherzustellen.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn die Sicherungsdatei Verweise auf Remotepartitionen enthält.  
  
 Das folgende Raster, das bei Auswahl dieser Option aktiviert ist, wird verwendet, um für jede lokale Partition einen Wiederherstellungsordner anzugeben:  
  
|Spalte|BESCHREIBUNG|  
|------------|-----------------|  
|**Server**|Zeigt den Namen der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] an, die die Remotepartition verwaltet.|  
|**Data Source**|Zeigt den Namen der Datenquelle in der Sicherungsdatei an, die die Datenbank mit der Remotepartition darstellt.|  
|**Sicherungsdatei**|Geben Sie den vollständigen Pfad und den Dateinamen der Remotesicherungsdatei an, die verwendet werden soll. Wahlweise können Sie auch auf die Schaltfläche mit den drei Punkten(**...**) klicken, um das Dialogfeld **Datenbankdateien suchen** anzuzeigen und dort den Pfad und Dateinamen der betreffenden Remotesicherungsdatei auszuwählen. Weitere Informationen zum Dialogfeld **Datenbankdateien suchen** finden Sie unter [Dialogfeld „Datenbankdateien suchen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).|  
|**...**|Klicken Sie auf diese Schaltfläche, um das Dialogfeld **Remotepartitionen – Erweiterte Einstellungen** anzuzeigen und erweiterte Optionen wie die Verbindungszeichenfolge für die Datenquelle zum Wiederherstellen der Remotepartition zu ändern. Weitere Informationen zum Dialogfeld **Remotepartitionen – Erweiterte Einstellungen** finden Sie unter [Dialogfeld „Remote-Partitionen – Erweiterte Einstellungen“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld "Datenbank wiederherstellen" &#40;Analysis Services-Mehrdimensionale Daten&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Allgemein &#40;Dialog Feld Datenbank wiederherstellen&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
