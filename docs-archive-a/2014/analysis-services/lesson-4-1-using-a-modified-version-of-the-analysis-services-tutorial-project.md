---
title: Verwenden einer geänderten Version des Analysis Services Tutorial-Projekts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
author: minewiskan
ms.author: owend
ms.openlocfilehash: b833a05a567f37443cf89f7356a0855e0827ea73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619424"
---
# <a name="using-a-modified-version-of-the-analysis-services-tutorial-project"></a>Verwenden einer geänderten Version des Analysis Services Tutorial-Projekts
  Die verbleibenden Lektionen in diesem Lernprogramm basieren auf einer erweiterten Version des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekts, das Sie in den ersten drei Lektionen abgeschlossen haben. Zusätzliche Tabellen und benannte Berechnungen wurden der **Adventure Works DW 2012** -Datenquellensicht hinzugefügt, zusätzliche Dimensionen wurden dem Projekt hinzugefügt, und diese neuen Dimensionen wurden dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube hinzugefügt. Außerdem wurde eine zweite Measuregruppe, die Measures aus einer zweiten Faktentabelle enthält, hinzugefügt. Mithilfe dieses erweiterten Projekts können Sie lernen, wie Sie Ihrer Business Intelligence-Anwendung Funktionalität hinzufügen können, ohne dass Sie bereits durchgeführte Lernschritte wiederholen müssen.  
  
 Bevor Sie dieses Lernprogramm fortsetzen können, müssen Sie die erweiterte Version des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekts herunterladen, extrahieren, laden und verarbeiten.  Überprüfen Sie anhand der Anweisungen in dieser Lektion, ob alle Schritte ausgeführt wurden.  
  
## <a name="downloading-and-extracting-the-project-file"></a>Herunterladen und Extrahieren der Projektdatei  
  
1.  [Klicken Sie hier](https://go.microsoft.com/fwlink/?LinkID=221866) , um die Downloadseite mit Beispielprojekten für dieses Lernprogramm aufzurufen. Die Lernprogrammprojekte sind im Download **Analysis Services Tutorial SQL Server 2012** enthalten.  
  
2.  Klicken Sie auf **Analysis Services Tutorial SQL Server 2012** , um das Paket herunterzuladen, in dem die Projekte für dieses Lernprogramm enthalten sind.  
  
     Standardmäßig wird eine ZIP-Datei im Ordner Downloads gespeichert. Sie müssen die ZIP-Datei an einen Ort mit einem kürzeren Pfadnamen verschieben (erstellen Sie z. B. einen Ordner C:\Tutorials, um die Dateien zu speichern).  Anschließend können Sie die in der ZIP-Datei enthaltenen Dateien extrahieren. Wenn Sie versuchen, die Dateien aus dem Ordner Downloads zu entzippen, der über einen längeren Pfad verfügt, wird nur Lektion 1 extrahiert.  
  
3.  Erstellen Sie einen Unterordner auf oder nahe dem Stammlaufwerk, z. B. C:\Tutorial.  
  
4.  Verschieben Sie die Datei **Analysis Services Tutorial SQL Server 2012.zip** in den Unterordner.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Alle extrahieren**aus.  
  
6.  Navigieren Sie zum Ordner **Lesson 4 Start** , und suchen Sie die Datei **Analysis Services Tutorial.sln** .  
  
## <a name="loading-and-processing-the-enhanced-project"></a>Laden und Verarbeiten des erweiterten Projekts  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Klicken Sie in im Menü **Datei** auf Projekt Mappe **Schließen** , um Dateien zu schließen, die Sie nicht verwenden.  
  
2.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie anschließend auf **Projekt/Projektmappe**.  
  
3.  Wechseln Sie zu dem Ort, an dem die Dateien des Lernprogrammprojekts extrahiert wurden.  
  
     Suchen Sie den Ordner **Lesson 4 Start**, und doppelklicken Sie auf Analysis Services Tutorial.sln.  
  
4.  Stellen Sie die erweiterte Version des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekts für die lokale Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]oder für eine andere Instanz bereit, und überprüfen Sie, ob die Verarbeitung erfolgreich abgeschlossen wird.  
  
## <a name="understanding-the-enhancements-to-the-project"></a>Grundlegendes zu den Erweiterungen am Projekt  
 Die erweiterte Version des Projekts unterscheidet sich von der Version des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekts, das Sie in den ersten drei Lektionen abgeschlossen haben. Die Unterschiede werden in den folgenden Abschnitten beschrieben. Lesen Sie diese Informationen durch, bevor Sie die verbleibenden Lektionen in dem Lernprogramm fortsetzen.  
  
