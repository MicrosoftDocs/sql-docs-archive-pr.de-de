---
title: Ausdrucks-Generator | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 812b0d744d415d5419d54176359ddcd5837dd206
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617214"
---
# <a name="expression-builder"></a>Ausdrucks-Generator
  Verwenden Sie das Dialogfeld **Ausdrucks-Generator** , um mithilfe einer grafischen Benutzeroberfläche einen Eigenschaftsausdruck zu erstellen und zu bearbeiten oder den Ausdruck zu schreiben, der den Wert einer Variablen festlegt. Diese grafische Benutzeroberfläche bietet Listen von Variablen sowie integrierte Verweise auf Funktionen, Typumwandlungen und Operatoren der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Ausdruckssprache.  
  
 Ein Eigenschaftsausdruck ist ein einer Eigenschaft zugewiesener Ausdruck. Wenn der Ausdruck ausgewertet wird, wird die Eigenschaft dynamisch aktualisiert, damit das Auswertungsergebnis des Ausdrucks verwendet wird. Genauso ermöglicht ein Ausdruck, der in einer Variablen verwendet wird, das Update des Variablenwerts mit dem Auswertungsergebnis des Ausdrucks.  
  
 Es gibt mehrere Verwendungsmöglichkeiten für Ausdrücke:  
  
-   **Tasks** Aktualisieren Sie die „An“-Zeile, die ein Task des Typs „Mail“ senden verwendet, indem eine in einer Variablen gespeicherte E-Mail-Adresse eingefügt wird, oder aktualisieren Sie die Betreffzeile, indem Sie eine Zeichenfolge, wie z.B. "Sales for:", und das aktuelle Datum verketten, das von der GETDATE-Funktion zurückgegeben wird.  
  
-   **Variablen** Legen Sie den Wert einer Variablen auf den aktuellen Monat fest, indem Sie einen Ausdruck wie `DATEPART("mm",GETDATE())`verwenden. Oder legen Sie den Wert einer Zeichenfolge fest, indem Sie das Zeichenfolgenliteral und das aktuelle Datum mithilfe des Ausdrucks `"Today's date is " + (DT_WSTR,30)(GETDATE())`verketten.  
  
-   **Verbindungs-Manager** Legen Sie die Codepage eines Flatfile-Verbindungs-Managers fest, indem Sie eine Variable verwenden, die einen anderen Codepagebezeichner enthält, oder geben Sie die Anzahl der auszulassenden Zeilen in der Datendatei an, indem Sie eine positive ganze Zahl, z. B. 3, in dem Ausdruck eingeben.  
  
 Weitere Informationen zu Eigenschaftenausdrücken und zum Schreiben von Ausdrücken finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](use-property-expressions-in-packages.md) und [Integration Services-Ausdrücke &#40;SSIS&#41;](integration-services-ssis-expressions.md).  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Variablen**|Erweitern Sie den Ordner **Variablen** , und ziehen Sie die gewünschten Variablen in das Feld **Ausdruck** .|  
|**Mathematische Funktionen**<br /><br /> **Zeichenfolgenfunktionen**<br /><br /> **Datum/Uhrzeit-Funktionen**<br /><br /> **NULL-Funktionen**<br /><br /> **Typumwandlungen**<br /><br /> **Operatoren**|Erweitern Sie die entsprechenden Ordner, und ziehen Sie die gewünschten Funktionen, Typumwandlungen und Operatoren in das Feld **Ausdruck** .|  
|**Ausdruck**|Geben Sie einen Ausdruck ein, oder bearbeiten Sie einen Ausdruck.|  
|**Ausgewerteter Wert**|Listet das Ergebnis der Ausdrucksauswertung auf.|  
|**Ausdruck auswerten**|Klicken Sie auf **Ausdruck auswerten** , um das Auswertungsergebnis des Ausdrucks anzuzeigen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Seite Ausdrücke](expressions-page.md)   
 [Eigenschaftsausdrucks-Editor](property-expressions-editor.md)   
 [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md)   
 [Systemvariablen](../system-variables.md)  
  
  
