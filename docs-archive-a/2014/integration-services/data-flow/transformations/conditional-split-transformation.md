---
title: Transformation für bedingtes Teilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96ff4b177992c329908ebc93df8f6220168e634d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619242"
---
# <a name="conditional-split-transformation"></a>Transformation für bedingtes Teilen
  Die Transformation für bedingtes Teilen kann Datenzeilen je nach Dateninhalt an andere Ausgaben routen. Die Implementierung der Transformation für bedingtes Teilen ist mit einer CASE-Entscheidungsstruktur in einer Programmiersprache vergleichbar. Diese Transformation wertet Ausdrücke aus und leitet dann basierend auf den Ergebnissen die Datenzeilen an die angegebene Ausgabe weiter. Diese Transformation stellt zudem eine Standardausgabe bereit, damit eine Zeile, die mit keinem Ausdruck übereinstimmt, an die Standardausgabe weitergeleitet wird.  
  
## <a name="configuration-of-the-conditional-split-transformation"></a>Konfiguration der Transformation für bedingtes Teilen  
 Es gibt folgende Möglichkeiten, um die Transformation für bedingtes Teilen zu konfigurieren:  
  
-   Stellen Sie einen Ausdruck, der in einen booleschen Wert ausgewertet wird, für jede von der Transformation zu testende Bedingung bereit.  
  
-   Geben Sie die Reihenfolge an, in der die Bedingungen ausgewertet werden. Die Reihenfolge ist wichtig, weil eine Zeile entsprechend der ersten Bedingung, die zu true ausgewertet wird, an die Ausgabe gesendet wird.  
  
-   Geben Sie die Standardausgabe für die Transformation an. Für die Transformation muss eine Standardausgabe angegeben werden.  
  
 Jede Eingabezeile kann nur an eine Ausgabe gesendet werden, nämlich an die Ausgabe für die erste Bedingung, die zu true ausgewertet wird. Beispielsweise leiten die folgenden Bedingungen Zeilen in der **FirstName** -Spalte, die mit dem Buchstaben *A* beginnen, an eine bestimmte Ausgabe weiter. Zeilen, die mit dem Buchstaben *B* beginnen, werden an eine andere Ausgabe weitergeleitet. Alle anderen Zeilen werden an die Standardausgabe weitergeleitet.  
  
 Output 1  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 Output 2  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] schließt Funktionen und Operatoren ein, mit denen Sie die Ausdrücke erstellen können, die Eingabedaten auswerten und Ausgabedaten weiterleiten. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)ausgewertet wird.  
  
 Die Transformation für bedingtes Teilen schließt die benutzerdefinierte Eigenschaft `FriendlyExpression` ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../../expressions/use-property-expressions-in-packages.md) und [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md).  
  
 Diese Transformation weist eine Eingabe, mindestens eine Ausgabe und eine Fehlerausgabe auf.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für bedingtes Teilen** festlegen können, finden Sie unter [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen](conditional-split-transformation.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen](conditional-split-transformation.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
