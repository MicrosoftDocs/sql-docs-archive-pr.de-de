---
title: Richtlinien für die Verwendung von Indizes für Speicher optimierte Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f00d643088634c918eb626917eae64a001ce3678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701564"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a>Richtlinien für die Verwendung von Indizes für speicheroptimierte Tabellen
  Indizes werden für den effizienten Datenzugriff in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tabellen verwendet. Die Auswahl der richtigen Indizes kann die Abfrageleistung deutlich verbessern. Stellen Sie sich beispielsweise die folgende Abfrage vor:  
  
```sql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 Wenn kein Index für Spalte c1 enthalten ist, muss [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die gesamte Tabelle t überprüfen und dann nach den Zeilen filtern, die die Bedingung „c1=1“ erfüllen. Wenn jedoch t über einen Index für die Spalte c1 verfügt, kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] direkt auf Wert 1 suchen und die gewünschten Zeilen abrufen.  
  
 Bei der Suche nach Datensätzen, die einen bestimmten Wert oder Wertebereich in einer oder mehreren Tabellenspalten aufweisen, kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für diese Spalten einen Index nutzen, um die entsprechenden Datensätze schnell zu finden. Sowohl datenträgerbasierte als auch speicheroptimierte Tabellen profitieren von Indizes. Es gibt jedoch bestimmte Unterschiede zwischen Index Strukturen, die bei der Verwendung von Speicher optimierten Tabellen berücksichtigt werden müssen. (Indizes für Speicher optimierte Tabellen werden als Speicher optimierte Indizes bezeichnet.) Einige der Hauptunterschiede sind:  
  
-   Speicher optimierte Indizes müssen mit [CREATE TABLE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-table-transact-sql)erstellt werden. Datenträgerbasierte Indizes können mit `CREATE TABLE` und `CREATE INDEX` erstellt werden.  
  
-   Speicheroptimierte Indizes sind nur im Arbeitsspeicher vorhanden. Indexstrukturen werden nicht auf dem Datenträger beibehalten und Indexvorgänge werden nicht im Transaktionsprotokoll protokolliert. Die Indexstruktur wird beim Erstellen der speicheroptimierten Tabelle im Arbeitsspeicher erstellt, und zwar während CREATE TABLE wie auch während des Datenbankstarts.  
  
-   Speicheroptimierte Indizes decken grundsätzlich ab. Dies bedeutet, dass alle Spalten virtuell im Index enthalten sind, und Bookmark Lookup-Vorgänge in speicheroptimierten Tabellen nicht erforderlich sind. An Stelle eines Verweises auf den Primärschlüssel enthalten speicheroptimierte Indizes einfach einen Speicherzeiger auf die tatsächliche Zeile in der Tabellendatenstruktur.  
  
-   Fragmentierung und Füllfaktor gelten nicht für speicheroptimierte Indizes. In datenträgerbasierte Indizes verweist die Fragmentierung auf Seiten im B-Baum, die außerhalb der Reihenfolge auf den Datenträger geschrieben werden. Speicheroptimierte Indizes werden nicht auf Datenträger geschrieben oder von dort gelesen. Der Füllfaktor bei datenträgerbasierte B-Baum-Indizes bezieht sich darauf, zu welchem Grad die physischen Seitenstrukturen tatsächlich mit Daten gefüllt sind. Die speicheroptimierten Indexstrukturen haben keine Seiten mit fester Größe.  
  
 Es gibt zwei Typen speicheroptimierter Indizes:  
  
-   Nicht gruppierte Hashindizes, die für Punktsuchen vorgenommen werden. Weitere Informationen zu Hash Indizes finden Sie unter [Hash Indizes](hash-indexes.md).  
  
-   Nicht gruppierte Indizes, die für Bereichsscans und sortierte Scans vorgenommen werden.  
  
 Mit einem Hashindex erfolgt der Datenzugriff über eine Hashtabelle im Arbeitsspeicher. Hashindizes haben keine Seiten und haben immer eine feste Größe. Ein Hashindex kann jedoch leere Hashbuckets enthalten, was eine begrenzte Platzverschwendung nach sich zieht. Die Werte, die von einer Abfrage mithilfe eines Hashindexes zurückgegeben werden, sind nicht sortiert. Hashindizes werden für Indexsuchen auf Gleichheitsprädikaten optimiert und unterstützen auch vollständige Indexscans.  
  
 Nicht gruppierte Indizes (nicht Hashindizes) unterstützen alles, was Hashindizes unterstützen, sowie Suchvorgänge für Ungleichheitsprädikate, beispielsweise größer als oder kleiner als, und eine Sortierreihenfolge. Zeilen können nach der Reihenfolge abgerufen werden, die bei der Indexerstellung festgelegt wurde. Wenn die Sortierreihenfolge des Indexes der Sortierreihenfolge entspricht, die für eine bestimmte Abfrage erforderlich ist, der Indexschlüssel also z. B. mit der ORDER BY-Klausel übereinstimmt, müssen die Zeilen im Rahmen der Abfrageausführung nicht sortiert werden. Speicheroptimierte, nicht gruppierte Indizes sind unidirektional; sie unterstützen keinen Abruf von Zeilen in einer Sortierreihenfolge, die die Umkehrung der Sortierreihenfolge des Indexes ist. Bei einem als (c1 ASC) angegebenen Index ist es beispielsweise nicht möglich, den Index in umgekehrter Reihenfolge zu scannen, z. B. (c1 DESC).  
  
 Jeder Index belegt Arbeitsspeicher. Hashindizes belegen einen festen Speicherplatz, dessen Größe eine Funktion der Bucketanzahl ist. Bei nicht gruppierten Indizes basiert die Arbeitsspeichernutzung auf der Zeilenanzahl und Größe der Indexschlüsselspalten. Je nach Arbeitsauslastung ist dies mit etwas zusätzlichem Aufwand verbunden. Arbeitsspeicher für speicheroptimierte Indizes erfolgt zusätzlich und getrennt von dem Arbeitsspeicher, der verwendet wird, um Zeilen in den speicheroptimierten Tabellen zu speichern.  
  
 Doppelte Schlüsselwerte sind immer dem gleichen Bucket im Hashindex zugeordnet. Wenn der Hashindex viele doppelte Schlüsselwerte enthält, können die entstehenden langen Hashzeichenketten die Leistung beeinträchtigen. Hashkonflikte, die in jedem Hashindex auftreten, reduzieren die Leistung in diesem Szenario noch weiter. Wenn die Anzahl eindeutiger Index Schlüssel mindestens 100-mal kleiner als die Zeilen Anzahl ist, können Sie das Risiko von Hash Konflikten verringern, indem Sie die Bucketanzahl deutlich vergrößern ( [mindestens das](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) Achtfache der Anzahl eindeutiger Index Schlüssel), oder Sie können Hash Konflikte vollständig durch die Verwendung eines nicht gruppierten Indexes eliminieren.  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a>Bestimmen der richtigen Indizes für speicheroptimierte Tabellen  
 Jede speicheroptimierte Tabelle muss mindestens einen Index haben. Beachten Sie, dass jede PRIMARY KEY-Einschränkung implizit einen Index erstellt. Wenn eine Tabelle über einen Primärschlüssel verfügt, hat sie also einen Index. Ein Primärschlüssel ist eine Voraussetzung für dauerhafte speicheroptimierte Tabellen.  
  
 Wenn Sie eine speicheroptimierte Tabelle abfragen, bieten Hashindizes eine bessere Leistung, wenn die Prädikatklausel nur Gleichheitsprädikate enthält. Das Prädikat muss alle Spalten im Hashindexschlüssel enthalten. Ein Hashindex wird mit einem Ungleichheitsprädikat auf einen Scan wiederhergestellt.  
  
 Eine Spalte in einer speicheroptimierten Tabelle kann Teil eines Hashindexes und des nicht gruppierten Indexes sein.  
  
 Wenn Sie eine speicheroptimierte Tabelle mit Ungleichheitsprädikaten abfragen, bieten nicht gruppierte Indizes eine bessere Leistung als nicht gruppierte Hashindizes.  
  
 Der Hashindex erfordert einen Schlüssel (für den Hash), um den Index zu durchsuchen. Wenn ein Indexschlüssel aus zwei Spalten besteht und Sie nur die erste Spalte bereitstellen, hat [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keinen vollständigen Schlüssel für den Hash. Dies führt zu einem Indexscan-Abfrageplan. Die Verwendung bestimmt, welche Spalten indiziert werden sollen.  
  
 Wenn eine Spalte in einem nicht gruppierten Index in vielen Zeilen denselben Wert hat (Indexschlüsselspalten verfügen über zahlreiche doppelte Werte), kann die Leistung bei Updates, Einfügungen und Löschungen abnehmen.  Eine Möglichkeit, die Leistung zu verbessern, ist in diesem Fall das Hinzufügen einer anderen Spalte zum nicht gruppierten Index.  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a>Vorgänge für speicheroptimierte und datenträgerbasierte Indizes.  
  
|Vorgang|Speicheroptimierter, nicht gruppierter Hashindex|Speicheroptimierter, nicht gruppierter Index|Datenträgerbasierter Index|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|Indexscan, alle Tabellenzeilen abrufen.|Ja|Ja|Ja|  
|Indexsuche auf Gleichheitsprädikaten (=).|Ja<br /><br /> (Vollständiger Schlüssel erforderlich.)|Ja<sup>1</sup>|Ja|  
|Index Suche auf Ungleichheits Prädikaten (>, <, \<=, > =, between).|Nein (führt zu einem Indexscan)|Ja<sup>1</sup>|Ja|  
|Abrufen der Zeilen in einer Sortierreihenfolge, die der Indexdefinition entspricht.|Nein|Ja|Ja|  
|Abrufen der Zeilen in einer Sortierreihenfolge, die der Umkehrung der Indexdefinition entspricht.|Nein|Nein|Ja|  
  
 In dieser Tabelle bedeutet "Ja", dass der Index die Anforderung adäquat bedienen kann, und "Nein" bedeutet, dass der Index nicht erfolgreich zum Erfüllen der Anforderung verwendet werden kann.  
  
 <sup>1</sup> für einen nicht gruppierten Speicher optimierten Index ist der vollständige Schlüssel nicht erforderlich, um eine Index Suche auszuführen. Obwohl bei Angabe der die Spaltenreihenfolge des Indexschlüssels ein Scan auftritt, wenn ein Wert für eine Spalte nach einer fehlenden Spalte kommt.  
  
## <a name="index-count"></a>Indexanzahl  
 Eine speicheroptimierte Tabelle kann über bis zu 8 Indizes verfügen, darunter den mit dem Primärschlüssel erstellten Index.  
  
 Hinsichtlich der Indexzahl bei speicheroptimierten Tabellen sollten Sie Folgendes berücksichtigen:  
  
-   Geben Sie beim Erstellen der Tabelle die erforderlichen Indizes an. Nach dem Erstellen einer speicheroptimierten Tabelle ist es nicht mehr möglich, einen Index zu hinzuzufügen. Wenn Sie einer speicheroptimierten Tabelle einen Index hinzufügen möchten, verwerfen Sie diese Tabelle und erstellen Sie sie neu.  
  
-   Erstellen Sie keinen Index, den Sie selten verwenden:  
  
     Die automatische Speicherbereinigung funktioniert am besten, wenn alle Indizes einer Tabelle häufig verwendet werden. Selten verwendete Indizes können dazu führen, dass das System der automatischen Speicherbereinigung für alte Zeilenversionen nicht optimal ausgeführt wird.  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a>Erstellen eines speicheroptimierten Indexes: Codebeispiele  
 Spaltenebenen-Hashindex:  
  
```sql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Tabellenebenen-Hashindex:  
  
```sql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Hashindex des primären Schlüssels auf Spaltenebene:  
  
```sql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Hashindex des primären Schlüssels auf Tabellenebene:  
  
```sql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Nicht gruppierter Index auf Spaltenebene:  
  
```sql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Nicht gruppierter Index auf Tabellenebene:  
  
```sql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 Nicht gruppierter Index des primären Schlüssels auf Spaltenebene:  
  
```sql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Nicht gruppierter Index des primären Schlüssels auf Tabellenebene:  
  
```sql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 Nach Definition der Spalten definierter mehrspaltiger Index:  
  
```sql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indizes für Speicher optimierte Tabellen](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Bestimmen der korrekten Bucketanzahl für Hash Indizes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md)   
 [Hash Indizes](hash-indexes.md)  
  
  
