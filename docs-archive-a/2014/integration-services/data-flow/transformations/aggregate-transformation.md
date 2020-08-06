---
title: Transformation für das Aggregieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9e69d741ddd2bd14a31d7aa79a8c825641713523
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695889"
---
# <a name="aggregate-transformation"></a>Transformation für das Aggregieren
  Die Transformation für das Aggregieren wendet Aggregatfunktionen, wie z.B. Average, auf Spaltenwerte an und kopiert die Ergebnisse in die Transformationsausgabe. Neben Aggregatfunktionen stellt diese Transformation die GROUP BY-Klausel bereit, mit der Sie Gruppen für das Aggregieren angeben können.  
  
## <a name="operations"></a>Operationen (Operations)  
 Die Transformation für das Aggregieren unterstützt die folgenden Vorgänge.  
  
|Vorgang|BESCHREIBUNG|  
|---------------|-----------------|  
|Gruppieren nach|Unterteilt Datasets in Gruppen. Spalten eines beliebigen Datentyps können für das Gruppieren verwendet werden. Weitere Informationen finden Sie unter [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).|  
|SUM|Summiert die Werte einer Spalte. Summiert werden können nur Spalten mit einem numerischen Datentyp. Weitere Informationen finden Sie unter [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).|  
|Average|Gibt den Mittelwert der Werte in einer Spalte zurück. Der Mittelwert kann nur für Spalten mit einem numerischen Datentyp ermittelt werden. Weitere Informationen finden Sie unter [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).|  
|Anzahl|Gibt die Anzahl von Elementen in einer Gruppe zurück. Weitere Informationen finden Sie unter [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).|  
|Count distinct|Gibt die Anzahl eindeutiger Werte ungleich null in einer Gruppe zurück.|  
|Minimum|Gibt den kleinsten Wert in einer Gruppe zurück. Weitere Informationen finden Sie unter [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql). Im Gegensatz zur MIN-Funktion von Transact-SQL kann dieser Vorgang nur mit numerischen, Datums- und Zeitdatentypen verwendet werden.|  
|Maximum|Gibt den größten Wert in einer Gruppe zurück. Weitere Informationen finden Sie unter [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql). Im Gegensatz zur MAX-Funktion von Transact-SQL kann dieser Vorgang nur mit numerischen, Datums- und Zeitdatentypen verwendet werden.|  
  
 Die Transformation für das Aggregieren behandelt NULL-Werte auf die gleiche Weise wie die relationale Datenbank-Engine von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Dieses Verhalten ist im SQL-92-Standard definiert. Es gelten die folgenden Regeln:  
  
-   In einer GROUP BY-Klausel werden NULL-Werte wie andere Spaltenwerte behandelt. Enthält die Gruppierungsspalte mehrere NULL-Werte, werden diese in einer Gruppe zusammengefasst.  
  
-   In den Funktionen COUNT (Spaltenname) und COUNT (DISTINCT-Spaltenname) werden NULL-Werte ignoriert. Das Ergebnis schließt Zeilen mit NULL-Werten in der benannten Spalte aus.  
  
-   In der COUNT-Funktion (*) werden alle Zeilen gezählt, auch Zeilen mit NULL-Werten.  
  
## <a name="big-numbers-in-aggregates"></a>Große Zahlen in Aggregaten  
 Eine Spalte kann numerische Werte enthalten, die aufgrund ihres großen Werts oder der Anforderungen an die Genauigkeit speziell berücksichtigt werden müssen. Die Transformation für das Aggregieren beinhaltet die IsBig-Eigenschaft, die Sie für Ausgabespalten festlegen können, um eine spezielle Handhabung großer oder sehr genauer Zahlen aufzurufen. Falls ein Spaltenwert u.U. 4 Milliarden überschreitet oder eine Genauigkeit über den float-Datentyp hinaus erforderlich ist, sollte IsBig auf 1 festgelegt werden.  
  
 Das Festlegen der IsBig-Eigenschaft auf 1 hat folgende Auswirkungen auf die Ausgabe der Transformation für das Aggregieren:  
  
-   Der DT_R8-Datentyp wird anstelle des DT_R4-Datentyps verwendet.  
  
-   Count-Ergebnisse werden als DT_UI8-Datentyp gespeichert.  
  
-   Distinct Count-Ergebnisse werden als DT_UI4-Datentyp gespeichert.  
  
> [!NOTE]  
>  Für Spalten, die für die Vorgänge GROUP BY, Maximum oder Minimum verwendet werden, können Sie IsBig nicht auf 1 festlegen.  
  
## <a name="performance-considerations"></a>Überlegungen zur Leistung  
 Die Transformation für das Aggregieren enthält Eigenschaften, die Sie festlegen können, um die Leistung der Transformation zu optimieren.  
  
-   Wenn Sie einen **GROUP BY** -Vorgang ausführen, legen Sie die Keys-Eigenschaft oder die KeysScale-Eigenschaft für die Komponente und die Komponentenausgaben fest. Mithilfe von Keys können Sie die genaue Anzahl von Schlüsseln festlegen, die von der Transformation behandelt werden sollen. (In diesem Kontext bezeichnet Keys die Anzahl der Gruppen, die als Ergebnis eines **GROUP BY** -Vorgangs erwartet werden.) Mit KeysScale können Sie eine ungefähre Anzahl von Schlüsseln angeben. Wenn Sie einen entsprechenden Wert für Keys oder KeyScale angeben, verbessern Sie damit die Leistung, da von der Transformation den zwischengespeicherten Daten eine ausreichende Menge an Arbeitsspeicher zugewiesen werden kann.  
  
