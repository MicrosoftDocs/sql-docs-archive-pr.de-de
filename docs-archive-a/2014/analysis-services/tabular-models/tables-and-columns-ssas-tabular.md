---
title: Tabellen und Spalten (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f23b21ce492fd3160df727c1562ee706848fa99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723105"
---
# <a name="tables-and-columns-ssas-tabular"></a>Tabellen und Spalten (SSAS – tabellarisch)
  Nachdem Sie einem Modell mit dem Tabellenimport-Assistenten Tabellen und Daten hinzugefügt haben, können Sie Tabellen bearbeiten, indem Sie neue Datenspalten hinzufügen, Beziehungen zwischen Tabellen erstellen, Berechnungen zur Erweiterung der Daten definieren sowie die Daten in den Tabellen zur besseren Übersichtlichkeit filtern und sortieren.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_benefits)  
  
-   [Arbeiten mit Tabellen und Spalten](#bkmk_working)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> Vorteile  
 Tabellen in tabellarischen Modellen stellen das Framework bereit, in dem Spalten und andere Metadaten definiert werden. Die Tabellen umfassen:  
  
 **Tabellendefinition**  
 Die Tabellendefinition enthält den Spaltensatz. Spalten können aus einer Datenquelle importiert oder manuell hinzugefügt werden, z. B. mit berechneten Spalten.  
  
 **Tabellen Metadaten**  
 Beziehungen, Measures, Rollen, Perspektiven und eingefügte Daten sind ausnahmslos Metadaten, durch die Objekte innerhalb des Kontexts einer Tabelle definiert werden.  
  
 **Daten**  
 Sobald Sie zum ersten Mal Tabellen importieren, indem Sie den Tabellenimport-Assistenten verwenden oder neue Daten in berechneten Spalten erstellen, werden die Tabellenspalten mit Daten aufgefüllt. Wenn Daten in der Quelle geändert werden oder ein Modell aus dem Arbeitsspeicher entfernt wird, müssen Sie einen Verarbeitungsvorgang ausführen, um die Tabellen erneut mit Daten aufzufüllen.  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_working"></a>Arbeiten mit Tabellen und Spalten  
 Im Modell-Designer werden nicht direkt neue Modelltabellen erstellt. Es wird automatisch eine neue Registerkarte erstellt, wenn Daten aus einer anderen Datenquelle importiert oder kopiert werden. Jede Registerkarte (im Modell-Designer) enthält eine Tabelle mit Daten, z. B.:  
  
-   Eine einzelne Tabelle oder Sicht aus einer relationalen Datenbank oder aus anderen nicht relationalen Quellen, z. B. einem Analysis Services-Cube.  
  
-   Ein aus einem Feed oder einer Textdatei importierter Tabellensatz an Daten.  
  
-   Eine Kombination sowohl aus relationalen Daten als auch aus Tabellendaten (HTML), die kopiert und in die Tabelle eingefügt wurden.  
  
 Wenn Sie Daten importieren, wird jede Tabelle bzw. Sicht, jedes Blatt oder jede Datendatei im Modell-Designer als Tabelle hinzugefügt. Normalerweise fügen Sie Daten aus verschiedenen Quellen auf separaten Registerkarten hinzu. Sie können Daten aber mit **Einfügen** und **Am Ende einfügen**in einer einzelnen Tabelle kombinieren. Weitere Informationen finden Sie unter [Kopieren und Einfügen von Daten &#40;SSAS – tabellarisch&#41;](../copy-and-paste-data-ssas-tabular.md).  
  
 Nachdem Sie alle benötigten Daten hinzugefügt haben, können Sie zusätzliche Beziehungen zwischen den Tabellen erstellen, verknüpfte Werte in anderen Tabellen suchen oder darauf verweisen oder abgeleitete Werte durch das Hinzufügen von neuen berechneten Spalten erstellen.  
  
 Bei Verwendung sehr umfangreicher Datasets können Sie bestimmte Daten herausfiltern, damit sie nicht sichtbar sind. Außerdem möchten Sie Daten u. U. auch in einer anderen Reihenfolge sortieren. Im Modell-Designer können Sie Funktionen zum Filtern, Sortieren und Ausblenden verwenden, um ganze Spalten oder bestimmte Daten anzuzeigen bzw. auszublenden.  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Hinzufügen von Spalten zu einer Tabelle &#40;SSAS – tabellarisch&#41;](add-columns-to-a-table-ssas-tabular.md)|Beschreibt, wie einer Tabellendefinition eine Quellspalte hinzugefügt wird.|  
|[Löschen einer Spalte &#40;SSAS – tabellarisch&#41;](delete-a-column-ssas-tabular.md)|Beschreibt, wie eine Modelltabellenspalte mithilfe des Modell-Designers oder mithilfe des Dialogfelds Tabelleneigenschaften gelöscht werden kann.|  
|[Ändern von Tabellen-, Spalten- oder Zeilenfilterzuordnungen &#40;SSAS – tabellarisch&#41;](change-table-column-or-row-filter-mappings-ssas-tabular.md)|Beschreibt, wie Tabellen-, Spalten- oder Zeilenfilterzuordnungen mit der Tabellenvorschau oder dem SQL-Abfrage-Editor im Dialogfeld Tabelleneigenschaften bearbeiten geändert werden.|  
|[Angeben von „Als Datumstabelle markieren“ zur Verwendung mit Zeitintelligenz &#40;SSAS – tabellarisch&#41;](specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|Beschreibt, wie das Dialogfeld Als Datumstabelle markieren verwendet wird, um eine Datumstabelle und eine Spalte mit einem eindeutigen Bezeichner anzugeben. Die Angabe einer Datumstabelle und eines eindeutigen Bezeichners ist bei Verwendung von Zeitintelligenzfunktionen in DAX-Formeln erforderlich.|  
|[Hinzufügen einer Tabelle &#40;SSAS – tabellarisch&#41;](add-a-table-ssas-tabular.md)|Beschreibt, wie eine Tabelle aus einer Datenquelle unter Verwendung einer vorhandenen Datenquellenverbindung hinzugefügt wird.|  
|[Löschen einer Tabelle &#40;SSAS – tabellarisch&#41;](delete-a-table-ssas-tabular.md)|Beschreibt, wie nicht mehr benötigte Tabellen in der Arbeitsbereichsdatenbank des Modells gelöscht werden.|  
|[Umbenennen einer Tabelle oder Spalte &#40;SSAS – tabellarisch&#41;](rename-a-table-or-column-ssas-tabular.md)|Beschreibt, wie eine Tabelle oder eine Spalte umbenannt wird, damit sie im Modell besser identifiziert werden kann.|  
|[Festlegen des Datentyps einer Spalte &#40;SSAS – tabellarisch&#41;](set-the-data-type-of-a-column-ssas-tabular.md)|Beschreibt, wie der Datentyp einer Spalte geändert wird. Der Datentyp definiert, wie Daten in der Spalte gespeichert und dargestellt werden.|  
|[Ausblenden oder Einfrieren von Spalten &#40;SSAS – tabellarisch&#41;](hide-or-freeze-columns-ssas-tabular.md)|Beschreibt, wie Spalten ausgeblendet werden, die nicht angezeigt werden sollen, und wie ein Bereich eines Modells sichtbar bleibt, während Sie einen Bildlauf zu einem anderen Bereich des Modells durchführen, indem Sie bestimmte Spalten in einem Bereich fixieren (Sperren).|  
|[Berechnete Spalten &#40;SSAS – tabellarisch&#41;](ssas-calculated-columns.md)|In den Themen in diesem Abschnitt wird beschrieben, wie dem Modell mithilfe berechneter Spalten aggregierte Daten hinzugefügt werden.|  
|[Filtern und Sortieren von Daten &#40;SSAS – tabellarisch&#41;](../filter-and-sort-data-ssas-tabular.md)|In den Themen in diesem Abschnitt wird beschrieben, wie Daten mit den Steuerelementen im Modell-Designer gefiltert oder sortiert werden.|  
  
  
