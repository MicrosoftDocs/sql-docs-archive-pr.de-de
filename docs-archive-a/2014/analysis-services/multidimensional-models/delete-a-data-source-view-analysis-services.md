---
title: Löschen einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
ms.openlocfilehash: 24b587e8d8961161ea803915c31d117c11f7cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622250"
---
# <a name="delete-a-data-source-view-analysis-services"></a>Löschen einer Datenquellensicht (Analysis Services)
  Wenn Sie in einem OLAP-Projekt eine Datenquellensicht (Data Source View, DSV) nicht mehr verwenden, können Sie sie aus dem Projekt in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]löschen.  
  
 Das Löschen einer DSV kann nicht rückgängig gemacht werden. Eine gelöschte DSV kann in einem Projekt oder einer Datenbank von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht wiederhergestellt werden.  
  
 DSVs, von denen andere Objekte abhängen, können nicht aus einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank gelöscht werden, die von [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] im Onlinemodus geöffnet wurde. Um eine DSV aus einem Projekt zu löschen, das mit einer auf einem Server ausgeführten Datenbank verbunden ist, müssen Sie zuerst alle von der DSV abhängigen Objekte in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank löschen, bevor Sie die DSV selbst löschen können.  
  
 Durch das Löschen einer DSV werden andere [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte, die davon abhängig sind, ungültig. Aus diesem Grund wird vor dem Löschen der DSV die Liste der Objekte angezeigt, die durch das Entfernen der DSV ungültig werden. Überprüfen Sie die Liste sorgfältig, um sicherzustellen, dass keine Objekte enthalten sind, die Sie weiterhin verwenden möchten.  
  
 ![Objekte löschen (Dialogfeld)](../media/ssas-olapdsv-deleteobjects.gif "Objekte löschen (Dialogfeld)")  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen Sichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Ändern von Eigenschaften in einer Datenquellensicht &#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md)  
  
  
