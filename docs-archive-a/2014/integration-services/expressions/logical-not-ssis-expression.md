---
title: '! (Logisches NOT) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bbf313930575e864f1556952425567fca96db15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617201"
---
# <a name="-logical-not-ssis-expression"></a>! (Logisches NOT) (SSIS-Ausdruck)
  Negiert einen booleschen Operanden.  
  
> [!NOTE]  
>  Der !-Operator kann nicht zusammen mit anderen Operatoren verwendet werden. Beispielsweise können nicht den !-Operator und den >-Operator zum !>-Operator zusammenfassen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression*  
 Ein gültiger Ausdruck, der zu einem booleschen Wert ausgewertet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle wird das Ergebnis des ausgeführt werden müssen.  
  
|Ursprünglicher boolescher Ausdruck|Nach dem Anwenden des !- Operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird zu FALSE ausgewertet, falls der Wert in der **Color** -Spalte "red" ist.  
  
```  
!(Color == "red")  
```  
  
 In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **MonthNumber** -Variablen mit der ganzen Zahl identisch ist, die den aktuellen Monat darstellt. Weitere Informationen finden Sie unter [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md) und [GETDATE &#40;SSIS-Ausdruck&#41;](getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
