---
title: Syntax (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], syntax
- syntax [Integration Services]
ms.assetid: 61c053c5-1182-4ad0-b804-51cbd19aa0ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7be12ee5e0467e3789fbe2771d881d9ae3f25f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701354"
---
# <a name="syntax-ssis"></a>Syntax (SSIS)
  Die Ausdruckssyntax von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ähnelt der von den Sprachen C und C# verwendeten Syntax. Ausdrücke schließen Elemente ein, wie z. B. Bezeichner (Spalten und Variablen), Literale, Operatoren und Funktionen. Dieses Thema enthält eine Zusammenfassung der speziellen Anforderungen der Ausdrucksauswertungssyntax für die verschiedenen Ausdruckselemente.  
  
> [!NOTE]  
>  In vorherigen Versionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]galt eine maximale Zeichenlänge von 4000 Zeichen für das Auswertungsergebnis eines Ausdrucks, wenn das Ergebnis vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentyp DT_WSTR oder DT_STR war. Diese Begrenzung wurde aufgehoben.  
  
 Beispielausdrücke, in denen bestimmte Operatoren und Funktionen verwendet werden, finden Sie in den Themen zu den einzelnen Operatoren und Funktionen unter [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md) und [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md).  
  
 Beispielausdrücke, in denen mehrere Operatoren und Funktionen sowie Bezeichner und Literale verwendet werden, finden Sie unter [Beispiele für erweiterte SQL Server Integration Services-Ausdrücke](examples-of-advanced-integration-services-expressions.md).  
  
 Beispielausdrücke zur Verwendung in Eigenschaftsausdrücken finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](use-property-expressions-in-packages.md).  
  
