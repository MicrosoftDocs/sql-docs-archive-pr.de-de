---
title: MSSQLSERVER_9532 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c34ebc7c682d2ffe8bc0205565f5dfd44fdd5b66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617035"
---
# <a name="mssqlserver_9532"></a>MSSQLSERVER_9532
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9532|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|Meldungstext|Konvertierungsfehler während des Abfrage-/DML-Vorgangs mit dem Spaltensatz '%.*ls' beim Versuch, den '%ls'-Datentyp für die '%.\*ls'-Spalte in den '%ls'-Datentyp zu konvertieren.|  
  
## <a name="explanation"></a>Erklärung  
 Bei einem Spaltensatz handelt es sich um eine nicht typisierte XML-Darstellung, die einige Tabellenspalten mit geringer Dichte in einer strukturierten Ausgabe kombiniert. Wenn Sie die Sparsespalten mit dem XML-Spaltensatz einfügen bzw. aktualisieren, werden die Werte, die in die zugrunde liegenden Sparsespalten eingefügt werden, automatisch vom `xml`-Datentyp konvertiert. Es wurde ein Wert angegeben, der nicht in den Datentyp der Spalte konvertiert werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Da der bereitgestellte Wert nicht implizit konvertiert werden konnte, könnte es sich um einen ungültigen Eintrag handeln. Beheben Sie den Fehler, und versuchen Sie es erneut. Wenn der Wert korrekt ist, bearbeiten Sie die Anweisung so, dass die einzelnen Spalten anstelle des gesamten Spaltensatzes verwendet werden. Dadurch können Sie den Wert explizit in den richtigen Datentyp umwandeln.  
  
  
