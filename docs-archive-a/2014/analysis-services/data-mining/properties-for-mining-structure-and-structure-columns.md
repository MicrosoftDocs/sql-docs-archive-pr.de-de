---
title: Eigenschaften für Mining Struktur-und Struktur Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], column properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- properties [data mining]
ms.assetid: ce90f684-bb8c-4eca-b9e6-000794dbee16
author: minewiskan
ms.author: owend
ms.openlocfilehash: d83052c91b62f2c8873a80084b02200f276b4aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718925"
---
# <a name="properties-for-mining-structure-and-structure-columns"></a>Eigenschaften für Miningstrukturen und Strukturspalten
  Sie können mithilfe der Registerkarte **Miningstruktur** des Data Mining-Designers die Eigenschaften für eine Miningstruktur und für die verbundenen Spalten und geschachtelten Tabellen festlegen oder ändern. Eigenschaften, die Sie auf dieser Registerkarte festlegen, werden an alle Miningmodelle weitergegeben, die mit der Struktur verbunden sind.  
  
> [!NOTE]  
>  Wenn Sie den Wert einer beliebigen Eigenschaft in der Miningstruktur ändern, darunter auch Metadaten wie Name oder Beschreibung, müssen die Miningstruktur und zugehörige Modelle neu verarbeitet werden, bevor Sie das Modell anzeigen oder abfragen können.  
  
## <a name="properties-of-mining-structures-and-mining-structure-columns"></a>Eigenschaften von Miningstrukturen und Miningstrukturspalten  
 In der folgenden Tabelle werden die Eigenschaften für die Mining Struktur und die Mining Struktur Spalten beschrieben, die für Data Mining spezifisch sind und auf der Registerkarte **Mining Struktur** angezeigt oder konfiguriert werden können. Um diese Eigenschaften anzuzeigen oder zu konfigurieren, klicken Sie mit der rechten Maustaste auf ein Element in der Strukturansicht, und klicken Sie dann auf **Eigenschaften**.  
  
-   Klicken Sie auf die Überschrift der Miningstruktur, um die Eigenschaften der Struktur anzuzeigen.  
  
-   Um die Eigenschaften einer Spalte oder einer geschachtelten Tabelle anzuzeigen, klicken Sie auf den Spaltenname.  
  
### <a name="properties-of-the-mining-structure"></a>Eigenschaften der Miningstruktur  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**CacheMode**|Gibt an, ob die beim Trainieren verwendeten Fälle nach Abschluss des Trainings zwischengespeichert oder verworfen werden sollen.<br /><br /> Hinweis: Diese Eigenschaft muss auf festgelegt werden `KeepTrainingCases` , um Drillthrough und zurück gehaltene Daten zu aktivieren.|  
|**Sortierung**|Gibt die Standardsortierung für die Spalte an. Wird keine Sortierung angegeben, wird die Sortierung des Servers verwendet.|  
|**Beschreibung**|Beschreibt die Miningstruktur. Die Beschreibung sollte den Zweck und die Zusammensetzung der Daten in der Struktur beinhalten.|  
|**ErrorConfiguration (Standard)**|Legt Optionen für die spezielle Behandlung möglicher Fehler fest.|  
|**HoldoutMaxCases**|Gibt die maximale Anzahl von Strukturfällen an, die als Testdataset reserviert werden können.  Werden Werte sowohl für **HoldoutMaxCases** als auch für **HoldoutPercent**angegeben, werden die Bedingungen miteinander kombiniert.<br /><br /> Hinweis: zum Festlegen dieser Eigenschaft <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> muss auf festgelegt werden `KeepTrainingCases` .|  
|**HoldoutPercent**|Gibt die Prozentzahl der Strukturfälle an, die als Testdataset reserviert werden sollen. Werden Werte sowohl für **HoldoutMaxCases** als auch für **HoldoutPercent**angegeben, werden die Bedingungen miteinander kombiniert.<br /><br /> Hinweis: zum Festlegen dieser Eigenschaft <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> muss auf festgelegt werden `KeepTrainingCases` .|  
|**HoldoutSeed**|Gibt einen Ausgangswert zum Initialisieren der Partitionierung des Zurückhaltungstestdatasets an, um sicherzustellen, dass das Dataset erneut erstellt werden kann.<br /><br /> Hinweis: zum Festlegen dieser Eigenschaft <xref:Microsoft.AnalysisServices.MiningStructure.CacheMode%2A> muss auf festgelegt werden `KeepTrainingCases` .|  
|**ID**|Zeigt den eindeutigen Bezeichner der Miningstruktur an.<br /><br /> Der Name, den Sie der Miningstruktur bei deren Erstellung zugewiesen haben, wird als ID verwendet. Wenn Sie den Namen später ändern, indem Sie einen neuen Wert für die `Name`-Eigenschaft eingeben, wird der neue Name nur als Alias verwendet. Die ID wird nicht geändert.|  
|**Sprache**|Gibt die Sprache für die Beschriftungen in der Miningstruktur an.|  
|`Name`|Gibt den Namen oder Alias der Miningstruktur an.<br /><br /> Wenn Sie den Wert für die Name-Eigenschaft ändern, wird der neue Name nur als Beschriftung oder Alias verwendet. Der Bezeichner für die Miningstruktur wird nicht geändert.|  
|**Quelle**|Zeigt den Namen und den Typ der Datenquelle an.|  
  
