---
title: Dialog Feld "Speichereinstellungen" (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.f1
- sql12.asvs.cubeeditor.cubebuilder.measuregroupstoragesettings.f1
ms.assetid: 80c41c71-226c-45fe-b9cf-af824b592fe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2ec48f97e7d0a86f64f53e41f5c5df1c0728fff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723142"
---
# <a name="storage-settings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Speichereinstellungen' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Speichereinstellungen** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie das proaktive Zwischenspeichern, den Speicher und Benachrichtigungseinstellungen für Dimensionen, Cubes, Measuregruppen und Partitionen festlegen. Das Dialogfeld **Speichereinstellungen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie folgendermaßen aufrufen:  
  
-   Klicken Sie im Eigenschaften Fenster von auf die Schaltfläche mit den Auslassungs Zeichen (**...**) für den `ProactiveCaching` Eigenschafts Wert einer Dimension **Properties** , eines Cubes, einer Measure-Gruppe oder einer Partition [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .  
  
-   Erweitern Sie auf der Registerkarte **Partitionen** von **Cube-Designer** eine Measuregruppe, und klicken Sie auf **Speichereinstellungen**.  
  
-   Erweitern Sie eine Measuregruppe, wählen Sie auf der Registerkarte **Partitionen** von **Cube-Designer** im Raster der Measuregruppe eine Partition für diese Measuregruppe aus, und klicken Sie auf **Speichereinstellungen**.  
  
-   Erweitern Sie eine Measuregruppe, wählen Sie auf der Registerkarte **Partitionen** von **Cube-Designer** eine Partition im Raster für diese Measuregruppe aus, und klicken Sie in **Cube-Designer** auf der Registerkarte **Partitionen** im Bereich **Symbolleiste** auf **Speichereinstellungen**.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|Werte|  
|----------|----------------|------------|  
|**Standardeinstellung**|Wählen Sie diese Option aus, um den Schieberegler **Standardeinstellung** zu aktivieren und vordefinierte Einstellungen für den Speichermodus und die Funktion proaktives Zwischenspeichern zu verwenden.||  
|**Standardeinstellung**|Legen Sie eine der folgenden vordefinierten Einstellungen fest:<br /><br /> **Echtzeit-ROLAP**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|ROLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 0 Sekunden.<br /><br /> Schaltet das Objekt sofort online.|  
||**Echtzeit-HOLAP**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|HOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 0 Sekunden.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von null (0) Sekunden und ohne Ruhe-Überschreibungsintervall.<br /><br /> Schaltet das Objekt sofort online.|  
||**MOLAP mit geringer Latenzzeit**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 30 Minuten.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von 10 Sekunden und einem Ruhe-Überschreibungsintervall von 10 Minuten.<br /><br /> Schaltet das Objekt sofort online.|  
||**MOLAP mit mittlerer Latenzzeit**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Löscht veraltete Zwischenspeicherinhalte mit einer Latenzzeit von 4 Stunden.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von 10 Sekunden und einem Ruhe-Überschreibungsintervall von 10 Minuten.<br /><br /> Schaltet das Objekt sofort online.|  
||**Automatische MOLAP**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Aktualisiert den Zwischenspeicher bei Änderungen der Daten mit einem Ruheintervall von null (0) Sekunden und ohne Ruhe-Überschreibungsintervall.|  
||**Geplante MOLAP**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|MOLAP-Speichermodus<br /><br /> Aktiviert die proaktive Zwischenspeicherung.<br /><br /> Aktualisiert den Zwischenspeicher in regelmäßigen Abständen mit einem Neuerstellungsintervall von einem Tag.|  
||**MOLAP**<br /><br /> Wählen Sie diese Einstellung aus, um die folgenden Einstellungen für die Speicherung und das proaktive Zwischenspeichern zu verwenden:|MOLAP-Speichermodus|  
|**Benutzerdefinierte Einstellung**|Wählen Sie diese Option aus, um die Einstellungen für Speichermodus, proaktives Zwischenspeichern und Benachrichtigungsoptionen explizit festzulegen.||  
|**Optionen**|Klicken Sie hier, um das Dialogfeld **Speicheroptionen** anzuzeigen und Speichermodus, proaktives Zwischenspeichern und Benachrichtigungsoptionen explizit festzulegen. Weitere Informationen zum Dialogfeld **Speicheroptionen** finden Sie unter [Speicheroptionen &#40;Dialogfeld, Analysis Services – mehrdimensionale Daten&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md).||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Proaktives Zwischenspeichern &#40;Partitionen&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Cube-Speicher &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)  
  
  
