---
title: ~ (Bitweises NOT) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619964"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (Bitweises NOT) (SSIS-Ausdruck)
  Führt eine bitweise Negation einer ganzen Zahl aus. Dieser Operator kann auf integer-Datentypen mit und ohne Vorzeichen angewendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression*  
 Ein beliebiger gültiger Ausdruck eines integer-Datentyps. *integer*_*expression* ist eine ganze Zahl, die für die bitweise Operation in eine binäre Zahl transformiert wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt den Datentyp von *integer_expression*zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Keine  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird eine bitweise ~ (NOT)-Operation für die Zahl 170 (0000 0000 1010 1010) ausgeführt. Diese Zahl ist eine ganze Zahl mit Vorzeichen.  
  
```  
  
~ 170  
```  
  
 Der Ausdruck wird zu -170 (1111111101010101) ausgewertet.  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
