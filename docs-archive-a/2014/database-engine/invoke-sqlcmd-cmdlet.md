---
title: Invoke-Sqlcmd-Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b1572b03b5772f35ac68a6b85aeedde43d150c07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698504"
---
# <a name="invoke-sqlcmd-cmdlet"></a>Invoke-Sqlcmd-Cmdlet
  **Invoke-Sqlcmd** ist ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Cmdlet, das Skripts ausführt, die Anweisungen aus den Sprachen ([!INCLUDE[tsql](../includes/tsql-md.md)] und XQuery) und Befehle enthalten, die vom Hilfsprogramm **sqlcmd** unterstützt werden.  
  
## <a name="using-invoke-sqlcmd"></a>Verwenden von Invoke-Sqlcmd  
 Mit dem **Invoke-Sqlcmd** -Cmdlet können Sie die **sqlcmd** -Skriptdateien in einer Windows PowerShell-Umgebung ausführen. Viele der Vorgänge, die Sie mit **sqlcmd** durchführen können, können auch mit **Invoke-Sqlcmd**durchgeführt werden.  
  
 Dies ist ein Beispiel für den Aufruf von Invoke-Sqlcmd zum Ausführen einer einfachen Abfrage, die dem Festlegen von **sqlcmd** mit den Optionen **-Q** und **-S** ähnelt:  
  
```powershell
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 Dies ist ein Beispiel für den Aufruf von **Invoke-Sqlcmd**, in dem eine Eingabedatei angegeben und die Ausgabe an eine Datei weitergeleitet wird. Dies ähnelt dem Festlegen von **sqlcmd** mit den Optionen **-i** und **-o** :  
  
```powershell
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -FilePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 Dies ist ein Beispiel für die Verwendung eines Windows PowerShell-Arrays zum Übergeben von mehreren **sqlcmd** -Skriptvariablen an **Invoke-Sqlcmd**. Die „$“-Zeichen, die die **sqlcmd** -Skriptvariablen in der SELECT-Anweisung identifizieren, wurden mit dem PowerShell-Escapezeichen „`“ versehen:  
  
```powershell
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 Dies ist ein Beispiel für die Verwendung des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieters für Windows PowerShell zur Navigation zu einer Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]und zur anschließenden Verwendung des Windows PowerShell-Cmdlets **Get-Item** , um das SMO-Serverobjekt für die Instanz abzurufen und es an **Invoke-Sqlcmd**zu übergeben:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 Der Query-Parameter ist ein Positionsparameter und muss nicht benannt werden. Wenn die erste Zeichenfolge, die an **Invoke-Sqlcmd**übergeben wird, nicht benannt ist, wird dieser als Parameter „-Query“ behandelt.  
  
```powershell
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Pfadkontext in Invoke-Sqlcmd  
 Wenn Sie den Database-Parameter nicht verwenden, wird der Datenbankkontext für Invoke-Sqlcmd vom Pfad gesetzt, der aktiv ist, wenn cmdlet aufgerufen wird.  
  
|Pfad|Datenbankkontext|  
|----------|----------------------|  
|Beginnt mit einem anderen Laufwerk als SQLSERVER:|Die Standarddatenbank für die Anmelde-ID in der Standardinstanz auf dem lokalen Computer.|  
|SQLSERVER:\SQL|Die Standarddatenbank für die Anmelde-ID in der Standardinstanz auf dem lokalen Computer.|  
|SQLSERVER:\SQL\ComputerName|Die Standarddatenbank für die Anmelde-ID in der Standardinstanz auf dem angegebenen Computer.|  
|SQLSERVER:\SQL\ComputerName\InstanceName|Die Standarddatenbank für die Anmelde-ID in der angegebenen Instanz auf dem angegebenen Computer.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases|Die Standarddatenbank für die Anmelde-ID in der angegebenen Instanz auf dem angegebenen Computer.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases\DatabaseName|Die angegebene Datenbank in der angegebenen Instanz auf dem angegebenen Computer. Dies gilt auch für längere Pfade, wie z. B. einen Pfad, der den Knoten Tabellen und Spalten innerhalb einer Datenbank angibt.|  
  
 Nehmen wir beispielsweise an, dass die Standarddatenbank für Ihr Windows-Konto in der Standardinstanz auf dem lokalen Computer die master-Datenbank ist. Dann würden die folgenden Befehle master zurückgeben:  
  
```powershell
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Die folgenden Befehle würden [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]zurückgeben:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Invoke-Sqlcmd stellt eine Warnung bereit, wenn es den Pfaddatenbankkontext verwendet. Sie können den SuppressProviderContextWarning-Parameter verwenden, um die Warnmeldung zu deaktivieren. Sie können den IgnoreProviderContext-Parameter verwenden, um Invoke-Sqlcmd anzuweisen, immer die Standarddatenbank für die Anmeldung zu verwenden.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Vergleichen von Invoke-Sqlcmd und dem sqlcmd-Hilfsprogramm  
 Mit**Invoke-Sqlcmd** können zahlreiche der Skripts ausgeführt werden, die auch mit dem **sqlcmd** Hilfsprogramm ausgeführt werden können. **Invoke-Sqlcmd** wird jedoch in einer Windows PowerShell-Umgebung ausgeführt, die sich von der Eingabeaufforderungsumgebung unterscheidet, in der **sqlcmd** ausgeführt wird. Das Verhalten von **Invoke-Sqlcmd** wurde für die Ausführung in einer Windows PowerShell-Umgebung angepasst.  
  
 Nicht alle **sqlcmd** -Befehle sind in **Invoke-Sqlcmd**implementiert. Befehle, die nicht implementiert werden, sind die folgenden: **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**, and **:serverlist**.  
  
 **Invoke-Sqlcmd** initialisiert die **sqlcmd** -Umgebung oder Skriptvariablen wie SQLCMDDBNAME oder SQLCMDWORKSTATION nicht.  
  
 **Invoke-Sqlcmd** zeigt keine Meldungen, wie die Ausgabe von PRINT-Anweisungen, an, außer Sie geben den gängigen Windows PowerShell-Parameter **-Verbose** an. Beispiel:  
  