## <a name="identifiers"></a>Bezeichner  
 Ausdrücke können Spalten- und Variablenbezeichner einschließen. Die Spalten können aus der Datenquelle stammen oder mithilfe von Transformationen im Datenfluss erstellt werden. In Ausdrücken kann mit Herkunftsbezeichnern auf Spalten verwiesen werden. Bei Herkunftsbezeichnern handelt es sich um Zahlen, mit denen Paketelemente eindeutig identifiziert werden. Wenn in Ausdrücken auf Herkunftsbezeichner verwiesen wird, muss das Nummernzeichen (#) verwendet werden. Beispielsweise wird auf den Herkunftsbezeichner 138 mit #138 verwiesen.  
  
 Ausdrücke können Systemvariablen von [!INCLUDE[ssIS](../../includes/ssis-md.md)] sowie benutzerdefinierte Variablen einschließen. Wenn in Ausdrücken auf Variablen verwiesen wird, muss das \@-Präfix verwendet werden. Beispielsweise wird auf die `Counter`-Variable mit \@Counter verwiesen. Das Zeichen \@ ist nicht Bestandteil des Variablennamens, sondern zeigt der Ausdrucksauswertung nur an, dass der Bezeichner eine Variable ist. Weitere Informationen finden Sie unter [Bezeichner &#40;SSIS&#41;](identifiers-ssis.md).  
  
## <a name="literals"></a>Literale  
 Ausdrücke können numerische und boolesche Literale sowie Zeichenfolgenliterale einschließen. Zeichenfolgenliterale müssen in Ausdrücken in Anführungszeichen eingeschlossen werden. Für numerische und boolesche Literale werden keine Anführungszeichen verwendet. Die Ausdruckssprache beinhaltet Escapesequenzen für für häufig verwendete Escapezeichen. Weitere Informationen finden Sie unter [Literale &#40;SSIS&#41;](numeric-string-and-boolean-literals.md).  
  
## <a name="operators"></a>Operatoren  
 Die Ausdrucksauswertung stellt eine Reihe von Operatoren bereit, die eine ähnliche Funktionalität wie die Operatoren in Sprachen, wie z. B. Transact-SQL, C++ und C#, aufweisen. Die Ausdruckssprache enthält jedoch zusätzliche Operatoren und verwendet andere Symbole, mit denen Sie möglicherweise nicht vertraut sind. Weitere Informationen finden Sie unter [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md).  
  
### <a name="namespace-resolution-operator"></a>Namespaceauflösungsoperator  
 In Ausdrücken wird mit dem Namespaceauflösungsoperator (::) die Mehrdeutigkeit von gleichnamigen Variablen vermieden. Mit dem Namespaceauflösungsoperator können Sie die Variable mit ihrem Namespace qualifizieren. Dadurch können mehrere gleichnamige Variablen in demselben Paket verwendet werden.  
  
#### <a name="cast-operator"></a>Umwandlungsoperator  
 Der Umwandlungsoperator konvertiert Ausdrucksergebnisse, Spaltenwerte, Variablenwerte und Konstanten in einen anderen Datentyp. Der Umwandlungsoperator der Ausdruckssprache ist mit dem Umwandlungsoperator in den Programmiersprachen C und C# zu vergleichen. In Transact-SQL stellen die Funktionen CAST und CONVERT diese Funktionalität bereit. Die Syntax des Umwandlungsoperators unterscheidet sich gegenüber CAST und CONVERT folgendermaßen:  
  
-   Ein Ausdruck kann als Argument verwendet werden.  
  
-   In der Syntax ist das CAST-Schlüsselwort nicht eingeschlossen.  
  
-   In der Syntax ist das AS-Schlüsselwort nicht eingeschlossen.  
  
##### <a name="conditional-operator"></a>Bedingungsoperator  
 Der Bedingungsoperator gibt einen von zwei Ausdrücken basierend auf der Auswertung eines booleschen Ausdrucks zurück. Der Bedingungsoperator der Ausdruckssprache ist mit dem Bedingungsoperator in den Programmiersprachen C und C# zu vergleichen. In mehrdimensionalen Ausdrücken (MDX, Multidimensional Expressions) stellt die IIF-Funktion eine ähnliche Funktionalität bereit.  
  
###### <a name="logical-operators"></a>Logische Operatoren  
 Die Ausdruckssprache unterstützt das Zeichen ! für den logischen NOT-Operator. In Transact-SQL ist der !- Operator in die relationalen Operatoren integriert. Beispielsweise enthält Transact-SQL die Operatoren > und !>. Die Kombination des !-Operators mit anderen Operatoren wird von der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Ausdruckssprache nicht unterstützt. Beispielsweise können ! und > nicht zu !> kombiniert werden. Die Ausdruckssprache unterstützt jedoch keine integrierte !=-Zeichenkombination für Ungleich-Vergleiche.  
  
###### <a name="equality-operators"></a>Gleichheitsoperatoren  
 Die Ausdrucksauswertungsgrammatik enthält den Gleichheitsoperator (==). Dieser Operator ist das Äquivalent zum =-Operator in Transact-SQL bzw. zum ==-Operator in C#.  
  
## <a name="functions"></a>Functions  
 Die Ausdruckssprache enthält Datums- und Zeitfunktionen, mathematische Funktionen und Zeichenfolgenfunktionen, die mit Transact-SQL-Funktionen und C#-Methoden vergleichbar sind.  
  
 Einige Funktionen besitzen zwar denselben Namen wie Transact-SQL-Funktionen, weisen jedoch in der Ausdrucksauswertung eine etwas andere Funktionalität auf.  
  
-   In Transact-SQL ersetzt die ISNULL-Funktion NULL-Werte mit einem angegebenen Wert. Die ISNULL-Funktion der Ausdrucksauswertung gibt dagegen einen booleschen Wert zurück, je nachdem, ob ein Ausdruck NULL ist.  
  
-   In Transact-SQL enthält die ROUND-Funktion eine Option zum Abschneiden des Resultsets, während dies bei der ROUND-Funktion in der Ausdrucksauswertung nicht der Fall ist.  
  
 Weitere Informationen finden Sie unter [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Verwenden eines Ausdrucks in einer Datenflusskomponente](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Technischer Artikel, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), auf pragmaticworks.com  
  
-   Technischer Artikel, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), auf social.technet.microsoft.com  
  
  
