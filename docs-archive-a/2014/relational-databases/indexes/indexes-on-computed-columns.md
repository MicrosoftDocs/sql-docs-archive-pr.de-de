---
title: Indizes in berechneten Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, index creation
- index creation [SQL Server], computed columns
- imprecise columns
- persisted computed columns
- precise [SQL Server]
ms.assetid: 8d17ac9c-f3af-4bbb-9cc1-5cf647e994c4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ecbca9e7838c4c9395a8bcb6e11351c40f7037f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725741"
---
# <a name="indexes-on-computed-columns"></a>Indizes in berechneten Spalten
  Sie können Indizes für berechnete Spalten definieren, sofern die folgenden Anforderungen erfüllt sind:  
  
-   Anforderungen hinsichtlich des Besitzes  
  
-   Anforderungen hinsichtlich des Determinismus  
  
-   Anforderungen hinsichtlich der Präzision  
  
-   Anforderungen hinsichtlich des Datentyps  
  
-   Anforderungen hinsichtlich der SET-Option  
  
 **Ownership Requirements**  
  
 Alle Funktionsverweise in der berechneten Spalte müssen denselben Besitzer wie die Tabelle aufweisen.  
  
 **Determinism Requirements**  
  
> [!IMPORTANT]  
>  Ausdrücke gelten als deterministisch, wenn sie für eine bestimmte Gruppen von Eingaben stets dasselbe Ergebnis zurückgeben. Die **IsDeterministic** -Eigenschaft der [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) -Funktion teilt mit, ob der Ausdruck einer berechneten Spalte ( *computed_column_expression* ) deterministisch ist.  
  
 Der *computed_column_expression* muss deterministisch sein. Ein *computed_column_expression* ist deterministisch, wenn mindestens eine der folgenden Bedingungen zutrifft:  
  
