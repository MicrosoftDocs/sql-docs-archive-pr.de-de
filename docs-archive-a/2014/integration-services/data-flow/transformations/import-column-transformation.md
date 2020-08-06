---
title: Transformation für das Importieren von Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4330438614cce7892e74dc9a1dcbb6680b72972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621100"
---
# <a name="import-column-transformation"></a>Transformation für das Importieren von Spalten
  Die Transformation für das Importieren von Spalten liest Daten aus Dateien und fügt die Daten Spalten in einem Datenfluss hinzu. Mit dieser Transformation kann ein Paket einem Datenfluss Text und Bilder hinzufügen, die in separaten Dateien gespeichert sind. Beispielsweise können in einem Datenfluss, der Daten in eine Tabelle mit Produktinformationen lädt, mit der Transformation für das Importieren von Spalten Kundenbeurteilungen für jedes Produkt aus Dateien importiert und die Beurteilungen dem Datenfluss hinzugefügt werden.  
  
 Es gibt folgende Möglichkeiten, um die Transformation für das Importieren von Spalten zu konfigurieren:  
  
-   Geben Sie die Tabelle an, der die Transformation Daten hinzufügt.  
  
-   Geben Sie an, ob die Transformation eine Bytereihenfolgemarke (BOM, Byte-Order Mark) erwartet.  
  
    > [!NOTE]  
    >  Eine BOM wird nur bei Daten vom DT_NTEXT-Datentyp erwartet.  
  
 Eine Spalte in der Transformationseingabe enthält die Namen von Dateien, in denen die Daten gespeichert sind. In jeder Zeile des Datasets kann eine andere Datei angegeben sein. Wenn die Transformation für das Importieren von Spalten eine Zeile verarbeitet, wird der Dateiname gelesen, die entsprechende Datei im Dateisystem geöffnet und der Dateiinhalt in eine Ausgabespalte geladen. Die Ausgabespalte muss den Datentyp DT_TEXT, DT_NTEXT oder DT_IMAGE aufweisen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../integration-services-data-types.md).  
  
 Diese Transformation weist eine Eingabe, eine Ausgabe und eine Fehlerausgabe auf.  
  
## <a name="configuration-of-the-import-column-transformation"></a>Konfiguration der Transformation für das Importieren von Spalten  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften dieser Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transformation für das Exportieren von Spalten](export-column-transformation.md)   
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
