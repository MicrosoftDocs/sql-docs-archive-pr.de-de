---
title: Grundlegendes zu MDX-Skripts (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f7638339d8fc366ee384d453f6df683f3bd41f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620611"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>Grundlegendes zu MDX-Skripts (Analysis Services)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]besteht ein MDX-Skript (Multidimensional Expressions) aus einem oder mehreren MDX-Ausdrücken oder -Anweisungen, die einen Cube mit Berechnungen auffüllen.  
  
 In einem MDX-Skript wird der Berechnungsprozess für einen Cube definiert. Ein MDX-Skript wird auch als Teil des Cubes selbst angesehen. Daher bewirkt ein Ändern eines MDX-Skripts, das einem Cube zugeordnet ist, dass der Berechnungsprozess für den Cube sofort geändert wird.  
  
 Um MDX-Skripts zu erstellen, können Sie den Cube-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]verwenden. Weitere Informationen finden Sie unter [Definieren von Zuweisungen und anderen Skriptbefehlen](../define-assignments-and-other-script-commands.md) und [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892)(Einführung in MDX-Skripts in Microsoft SQL Server 2005).  
  
 Informationen zu Leistungsproblemen im Zusammenhang mit MDX-Abfragen und -Berechnungen finden Sie im Abschnitt zur MDX-Optimierung im [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Grundlegendes MDX-Skript &#40;MDX&#41;](the-basic-mdx-script-mdx.md)|Beschreibt ausführlich das grundlegende MDX-Skript (samt dem MDX-Standardskript, das in jedem Cube bereitgestellt wird), und beschreibt, wie MDX-Skripts in einem Cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]im Grundsatz funktionieren.|  
|[Verwalten von Gültigkeitsbereich und Kontext &#40;MDX&#41;](managing-scope-and-context-mdx.md)|Beschreibt, wie die [CALCULATE](/sql/mdx/mdx-scripting-calculate) -Anweisung, die [SCOPE](/sql/mdx/mdx-scripting-scope) -Anweisung und die [This](/sql/mdx/this-mdx) -Funktion dazu verwendet werden, in einem MDX-Skript den Kontext und den Gültigkeitsbereich zu verwalten.|  
|[Verwenden von Variablen und Parametern &#40;MDX&#41;](using-variables-and-parameters-mdx.md)|Beschreibt, wie Variablen und Parameter in einem MDX-Skript verwendet werden.|  
|[Fehlerbehandlung &#40;MDX&#41;](error-handling-mdx.md)|Erläutert die Fehlerbehandlung innerhalb eines MDX-Skripts.|  
|[Unterstütztes MDX &#40;MDX&#41;](supported-mdx-mdx.md)|Stellt eine Liste der MDX-Operatoren, -Anweisungen und -Funktionen bereit, die in einem MDX-Skript unterstützt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Sprachreferenz &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
