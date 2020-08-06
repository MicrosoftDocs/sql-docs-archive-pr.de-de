---
title: Statistik | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistical information [SQL Server], query optimization
- query performance [SQL Server], statistics
- query optimization statistics [SQL Server]
- statistical information [SQL Server], database options
- query optimization statistics [SQL Server], about query optimization statistics
- statistical information [SQL Server], guidelines
- statistical information [SQL Server]
- using statistics [SQL Server]
- statistical information [SQL Server], indexes
- index statistics [SQL Server]
- query optimizer [SQL Server], statistics
- statistics [SQL Server]
ms.assetid: b86a88ba-4f7c-4e19-9fbd-2f8bcd3be14a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0f0950e48245bed53581d2f91b120ab9555aa562
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621411"
---
# <a name="statistics"></a>Statistik
  Der Abfrageoptimierer verwendet Statistiken zum Erstellen von Abfrageplänen, die die Abfrageleistung verbessern. Bei den meisten Abfragen generiert der Abfrageoptimierer automatisch die notwendigen Statistiken für einen hochwertigen Abfrageplan. In einigen Fällen müssen Sie weitere Statistiken erstellen oder den Abfrageentwurf ändern, um optimale Ergebnisse zu erzielen. Dieses Thema enthält eine Erläuterung von Statistikkonzepten sowie Richtlinien zur effektiven Verwendung von Abfrageoptimierungsstatistiken.  
  
