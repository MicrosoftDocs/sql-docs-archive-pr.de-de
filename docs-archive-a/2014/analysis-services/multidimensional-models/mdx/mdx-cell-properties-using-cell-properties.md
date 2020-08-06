---
title: Verwenden von Zell Eigenschaften (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic cell properties [MDX]
- cells [MDX]
- cell properties [MDX]
- CELL PROPERTIES keyword
ms.assetid: a593c74d-8c5e-485e-bd92-08f9d22451d4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 996b873bfd52f1d695eb613d1fd407decbf493c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618364"
---
# <a name="using-cell-properties-mdx"></a>Verwenden von Zelleigenschaften (MDX)
  Zelleigenschaften in MDX (Multidimensional Expressions) enthalten Informationen zum Inhalt und Format von Zellen in einer mehrdimensionalen Datenquelle, wie einem Cube.  
  
 MDX unterstützt das CELL PROPERTIES-Schlüsselwort in einer MDX-Anweisung zum Abrufen von systeminternen Zelleigenschaften. Systeminterne Zelleigenschaften werden am häufigsten für die visuelle Darstellung von Zellendaten verwendet.  
  
## <a name="cell-properties-keyword-syntax"></a>Syntax des CELL PROPERTIES-Schlüsselworts  
 Das `CELL PROPERTIES`-Schlüsselwort der MDX-`SELECT`-Anweisung hat folgende Syntax:  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 Die folgende Syntax zeigt das Format des `<cell_props>`-Werts und zeigt, wie für diesen Wert das `CELL PROPERTIES`-Schlüsselwort zusammen mit systeminternen Zelleigenschaften verwendet wird:  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>Unterstützte systeminterne Zelleigenschaften  
 In der folgenden Tabelle sind die unterstützten systeminternen Zelleigenschaften aufgelistet, die im `<property>` -Wert verwendet werden.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|`ACTION_TYPE`|Eine Bitmaske, die die Arten der Aktionen für die Zelle angibt. Diese Eigenschaft kann einen der folgenden Werte haben:<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> Hinweis: Drillthroughaktionen werden nicht für Abfragen eingeschlossen, die in der WHERE-Klausel eine Menge enthalten.|  
|**BACK_COLOR**|Die Hintergrundfarbe zum Anzeigen der `VALUE`- oder der `FORMATTED_VALUE`-Eigenschaft. Weitere Informationen finden Sie unter [FORE_COLOR und BACK_COLOR – Inhalte &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`CELL_ORDINAL`|Die Ordinalzahl der Zelle im Dataset.|  
|**FONT_FLAGS**|Die Bitmaske, die Auswirkungen auf die Schriftart detailliert angibt. Der Wert 5 stellt z. B. die Kombination der Schriftarteffekte Fett (`MDFF_BOLD`) und Unterstrichen (`MDFF_UNDERLINE`) dar. Der Wert ist das Ergebnis einer bitweisen OR-Operation von einem oder mehreren der folgenden Konstanten:<br /><br /> `MDFF_BOLD` = 1<br /><br /> `MDFF_ITALIC` = 2<br /><br /> `MDFF_UNDERLINE` = 4<br /><br /> `MDFF_STRIKEOUT` = 8|  
|**FONT_NAME**|Die Schriftart, die für das Anzeigen der `VALUE`- oder `FORMATTED_VALUE`-Eigenschaft verwendet werden soll.|  
|**FONT_SIZE**|Der Schriftgrad, der für das Anzeigen der `VALUE`- oder `FORMATTED_VALUE`-Eigenschaft verwendet werden soll.|  
|**FORE_COLOR**|Die Vordergrundfarbe zum Anzeigen der `VALUE`- oder der `FORMATTED_VALUE`-Eigenschaft. Weitere Informationen finden Sie unter [FORE_COLOR und BACK_COLOR – Inhalte &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`FORMAT`|Wie in `FORMAT_STRING`.|  
|`FORMAT_STRING`|Die Formatzeichenfolge, mit der der Wert der `FORMATTED_VALUE`-Eigenschaft erstellt wird. Weitere Informationen finden Sie unter [FORMAT_STRING-Inhalt &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md).|  
|`FORMATTED_VALUE`|Die Zeichenfolge, die eine formatierte Anzeige der `VALUE`-Eigenschaft darstellt.|  
|`LANGUAGE`|Das Gebietsschema, in dem `FORMAT_STRING` verwendet wird. `LANGUAGE` wird i. d. R. zur Währungskonvertierung verwendet.|  
|`UPDATEABLE`|Ein Wert, der angibt, ob die Zelle aktualisiert werden kann. Diese Eigenschaft kann einen der folgenden Werte haben:<br /><br /> `MD_MASK_ENABLED`(0x00000000) die Zelle kann aktualisiert werden.<br /><br /> `MD_MASK_NOT_ENABLED`(0x10000000) die Zelle kann nicht aktualisiert werden.<br /><br /> `CELL_UPDATE_ENABLED`(0x00000001) die Zelle kann im Cellset aktualisiert werden.<br /><br /> `CELL_UPDATE_ENABLED_WITH_UPDATE`(0x00000002) die Zelle kann mit einer Update-Anweisung aktualisiert werden. Das Update kann einen Fehler erzeugen, wenn eine Blattzelle aktualisiert werden soll, für die der Schreibzugriff nicht aktiviert ist.<br /><br /> `CELL_UPDATE_NOT_ENABLED_FORMULA`(0x10000001) die Zelle kann nicht aktualisiert werden, da die Zelle über ein berechnetes Element unter den Koordinaten verfügt. die Zelle wurde mit einer Menge in der WHERE-Klausel abgerufen. Eine Zelle kann selbst dann aktualisiert werden, wenn sich eine Formel oder eine berechnete Zelle auf den Wert der Zelle auswirkt (sich irgendwo im Verlauf des Aggregationspfades befindet). In diesem Szenario ist der endgültige Wert der Zelle möglicherweise nicht mit dem aktualisierten Wert identisch, weil sich die Berechnung auf das Ergebnis ausgewirkt hat.<br /><br /> `CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE`(0x10000002) die Zelle kann nicht aktualisiert werden, da keine Summen Measures (count, min, Max, distincount, semiadditiv) nicht aktualisiert werden können.<br /><br /> `CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE`(0x10000003) die Zelle kann nicht aktualisiert werden, da die Zelle nicht vorhanden ist, da Sie sich an der Schnittmenge eines Measures und einem Dimensions Element befindet, das nicht mit der Measure-Gruppe des Measures verknüpft ist.<br /><br /> `CELL_UPDATE_NOT_ENABLED_SECURE`(0x10000005) die Zelle kann nicht aktualisiert werden, da die Zelle gesichert ist.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CALCLEVEL`(0x10000006) für zukünftige Verwendung reserviert.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE`(0x10000007) die Zelle kann wegen interner Gründe nicht aktualisiert werden.<br /><br /> `CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE`(0x10000009) die Zelle kann nicht aktualisiert werden, da das Update in Mining Modell-, indirekten oder Data Mining Dimensionen nicht unterstützt wird.|  
|`VALUE`|Der unformatierte Wert der Zelle.|  
  
 Nur die Zelleigenschaften `CELL_ORDINAL`, `FORMATTED_VALUE` und `VALUE` sind erforderlich. Alle Zelleigenschaften, systeminterne wie anbieterspezifische, sind einschließlich ihrer Datentypen und der Anbieterunterstützung im `PROPERTIES`-Schemarowset definiert. Weitere Informationen zum `PROPERTIES` Schemarowset finden Sie unter [MDSCHEMA_PROPERTIES-Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset).  
  
 Wenn das `CELL PROPERTIES`-Schlüsselwort nicht angegeben ist, werden standardmäßig die Zelleigenschaften `VALUE`, `FORMATTED_VALUE` und `CELL_ORDINAL` (in dieser Reihenfolge) zurückgegeben. Ist das `CELL PROPERTIES`-Schlüsselwort angegeben, werden nur die Zelleigenschaften zurückgegeben, die explizit mit dem Schlüsselwort angegeben sind.  
  
 Das folgende Beispiel zeigt die Verwendung des `CELL PROPERTIES`-Schlüsselworts in einer MDX-Abfrage:  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 Für MDX-Abfragen, die vereinfachte Rowsets zurückgeben, werden keine Zelleigenschaften zurückgegeben. In diesem Fall wird jede Zelle so dargestellt, als würde nur die Zelleigenschaft `FORMATTED_VALUE` zurückgegeben.  
  
## <a name="setting-cell-properties"></a>Festlegen von Zelleigenschaften  
 Zell Eigenschaften können in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] an verschiedenen Stellen festgelegt werden. Beispielsweise kann die Eigenschaft Formatzeichenfolge für reguläre Measures auf der Registerkarte Cubestruktur des Cube-Editors in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]festgelegt werden. Die gleiche Eigenschaft kann für im Cube definierte berechnete Measures auf der Registerkarte Berechnungen des Cube-Editors festgelegt werden. Dort wird auch die Formatzeichenfolge von berechneten Measures definiert, die ihrerseits in der WITH-Klausel einer Abfrage definiert sind. Die folgende Abfrage veranschaulicht, wie Zelleigenschaften für ein berechnetes Measure festgelegt werden können:  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
