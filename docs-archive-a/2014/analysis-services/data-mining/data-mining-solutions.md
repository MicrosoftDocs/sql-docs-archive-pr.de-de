---
title: Data Mining-Lösungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0ab4b5ddcc9958fa36d6c8ecae0e7fd79585b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616843"
---
# <a name="data-mining-solutions"></a>Data Mining-Projektmappen
  Eine Data Mining-Projektmappe ist eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projektmappe, die ein oder mehrere Data Mining-Projekte enthält.  
  
 Die Themen in diesem Abschnitt enthalten Informationen zum Entwerfen und Implementieren einer integrierten Data Mining Lösung mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Eine Übersicht über den Data Mining-Entwurfsprozess und verwandte Tools finden Sie unter [Data Mining Concepts](data-mining-concepts.md).  
  
 Weitere Informationen zu zusätzlichen Projekttypen, die für Data Mining nützlich sind, finden Sie unter [Verwandte Projekte für Data Mining-Lösungen](data-mining-solutions.md).  
  
 [Vergleich der relationalen und mehrdimensionalen Projektmappen](#bkmk_RelMD)  
  
 [Bereitstellen von Data Mining-Projektmappen](#bkmk_Deploy)  
  
 [Anleitungen für Projektmappen](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a>Relationale und mehrdimensionale Lösungen  
 Eine Data Mining Lösung kann entweder auf mehrdimensionalen Daten basieren, d. h. auf einem vorhandenen Cube, oder auf rein relationalen Daten, wie z. b. Tabellen und Sichten in einer Data Warehouse, oder auf Textdateien, Excel-Arbeitsmappen oder anderen externen Datenquellen.  
  
-   Sie können Data Mining-Objekte innerhalb einer vorhandenen mehrdimensionalen Datenbankprojektmappe erstellen.  
  
     In der Regel würden Sie eine Projektmappe so erstellen, wenn Sie bereits einen Cube erstellt haben und Data Mining mit dem Cube als Datenquelle ausführen möchten. Wenn Sie Modelle auf Grundlage eines Cubes verschieben und sichern, muss der Cube auch verschoben oder kopiert werden.  
  
-   Sie können eine Data Mining-Projektmappe erstellen, die nur Data Mining-Objekte enthält, einschließlich der unterstützenden Datenquellen und Datenquellensichten, und die nur die relationale Datenquelle verwendet.  
  
     Dies ist die bevorzugte Methode zum Erstellen von Data Mining-Modellen, da die Verarbeitung und das Abfragen für relationale Datenquellen im Allgemeinen am schnellsten ist. Sie können sich auch Modelle zwischen Servern problemlos mit den Befehlen EXPORT und IMPORT verschieben und sichern.  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a>Bereitstellen von Data Mining-Lösungen  
 Die Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], für dir Sie die Projektmappe bereitstellen, muss in einem Modus ausgeführt werden, der mehrdimensionale Objekte und Data Mining-Objekte unterstützt. Sie können daher Data Mining-Objekte nicht in einer Instanz bereitstellen, die tabellarische Modelle oder PowerPivot-Daten hostet.  
  
 Wenn Sie in Visual Studio eine Data Mining-Projektmappe erstellen, müssen Sie demzufolge die Vorlage für multidimensionale Projekte bzw. Data Mining-Projekte von Analysis Services **** verwenden.  
  
 Wenn Sie die Projektmappe bereitstellen, werden die für Data Mining verwendeten Objekte in der angegebenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz erstellt, und zwar in einer Datenbank mit dem gleichen Namen wie die Projektmappendatei.  
  
 Weitere Informationen zum Bereitstellen der relationalen und mehrdimensionalen Projektmappen finden Sie unter [Bereitstellen von Data Mining-Projektmappen](deployment-of-data-mining-solutions.md).  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a>Exemplarische Vorgehensweise  
 Bietet eine Übersicht zum Erstellen von Data Mining-Projektmappen mit dem Data Mining-Assistenten.  
  
 [Erstellen einer relationalen Miningstruktur](create-a-relational-mining-structure.md)  
 Erstellen Sie eine Miningstruktur aus relationalen Daten, Textdateien und anderen Quellen, die in einer Datenquellensicht kombiniert werden können.  
  
 [Erstellen einer OLAP-Miningstruktur](create-an-olap-mining-structure.md)  
 Erstellen Sie auf Grundlage von Daten in einem OLAP-Cube eine Miningstruktur. Modelle, die Sie aus OLAP-Daten erstellen, können als Data Mining-Dimension gespeichert werden, oder Sie können den Satz mit Daten und die Modelle als neuen Cube speichern.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Data Mining-Projekte](data-mining-projects.md)  
  
 [Verarbeiten von Data Mining-Objekten](processing-data-mining-objects.md)  
  
 [Verwandte Projekte für Data Mining-Lösungen](data-mining-solutions.md)  
  
 [Bereitstellen von Data Mining-Projektmappen](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a>Verwandte Aufgaben und Themen  
 Nachdem Sie eine grundlegende Data Mining-Projektmappe erstellt haben, einschließlich Datenquellen und einer Miningstruktur, können Sie auf der Projektmappe aufbauen, indem Sie neue Modelle hinzufügen, Modelle testen und vergleichen, Vorhersagen erstellen und mit Teilmengen der Daten experimentieren.  
  
 Weitere Informationen finden Sie unter den folgenden Links:  
  
|Aufgaben|Themen|  
|-----------|------------|  
|Testen Sie die Modelle, die Sie erstellen, überprüfen Sie die Qualität der Trainingsdaten, und erstellen Sie Diagramme, die die Genauigkeit von Data Mining-Modellen darstellen.|[Tests und Überprüfung &#40;Data Mining&#41;](testing-and-validation-data-mining.md)|  
|Trainieren Sie das Modell, indem Sie die Struktur und verwandte Modelle mit Daten auffüllen. Aktualisieren und erweitern Sie Modelle mit neuen Daten.|[Verarbeiten von Data Mining-Objekten](processing-data-mining-objects.md)|  
|Passen Sie durch das Anwenden von Filtern auf die Trainingsdaten, Auswählen eines anderen Algorithmus oder Festlegen von erweiterten Algorithmusparametern ein Miningmodell an.|[Anpassen von Miningmodellen und -strukturen](customize-mining-models-and-structure.md)|  
|Passen Sie ein Miningmodell durch Anwenden von Filtern auf die Daten an, die beim Trainieren des Modus verwendet werden.|[Hinzufügen von Miningmodellen zu einer Struktur &#40;Analysis Services - Data Mining&#41;](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|Aktualisieren und verwalten Sie Data Mining-Projektmappen.|Link TBD|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Tutorials &#40;Analysis Services&#41;](../data-mining-tutorials-analysis-services.md)  
  
  
