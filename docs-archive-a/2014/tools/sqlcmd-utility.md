---
title: sqlcmd-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbe5a3dcefb2218543e015dad71acfe79aea8e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723241"
---
# <a name="sqlcmd-utility"></a>SQLCMD-Hilfsprogramm
  Mithilfe des `sqlcmd` Hilfsprogramms können Sie [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, System Prozeduren und Skriptdateien an der Eingabeaufforderung, im **Abfrage-Editor** im SQLCMD-Modus, in einer Windows-Skriptdatei oder in einem Betriebssystem-Auftrags Schritt (Cmd.exe) eines-Agent-Auftrags eingeben [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Dieses Hilfsprogramm verwendet zum Ausführen von [!INCLUDE[tsql](../includes/tsql-md.md)]-Batches ODBC.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]verwendet den [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SqlClient zur Ausführung im regulären und im SQLCMD-Modus im **Abfrage-Editor**. Beim Ausführen von `sqlcmd` über die Befehlszeile verwendet `sqlcmd` den ODBC-Treiber. Da unterschiedliche Standardoptionen gelten können, führt die Ausführung derselben Abfrage im SQLCMD-Modus von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] und im Hilfsprogramm `sqlcmd` möglicherweise zu unterschiedlichen Ergebnissen.  
  
 Derzeit erfordert `sqlcmd` kein Leerzeichen zwischen der Befehlszeilenoption und dem Wert. In einer zukünftigen Version kann jedoch ein Leerzeichen zwischen der Befehlszeilenoption und dem Wert erforderlich sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a>Befehlszeilenoptionen  
 **Anmeldungsvorgänge**  
  **-A**  
 Bewirkt die Anmeldung an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC). Diese Verbindungsart wird verwendet, um Serverprobleme zu behandeln. Diese Option kann nur bei Servercomputern verwendet werden, die DAC unterstützen. Wenn DAC nicht verfügbar ist, generiert `sqlcmd` eine Fehlermeldung und wird dann beendet. Weitere Informationen zu DAC finden Sie unter [Diagnoseverbindung für Datenbankadministratoren](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).  
  
 **-C**  
 Dieser Schalter wird vom Client verwendet, um ihn so zu konfigurieren, dass er dem Serverzertifikat ohne Überprüfung implizit vertraut. Diese Option entspricht der ADO.NET-Option `TRUSTSERVERCERTIFICATE = true`.  
  
 **-d** _Datenbankname_  
 Gibt eine `USE` *db_name* Anweisung aus, wenn Sie starten `sqlcmd` . Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDDBNAME festgelegt. Hierdurch wird die Ausgangsdatenbank angegeben. Der Standardwert ist die Standarddatenbank-Eigenschaft der Anmelde-ID. Wenn die Datenbank nicht vorhanden ist, wird eine Fehlermeldung generiert und `sqlcmd` beendet.  
  
 **-l** _login_timeout_  
 Gibt an, wie viele Sekunden bei der Herstellung einer Verbindung mit einem Server verstreichen dürfen, bevor für eine `sqlcmd`-Anmeldung beim ODBC-Treiber ein Timeout eintritt. Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDLOGINTIMEOUT festgelegt. Der Standardwert für das Timeout eines `sqlcmd`-Anmeldevorgangs ist acht Sekunden. Der Timeoutwert für den Anmeldungszeitraum muss eine Zahl zwischen 0 und 65534 sein. Wenn der angegebene Wert kein numerischer Wert ist oder außerhalb dieses Bereichs liegt, generiert `sqlcmd` eine Fehlermeldung. Mit dem Wert 0 wird eine unbegrenzte Wartezeit festgelegt.  
  
 **-E**  
 Verwendet eine vertrauenswürdige Verbindung anstelle eines Benutzernamens und eines Kennworts für die Anmeldung bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Standardmäßig wird von `sqlcmd` die vertrauenswürdige Verbindung verwendet, wenn -E nicht angegeben ist.  
  
 Die Option **-E** ignoriert mögliche Umgebungsvariableneinstellungen für Benutzernamen und Kennwörter, z.B. SQLCMDPASSWORD. Wird die Option **-E** zusammen mit der Option **-U** oder der Option **-P** verwendet, wird eine Fehlermeldung generiert.  
  
 **-H** _Arbeitsstationsname_  
 Der Name einer Arbeitsstation. Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDWORKSTATION festgelegt. Der Name der Arbeitsstation wird in der **hostname**-Spalte der **sys.processes**-Katalogsicht aufgeführt, und der Name kann mithilfe der gespeicherten Prozedur **sp_who** zurückgegeben werden. Wenn diese Option nicht angegeben ist, wird standardmäßig der Name des aktuellen Computers angenommen. Mithilfe dieses Namens können verschiedene `sqlcmd`-Sitzungen identifiziert werden.  
  
 **-K** _Anwendungsabsicht_  
 Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Der einzige derzeit unterstützte Wert ist **ReadOnly**. Wenn **-K** nicht angegeben wird, unterstützt das sqlcmd-Hilfsprogramm keine Konnektivität mit einem sekundären Replikat in einer AlwaysOn-Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [aktive sekundäre Replikate: lesbare sekundäre Replikate](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 `-M`*multisubnet_failover*  
 Geben Sie immer `-M` an, wenn Sie eine Verbindung mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Verfügbarkeitsgruppenlistener oder einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failovercluster-Verfügbarkeitsgruppenlistener herstellen. `-M` gewährleistet eine schnellere Erkennung und Verbindung mit dem (gerade) aktiven Server. Wenn `-M` nicht angegeben ist, wird `-M` deaktiviert. Weitere Informationen zu [!INCLUDE[ssHADR](../includes/sshadr-md.md)] finden Sie unter [verfügbarkeitsgruppenlistener, Client Konnektivität und Anwendungs Failover &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [Erstellung und Konfiguration von Verfügbarkeits Gruppen &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen ](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)#b4 SQL Server&#41;und [aktive sekundäre Replikate: lesbare sekundäre Replikate](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .  
  
 **-N**  
 Dieser Schalter wird vom Client verwendet, um eine verschlüsselte Verbindung anzufordern.  
  
 **-P** _Kennwort_  
 Ein vom Benutzer angegebenes Kennwort. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Wenn die Option-U verwendet wird und die Option **-P** nicht verwendet wird und die SQLCMDPASSWORD-Umgebungsvariable nicht festgelegt wurde, wird `sqlcmd` der Benutzer von zur Angabe eines Kennworts aufgefordert. Wenn die Option **-P** am Ende der Eingabeaufforderung ohne Kennwort verwendet wird, `sqlcmd` verwendet das Standard Kennwort (null).  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort. Weitere Informationen finden Sie unter [Strong Passwords](../relational-databases/security/strong-passwords.md).  
  
 Die Aufforderung zur Eingabe des Kennworts wird folgendermaßen an der Konsole ausgegeben: `Password:`  
  
 Die Benutzereingabe bleibt verborgen, d. h. es erfolgt keine Anzeige, und der Cursor bleibt an der Anfangsposition.  
  
 Über die SQLCMDPASSWORD-Umgebungsvariable können Sie ein Standardkennwort für die aktuelle Sitzung festlegen. Aus diesem Grund ist die Hartcodierung von Kennwörtern in Batchdateien nicht notwendig.  
  
 Im folgenden Beispiel wird zuerst die SQLCMDPASSWORD-Variable an der Eingabeaufforderung festgelegt und dann auf das Hilfsprogramm `sqlcmd` zugegriffen. Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  Das Kennwort kann von jeder Person gelesen werden, die auf den Computerbildschirm schauen kann.  
  
 Geben Sie Folgendes an der daraufhin angezeigten Eingabeaufforderung ein:  
  
 `sqlcmd`  
  
 Wenn die Kombination aus Benutzername und Kennwort falsch ist, wird eine Fehlermeldung generiert.  
  
> [!NOTE]  
>  Die OSQLPASSWORD-Umgebungsvariable wurde aus Gründen der Abwärtskompatibilität beibehalten. Die SQLCMDPASSWORD-Umgebungsvariable hat Vorrang vor der OSQLPASSWORD-Umgebungsvariablen. Dies bedeutet, dass `sqlcmd` und **osql** ohne Störungen nebeneinander verwendet werden können und dass alte Skripts weiterhin funktionieren.  
  
 Wird die Option **-P** zusammen mit der Option **-E** verwendet, wird eine Fehlermeldung generiert.  
  
 Werden nach der Option **-P** mehrere Argumente angegeben, wird eine Fehlermeldung generiert und das Programm beendet.  
  
 **-S** [*Protokoll*:]*Server*[ **\\** _instance_name_] [**,**_Port_]  
 Gibt die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz an, mit der eine Verbindung hergestellt wird. Durch die Option wird die `sqlcmd`-Skriptvariable SQLCMDSERVER festgelegt.  
  
 Geben Sie *Servername* an, um eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf diesem Servercomputer herzustellen. Geben Sie *server_name* [ **\\** _instance_name_ ] an, um eine Verbindung mit einer benannten Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf diesem Server Computer herzustellen. Wenn kein Servercomputer angegeben wird, stellt `sqlcmd` eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer her. Diese Option ist erforderlich, wenn Sie `sqlcmd` von einem Remote Computer im Netzwerk ausführen.  
  
 Das *Protokoll* kann `tcp` (TCP/IP), `lpc` (Shared Memory) oder `np` (Named Pipes) sein.  
  
 Wenn Sie beim Starten von keine *server_name* [ **\\** _instance_name_ ] angeben `sqlcmd` , [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sucht nach der SQLCMDSERVER-Umgebungsvariablen und verwendet diese.  
  
> [!NOTE]  
>  Die OSQLSERVER-Umgebungsvariable wurde aus Gründen der Abwärtskompatibilität beibehalten. Die SQLCMDSERVER-Umgebungsvariable hat Vorrang vor der OSQLSERVER-Umgebungsvariablen. Dies bedeutet, dass `sqlcmd` und **osql** ohne Störungen nebeneinander verwendet werden können und dass alte Skripts weiterhin funktionieren.  
  
 **-U** _login_id_  
 Die Benutzeranmelde-ID.  
  
> [!NOTE]  
>  Die OSQLUSER-Umgebungsvariable steht aus Gründen der Abwärtskompatibilität zur Verfügung. Die SQLCMDUSER-Umgebungsvariable ist bezüglich der OSQLUSER-Umgebungsvariable vorrangig. Dies bedeutet, dass `sqlcmd` und **osql** ohne Störungen nebeneinander verwendet werden können. Es bedeutet ferner, dass vorhandene **osql** -Skripts weiterhin funktionieren.  
  
 Wenn weder die Option **-U** noch die Option **-P** angegeben ist, wird `sqlcmd` von versucht, eine Verbindung mithilfe des Windows- [!INCLUDE[msCoName](../includes/msconame-md.md)] Authentifizierungsmodus herzustellen. Die Authentifizierung basiert auf dem Windows-Konto des Benutzers, der `sqlcmd` ausführt.  
  
 Wird die Option **-U** zusammen mit der Option **-E** verwendet (weiter unten in diesem Thema beschrieben), wird eine Fehlermeldung generiert. Werden nach der Option **-U** mehrere Argumente angegeben, wird eine Fehlermeldung generiert und das Programm beendet.  
  
 **-z** _neues_Kennwort_  
 Kennwort ändern:  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 **-Z** _neues_Kennwort_  
 Kennwort ändern und beenden:  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 **Eingabe-/Ausgabeoptionen**  
  **-f** _Codepage_ | **i:** _Codepage_[ **,o:** _Codepage_] | **o:** _Codepage_[ **,i:** _Codepage_]  
 Gibt die Eingabe- und Ausgabecodepages an. Die Codepagenummer ist ein numerischer Wert, der eine installierte Windows-Codepage angibt.  
  
 Regeln zum Konvertieren von Codepages:  
  
-   Wenn keine Codepages angegeben sind, verwendet `sqlcmd` die aktuelle Codepage sowohl für Eingabe- als auch für Ausgabedateien, außer wenn es sich bei der Eingabedatei um eine Unicode-Datei handelt, da in diesem Fall keine Konvertierung erforderlich ist.  
  
-   `sqlcmd` erkennt Unicode-Eingabedateien des Formats Big-Endian bzw. Little-Endian automatisch. Wenn die Option **-u** angegeben wurde, handelt es sich bei der Ausgabe stets um Unicode-Dateien des Formats Little-Endian.  
  
-   Wenn keine Ausgabedatei angegeben wurde, handelt es sich bei der Ausgabe-Codepage um die Codepage der Konsole. Auf diese Weise wird die Ausgabe richtig auf der Konsole angezeigt.  
  
-   Wenn mehrere Eingabedateien angegeben wurden, wird davon ausgegangen, dass sie dieselbe Codepage verwenden. Unicode- und Nicht-Unicode-Eingabedateien können gemischt verwendet werden.  
  
 Geben Sie an der Eingabeaufforderung `chcp` ein, um die Codepage von Cmd.exe zu überprüfen.  
  
 **-i** _input_file_[**,**_input_file2_...]  
 Identifiziert die Datei, die einen Batch mit SQL-Anweisungen oder gespeicherten Prozeduren enthält. Sie können mehrere Dateien angeben, die der Reihe nach gelesen und verarbeitet werden. Verwenden Sie keine Leerzeichen zwischen Dateinamen. `sqlcmd` prüft zunächst, ob alle angegebenen Dateien vorhanden sind. Wenn eine oder mehrere Dateien nicht vorhanden sind, wird `sqlcmd` beendet. Die Optionen -i und -Q/-q schließen sich gegenseitig aus.  
  
 Beispiele für Pfade:  
  
 **-i** C: \\<Dateiname\>  
  
 **-i** \\ \\<Server \> \\<Freigabe $>\\<Dateiname\>  
  
 **-i** "C:\some Folder \\<Dateiname \> "  
  
 Dateipfade, die Leerzeichen enthalten, müssen in Anführungszeichen eingeschlossen werden.  
  
 Diese Option kann mehrmals verwendet werden: **-i**_input_file_ **-i**_input_file._  
  
 **-o** _Ausgabedatei_  
 Identifiziert die Datei, in die die Ausgabe von `sqlcmd` geschrieben wird.  
  
 Ist **-u** angegeben, wird die *Ausgabedatei* im Unicode-Format gespeichert. Wenn der Dateiname ungültig ist, wird eine Fehlermeldung generiert und `sqlcmd` beendet. `sqlcmd` unterstützt nicht das gleichzeitige Schreiben mehrerer `sqlcmd`-Prozesse in die gleiche Datei. In diesem Fall wäre die Dateiausgabe beschädigt oder fehlerhaft. Weitere Informationen zu Dateiformaten finden Sie in den Erläuterungen zum Schalter **-f** . Falls sie noch nicht vorhanden ist, wird die Datei erstellt. Eine möglicherweise aus einer früheren `sqlcmd`-Sitzung verbliebene Datei wird überschrieben. Bei der hier angegebenen Datei handelt es sich nicht um die **stdout** -Datei. Wenn eine **stdout** -Datei angegeben ist, wird diese Datei nicht verwendet.  
  
 Beispiele für Pfade:  
  
 **-o** C: \\< Dateiname>  
  
 **-o** \\ \\<Server \> \\<Freigabe $>\\<Dateiname\>  
  
 **-o "** C:\ein Ordner \\<Dateiname \> "  
  
 Dateipfade, die Leerzeichen enthalten, müssen in Anführungszeichen eingeschlossen werden.  
  
 **-r**[**0** | **1**]  
 Leitet die Ausgabe der Fehlermeldung auf den Bildschirm um (**stderr**). Wenn Sie keinen Parameter bzw. wenn Sie **0**angeben, werden nur Fehlermeldungen mit dem Schweregrad 11 oder höher umgeleitet. Wenn Sie **1**angeben, wird die gesamte Fehlermeldungsausgabe (einschließlich der Ausgabe von PRINT) umgeleitet. Dies hat keine Wirkung, wenn Sie die Option -o verwenden. Standardmäßig werden Meldungen an **stdout**gesendet.  
  
 **-R**  
 Bewirkt, dass `sqlcmd` die aus abgerufenen numerischen, Währungs-, Datums-und Zeit Spalten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] basierend auf dem Gebiets Schema des Clients lokalisiert werden. Standardmäßig werden diese Spalten entsprechend den regionalen Einstellungen des Servers angezeigt.  
  
 **-u**  
 Gibt an, dass *Ausgabedatei* unabhängig vom Format von *Eingabedatei*im Unicode-Format gespeichert wird.  
  
 **Abfrageausführungsoptionen**  
  **-e**  
 Schreibt Eingabeskripts in das Standardausgabegerät (**stdout**).  
  
 **-I**  
 Legt die SET QUOTED_IDENTIFIER-Verbindungsoption auf ON fest. Die Standardeinstellung ist OFF. Weitere Informationen finden Sie unter [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **-q "** _CmdLine-Abfrage_ **"**  
 Führt eine Abfrage aus, wenn `sqlcmd` startet, beendet `sqlcmd` jedoch nicht, nachdem die Ausführung der Abfrage abgeschlossen ist. Es können mehrere durch Semikolons getrennte Abfragen ausgeführt werden. Schließen Sie die Abfrage in Anführungszeichen ein, wie im folgenden Beispiel gezeigt wird.  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  Verwenden Sie nicht das Abschlusszeichen GO in der Abfrage.  
  
 Wird `-b` zusammen mit dieser Option angegeben, wird `sqlcmd` mit einem Fehler beendet. Der Schalter `-b` wird weiter unten in diesem Thema beschrieben.  
  
 **-Q"** _Befehlszeilenabfrage_ **"**  
 Führt eine Abfrage aus, wenn `sqlcmd` startet, und beendet `sqlcmd` unmittelbar im Anschluss. Es können mehrere durch Semikolons getrennte Abfragen ausgeführt werden.  
  
 Schließen Sie die Abfrage in Anführungszeichen ein, wie im folgenden Beispiel gezeigt wird.  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  Verwenden Sie nicht das Abschlusszeichen GO in der Abfrage.  
  
 Wird `-b` zusammen mit dieser Option angegeben, wird `sqlcmd` mit einem Fehler beendet. Der Schalter `-b` wird weiter unten in diesem Thema beschrieben.  
  
 **-t** _Abfragetimeout_  
 Gibt die Anzahl der Sekunden an, bevor ein Befehl (oder eine SQL-Anweisung) ein Timeout hat. Mit dieser Option wird die- `sqlcmd` Skript Variable sqlcmdstatus Timeout festgelegt. Wenn für *Abfragetimeout* kein Wert angegeben ist, tritt für den Befehl kein Timeout ein. Der Wert für *query**time_out* muss eine Zahl zwischen 1 und 65534 sein. Wenn der angegebene Wert kein numerischer Wert ist oder außerhalb dieses Bereichs liegt, generiert `sqlcmd` eine Fehlermeldung.  
  
> [!NOTE]  
>  Der tatsächliche Timeoutwert kann einige Sekunden von dem für *Timeout* angegebenen Wert abweichen.  
  
 **-vvar =** _Wert_[ **var =** _value_...]  
 Erstellt eine `sqlcmd` Skript Variable, die in einem Skript verwendet werden kann `sqlcmd` . Setzen Sie den Wert in Anführungszeichen, falls er Leerzeichen enthält. Sie können mehrere Werte für **_var_** = **" *`values`* "** angeben. Wenn einer der angegebenen Werte fehlerhaft ist, generiert `sqlcmd` eine Fehlermeldung und wird beendet.  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 **-x**  
 Bewirkt, dass `sqlcmd` Skriptvariablen ignoriert. Dies erweist sich als nützlich, wenn ein Skript mehrere INSERT-Anweisungen enthält, die Zeichenfolgen im selben Format wie reguläre Variablen enthalten können, etwa $(*Variablenname*).  
  
 **Formatierungsoptionen**  
  **-h** _Kopfzeilen_  
 Gibt die Anzahl der Zeilen an, die zwischen den Spaltenüberschriften ausgegeben werden. Standardmäßig werden die Überschriften für jedes Resultset der Abfrage einmal gedruckt. Mit dieser Option wird die- `sqlcmd` Skript Variable sqlcmdheaders festgelegt. Mit **-1** können Sie angeben, dass keine Überschriften ausgegeben werden sollen. Ein ungültiger Wert bewirkt, dass `sqlcmd` eine Fehlermeldung generiert und dann beendet wird.  
  
 **-k** [**1** | **2**]  
 Entfernt alle Steuerzeichen aus der Ausgabe, z. B. Tabstoppzeichen und Neue-Zeile-Zeichen. Hierdurch bleibt die Spaltenformatierung erhalten, wenn Daten zurückgegeben werden. Wenn 1 angegeben wird, werden die Steuerzeichen durch ein einzelnes Leerzeichen ersetzt. Wenn 2 angegeben wird, werden aufeinanderfolgende Steuerzeichen durch ein einzelnes Leerzeichen ersetzt. **-k** ist der Gleiche wie **-k1**.  
  
 **-s** _Spaltentrennzeichen_  
 Gibt das Spaltentrennzeichen an. Der Standardwert ist ein Leerzeichen. Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDCOLSEP festgelegt. Um Zeichen verwenden zu können, die für das Betriebssystem eine besondere Bedeutung haben, z. B. das kaufmännische Und-Zeichen (&) oder das Semikolon (;), müssen Sie das Zeichen in Anführungszeichen (") einschließen. Das Spaltentrennzeichen kann ein beliebiges 8-Bit-Zeichen sein.  
  
 **-w** _Spaltenbreite_  
 Gibt die Bildschirmbreite für die Ausgabe an. Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDCOLWIDTH festgelegt. Die Spaltenbreite muss eine Zahl größer als 8 und kleiner als 65536 sein. Wenn die angegebene Spaltenbreite außerhalb dieses Bereichs liegt, generiert `sqlcmd` eine Fehlermeldung. Die Standardbreite beträgt 80 Zeichen. Wenn eine Ausgabezeile die angegebene Spaltenbreite überschreitet, wird sie in die nächste Zeile umbrochen.  
  
 **-W**  
 Mit dieser Option werden nachfolgende Leerzeichen aus einer Spalte entfernt. Verwenden Sie diese Option zusammen mit der Option **-s** , um Daten vorzubereiten, die in eine andere Anwendung exportiert werden sollen. Diese Option kann nicht mit der Option **-y** oder **-Y** verwendet werden.  
  
 **-y** _Anzeigebreite_bei_Typen_mit_variabler_Länge_  
 Legt die `sqlcmd`-Skriptvariable SQLCMDMAXVARTYPEWIDTH fest. Der Standardwert ist 256. Sie begrenzt die Anzahl der Zeichen, die für die großen Datentypen variabler Länge zurückgegeben werden:  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  UDTs können je nach Implementierung eine feste Länge aufweisen. Wenn die Länge eines UDT mit fester Länge den Wert für *Anzeigebreite*unterschreitet, hat dies keinen Einfluss auf den Wert des zurückgegebenen UDT. Wenn die Länge den Wert für *Anzeigebreite*jedoch überschreitet, wird die Ausgabe abgeschnitten.  
  
 
> [!IMPORTANT]  
>  Verwenden Sie die Option **-y 0** mit äußerster Sorgfalt, da sie je nach Größe der zurückgegebenen Daten zu ernsthaften Leistungsproblemen auf dem Server und im Netzwerk führen kann.  
  
 **-Y** _Anzeigebreite_bei_Typen_mit_fester_Länge_  
 Legt die `sqlcmd`-Skriptvariable SQLCMDMAXFIXEDTYPEWIDTH fest. Der Standardwert ist 0 (unbegrenzt). Er begrenzt die Anzahl der zurückgegebenen Zeichen für die folgenden Datentypen:  
  
-   `char(`*n* `)` , wobei 1<= n<= 8000  
  
-   `nchar(n`*n* `)` , wobei 1<= n<= 4000  
  
-   `varchar(n`*n* `)` , wobei 1<= n<= 8000  
  
-   `nvarchar(n`*n* `)` , wobei 1<= n<= 4000  
  
-   `varbinary(n`*n* `)` , wobei 1<= n<= 4000  
  
-   `variant`  
  
 **Optionen für die Fehlerberichterstellung**  
  `-b`  
 Gibt an, dass `sqlcmd` beendet und ein DOS ERRORLEVEL-Wert zurückgegeben wird, wenn ein Fehler auftritt. Für die DOS ERRORLEVEL-Variable wird der Wert **1** zurückgegeben, wenn der Schweregrad der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Fehlermeldung größer als 10 ist. Andernfalls wird der Wert **0** zurückgegeben. Wenn die Option `-V` zusätzlich zu `-b` festgelegt wurde, meldet `sqlcmd` keinen Fehler, wenn der Schweregrad kleiner ist als die mithilfe von `-V` festgelegten Werte. Mit Eingabeaufforderungs-Batchdateien kann der Wert von ERRORLEVEL getestet und der Fehler entsprechend behoben werden. `sqlcmd` meldet keine Fehler für Schweregrad 10 (Informationsmeldungen).  
  
 Wenn das `sqlcmd`-Skript einen falschen Kommentar bzw. einen Syntaxfehler enthält oder eine Skriptvariable fehlt, wird der ERRORLEVEL-Wert 1 zurückgegeben.  
  
 **-m** _Fehlerebene_  
 Steuert, welche Fehlermeldungen an **stdout**gesendet werden. Fehlermeldungen mit einem Schweregrad, der größer oder gleich diesem Wert ist, werden gesendet. Wenn dieser Wert auf **-1**festgelegt ist, werden alle Meldungen gesendet, einschließlich der Informationsmeldungen. Es sind keine Leerzeichen zwischen **-m** und **-1**zulässig. Beispielsweise ist **-m-1** gültig, **-m -1** jedoch nicht.  
  
 Mit dieser Option wird außerdem die `sqlcmd`-Skriptvariable SQLCMDERRORLEVEL festgelegt. Diese Variable hat den Standardwert 0.  
  
 `-V`*error_severity_level*  
 Steuert den Schweregrad, der zur Festlegung der ERRORLEVEL-Variable verwendet wird. Für Fehlermeldungen mit einem Schweregrad, der größer oder gleich diesem Wert ist, wird ERRORLEVEL festgelegt. Werte kleiner 0 werden als 0 zurückgegeben. Batch- und CMD-Dateien können verwendet werden, um den Wert der ERRORLEVEL-Variable zu testen.  
  
 **Sonstige Optionen**  
  **-a** _Paketgröße_  
 Fordert ein Paket einer anderen Größe an. Durch diese Option wird die `sqlcmd`-Skriptvariable SQLCMDPACKETSIZE festgelegt. *packet_size* muss einen Wert zwischen 512 und 32767 haben. Der Standardwert lautet 4096. Ein höherer Wert für die Paketgröße kann das Leistungsverhalten beim Ausführen von Skripts verbessern, die zahlreiche SQL-Anweisungen zwischen GO-Befehlen aufweisen. Sie können eine größere Paketgröße anfordern. Wird die Anforderung jedoch verweigert, verwendet `sqlcmd` die Standardeinstellung des Servers für die Paketgröße.  
  
 **-c** _Batchterminator_  
 Gibt das Batchabschlusszeichen an. Standardmäßig werden Befehle abgeschlossen und an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gesendet, indem das Wort „GO“ in eine eigene Zeile eingegeben wird. Wenn Sie das Batchabschlusszeichen neu festlegen, dürfen Sie keine für [!INCLUDE[tsql](../includes/tsql-md.md)] reservierten Schlüsselwörter oder Zeichen verwenden, die eine spezielle Bedeutung für das Betriebssystem haben, und zwar auch dann nicht, wenn vor dem Wort bzw. Zeichen ein umgekehrter Schrägstrich steht.  
  
 **-L**[**c**]  
 Listet die lokal konfigurierten Servercomputer sowie die Namen der Servercomputer auf, die Broadcastnachrichten über das Netzwerk senden. Dieser Parameter kann nicht in Verbindung mit anderen Parametern verwendet werden. Es können maximal 3.000 Servercomputer aufgelistet werden. Wenn die Serverliste aufgrund der Puffergröße abgeschnitten wurde, wird eine Warnmeldung angezeigt.  
  
> [!NOTE]  
>  Aufgrund der Beschaffenheit des Broadcastings in Netzwerken ist es möglich, dass `sqlcmd` nicht von allen Servern rechtzeitig eine Antwort empfängt. Daher kann die Liste der zurückgegebenen Server mit jedem Aufruf dieser Option variieren.  
  
 Wenn der optionale Parameter **c** angegeben wird, wird die Ausgabe ohne die Kopfzeile Server: angezeigt, und jede Server Zeile wird ohne führende Leerzeichen aufgelistet. Dies wird als einfache Ausgabe bezeichnet. Durch die einfache Ausgabe wird die Verarbeitungsleistung von Skriptsprachen verbessert.  
  
 **-p**[**1**]  
 Gibt Leistungsstatistiken für jedes Resultset aus. Folgende Ausgabe ist ein Beispiel für das Format von Leistungsstatistiken:  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 Hierbei gilt:  
  
 `x` = Anzahl von Transaktionen, die von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verarbeitet werden.  
  
 `t1` = Gesamtdauer aller Transaktionen.  
  
 `t2` = Durchschnittliche Dauer einer einzelnen Transaktion.  
  
 `t3` = Durchschnittliche Anzahl von Transaktionen pro Sekunde.  
  
 Alle Zeitangaben erfolgen in Millisekunden.  
  
 Wird der optionale Parameter **1** angegeben, wird die Statistik im durch Doppelpunkte getrennten Format ausgegeben, das problemlos in eine Kalkulationstabelle importiert oder von einem Skript verarbeitet werden kann.  
  
 Wenn der optionale Parameter ein anderer Wert als **1**ist, wird ein Fehler generiert und `sqlcmd` beendet.  
  
 `-X`[**1**]  
 Deaktiviert Befehle, die die Systemsicherheit gefährden können, wenn `sqlcmd` von einer Batchdatei aus ausgeführt wird. Die deaktivierten Befehle werden weiterhin erkannt; `sqlcmd` gibt eine Warnmeldung aus und setzt die Ausführung fort. Wenn der optionale Parameter **1** angegeben wird, `sqlcmd` generiert eine Fehlermeldung und wird dann beendet. Die folgenden Befehle werden deaktiviert, wenn die Option `-X` verwendet wird:  
  
-   **ED**  
  
-   **!!** _command_  
  
 Die Angabe der Option `-X` verhindert, dass Umgebungsvariablen an `sqlcmd` übergeben werden. Sie verhindert darüber hinaus die Ausführung des Startskripts, das mithilfe der SQLCMDINI-Skriptvariablen angegeben wurde. Weitere Informationen zu `sqlcmd` Skript Variablen finden Sie unter [Verwenden von sqlcmd mit Skript Variablen](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 **-?**  
 Zeigt eine Syntaxzusammenfassung der `sqlcmd`-Optionen an.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Optionen müssen nicht in der Reihenfolge verwendet werden, in der sie im Abschnitt zur Syntax gezeigt wurden.  
  
 Wenn mehrere Ergebnisse zurückgegeben werden, gibt `sqlcmd` eine Leerzeile zwischen den einzelnen Resultsets in einem Batch aus. Außerdem wird die Meldung " \<x> betroffene Zeilen" nicht angezeigt, wenn Sie für die ausgeführte Anweisung nicht gilt.  
  
 Wenn Sie `sqlcmd` interaktiv verwenden möchten, geben Sie `sqlcmd` an der Eingabeaufforderung mit einer oder mehreren der zuvor in diesem Thema beschriebenen Optionen ein. Weitere Informationen finden Sie unter [Verwenden des Hilfsprogramms „sqlcmd“](../relational-databases/scripting/sqlcmd-use-the-utility.md).  
  
> [!NOTE]  
>  Die Optionen **-L**, **-Q**, **-Z** oder **-i** bewirken `sqlcmd` , dass Sie nach der Ausführung beendet werden.  
  
 Die gesamte Länge der `sqlcmd`-Befehlszeile in der Befehlsumgebung (Cmd.exe) einschließlich aller Argumente und erweiterten Variablen entspricht der Länge, die im Betriebssystem für Cmd.exe bestimmt wurde.  
  
## <a name="variable-precedence-low-to-high"></a>Rangfolge der Variablen (vom niedrigsten bis zum höchsten Rang)  
  
1.  Umgebungsvariablen auf Systemebene  
  
2.  Umgebungsvariablen auf Benutzerebene  
  
3.  An der Eingabeaufforderung festgelegte Befehlsshell (**Set** X = Y) vor der Ausführung `sqlcmd` .  
  
4.  **sqlcmd-v** X=Y  
  
5.  **:Setvar** X Y  
  
> [!NOTE]  
>  Öffnen Sie die **Systemsteuerung**, klicken Sie auf **System**und anschließend auf die Registerkarte **Erweitert** , um die Umgebungsvariablen anzuzeigen.  
  
## <a name="sqlcmd-scripting-variables"></a>sqlcmd-Skriptvariablen  
  
|Variable|Damit verbundene Schalter|R/W|Standard|  
|--------------|--------------------|----------|-------------|  
|SQLCMDUSER|-U|R|""|  
|SQLCMDPASSWORD|-P|--|""|  
|SQLCMDSERVER|-S|R|"DefaultLocalInstance"|  
|SQLCMDWORKSTATION|-H|R|"ComputerName"|  
|SQLCMDDBNAME|-d|R|""|  
|SQLCMDLOGINTIMEOUT|-l|R/W|"8" (Sekunden)|  
|SQLCMDSTATTIMEOUT|-t|R/W|"0" = unbegrenzt warten|  
|SQLCMDHEADERS|-H|R/W|"0"|  
|SQLCMDCOLSEP|-S|R/W|" "|  
|SQLCMDCOLWIDTH|-w|R/W|"0"|  
|SQLCMDPACKETSIZE|-a|R|"4096"|  
|SQLCMDERRORLEVEL|-M|R/W|0|  
|SQLCMDMAXVARTYPEWIDTH|-y|R/W|"256"|  
|SQLCMDMAXFIXEDTYPEWIDTH|-y|R/W|"0" = unbegrenzt|  
|SQLCMDEDITOR||R/W|"edit.com"|  
|SQLCMDINI||R|""|  
  
 SQLCMDUSER, SQLCMDPASSWORD und SQLCMDSERVER werden festgelegt, wenn **:Connect**  
  
 verwendet wird.  
  
 Durch R wird angezeigt, dass der Wert nur einmal während der Programminitialisierung festgelegt werden kann.  
  
 Durch R/W wird angezeigt, dass der Wert mithilfe des **setvar** -Befehls geändert werden kann und auf nachfolgende Befehle der neue Wert angewendet wird.  
  
## <a name="sqlcmd-commands"></a>sqlcmd-Befehle  
 Zusätzlich zu [!INCLUDE[tsql](../includes/tsql-md.md)] den-Anweisungen in `sqlcmd` sind auch die folgenden Befehle verfügbar:  
  
|||  
|-|-|  
|**GO** [*Anzahl*]|**:List**|  
|[ **:** ] **RESET**|**:Error**|  
|[ **:** ] **ED**|**:Out**|  
|[**:**] **!!**|**:Perftrace**|  
|[ **:** ] **QUIT**|**:Connect**|  
|[ **:** ] **EXIT**|**:On Error**|  
|**:r**|**:Help**|  
|**:ServerList**|**:XML** [**ON** &#124; **OFF**]|  
|**:Setvar**|**:Listvar**|  
  
 Beachten Sie bei der Verwendung von `sqlcmd`-Befehlen Folgendes:  
  
-   Mit Ausnahme von GO muss vor allen `sqlcmd`-Befehlen ein Doppelpunkt (:) angegeben werden.  
  
    > [!IMPORTANT]  
    >  Aus Gründen der Abwärtskompatibilität mit bestehenden **osql** -Skripts werden einige der Befehle auch ohne Angabe des Doppelpunkts erkannt. Dies wird durch [**:**] gekennzeichnet.  
  
-   `sqlcmd`-Befehle werden nur erkannt, wenn sie am Anfang einer Zeile stehen.  
  
-   Bei keinem `sqlcmd`-Befehl wird die Groß- und Kleinschreibung beachtet.  
  
-   Jeder Befehl muss in einer eigenen Zeile stehen. Auf einen Befehl darf keine [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung oder ein anderer Befehl folgen.  
  
-   Die Befehle werden sofort ausgeführt. Sie werden nicht wie [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen in den Ausführungspuffer gestellt.  
  
 **Bearbeitungsbefehle**  
  [ **:** ] **ED**  
 Startet den Text-Editor. Mit diesem Editor kann der aktuelle [!INCLUDE[tsql](../includes/tsql-md.md)]-Batch oder der zuletzt ausgeführte Batch bearbeitet werden. Um den zuletzt ausgeführten Batch zu bearbeiten, muss der **ED** -Befehl unmittelbar nach Abschluss der Ausführung des letzten Batches eingegeben werden.  
  
 Der Text-Editor wird durch die SQLCMDEDITOR-Umgebungsvariable definiert. Der Standardeditor ist 'Edit'. Sie können den Editor ändern, indem Sie die SQLCMDEDITOR-Umgebungsvariable festlegen. Wenn Sie beispielsweise den [!INCLUDE[msCoName](../includes/msconame-md.md)]-Editor als Editor festlegen möchten, müssen Sie Folgendes eingeben:  
  
 `SET SQLCMDEDITOR=notepad`  
  
 [ **:** ] **RESET**  
 Löscht den Anweisungscache.  
  
 **:List**  
 Gibt den Inhalt des Anweisungscaches aus.  
  
 **Variablen**  
  **: Setvar** \<**var**> [ **"*`value`*"** ]  
 Definiert `sqlcmd`-Skriptvariablen. Skriptvariablen haben das folgende Format: `$(VARNAME)`.  
  
 Bei Variablennamen wird die Groß- und Kleinschreibung nicht beachtet.  
  
 Skriptvariablen können folgendermaßen festgelegt werden:  
  
-   Implizit – mithilfe einer Befehlszeilenoption. Beispielsweise wird mit der Option **-l** die SQLCMDLOGINTIMEOUT-Variable festgelegt `sqlcmd` .  
  
-   Explizit – mithilfe des **:Setvar** -Befehls.  
  
-   Durch die Definition einer Umgebungsvariablen vor der Ausführung von `sqlcmd`.  
  
> [!NOTE]  
>  Die Option `-X` verhindert, dass Umgebungsvariablen an `sqlcmd` übergeben werden.  
  
 Wenn eine Variable, die mithilfe von **:Setvar** definiert wurde, denselben Namen wie eine Umgebungsvariable aufweist, ist die mit **:Setvar** definierte Variable vorrangig.  
  
 Variablennamen dürfen keine Leerzeichen enthalten.  
  
 Variablennamen können nicht dieselbe Form wie ein Variablenausdruck, z. B. $(var), haben.  
  
 Wenn der Zeichenfolgenwert der Skriptvariablen Leerzeichen enthält, müssen Sie den Wert in Anführungszeichen einschließen. Wenn für eine Skriptvariable kein Wert angegeben wird, wird die Skriptvariable ausgelassen.  
  
 **:Listvar**  
 Zeigt die Liste der zurzeit festgelegten Skriptvariablen an.  
  
> [!NOTE]  
>  Es werden nur Skript Variablen angezeigt, die von festgelegt werden `sqlcmd` , und diejenigen, die mit dem Befehl **: setvar** festgelegt werden.  
  
 **Ausgabebefehle**  
  **:Error**   
 **_\<_** _filename_  **_>|_ Stderr | STDOUT**  
 Leitet die gesamte Fehlerausgabe in die mit *Dateiname*angegebene Datei, in **stderr** oder in **stdout**um. Der Befehl **Error** kann mehrmals in einem Skript verwendet werden. Die Fehlerausgabe wird standardmäßig an **stderr**gesendet.  
  
 *file name*  
 Erstellt und öffnet eine Datei, in die die Ausgabe geschrieben wird. Wenn die Datei bereits vorhanden ist, wird sie auf 0 Byte gekürzt. Wenn der Zugriff auf die Datei aufgrund unzureichender Berechtigungen oder anderer Ursachen nicht möglich ist, wird die Ausgabe nicht umgeleitet, sondern an das zuletzt angegebene Ziel oder an das Standardziel gesendet.  
  
 **STDERR**  
 Leitet die Fehlerausgabe in den **stderr** -Datenstrom. Wenn dieser Datenstrom umgeleitet wurde, wird die Fehlerausgabe von dem Ziel empfangen, zu dem der Datenstrom umgeleitet wurde.  
  
 **STDOUT**  
 Leitet die Fehlerausgabe in den **stdout** -Datenstrom. Wenn dieser Datenstrom umgeleitet wurde, wird die Fehlerausgabe von dem Ziel empfangen, zu dem der Datenstrom umgeleitet wurde.  
  
 ** \<** _filename_ **> : Ausgehend** |  **Stderr** |  **Stdout**  
 Erstellt und leitet alle Abfrageergebnisse in der bzw. an die durch *Dateiname*angegebene Datei, an **stderr** oder an **stdout**um. Standardmäßig wird die Ausgabe an **stdout**gesendet. Wenn die Datei bereits vorhanden ist, wird sie auf 0 Byte gekürzt. Der Befehl **Out** kann mehrmals in einem Skript verwendet werden.  
  
 **:P ERF- \<** _filename_ **> Ablauf Verfolgung** |  **Stderr** |  **Stdout**  
 Erstellt und leitet alle Informationen zur Leistungsnachverfolgung in der bzw. an die durch *Dateiname*angegebene Datei, an **stderr** oder **stdout**um. Standardmäßig wird die Ausgabe zur Leistungsnachverfolgung an **stdout**gesendet. Wenn die Datei bereits vorhanden ist, wird sie auf 0 Byte gekürzt. Der Befehl **Perftrace** kann mehrmals in einem Skript verwendet werden.  
  
 **Befehle zur Ausführungssteuerung**  
  **: Bei Fehler**[ `exit`  |  `ignore` ]  
 Legt die Aktion fest, die ausgeführt werden soll, wenn ein Fehler während der Skript- oder Batchausführung auftritt.  
  
 Wird die Option `exit` verwendet, wird `sqlcmd` mit dem entsprechenden Fehlerwert beendet.  
  
 Wenn die Option `ignore` verwendet wird, ignoriert `sqlcmd` den Fehler und setzt die Batch- oder Skriptausführung fort. Standardmäßig wird eine Fehlermeldung ausgegeben.  
  
 [ **:** ] **QUIT**  
 Bewirkt, dass `sqlcmd` beendet wird.  
  
 [**:**] **Exit**[ **( *`statement`* )** ]  
 Gibt Ihnen die Möglichkeit, das Ergebnis einer SELECT-Anweisung als Rückgabewert von `sqlcmd` zu verwenden. Wenn numerisch, wird die erste Spalte der letzten Ergebniszeile in eine 4 Byte lange ganze Zahl (Long) konvertiert. MS-DOS übergibt das niedrige Byte an den übergeordneten Prozess oder an die Fehlerebene des Betriebssystems. Windows 200x übergibt die gesamte 4 Bytes lange ganze Zahl. Die Syntax ist:  
  
 `:EXIT(query)`  
  
 Beispiel:  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 Sie können den **EXIT** -Parameter auch als Teil einer Batchdatei einschließen. Geben Sie an der Eingabeaufforderung z. B. Folgendes ein:  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 Das `sqlcmd` Hilfsprogramm sendet alles zwischen den Klammern **()** an den Server. Wenn eine gespeicherte Systemprozedur eine Menge auswählt und einen Wert zurückgibt, wird nur die Auswahl zurückgegeben. Eine EXIT **()** -Anweisung ohne Angabe zwischen den Klammern führt alle im Batch vorhergehenden Anweisungen aus und beendet das Hilfsprogramm dann ohne Rückgabewert.  
  
 Wird eine fehlerhafte Abfrage angegeben, wird `sqlcmd` beendet, ohne dass ein Wert zurückgegeben wird.  
  
 Folgende Liste enthält eine Aufstellung von EXIT-Formaten:  
  
-   :EXIT  
  
 Führt den Batch nicht aus, beendet das Hilfsprogramm sofort und gibt keinen Wert zurück.  
  
-   :EXIT( )  
  
 Führt den Batch aus, beendet dann das Hilfsprogramm und gibt keinen Wert zurück.  
  
-   :EXIT(query)  
  
 Führt den Batch mit der darin enthaltenen Abfrage aus und beendet dann das Hilfsprogramm, nachdem die Ergebnisse der Abfrage zurückgegeben wurden.  
  
 Wenn RAISERROR innerhalb eines `sqlcmd` Skripts verwendet wird und der Status 127 ausgelöst wird, `sqlcmd` wird beendet und die Meldungs-ID an den Client zurückgegeben. Beispiel:  
  
 `RAISERROR(50001, 10, 127)`  
  
 Dieser Fehler bewirkt, dass das `sqlcmd`-Skript beendet und die Meldungs-ID 50001 an den Client zurückgegeben wird.  
  
 Die Rückgabewerte -1 bis -99 sind für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] reserviert; `sqlcmd` definiert die folgenden zusätzlichen Rückgabewerte:  
  
|Rückgabewerte|BESCHREIBUNG|  
|-------------------|-----------------|  
|-100|Vor dem Auswählen des Rückgabewerts ist ein Fehler aufgetreten.|  
|-101|Beim Auswählen eines Rückgabewerts wurden keine Zeilen gefunden.|  
|-102|Beim Auswählen des Rückgabewerts ist ein Konvertierungsfehler aufgetreten.|  
  
 **GO** [*Anzahl*]  
 GO signalisiert sowohl das Ende eines Batches als auch die Ausführung aller zwischengespeicherten [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen. Wenn ein Wert für *Anzahl* angegeben ist, werden die zwischengespeicherten Anweisungen so oft, wie durch *Anzahl* angegeben, in Form eines einzigen Batches ausgeführt.  
  
 **Sonstige Befehle**  
  **: r\<** _filename_ **>**  
 Analysiert zusätzliche [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen und- `sqlcmd` Befehle aus der durch angegebenen Datei **<*`filename`*>** in den Anweisungs Cache.  
  
 Wenn die Datei [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen enthält, die nicht von **GO** gefolgt sind, müssen Sie **GO** in der ersten Zeile nach **:r** eingeben.  
  
> [!NOTE]  
>  **\<** _filename_ **>** wird relativ zum Start Verzeichnis gelesen, in dem `sqlcmd` ausgeführt wurde.  
  
 Die Datei wird gelesen und ausgeführt, nachdem ein Batchabschlusszeichen gefunden wurde. Sie können den Befehl **:r** mehrmals verwenden. Die Datei kann beliebige `sqlcmd`-Befehle enthalten, Dies schließt das Batchabschlusszeichen **GO**ein.  
  
> [!NOTE]  
>  Die im interaktiven Modus angezeigte Zeilenanzahl wird für jeden gefundenen **:r** -Befehl um 1 erhöht. Der **:r** -Befehl wird in der Ausgabe des Listenbefehls angezeigt.  
  
 **:Serverlist**  
 Listet die lokal konfigurierten Server sowie die Namen der Server auf, die Nachrichten über das Netzwerk senden.  
  
 **: Connect** _server_name_[ **\\** _instance_name_] [-l *Timeout*] [-U *user_name* [-P *Kennwort*]]  
 Stellt eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] her. Schließt außerdem die aktuelle Verbindung.  
  
 Timeoutoptionen:  
  
|||  
|-|-|  
|0|unbegrenzte Wartezeit|  
|n>0|Wartezeit beträgt n Sekunden|  
  
 Die SQLCMDSERVER-Skriptvariable spiegelt die zurzeit aktive Verbindung wider.  
  
 Wenn *Timeout* nicht angegeben wird, gilt standardmäßig der Wert der SQLCMDLOGINTIMEOUT-Variablen.  
  
 Wenn nur *Benutzername* angegeben wird (entweder als Option oder als Umgebungsvariable), wird der Benutzer zur Eingabe eines Kennworts aufgefordert. Dies trifft nicht zu, wenn die Umgebungsvariable SQLCMDUSER oder SQLCMDPASSWORD festgelegt wurde. Wenn weder Optionen noch Umgebungsvariablen angegeben werden, wird der Windows-Authentifizierungsmodus für die Anmeldung verwendet. Wenn z. B. mithilfe integrierter Sicherheit eine Verbindung mit der Instanz `instance1` auf dem Computer mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (`myserver`) hergestellt werden soll, würden Sie Folgendes eingeben:  
  
 `:connect myserver\instance1`  
  
 Wenn mithilfe von Skriptvariablen eine Verbindung mit der Standardinstanz auf `myserver` hergestellt werden soll, würden Sie Folgendes eingeben:  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 [**:**] **!!**\< *command*>  
 Führt Betriebssystembefehle aus. Um einen Betriebssystembefehl auszuführen, geben Sie zwei Ausrufezeichen ( **!!** ) gefolgt von dem Betriebssystembefehl in eine neue Zeile ein. Beispiel:  
  
 `:!! Dir`  
  
> [!NOTE]  
>  Der Befehl wird auf dem Computer ausgeführt, auf dem `sqlcmd` ausgeführt wird.  
  
 **:XML** [**ON** | **OFF**]  
 Weitere Informationen finden Sie unter "XML-Ausgabeformat" weiter unten in diesem Thema.  
  
 **:Help**  
 Listet die `sqlcmd`-Befehle zusammen mit einer kurzen Beschreibung jedes Befehls auf.  
  
### <a name="sqlcmd-file-names"></a>sqlcmd-Dateinamen  
 `sqlcmd`Eingabedateien können mit der Option **-i** oder dem Befehl **: r** angegeben werden. Ausgabedateien können mit der Option **-o** oder den Befehlen **:Error**, **:Out** und **:Perftrace** angegeben werden. Es folgen einige Richtlinien für das Verwenden dieser Dateien:  
  
-   **: Error**, **: Out** und **:P ERF-Trace** sollten separate verwenden **<*`filename`*>** . Wenn das gleiche **<*`filename`*>** verwendet wird, können Eingaben aus den Befehlen gemischt werden.  
  
-   Wenn eine Eingabedatei auf einem Remoteserver einen Laufwerksdateipfad wie z. B. :out c:\OutputFile.txt enthält und von `sqlcmd` auf einem lokalen Computer aufgerufen wird, wird die Ausgabedatei auf dem lokalen Computer und nicht auf dem Remoteserver erstellt.  
  
-   Gültige Dateipfade sind: C: \\ **<*`filename`*>** , \\ \\<Server \> \\<Freigabe $>\\ **<*`filename`*>** und "c:\some Folder \\ **<*`file name`*>** ". Verwenden Sie Anführungszeichen, wenn der Pfad ein Leerzeichen enthält.  
  
-   Mit jeder neuen `sqlcmd`-Sitzung werden eventuell schon vorhandene gleichnamige Dateien überschrieben.  
  
### <a name="informational-messages"></a>Informationsmeldungen  
 `sqlcmd` gibt alle vom Server gesendeten Informationsmeldungen aus. Im folgenden Beispiel wird eine Informationsmeldung ausgegeben, nachdem die [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen ausgeführt wurden.  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 Wenn Sie die EINGABETASTE drücken, wird folgende Informationsmeldung ausgegeben: Der Datenbankkontext wurde in "AdventureWorks2012" geändert.  
  
### <a name="output-format-from-transact-sql-queries"></a>Ausgabeformat von Transact-SQL-Abfragen  
 `sqlcmd` gibt zuerst eine Spaltenüberschrift aus, die die in der SELECT-Liste angegebenen Spaltennamen enthält. Die Spaltennamen werden durch das SQLCMDCOLSEP-Zeichen getrennt. Standardmäßig handelt es sich hierbei um ein Leerzeichen. Wenn der Spaltenname kürzer als die Spaltenbreite ist, wird die Ausgabe bis zur nächsten Spalte mit Leerzeichen aufgefüllt.  
  
 Auf diese Zeile folgt eine Trennlinie, die durch eine Reihe von Bindestrichen dargestellt wird. Die folgende Ausgabe zeigt ein Beispiel.  
  
 Starten Sie `sqlcmd`. Geben Sie an der `sqlcmd` Eingabeaufforderung Folgendes ein:  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 Wenn Sie die EINGABETASTE drücken, wird das folgende Resultset zurückgegeben.  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 Obwohl die `BusinessEntityID` -Spalte nur 4 Zeichen breit ist, wurde sie erweitert, um den längeren Spaltennamen aufzunehmen. Standardmäßig wird die Ausgabe mit dem 80. Zeichen beendet. Dies kann geändert werden, indem Sie die Option **-w** verwenden oder die SQLCMDCOLWIDTH-Skriptvariable festlegen.  
  
### <a name="xml-output-format"></a>XML-Ausgabeformat  
 Die XML-Ausgabe, die sich aus der FOR XML-Klausel ergibt, wird unformatiert in einem fortlaufenden Datenstrom ausgegeben.  
  
 Verwenden Sie den Befehl `:XML ON`, wenn Sie eine Ausgabe im XML-Format erwarten.  
  
> [!NOTE]  
>  `sqlcmd` gibt Fehlermeldungen im üblichen Format zurück. Beachten Sie, dass die Fehlermeldungen auch im XML-Textstrom im XML-Format ausgegeben werden. Mit `:XML ON` zeigt `sqlcmd` keine Informationsmeldungen an.  
  
 Verwenden Sie den folgenden Befehl, um den XML-Modus zu deaktivieren: `:XML OFF`.  
  
 Der GO-Befehl sollte nicht verwendet werden, bevor der XML OFF-Befehl ausgegeben wurde, da XML OFF bewirkt, dass `sqlcmd` zur zeilenbasierten Ausgabe zurückkehrt.  
  
 Es ist nicht möglich, XML-Daten (Datenstrom) und Rowsetdaten zu mischen. Wenn der XML ON-Befehl nicht ausgegeben wurde, bevor eine [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisung, die XML-Datenströme ausgibt, ausgeführt wurde, wird die Ausgabe nicht richtig dargestellt. Wenn der XML ON-Befehl ausgegeben wurde, können Sie keine [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen ausführen, die reguläre Rowsets ausgeben.  
  
> [!NOTE]  
>  Der **:XML** -Befehl unterstützt die SET STATISTICS XML-Anweisung nicht.  
  
## <a name="sqlcmd-best-practices"></a>Bewährte Methoden für die Verwendung von sqlcmd  
 Die folgenden Methoden haben sich dazu bewährt, Sicherheit und Effizienz zu optimieren.  
  
-   Verwenden Sie die integrierte Sicherheit von Windows.  
  
-   Verwenden Sie in automatisierten Umgebungen `-X`.  
  
-   Sichern Sie Eingabe- und Ausgabedateien, indem Sie die geeigneten NTFS-Dateisystemberechtigungen verwenden.  
  
-   Führen Sie aus Leistungsgründen möglichst alle Aufgaben in einer einzigen `sqlcmd`-Sitzung, nicht in einer Reihe von verschiedenen Sitzungen durch.  
  
-   Legen Sie für Batch- bzw. Abfragetimeouts Werte fest, die höher sind als die erwartete Ausführungsdauer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten des Hilfsprogramms „sqlcmd“](../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Ausführen von Transact-SQL-Skriptdateien mithilfe von „sqlcmd“](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)   
 [Verwenden des Hilfsprogramms „sqlcmd“](../relational-databases/scripting/sqlcmd-use-the-utility.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)   
 [Herstellen einer Verbindung mit der Datenbank-Engine mithilfe von „sqlcmd“](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)   
 [Bearbeiten von SQLCMD-Skripts mit dem Abfrage-Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)   
 [Verwalten von Auftragsschritten](../ssms/agent/manage-job-steps.md)   
 [Erstellen eines CmdExec-Auftragsschritts](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
