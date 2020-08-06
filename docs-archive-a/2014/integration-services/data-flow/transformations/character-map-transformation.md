---
title: Transformation zum Zuordnen der Zeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactertrans.f1
helpviewer_keywords:
- mutually exclusive mapping [Integration Services]
- mapping data [Integration Services]
- string functions
- Character Map transformation [Integration Services]
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5fc31e1a3500a7a7b023e43a968e70e5b438dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619244"
---
# <a name="character-map-transformation"></a>Transformation zum Zuordnen der Zeichen
  Die Transformation zum Zuordnen der Zeichen wendet Zeichenfolgenfunktionen, wie z. B. die Konvertierung von Klein- in Großbuchstaben, auf Zeichendaten an. Diese Transformation betrifft nur Spaltendaten mit einem Zeichenfolgen-Datentyp.  
  
 Die Transformation zum Zuordnen der Zeichen kann Spaltendaten direkt konvertieren oder der Transformationsausgabe eine Spalte hinzufügen und die konvertierten Daten in die neue Spalte einfügen. Sie können auf eine Eingabespalte verschiedene Zuordnungsvorgänge anwenden und die Ergebnisse verschiedenen Spalten hinzufügen. Konvertieren Sie z. B. eine Spalte in Groß- und Kleinbuchstaben, und fügen Sie die Ergebnisse zwei unterschiedlichen Spalten hinzu.  
  
 Die Zuordnung kann unter bestimmten Umständen das Abschneiden von Daten verursachen. Beispielsweise, wenn Einzelbytezeichen Zeichen mit einer Multibytedarstellung zugeordnet werden. Die Transformation zum Zuordnen der Zeichen schließt eine Fehlerausgabe ein, mit der abgeschnittene Daten an eine separate Ausgabe weitergeleitet werden können. Weitere Informationen finden Sie unter [Fehlerbehandlung in Daten](../error-handling-in-data.md).  
  
 Diese Transformation weist eine Eingabe, eine Ausgabe und eine Fehlerausgabe auf.  
  
## <a name="mapping-operations"></a>Zuordnungsvorgänge  
 In der folgenden Tabelle sind die Zuordnungsvorgänge beschrieben, die von der Transformation zum Zuordnen der Zeichen unterstützt werden.  
  
|Vorgang|BESCHREIBUNG|  
|---------------|-----------------|  
|Byteumkehrung|Kehrt die Bytereihenfolge um.|  
|Normale Breite|Ordnet Zeichen halber Breite Zeichen normaler Breite zu.|  
|Halbe Breite|Ordnet Zeichen normaler Breite Zeichen halber Breite zu.|  
|Hiragana|Ordnet Katakanazeichen Hiraganazeichen zu.|  
|Katakana|Ordnet Hiraganazeichen Katakanazeichen zu.|  
|Linguistische Schreibweise|Wendet die linguistische Schreibweise anstelle der Systemregeln an. Die linguistische Schreibweise bezieht sich auf die Funktionalität der Win32 API für die einfache Unicode-Schreibweisenzuordnung von Türkisch und anderen Gebietsschemas.|  
|Kleinbuchstaben|Konvertiert Zeichen in Kleinbuchstaben.|  
|Chinesisch (vereinfacht)|Ordnet Zeichen in traditionellem Chinesisch Zeichen in vereinfachtem Chinesisch zu.|  
|Chinesisch (traditionell)|Ordnet Zeichen in vereinfachtem Chinesisch Zeichen in traditionellem Chinesisch zu.|  
|Großbuchstaben|Konvertiert Zeichen in Großbuchstaben.|  
  
## <a name="mutually-exclusive-mapping-operations"></a>Zuordnungsvorgänge, die sich gegenseitig ausschließen  
 In einer Transformation können mehrere Vorgänge ausgeführt werden. Manche Zuordnungsvorgänge schließen sich jedoch gegenseitig aus. In der folgenden Tabelle sind die Einschränkungen aufgeführt, die bei der Verwendung mehrerer Vorgänge in derselben Spalte gelten. Vorgänge in den Spalten Vorgang A und Vorgang B schließen sich gegenseitig aus.  
  
|Vorgang A|Vorgang B|  
|-----------------|-----------------|  
|Kleinbuchstaben|Großbuchstaben|  
|Hiragana|Katakana|  
|Halbe Breite|Normale Breite|  
|Chinesisch (traditionell)|Chinesisch (vereinfacht)|  
|Kleinbuchstaben|Hiragana, Katakana, halbe Breite, normale Breite|  
|Großbuchstaben|Hiragana, Katakana, halbe Breite, normale Breite|  
  
## <a name="configuration-of-the-character-map-transformation"></a>Konfiguration der Transformation zum Zuordnen der Zeichen  
 Es gibt folgende Möglichkeiten, um die Transformation zum Zuordnen der Zeichen zu konfigurieren:  
  
-   Geben Sie die zu konvertierenden Spalten an.  
  
-   Geben Sie die auf jede Spalte anzuwendenden Vorgänge an.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Zeichenzuordnung** festlegen können, finden Sie unter [Character Map Transformation Editor](../../character-map-transformation-editor.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  
