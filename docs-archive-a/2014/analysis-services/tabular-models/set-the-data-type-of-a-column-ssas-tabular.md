---
title: Festlegen des Datentyps einer Spalte (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34e2d508-7b64-4503-a4f0-c6c6ad5f8a44
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d747f96e836a683ccce3aca3c5e3349ca633210
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694733"
---
# <a name="set-the-data-type-of-a-column-ssas-tabular"></a>Festlegen des Datentyps einer Spalte (SSAS – tabellarisch)
  Wenn Sie Daten importieren oder Daten in ein Modell einfügen, werden Datentypen vom Modell-Designer automatisch erkannt und angewendet. Nachdem Sie dem Modell Daten hinzugefügt haben, können Sie den Datentyp einer Spalte manuell ändern, um die Speicherung von Daten zu ändern. Bei Bedarf können Sie stattdessen nur das Anzeigeformat der Daten ändern, ohne die Methode der Datenspeicherung zu ändern.  
  
### <a name="to-change-the-data-type-or-display-format-for-a-column"></a>So ändern Sie den Datentyp oder das Anzeigeformat für eine Spalte  
  
1.  Wählen Sie im Modell-Designer die Spalte aus, für die Sie den Datentyp oder das Anzeigeformat ändern möchten.  
  
2.  Führen Sie im Fenster **Eigenschaften** der Spalte einen der folgenden Schritte aus:  
  
    -   Wählen Sie in der **Datenformat** -Eigenschaft ein anderes Datenformat aus.  
  
    -   Wählen Sie in der **Datentyp** -Eigenschaft einen anderen Datentyp aus.  
  
## <a name="considerations-when-changing-data-types"></a>Überlegungen zum Ändern von Datentypen  
 Wenn Sie versuchen, den Datentyp einer Spalte zu ändern oder eine Datenkonvertierung auszuwählen, kann in einigen Fällen einer der folgenden Fehler auftreten:  
  
-   Fehler beim Ändern des Datentyps  
  
-   Fehler beim Ändern des Spaltendatentyps  
  
 Diese Fehler können auch auftreten, wenn der Datentyp als Option in der Dropdownliste Datentyp verfügbar ist. In diesem Abschnitt erfahren Sie, warum diese Fehler auftreten und wie Sie sie korrigieren können.  
  
### <a name="understanding-automatically-determined-data-types"></a>Grundlegendes zur automatischen Ermittelung von Datentypen  
 Wenn Sie einem Modell Daten hinzufügen, überprüft der Modell-Designer die Datenspalten, um festzustellen, welche Datentypen die jeweilige Spalte enthält. Wenn die Daten in der jeweiligen Spalte konsistent sind, wird der Spalte der am besten passendste Datentyp zugewiesen.  
  
 Wenn Sie Daten jedoch aus Excel oder einer anderen Quelle hinzufügen, die keine einheitliche Verwendung eines einzelnen Datentyps in jeder Spalte erzwingt, weist der Modell-Designer den Datentyp zu, der auf alle Werte innerhalb der Spalte zutrifft. Wenn eine Spalte Zahlen verschiedener Typen enthält, z. B. ganze Zahlen, lange Zahlen und Währung, verwendet der Modell-Designer den decimal-Datentyp. Wenn eine Spalte Ziffern und Text enthält, verwendet der Modell-Designer stattdessen den text-Datentyp. Der Modell-Designer stellt keinen Datentyp bereit, der mit dem allgemeinen Datentyp in Excel vergleichbar wäre.  
  
 Wenn eine Spalte Zahlenwerte und Texteinträge enthält, können Sie die Spalte daher nicht in einen numerischen Datentyp konvertieren.  
  
 Die folgenden Datentypen sind in Business Intelligence-Semantikmodellen verfügbar:  
  
|Modelldatentypen|  
|----------------------|  
|Text<br /><br /> Decimal Number<br /><br /> Ganze Zahl<br /><br /> Währung<br /><br /> TRUE/FALSE<br /><br /> Date|  
  
 Wenn Sie feststellen, dass die Daten einen falschen bzw. nicht den gewünschten Datentyp aufweisen, haben Sie mehrere Möglichkeiten:  
  
-   Sie können die Daten erneut importieren. Hierzu öffnen Sie die vorhandene Verbindung mit der Datenquelle und importieren die Spalte erneut. Je nach Datenquellentyp können Sie beim Import einen Filter anwenden, um Problemwerte zu entfernen.  
  
-   Sie können in einer berechneten Spalte eine DAX-Formel erstellen, um einen neuen Wert des gewünschten Datentyps zu erstellen. Sie können z. B. die TRUNC-Funktion verwenden, um eine Dezimalzahl in eine ganze Zahl zu ändern. Sie können auch Informationsfunktionen und logische Funktionen kombinieren, um Werte zu testen und zu konvertieren.  
  
### <a name="understanding-data-conversion"></a>Grundlegendes zur Datenkonvertierung  
 Wenn bei der Auswahl einer Datenkonvertierungsoption ein Fehler auftritt, kann dies daran liegen, dass der aktuelle Datentyp der Spalte die ausgewählte Konvertierung nicht unterstützt. Nicht alle Konvertierungen sind für alle Datentypen zulässig. Sie können eine Spalte z. B. nur dann in einen booleschen Datentyp ändern, wenn der aktuelle Datentyp der Spalte entweder eine Zahl (ganz oder dezimal) oder Text ist. Daher müssen Sie für die Daten in der Spalte einen passenden Datentyp auswählen.  
  
 Nachdem Sie einen entsprechenden Datentyp ausgewählt haben, warnt der Modell-Designer Sie vor möglichen Änderungen an den Daten, z. B. geringere Genauigkeit oder abgeschnittene Daten. Klicken Sie zur Bestätigung auf OK, um die Daten in den neuen Datentyp zu ändern.  
  
 Wenn der Datentyp unterstützt wird, der Modell-Designer jedoch Werte findet, die vom neuen Datentyp nicht unterstützt werden, erhalten Sie eine weitere Fehlermeldung. Sie müssen die Datenwerte korrigieren, bevor Sie fortfahren.  
  
 Unter [Unterstützte Datentypen &#40;SSAS – tabellarisch&#41;](data-types-supported-ssas-tabular.md)finden Sie detaillierte Informationen zu den Datentypen, die in Business Intelligence-Semantikmodellen verwendet werden. Zudem wird erläutert, wie die Datentypen implizit konvertiert und wie verschiedene Datentypen in Formeln verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte Datentypen &#40;SSAS – tabellarisch&#41;](data-types-supported-ssas-tabular.md)  
  
  
