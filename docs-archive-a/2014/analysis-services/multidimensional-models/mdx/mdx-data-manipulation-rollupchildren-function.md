---
title: Arbeiten mit der RollupChildren-Funktion (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721921"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a>Arbeiten mit der RollupChildren-Funktion (MDX)
  Die MDX-Funktion (Multidimensional Expressions) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Skript für Search und replace] führt einen Rollup der untergeordneten Elemente eines Members aus, wendet einen anderen unären Operator auf jedes untergeordnete Element an und gibt den Wert dieses Rollups als Zahl zurück. Der unäre Operator kann durch eine Elementeigenschaft des untergeordneten Elements bereitgestellt werden, oder der Operator kann ein Zeichenfolgenausdruck sein, der direkt an die Funktion übergeben wird.  
  
## <a name="rollupchildren-function-examples"></a>Beispiele zur RollupChildren-Funktion  
 Die Verwendung der `RollupChildren`-Funktion in MDX-Anweisungen (Multidimensional Expressions) ist einfach zu erklären, die Funktion kann jedoch weit reichende Folgen für MDX-Abfragen haben.  
  
 Der Einfluss der `RollupChildren`-Funktion wird in MDX-Abfragen ersichtlich, die zum Durchführen einer selektiven Analyse der vorhandenen Cubedaten entworfen wurden. Die folgende Tabelle enthält beispielsweise eine Liste untergeordneter Elemente des übergeordneten Elements Net Sales, wobei die unären Operatoren (die durch die `UNARY_OPERATOR`-Elementeigenschaft dargestellt sind) in Klammern angegeben sind.  
  
|Übergeordnetes Element|Untergeordnetes Element|  
|-------------------|------------------|  
|Nettoumsatz|Domestic Sales (+)<br /><br /> Domestic Returns (-)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (-)|  
  
 Das übergeordnete Element Net Sales stellt derzeit die Gesamtsumme der in- und ausländischen Bruttoumsatzwerte bereit, wobei in- und ausländische Rücknahmen im Rahmen des Rollups subtrahiert werden.  
  
 Sie möchten jedoch eine schnelle und einfache Vorhersage des in- und ausländischen Bruttoumsatzes plus 10 % bereitstellen, wobei die in- und ausländischen Rücknahmen ignoriert werden. Zum Berechnen dieses Wertes können Sie die `RollupChildren`-Funktion auf eine der beiden folgenden Arten verwenden: mit einer benutzerdefinierten Elementeigenschaft oder mit der `IIf`-Funktion.  
  
### <a name="using-a-custom-member-property"></a>Verwenden einer benutzerdefinierten Elementeigenschaft  
 Wenn die Rollupberechnung häufig ausgeführt werden soll, besteht die Möglichkeit, eine Elementeigenschaft zu erstellen, in der der Operator gespeichert ist, der für jedes untergeordnete Element für eine bestimmte Funktion verwendet werden soll. Die folgende Tabelle zeigt gültige unäre Operatoren an und beschreibt das erwartete Ergebnis.  
  
|Operator|Ergebnis|  
|--------------|------------|  
|+|Gesamt = Gesamt + aktuelles untergeordnetes Element|  
|-|Gesamt = Gesamt - aktuelles untergeordnetes Element|  
|*|Gesamt = Gesamt * aktuelles untergeordnetes Element|  
|/|Gesamt = Gesamt / aktuelles untergeordnetes Element|  
|~|Untergeordnetes Element wird im Rollup nicht verwendet. Der Wert des untergeordneten Elements wird ignoriert.|  
  
 Beispielsweise könnte eine Elementeigenschaft mit dem Namen `SALES_OPERATOR` erstellt werden, der folgende unäre Operatoren zugewiesen werden (siehe nächste Tabelle).  
  
|Übergeordnetes Element|Untergeordnetes Element|  
|-------------------|------------------|  
|Nettoumsatz|Domestic Sales (+)<br /><br /> Domestic Returns (~)<br /><br /> Foreign Sales (+)<br /><br /> Foreign Returns (~)|  
  
 Mit dieser neuen Elementeigenschaft führt die folgende MDX-Anweisung die Schätzung des Bruttoumsatzes schnell und effizient aus (wobei in- und ausländische Rücknahmen ignoriert werden):  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 Beim Aufrufen der Funktion wird der Wert jedes untergeordneten Elements mithilfe des Operators, der in der Elementeigenschaft gespeichert ist, auf das Gesamtergebnis angewendet. Die Elemente für in- und ausländische Rücknahmen werden ignoriert, und der von der `RollupChildren`-Funktion zurückgegebene Rollupgesamtwert wird mit 1,1 multipliziert.  
  
### <a name="using-the-iif-function"></a>Verwenden der IIf-Funktion  
 Wenn der Beispiel Vorgang nicht alltäglich ist oder der Vorgang nur auf eine MDX-Abfrage angewendet wird, kann die [IIf](/sql/mdx/iif-mdx) -Funktion mit der-Funktion verwendet werden, `RollupChildren` um dasselbe Ergebnis bereitzustellen. Die folgende MDX-Abfrage stellt dasselbe Ergebnis wie das vorherige MDX-Abfragebeispiel bereit, jedoch ohne die Verwendung einer benutzerdefinierten Elementeigenschaft:  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 Die MDX-Anweisung wertet den unären Operator des untergeordneten Elements aus. Wird der unäre Operator zur Subtraktion verwendet (wie dies bei den Elementen der in- und ausländischen Rücknahmen der Fall ist), wird der unäre Tildeoperator (~) durch die `IIf`-Funktion ersetzt. Andernfalls verwendet die `IIf`-Funktion den unären Operator des untergeordneten Elements. Schließlich wird der zurückgegebene Rollupgesamtwert mit 1,1 multipliziert, um die Vorhersage der in- und ausländischen Bruttoumsätze bereitzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten von Daten &#40;MDX&#41;](mdx-data-manipulation-manipulating-data.md)  
  
  