```powershell
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 Nicht alle **sqlcmd** -Parameter werden in einer PowerShell-Umgebung benötigt. Beispielsweise formatiert Windows PowerShell alle Ausgaben von Cmdlets, sodass die **sqlcmd** -Parameter, die Formatierungsoptionen festlegen, nicht in **Invoke-Sqlcmd**implementiert werden. Die folgende Tabelle zeigt die Beziehung zwischen den **aufrufen-sqlcmd-** Parametern und den **sqlcmd** -Optionen:  
  
|BESCHREIBUNG|sqlcmd-Option|Invoke-Sqlcmd-Parameter|  
|-----------------|-------------------|------------------------------|  
|Server- und Instanzname.|-S|-ServerInstance|  
|Die zu verwendende ursprüngliche Datenbank.|-d|-Database|  
|Die angegebene Abfrage ausführen und dann beenden.|-Q|-Query|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmelde-ID für die Authentifizierung.|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Kennwort für die Authentifizierung.|-P|-Password|  
|Variablendefinition.|-v|-Variable|  
|Abfragetimeoutintervall.|-t|-QueryTimeOut|  
|Ausführung bei Fehler beenden.|-b|-AbortOnError|  
|Dedizierte Administratorverbindung.|-A|-DedicatedAdministratorConnection|  
|Interaktive Befehle, Startskript und Umgebungsvariablen deaktivieren.|-X|-DisableCommands|  
|Variablenersetzung deaktivieren.|-X|-DisableVariables|  
|Minimaler Schweregrad für Bericht.|-v|-SeverityLevel|  
|Minimaler Fehlergrad für Bericht.|-M|-ErrorLevel|  
|Anmeldungstimeoutintervall.|-l|-ConnectionTimeout|  
|Hostname.|-H|-HostName|  
|Kennwort ändern und beenden.|-Z|-NewPassword|  
|Eingabedatei, die eine Abfrage enthält|-i|-InputFile|  
|Maximale Länge der Zeichenausgabe.|-w|-MaxCharLength|  
|Maximale Länge der Binärausgabe.|-w|-MaxBinaryLength|  
|Verbinden mit SSL-Verschlüsselung.|Kein Parameter|-EncryptConnection|  
|Anzeigen von Fehlern|Kein Parameter|-OutputSqlErrors|  
|Meldungen an stderr ausgeben.|-r|Kein Parameter|  
|Regionale Einstellungen des Clients verwenden|-R|Kein Parameter|  
|Die angegebene Abfrage ausführen und mit der Ausführung fortfahren.|-q|Kein Parameter|  
|Codepage zur Verwendung für Ausgabedaten.|-f|Kein Parameter|  
|Ein Kennwort ändern und mit der Ausführung fortfahren|-Z|Kein Parameter|  
|Paketgröße|-a|Kein Parameter|  
|Spaltentrennzeichen|-S|Kein Parameter|  
|Steuern von Ausgabeheadern|-H|Kein Parameter|  
|Angeben von Steuerzeichen|-k|Kein Parameter|  
|Feste Längenanzeigebreite|-y|Kein Parameter|  
|Variable Längenanzeigebreite|-y|Kein Parameter|  
|Eingabe auf dem Bildschirm anzeigen.|-E|Kein Parameter|  
|Bezeichner in Anführungszeichen aktivieren|-I|Kein Parameter|  
|Nachfolgende Leerzeichen löschen.|-w|Kein Parameter|  
|Instanzen auflisten|-l|Kein Parameter|  
|Ausgabe als Unicode formatieren|-U|Kein Parameter|  
|Statistiken drucken|-p|Kein Parameter|  
|Befehlsende|-c|Kein Parameter|  
|Verbindung mithilfe der Windows-Authentifizierung herstellen|-E|Kein Parameter|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden der Datenbank-Engine-Cmdlets](../../2014/database-engine/use-the-database-engine-cmdlets.md)   
 [sqlcmd (Hilfsprogramm)](../tools/sqlcmd-utility.md)   
 [Verwenden des Hilfsprogramms sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
