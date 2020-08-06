---
title: Abfragen von mehrdimensionalen Daten mit MDX | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b7589a98636e56e8c592cef213785544e18f4ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620608"
---
# <a name="querying-multidimensional-data-with-mdx"></a>Abfragen von mehrdimensionalen Daten mit MDX
  MDX (Multidimensional Expressions) ist die Abfragesprache, die Sie zum Arbeiten mit und zum Abrufen von mehrdimensionalen Daten in verwenden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . MDX basiert auf der XML for Analysis (XMLA)-Spezifikation mit spezifischen Erweiterungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . MDX verwendet Ausdrücke bestehend aus Bezeichnern, Werten, Anweisungen, Funktionen und Operatoren, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zum Abrufen von Objekten (z. B. einer Menge oder einem Element) oder Skalarwerten (z. B. einer Zeichenfolge oder einer Zahl) auswerten kann.  
  
 MDX-Abfragen und-Ausdrücke in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] werden für Folgendes verwendet:  
  
-   Rückgabe von Daten an eine Client Anwendung aus einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Cube.  
  
-   Formatieren von Abfrageergebnissen  
  
-   Ausführen von Cube-Entwurfsaufgaben, wie z. B. Definieren von berechneten Elementen, benannten Mengen, Zuweisungen mit definiertem Bereich oder Key Performance Indicators (KPI)  
  
-   Ausführen von Verwaltungsaufgaben, wie z. B. Dimensions- und Zellensicherheit  
  
 Die MDX-Syntax ist, oberflächlich betrachtet, der SQL-Syntax sehr ähnlich, die normalerweise bei relationalen Datenbanken verwendet wird. MDX ist jedoch keine Erweiterung von SQL und unterscheidet sich in vielerlei Hinsicht von SQL. Um MDX-Ausdrücke zum Entwerfen bzw. Sichern von Cubes oder MDX-Abfragen zum Zurückgeben und Formatieren von mehrdimensionalen Daten erstellen zu können, müssen Sie die grundlegenden Konzepte von MDX und der Dimensionsmodellierung, die MDX-Syntaxelemente, MDX-Operatoren, MDX-Anweisungen sowie MDX-Funktionen verstehen.  
  
> [!NOTE]  
>  Weitere Informationen finden Sie auf der Microsoft TechNet-Website im Abschnitt Weitere Ressourcen auf der Seite [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) . Weitere Informationen zu Leistungsproblemen im Zusammenhang mit MDX-Abfragen und-Berechnungen finden Sie im Abschnitt "Writing Efficient MDX" im [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)|Mithilfe von MDX (Multidimensional Expressions) können Sie mehrdimensionale Daten Abfragen oder MDX-Ausdrücke zur Verwendung in einem Cube erstellen. zuerst sollten Sie jedoch die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Dimensions Konzepte und die Terminologie verstehen.|  
|[Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)|MDX (Multidimensional Expressions) ermöglicht Ihnen das Abfragen von mehrdimensionalen Objekten (z. B. Cubes) sowie das Zurückgeben von mehrdimensionalen Cellsets, die die Daten des jeweiligen Cubes enthalten. Dieses Thema und die zugehörigen Unterthemen bieten eine Übersicht über MDX-Abfragen.|  
|[Grundlegendes zu MDX-Skripts &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] besteht ein MDX-Skript (Multidimensional Expressions) aus einem oder mehreren MDX-Ausdrücken oder-Anweisungen, die einen Cube mit Berechnungen auffüllen.<br /><br /> In einem MDX-Skript wird der Berechnungsprozess für einen Cube definiert. Ein MDX-Skript wird auch als Teil des Cubes selbst angesehen. Daher bewirkt ein Ändern eines MDX-Skripts, das einem Cube zugeordnet ist, dass der Berechnungsprozess für den Cube sofort geändert wird.<br /><br /> Um MDX-Skripts zu erstellen, können Sie den Cube-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]verwenden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Syntax Elemente &#40;MDX-&#41;](/sql/mdx/mdx-syntax-elements-mdx)   
 [MDX-Sprachreferenz &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
