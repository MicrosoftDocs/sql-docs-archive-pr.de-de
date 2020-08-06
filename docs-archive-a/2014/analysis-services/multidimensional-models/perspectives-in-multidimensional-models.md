---
title: Perspektiven in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- hiding objects from perspective
- renaming perspectives
- attributes [Analysis Services], default members
- removing perspectives
- perspectives [Analysis Services]
- names [Analysis Services], perspectives
- cubes [Analysis Services], perspectives
- deleting perspectives
ms.assetid: 5a3d6577-6833-4c24-820c-b65bb856157b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2d4be87ddbd691710b361d8b07d225bce37659fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615650"
---
# <a name="perspectives-in-multidimensional-models"></a>Perspektiven in mehrdimensionalen Modellen
  Bei einer Perspektive handelt es sich um eine für eine bestimmte Anwendung oder Benutzergruppe erstellte Teilmenge eines Cubes. Der Cube selbst stellt die Standardperspektive dar. Eine Perspektive wird auf einem Client als Cube verfügbar gemacht. Wenn ein Benutzer eine Perspektive anzeigt, wird diese wie ein weiterer Cube angezeigt. Alle Änderungen, die an den Cubedaten durch Rückschreibevorgänge in der Perspektive vorgenommen wurden, erfolgen am Originalcube. Weitere Informationen zu den in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]enthaltenen Sichten finden Sie unter [Perspektiven](../multidimensional-models-olap-logical-cube-objects/perspectives.md).  
  
 Verwenden Sie im Cube-Designer die Registerkarte **Perspektiven** , um Perspektiven in einem Cube zu erstellen oder zu ändern. Die erste Spalte der Registerkarte **Perspektiven** ist die Spalte **Cubeobjekte** , in der alle Objekte des Cubes aufgelistet sind. Diese Spalte entspricht der Standardperspektive des Cubes, mit der der Cube selbst dargestellt wird.  
  
## <a name="creating-or-deleting-perspectives"></a>Erstellen oder Löschen von Perspektiven  
 Sie können der Registerkarte **Perspektiven** eine Perspektive hinzufügen, indem Sie im Menü **Cube** auf **Neue Perspektive** klicken. Klicken Sie alternativ auf der Symbolleiste auf die Schaltfläche **Neue Perspektive** oder mit der rechten Maustaste auf eine beliebige Stelle im Bereich und dann im Kontextmenü auf **Neue Perspektive** . Sie können einem Cube eine beliebige Anzahl von Perspektiven hinzufügen.  
  
 Klicken Sie zum Entfernen einer Perspektive zunächst auf eine beliebige Zelle in der Spalte der zu löschenden Perspektive. Klicken Sie dann im Menü **Cube** auf **Perspektive löschen**. Klicken Sie alternativ auf der Symbolleiste auf die Schaltfläche **Perspektive löschen** oder mit der rechten Maustaste auf eine beliebige Zelle der zu löschenden Perspektive und dann im Kontextmenü auf **Perspektive löschen** .  
  
## <a name="renaming-perspectives"></a>Umbenennen von Perspektiven  
 In der ersten Zeile der jeweiligen Perspektive wird der Name der Perspektive angezeigt. Beim Erstellen einer Perspektive lautet der Name zunächst Perspektive (gefolgt von der Ordnungszahl, beginnend mit 1, falls eine Perspektive mit dem Namen Perspektive bereits vorhanden ist). Sie können auf den Namen klicken, um ihn zu bearbeiten.  
  
## <a name="hiding-objects-from-a-perspective"></a>Ausblenden von Objekten aus einer Perspektive  
 Deaktivieren Sie zum Ausblenden eines Objekts aus einer Perspektive das Kontrollkästchen in der Zeile, die dem Objekt in der Spalte der Perspektive entspricht. Die Cubeobjekte, die aus einer Perspektive ausgeblendet werden können, sind die folgenden:  
  
-   Measuregruppen  
  
-   Measures  
  
-   Dimensionen  
  
-   Hierarchien  
  
-   Benannte Mengen  
  
-   KPIs  
  
-   Aktionen  
  
-   Berechnete Elemente  
  
 Erweitern Sie zum Anzeigen eines Objekts die Kategorie (**Measuregruppen**, **Dimensionen**, **KPIs**, **Berechnungen**oder **Aktionen**) für einen beliebigen Objekttyp unter **Cubeobjekte**. Erweitern Sie zunächst eine Dimension, und erweitern Sie dann die Zeile **Hierarchien** , um die Hierarchien einer Dimension anzuzeigen, oder die Zeile **Attribute** , um die Attribute einer Dimension anzuzeigen. Erweitern Sie die Measuregruppe, um die in einer Measuregruppe enthaltenen Measures anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cubes in mehrdimensionalen Modellen](cubes-in-multidimensional-models.md)  
  
  
