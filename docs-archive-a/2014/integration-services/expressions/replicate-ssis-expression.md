---
title: REPLICATE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9502df5bc20c6ad85f1f98fb57fe6b3cf431cc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701414"
---
# <a name="replicate-ssis-expression"></a>REPLICATE (SSIS-Ausdruck)
  Gibt einen Zeichenausdruck zurück, der mehrfach repliziert wird. Das *times* -Argument muss zu einer ganzen Zahl ausgewertet werden.  
  
> [!NOTE]  
>  Die REPLICATE-Funktion verwendet häufig lange Zeichenfolgen und wird daher eher Probleme mit der auf 4.000 Zeichen beschränkten Länge von Ausdrücken verursachen. Hat das Auswertungsergebnis eines Ausdrucks den Integration Services-Datentyp DT_WSTR oder DT_STR, wird der Ausdruck nach 4.000 Zeichen abgeschnitten. Ist der Ergebnistyp eines Unterausdrucks DT_STR oder DT_WSTR, wird dieser Unterausdruck unabhängig vom Ergebnistyp des Gesamtausdrucks ebenfalls nach 4.000 Zeichen abgeschnitten. Die Folgen der Kürzung können unauffällig behandelt werden oder eine Warnung oder einen Fehler verursachen. Weitere Informationen finden Sie unter [Syntax &#40;SSIS&#41;](syntax-ssis.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck, der repliziert werden soll.  
  
 *times*  
 Eine ganzzahliger Ausdruck, der angibt, wie oft *character_expression* repliziert wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Bemerkungen  
 Falls *times* null ist, gibt die Funktion eine leere Zeichenfolge zurück.  
  
 Falls *times* eine negative Zahl ist, gibt die Funktion einen Fehler zurück.  
  
 Für das *times* -Argument sind auch Variablen und Spalten möglich.  
  
 REPLICATE kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor REPLICATE ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md) und [CAST &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 REPLICATE gibt ein NULL-Ergebnis zurück, wenn eines der Argumente NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral dreimal repliziert. Als Ergebnis wird "Mountain BikeMountain BikeMountain Bike" zurückgegeben.  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 In diesem Beispiel werden Werte in der **Name** -Spalte mit dem Wert in der **Times** -Variablen repliziert. Falls **Times** 3 und **Name** Touring Front Wheel ist, wird als Ergebnis Touring Front WheelTouring Front WheelTouring Front Wheel zurückgegeben.  
  
```  
REPLICATE(Name, @Times)  
```  
  
 In diesem Beispiel wird der Wert in der **Name** -Variablen mit dem Wert in der **Times** -Spalte repliziert. **Times** weist einen nicht ganzzahligen Datentyp auf, und der Ausdruck schließt eine explizite Umwandlung in einen ganzzahligen Datentyp. Falls **Name** Helmet einschließt und **Times** 2 ist, wird als Ergebnis "HelmetHelmet" zurückgegeben.  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
