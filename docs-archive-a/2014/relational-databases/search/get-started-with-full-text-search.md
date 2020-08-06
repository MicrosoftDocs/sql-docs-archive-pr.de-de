---
title: Erste Schritte mit der Volltextsuche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eec806bffba330ac3ab995c1b3bfd3504589ecfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697821"
---
# <a name="get-started-with-full-text-search"></a>Erste Schritte mit der Volltextsuche
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die Datenbanken standardmäßig volltextfähig. Wenn Sie jedoch einen Volltextindex für eine Tabelle verwenden möchten, müssen Sie die Volltextindizierungsfunktion für die Spalten der Tabellen einrichten, auf die Sie mit der Volltext-Engine zugreifen möchten.  
  
##  <a name="configuring-a-database-for-full-text-search"></a><a name="configure"></a>Konfigurieren einer Datenbank für die voll Text Suche  
 Datenbankadministratoren führen in beliebigen Szenarien die folgenden grundlegenden Schritte aus, um Tabellenspalten in einer Datenbank für die Volltextsuche zu konfigurieren:  
  
1.  Erstellen eines Volltextkatalogs.  
  
2.  Erstellen eines Volltextindex für jede zu durchsuchende Tabelle durch folgenden Vorgang:  
  
    1.  Angeben der einzelnen Textspalten, die in den Volltextindex eingeschlossen werden sollen.  
  
    2.  Wenn eine bestimmte Spalte als Binärdaten (-oder- `varbinary(max)` Daten) gespeicherte Dokumente enthält `image` , müssen Sie eine Tabellenspalte (die *Typspalte*) angeben, die den Typ der einzelnen Dokumente in der indizierten Spalte identifiziert.  
  
    3.  Angeben der Sprache, die die Volltextsuche für die Dokumente in der Spalte verwenden soll.  
  
    4.  Auswählen des Mechanismus für die Änderungsnachverfolgung, der für den Volltextindex verwendet werden soll, um Änderungen in der Basistabelle und den darin enthaltenen Spalten nachzuverfolgen.  
  
 Die Volltextsuche unterstützt mehrere Sprachen durch die Verwendung der folgenden *linguistischen Komponenten*: Wörtertrennungen und Wortstammerkennungen, Stopplisten mit Stoppwörtern (auch als Füllwörter bezeichnet) und Thesaurusdateien. Für Thesaurusdateien (und in einigen Fällen auch für Stopplisten) ist die Konfiguration durch den Datenbankadministrator erforderlich. Eine bestimmte Thesaurusdatei unterstützt alle Volltextindizes, die die entsprechende Sprache verwenden, und eine bestimmte Stopliste kann einer beliebigen Anzahl von Volltextindizes zugeordnet werden.  
  
##  <a name="setting-up-a-full-text-catalog-and-index"></a><a name="setup"></a>Einrichten eines voll Text Katalogs und eines Index  
 Führen Sie dazu die folgenden grundlegenden Schritte aus:  
  
1.  Erstellen eines Volltextkatalogs zum Speichern der Volltextindizes.  
  
     Jeder Volltextindex muss einem Volltextkatalog angehören. Sie können einen separaten Textkatalog für jeden Volltextindex erstellen oder einem Katalog mehrere Volltextindizes zuordnen. Ein Volltextkatalog ist ein virtuelles Objekt und gehört keiner Dateigruppe an. Der Katalog ist ein logisches Konzept, das auf eine Gruppe von Volltextindizes verweist.  
  
