---
title: Hinzufügen oder Löschen einer benutzerdefinierten Hierarchie | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20404a1d93d57221eb830366392eb90600f26c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619392"
---
# <a name="add-or-delete-a-user-defined-hierarchy"></a>Hinzufügen oder Löschen einer benutzerdefinierten Hierarchie
  Zum Hinzufügen oder Entfernen einer benutzerdefinierten Hierarchie zu bzw. aus einer Dimension verwenden Sie die Registerkarte **Dimensionsstruktur** im Dimensions-Designer von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Wenn Sie eine benutzerdefinierte Hierarchie hinzufügen, steht diese den Benutzern erst dann zur Verfügung, wenn sie in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz instanziiert und die Dimension verarbeitet wurde. Weitere Informationen finden Sie unter mehr [dimensionale Modell Datenbanken &#40;SSAS&#41;](multidimensional-model-databases-ssas.md) und mehr [dimensionale Modell Objekt Verarbeitung](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a>So fügen Sie einer Dimension eine benutzerdefinierte Hierarchie hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das entsprechende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt und danach die Dimension, mit der Sie arbeiten möchten.  
  
     Die Dimension wird im Dimensions-Designer auf der Registerkarte **Dimensionsstruktur** geöffnet.  
  
2.  Ziehen Sie das Attribut, das Sie in der benutzerdefinierten Hierarchie verwenden möchten, aus dem Bereich **Attribute** in den Bereich **Hierarchien** .  
  
3.  Ziehen Sie zusätzliche Attribute in den Bereich, um Ebenen in der benutzerdefinierten Hierarchie zu bilden.  
  
     Die Reihenfolge, in der Attribute in der Hierarchie aufgeführt sind, spielt eine wichtige Rolle. Beispielsweise sollten in einer Zeithierarchie Jahre in der Hierarchieliste höher angezeigt werden als Tage.  
  
4.  Wahlweise können Sie die Ebenen in der benutzerdefinierten Hierarchie auch neu anordnen, indem Sie sie an die jeweils gewünschte Position ziehen.  
  
5.  Sie haben auch die Möglichkeit, Eigenschaften der benutzerdefinierten Hierarchie oder deren Ebenen zu ändern.  
  
     So empfiehlt es sich beispielsweise, einen Namen für die benutzerdefinierte Hierarchie anzugeben, eine oder mehrere Ebenen umzubenennen und einen benutzerdefinierten Namen für die Alle-Ebene zu definieren. Weitere Informationen finden Sie unter [Eigenschaften der Benutzer Hierarchie und Eigenschaften](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)von [Ebenen &#91;&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).  
  
    > [!NOTE]  
    >  Standardmäßig ist eine benutzerdefinierte Hierarchie lediglich ein Pfad, in dem Benutzer nach Informationen suchen können. Wenn jedoch Beziehungen zwischen Ebenen vorhanden sind, können Sie die Abfrageleistung verbessern, indem Sie Attributbeziehungen zwischen Ebenen konfigurieren. Weitere Informationen finden Sie unter [Attributbeziehungen](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) und [Definieren von Attributbeziehungen](attribute-relationships-define.md).  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a>So entfernen Sie eine benutzerdefinierte Hierarchie aus einer Dimension  
  
-   Klicken Sie auf der Registerkarte **Dimensionsstruktur** im Bereich **Hierarchien** auf die benutzerdefinierte Hierarchie, die Sie entfernen möchten. Klicken Sie auf der Symbolleiste auf **Löschen**.  
  
     - ODER  
  
-   Klicken Sie im Bereich **Hierarchien** mit der rechten Maustaste auf die benutzerdefinierte Hierarchie, die Sie entfernen möchten, und klicken Sie anschließend auf **Löschen**.  
  
     - ODER  
  
-   Ziehen Sie die benutzerdefinierte Hierarchie von der Entwurfsoberfläche weg.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzer Hierarchien](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Erstellen von benutzerdefinierten Hierarchien](user-defined-hierarchies-create.md)  
  
  
