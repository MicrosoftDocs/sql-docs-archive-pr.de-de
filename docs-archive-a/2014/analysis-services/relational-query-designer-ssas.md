---
title: Relationaler Abfrage-Designer (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.relquerydesginer.f1
ms.assetid: 9399b1d1-1ad2-44df-bd11-bef60fbf01ec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79765f589dcc649bdb2d12bd9dda0d4c955ae916
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608012"
---
# <a name="relational-query-designer-ssas"></a>Relationaler Abfrage-Designer (SSAS)
  Mit dem relationalen Abfrage-Designer können Sie eine Abfrage erstellen, die die Daten angibt, die aus [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] relationalen Datenbanken und [!INCLUDE[msCoName](../includes/msconame-md.md)] abgerufen werden sollen [!INCLUDE[ssDWfull](../includes/ssdwfull-md.md)] . Verwenden Sie den grafischen Abfrage-Designer zum Durchsuchen von Metadaten, zum interaktiven Erstellen einer Abfrage sowie zum Anzeigen der Ergebnisse Ihrer Abfrage.  Verwenden Sie den textbasierten Abfrage-Designer, um die Abfrage anzuzeigen, die vom grafischen Abfrage-Designer erstellt wurde, oder um eine Abfrage zu ändern. Sie können auch eine vorhandene Abfrage aus einer Datei oder einem Bericht importieren.  
  
 Wenn Sie dies vorziehen, können Sie die Abfrage mit dem textbasierten Editor in der SQL-Sprache schreiben. Wenn Sie zum textbasierten Abfrage-Designer wechseln möchten, klicken Sie auf der Symbolleiste auf **Als Text bearbeiten**. Nachdem Sie eine Abfrage im textbasierten Abfrage-Designer bearbeitet haben, können Sie den grafischen Abfrage-Designer nicht mehr verwenden.  
  
> [!NOTE]  
>  Sie müssen den textbasierten Abfrage-Designer verwenden, um eine Abfrage für die Oracle-, OLE DB-, ODBC- und Teradata-Datenquellentypen zu erstellen.  
  
> [!IMPORTANT]  
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.  
>   
>  Die Anmeldeinformationen des aktuellen Benutzers, nicht die auf der Seite Identitätswechselinformationen angegebenen Anmeldeinformationen, werden zum Herstellen einer Verbindung mit der Datenquelle verwendet, wenn eine Abfrage ausgeführt wird.  
  
## <a name="graphical-query-designer"></a>Grafischer Abfrage-Designer  
 Mit dem grafischen Abfrage-Designer können Sie die Datenbanktabellen und -sichten durchsuchen, interaktiv die SQL-Anweisung SELECT erstellen, mit der die Datenbanktabellen und Spalten angegeben werden, aus denen Daten für das Dataset abgerufen werden. Sie wählen die Felder aus, die im Dataset enthalten sein sollten, und geben optional Filter an, die die Daten im Dataset begrenzen. Sie können angeben, dass Filter als Parameter verwendet werden und den Wert des Filters zur Laufzeit bereitstellen. Wenn Sie mehrere Tabellen auswählen, beschreibt der Abfrage-Designer die Beziehung zwischen Sätzen von zwei Tabellen.  
  
 Der grafische Abfrage-Designer ist in drei Bereiche aufgeteilt. Abhängig davon, ob die Abfrage Tabellen/Sichten oder gespeicherte Prozeduren/Tabellenwertfunktionen verwendet, ändert sich das Layout des Abfrage-Designers.  
  
> [!NOTE]  
>  [!INCLUDE[ssDWfull](../includes/ssdwfull-md.md)] unterstützt keine gespeicherten Prozeduren oder Tabellenwertfunktionen.  
  
 Die folgende Abbildung zeigt den grafischen Abfrage-Designer, wenn er mit Tabellen oder Sichten verwendet wird.  
  
 ![Grafischer Designer für Abfragen](media/rsqd-relational-graphical.gif "Grafischer Designer für Abfragen")  
  
 Die folgende Abbildung zeigt den grafischen Abfrage-Designer an, wenn er mit gespeicherten Prozeduren oder Tabellenwertfunktionen verwendet wird.  
  
 ![Gespeicherte Prozedur im grafischen Abfrage-Designer](media/rs-relational-graphical-sp.gif "Gespeicherte Prozedur im grafischen Abfrage-Designer")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|[Datenbanksicht](#DatabaseView)|Zeigt eine hierarchische Sicht von Tabellen, Sichten, gespeicherten Prozeduren und Tabellenwertfunktionen an, die nach Datenbankschema angeordnet sind.|  
|[Ausgewählte Felder](#SelectedFields)|Zeigt die Liste der Datenbankfeldnamen von den ausgewählten Elementen im Bereich Datenbanksicht an. Diese Felder werden zur Feldauflistung für das Dataset.|  
|[Funktionsparameter](#FunctionParameters)|Zeigt die Liste der Eingabeparameter für gespeicherte Prozeduren oder Tabellenwertfunktionen im Bereich Datenbanksicht an.|  
|[Beziehungen](#Relationships)|Zeigt eine Liste von Beziehungen an, die aus ausgewählten Feldern für Tabellen oder Sichten im Bereich "Datenbanksicht" abgeleitet werden, oder zeigt manuell erstellte Beziehungen an.|  
|[Angewendete Filter](#AppliedFilters)|Zeigt eine Liste von Feldern und Filterkriterien für Tabellen oder Sichten in der Datenbanksicht an.|  
|[Abfrageergebnisse](#QueryResults)|Zeigt Beispieldaten für das Resultset für die automatisch generierte Abfrage an.|  
  
###  <a name="database-view-pane"></a><a name="DatabaseView"></a> Bereich Datenbanksicht  
 Im Bereich Datenbanksicht werden die Metadaten für Datenbankobjekte angezeigt, zu deren Anzeige Sie berechtigt sind. Diese Berechtigung wird von der Datenquellenverbindung und den Anmeldeinformationen bestimmt. In der hierarchischen Sicht werden Datenbankobjekte nach Datenbankschema angeordnet angezeigt. Erweitern Sie den Knoten für jedes Schema, um Tabellen, Sichten, gespeicherte Prozeduren und Tabellenwertfunktionen anzuzeigen. Erweitern Sie die Tabelle oder Sicht, um die einzelnen Spalten anzuzeigen.  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a>Bereich "ausgewählte Felder"  
 Der Bereich "Ausgewählte Felder" zeigt die Felder im Dataset und die Gruppen und Aggregate an, die in die Abfrage eingeschlossen werden sollen.  
  
 Die folgenden Optionen werden angezeigt:  
  
-   **Ausgewählte Felder** zeigt die Datenbankfelder an, die Sie für Tabellen oder Sichten auswählen, oder die Eingabeparameter für gespeicherte Prozeduren oder Tabellenwertfunktionen. Die Felder, die in diesem Bereich angezeigt werden, werden zur Feldauflistung für das Dataset.  
  
     Verwenden Sie den Berichtsdatenbereich, um die Feldauflistung für ein Dataset anzuzeigen.  
  
-   **Gruppieren und aggregieren:** Schaltet die Verwendung der Gruppierung und von Aggregaten in der Abfrage um. Wenn Sie die Funktion zum Gruppieren und Aggregieren deaktivieren, nachdem Sie die Gruppierung und Aggregate hinzugefügt haben, werden sie entfernt. Der Text **(keine)** gibt an, dass Gruppierung und Aggregate nicht verwendet werden. Wenn Sie die Funktion zum Gruppieren und aggregieren wieder aktivieren, werden die vorherige Gruppierung und die vorherigen Aggregate wiederhergestellt.  
  
-   **Feld löschen** Löscht das ausgewählte Feld.  
  
#### <a name="group-and-aggregate"></a>Gruppieren und aggregieren:  
 Datenbankabfragen, die eine große Tabelle umfassen, geben möglicherweise eine Reihe von Datenzeilen zurück, die zu groß sind, um nützlich zu sein. Zudem wirkt sich dies negativ auf die Leistung des Netzwerks aus, über das die gewaltige Datenmenge transportiert wird. Um die Anzahl der Datenzeilen einzuschränken, kann die Abfrage SQL-Aggregate enthalten, die die Daten auf dem Datenbankserver zusammenfassen.  
  
 Aggregate stellen Zusammenfassungen der Daten bereit. Die Daten werden gruppiert, um das Aggregat zu unterstützen, das die Zusammenfassungsdaten übermittelt. Wenn Sie in der Abfrage ein Aggregat verwenden, werden die anderen von der Abfrage zurückgegebenen Felder automatisch gruppiert, und die Abfrage enthält die SQL-Klausel GROUP BY. Sie können Daten zusammenfassen, ohne ein Aggregat hinzuzufügen, indem Sie nur die Option **Gruppiert nach** in der Liste **Gruppieren und aggregieren** verwenden. Viele der Aggregate schließen eine Version ein, die das Schlüsselwort DISTINCT verwendet. Durch das Einschließen von DISTINCT werden doppelte Werte ausgeschlossen.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwendet [!INCLUDE[tsql](../includes/tsql-md.md)] und [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssDWfull](../includes/ssdwfull-md.md)] verwendet [!INCLUDE[DWsql](../includes/dwsql-md.md)] . Beide Dialekte der SQL-Sprache unterstützen die Klausel, das Schlüsselwort und die Aggregate, die der Abfrage-Designer bereitstellt.  
  
 Weitere Informationen zu [!INCLUDE[tsql](../includes/tsql-md.md)] finden Sie unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference) in der -[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Onlinedokumentation](https://go.microsoft.com/fwlink/?LinkId=141687) auf „msdn.microsoft.com“.  
  
 In der folgenden Tabelle sind die Aggregate einschließlich einer kurzen Beschreibung aufgelistet.  
  
|Aggregat|BESCHREIBUNG|  
|---------------|-----------------|  
|Avg|Gibt den Mittelwert der Werte in einer Gruppe zurück. Implementiert das SQL AVG-Aggregat.|  
|Anzahl|Gibt die Anzahl von Elementen in einer Gruppe zurück. Implementiert das SQL COUNT-Aggregat.|  
|Count Big|Gibt die Anzahl von Elementen in einer Gruppe zurück. Es ist das SQL COUNT_BIG-Aggregat. Der Unterschied zwischen COUNT und COUNT_BIG ist, dass COUNT_BIG immer einen `bigint`-Datentypwert zurückgibt.|  
|Min.|Gibt den kleinsten Wert in einer Gruppe zurück. Implementiert das SQL MIN-Aggregat.|  
|Max|Gibt den größten Wert in einer Gruppe zurück. Implementiert das SQL MAX-Aggregat.|  
|StDev|Gibt die statistische Standardabweichung aller Werte in einer Gruppe zurück. Implementiert das SQL STDEV-Aggregat.|  
|StDevP|Gibt die statistische Standardabweichung für die Auffüllung aller Werten im angegebenen Ausdruck einer Gruppe zurück. Implementiert das SQL STDEVP-Aggregat.|  
|SUM|Gibt die Summe aller Werte in der Gruppe zurück. Implementiert das SQL SUM-Aggregat.|  
|Var|Gibt die statistische Varianz aller Werte in der Gruppe zurück. Implementiert das SQL VAR-Aggregat.|  
|VarP|Gibt die statistische Varianz der Auffüllung für alle Werte in der Gruppe zurück. Implementiert das SQL VARP-Aggregat.|  
|Avg Distinct|Gibt eindeutige Durchschnittswerte zurück. Implementiert eine Kombination der AVG-Aggregation und des DISTINCT-Schlüsselworts.|  
|Count Distinct|Gibt eindeutige Anzahlwerte zurück. Implementiert eine Kombination des COUNT-Aggregats und des DISTINCT-Schlüsselworts.|  
|Count Big Distinct|Gibt eine eindeutige Anzahl von Elementen in einer Gruppe zurück. Implementiert eine Kombination des COUNT_BIG-Aggregats und des DISTINCT-Schlüsselworts.|  
|StDev Distinct|Gibt eindeutige statistische Standardabweichungen zurück. Implementiert eine Kombination des STDEV-Aggregats und des DISTINCT-Schlüsselworts.|  
|StDevP Distinct|Gibt eindeutige statistische Standardabweichungen zurück. Implementiert eine Kombination des STDEVP-Aggregats und des DISTINCT-Schlüsselworts.|  
|Sum Distinct|Gibt eindeutige Summen zurück. Implementiert eine Kombination des SUM-Aggregats und des DISTINCT-Schlüsselworts.|  
|Var Distinct|Gibt eindeutige statistische Varianzen zurück. Implementiert eine Kombination des VAR-Aggregats und des DISTINCT-Schlüsselworts.|  
|VarP Distinct|Gibt eindeutige statistische Varianzen zurück. Implementiert eine Kombination des VARP-Aggregats und des DISTINCT-Schlüsselworts.|  
  
###  <a name="function-parameters-pane"></a><a name="FunctionParameters"></a>Funktionsparameter Bereich  
 Der Bereich Funktionsparameter zeigt die Parameter für eine gespeicherte Prozedur oder Tabellenwertfunktion an. Die folgenden Spalten werden angezeigt:  
  
-   **Parametername** zeigt den Namen des Parameters an, der von der gespeicherten Prozedur oder Tabellenwertfunktion definiert wird.  
  
-   **Wert** Ein Wert, der für den Parameter verwendet werden soll, wenn die Abfrage zur Laufzeit ausgeführt wird, um Daten abzurufen, die im Bereich Abfrageergebnisse angezeigt werden sollen. Dieser Wert wird zur Laufzeit nicht verwendet.  
  
###  <a name="relationships-pane"></a><a name="Relationships"></a>Beziehungs Bereich  
 Im Bereich "Beziehungen" werden die Joinbeziehungen angezeigt. Die Beziehungen können automatisch von den Fremdschlüsseleinschränkungen erkannt werden, die aus den Datenbankmetadaten abgerufen werden, oder Sie können diese manuell erstellen.  
  
 Die folgenden Optionen werden angezeigt:  
  
-   **Automatische Erkennung** schaltet das Feature zur automatischen Erkennung um, die Beziehungen zwischen Tabellen automatisch erstellt. Wenn die automatische Erkennung aktiviert ist, erstellt der Abfrage-Designer Beziehungen aus Fremdschlüsseln in Tabellen; andernfalls müssen Sie die Beziehungen manuell erstellen. Wenn Sie Tabellen im Bereich **Datenbanksicht** auswählen, versucht die Funktion zur automatischen Erkennung automatisch, Beziehungen zu erstellen. Wenn Sie die Funktion zur automatischen Erkennung aktivieren, nachdem Sie manuell Joins erstellt haben, werden diese Joins verworfen.  
  
    > [!IMPORTANT]  
    >  Bei der Verwendung mit [!INCLUDE[ssDWfull](../includes/ssdwfull-md.md)] werden die zum Erstellen von Joins benötigten Metadaten nicht bereitgestellt, und Beziehungen können nicht automatisch erkannt werden. Wenn die Abfrage Daten aus [!INCLUDE[ssDWfull](../includes/ssdwfull-md.md)]abruft, müssen alle Tabellenjoins manuell erstellt werden.  
  
-   **Beziehung hinzufügen** Fügt der Liste **Beziehung** eine Beziehung hinzu.  
  
     Wenn die automatische Erkennung aktiviert ist, werden die Tabellen, von denen Spalten in der Abfrage verwendet werden, automatisch der Liste **Beziehung** hinzugefügt. Wenn die automatische Erkennung feststellt, dass zwei Tabellen verknüpft sind, wird der Spalte **Linke Tabelle** eine Tabelle und der Spalte **Rechte Tabelle** die andere Tabelle hinzugefügt, und zwischen ihnen wird ein innerer Join erstellt. Jede Beziehung generiert eine JOIN-Klausel in der Abfrage. Wenn die Tabellen nicht verknüpft sind, werden alle Tabellen in der Spalte **Linke Tabelle** aufgelistet, und die Spalte **Jointyp** gibt an, dass die Tabellen nicht mit anderen Tabellen verknüpft sind. Wenn die Funktion zur automatischen Erkennung aktiviert ist, können Sie manuell keine Beziehungen zwischen Tabellen hinzufügen, die von der automatischen Erkennung als nicht verknüpft erkannt wurden.  
  
     Wenn die Funktion zur automatischen Erkennung deaktiviert ist, können Sie zwischen Tabellen Beziehungen hinzufügen und ändern. Klicken Sie auf **Felder bearbeiten** , um die Felder anzugeben, die zum Verknüpfen der beiden Tabellen verwendet werden sollen.  
  
     Die Reihenfolge, in der die Beziehungen in der Liste **Beziehung** angezeigt werden, ist die Reihenfolge, in der die Joins in der Abfrage ausgeführt werden. Sie können die Reihenfolge von Beziehungen ändern, indem Sie sie in der Liste nach oben und unten verschieben.  
  
     Beim Verwenden von mehreren Beziehungen in einer Abfrage muss in einer der vorangehenden Beziehungen auf eine der Tabellen in jeder Beziehung, außer auf die erste, verwiesen werden.  
  
     Wenn von einer vorangehenden Beziehung auf beide Tabellen in einer Beziehung verwiesen wird, generiert die Beziehung keine separate Joinklausel; stattdessen wird der für die vorangehende Beziehung generierten Joinklausel eine Joinbedingung hinzugefügt. Der Jointyp wird von der vorangehenden Beziehung abgeleitet, von der auf die gleichen Tabellen verwiesen wurde.  
  
-   **Felder bearbeiten** Öffnet das Dialogfeld **Verknüpfte Felder bearbeiten** , in dem Sie Beziehungen zwischen Tabellen hinzufügen und ändern. Sie haben ausgewählt, dass die Felder in der rechten und linken Tabelle verknüpft werden sollen. Sie können mehrere Felder aus der linken Tabelle und aus der rechten Tabelle verknüpfen, um mehrere Joinbedingungen in einer Beziehung anzugeben. Die beiden Felder, die die linken und rechten Tabellen verknüpfen, müssen nicht über den gleichen Namen verfügen. Der Datentyp der verknüpften Felder muss kompatible Datentypen haben.  
  
-   **Beziehung löschen:**  Löscht die ausgewählte Beziehung **.**  
  
-   **Nach oben** und **Nach oben** Verschiebt Beziehungen in der Liste **Beziehung** nach oben oder nach unten. Die Reihenfolge, in der Beziehungen in die Abfrage eingefügt werden, kann sich auf die Abfrageergebnisse auswirken. Die Beziehungen werden der Abfrage in der Reihenfolge hinzugefügt, in der sie in der Liste **Beziehung** angezeigt werden.  
  
 Die folgenden Spalten werden angezeigt:  
  
-   **Linke Tabelle** Zeigt den Namen der ersten Tabelle an, die ein Teil einer Joinbeziehung ist.  
  
-   **Jointyp** Zeigt den Typ der SQL-Anweisung JOIN an, die in der automatisch generierten Abfrage verwendet wird. Wenn eine Fremdschlüsseleinschränkung erkannt wird, wird standardmäßig INNER JOIN verwendet. Andere Jointypen können LEFT JOIN oder RIGHT JOIN sein. Wenn keiner dieser Jointypen zutrifft, wird in der Spalte **Jointyp****Nicht verbunden**angezeigt. Für nicht verknüpfte Tabellen werden keine CROSS JOIN-Joins erstellt; stattdessen müssen Sie Beziehungen manuell erstellen, indem Sie Spalten in der linken und rechten Tabelle verknüpfen. Weitere Informationen zu JOINs finden Sie unter den JOIN-Grundlagen in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=141687) on msdn.microsoft.com.  
  
-   **Rechte Tabelle** Zeigt den Namen der zweiten Tabelle in der Joinbeziehung an.  
  
-   **Joinfelder** listet Paare von verknüpften Felder auf. Wenn eine Beziehung mehrere Joinbedingungen umfasst, werden die Joinfelderpaare durch Kommas (,) getrennt.  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a>Bereich angewendete Filter  
 Im Bereich "Angewendete Filter" werden die Kriterien angezeigt, mit denen die Anzahl von Datenzeilen begrenzt wird, die zur Laufzeit abgerufen werden. In diesem Bereich angegebene Kriterien werden verwendet, um eine SQL-WHERE-Klausel zu generieren. Wenn Sie die Parameteroption auswählen, wird automatisch ein Parameter erstellt.  
  
 Die folgenden Spalten werden angezeigt:  
  
-   **Feldname** Zeigt den Namen des Felds an, für das die Kriterien angewendet werden sollen.  
  
-   **Operator** Zeigt den Vorgang an, der im Filterausdruck verwendet werden soll.  
  
-   **Wert** Zeigt den Wert an, der im Filterausdruck verwendet werden soll.  
  
-   **Parameter** Zeigt die Option an, mit der ein Abfrageparameter der Abfrage hinzugefügt werden kann.  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> Bereich Abfrageergebnisse  
 Im Bereich Abfrageergebnisse werden die Ergebnisse für die automatisch generierte Abfrage angezeigt, die mit den Auswahlen in den anderen Bereichen angegeben wird. Die Spalten im Resultset entsprechen den Feldern, die Sie im Bereich Ausgewählte Felder angeben. Die Zeilendaten werden mit den Filtern begrenzt, die Sie im Bereich Angewendete Filter angeben.  
  
 Diese Daten stellen Werte aus der Datenquelle zum Zeitpunkt der Abfrageausführung dar.  
  
 Die Sortierreihenfolge im Resultset wird von der Reihenfolge bestimmt, in der die Daten aus der Datenquelle abgerufen werden. Die Sortierreihenfolge kann geändert werden, indem der Abfragetext direkt geändert wird. Weitere Informationen zum Verwenden der GROUP BY-Klausel in einer Abfrage finden Sie in „GROUP BY (Transact-SQL)“ in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335).  
  
### <a name="graphical-query-designer-toolbar"></a>Symbolleiste für den grafischen Abfrage-Designer  
 Die Symbolleiste des grafischen Abfrage-Designers stellt die folgenden Schaltflächen bereit, mit denen Sie eine Abfrage angeben oder die Ergebnisse der Abfrage anzeigen können.  
  
|Schaltfläche|Beschreibung|  
|------------|-----------------|  
|**Als Text bearbeiten**|Wechselt zum textbasierten Abfrage-Designer, um die automatisch generierte Abfrage anzuzeigen oder die Abfrage zu ändern.|  
|**Importieren**|Importiert eine vorhandene Abfrage aus einer Datei oder einem Bericht. Die Dateitypen SQL und RDL werden unterstützt.|  
|**Abfrage ausführen**|Führen Sie die Abfrage aus. Das Resultset wird im Bereich mit den Abfrageergebnissen angezeigt.|  
  
## <a name="understanding-automatically-generated-queries"></a>Grundlegendes zu automatisch generierten Abfragen  
 Wenn Sie Tabellen und Spalten oder gespeicherte Prozeduren und Sichten im Bereich Datenbanksicht auswählen, ruft der Abfrage-Designer die zugrunde liegenden Primärschlüssel- und Fremdschlüsselbeziehungen aus dem Datenbankschema ab. Der Abfrage-Designer erkennt Beziehungen zwischen zwei Tabellen, indem er diese Beziehungen analysiert, und fügt der Abfrage Joins hinzu. Sie können die Abfrage dann ändern, indem Sie Gruppen und Aggregate hinzufügen, Beziehungen hinzufügen oder ändern und Filter hinzufügen. Klicken Sie auf **Als Text bearbeiten**, um den Abfragetext anzuzeigen, der die Spalten, aus denen Daten abgerufen werden sollen, die Joins zwischen Tabellen und alle Gruppen oder Aggregate anzeigt.  
  
## <a name="text-based-query-designer"></a>Textbasierter Abfrage-Designer  
 Der textbasierte Abfrage-Designer ermöglicht, eine Abfrage mithilfe der Abfragesprache zu verwenden, die von der Datenquelle unterstützt wird, die Abfrage auszuführen und die Ergebnisse zur Entwurfszeit anzuzeigen. Sie können mehrere SQL-Anweisungen, Abfrage- oder Befehlssyntaxen für benutzerdefinierte Datenverarbeitungserweiterungen und Abfragen angeben, die als Ausdrücke angegeben sind.  
  
 Da der textbasierte Abfrage-Designer die Abfrage nicht vorab verarbeitet, kann er mit jeder Art von Abfragesyntax arbeiten. Er ist das Standard-Abfrage-Designer-Tool für viele Datenquellentypen.  
  
 Der textbasierte Abfrage-Designer zeigt eine Symbolleiste und die folgenden zwei Bereiche an:  
  
-   **Abfrage** Zeigt den Abfragetext, den Tabellennamen oder den Namen der gespeicherten Prozedur an, je nach Abfragetyp. Nicht alle Abfragetypen können für alle Datenquellentypen verwendet werden. Beispiel: Tabellenname wird nur vom Datenquellentyp OLE DB unterstützt.  
  
-   **Ergebnis** Zeigt die Ergebnisse einer Ausführung der Abfrage zur Entwurfszeit an.  
  
### <a name="text-based-query-designer-toolbar"></a>Symbolleiste für den textbasierten Abfrage-Designer  
 Der textbasierte Abfrage-Designer stellt eine einzige Symbolleiste für alle Befehlstypen bereit. In der folgenden Tabelle werden jede Schaltfläche auf der Symbolleiste und ihre Funktion aufgelistet.  
  
|Schaltfläche|Beschreibung|  
|------------|-----------------|  
|**Als Text bearbeiten**|Wechseln zwischen dem textbasierten Abfrage-Designer und dem grafischen Abfrage-Designer. Nicht alle Datenquellentypen unterstützen grafische Abfrage-Designer.|  
|**Importieren**|Importiert eine vorhandene Abfrage aus einer Datei oder einem Bericht. Nur die Dateitypen SQL und RDL werden unterstützt.|  
|![Abfrage ausführen](media/rsqdicon-run.gif "Abfrage ausführen")|Führen Sie die Abfrage aus, und zeigen Sie das Resultset im Ergebnisbereich an.|  
|**Befehlstyp**|Wählen Sie **Text**, **StoredProcedure**oder **TableDirect**. Weist eine gespeicherte Prozedur Parameter auf, wird das Dialogfeld **Abfrageparameter definieren** angezeigt, wenn Sie auf der Symbolleiste auf **Ausführen** klicken. Sie können nach Bedarf Werte eingeben.<br /><br /> Beachten Sie Folgendes: Wenn eine gespeicherte Prozedur mehr als ein Resultset zurückgibt, wird nur das erste Resultset verwendet, um das DataSet aufzufüllen. Beachten Sie auch, dass <br />                      **TableDirect** ist nur für den Daten Quellentyp OLE DB verfügbar.|  
  
#### <a name="command-type-text"></a>Befehlstyp "Text"  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dataset erstellen, wird vom Berichts-Designer standardmäßig der relationale Abfrage-Designer geöffnet. Wenn Sie zum textbasierten Abfrage-Designer wechseln möchten, klicken Sie auf der Symbolleiste auf die Umschaltfläche **Als Text bearbeiten** . Der textbasierte Abfrage-Designer hat zwei Bereiche: den Abfragebereich und den Ergebnisbereich. In der folgenden Abbildung werden die einzelnen Bereiche bezeichnet.  
  
 ![Generischer Abfrage-Designer für relationale Datenabfragen](media/rsqd-dsaw-sql-generic.gif "Generischer Abfrage-Designer für relationale Datenabfragen")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrage|Zeigt den SQL-Abfragetext an. In diesem Bereich schreiben oder bearbeiten Sie eine SQL-Abfrage.|  
|Ergebnis|Zeigt die Ergebnisse der Abfrage an. Klicken Sie zum Ausführen der Abfrage mit der rechten Maustaste in einen beliebigen Bereich, und klicken Sie auf **Ausführen**, oder klicken Sie auf der Symbolleiste auf **Ausführen** .|  
  
#### <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die Liste der Nachnamen aus einer Tabelle mit dem Namen `ContactType` zurück.  
  
```sql  
SELECT Name FROM ContactType  
```  
  
 Wenn Sie auf der Symbolleiste auf **Ausführen** klicken, wird der Befehl im Bereich **Abfrage** ausgeführt, und die Ergebnisse werden im Bereich **Ergebnis** angezeigt.  
  
#### <a name="command-type-storedprocedure"></a>StoredProcedure-Befehlstyp  
 Wenn Sie den **Befehlstyp StoredProcedure**auswählen, zeigt der textbasierte Abfrage-Designer zwei Bereiche an: den Abfragebereich und den Ergebnisbereich. Geben Sie den Namen der gespeicherten Prozedur im Bereich **Abfrage** ein, und klicken Sie auf der Symbolleiste auf Ausführen. Wenn die gespeicherte Prozedur Parameter verwendet, wird das Dialogfeld **Abfrageparameter definieren** geöffnet. Geben Sie die Parameterwerte für die gespeicherte Prozedur ein.  
  
 Die folgende Abbildung zeigt die Bereiche Abfrage und Ergebnis an, wenn Sie eine gespeicherte Prozedur ausführen. In diesem Fall sind die Eingabeparameter Konstanten.  
  
 ![Gespeicherte Prozedur im textbasierten Abfrage-Designer](media/rs-relational-text-sp.gif "Gespeicherte Prozedur im textbasierten Abfrage-Designer")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrage|Zeigt den Namen der gespeicherten Prozedur und eventueller Eingabeparameter an.|  
|Ergebnis|Zeigt die Ergebnisse der Abfrage an. Klicken Sie zum Ausführen der Abfrage mit der rechten Maustaste in einen beliebigen Bereich, und klicken Sie auf **Ausführen**, oder klicken Sie auf der Symbolleiste auf **Ausführen** .|  
  
#### <a name="example"></a>Beispiel  
 Die folgende Abfrage ruft eine gespeicherte Prozedur mit dem Namen `uspGetWhereUsedProductID` auf. Wenn die gespeicherte Prozedur Eingabeparameter hat, müssen Sie Parameterwerte angeben, wenn Sie die Abfrage ausführen.  
  
```sql  
uspGetWhereUsedProductID  
```  
  
 Klicken Sie auf die Schaltfläche **Ausführen** ( **!** ). In der folgenden Tabelle finden Sie ein Beispiel `uspGetWhereUsedProductID` für Parameter, für die Sie Werte im Dialogfeld **Abfrage Parameter definieren** angeben.  
  
|||  
|-|-|  
|*\@StartProductID*|820|  
|*\@CheckDate*|20010115|  
  
#### <a name="command-type-tabledirect"></a>TableDirect-Befehlstyp  
 Wenn Sie den **Befehlstyp TableDirect**auswählen, zeigt der textbasierte Abfrage-Designer zwei Bereiche an: den Abfragebereich und den Ergebnisbereich. Wenn Sie eine Tabelle auswählen und auf die Schaltfläche **Ausführen** klicken, werden alle Spalten für diese Tabelle zurückgegeben.  
  
#### <a name="example"></a>Beispiel  
 Bei einem Datenquellentyp OLE DB gibt die folgende Datasetabfrage ein Resultset für alle Kontakttypen in der Tabelle `ContactType` zurück.  
  
 `ContactType`  
  
 Die Eingabe des Tabellennamens `ContactType` entspricht der Erstellung der SQL-Anweisung `SELECT * FROM ContactType`.  
  
  