2.  Erstellen eines Volltextindex für eine Tabelle oder eine indizierte Sicht.  
  
     Ein Volltextindex ist ein besonderer Typ eines tokenbasierten funktionellen Index, der durch die Volltext-Engine erstellt und verwaltet wird. Um eine Volltextsuche für eine Tabelle oder Sicht erstellen zu können, muss ein eindeutiger, einspaltiger Index vorhanden sein, der keine NULL-Werte zulässt. Die Volltext-Engine benötigt diesen eindeutigen Index, um jeder Zeile in der Tabelle einen eindeutigen, komprimierbaren Schlüssel zuzuordnen. Ein Volltextindex kann Spalten der Typen `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary` und `varbinary(max)` beinhalten. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Volltextindizes](create-and-manage-full-text-indexes.md).  
  
 Bevor Sie mehr über das Erstellen von Volltextindizes erfahren, sollten Sie die Unterschiede zu regulären [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Indizes kennen. In der folgenden Tabelle sind die Unterschiede aufgeführt:  
  
|Volltextindizes|Reguläre SQL Server-Indizes|  
|------------------------|--------------------------------|  
|Nur ein Volltextindex pro Tabelle zulässig.|Mehrere reguläre Indizes pro Tabelle zulässig.|  
|Das Hinzufügen von Daten zu Volltextindizes, *Auffüllen* genannt, muss angefordert werden. Dies erfolgt entweder mithilfe eines Zeitplans bzw. mithilfe einer speziellen Anforderung oder automatisch beim Hinzufügen neuer Daten.|Automatisches Update, wenn die Daten, auf denen der Index basiert, eingefügt, aktualisiert oder gelöscht werden.|  
|Gruppiert innerhalb derselben Datenbank zu einem oder mehreren Volltextkatalogen.|Nicht gruppiert.|  
  
  
##  <a name="choosing-options-for-a-full-text-index"></a><a name="options"></a>Auswählen von Optionen für einen voll Text Index  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   Wählen der Spaltensprache  
  
-   Wählen einer Dateigruppe für einen Volltextindex  
  
-   Zuweisen des Volltextindexes zu einem Volltextkatalog  
  
-   Zuordnen einer Stoppliste zum Volltextindex  
  
-   Aktualisieren eines Volltextindex  
  
### <a name="choosing-the-column-language"></a>Wählen der Spaltensprache  
 Weitere Informationen zu Überlegungen beim Auswählen der Sprache für die Spalte finden Sie unter [Auswählen einer Sprache beim Erstellen eines Volltextindex](choose-a-language-when-creating-a-full-text-index.md).  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a>Wählen einer Dateigruppe für einen Volltextindex  
 Die Erstellung eines Volltextindex ist ein ziemlich E/A-intensiver Vorgang (grob gesprochen besteht es aus dem Lesen von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dem anschließenden Weitergeben der gefilterten Daten an den Volltextindex). Die beste Vorgehensweise besteht darin, einen Volltextindex in der Datenbankdateigruppe anzuordnen, die am besten für die Optimierung der E/A-Leistung geeignet ist, oder ordnen Sie die Volltextindizes in einer anderen Dateigruppe auf einem anderen Volume an.  
  
 Wenn Ihnen eine einfache Verwaltbarkeit wichtig ist, empfiehlt es sich, Tabellendaten und zugehörige Volltextkataloge in derselben Dateigruppe zu speichern. Aus Leistungsgründen kann es in einigen Fällen auch ratsam sein, die Tabellendaten und den Volltextindex in verschiedenen Dateigruppen auf unterschiedlichen Volumes anzuordnen, um die E/A-Parallelität zu erhöhen.  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a>Zuweisen des Volltextindexes zu einem Volltextkatalog  
 Es ist wichtig, die Zuordnung von Volltextindizes für Tabellen zu Volltextkatalogen zu planen.  
  
 Es ist zu empfehlen, Tabellen mit denselben Updatemerkmalen (z. B. geringe Anzahl an Änderungen gegenüber einer großen Anzahl an Änderungen oder Tabellen, die regelmäßig zu bestimmten Tageszeiten geändert werden) zu gruppieren und demselben Volltextkatalog zuzuweisen. Indem Sie Zeitpläne für Volltextkataloge einrichten, bleiben Volltextindizes mit den Tabellen synchronisiert, ohne dass sich dies in Phasen umfangreicher Datenbankaktivitäten negativ auf die Ressourcenverwendung des Datenbankservers auswirkt.  
  
 Wenn Sie einem Volltextkatalog eine Tabelle zuweisen, sollten Sie die folgenden Richtlinien berücksichtigen:  
  
-   Wählen Sie stets den kleinsten eindeutigen Index, der verfügbar ist, als eindeutigen Volltextschlüssel aus (Ein Integer-basierter 4-Byte-Index ist optimal.) Dadurch werden die für den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Suchdienst benötigten Ressourcen erheblich im Dateisystem reduziert. Wenn Sie einen breiten Primärschlüssel verwenden (mehr als 100 Byte), sollten Sie erwägen, als eindeutigen Volltextschlüssel einen anderen eindeutigen Index in der Tabelle auszuwählen (oder einen anderen eindeutigen Index zu erstellen). Andernfalls kann die Volltextauffüllung nicht mehr fortgesetzt werden, wenn der eindeutige Volltextschlüssel die maximal zulässige Größe erreicht (900 Byte).  
  
-   Wenn Sie eine Tabelle indizieren, die über mehrere Millionen Zeilen verfügt, sollten Sie die Tabelle einem eigenen Volltextkatalog zuweisen.  
  
-   Berücksichtigen Sie sowohl den Umfang der Änderungen in den Tabellen, die mit einem Volltextindex indiziert werden, als auch die Gesamtzahl der Tabellenzeilen. Wenn die Gesamtzahl der geänderten Zeilen zusammen mit der Anzahl an Zeilen, die während der letzten Volltextauffüllung in der Tabelle enthalten waren, mehrere Millionen umfasst, sollten Sie die Tabelle einem eigenen Volltextkatalog zuweisen.  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a>Zuordnen einer Stopliste zum Volltextindex  
 Mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] werden Stoplisten eingeführt. Eine *Stoppliste* ist eine Liste von Stoppwörtern. Stoppwörter werden auch als Füllwörter bezeichnet. Jedem Volltextindex ist eine Stoppliste zugeordnet, und die Wörter der Stoppliste werden auf Volltextabfragen des Indexes angewendet. Standardmäßig ist der Systemstoppliste ein neuer Volltextindex zugeordnet. Sie können stattdessen jedoch auch eine eigene Stoppliste erstellen und verwenden. Weitere Informationen finden sie unter [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 Beispielsweise erstellt die folgende [CREATE FULLTEXT Stopp Liste](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) - [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisung eine neue Volltext-Stopp Liste mit dem Namen myStoplist3 "durch Kopieren aus der System Stopp Liste:  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 Mit der folgenden [ALTER FULLTEXT Stopp Liste](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung wird eine Stopp Liste mit dem Namen "myStoplist" geändert, wobei das Wort "en" zuerst für Spanisch und dann für Französisch hinzugefügt wird:  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a>Aktualisieren eines Volltextindexes  
 Volltextindizes können wie reguläre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Indizes automatisch aktualisiert werden, sobald Daten in den zugeordneten Tabellen geändert werden. Dies ist das Standardverhalten. Alternativ dazu können Sie die Volltextindizes auch manuell auf dem aktuellen Stand halten oder in bestimmten Abständen aktualisieren lassen. Das Auffüllen eines Volltextindex kann zeitaufwändig und ressourcenintensiv sein. Aus diesem Grund wird das Indexupdate meist als asynchroner Vorgang durchgeführt, der im Hintergrund ausgeführt wird und den Volltextindex jeweils nach Änderungen in der Basistabelle aktualisiert. Das sofortige Aktualisieren eines Volltextindex nach jeder Änderung in der Basistabelle kann ressourcenintensiv sein. Bei sehr hohen Update-, Einfügungs- und Löschungsraten kann es deshalb zu einer Verringerung der Abfrageleistung kommen. In diesem Fall sollten Sie erwägen, eine manuelle Änderungsnachverfolgung und entsprechende Updates zu planen, um die zahlreichen Änderungen von Zeit zu Zeit zu bearbeiten, anstatt mit den Abfragen um Ressourcen zu wetteifern.  
  
 Zum Überwachen des Auffüllungsstatus verwenden Sie entweder die Funktion FULLTEXTCATALOGPROPERTY oder OBJECTPROPERTYEX. Führen Sie die folgende Anweisung aus, um den Auffüllungsstatus des Katalogs zu ermitteln:  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 In der Regel ist das zurückgegebene Ergebnis 1, während ein vollständiges Auffüllen ausgeführt wird.  
  
  
##  <a name="example-setting-up-full-text-search"></a><a name="example"></a>Beispiel: Einrichten der voll Text Suche  
 Im folgenden zweiteiligen Beispiel wird ein Volltextkatalog mit dem Namen `AdvWksDocFTCat` in der AdventureWorks-Datenbank erstellt, und anschließend wird ein Volltextindex für die Tabelle `Document` in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] erstellt. Diese Anweisung erstellt den Volltextkatalog im bei der Installation angegebenen Standardverzeichnis. Der Ordner mit dem Namen `AdvWksDocFTCat` befindet sich im Standardverzeichnis.  
  
1.  Im Beispiel wird eine `AdvWksDocFTCat`CREATE FULLTEXT CATALOG [-Anweisung verwendet, um einen Volltextkatalog mit dem Namen](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) zu erstellen:  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  Bevor Sie einen Volltextindex für die Document-Tabelle erstellen können, müssen Sie sicherstellen, dass die Tabelle über einen eindeutigen, einspaltigen Index verfügt, der keine NULL-Werte zulässt. Die folgende [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) -Anweisung erstellt in der DocumentID-Spalte der Document-Tabelle den eindeutigen `ui_ukDoc`-Index:  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  Nachdem Sie einen eindeutigen Schlüssel erstellt haben, können Sie in der `Document` -Tabelle einen Volltextindex erstellen, indem Sie die folgende [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) -Anweisung verwenden.  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     Die in diesem Beispiel definierte TYPE COLUMN gibt die Typspalte in der Tabelle an, die den Typ des Dokuments in der Spalte Document (binäre Spalte) enthält. In der Spalte Typ wird die vom Benutzer angegebene Dateierweiterung ". doc", ". xls" usw. in einer bestimmten Zeile gespeichert. Die Volltext-Engine verwendet die Erweiterung einer Zeile, um den richtigen Filter für die Analyse der Daten in dieser Zeile aufzurufen. Nachdem der Filter die binären Daten der Zeile analysiert hat, analysiert die angegebene Wörtertrennung den Inhalt (in diesem Beispiel wird die Wörtertrennung für britisches Englisch verwendet). Beachten Sie, dass der Filtervorgang nur zur Indizierungszeit ausgeführt wird bzw. wenn ein Benutzer eine Spalte in der Basistabelle einfügt oder aktualisiert, während für den Volltextindex die automatische Änderungsnachverfolgung aktiviert ist. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Filtern für die Suche](configure-and-manage-filters-for-search.md).  
  
  
##  <a name="common-tasks"></a><a name="tasks"></a>Allgemeine Aufgaben  
  