##  <a name="components-and-concepts"></a><a name="DefinitionQOStatistics"></a> Komponenten und Konzepte  
 Statistik  
 Statistiken zur Abfrageoptimierung sind Objekte, die statistische Informationen über die Verteilung von Werten in Spalten einer Tabelle oder indizierten Sicht enthalten. Der Abfrageoptimierer verwendet diese Statistiken, um die *Kardinalität*oder Anzahl von Zeilen im Abfrageergebnis zu schätzen. Diese *Kardinalitätsschätzungen* ermöglichen es dem Abfrageoptimierer, einen hochwertigen Abfrageplan zu erstellen. Beispielsweise kann der Abfrageoptimierer Kardinalitätsschätzungen verwenden, um statt des ressourcenintensiveren Index Scan-Operators den Index Seek-Operator auszuwählen und so die Abfrageleistung zu verbessern.  
  
 Jedes Statistikobjekt wird für eine Liste mit mindestens einer Tabellenspalte erstellt und enthält ein Histogramm, das die Verteilung von Werten in der ersten Spalte anzeigt. Statistikobjekte, die sich auf mehrere Spalten beziehen, enthalten außerdem statistische Informationen über die spaltenübergreifende Korrelation von Werten. Diese Korrelationsstatistiken oder *Dichten*werden von der Anzahl unterschiedlicher Zeilen mit Spaltenwerten abgeleitet. Weitere Informationen zu Statistikobjekten finden Sie unter [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).  
  
 Gefilterte Statistiken  
 Gefilterte Statistiken können die Abfrageleistung für Abfragen verbessern, bei denen aus klar definierten Teilmengen von Daten ausgewählt wird. Gefilterte Statistiken verwenden ein Filterprädikat, um die Teilmenge von Daten auszuwählen, die in der Statistik enthalten ist. Sorgfältig entworfene gefilterte Statistiken können den Abfrageausführungsplan im Vergleich zu Tabellenstatistiken verbessern. Weitere Informationen zum Filterprädikat finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql). Weitere Informationen zum Zeitpunkt der Erstellung von gefilterten Statistiken finden Sie im Abschnitt [Zeitpunkt der Erstellung von Statistiken](#UpdateStatistics) in diesem Thema. Eine Fallstudie finden Sie im Blogbeitrag [Using Filtered Statistics with Partitioned Tables](https://go.microsoft.com/fwlink/?LinkId=178505)(Verwenden von gefilterten Statistiken mit partitionierten Tabellen) auf der SQLCAT-Website.  
  
 Statistikoptionen  
 Anhand von drei Optionen können Sie festlegen, wann und wie Statistiken erstellt und aktualisiert werden. Diese Optionen werden nur auf Datenbankebene festgelegt.  
  
 AUTO_CREATE_STATISTICS (Option)  
 Ist die AUTO_CREATE_STATISTICS-Option zum automatischen Erstellen von Statistiken aktiviert, erstellt der Abfrageoptimierer nach Bedarf Statistiken für einzelne Spalten im Abfrageprädikat, um Kardinalitätsschätzungen für den Abfrageplan zu verbessern. Diese Statistiken für einzelne Spalten werden für Spalten erstellt, die noch nicht über ein Histogramm in einem vorhandenen Statistikobjekt verfügen. Durch die AUTO_CREATE_STATISTICS-Option wird nicht festgelegt, ob Statistiken für Indizes erstellt werden. Durch diese Option werden auch keine gefilterten Statistiken generiert. Sie gilt ausschließlich für Statistiken für einzelne Spalten der gesamten Tabelle.  
  
 Erstellt der Abfrageoptimierer Statistiken als Ergebnis der Verwendung der AUTO_CREATE_STATISTICS-Option, beginnt der Statistikname mit `_WA`. Mithilfe der folgenden Abfrage können Sie bestimmen, ob der Abfrageoptimierer Statistiken für eine Abfrageprädikatsspalte erstellt hat.  
  
```  
SELECT OBJECT_NAME(s.object_id) AS object_name,  
    COL_NAME(sc.object_id, sc.column_id) AS column_name,  
    s.name AS statistics_name  
FROM sys.stats AS s JOIN sys.stats_columns AS sc  
    ON s.stats_id = sc.stats_id AND s.object_id = sc.object_id  
WHERE s.name like '_WA%'  
ORDER BY s.name;  
```  
  
 AUTO_UPDATE_STATISTICS (Option)  
 Wenn die AUTO_UPDATE_STATISTICS-Option zur automatischen Aktualisierung von Statistiken aktiviert ist, stellt der Abfrageoptimierer fest, wann Statistiken veraltet sein könnten, und aktualisiert diese Statistiken, sobald sie von einer Abfrage verwendet werden. Statistiken sind veraltet, wenn die Datenverteilung in der Tabelle oder indizierten Sicht durch die Vorgänge INSERT, UPDATE, DELETE oder MERGE geändert wurde. Der Abfrageoptimierer stellt fest, wann Statistiken veraltet sein könnten, indem er die Anzahl der Datenänderungen seit des letzten Statistikupdates ermittelt und sie mit einem Schwellenwert vergleicht. Der Schwellenwert basiert auf der Anzahl von Zeilen in der Tabelle oder indizierten Sicht.  
  
 Bevor der Abfrageoptimierer eine Abfrage kompiliert und einen zwischengespeicherten Abfrageplan ausführt, sucht er nach veralteten Statistiken. Vor dem Kompilieren einer Abfrage ermittelt der Abfrageoptimierer anhand der Spalten, Tabellen und indizierten Sichten im Abfrageprädikat, welche Statistiken veraltet sein könnten. Vor dem Ausführen eines zwischengespeicherten Abfrageplans überprüft das [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , ob der Abfrageplan auf aktuelle Statistiken verweist.  
  
 Die AUTO_UPDATE_STATISTICS-Option gilt für Statistikobjekte, die für Indizes, einzelne Spalten in Abfrageprädikaten und mit der [CREATE STATISTICS](/sql/t-sql/statements/create-statistics-transact-sql) -Anweisung generierte Statistiken erstellt wurden. Diese Option gilt auch für gefilterte Statistiken.  
  
 AUTO_UPDATE_STATISTICS_ASYNC  
 Mit der AUTO_UPDATE_STATISTICS_ASYNC-Option für die asynchrone Statistikaktualisierung wird festgelegt, ob der Abfrageoptimierer die synchrone oder asynchrone Statistikaktualisierung verwendet. Die Option für das asynchrone Statistikupdate ist standardmäßig deaktiviert, sodass der Abfrageoptimierer Statistiken synchron aktualisiert. Die AUTO_UPDATE_STATISTICS_ASYNC-Option gilt für Statistikobjekte, die für Indizes, einzelne Spalten in Abfrageprädikaten und mit der [CREATE STATISTICS](/sql/t-sql/statements/create-statistics-transact-sql) -Anweisung generierte Statistiken erstellt wurden.  
  
 Statistikaktualisierungen können entweder synchron (Standard) oder asynchron sein. Bei synchronen Statistikupdates werden Abfragen immer anhand aktueller Statistiken kompiliert und ausgeführt. Wenn Statistiken veraltet sind, wartet der Abfrageoptimierer auf aktualisierte Statistiken, bevor er die Abfrage kompiliert und ausführt. Bei asynchronen Statistikupdates werden Abfragen anhand vorhandener Statistiken kompiliert, auch wenn diese veraltet sind. Der Abfrageoptimierer könnte einen suboptimalen Abfrageplan auswählen, wenn die Statistiken beim Kompilieren der Abfrage veraltet sind. Wenn Abfragen nach dem Ausführen asynchroner Updates kompiliert werden, hat dies den Vorteil, dass für die Abfragen aktualisierte Statistiken verwendet werden.  
  
 Verwenden Sie ggf. synchrone Statistiken, wenn Sie Vorgänge ausführen, die die Verteilung der Daten ändern, beispielsweise das Kürzen einer Tabelle oder das Ausführen eines Massenupdates für einen großen Zeilenprozentsatz. Wenn Sie nach dem Abschließen des Vorgangs die Statistiken nicht aktualisieren, wird mithilfe von synchronen Statistiken sichergestellt, dass Statistiken vor dem Ausführen von Abfragen über die geänderten Daten aktuell sind.  
  
 In den folgenden Szenarien empfiehlt sich die Verwendung asynchroner Statistiken, um besser vorhersagbare Antwortzeiten für Abfragen zu erzielen:  
  
-   Häufig werden von der Anwendung die gleichen Abfragen, ähnliche Abfragen bzw. ähnliche zwischengespeicherte Abfragepläne ausgeführt. Bei Verwendung asynchroner Statistikupdates können die Antwortzeiten für Abfragen vorhersagbarer sein als bei synchronen Statistikupdates, weil der Abfrageoptimierer eingehende Abfragen direkt ausführen kann, ohne auf aktuelle Statistiken zu warten. Dadurch wird verhindert, dass sich einige Abfragen verzögern und andere nicht.  
  
-   In der Anwendung sind Timeouts bei Clientanforderungen aufgetreten, die dadurch verursacht werden, dass mindestens eine Abfrage auf aktualisierte Statistiken wartet. In einigen Fällen kann das Warten auf synchrone Statistiken dazu führen, dass Anwendungen mit kurzen Timeouts einen Fehler erzeugen.  
  
 INCREMENTAL STATS  
 Bei ON wird die Statistik pro Partition erstellt. Bei OFF wird die Statistikstruktur gelöscht und die Statistik von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu berechnet. Der Standardwert ist OFF. Diese Einstellung überschreibt die INCREMENTAL-Eigenschaft auf Datenbankebene.  
  
 Wenn einer umfangreichen Tabelle neue Partitionen hinzugefügt werden, sollte die Statistik aktualisiert werden, um die neuen Partitionen zu berücksichtigen. Das Scannen der gesamten Tabelle (FULLSCAN- oder SAMPLE-Option) könnte jedoch ziemlich lange dauern. Außerdem ist das Scannen der gesamten Tabelle nicht erforderlich, da ggf. nur die Statistik der neuen Partitionen benötigt wird. Durch die INCREMENTAL-Option werden nur Statistikdaten pro Partition erstellt und gespeichert. Beim Update werden nur die Statistiken der Partitionen aktualisiert, die eine neue Statistik erfordern.  
  
 Wenn Statistiken pro Partition nicht unterstützt werden, wird die Option ignoriert und eine Warnung generiert. Inkrementelle Statistiken werden für folgende Statistiktypen nicht unterstützt:  
  
-   Statistiken, die mit Indizes erstellt wurden, die über keine Partitionsausrichtung mit der Basistabelle verfügen.  
  
-   Statistiken, die mit lesbaren sekundären AlwaysOn-Datenbanken erstellt wurden.  
  
-   Statistiken, die für schreibgeschützte Datenbanken erstellt wurden.  
  
-   Statistiken, die für gefilterte Indizes erstellt wurden.  
  
-   Statistiken, die für Sichten erstellt wurden.  
  
-   Statistiken, die für interne Tabellen erstellt wurden.  
  
-   Statistiken, die mit räumlichen Indizes oder XML-Indizes erstellt wurden.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
##  <a name="when-to-create-statistics"></a><a name="CreateStatistics"></a>Zeitpunkt der Erstellung von Statistiken  
 Der Abfrageoptimierer erstellt automatisch folgende Statistiken:  
  
1.  Bei der Indexerstellung berechnet der Abfrageoptimierer Statistiken für Indizes, die sich auf Tabellen oder Sichten beziehen. Diese Statistiken werden für die Schlüsselspalten des Indexes erstellt. Wenn es sich um einen gefilterten Index handelt, erstellt der Abfrageoptimierer gefilterte Statistiken für die gleiche Teilmenge von Zeilen, die für den gefilterten Index angegeben wurden. Weitere Informationen zu gefilterten Indizes finden Sie unter [Erstellen gefilterter Indizes](../indexes/create-filtered-indexes.md) und [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
2.  Der Abfrageoptimierer erstellt Statistiken für einzelne Spalten in Abfrageprädikaten, wenn AUTO_CREATE_STATISTICS aktiviert ist.  
  
 Bei den meisten Abfragen werden durch diese beiden Methoden zum Erstellen von Statistiken hochwertige Abfragepläne gewährleistet. In einigen Fällen können Sie Abfragepläne verbessern, indem Sie zusätzliche Statistiken mit der [CREATE STATISTICS](/sql/t-sql/statements/create-statistics-transact-sql) -Anweisung erstellen. In diesen zusätzlichen Statistiken können Sie statistische Korrelationen aufzeichnen, die vom Abfrageoptimierer beim Erstellen von Statistiken für Indizes oder einzelne Spalten nicht berücksichtigt werden. Ihre Anwendung kann über zusätzliche statistische Korrelationen in den Tabellendaten verfügen, durch die der Abfrageoptimierer Abfragepläne verbessern kann, wenn sie für die Berechnung von Statistikobjekten zugrunde gelegt werden. Der Abfrageplan kann beispielsweise optimiert werden, indem gefilterte Statistiken für eine Teilmenge von Datenzeilen oder Statistiken für mehrere Spalten für Abfrageprädikatsspalten ausgeführt werden.  
  
 Wenn Statistiken mit der CREATE STATISTICS-Anweisung erstellt werden, empfiehlt es sich, die AUTO_CREATE_STATISTICS-Option aktiviert zu lassen, damit der Abfrageoptimierer weiterhin routinemäßig Statistiken für einzelne Spalten für Abfrageprädikatsspalten erstellt. Weitere Informationen zu Abfrageprädikaten finden Sie unter [Suchbedingung &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).  
  
 Wenn eine der folgenden Bedingungen zutrifft, können Sie die Erstellung von Statistiken mit der CREATE STATISTICS-Anweisung in Erwägung ziehen:  
  
-   Der [!INCLUDE[ssDE](../../../includes/ssde-md.md)] -Optimierungsratgeber schlägt vor, Statistiken zu erstellen.  
  
-   Das Abfrageprädikat enthält mehrere korrelierende Spalten, die sich noch nicht im gleichen Index befinden.  
  
-   Bei der Abfrageausführung wird aus einer Teilmenge von Daten ausgewählt.  
  
-   Statistiken für eine Abfrage fehlen.  
  
### <a name="query-predicate-contains-multiple-correlated-columns"></a>Das Abfrageprädikat enthält mehrere korrelierende Spalten  
 Wenn ein Abfrageprädikat mehrere Spalten mit spaltenübergreifenden Beziehungen und Abhängigkeiten enthält, könnte der Abfrageplan durch Statistiken für mehrere Spalten optimiert werden. Statistiken für mehrere Spalten enthalten spaltenübergreifende Korrelationsstatistiken, so genannte *Dichten*, die in Statistiken für einzelne Spalten nicht verfügbar sind. Durch Dichten können Kardinalitätsschätzungen verbessert werden, wenn Abfrageergebnisse von Datenbeziehungen zwischen mehreren Spalten abhängig sind.  
  
 Wenn sich die Spalten bereits im gleichen Index befinden, ist das Statistikobjekt für mehrere Spalten bereits vorhanden und muss nicht manuell erstellt werden. Wenn sich die Spalten noch nicht im gleichen Index befinden, können Sie Statistiken für mehrere Spalten erstellen, indem Sie einen Index für die Spalten anlegen oder die CREATE STATISTICS-Anweisung verwenden. Zur Verwaltung eines Indexes werden mehr Systemressourcen benötigt als zur Verwaltung eines Statistikobjekts. Wenn die Anwendung keinen Index für mehrere Spalten erfordert, können Sie Systemressourcen sparen, indem Sie das Statistikobjekt erstellen, ohne den Index zu generieren.  
  
 Wenn Statistiken für mehrere Spalten erstellt werden, wirkt sich die Reihenfolge der Spalten in der Statistikobjektdefinition darauf aus, wie effektiv die Dichten beim Erstellen von Kardinalitätsschätzungen sind. Im Statistikobjekt werden Dichten für jedes Präfix von Schlüsselspalten in der Statistikobjektdefinition gespeichert. Weitere Informationen zu Dichten finden Sie unter [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql).  
  
 Zum Erstellen von Dichten, die für Kardinalitätsschätzungen hilfreich sind, müssen die Spalten im Abfrageprädikat einem der Spaltenpräfixe in der Statistikobjektdefinition entsprechen. Im Folgenden wird beispielsweise aus den Spalten `LastName`, `MiddleName`und `FirstName`ein Objekt für eine Statistik für mehrere Spalten erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.stats  
    WHERE name = 'LastFirst'  
    AND object_ID = OBJECT_ID ('Person.Person'))  
DROP STATISTICS Person.Person.LastFirst;  
GO  
CREATE STATISTICS LastFirst ON Person.Person (LastName, MiddleName, FirstName);  
GO  
```  
  
 In diesem Beispiel verfügt das Statistikobjekt `LastFirst` über Dichten für die folgenden Spaltenpräfixe: (`LastName`), (`LastName, MiddleName`) und (`LastName, MiddleName, FirstName`). Für (`LastName, FirstName`) ist keine Dichte verfügbar. Wenn in der Abfrage `LastName` und `FirstName` ohne `MiddleName`verwendet werden, ist die Dichte für Kardinalitätsschätzungen nicht verfügbar.  
  
### <a name="query-selects-from-a-subset-of-data"></a>Bei der Abfrageausführung wird aus einer Teilmenge von Daten ausgewählt  
 Wenn der Abfrageoptimierer Statistiken für einzelne Spalten und Indizes erstellt, berechnet er Statistiken für die Werte sämtlicher Zeilen. Wenn bei Abfragen aus einer Teilmenge von Zeilen ausgewählt wird und diese Teilmenge über eine eindeutige Datenverteilung verfügt, können Abfragepläne durch gefilterte Statistiken verbessert werden. Sie können gefilterte Statistiken erstellen, indem Sie die CREATE STATISTICS-Anweisung mit der WHERE-Klausel verwenden, um den Filterprädikatausdruck zu definieren.  
  
 Durch die Verwendung von [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]beispielsweise gehört jedes Produkt in der Production.Product-Tabelle zu einer von vier Kategorien in der Production.ProductCategory-Tabelle: Fahrräder, Bauteile, Bekleidung und Zubehör. Jede Kategorie verfügt über eine andere Datenverteilung für das Gewicht: Die Gewichte der Fahrräder reichen von 13,77 bis 30,0, die Gewichte der Bauteile reichen von 2,12 bis 1050,00 mit einigen NULL-Werten, die Gewichte der Bekleidung sind alle NULL, und die Gewichte des Zubehörs sind ebenfalls NULL.  
  
 Bei den Fahrrädern liefern gefilterte Statistiken dem Abfrageoptimierer zu allen Fahrradgewichten genauere Statistikdaten und können die Abfrageplanqualität im Vergleich zu Tabellenstatistiken oder nicht vorhandenen Statistiken für die Weight-Spalte verbessern. Die Spalte mit dem Fahrradgewicht eignet sich besonders für gefilterte Statistiken, jedoch weniger für einen gefilterten Index, wenn nur relativ wenige Suchen nach Gewichtsangaben ausgeführt werden. Die Leistungsvorteile, die gefilterte Indizes bei der Suche bieten, können die zusätzlichen Kosten für Wartung und Speicher, die mit der Implementierung eines gefilterten Indexes in der Datenbank verbunden sind, jedoch nicht aufwiegen.  
  
 Durch die folgende Anweisung wird die gefilterte `BikeWeights` -Statistik für alle Unterkategorien von Fahrrädern erstellt. Durch den gefilterten Prädikatausdruck werden Fahrräder definiert, indem alle Fahrradunterkategorien mit dem Vergleich `Production.ProductSubcategoryID IN (1,2,3)`aufgelistet werden. Das Prädikat kann den Kategorienamen für Fahrräder nicht verwenden, da er in der Production.ProductCategory-Tabelle gespeichert ist; alle Spalten im Filterausdruck müssen sich in der gleichen Tabelle befinden.  
  
 [!code-sql[StatisticsDDL#FilteredStats2](../../snippets/tsql/SQL14/tsql/statisticsddl/transact-sql/filteredstats.sql#filteredstats2)]  
  
 Der Abfrageoptimierer kann die gefilterte Statistik für `BikeWeights` verwenden, um den Abfrageplan für die folgende Abfrage zu verbessern, bei der alle Fahrräder ausgewählt werden, deren Gewicht größer ist als `25`.  
  
```  
SELECT P.Weight AS Weight, S.Name AS BikeName  
FROM Production.Product AS P  
    JOIN Production.ProductSubcategory AS S   
    ON P.ProductSubcategoryID = S.ProductSubcategoryID  
WHERE P.ProductSubcategoryID IN (1,2,3) AND P.Weight > 25  
ORDER BY P.Weight;  
GO  
```  
  
### <a name="query-identifies-missing-statistics"></a>Abfrage identifiziert fehlende Statistiken  
 Wenn der Abfrageoptimierer aufgrund eines Fehlers oder eines anderen Ereignisses keine Statistiken erstellen kann, erstellt er den Abfrageplan ohne Verwendung von Statistiken. Der Abfrageoptimierer kennzeichnet die Statistik als nicht vorhanden und versucht beim nächsten Ausführen der Abfrage, die Statistik erneut zu generieren.  
  
 Fehlende Statistiken werden als Warnungen angegeben (Tabellenname als rot formatierter Text), wenn der Ausführungsplan einer Abfrage mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]grafisch angezeigt wird. Das Fehlen von Statistiken wird zudem angezeigt, wenn die **Missing Column Statistics**-Ereignisklasse mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] überwacht wird. Weitere Informationen finden Sie unter [Fehler und Warnungen-Ereigniskategorie &#40;Datenbank-Engine&#41;](../event-classes/errors-and-warnings-event-category-database-engine.md).  
  
 Wenn Statistiken fehlen, führen Sie die folgenden Schritte aus:  
  
-   Überprüfen Sie, ob AUTO_CREATE_STATISTICS und AUTO_UPDATE_STATISTICS aktiviert sind.  
  
-   Stellen Sie sicher, dass die Datenbank nicht schreibgeschützt ist. Wenn die Datenbank schreibgeschützt ist, können vom Abfrageoptimierer keine Statistiken gespeichert werden.  
  
-   Erstellen Sie die fehlende Statistik mithilfe der CREATE STATISTICS-Anweisung.  
  
 Fehlen Statistiken über eine schreibgeschützte Datenbank oder Momentaufnahme oder sind diese veraltet, erstellt [!INCLUDE[ssDE](../../../includes/ssde-md.md)] temporäre Statistiken in `tempdb` und behält diese bei. Wenn das [!INCLUDE[ssDE](../../../includes/ssde-md.md)] temporäre Statistiken erstellt, wird dem Statistiknamen das _readonly_database_statistic-Suffix angefügt, um die temporären Statistiken von den dauerhaften Statistiken zu unterscheiden. Das Suffix „_readonly_database_statistic“ ist für von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]generierte Statistiken reserviert. Skripts für die temporären Statistiken können erstellt und auf einer Datenbank mit Lese-/Schreibzugriff reproduziert werden. Bei einer Skripterstellung ändert [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] das Suffix des Statistiknamens von _readonly_database_statistic zu _readonly_database_statistic_scripted.  
  
 Nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann temporäre Statistiken erstellen und aktualisieren. Sie können jedoch temporäre Statistiken löschen und Statistikeigenschaften mit den gleichen Tools überwachen, die Sie für dauerhafte Statistiken verwenden:  
  
-   Löschen Sie temporäre Statistiken mit der Anweisung [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql) -Anweisung generierte Statistiken erstellt wurden.  
  
-   Überwachen Sie Statistiken mit den Katalogsichten **sys.stats** und **sys.stats_columns** . **sys_stats** beinhaltet die Spalte **is_temporary** . Damit wird angegeben, welche Statistiken dauerhaft und welche temporär sind.  
  
 Da temporäre Statistiken in `tempdb` gespeichert werden, werden durch einen Neustart des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Diensts alle temporären Statistiken entfernt.  
  
##  <a name="when-to-update-statistics"></a><a name="UpdateStatistics"></a>Zeitpunkt der Statistik Aktualisierung  
 Der Abfrageoptimierer stellt fest, wann Statistiken veraltet sein könnten, und aktualisiert sie, sobald sie für einen Abfrageplan benötigt werden. In einigen Fällen können Sie den Abfrageplan und damit die Abfrageleistung verbessern, indem Sie Statistiken häufiger aktualisieren, als dies bei Aktivierung von AUTO_UPDATE_STATISTICS der Fall ist. Sie können Statistiken mit der UPDATE STATISTICS-Anweisung oder der gespeicherten Prozedur sp_updatestats aktualisieren.  
  
 Durch das Update von Statistiken wird sichergestellt, dass Abfragen anhand aktueller Statistiken kompiliert werden. Dies führt jedoch dazu, dass Abfragen neu kompiliert werden. Es empfiehlt sich, Statistiken nicht zu oft zu aktualisieren und die Vorteile optimierter Abfragepläne gegen den Zeitaufwand für die Neukompilierung von Abfragen abzuwägen. Die Entscheidung hängt von der verwendeten Anwendung ab.  
  
 Beim Aktualisieren von Statistiken mit UPDATE STATISTICS oder sp_updatestats empfiehlt es sich, AUTO_UPDATE_STATISTICS aktiviert zu lassen, damit der Abfrageoptimierer die Statistiken weiterhin routinemäßig aktualisiert. Weitere Informationen zum Aktualisieren von Statistiken für eine Spalte, einen Index, eine Tabelle oder eine indizierte Sicht finden Sie unter [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql). Informationen zum Aktualisieren von Statistiken für alle benutzerdefinierten und internen Tabellen in der Datenbank finden Sie in der Beschreibung der gespeicherten Prozedur [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).  
  
 Um zu ermitteln, wann Statistiken zuletzt aktualisiert wurden, verwenden Sie die [STATS_DATE](/sql/t-sql/functions/stats-date-transact-sql) -Funktion.  
  
 Ziehen Sie die Aktualisierung von Statistiken unter folgenden Bedingungen in Betracht:  
  
-   Die Ausführungszeiten von Abfragen sind langsam.  
  
-   Es werden INSERT-Vorgänge für aufsteigend oder absteigend sortierte Schlüsselspalten ausgeführt.  
  
-   Eine Wartung wurde durchgeführt.  
  
### <a name="query-execution-times-are-slow"></a>Die Ausführungszeiten von Abfragen sind langsam  
 Wenn die Antwortzeiten von Abfragen langsam oder nicht vorhersagbar sind, sollten Sie sicherstellen, dass Abfragen auf aktuelle Statistiken zugreifen, bevor Sie weitere Schritte zur Problembehandlung ausführen.  
  
### <a name="insert-operations-occur-on-ascending-or-descending-key-columns"></a>Es werden INSERT-Vorgänge für aufsteigend oder absteigend sortierte Schlüsselspalten ausgeführt  
 Statistiken für aufsteigend oder absteigend sortierte Schlüsselspalten, z. B. IDENTITY-Spalten oder Spalten mit Echtzeit-Zeitstempeln, können häufigere Statistikupdates erfordern, als sie vom Abfrageoptimierer ausgeführt werden. Durch INSERT-Vorgänge werden neue Werte an aufsteigend oder absteigend sortierte Spalten angefügt. Möglicherweise wurden zu wenige Zeilen hinzugefügt, um ein Statistikupdate auszulösen. Wenn Statistiken nicht aktuell sind und bei der Abfrageausführung aus den zuletzt hinzugefügten Zeilen ausgewählt wird, weisen die aktuellen Statistiken keine Kardinalitätsschätzungen für diese neuen Werte auf. Dies kann zu ungenauen Kardinalitätsschätzungen und einer langsamen Abfrageleistung führen.  
  
 Eine Abfrage, die aus den letzten Bestelldaten auswählt, verfügt z. B. über ungenaue Kardinalitätsschätzungen, wenn die Statistiken nicht aktualisiert werden, um Kardinalitätsschätzungen für die letzten Bestelldaten einzuschließen.  
  
### <a name="after-maintenance-operations"></a>Eine Wartung wurde durchgeführt  
 Die Aktualisierung von Statistiken empfiehlt sich auch nach dem Durchführen von Wartungsvorgängen, durch die die Verteilung der Daten geändert wird; hierzu gehören z. B. das Abschneiden einer Tabelle oder das Ausführen einer Masseneinfügung für einen großen Prozentsatz von Zeilen. Dadurch lassen sich zukünftige Verzögerungen bei der Abfrageverarbeitung vermeiden, d. h., Abfragen müssen nicht auf automatische Statistikupdates warten.  
  
 Vorgänge wie das Neuerstellen, Defragmentieren oder Neuorganisieren eines Indexes wirken sich nicht auf die Verteilung von Daten aus. Folglich müssen Sie keine Statistiken aktualisieren, nachdem Sie die Vorgänge ALTER INDEX REBUILD, DBCC REINDEX, DBCC INDEXDEFRAG oder ALTER INDEX REORGANIZE ausgeführt haben. Der Abfrageoptimierer aktualisiert Statistiken, wenn mit ALTER INDEX REBUILD oder DBCC DBREINDEX ein Index für eine Tabelle oder Sicht erstellt wird. Dieses Statistikupdate tritt jedoch als Nebenprodukt der Indexneuerstellung auf. Der Abfrageoptimierer führt keine Statistikaktualisierung nach einem DBCC INDEXDEFRAG-Vorgang oder ALTER INDEX REORGANIZE-Vorgang aus.  
  
##  <a name="queries-that-use-statistics-effectively"></a><a name="DesignStatistics"></a>Abfragen, die Statistiken effektiv verwenden  
 Bestimmte Abfrageimplementierungen, z. B. lokale Variablen und komplexe Ausdrücke im Abfrageprädikat, können zu suboptimalen Abfrageplänen führen. Sie können dies verhindern, indem Sie Abfrageentwurfsrichtlinien für die effektive Verwendung von Statistiken befolgen. Weitere Informationen zu Abfrageprädikaten finden Sie unter [Suchbedingung &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).  
  
 Zur Optimierung von Abfrageplänen können Sie Abfrageentwurfsrichtlinien anwenden, die Statistiken effektiv einsetzen, um *Kardinalitätsschätzungen* für Ausdrücke, Variablen und Funktionen in Abfrageprädikaten zu verbessern. Wenn der Abfrageoptimierer den Wert eines Ausdrucks, einer Variablen oder Funktion nicht kennt, weiß er nicht, welchen Wert er im Histogramm suchen soll. Folglich kann nicht die beste Kardinalitätsschätzung aus dem Histogramm abgerufen werden. Für alle als Stichprobe entnommenen Zeilen im Histogramm verwendet der Abfrageoptimierer stattdessen die durchschnittliche Anzahl von Zeilen pro eindeutigem Wert als Basis für die Kardinalitätsschätzung. Dies führt zu suboptimalen Kardinalitätsschätzungen und kann die Abfrageleistung beeinträchtigen.  
  
 In den folgenden Richtlinien wird beschrieben, wie Abfragen geschrieben werden müssen, um Abfragepläne durch optimierte Kardinalitätsschätzungen zu verbessern.  
  
### <a name="improving-cardinality-estimates-for-expressions"></a>Verbessern von Kardinalitätsschätzungen für Ausdrücke  
 Um Kardinalitätsschätzungen für Ausdrücke zu verbessern, beachten Sie die folgenden Richtlinien:  
  
-   Vereinfachen Sie nach Möglichkeit Ausdrücke, in denen Konstanten enthalten sind. Der Abfrageoptimierer wertet nicht alle Funktionen und Ausdrücke mit Konstanten aus, bevor er Kardinalitätsschätzungen ermittelt. Vereinfachen Sie z. B. den ABS(`-100) to 100`)-Ausdruck.  
  
-   Wenn der Ausdruck mehrere Variablen verwendet, können Sie in Betracht ziehen, eine berechnete Spalte für den Ausdruck und dann Statistiken oder einen Index für die berechnete Spalte zu erstellen. Das Abfrageprädikat `WHERE PRICE + Tax > 100` könnte beispielsweise eine bessere Kardinalitätsschätzung aufweisen, wenn Sie eine berechnete Spalte für den Ausdruck `Price + Tax`erstellen.  
  
### <a name="improving-cardinality-estimates-for-variables-and-functions"></a>Verbessern von Kardinalitätsschätzungen für Variablen und Funktionen  
 Um die Kardinalitätsschätzungen für Variablen und Funktionen zu verbessern, beachten Sie die folgenden Richtlinien:  
  
-   Wenn das Abfrageprädikat eine lokale Variable verwendet, könnte das Umschreiben der Abfrage sinnvoll sein, sodass sie statt einer lokalen Variablen einen Parameter verwendet. Der Wert einer lokalen Variablen ist nicht bekannt, wenn der Abfrageoptimierer den Abfrageausführungsplan erstellt. Wenn eine Abfrage auf einem Parameter basiert, verwendet der Abfrageoptimierer die Kardinalitätsschätzung für den ersten tatsächlichen Parameterwert, der an die gespeicherte Prozedur übergeben wird.  
  
-   Erwägen Sie die Verwendung einer Standardtabelle oder temporären Tabelle, in der die Ergebnisse der Tabellenwertfunktionen mit mehreren Anweisungen enthalten sind. Der Abfrageoptimierer erstellt keine Statistiken für Tabellenwertfunktionen mit mehreren Anweisungen. Bei dieser Vorgehensweise kann der Abfrageoptimierer Statistiken für die Tabellenspalten erstellen und sie zum Optimieren der Abfragepläne nutzen.  
  
-   Standardtabellen oder temporäre Tabelle können auch als Ersatz für Tabellenvariablen verwendet werden. Der Abfrageoptimierer erstellt keine Statistiken für Tabellenvariablen. Bei dieser Vorgehensweise kann der Abfrageoptimierer Statistiken für die Tabellenspalten erstellen und sie zum Optimieren der Abfragepläne nutzen. Die Vorteile von temporären Tabellen und Tabellenvariablen müssen gegeneinander abgewogen werden. Tabellenvariablen, die in gespeicherten Prozeduren verwendet werden, verursachen weniger Neukompilierungen der gespeicherten Prozedur als temporäre Tabellen. Nicht bei allen Anwendungen wird die Leistung optimiert, wenn statt einer Tabellenvariablen eine temporäre Tabelle verwendet wird.  
  
-   Wenn eine gespeicherte Prozedur eine Abfrage enthält, die einen übergebenen Parameter verwendet, sollten Sie den Parameterwert innerhalb der gespeicherten Prozedur nicht ändern, bevor Sie ihn in der Abfrage verwenden. Die Kardinalitätsschätzungen für die Abfrage basieren auf dem übergebenen Parameterwert und nicht auf dem aktualisierten Wert. Damit der Parameterwert nicht geändert werden kann, können Sie die Abfrage so umschreiben, dass zwei gespeicherte Prozeduren verwendet werden.  
  
     Durch die gespeicherte Prozedur `Sales.GetRecentSales` wird der Wert des `@date` -Parameters z. B. geändert, wenn `@date is NULL`gilt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID ( 'Sales.GetRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetRecentSales (@date datetime)  
    AS BEGIN  
        IF @date is NULL  
            SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
        SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
        WHERE h.SalesOrderID = d.SalesOrderID  
        AND h.OrderDate > @date  
    END  
    GO  
    ```  
  
     Wenn der erste Aufruf der gespeicherten Prozedur `Sales.GetRecentSales` für den `@date` -Parameter NULL übergibt, kompiliert der Abfrageoptimierer die gespeicherte Prozedur mit der Kardinalitätsschätzung für `@date = NULL` , obwohl das Abfrageprädikat nicht mit `@date = NULL`aufgerufen wird. Diese Kardinalitätsschätzung kann deutlich von der Anzahl der Zeilen im tatsächlichen Abfrageergebnis abweichen. Folglich könnte der Abfrageoptimierer einen suboptimalen Abfrageplan auswählen. Um dies zu vermeiden, können Sie die gespeicherte Prozedur wie folgt in zwei Prozeduren unterteilen:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID ( 'Sales.GetNullRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetNullRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetNullRecentSales (@date datetime)  
    AS BEGIN  
        IF @date is NULL  
            SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
        EXEC Sales.GetNonNullRecentSales @date;  
    END  
    GO  
    IF OBJECT_ID ( 'Sales.GetNonNullRecentSales', 'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetNonNullRecentSales;  
    GO  
    CREATE PROCEDURE Sales.GetNonNullRecentSales (@date datetime)  
    AS BEGIN  
        SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
        WHERE h.SalesOrderID = d.SalesOrderID  
        AND h.OrderDate > @date  
    END  
    GO  
    ```  
  
### <a name="improving-cardinality-estimates-with-query-hints"></a>Verbessern von Kardinalitätsschätzungen mit Abfragehinweisen  
 Um Kardinalitätsschätzungen für lokale Variablen zu verbessern, können Sie den OPTIMIZE FOR-Abfragehinweis oder den OPTIMIZE FOR UNKNOWN-Abfragehinweis mit RECOMPILE verwenden. Weitere Informationen finden Sie unter [Abfragehinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).  
  
 Bei einigen Anwendungen könnte es zu lange dauern, die Abfrage bei jeder Ausführung neu zu kompilieren. Der OPTIMIZER FOR-Abfragehinweis kann hilfreich sein, auch wenn Sie die RECOMPILE-Option nicht verwenden. Sie können der gespeicherten Sales.GetRecentSales-Prozedur z. B. eine OPTIMIZER FOR-Option hinzufügen, um ein bestimmtes Datum anzugeben. Im folgenden Beispiel wird der Sales.GetRecentSales-Prozedur die OPTIMIZE FOR-Option hinzugefügt.  
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Sales.GetRecentSales', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetRecentSales;  
GO  
CREATE PROCEDURE Sales.GetRecentSales (@date datetime)  
AS BEGIN  
    IF @date is NULL  
        SET @date = DATEADD(MONTH, -3, (SELECT MAX(ORDERDATE) FROM Sales.SalesOrderHeader))  
    SELECT * FROM Sales.SalesOrderHeader h, Sales.SalesOrderDetail d  
    WHERE h.SalesOrderID = d.SalesOrderID  
    AND h.OrderDate > @date  
    OPTION ( OPTIMIZE FOR ( @date = '2004-05-01 00:00:00.000'))  
END;  
GO  
```  
  
### <a name="improving-cardinality-estimates-with-plan-guides"></a>Verbessern von Kardinalitätsschätzungen mit Planhinweislisten  
 Für einige Anwendungen sind die Abfrageentwurfsrichtlinien möglicherweise nicht geeignet, weil Sie die Abfrage nicht ändern können oder die Verwendung des RECOMPILE-Abfragehinweises zu viele Neukompilierungen verursacht. Sie können mithilfe der Planhinweislisten weitere Hinweise (z. B. USE PLAN) angeben, um das Abfrageverhalten zu steuern. Zur gleichen Zeit können Sie mit dem Hersteller klären, ob die Anwendung geändert wurde. Weitere Informationen zu Planhinweislisten finden Sie unter [Planhinweislisten](../performance/plan-guides.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)   
 [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-show-statistics-transact-sql)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Erstellen gefilterter Indizes](../indexes/create-filtered-indexes.md)  