-   Legen Sie beim Durchführen eines **DISTINCT COUNT** -Vorgangs die CountDistinctKeys-Eigenschaft oder die CountDistinctScale-Eigenschaft der Komponente fest. Mithilfe von CountDistinctKeys können Sie die genaue Anzahl von Schlüsseln festlegen, die von der Transformation für einen COUNT DISTINCT-Vorgang behandelt werden sollen. (In diesem Kontext bezeichnet CountDistinctKeys die Anzahl der unterschiedlichen Werte, die als Ergebnis eines **DISTINCT COUNT** -Vorgangs erwartet werden.) Mithilfe von CountDistinctScale können Sie eine ungefähre Anzahl von Schlüsseln für einen COUNT DISTINCT-Vorgang festlegen. Wenn Sie einen entsprechenden Wert für CountDistinctKeys oder CountDistinctScale angeben, verbessern Sie damit die Leistung, da von der Transformation den zwischengespeicherten Daten eine ausreichende Menge an Arbeitsspeicher zugewiesen werden kann.  
  
## <a name="aggregate-transformation-configuration"></a>Konfiguration der Transformation für das Aggregieren  
 Die Transformation für das Aggregieren konfigurieren Sie auf der Transformations-, Ausgabe- und Spaltenebene.  
  
-   Auf der Transformationsebene konfigurieren Sie die Transformation für das Aggregieren auf Leistung, indem Sie die folgenden Werte angeben:  
  
    -   Die Anzahl der Gruppen, die als Ergebnis eines **GROUP BY** -Vorgangs erwartet werden.  
  
    -   Die Anzahl der unterschiedlichen Werte, die als Ergebnis eines **COUNT DISTINCT** -Vorgangs erwartet werden.  
  
    -   Der Prozentsatz, um den der Arbeitsspeicher während der Aggregation erweitert werden kann.  
  
     Für die Transformation für das Aggregieren kann auch konfiguriert werden, dass anstelle eines Fehlers eine Warnung generiert wird, wenn der Wert eines Divisors null ist.  
  
-   Auf der Ausgabeebene können Sie die Transformation für das Aggregieren auf Leistung konfigurieren, indem Sie die Anzahl der Gruppen angeben, die als Ergebnis eines **GROUP BY** -Vorgangs erwartet werden. Die Transformation für das Aggregieren unterstützt mehrere Ausgaben, und jede kann unterschiedlich konfiguriert werden.  
  
-   Auf der Spaltenebene geben Sie die folgenden Werte an:  
  
    -   Die von der Spalte durchgeführte Aggregation.  
  
    -   Die Vergleichsoptionen der Aggregation.  
  
 Sie können die Transformation für das Aggregieren auf Leistung auch konfigurieren, indem Sie diese Werte angeben:  
  
-   Die Anzahl der Gruppen, die als Ergebnis eines **GROUP BY** -Vorgangs für die Spalte erwartet werden.  
  
-   Die Anzahl der unterschiedlichen Werte, die als Ergebnis eines **COUNT DISTINCT** -Vorgangs für die Spalte erwartet werden.  
  
 Sie können Spalten auch als IsBig angeben, wenn eine Spalte große numerische Werte oder numerische Werte mit hoher Genauigkeit enthält.  
  
 Die Transformation für das Aggregieren ist asynchron. Das heißt, sie verwendet und veröffentlicht Daten nicht zeilenweise. Vielmehr verwendet sie das gesamte Rowset, führt Gruppierungen und Aggregationen aus und veröffentlicht dann die Ergebnisse.  
  
 Diese Transformation übergibt keine Spalten, sondern erstellt im Datenfluss für die veröffentlichten Daten neue Spalten. Nur die Eingabespalten, für die Aggregatfunktionen gelten, oder die Eingabespalten, die die Transformation zum Gruppieren verwendet, werden in die Transformationsausgabe kopiert. Angenommen, eine Transformation für das Aggregieren weist drei Spalten auf: **CountryRegion**, **City**und **Population**. Die Transformation gruppiert nach der **CountryRegion** -Spalte und wendet die SUM-Funktion auf die **Population** -Spalte an. Deshalb ist in der Ausgabe die **City** -Spalte nicht enthalten.  
  
 Sie können der Transformation für das Aggregieren auch mehrere Ausgaben hinzufügen und jede Aggregation an eine andere Ausgabe weiterleiten. Wendet beispielsweise die Transformation für das Aggregieren die Funktionen Sum und Average an, kann jede Aggregation an eine andere Ausgabe geleitet werden.  
  
 Auf eine einzelne Eingabespalte können mehrere Aggregationen angewendet werden. Wenn Sie z.B. die Sum- und Average-Werte für eine Eingabespalte mit dem Namen **Sales**haben möchten, können Sie die Transformation so konfigurieren, dass sie die Sum-Funktion und die Average-Funktion auf die **Sales** -Spalte anwendet.  
  
 Die Transformation für das Aggregieren weist je eine Eingabe und mindestens eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Transformations-Editor für Aggregieren** festlegen können:  
  
-   [Transformations-Editor für Aggregieren &#40;Registerkarte Aggregationen&#41;](../../aggregate-transformation-editor-aggregations-tab.md)  
  
-   [Transformations-Editor für Aggregieren &#40;Registerkarte Erweitert&#41;](../../aggregate-transformation-editor-advanced-tab.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
-   [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
