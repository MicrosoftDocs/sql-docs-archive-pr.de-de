---
title: Aufbauen von Teilcubes in MDX (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
author: minewiskan
ms.author: owend
ms.openlocfilehash: 653b4d30aa86f52179c7b13619ac4347aa65c339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619415"
---
# <a name="building-subcubes-in-mdx-mdx"></a>Erstellen von Teilcubes in MDX (MDX)
  Ein Teilcube ist eine Teilmenge eines Cubes, die einer gefilterten Sicht der zugrunde liegenden Daten entspricht. Durch Begrenzen des Cubes auf einen Teilcube können Sie die Abfrageleistung verbessern.  
  
 Zum Definieren eines Teilcubes verwenden Sie die in diesem Thema beschriebene [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) -Anweisung.  
  
## <a name="create-subcube-syntax"></a>Syntax von CREATE SUBCUBE  
 Verwenden Sie die folgende Syntax, um einen Teilcube zu erstellen:  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 Die Syntax von CREATE SUBCUBE ist recht einfach. Der *Subcube_Identifier* -Parameter gibt den Cube an, auf dem der Teilcube basieren soll. Der *Subcube_Expression* -Parameter wählt den Teil des Cubes aus, der zum Teilcube werden soll.  
  
 Nachdem Sie einen Teilcube erstellt haben, wird dieser Teilcube so lange der Kontext für alle MDX-Abfragen, bis Sie die Sitzung geschlossen oder die [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) -Anweisung ausgeführt haben.  
  
### <a name="what-a-subcube-contains"></a>Inhalt eines Teilcubes  
 Obwohl die CREATE SUBCUBE-Anweisung recht einfach zu verwenden ist, zeigt die Anweisung selbst nicht explizit alle Elemente, die Bestandteil eines Teilcubes werden. Für das Definieren eines Teilcubes gelten folgende Regeln:  
  
-   Wenn Sie das `(All)`-Element einer Hierarchie einfügen, fügen Sie jedes Element dieser Hierarchie ein.  
  
-   Wenn Sie ein Element einfügen, fügen Sie auch die Vorgänger und Nachfolger dieses Elements ein.  
  
-   Wenn Sie jedes Element einer Ebene einfügen, fügen Sie alle Elemente aus der Hierarchie ein. Elemente aus anderen Hierarchien werden ausgeschlossen, wenn diese Elemente keine Elemente auf der Ebene haben (beispielsweise eine unausgeglichene Hierarchie: etwa eine Stadt, für die es keine Kunden gibt).  
  
-   Ein Teilcube enthält immer jedes `(All)`-Element aus dem Cube.  
  
 Aggregatwerte im Teilcube werden visuell summiert. Ein Teilcube enthält beispielsweise `USA`, `WA`und `OR`. Der Aggregatwert für `USA` ist die Summe aus `{WA,OR}` , weil `WA` und `OR` die einzigen Staaten sind, die durch den Teilcube definiert sind. Alle anderen Staaten werden ignoriert.  
  
 Explizite Verweise auf Zellen, die sich außerhalb des Teilcubes befinden, geben Zellwerte zurück, die im Kontext des gesamten Cubes ausgewertet wurden. Beispielsweise erstellen Sie einen Teilcube, der auf das aktuelle Jahr beschränkt ist. Sie verwenden dann die [ParallelPeriod](/sql/mdx/parallelperiod-mdx) -Funktion, um das aktuelle Jahr mit dem vorherigen Jahr zu vergleichen. Der Unterschied in den Werten wird zurückgegeben, obwohl der Wert des vorherigen Jahres außerhalb des Teilcubes liegt.  
  
 Wenn der ursprüngliche Kontext nicht überschrieben wurde, werden SET-Funktionen, die in einer untergeordneten SELECT-Anweisung ausgewertet werden, im Kontext dieser Anweisung ausgewertet. Wurde der Kontext überschrieben, werden SET-Funktionen im Kontext des gesamten Cubes ausgewertet.  
  
## <a name="create-subcube-example"></a>Beispiel zu CREATE SUBCUBE  
 Im folgenden Beispiel wird ein Teilcube erstellt, der den Budget-Cube auf die Konten 4200 und 4300 beschränkt:  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 Nachdem für die Sitzung ein Teilcube erstellt wurde, werden alle weiteren Abfragen nicht mehr für den gesamten Cube, sondern nur noch für den Teilcube ausgeführt. Sie führen beispielsweise die folgende Abfrage aus. Diese Abfrage gibt nur Elemente von den Konten 4200 und 4300 zurück.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten des Cubekontexts in einer Abfrage &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
