---
title: Transformation für abgeleitete Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bbdc46f2e67b1b859fcfa446c584373cfbeca0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608768"
---
# <a name="derived-column-transformation"></a>Transformation für abgeleitete Spalten
  Mit der Transformation für abgeleitete Spalten werden neue Spaltenwerte erstellt, indem Ausdrücke auf Transformationseingabespalten angewendet werden. Ein Ausdruck kann eine beliebige Kombination von Variablen, Funktionen, Operatoren und Spalten aus der Transformationseingabe enthalten. Das Ergebnis kann als neue Spalte hinzugefügt oder in eine vorhandene Spalte als Ersatzwert eingefügt werden. Die Transformation für abgeleitete Spalten kann mehrere abgeleitete Spalten definieren, und jede Variable oder Eingabespalte kann in mehreren Ausdrücken verwendet werden.  
  
 Mit dieser Transformation können die folgenden Aufgaben ausgeführt werden:  
  
-   Verketten von Daten aus verschiedenen Spalten zu einer abgeleiteten Spalte. Beispielsweise können Sie mithilfe des Ausdrucks **Werte aus den Spalten** FirstName **und** LastName **zu einer einzelnen abgeleiteten Spalte mit dem Namen**FullName `FirstName + " " + LastName`verketten.  
  
-   Extrahieren von Zeichen aus Zeichenfolgendaten mithilfe von Funktionen, wie z. B. SUBSTRING, und anschließendes Speichern des Ergebnisses in einer abgeleiteten Spalte. Beispielsweise können Sie mithilfe des Ausdrucks **die Initialen einer Person aus der** FirstName `SUBSTRING(FirstName,1,1)`-Spalte extrahieren.  
  
-   Anwenden mathematischer Funktionen auf numerische Daten und Speichern des Ergebnisses in einer abgeleiteten Spalte. Beispielsweise können Sie mithilfe des Ausdrucks **die Länge und die Genauigkeit der numerischen**SalesTax `ROUND(SalesTax, 2)`-Spalte in eine Zahl mit zwei Dezimalstellen ändern.  
  
-   Erstellen von Ausdrücken, die Eingabespalten und Variablen vergleichen. Beispielsweise können Sie mithilfe des Ausdrucks **die** Version **-Variable mit den Daten in der**ProductVersion **-Spalte vergleichen und in Abhängigkeit vom Ergebnis des Vergleichs den Wert von** Version **bzw.** ProductVersion `ProductVersion == @Version? ProductVersion : @Version`verwenden.  
  
-   Extrahieren von Elementen eines datetime-Werts. Beispielsweise können Sie mithilfe des Ausdrucks `DATEPART("year",GETDATE())`und den Funktionen "GETDATE" und "DATEPART" das aktuelle Jahr extrahieren.  
  
-   Konvertieren Sie Datumszeichenfolgen mithilfe eines Ausdrucks in ein bestimmtes Format.  
  
## <a name="configuration-of-the-derived-column-transformation"></a>Konfiguration der Transformation für abgeleitete Spalten  
 Es gibt folgende Möglichkeiten, um die Transformation für abgeleitete Spalten zu konfigurieren:  
  
-   Geben Sie für jede Eingabespalte oder jede neue Spalte, die geändert wird, einen Ausdruck ein. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)ausgewertet wird.  
  
    > [!NOTE]  
    >  Falls ein Ausdruck auf eine Eingabespalte verweist, die von der Transformation für abgeleitete Spalten überschrieben wird, wird im Ausdruck nicht der abgeleitete Wert, sondern der ursprüngliche Wert verwendet.  
  
-   Wenn Sie neuen Spalten Ergebnisse hinzufügen und der Datentyp `string` lautet, geben Sie eine Codepage an. Weitere Informationen finden Sie unter [Comparing String Data](../comparing-string-data.md).  
  
 Die Transformation für bedingtes Teilen schließt die benutzerdefinierte Eigenschaft FriendlyExpression ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../../expressions/use-property-expressions-in-packages.md)und [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md).  
  
 Diese Transformation weist eine Eingabe, eine reguläre Ausgabe und eine Fehlerausgabe auf.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für abgeleitete Spalte** festlegen können, finden Sie unter [Derived Column Transformation Editor](../../derived-column-transformation-editor.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Ableiten von Spaltenwerten mithilfe der Transformation für abgeleitete Spalten](derived-column-transformation.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), auf social.technet.microsoft.com  
  
 Blog, Gewusst [wie: Aufteilen von Spaltendaten mithilfe von SSIS](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html).  
  
  