### <a name="properties-of-the-mining-structure-columns"></a>Eigenschaften der Miningstrukturspalten  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|**ClassifiedColumns**|Identifiziert die Spalte, die eine klassifizierte Spalte beschreibt.|  
|**Inhalt**|Der Inhaltstyp der Spalte.|  
|**Beschreibung**|Beschreibt die Spalte. Die Beschreibung der Spalte sollte Informationen darüber enthalten, wie die Daten in der Spalte für Data Mining abgeleitet oder bearbeitet wurden.|  
|**DiscretizationBucketCount**|Zeigt die Anzahl der Buckets in der diskretisierten Spalte an.<br /><br /> Nur verfügbar, wenn der Inhaltstyp auf `Discretized` festgelegt ist.<br /><br /> Diese Eigenschaft ist schreibgeschützt.|  
|**DiscretizationMethod**|Zeigt die Methode an, die zur Diskretisierung der Spalte verwendet wurde.<br /><br /> Nur verfügbar, wenn der Inhaltstyp auf `Discretized` festgelegt ist.<br /><br /> Diese Eigenschaft ist schreibgeschützt.|  
|**Distribution**|Gibt die Verteilung von Inhalten in der Spalte an.|  
|**ID**|Zeigt den Bezeichner der Spalte an.<br /><br /> Der Wert der ID-Eigenschaft wird beim Ändern des Werts der Name-Eigenschaft für die Spalte nicht beeinflusst.|  
|**IsKey**|Gibt an, ob es sich bei der Spalte um eine Schlüsselspalte handelt.|  
|**KeyColumns**|Enthält die Definition einer Spalte, die der Schlüssel oder Teil eines Schlüssels für ein Attribut ist.|  
|**ModelingFlags**|Legt weitere Parameter fest, die vom Algorithmus verfügbar gemacht werden.|  
|`Name`|Der Name der Spalte.|  
|**NameColumn**|Identifiziert die Spalte, die den Namen des übergeordneten Elements bereitstellt.|  
|**Quelle**|Zeigt die Quelle der Spalte an.<br /><br /> Für relationale Datenquellen ist der Wert immer **(none)**.<br /><br /> Bei auf einem OLAP-Cube basierenden Strukturen entspricht der Wert der MDX-Anweisung, die den Slice definiert, der als Quelle für die geschachtelte Tabelle verwendet wird.|  
|**SourceMeasureGroup**|Zeigt die Quelle der Measuregruppe an.<br /><br /> Für relationale Datenquellen ist der Wert immer **(none)**.<br /><br /> Bei auf einem OLAP-Cube basierenden Strukturen entspricht der Wert der MDX-Anweisung, die den Slice definiert, der als Quelle für die geschachtelte Tabelle verwendet wird.|  
|**Type**|Der Datentyp für den Inhalt der Spalte.|  
  
 Weitere Informationen zum Festlegen oder Ändern von Eigenschaften finden Sie unter [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer relationalen Mining Struktur](create-a-relational-mining-structure.md)   
 [Miningstrukturspalten](mining-structure-columns.md)  
  
  
