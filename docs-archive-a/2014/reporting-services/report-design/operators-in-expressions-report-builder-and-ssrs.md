---
title: Operatoren in Ausdrücken (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa8042df39e535425a05414c1e39ee6a12ff2f39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617732"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a>Operatoren in Ausdrücken (Berichts-Generator und SSRS)
  Ein Operator ist ein Symbol, das Aktionen darstellt, die auf einen oder mehrere Begriffe in einem Ausdruck angewendet werden. Die folgenden Operatorkategorien werden in einem Ausdruck unterstützt: Arithmetik, Vergleich, Verkettung, logisch oder bitweise und Bitverschiebung  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a>Arithmetik  
 Arithmetische Operatoren führen mathematische Vorgänge für zwei numerische Begriffe in einem Ausdruck aus.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|^|Erhebt eine Zahl zur Potenz einer anderen Zahl.|  
|*|Multipliziert zwei Zahlen.|  
|/|Dividiert zwei Zahlen und gibt ein Gleitkommaergebnis zurück.|  
|\|Dividiert zwei Zahlen und gibt eine ganze Zahl als Ergebnis zurück.|  
|Mod|Gibt den ganzzahligen Rest einer Division zurück. Beispiel: 7 Mod 5 = 2 (der Rest von 7 geteilt durch 5 ist 2).|  
|+|Addiert zwei Zahlen.|  
|-|Gibt die Differenz zwischen zwei Zahlen zurück oder gibt den negativen Wert eines numerischen Begriffs an.|  
  
### <a name="comparison"></a>Vergleich  
 Vergleichsoperatoren testen, ob zwei Ausdrücke gleichwertig sind.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|<|Kleiner als.|  
|\<=|Kleiner oder gleich.|  
|>|Größer als.|  
|>=|Größer oder gleich.|  
|=|Gleich.|  
|<>|Ungleich.|  
|Wie|Bestimmt, ob eine bestimmte Zeichenfolge mit einem angegebenen Muster übereinstimmt. Ein Muster kann normale Zeichen und Platzhalterzeichen einschließen. Bei einem Mustervergleich müssen normale Zeichen exakt mit den angegebenen Zeichen in der Zeichenfolge übereinstimmen. Platzhalterzeichen können jedoch mit beliebigen Teilen der Zeichenfolge übereinstimmen. Das Verwenden der Vergleichsoperatoren für Zeichenfolgen = und != ist nicht so flexibel wie das Verwenden von Platzhalterzeichen mit dem LIKE-Operator.<br /><br /> Im folgenden sind die Zeichen aufgeführt, die als Platzhalter Zeichen verwendet werden können:<br /><br /> **%**: Eine beliebige Zeichenfolge mit NULL oder mehr Zeichen.<br /><br /> **_**: Beliebiges einzelnes Zeichen.<br /><br /> **[]**: Ein beliebiges einzelnes Zeichen innerhalb des angegebenen Bereichs (z. b. [a-f]) oder der festgelegten Menge (z. b. [aeiou]).<br /><br /> **[^]**: Ein einzelnes Zeichen, das nicht innerhalb des angegebenen Bereichs (z. b. [^ a-f]) oder der festgelegten Menge (z. b. [^ aeiou]) liegt.|  
|Is|Vergleicht zwei Objektverweise.|  
  
### <a name="string-concatenation"></a>Verketten von Zeichenfolgen  
 Mit der Zeichenfolgenverkettung wird die zweite Zeichenfolge in einem Ausdruck an die erste Zeichenfolge angefügt. Verwenden Sie für andere Zeichenfolgenoperationen integrierte Funktionen.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|&|Verkettet zwei Zeichenfolgen.|  
|+|Verkettet zwei Zeichenfolgen.|  
  
### <a name="logical-and-bitwise"></a>Logisch und bitweise  
 Logische und bitweise Operatoren führen logische Manipulationen zwischen zwei ganzzahligen Begriffen in einem Ausdruck aus.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|And|Führt eine logische Konjunktion zweier boolescher Ausdrücke oder eine bitweise Konjunktion zweier numerischer Ausdrücke aus.|  
|Not|Führt eine logische Negation eines booleschen Ausdrucks oder eine bitweise Negation eines numerischen Ausdrucks aus.|  
|oder|Führt eine logische Disjunktion zweier boolescher Ausdrücke oder eine bitweise Disjunktion zweier numerischer Werte aus.|  
|Xor|Führt einen logischen Ausschluss zweier boolescher Ausdrücke oder einen bitweisen Ausschluss zweier numerischer Ausdrücke durch.|  
|AndAlso|Führt eine logische Konjunktion zweier Ausdrücke durch.|  
|OrElse|Führt eine logische Disjunktion zweier Ausdrücke durch.|  
  
### <a name="bit-shift"></a>Bitverschiebung  
 Bitweise Operatoren führen Bitmanipulationen zwischen zwei ganzzahligen Begriffen in einem Ausdruck aus.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|<\<|Führt eine arithmetische Verschiebung nach links für ein Bitmuster aus.|  
|>>|Führt eine arithmetische Verschiebung nach rechts für ein Bitmuster aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdruck (Dialogfeld)](../expression-dialog-box.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](data-types-in-expressions-report-builder-and-ssrs.md)   
 [Dialogfeld „Ausdruck“ (Berichts-Generator)](../expression-dialog-box-report-builder.md)  
  
  
