---
title: NULL (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14cd51b4e245ca6984a4c62eae2b9d5536ab1f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608760"
---
# <a name="null-ssis-expression"></a>NULL (SSIS-Ausdruck)
  Gibt einen NULL-Wert eines angeforderten Datentyps zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>Argumente  
 *typespec*  
 Ein gültiger Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 Ein beliebiger gültiger Datentyp mit einem NULL-Wert.  
  
## <a name="remarks"></a>Bemerkungen  
 NULL gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Parameter sind erforderlich, um einen NULL-Wert für bestimmte Datentypen anzufordern. In der folgenden Tabelle sind diese Datentypen und die zugehörigen Parameter aufgelistet.  
  
|Datentyp|Parameter|Beispiel|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) wandelt 30 Zeichen mithilfe der 1252-Codepage in den DT_STR-Datentyp um.|  
|DT_WSTR|*charcount*|(DT_WSTR,20) wandelt 20 Zeichen in den DT_WSTR-Datentyp um.|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) wandelt 50 Bytes in den DT_BYTES-Datentyp um.|  
|DT_DECIMAL|*scale*|(DT_DECIMAL,2) wandelt einen numerischen Wert mithilfe von 2 Dezimalstellen in den DT_DECIMAL-Datentyp um.|  
|DT_NUMERIC|*precision*<br /><br /> *scale*|(DT_NUMERIC,10,3) wandelt einen numerischen Wert mithilfe einer Genauigkeit von 10 und 3 Dezimalstellen in den DT_NUMERIC-Datentyp um.|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) wandelt einen Wert mithilfe der 1252-Codepage in den DT_TEXT-Datentyp um.|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird der NULL-Wert der Datentypen zurückgegeben: DT_STR, DT_DATE und DT_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ISNULL &#40;SSIS-Ausdruck&#41;](null-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
