---
title: Transformations-Editor für ausdrucksexextraktion (Registerkarte Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718469"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Transformations-Editor für Ausdrucksextrahierung (Registerkarte Erweitert)
  Auf der Registerkarte **Erweitert** des Dialogfelds **Transformations-Editor für Ausdrucksextrahierung** können Sie Eigenschaften für die Extrahierung angeben, wie z. B. Häufigkeit, Länge und ob Wörter oder Ausdrücke extrahiert werden sollen.  
  
 Weitere Informationen zur Transformation für Ausdrucksextrahierung finden Sie unter [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Nomen**  
 Gibt an, dass durch die Transformation nur einzelne Nomen extrahiert werden.  
  
 **Nominaler Ausdruck**  
 Gibt an, dass durch die Transformation nur nominale Ausdrücke extrahiert werden.  
  
 **Nomen und nominaler Ausdruck**  
 Gibt an, dass durch die Transformation sowohl Nomen als auch nominale Ausdrücke extrahiert werden.  
  
 **Frequency**  
 Gibt an, dass es sich bei dem Ergebnis um die Häufigkeit des Begriffs handelt.  
  
 **TFIDF**  
 Gibt an, dass es sich bei dem Ergebnis um den TFIDF-Wert des Begriffs handelt. Das TFIDF-Ergebnis ist das Produkt von Ausdruckshäufigkeit und umgekehrter Dokumenthäufigkeit, definiert als: TFIDF des Ausdrucks T = (Häufigkeit von T) * log((Anz. Zeilen in der Eingabe)/(Anz. Zeilen mit T))  
  
 **Schwellenwert für Häufigkeit**  
 Gibt in Form eines Zahlenwertes an, wie oft ein Wort oder ein Ausdruck vorkommen muss, bevor die Extrahierung erfolgt. Der Standardwert ist 2.  
  
 **Maximale Ausdruckslänge**  
 Gibt die maximale Länge des Ausdrucks in Worten an. Diese Option bezieht sich nur auf nominale Ausdrücke. Der Standardwert ist 12.  
  
 **Ausdrucksextrahierung mit Unterscheidung nach Groß-/Kleinschreibung verwenden**  
 Gibt an, ob bei der Extrahierung nach Groß-/Kleinschreibung unterschieden wird. Der Standardwert lautet `False`.  
  
 **Konfigurieren der Fehlerausgabe**  
 Geben Sie mit dem Dialogfeld [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) die Fehlerbehandlung für Zeilen an, die Fehler verursachen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Ausdrucksextrahierung &#40;Registerkarten&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Transformations-Editor für Ausdrucksextrahierung &#40;&#41;Register](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Transformation für Ausdruckssuche](data-flow/transformations/lookup-transformation.md)  
  
  