### <a name="to-create-a-full-text-catalog"></a>So erstellen Sie einen Volltextkatalog  
  
-   [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [Erstellen und Verwalten von Volltextkatalogen](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a>So zeigen Sie die Indizes einer Tabelle (oder Sicht) an  
  
-   [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a>So erstellen Sie einen eindeutigen Index  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [Öffnen des Tabellen-Designers &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a>So erstellen Sie einen Volltextindex  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [Erstellen und Verwalten von Volltextindizes](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a>So zeigen Sie Informationen zu einem Volltextindex an  
  
|Katalogsicht oder dynamische Verwaltungssicht|BESCHREIBUNG|  
|----------------------------------------|-----------------|  
|[sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|Gibt eine Zeile für jeden Verweis zwischen Volltextkatalog und Volltextindex zurück.|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|Enthält eine Zeile für jede Spalte, die Teil eines Volltextindexes ist.|  
|[sys.fulltext_index_fragments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|Ein Volltextindex verwendet interne Tabellen, die als Volltextindexfragmente bezeichnet werden, um die umgekehrten Indexdaten zu speichern. Diese Sicht kann verwendet werden, um die Metadaten zu diesen Fragmenten abzufragen. Diese Sicht enthält eine Zeile für jedes Volltextindexfragment in jeder Tabelle, die einen Volltextindex enthält.|  
|[sys.fulltext_indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|Enthält eine Zeile pro Volltextindex eines Tabellenobjekts.|  
|[sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|Gibt Informationen zum Inhalt eines Volltextindex für die angegebene Tabelle zurück.|  
|[sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|Gibt Informationen zum Inhalt auf Dokumentebene eines Volltextindex für die angegebene Tabelle zurück. Ein Schlüsselwort kann in mehreren Dokumenten angezeigt werden.|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|Gibt Informationen zu den aktuell ausgeführten Volltextindexauffüllungen zurück.|  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)   
 [Auffüllen von Volltextindizes](populate-full-text-indexes.md)   
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL-&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)   
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