-   Alle Funktionen, auf die der Ausdruck verweist, sind deterministisch und präzise. Zu diesen Funktionen zählen benutzerdefinierte und integrierte Funktionen. Weitere Informationen finden Sie unter [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md). Funktionen können unpräzise sein, wenn die berechnete Spalte als PERSISTED markiert ist. Weitere Informationen finden Sie unter [Erstellen von Indizes für persistente berechnete Spalten](#BKMK_persisted) nachfolgend in diesem Thema.  
  
-   Alle Spalten, auf die der Ausdruck verweist, stammen aus der Tabelle, die die berechnete Spalte enthält.  
  
-   Kein Spaltenverweis ruft Daten aus mehreren Zeilen ab. Beispielsweise hängen Aggregatfunktionen wie SUM oder AVG von Daten aus mehreren Zeilen ab, und ein *computed_column_expression* wäre dadurch nicht deterministisch.  
  
-   Der *computed_column_expression* kann weder auf Systemdaten noch auf Benutzerdaten zugreifen.  
  
 Jede berechnete Spalte, die einen CLR-Ausdruck (Common Language Runtime) enthält, muss deterministisch und als PERSISTED markiert sein, bevor die Spalte indiziert werden kann. Ausdrücke des CLR-benutzerdefinierten Typs sind in den Definitionen berechneter Spalten zulässig. Berechnete Spalten, deren Typ ein CLR-benutzerdefinierter Typ ist, können indiziert werden, sofern der Typ vergleichbar ist. Weitere Informationen finden Sie unter [Benutzerdefinierte CLR-Typen](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
> [!NOTE]  
>  Wenn Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf Zeichenfolgenliterale des Date-Datentyps in indizierten berechneten Spalten verweisen, ist es ratsam, das Literal explizit in den gewünschten Datentyp zu konvertieren, indem Sie ein deterministisches Datenformat verwenden. Eine Liste der deterministischen Datenformatstile finden Sie unter [CAST und CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql). Ausdrücke für die implizierte Konvertierung von Zeichenfolgen in date-Datentypen werden als nicht deterministisch bezeichnet, es sei denn, der Kompatibilitätsgrad der Datenbank ist auf 80 oder niedriger festgelegt. Ursache hierfür ist, dass die Ergebnisse von den [LANGUAGE](/sql/t-sql/statements/set-language-transact-sql) - und [DATEFORMAT](/sql/t-sql/statements/set-dateformat-transact-sql) -Einstellungen der Serversitzung abhängig sind. Die Ergebnisse des Ausdrucks `CONVERT (datetime, '30 listopad 1996', 113)` hängen beispielsweise von der LANGUAGE-Einstellung ab, da die Zeichenfolge '`30 listopad 1996`' für verschiedene Monate in verschiedenen Sprachen steht. In ähnlicher Weise interpretiert `DATEADD(mm,3,'2000-12-01')`in dem Ausdruck [!INCLUDE[ssDE](../../../includes/ssde-md.md)] die Zeichenfolge `'2000-12-01'` basierend auf der DATEFORMAT-Einstellung.  
>   
>  Die implizierte Konvertierung von Nicht-Unicode-Zeichendaten zwischen Sortierungen wird auch als nicht deterministisch erachtet, wenn der Kompatibilitätsgrad nicht auf 80 oder niedriger festgelegt ist.  
>   
>  Beträgt die Einstellung des Kompatibilitätsgrades der Datenbank 90, können Sie keine Indizes für berechnete Spalten erstellen, die diese Ausdrücke enthalten. Vorhandene berechnete Spalten, die diese Ausdrücke aus einer aktualisierten Datenbank enthalten, sind jedoch verwaltbar. Bei Verwendung indizierter berechneter Spalten, die implizite Konvertierungen von Zeichenfolgen in Datumsangaben enthalten, sollten Sie sicherstellen, dass die LANGUAGE- und DATEFORMAT-Einstellungen in der Datenbank und den Anwendungen konsistent sind, um mögliche Beschädigungen der Indizes zu vermeiden.  
  
 **Precision Requirements**  
  
 Der *computed_column_expression* muss präzise sein. Ein *computed_column_expression* ist präzise, wenn mindestens eine der folgenden Bedingungen zutrifft:  
  
-   Es handelt sich um keinen Ausdruck des `float`- oder `real`-Datentyps.  
  
-   In der Definition des Ausdrucks wird kein `float`- oder `real`-Datentyp verwendet. Beispielsweise ist in der folgenden Anweisung die `y`-Spalte vom `int`-Datentyp und deterministisch, aber nicht präzise.  
  
    ```  
    CREATE TABLE t2 (a int, b int, c int, x float,   
       y AS CASE x   
             WHEN 0 THEN a   
             WHEN 1 THEN b   
             ELSE c   
          END);  
    ```  
  
> [!NOTE]  
>  Jeder `float`- oder `real`-Ausdruck gilt als nicht präzise und kann nicht als Schlüssel eines Indexes verwendet werden; ein `float`- oder `real`-Ausdruck kann in einer indizierten Sicht, jedoch nicht als Schlüssel verwendet werden. Dies gilt auch für berechnete Spalten. Jede Funktion, jeder Ausdruck oder jede benutzerdefinierte Funktion gilt als unpräzise, wenn Sie `float`- oder `real`-Ausdrücke enthält. Das gilt auch für logische (Vergleiche).  
  
 Die **IsPrecise** -Eigenschaft der COLUMNPROPERTY-Funktion teilt mit, ob der Ausdruck einer berechneten Spalte ( *computed_column_expression* ) präzise ist.  
  
 **Datentyp Anforderungen**  
  
-   Der *computed_column_expression* , der für die berechnete Spalte definiert ist, kann nicht zu den `text` `ntext` Datentypen, oder ausgewertet werden `image` .  
  
-   Berechnete Spalten, die aus den Datentypen `image`, `ntext`, `text`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` und `xml` abgeleitet wurden, können indiziert werden, solange der Datentyp der berechneten Spalte als Indexschlüsselspalte zulässig ist.  
  
-   Berechnete Spalten, die aus `image`-, `ntext`- und `text`-Datentypen abgeleitet sind, können Nichtschlüsselspalten (eingeschlossene Spalten) in einem nicht gruppierten Index sein, so lange der Datentyp der berechneten Spalte für Nichtschlüsseldatenspalten zulässig ist.  
  
 **Anforderungen hinsichtlich der SET-Option**  
  
-   Die ANSI_NULLS-Option auf Verbindungsebene muss auf ON festgelegt sein, wenn die CREATE TABLE- oder ALTER TABLE-Anweisung, die die berechnete Spalte definiert, ausgeführt wird. Die [OBJECTPROPERTY](/sql/t-sql/functions/objectpropertyex-transact-sql) -Funktion meldet mithilfe der **IsAnsiNullsOn** -Eigenschaft, ob die Option auf ON festgelegt ist.  
  
-   Für die Verbindung, für die der Index erstellt wird, und für alle Verbindungen, die versuchen, INSERT-, UPDATE- oder DELETE-Anweisungen auszuführen, die Werte des Indexes ändern, müssen sechs SET-Optionen auf ON und eine SET-Option auf OFF festgelegt sein. Der Optimierer ignoriert einen Index für eine berechnete Spalte für alle SELECT-Anweisungen, die von einer Verbindung ausgeführt werden, die diese Optionseinstellungen nicht aufweist.  
  
    -   Die NUMERIC_ROUNDABORT-Option muss auf OFF festgelegt sein, und die folgenden Optionen müssen auf ON festgelegt sein:  
  
    -   ANSI_NULLS  
  
    -   ANSI_PADDING  
  
    -   ANSI_WARNINGS  
  
    -   ARITHABORT  
  
    -   CONCAT_NULL_YIELDS_NULL  
  
    -   QUOTED_IDENTIFIER  
  
     Durch Festlegen von ANSI_WARNINGS auf ON wird implizit ARITHABORT auf ON festgelegt, wenn der Kompatibilitätsgrad der Datenbank auf 90 oder höher festgelegt ist.  
  
##  <a name="creating-indexes-on-persisted-computed-columns"></a><a name="BKMK_persisted"></a> Erstellen von Indizes für persistente berechnete Spalten  
 Sie können einen Index für eine berechnete Spalte erstellen, die mit einem deterministischen, jedoch unpräzisen Ausdruck definiert wird, wenn die Spalte in der CREATE TABLE- oder ALTER TABLE-Anweisung als PERSISTED markiert wurde. Dies bedeutet, dass diese beibehaltenen [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Werte verwendet, wenn ein Index für die Spalte erstellt wird und wenn in einer Abfrage auf den Index verwiesen wird. Diese Option ermöglicht es Ihnen, einen Index für eine berechnete Spalte zu erstellen [!INCLUDE[ssDE](../../../includes/dnprdnshort-md.md)] , wenn, sowohl deterministisch als auch präzise ist.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)  
  
  
