---
title: Wichtige Änderungen an Datenbank-Engine Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bf1a25aabde1e684407218da7365ae7a2b4265a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726265"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2014"></a>Fehlerhafte Änderungen an Funktionen der Datenbank-Engine in SQL Server 2014
  In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] und früheren Versionen von beschrieben [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade auftreten. Weitere Informationen finden Sie unter [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
##  <a name="breaking-changes-in-sssql14"></a><a name="SQL14"></a> Wichtige Änderungen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Keine neuen Probleme.  
  
##  <a name="breaking-changes-in-sssql11"></a><a name="Denali"></a> Wichtige Änderungen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Auswählen aus Spalten oder Tabellen mit dem Namen NEXT|In Sequenzen wird die ANSI-Standardfunktion NEXT VALUE FOR verwendet. Wenn eine Tabelle oder eine Spalte als Next benannt wird und für die Tabelle oder Spalte der Wert Alias gilt und der ANSI-Standard wie weggelassen wird, kann die resultierende Anweisung einen Fehler verursachen. Schließen Sie das ANSI-Standardschlüsselwort AS ein, um das Problem zu umgehen. Beispielsweise müssen `SELECT NEXT VALUE FROM Table` als `SELECT NEXT AS VALUE FROM Table` und `SELECT Col1 FROM NEXT VALUE` als `SELECT Col1 FROM NEXT AS VALUE` umgeschrieben werden.|  
|PIVOT-Operator|Der PIVOT-Operator ist nicht in Abfragen für einen rekursiven allgemeinen Tabellenausdruck zugelassen, wenn der Datenbank-Kompatibilitätsgrad auf 110 festgelegt wird. Schreiben Sie die Abfrage um, oder ändern Sie den Kompatibilitätsgrad in 100 oder niedriger. Die Verwendung von PIVOT in einer rekursiven CTE-Abfrage erzeugt falsche Ergebnisse, wenn mehrere Zeilen pro Gruppierung vorhanden sind.|  
|sp_setapprole und sp_unsetapprole|Der `OUTPUT`-Parameter des Cookies für `sp_setapprole` ist zurzeit als `varbinary(8000)` dokumentiert, was der korrekten maximalen Länge entspricht. Die aktuelle Implementierung gibt jedoch `varbinary(50)` zurück. Anwendungen müssen weiterhin `varbinary(8000)` reservieren, damit die Anwendung weiterhin ordnungsgemäß ausgeführt wird, falls die Rückgabegröße des Cookies in einer zukünftigen Version erhöht wird. Weitere Informationen finden Sie unter [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).|  
|EXECUTE AS|Der OUTPUT-Parameter des Cookies für EXECUTE AS ist zurzeit als `varbinary(8000)` dokumentiert, was der korrekten maximalen Länge entspricht. Die aktuelle Implementierung gibt jedoch `varbinary(100)` zurück. Anwendungen müssen weiterhin `varbinary(8000)` reservieren, damit die Anwendung weiterhin ordnungsgemäß ausgeführt wird, falls die Rückgabegröße des Cookies in einer zukünftigen Version erhöht wird. Weitere Informationen finden Sie unter [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).|  
|sys.fn_get_audit_file-Funktion|Es wurden zwei zusätzliche Spalten (**user_defined_event_id** und **user_defined_information**) hinzugefügt, um benutzerdefinierte Überwachungs Ereignisse zu unterstützen. Anwendungen, bei denen keine Spalten nach Name ausgewählt werden, geben möglicherweise mehr Spalten zurück als erwartet. Wählen Sie entweder Spalten nach Name aus, oder passen Sie die Anwendung so an, dass sie diese zusätzlichen Spalten zulässt.|  
|Reserviertes Schlüsselwort WITHIN|WITHIN ist jetzt ein reserviertes Schlüsselwort. Verweise auf Objekte oder Spalten mit der Bezeichnung "within" schlagen fehl. Benennen Sie das Objekt oder die Spalte um, oder schränken Sie den Namen mit Klammern oder Anführungszeichen ein.  Beispiel: `SELECT * FROM [within]`.|  
|CAST- und CONVERT-Vorgänge in berechneten Spalten des Typs `time` oder `datetime2`|In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist das Standardformat für CAST- und CONVERT-Vorgänge bei den Datentypen `time` und `datetime2` 121, sofern keiner der Typen im Ausdruck einer berechneten Spalte verwendet wird. Für berechnete Spalten ist das Standardformat 0. Dieses Verhalten wirkt sich auf berechnete Spalten aus, wenn sie erstellt werden und in Abfragen mit automatischer Parametrisierung oder in Einschränkungsdefinitionen verwendet werden.<br /><br /> Unter dem Kompatibilitätsgrad 110 ist das Standardformat für CAST- und CONVERT-Vorgänge im Fall der Datentypen `time` und `datetime2` immer 121. Basiert die Abfrage auf dem alten Verhalten, verwenden Sie einen Kompatibilitätsgrad unter 110, oder geben Sie in der betroffenen Abfrage explizit das Format 0 an.<br /><br /> Ein Update der Datenbank auf Kompatibilitätsgrad 110 ändert keine Benutzerdaten, die auf dem Datenträger gespeichert wurden. Sie müssen diese Daten entsprechend manuell korrigieren. Haben Sie beispielsweise SELECT INFO zum Erstellen einer Tabelle von einer Quelle verwendet, die einen Ausdruck für eine berechnete Spalte (oben beschrieben) beinhaltete, werden die Daten mit dem Format 0 anstelle der Definition der berechneten Spalte an sich gespeichert. Sie müssen diese Daten manuell aktualisieren, um sie an das Format 121 anzupassen.|  
|ALTER TABLE|Die ALTER TABLE-Anweisung lässt nur zweiteilige Tabellennamen (schema.object) zu. Das Angeben eines Tabellennamens mit den folgenden Formaten schlägt nun zum Zeitpunkt der Kompilierung mit Fehler 117 fehl:<br /><br /> server.database.schema.table<br /><br /> .database.schema.table<br /><br /> ..schema.table<br /><br /> Bei früheren Versionen wurde durch die Angabe des Formats "server.database.schema.table" der Fehler 4902 zurückgegeben. Die Angabe des Formats ".database.schema.table" oder "..schema.table" war erfolgreich. Um das Problem zu beheben, vermeiden Sie die Verwendung eines vierteiligen Präfixes.|  
|Durchsuchen von Metadaten|Abfragen einer Sicht mit FOR BROWSE oder SET NO_BROWSETABLE ON geben jetzt die Metadaten der Sicht zurück, jedoch nicht die Metadaten des zugrunde liegenden Objekts. Dieses Verhalten entspricht jetzt anderen Methoden zum Durchsuchen von Metadaten.|  
|SOUNDEX|Unter dem Datenbank-Kompatibilitätsgrad 110 implementiert die SOUNDEX-Funktion neue Regeln, durch die sich möglicherweise die Werte, die von der Funktion berechnet wurden, von den Werten unterscheiden, die unter vorherigen Kompatibilitätsgraden berechnet wurden. Möglicherweise sind die Indizes, Heaps oder CHECK-Einschränkungen, die die SOUNDEX-Funktion verwenden, nach dem Upgrade auf Kompatibilitätsgrad 110 erneut zu erstellen. Weitere Informationen finden Sie unter [SOUNDEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/soundex-transact-sql)
|Meldung zur Zeilenanzahl für fehlgeschlagene DML-Anweisungen|In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] sendet [!INCLUDE[ssDE](../includes/ssde-md.md)] konsistent das Token TDS DONE mit "RowCount: 0" an Clients, wenn bei einer DML-Anweisung ein Fehler auftritt. In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wird ein falscher Wert von -1 an den Client gesendet, wenn die DML-Anweisung, bei der ein Fehler auftritt, in einem TRY-CATCH-Block enthalten ist und entweder von [!INCLUDE[ssDE](../includes/ssde-md.md)] automatisch parametrisiert wird oder sich der TRY-CATCH-Block nicht auf der gleichen Ebene wie die fehlgeschlagene Anweisung befindet. Wenn beispielsweise ein TRY-CATCH-Block eine gespeicherte Prozedur aufruft und eine DML-Anweisung in der Prozedur fehlschlägt, empfängt der Client den Wert von -1 nicht korrekt.<br /><br /> Anwendungen, die auf diesem falschen Verhalten basieren, schlagen fehl.|  
|SERVERPROPERTY (' Edition ')|Installierte Produktedition der Instanz von [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Verwenden Sie den Wert dieser Eigenschaft, um die Funktionen und Beschränkungen zu ermitteln, wie z. B. die maximale Anzahl der CPUs, die vom installierten Produkt unterstützt werden.<br /><br /> Basierend auf der installierten Enterprise Edition kann "Enterprise Edition" oder "Enterprise Edition: Core-basierte Lizenzierung" zurückgegeben werden. Die Enterprise-Editionen unterscheiden sich anhand der maximalen Rechenkapazität, die von einer einzelnen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz genutzt wird. Weitere Informationen zu Rechen Kapazitätsgrenzen in finden Sie unter [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).|  
|CREATE LOGIN|Die `CREATE LOGIN WITH PASSWORD = '` *Password* - `' HASHED` Option kann nicht mit Hashes verwendet werden, die von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 7 oder früher erstellt wurden.|  
|CAST- und CONVERT-Vorgänge für `datetimeoffset`|Die einzigen Formate, die bei der Konvertierung von Datums- und Uhrzeittypen in `datetimeoffset` unterstützt werden, sind 0 oder 1. Bei allen anderen Konvertierungsformaten wird der Fehler 9809 zurückgegeben. So gibt der folgende Code z. B. den Fehler 9809 zurück.<br /><br /> `SELECT CONVERT(date, CAST('7070-11-25 16:25:01.00986 -02:07' as datetimeoffset(5)), 107);`|  
  
### <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten  
  
|Sicht|Beschreibung|  
|----------|-----------------|  
|sys.dm_exec_requests|Die Befehlsspalte wird von `nvarchar(16)` in `nvarchar(32)` geändert.|  
|sys.dm_os_memory_cache_counters|Die folgenden Spalten wurden umbenannt:<br /><br /> single_pages_kb ist jetzt: <br />                          pages_kb<br /><br /> multi_pages_kb<br />                           ist nun: pages_in_use_kb|  
|sys.dm_os_memory_cache_entries|Die Spalte pages_allocated_count Spalte wurde pages_kb umbenannt.|  
|sys.dm_os_memory_clerks|Die Spalten multi_pages_kb wurde entfernt.<br /><br /> Die Spalte single_pages_kb Spalte wurde pages_kb umbenannt.|  
|sys.dm_os_memory_nodes|Die folgenden Spalten wurden umbenannt:<br /><br /> single_pages_kb ist jetzt: <br />                            pages_kb<br /><br /> multi_pages_kb ist jetzt: <br />                            foreign_committed_kb|  
|sys.dm_os_memory_objects|Die folgenden Spalten wurden umbenannt.<br /><br /> pages_allocated_count ist jetzt:<br />                            pages_in_bytes<br /><br /> max_pages_allocated_count ist jetzt: max_pages_in_bytes|  
|sys.dm_os_sys_info|Die folgenden Spalten wurden umbenannt:<br /><br /> physical_memory_in_bytes ist jetzt: <br />                            physical_memory_kb<br /><br /> bpool_commit_target ist jetzt: <br />                            committed_target_kb<br /><br /> bpool_visible ist jetzt: <br />                            visible_target_kb<br /><br /> virtual_memory_in_bytes ist jetzt: <br />                            virtual_memory_kb<br /><br /> bpool_commited ist jetzt:<br />                            committed_kb|  
|sys.dm_os_workers|Die Spalte "locale" wurde entfernt.|  
  
### <a name="catalog-views"></a>Katalogsichten  
  
|Sicht|Beschreibung|  
|----------|-----------------|  
|sys.data_spaces<br /><br /> sys.partition_schemes<br /><br /> sys.filegroups<br /><br /> sys.partition_functions|"sys.data_spaces" und "sys.partition_functions" wurde eine neue Spalte (is_system) hinzugefügt. ("sys.partition_schemes" und "sys.filegroups" erben die Spalten von "sys.data_spaces".)<br /><br /> Der Wert 1 in dieser Spalte gibt an, dass das Objekt für Volltextindexfragmente verwendet wird.<br /><br /> In "sys.partition_functions", "sys.partition_schemes" und "sys.filegroups" ist die neue Spalte nicht die letzte Spalte. Überarbeiten Sie vorhandene Abfragen, die auf der Reihenfolge der Spalten basieren, die von diesen Katalogsichten zurückgegeben wurden.|  
  
### <a name="sql-clr-data-types-geometry-geography-and-hierarchyid"></a>SQL CLR-Datentypen (geometry, geography und hierarchyid)  
 Die Assembly **Microsoft.SqlServer.Types.dll**, die die räumlichen Datentypen und den hierarchyid-Typ enthält, wurde von Version 10,0 auf Version 11,0 aktualisiert. Benutzerdefinierte Anwendungen, die auf diese Assembly verweisen, schlagen möglicherweise fehl, wenn die folgenden Bedingungen den Wert "true" aufweisen.  
  
-   Wenn Sie eine benutzerdefinierte Anwendung von einem Computer, auf dem [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] installiert wurde, auf einen Computer verschieben, auf dem nur [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] installiert ist, schlägt die Anwendung fehl, da die referenzierte Version 10,0 der **SqlTypes** -Assembly nicht vorhanden ist. Möglicherweise wird folgende Fehlermeldung angezeigt: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Wenn Sie auf die Version 11,0 der **SqlTypes** -Assembly verweisen und Version 10,0 ebenfalls installiert ist, wird möglicherweise die folgende Fehlermeldung angezeigt:`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   Wenn Sie von einer benutzerdefinierten Anwendung, die auf .NET 3,5, 4 oder 4,5 ausgerichtet ist, auf die **SqlTypes** -Assemblyversion 11,0 verweisen, schlägt die Anwendung fehl, da SqlClient nach dem Entwurf Version 10,0 der Assembly lädt. Dieser Fehler tritt auf, wenn die Anwendung eine der folgenden Methoden aufruft:  
  
    -   `GetValue`-Methode der `SqlDataReader`-Klasse  
  
    -   `GetValues`-Methode der `SqlDataReader`-Klasse  
  
    -   Klammerindexoperator [] der `SqlDataReader`-Klasse  
  
    -   `ExecuteScalar`-Methode der `SqlCommand`-Klasse  
  
 Sie können dieses Problem mithilfe einer der folgenden Methoden umgehen:  
  
-   Sie können dieses Problem im Code umgehen, indem Sie anstelle der oben aufgeführten Get-Methoden die `GetSqlBytes`-Methode aufrufen, um CLR-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Systemtypen abzurufen. Hierzu ein Beispiel:  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   Sie können dieses Problem umgehen, indem Sie eine Assemblyumleitung in der Anwendungskonfigurationsdatei verwenden. Siehe folgendes Beispiel:  
  
    ```xml  
    <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    <runtime>  
    ```  
  
-   Sie können dieses Problem in der Verbindungszeichenfolge umgehen, indem Sie den Wert "SQL Server 2012" für das Attribut "Typsystemversion" angeben, um SqlClient zu zwingen, Version 11.0 der Assembly zu laden. Dieses Verbindungszeichenfolgenattribut ist erst ab .NET 4.5 verfügbar.  
  
-   Das `assemblyBinding`-Tag sollte unter dem `runtime`-Tag eingebunden werden.  
  
### <a name="support-for-awe"></a>Unterstützung für AWE  
 AWE (Address Windowing Extensions, 32-Bit-Version) wird nicht mehr unterstützt. Dies könnte bei 32-Bit-Betriebssystemen zu geringerer Leistungsstärke führen. Migrieren Sie bei Installationen mit großem Arbeitsspeichervolumen zu einem 64-Bit-Betriebssystem.  
  
### <a name="xquery-functions-are-surrogate-aware"></a>XQuery-Funktionen sind ersatzzeichenabhängig  
 Die W3C-Empfehlung für XQuery-Funktionen und -Operatoren erfordert die Berücksichtigung eines Ersatzzeichenpaares, das ein Unicode-Zeichen für den oberen Bereich als einzelnes Symbol in UTF-16-Codierung darstellt. In Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vor [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] erkannten Zeichenfolgenfunktionen Ersatzzeichenpaare jedoch nicht als einzelnes Zeichen. Einige Zeichen folgen Operationen, z. b. Zeichen folgen Längen Berechnungen und Teil zeichenfolgenextraktionen, haben falsche Ergebnisse zurückgegeben [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt jetzt vollständig UTF-16 sowie die richtige Verarbeitung von Ersatzzeichenpaaren.  
  
 Der XML-Datentyp in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] lässt nur wohlgeformte Ersatzzeichenpaare zu. Einige Funktionen können jedoch unter bestimmten Umständen nicht definierte oder unerwartete Ergebnisse zurückgeben, da ungültige oder partielle Ersatzzeichenpaare an XQuery-Funktionen als Zeichenfolgenwerte übergeben werden können. Ziehen Sie die folgenden Methoden zum Generieren von Zeichenfolgenwerten in Betracht, wenn Sie XQuery in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwenden:  
  
-   Stellen Sie einen konstanten Zeichenfolgenwert als Binärwert bereit. Bei Verwendung dieser Methode ist es weiterhin möglich, ungültige oder partielle Ersatzzeichenpaare zu übergeben.  
  
-   Stellen Sie einen konstanten Zeichenfolgenwert bereit, indem Sie Zeichenentitäten bereitstellen. Bei Verwendung dieser Methode ist es nicht möglich, ungültige Ersatzzeichenpaare zu übergeben. Die XQuery-Funktionen erfordern eine einzelne Zeichenentität für das Zeichen auf hoher Ebene. Diese Funktionen lösen einen Fehler aus, wenn die Zeichenentitäten für die Ersatzzeichenpaare bereitgestellt werden.  
  
-   Importieren Sie externe Werte mithilfe von **SQL: column** oder **SQL: Variable**. Bei Verwendung dieser Methoden ist es weiterhin möglich, ungültige oder partielle Ersatzzeichenpaare einzuführen.  
  
#### <a name="affected-xquery-functions-and-operators"></a>Betroffene XQuery-Funktionen und -Operatoren  
 Die folgenden XQuery-Funktionen und -Operatoren verarbeiten jetzt UTF-16-Ersatzzeichenpaare ordnungsgemäß in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]:  
  
-   **FN: String-length**. Wenn jedoch ein ungültiges oder partielles Ersatz Zeichenpaar als Argument übermittelt wird, ist das Verhalten von **String-length** nicht definiert.  
  
-   **FN: Teil Zeichenfolge**.  
  
-   **FN: enthält**. Wenn jedoch ein partielles Ersatz Zeichenpaar als Wert übermittelt wird, gibt enthält möglicherweise unerwartete Ergebnisse zurück, da es möglicherweise das partielle Ersatz Zeichenpaar **enthält** , das in einem wohlgeformten Ersatz Zeichenpaar enthalten ist.  
  
-   **FN: Concat**. Wenn jedoch ein partielles Ersatz Zeichenpaar als Wert übermittelt wird, kann **Concat** falsche Ersatz Zeichenpaare oder partielle Ersatz Zeichenpaare liefern.  
  
-   Vergleichs Operatoren und die **Order by** -Klausel. Vergleichs Operatoren umfassen +, \<, > , \<=, > =, `eq` , `lt` , `gt` , `le` und `ge` .  
  
#### <a name="distributed-query-calls-to-a-system-procedure"></a>Aufrufe von verteilten Abfragen an eine Systemprozedur  
 Aufrufe von verteilten Abfragen über `OPENQUERY` an einige Systemprozeduren schlagen fehl, wenn sie von einem [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Server für einen anderen aufgerufen werden. Dies tritt auf, wenn das [!INCLUDE[ssDE](../includes/ssde-md.md)] keine Metadaten für eine Prozedur ermitteln kann. Beispiel: `SELECT * FROM OPENQUERY(..., 'EXEC xp_loginfo')`.  
  
#### <a name="isolation-level-and-sp_reset_connection"></a>Isolationsstufe und sp_reset_connection  
 Die Isolationsstufe für Verbindungen wird von Client-Treibern wie folgt behandelt:  
  
-   Alle nativen Treiber (SNAC, MDAC, ODBC) legen die Isolationsstufe (auf Grundlage der Anwendungseinstellung) auf sp_reset_connection fest.  
  
-   Für ADO.NET erhalten Sie im Wesentlichen eine zufällige Isolationsstufe, je nachdem, welche Verbindung Sie aus dem Pool abrufen (und ob die Anwendung eine andere Isolationsstufe verwendet). Da ein ADO.NET-Pool Verbindungen intern und transparent wiederverwenden kann, können Sie nicht vorhersagen, was Sie aus dem Pool erhalten werden.  
  
-   Für den JDBC-Treiber erhalten Sie dasselbe Verhalten wie für ADO.NET.  
  
     Die Anwendung muss nach dem Öffnen der Verbindung immer explizit die Isolationsstufe festlegen, um zu erhalten, was sie benötigt.  
  
     Die JDBC-Verbindung kann gepoolt werden, sodass die Anwendung eine zufällige Isolationsstufe erhalten kann, ohne dies zu wissen.  
  
 Um die Abwärtskompatibilität aufrechtzuerhalten, gilt dieses neue Verhalten nur für aktuelle Clients ab TDS 7.4.  
  
#### <a name="backward-compatibility"></a>Backward Compatibility  
 **Neues Verhalten hängt vom Kompatibilitätsgrad ab**  
  
 Die folgenden Funktionen und Operatoren zeigen das neue oben beschriebene Verhalten nur, wenn der Kompatibilitätsgrad mindestens 110 ist:  
  
-   **FN: enthält**.  
  
-   **FN: Concat**.  
  
-   Vergleichs Operatoren und **Order by** -Klausel  
  
 **Neues Verhalten hängt vom Standardnamespace-URI für Funktionen ab**  
  
 Die folgenden Funktionen veranschaulichen das oben beschriebene neue Verhalten nur dann, wenn der standardmäßige Namespace-URI dem-Namespace in der endgültigen Empfehlung entspricht, d [http://www.w3.org/2005/xpath-functions](http://www.w3.org/2005/xpath-functions) . h.. Wenn der Kompatibilitätsgrad mindestens 110 ist, bindet [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] den Standardfunktionsnamespace standardmäßig an diesen Namespace. Diese Funktionen zeigen das neue Verhalten, wenn dieser Namespace unabhängig vom Kompatibilitätsgrad verwendet wird.  
  
-   **FN: String-length**  
  
-   **FN: Teil Zeichenfolge**  
  
##  <a name="breaking-changes-in-sql-server-2008sql-server-2008r2"></a><a name="KJKatmai"></a>Wichtige Änderungen in SQL Server 2008/SQL Server 2008R2  
 Dieser Abschnitt enthält die in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] eingeführten wichtigen Änderungen. In [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] wurden keine Änderungen eingeführt.  
  
### <a name="collations"></a>Sortierungen  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Neue Sortierungen|In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] werden neue Sortierungen eingeführt, die vollständig an die Sortierungen von Windows Server 2008 angepasst sind. Durch die 80 neuen Sortierungen wurde die linguistische Genauigkeit verbessert; sie sind mit dem Versionshinweis "* _100" gekennzeichnet. Beachten Sie, dass eine neue Sortierung für den Server oder die Datenbank möglicherweise von Clients mit älteren Treibern nicht erkannt wird. Unbekannte Sortierungen können zu Anwendungsfehlern führen. Ziehen Sie die folgenden Lösungen in Betracht:<br /><br /> Aktualisieren Sie das Clientbetriebssystem, um die zugrunde liegenden Systemsortierungen zu aktualisieren.<br /><br /> Wenn auf dem Client Datenbankclient-Software installiert ist, sollten Sie ein Dienstupdate der Datenbankclient-Software in Erwägung ziehen.<br /><br /> Wählen Sie eine vorhandene Sortierung aus, die einer Codepage auf dem Client zugeordnet wird.|  
  
### <a name="common-language-runtime-clr"></a>Common Language Runtime (CLR)  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|CLR-Assemblys|Wenn eine Datenbank auf [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] aktualisiert wird, wird die `Microsoft.SqlServer.Types`-Assembly zur Unterstützung neuer Datentypen automatisch installiert. Upgrade Advisor-Regeln erkennen alle Benutzertypen oder Assemblys mit in Konflikt stehenden Namen. Der Upgrade Advisor schlägt im Fall von in Konflikt stehenden Assemblys das Umbenennen vor, und bei in Konflikt stehenden Typen das Umbenennen oder das Verwenden von zweiteiligen Namen im Code, um auf diesen bereits vorhandenen Benutzertypen zu verweisen.<br /><br /> Wenn bei einem Datenbankupgrade eine Benutzerassembly mit in Konflikt stehendem Namen entdeckt wird, wird diese Assembly automatisch umbenannt und die Datenbank in den Fehlerverdachtmodus versetzt.<br /><br /> Sollte während des Upgrades ein Benutzertyp mit in Konflikt stehendem Namen vorhanden sein, werden keine speziellen Schritte ausgeführt. Nach dem Upgrade sind sowohl der alte Benutzertyp als auch der neue Systemtyp vorhanden. Der Benutzertyp steht nur bei Verwendung von zweiteiligen Namen zur Verfügung.|  
|CLR-Assemblys|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] installiert .NET Framework 3.5 SP1, wodurch Bibliotheken im globalen Assemblycache (Global Assembly Cache, GAC) aktualisiert werden. Wenn die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank nicht unterstützte Bibliotheken enthält, kann die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Anwendung nach einem Upgrade auf [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] möglicherweise nicht mehr verwendet werden. Das liegt daran, dass durch Warten oder Aktualisieren von Bibliotheken im GAC die entsprechenden Assemblys in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht aktualisiert werden. Wenn eine Assembly sowohl in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank als auch im GAC vorhanden ist, müssen die beiden Kopien der Assembly genau übereinstimmen. Stimmen sie nicht überein, tritt ein Fehler auf, wenn die Assembly von der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] CLR-Integration verwendet wird. Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).<br /><br /> Bedienen oder aktualisieren Sie nach dem Upgrade der Datenbank die Kopie der Assembly in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbanken mit der ALTER ASSEMBLY-Anweisung. Weitere Informationen finden Sie im [Knowledge Base-Artikel 949080](https://go.microsoft.com/fwlink/?LinkId=154563).<br /><br /> Sie können auch die folgende Abfrage in Ihrer Datenbank ausführen, um festzustellen, ob in der Anwendung nicht unterstützte .NET Framework-Bibliotheken verwendet werden.<br /><br /> `SELECT name FROM sys.assemblies WHERE clr_name LIKE '%publickeytoken=b03f5f7f11d50a3a,%';`|  
|CLR-Routinen|Durch Identitätswechsel innerhalb der benutzerdefinierten CLR-Funktionen, benutzerdefinierten Aggregate oder benutzerdefinierten Typen (User-Defined Types, UDTs) können kann nach dem Upgrade auf [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] bei der Anwendung der Fehler 6522 auftreten. Die folgenden Szenarios können in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] erfolgreich ausgeführt werden, nicht jedoch in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Für jedes Szenario werden Auflösungen bereitgestellt.<br /><br /> Eine CLR-benutzerdefinierte Funktion, ein benutzerdefiniertes Aggregat oder eine UDT-Methode, die einen Identitätswechsel verwendet, verfügt über einen Parameter vom Typ `nvarchar(max)` , `varchar(max)` ,, `varbinary(max)` `ntext` , `text` , `image` oder einen großen UDT und weist nicht das **DataAccessKind. Read** -Attribut für die Methode auf. Um dieses Problem zu beheben, fügen Sie das **DataAccessKind. Read** -Attribut der Methode hinzu, kompilieren Sie die Assembly erneut, und stellen Sie die Routine und die Assembly erneut bereit.<br /><br /> Eine CLR-Tabellenwert Funktion, die über eine **Init** -Methode verfügt, die Identitätswechsel ausführt. Um dieses Problem zu beheben, fügen Sie das **DataAccessKind. Read** -Attribut der Methode hinzu, kompilieren Sie die Assembly erneut, und stellen Sie die Routine und die Assembly erneut bereit.<br /><br /> Eine CLR-Tabellenwert Funktion, die über eine **FillRow** -Methode verfügt, die Identitätswechsel ausführt. Um dieses Problem zu beheben, entfernen Sie den Identitätswechsel von der **FillRow** -Methode. Greifen Sie nicht mit der **FillRow** -Methode auf externe Ressourcen zu. Greifen Sie stattdessen über die **Init** -Methode auf externe Ressourcen zu.|  
  
### <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten  
  
|Sicht|Beschreibung|  
|----------|-----------------|  
|sys.dm_os_sys_info|Entfernt die Spalte cpu_ticks_in_ms- und die sqlserver_start_time_cpu_ticks.|  
|sys. dm_exec_query_resource_semaphoressys. dm_exec_query_memory_grants|Die Spalte resource_semaphore_id-Spalte stellt keine eindeutige ID in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] dar. Diese Änderung kann die Abfrageausführung bei der Problembehandlung beeinflussen. Weitere Informationen finden Sie unter [sys. dm_exec_query_resource_semaphores &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
  
### <a name="errors-and-events"></a>Fehler und Ereignisse  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Fehler beim Anmelden|In [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] wird der Fehler 18452 zurückgegeben, wenn versucht wird, mit einem SQL-Anmeldenamen eine Verbindung zu einem Server herzustellen, der nur die Windows-Authentifizierung verwendet. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] wird stattdessen der Fehler 18456 zurückgegeben.|  
  
### <a name="showplan"></a>Showplan  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Showplan (XML-Schema)|Ein neues **seekpredikatenew** -Element wird dem Showplan-XML-Schema hinzugefügt, und die einschließende XSD-Sequenz (**sqlpredikatestype**) wird in ein **\<xsd:choice>** Element konvertiert. Anstelle von mindestens einem **SeekPredicate** -Element kann jetzt mindestens ein **seekpredikatenew** -Element in der Showplan-XML-Datei angezeigt werden. Die beiden Elemente schließen sich gegenseitig aus. **SeekPredicate** wird im Showplan-XML-Schema für die Abwärtskompatibilität beibehalten. Abfrage Pläne, die in erstellt wurden, [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] können jedoch das **seekpredierenew** -Element enthalten. Anwendungen, die nur das untergeordnete **SeekPredicate** -Element aus dem Knoten ShowPlanXML/BatchSequence/Batch/Statements/StmtSimple/QueryPlan/RelOp/Indexscan/seekprediates abrufen, schlagen möglicherweise fehl, wenn das **SeekPredicate** -Element nicht vorhanden ist. Schreiben Sie die Anwendung neu, um entweder das **SeekPredicate** -oder das **seekpredikatenew** -Element in diesem Knoten zu erwarten. Weitere Informationen finden Sie unter .|  
|Showplan (XML-Schema)|Ein neues **IndexKind** -Attribut wird dem komplexen **ObjectType** -Typ im Showplan-XML-Schema hinzugefügt. Anwendungen, die eine strenge Validierung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Plänen anhand des [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]-Schemas durchführen, generieren einen Fehler.|  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|ALTER_AUTHORIZATION_DATABASE DDL-Ereignis|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]Wenn in das DDL-Ereignis ALTER_AUTHORIZATION_DATABASE ausgelöst wird, wird der Wert "Object" im **ObjectType** -Element der EventData-XML für dieses Ereignis zurückgegeben, wenn der Entitätstyp des Sicherungs fähigen Elements im DDL-Vorgang (Data Definition Language, Datendefinitionssprache) ein Objekt ist. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] wird der tatsächliche Typ (z. B. "table" oder "function") zurückgegeben.|  
|CONVERT|Wenn ein ungültiges Format an die CONVERT-Funktion übergeben wird und eine Konvertierung vom Binärformat ins Zeichenformat oder vom Zeichenformat ins Binärformat ausgeführt werden soll, wird ein Fehler zurückgegeben. In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde das ungültige Format bei Konvertierungen vom Binärformat ins Zeichenformat oder vom Zeichenformat ins Binärformat auf das Standardformat festgelegt.|  
|GRANT/DENY/REVOKE EXECUTE für Assemblys|EXECUTE-Berechtigungen können nicht für Assemblys gewährt, verweigert oder widerrufen werden. Diese Berechtigung hat keine Auswirkungen mehr und generiert einen Fehler. Gewähren, verweigern oder widerrufen Sie die EXECUTE-Berechtigung stattdessen für gespeicherte Prozeduren oder Funktionen, die auf die Assemblymethode verweisen.|  
|GRANT/DENY/REVOKE-Berechtigungen für Systemtypen|Berechtigungen können nicht für Systemtypen gewährt, verweigert oder widerrufen werden. Diese Anweisungen können in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zwar erfolgreich ausgeführt werden; sie haben jedoch keine Auswirkungen. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] wird ein Fehler zurückgegeben.|  
|GROUP BY|Die GROUP BY-Klausel darf keine Unterabfrage in einem Ausdruck enthalten, der für die GROUP BY-Liste verwendet wird. In älteren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] war dies noch zulässig. In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] wird der Fehler 144 zurückgegeben.<br /><br /> Beispielsweise ist die Ausführung des folgenden Codes in SQL Server 2005 erfolgreich, in SQL Server 2008 hingegen nicht.<br /><br /> `DECLARE @Test TABLE(a int NOT NULL);` <br /> `INSERT INTO @Test SELECT 1 union ALL SELECT 2;` <br /> `SELECT COUNT(*)` <br /> `FROM @Test` <br /> `GROUP BY CASE WHEN a IN (SELECT t.a FROM @Test AS t)` <br /> `THEN 1 ELSE 0` <br /> `END;`|  
|OUTPUT-Klausel|Um nicht deterministisches Verhalten zu vermeiden, darf die OUTPUT-Klausel nicht auf eine Spalte einer Sicht oder Inline-Tabellenwertfunktion verweisen, wenn diese Spalte mithilfe einer der folgenden Methoden definiert wurde:<br /><br /> Eine Unterabfrage.<br /><br /> Eine benutzerdefinierte Funktion, die auf Benutzer- oder Systemdaten zugreift bzw. bei der davon ausgegangen wird, dass sie einen solchen Zugriff ausführt.<br /><br /> Eine berechnete Spalte, die eine benutzerdefinierte Funktion enthält, die in ihrer Definition auf Benutzer- oder Systemdaten zugreift.<br /><br /> <br /><br /> Wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine solche Spalte in der OUTPUT-Klausel erkennt, wird der Fehler 4186 ausgelöst. Weitere Informationen finden Sie unter [MSSQLSERVER_4186](../relational-databases/errors-events/mssqlserver-4186-database-engine-error.md).|  
|OUTPUT INTO-Klausel|Für die Zieltabelle der OUTPUT INTO-Klausel dürfen keine Trigger aktiviert sein.|  
|Rang vorausberechnen-Option auf Serverebene|Diese Option wird in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] nicht unterstützt. Ändern Sie Anwendungen, die diese Funktion derzeit verwenden, so schnell wie möglich.|  
|READPAST-Tabellenhinweis|Unter Momentaufnahmeisolation dürfen Sie den READPAST-Hinweis nicht angeben.<br /><br /> Der READPAST-Hinweis wird ignoriert, wenn entweder die READ_COMMITED_SNAPSHOT-Datenbankoption oder die ALLOW_SNAPSHOT_ISOLATION-Datenbankoption auf ON festgelegt ist. Wenn Sie den READPAST-Hinweis jedoch mit READCOMMITTEDLOCK kombinieren, ist das READPAST-Verhalten mit dem des blockierenden READCOMMITTED-Hinweises identisch.|  
|sp_helpuser|Die folgenden Spaltennamen, die im Resultset der gespeicherten Prozedur sp_helpuser zurückgegeben werden, wurden geändert:<br /><br /> GroupName ist jetzt:<br />                            RoleName<br /><br /> Group_name ist jetzt:<br />                            Role_name<br /><br /> Group_id ist jetzt:<br />                            Role_id<br /><br /> Users_in_group ist jetzt:<br />                            Users_in_role|  
|Transparente Datenverschlüsselung|Die transparente Datenverschlüsselung (Transparent Data Encryption, TDE) erfolgt auf E/A-Ebene: Die Struktur der Seite im Speicher ist nicht verschlüsselt, und die Seite wird erst beim Schreiben auf einen Datenträger verschlüsselt. Die Datenbankdateien und die Protokolldateien werden verschlüsselt. Anwendungen von Drittanbietern, die den regulären Seitenzugriffsmechanismus von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] umgehen, beispielsweise durch direktes Scannen der Daten- oder Protokolldateien), generieren einen Fehler, wenn TDE in einer Datenbank verwendet wird, da die Daten in den Dateien verschlüsselt sind. In diesen Fällen kann mithilfe der Windows-Kryptografie-API eine Lösung zum Entschlüsseln der Daten außerhalb von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für die Anwendungen entwickelt werden.|  
  
### <a name="xquery"></a>XQuery  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Datetime-Unterstützung|Die Datentypen `xs:time`, `xs:date` und `xs:dateTime` in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] unterstützen keine Zeitzonen. Zeitzonendaten werden der UTC-Zeitzone zugeordnet. [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] stellt standardkonformes Verhalten bereit. Dies führt zu folgenden Änderungen:<br /><br /> Werte ohne Zeitzone werden überprüft.<br /><br /> Die bereitgestellte Zeitzone wird beibehalten; wenn keine Zeitzone bereitgestellt wird, wird diese Einstellung ebenfalls beibehalten.<br /><br /> Die interne Speicherdarstellung wird geändert.<br /><br /> Die Auflösung von gespeicherten Werten wird erhöht.<br /><br /> Negative Jahre sind nicht zulässig.<br /><br /> <br /><br /> Hinweis: Ändern Sie Anwendungen und XQuery-Ausdrücke, um die neuen Typwerte zu berücksichtigen.|  
|XQuery und Xpath-Ausdrücke|In [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] sind Schritte in einem XQuery-oder XPath-Ausdruck zulässig, die mit einem Doppelpunkt (': ') beginnen. Die folgende Anweisung enthält zum Beispiel einen Namenstest (`CTR02)`) innerhalb des Pfadausdrucks, der mit einem Doppelpunkt beginnt.<br /><br /> `SELECT FileContext.query('for n$ in //CTR return <C>{data )(n$/:CTR02)} </C>) AS Files FROM dbo.MyTable;`<br /><br /> In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ist diese Verwendung nicht zulässig, da sie nicht den XML-Standards entspricht. Der Fehler 9341 wird zurückgegeben. Entfernen Sie den führenden Doppelpunkt, oder geben Sie ein Präfix für den Namenstest an, z. B. (n$/p1:CTR02) oder (n$/CTR02).|  
  
### <a name="connecting"></a>Verbindung  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Herstellen einer Verbindung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client mithilfe von SSL|Aufgrund der weniger strengen Überprüfung wurde in der Vergangenheit für Anwendungen, die "SERVER=shortname; FORCE ENCRYPTION=true" mit Zertifikat verwendeten, in dessen Betreff vollqualifizierte Domänennamen (FQDNs) enthalten waren, eine Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client hergestellt. SQL Server 2008 R2 erhöht die Sicherheit, indem ein FQDN-Betreff für Zertifikate erzwungen wird. Anwendungen, die auf einer weniger strengen Überprüfung basieren, müssen eine der folgenden Aktionen ausführen:<br /><br /> Verwenden des FQDNs in der Verbindungszeichenfolge<br /><br /> : Diese Option erfordert kein Neukompilieren der Anwendung, wenn das Server Schlüsselwort der Verbindungs Zeichenfolge außerhalb der Anwendung konfiguriert wird.<br /><br /> Diese Option funktioniert nicht für Anwendungen, deren Verbindungs Zeichenfolgen hart codiert sind.<br /><br /> Diese Option funktioniert nicht für Anwendungen, die die Daten Bank Spiegelung verwenden, da der gespiegelte Server mit einem einfachen Namen antwortet.|  
||Hinzufügen eines Alias für den Kurznamen, um eine Zuordnung mit dem FQDN herzustellen<br /><br /> Diese Option funktioniert auch für Anwendungen, deren Verbindungs Zeichenfolgen hart codiert sind.<br /><br /> Diese Option funktioniert nicht für Anwendungen, die die Daten Bank Spiegelung verwenden, da die Anbieter keine Aliase für empfangene Failoverpartnernamen suchen.|  
||Für den Kurznamen muss ein Zertifikat ausgestellt werden.<br /><br /> Diese Option funktioniert für alle Anwendungen.|  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="Yukon"></a>Wichtige Änderungen in SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Weitere Informationen  
 [Veraltete Datenbank-Engine Features in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)   
 [Verhaltensänderungen an Datenbank-Engine Features in SQL Server 2014](../../2014/database-engine/behavior-changes-to-database-engine-features-in-sql-server-2014.md?view=sql-server-2014)   
 [Nicht mehr unterstützte Datenbank-Engine Funktionen in SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md?view=sql-server-2014)   
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
 [Wichtige Änderungen an Funktionen der Verwaltungstools in SQL Server 2014](breaking-changes-to-management-tools-features-in-sql-server-2014.md?view=sql-server-2014)  
  
