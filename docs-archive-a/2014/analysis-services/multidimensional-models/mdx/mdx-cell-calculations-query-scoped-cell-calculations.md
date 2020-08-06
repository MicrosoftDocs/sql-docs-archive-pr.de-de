---
title: Erstellen von Zellen Berechnungen im Bereich einer Abfrage (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a9c9d529bfeb26b959b2521e4ce3c3d7f10d082
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725073"
---
# <a name="creating-query-scoped-cell-calculations-mdx"></a>Erstellen von Zellenberechnungen im Bereich einer Abfrage (MDX)
  Sie verwenden in MDX (Multidimensional Expressions) das `WITH`-Schlüsselwort dazu, berechnete Zellen im Kontext einer Abfrage zu beschreiben. Das `WITH`-Schlüsselwort hat die folgende Syntax:  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 Der `CellCalc_Identifier` -Wert ist der Name der berechneten Zellen. Der `String_Expression` -Wert enthält eine Liste aus orthogonalen, eindimensionalen MDX-Mengenausdrücken. Für jeden dieser Mengenausdrücke gilt, dass sein Wert zu einer der Kategorien gehören muss, die in der folgenden Tabelle aufgeführt sind.  
  
|Category|BESCHREIBUNG|  
|--------------|-----------------|  
|Leere Menge|Ein MDX-Mengenausdruck, der zu einer leeren Menge aufgelöst wird. In diesem Fall ist der Gültigkeitsbereich der berechneten Zelle gleich dem gesamten Cube.|  
|Menge mit einem einzelnen Element|Ein MDX-Mengenausdruck, der zu einem einzelnen Element aufgelöst wird.|  
|Menge von Ebenenelementen|Ein MDX-Mengenausdruck, der zu den Elementen einer einzelnen Ebene aufgelöst wird. Ein Beispiel für einen solchen Mengen Ausdruck ist die *Level_Expression*.`Members` MDX-Funktion. Um berechnete Elemente einzuschließen, verwenden Sie die *Level_Expression*.`AllMembers` MDX-Funktion. Weitere Informationen finden Sie unter [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).|  
|Menge nachfolgender Werte|Ein MDX-Mengenausdruck, der zu den nachfolgenden Werten eines angegebenen Elements aufgelöst wird. Ein Beispiel für einen solchen Mengen Ausdruck ist die `Descendants` MDX-Funktion (*Member_Expression*, *Level_Expresion* *Desc_Flag*). Weitere Informationen finden Sie unter [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).|  
  
 Wenn das `String_Expression` -Argument eine Dimension nicht beschreibt, nimmt MDX an, dass alle Elemente beim Erstellen des Berechnungsteilcubes eingeschlossen werden. Daher gilt die Definition berechneter Zellen für den gesamten Cube, wenn das `String_Expression` -Argument den Wert NULL hat.  
  
 Das `MDX_Expression` -Argument enthält einen MDX-Ausdruck, der zu einem Zellwert für alle im `String_Expression` -Argument definierten Zellen ausgewertet wird.  
  
## <a name="additional-considerations"></a>Weitere Überlegungen  
 MDX verarbeitet die in der `CONDITION`-Eigenschaft angegebene Berechnungsbedingung nur einmal. Diese einmalige Verarbeitung verbessert die Leistung bei der Auswertung mehrerer Definitionen berechneter Zellen. Dies gilt insbesondere, wenn berechnete Zellen in Cubedurchläufen überlappen.  
  
 Wann diese einmalige Verarbeitung erfolgt, hängt davon ab, für welchen Gültigkeitsbereich die Definition der berechneten Zellen erstellt wurde:  
  
-   Wurde sie im globalen Gültigkeitsbereich als Teil eines Cubes erstellt, verarbeitet MDX die Berechnungsbedingung, wenn der Cube verarbeitet wird. Wenn Zellen in dem Cube geändert werden und die Zellen im Berechnungsteilcube einer Definition berechneter Zellen enthalten sind, ist die Berechnungsbedingung möglicherweise fehlerhaft, bis der Cube erneut verarbeitet wird. Änderungen an Zellen können sich z. B. aus Rückschreibevorgängen ergeben. Die Berechnungsbedingung wird bei der erneuten Verarbeitung des Cubes erneut verarbeitet.  
  
-   Wenn die Berechnungsbedingung im Gültigkeitsbereich einer Sitzung erstellt wurde, wird sie von MDX verarbeitet, wenn die Anweisung während der Sitzung ausgegeben wird. Genauso wie bei im globalen Gültigkeitsbereich erstellten Definitionen berechneter Zellen gilt bei einer Änderung von Zellen, dass die Berechnungsbedingung möglicherweise für die Definition berechneter Zellen fehlerhaft ist.  
  
-   Wenn die Berechnungsbedingung im Gültigkeitsbereich einer Abfrage erstellt wurde, wird sie von MDX verarbeitet, wenn die Abfrage ausgeführt wird. Hier tritt ebenfalls das Problem der Zellenänderungen auf, obwohl Probleme der Datenlatenzzeit minimal sind, da die Verarbeitungszeit bei der Ausführung einer MDX-Abfrage sehr kurz ist.  
  
 Andererseits verarbeitet MDX die Berechnungsformel immer dann, wenn eine MDX-Abfrage für den Cube ausgegeben wird, bei der Zellen aus der Definition berechneter Zellen betroffen sind. Diese Verarbeitung erfolgt unabhängig vom Gültigkeitsbereich bei der Erstellung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE CELL CALCULATION-Anweisung &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
  
