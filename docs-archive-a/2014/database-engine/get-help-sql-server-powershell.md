---
title: Aufrufen der SQL Server PowerShell-Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f1d97a3b694eebb924f9e1ff228d4d38da4f45ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701583"
---
# <a name="get-help-sql-server-powershell"></a>Get Help SQL Server PowerShell
  Es stehen mehrere Informationsquellen zur Verwendung des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieters für Windows PowerShell und Cmdlets zur Verfügung. Dazu gehört auch die Hilfe, die in der Windows PowerShell-Umgebung verfügbar ist.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Informationen zu Windows PowerShell finden Sie unter [Erste Schritte mit Windows PowerShell](https://technet.microsoft.com/library/hh857337.aspx).  
  
 Eine Übersicht über die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets und -Anbieter finden Sie unter [SQL Server PowerShell](../powershell/sql-server-powershell.md).  
  
### <a name="help-in-the-windows-powershell-environment"></a>Hilfe in der Windows PowerShell-Umgebung  
 Verwenden Sie das Cmdlet **Get-Help** , um Hilfe in der Windows PowerShell-Umgebung aufzurufen. **Get-Help** stellt grundlegende Hilfe zur Windows PowerShell-Sprache und den verschiedenen in Windows PowerShell verfügbaren Cmdlets und Anbietern bereit.  
  
 Weitere Informationen zur Verwendung von **Get-Help**finden Sie unter [Abrufen von Hilfeinformationen: Get-Help](https://go.microsoft.com/fwlink/?LinkId=102136).  
  
### <a name="sql-server-powershell-provider-help"></a>SQL Server PowerShell-Anbieterhilfe  
 Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Anbieter implementiert mehrere Ordner auf einem virtuellen SQLSERVER-Laufwerk, z. B. die Ordner SQLSERVER:\SQL und SQLSERVER:\DAC. Jeder Ordner ist einem der SQL Server-Verwaltbarkeitsobjektmodelle zugeordnet. Während Sie die jedem Knoten zugeordneten Methoden und Eigenschaften in einem SQL Server-Pfad auflisten können, können Sie dafür keine Hilfe in der PowerShell-Umgebung abrufen. Eine Tabelle mit den Ordnern mit Links zur zugeordneten Referenzdokumentation zur Programmierung finden Sie unter [SQL Server PowerShell-Anbieter](../powershell/sql-server-powershell-provider.md).  
  
### <a name="invoke-sqlcmd-help"></a>Invoke-Sqlcmd-Hilfe  
 Das Cmdlet **Invoke-Sqlcmd** akzeptiert alle Abfragen oder Skriptdateien als Eingabe, die vom **sqlcmd** -Hilfsprogramm ausgeführt werden können. Sie können mit **Get-Help** Informationen zu **Invoke-Sqlcmd** und den zugehörigen Parametern abrufen. **Get-Help** kann jedoch nicht für die **sqlcmd** -Abfragen verwendet werden.  
  
 Die Eingaben *-Query* oder *-QueryFromFile* können Folgendes enthalten:  
  
-   **sqlcmd** -Variablen und -Befehle. Informationen zu diesen Variablen und Befehlen finden Sie unter [sqlcmd (Hilfsprogramm)](../tools/sqlcmd-utility.md)im Abschnitt „Hinweise“.  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen. Weitere Informationen über die [!INCLUDE[tsql](../includes/tsql-md.md)]-Sprache finden Sie unter [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference).  
  
-   XQuery-Anweisungen. Weitere Informationen zu der von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützten XQuery-Sprache finden Sie unter [XQuery-Sprachreferenz &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a>Aufrufen von Hilfe für ein SQL Server-Cmdlet  
 **So erhalten Sie Hilfe zu einem Cmdlet**  
  
-   Führen Sie "Get-Help" aus, und geben Sie dabei den Namen des Cmdlet und die Ebene der Hilfe an, die zurückgegeben werden soll.  
  
### <a name="example-cmdlet-get-help"></a>Beispiel: Cmdlet Get-Help  
 In den folgenden Beispielen werden verschiedene Ebenen der Hilfe für **Invoke-Sqlcmd**zurückgegeben:  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a>Abrufen einer Liste von Anbietern  

### <a name="to-get-a-list-of-active-providers"></a>So rufen Sie eine Liste aktiver Anbieter ab
  
1.  Führen Sie "Get-Help" aus, und geben Sie dabei die Anbieterkategorie an.  
  
 Weitere Informationen darüber, wie Sie in Windows PowerShell Hilfe zu den Anbietern erhalten können, finden Sie unter [Laufwerke und Anbieter](https://go.microsoft.com/fwlink/?LinkId=102137).  
  
### <a name="example-get-a-list-of-providers"></a>Beispiel: Abrufen einer Liste von Anbietern  
 Mit diesem Code wird eine Liste der Anbieter, die gerade in der Windows PowerShell-Sitzung aktiviert sind, zurückgegeben:  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a>Aufrufen von Hilfe zum SQL Server-Anbieter  
 **So rufen Sie Hilfe zum Anbieter auf**  
  
1.  Ausführen von "Get-Help" mit Angabe des Namens "SQLServer"  
  
### <a name="example-get-sql-server-provider-help"></a>Beispiel: Aufrufen von Hilfe zum SQL Server-Anbieter  
 In diesem Beispiel werden grundlegende Informationen zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter zurückgegeben:  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a>Auflisten von Methoden und Eigenschaften  
 **So listen Sie die Methoden und die Eigenschaften für einen Knoten in einem SQL Server-Anbieterpfad auf**  
  
1.  Verweisen Sie mit CD auf einen Knoten im SQL Server-Pfad, oder erstellen Sie einen Variablensatz zu diesem Speicherort.  
  
2.  Führen **Sie das Get-Member** -Cmdlet mit dem-Type-Parameter entweder auf Methoden oder Eigenschaften fest.  
  
### <a name="examples-listing-methods-and-properties"></a>Beispiele: Auflisten von Methoden und Eigenschaften  
 In diesem Beispiel sind die für den Datenbankknoten unterstützten Methoden aufgeführt:  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 In diesem Beispiel werden die Eigenschaften für eine Variable aufgelistet, die auf ein SMO-Tabellenobjekt festgelegt wurde:  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server PowerShell Anbieter](../powershell/sql-server-powershell-provider.md)   
 [Verwenden der Datenbank-Engine-Cmdlets](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
