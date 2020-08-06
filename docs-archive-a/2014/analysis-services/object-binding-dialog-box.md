---
title: Objekt Bindung (Dialog Feld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
ms.openlocfilehash: a10c91e0222b826066aeede96aa665cc22540637
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619389"
---
# <a name="object-binding-dialog-box"></a>Objektbindung (Dialogfeld)
  Mithilfe des Dialogfelds **Objektbindung** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie Bindungen zwischen der Eigenschaft eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekts und einer Tabelle oder Spalte in einer Datenquellensicht definieren. Sie können das Dialogfeld **Objektbindung** anzeigen, indem Sie im Fenster **Eigenschaften** von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aus der Dropdownliste den Wert **(Neu)** für folgende Eigenschaften eines [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]-Objekts wählen:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Tastatur  
 **Bindungstyp**  
 Wählen Sie die Bindung aus, die für das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verwendet werden soll. Folgende Bindungstypen können verwendet werden:  
  
 Spaltenbindung  
 Bindet das Objekt innerhalb einer Datenquellensicht an eine vorhandene Tabelle und Spalte.  
  
 Spalte generieren  
 Zeigt an, dass eine neue Spalte in der Datenquellensicht definiert wird, der dann eine Spaltenbindung zugeordnet wird.  
  
> [!NOTE]  
>   Wenn diese Option ausgewählt ist, müssen Sie **Schemagenerierungs-Assistent** ausführen, bevor Sie das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt bereitstellen.  
  
 Zeilenbindung  
 Bindet das Objekt an eine Zeile in einer Faktentabelle und wird verwendet, um die Zählung von Measures anhand der Anzahl der in der Faktentabelle verarbeiteten Zeilen zu vereinfachen.  
  
 **Quell Tabelle**  
 Zeigt eine Liste von Tabellen in der Datenquellensicht an, die dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt zugeordnet sind.  
  
 **Quell Spalte**  
 Zeigt eine Liste von Spalten in der unter **Quelltabelle**ausgewählten Tabelle an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
