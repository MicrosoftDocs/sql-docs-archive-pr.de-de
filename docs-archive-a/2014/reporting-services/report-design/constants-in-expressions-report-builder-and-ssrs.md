---
title: Konstanten in Ausdrücken (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616445"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a>Konstanten in Ausdrücken (Berichts-Generator und SSRS)
  Eine Konstante besteht aus Literaltext oder vordefiniertem Text. Der Berichtsprozessor hat Zugriff auf die vordefinierten Konstanten. Wenn Sie die Konstanten in einen Ausdruck einschließen, werden die Werte, die sie darstellen, daher im Ausdruck ersetzt, bevor dieser ausgewertet wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a>Literaltext  
 In einem Ausdruck ist Literaltext Text, der in doppelten Anführungszeichen steht. Sie können Text auch direkt ohne doppelte Anführungszeichen in ein Textfeld eingeben, wenn er nicht Teil eines Ausdrucks ist. Wenn der Textfeldwert nicht mit einem Gleichheitszeichen (=) beginnt, wird der Text als Literaltext behandelt. In der folgenden Tabelle werden mehrere Beispiele für Literaltext in einem Ausdruck angezeigt.  
  
|Dauerhaft|Anzeigetext|Ausdruckstext|  
|--------------|------------------|---------------------|  
|Bericht ausgeführt um:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Adventure Works Cycles|Adventure Works Cycles|Adventure Works Cycles|  
|[Anzeigetext in Klammern]|\\[Anzeigetext in Klammern\\]|[Anzeigetext in Klammern]|  
  
## <a name="rdl-constants"></a>RDL-Konstanten  
 Sie können in der Berichtsdefinitionssprache (RDL) definierte Konstanten in einem Ausdruck verwenden. Im Dialogfeld **Ausdruck** werden Konstanten angezeigt, wenn Sie einen Ausdruck für eine Berichtseigenschaft erstellen, der nur bestimmte gültige Werte akzeptiert. Diese Werte werden auch als Enumerationstypen bezeichnet. Die folgende Tabelle enthält zwei Beispiele.  
  
|Eigenschaft|BESCHREIBUNG|Werte|  
|--------------|-----------------|------------|  
|Textausrichtung|Gültige Werte zum Ausrichten von Text in einem Textfeld.|Allgemein, Links, Zentriert, Rechts|  
|Rahmenart|Gültige Werte für eine einem Bericht hinzugefügte Zeile.|Standard, Keine, Gepunktet, Gestrichelt, Einfarbig, Doppelt, Strich-Punkt, Strich-Punkt-Punkt|  
  
## <a name="visual-basic-constants"></a>Visual Basic-Konstanten  
 Sie können in einem Ausdruck in der [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Laufzeitbibliothek definierte Konstanten verwenden. Beispielsweise kann die Konstante `DateInterval.Day` nicht verwendet werden. Für das Datum 10. Januar 2008 gibt der folgende Ausdruck beispielsweise die Zahl 10 zurück:  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a>CLR-Konstanten  
 Sie können in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime-Klassen (CLR) definierte Konstanten in einem Ausdruck verwenden. In der folgenden Tabelle wird ein Beispiel für eine systemdefinierte Farbe angezeigt.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|MistyRose|Beim Erstellen eines Ausdrucks für eine Berichtseigenschaft, die auf der Hintergrundfarbe basiert, können Sie eine Farbe mit Namen angeben. Gültige Namen werden im Dialogfeld **Ausdruck** aufgelistet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld ' Ausdruck '](../expression-dialog-box.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md)   
 [Dialogfeld „Ausdruck“ (Berichts-Generator)](../expression-dialog-box-report-builder.md)  
  
  