### <a name="data-source-view"></a>Datenquellensicht  
 Die Datenquellensicht im erweiterten Projekt enthält eine zusätzliche Faktentabelle und vier zusätzliche Dimensionstabellen aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Beachten Sie, dass das Diagramm \<All Tables> mit zehn Tabellen in der Datenquellensicht überfüllt wird. Dadurch wird das Verständnis der Beziehungen zwischen den Tabellen und die Suche nach bestimmten Tabellen erschwert. Die Tabellen sind in zwei logischen Diagrammen organisiert – das **Internet Sales** - und das **Reseller Sales** -Diagramm, um dieses Problem zu lösen. Diese Diagramme sind jeweils um eine einzelne Faktentabelle herum organisiert. Mithilfe von logischen Diagrammen können Sie eine bestimmte Untermenge der Tabellen in einer Datenquellensicht anzeigen und damit arbeiten, statt immer alle Tabellen und deren Beziehungen in einem einzigen Diagramm anzuzeigen.  
  
#### <a name="internet-sales-diagram"></a>Internet Sales-Diagramm  
 Das **Internet Sales** -Diagramm enthält die Tabellen, die mit dem Verkauf von [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] -Produkten direkt an Kunden über das Internet verknüpft sind. Bei den Tabellen im Diagramm handelt es sich um die vier Dimensionstabellen und eine Faktentabelle, die Sie in Lektion 1 der **Adventure Works DW 2012** -Datenquellensicht hinzugefügt haben. Nachfolgend sind diese Tabellen aufgeführt:  
  
-   **Geografie**  
  
-   **Customer**  
  
-   **Datum**  
  
-   **Produkt**  
  
-   **InternetSales**  
  
#### <a name="reseller-sales-diagram"></a>Reseller Sales-Diagramm  
 Das **Reseller Sales** -Diagramm enthält die Tabellen, die mit dem Verkauf von [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] -Produkten durch Wiederverkäufer verknüpft sind. Dieses Diagramm enthält die folgenden sieben Dimensionstabellen und eine Faktentabelle aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank:  
  
-   **Reseller**  
  
-   **Promotion**  
  
-   **SalesTerritory**  
  
-   **Geografie**  
  
-   **Datum**  
  
-   **Produkt**  
  
-   **Mitarbeiter**  
  
-   **ResellerSales**  
  
 Beachten Sie, dass die Tabellen **DimGeography**, **DimDate**und **DimProduct** sowohl im **Internet Sales** -Diagramm als auch im **Reseller Sales** -Diagramm verwendet werden. Dimensionstabellen können mit mehreren Faktentabellen verknüpft werden.  
  
### <a name="database-and-cube-dimensions"></a>Datenbank- und Cubedimensionen  
 Das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Projekt enthält fünf neue Datenbankdimensionen, und der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube enthält diese gleichen fünf Dimensionen als Cubedimensionen. Diese Dimensionen wurden definiert, um Benutzerhierarchien und Attribute bereitzustellen, die mithilfe von benannten Berechnungen, zusammengesetzten Elementschlüsseln und Anzeigeordnern geändert wurden. Die neuen Dimensionen werden in der folgenden Liste beschrieben.  
  
 Reseller-Dimension  
 Die Reseller-Dimension basiert auf der **Reseller** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
 Promotion-Dimension  
 Die Promotion-Dimension basiert auf der **Promotion** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
 Sales Territory-Dimension  
 Die Sales Territory-Dimension basiert auf der **SalesTerritory** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
 Employee-Dimension  
 Die Employee-Dimension basiert auf der **Employee** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
 Geography-Dimension  
 Die Geography-Dimension basiert auf der **Geography** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
#### <a name="analysis-services-cube"></a>Analysis Services-Cube  
 Der **Analysis Services Tutorial** -Cube enthält jetzt zwei Measuregruppen – die ursprüngliche Measuregruppe basierend auf der **InternetSales** -Tabelle und eine zweite Measuregruppe basierend auf der **ResellerSales** -Tabelle in der **Adventure Works DW 2012** -Datenquellensicht.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Definieren der Eigenschaften des übergeordneten Attributs in einer Über-/Unterordnungshierarchie](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md) 
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen eines Analysis Services-Projekts](lesson-2-5-deploying-an-analysis-services-project.md)  
  
  
