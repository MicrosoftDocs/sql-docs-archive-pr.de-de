---
title: Erstellen einer Formatdatei (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], creating
ms.assetid: f680b4a0-630f-4052-9c79-d348c1076f7b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca9c85bfcac3380ce13ba89fff6de0b5daadbece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607760"
---
# <a name="create-a-format-file-sql-server"></a>Erstellen einer Formatdatei (SQL Server)
  Beim Massenimportieren bzw. -exportieren von Daten in eine bzw. aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle können Sie eine Formatdatei für ein flexibles System für das Schreiben von Datendateien verwenden, bei denen nur geringfügige oder keine Bearbeitung erforderlich ist, um sie mit anderen Datenformaten oder für das Lesen von Datendateien aus anderen Softwareprogrammen kompatibel zu machen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt zwei Typen von Formatdateien: Nicht-XML- und XML-Formatdateien. Nicht-XML ist das ursprüngliche Format, das von früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt wird.  
  
 Im Allgemeinen sind XML-Formatdateien und Nicht-XML-Formatdateien austauschbar. Es empfiehlt sich jedoch, für neue Formatdateien die XML-Syntax zu verwenden, weil sich im Vergleich zu Nicht-XML-Formatdateien mehrere Vorteile ergeben.  
  
> [!NOTE]  
>  Die zum Lesen der Formatdatei verwendete Version des Hilfsprogramms **bcp** (Bcp.exe) muss mit der Version, mit der die Formatdatei erstellt wurde, identisch oder eine höhere Version sein. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] **Bcp** kann z. b. eine Format Datei der Version 10,0 lesen, die von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] **bcp**generiert wird [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] . **bcp** kann jedoch eine Format Datei der Version 11,0, die von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] **bcp**generiert wird, nicht lesen.  
  
 In diesem Thema wird die Verwendung des [Hilfsprogramms bcp](../../tools/bcp-utility.md) zum Erstellen einer Formatdatei für eine bestimmte Tabelle erläutert. Die Formatdatei basiert auf der angegebenen Datentypoption ( **-n**, **-c**, **-w**oder **-N**) sowie auf den Tabellen- bzw. Sichttrennzeichen.  
  
## <a name="creating-a-non-xml-format-file"></a>Erstellen einer Nicht-XML-Formatdatei  
 Geben Sie bei der Ausführung eines **bcp** -Befehls zum Erstellen einer Formatdatei das **format** -Argument an, und verwenden Sie **nul** anstatt eines Datendateipfads. Die **format** -Option erfordert außerdem die **-f** -Option, z.B.:  
  
 **bcp** _table_or_view_ **format** nul **-f**_format_file_name_  
  
> [!NOTE]  
>  Um Nicht-XML-Formatdateien klar zu kennzeichnen, empfiehlt es sich, als Dateierweiterung FMT zu verwenden, beispielsweise "MeineTabelle.fmt".  
  
 Informationen zu Struktur und Feldern von Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)unterstützt wird.  
  
### <a name="examples"></a>Beispiele  
 Dieser Abschnitt enthält die folgenden Beispiele, die die Verwendung der **bcp** -Befehle zum Erstellen von Nicht-XML-Formatdateien erläutern.  
  
-   A. Erstellen einer Nicht-XML-Formatdatei für systemeigene Daten  
  
-   B. Erstellen einer Nicht-XML-Formatdatei für Zeichendaten  
  
-   C. Erstellen einer Nicht-XML-Formatdatei für systemeigene Unicode-Daten  
  
-   D: Erstellen einer Nicht-XML-Formatdatei für Unicode-Zeichendaten  
  
 In diesen Beispielen wird die `HumanResources.Department` -Tabelle der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank verwendet. Die `HumanResources.Department` -Tabelle enthält vier Spalten: `DepartmentID`, `Name`, `GroupName`und `ModifiedDate`.  
  
#### <a name="a-creating-a-non-xml-format-file-for-native-data"></a>A. Erstellen einer Nicht-XML-Formatdatei für systemeigene Daten  
 In diesem Beispiel wird eine XML-Formatdatei, `Department-n.xml`, für die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` -Tabelle erstellt. Die Formatdatei verwendet systemeigene Datentypen. Der Inhalt der generierten Formatdatei wird nach dem Befehl angezeigt.  
  
 Der Befehl **bcp** enthält die folgenden Qualifizierer.  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**formatnul-f** _format_file_|Gibt die Nicht-XML-Formatdatei an.|  
|**-n**|Gibt systemeigene Datentypen an.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Geben Sie an der Windows-Eingabeaufforderung den folgenden `bcp` -Befehl ein:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -n -f Department-n.fmt  
```  
  
 Die generierte Formatdatei `Department-n.fmt`enthält die folgenden Informationen:  
  
```  
12.0  
4  
1       SQLSMALLINT   0       2       ""   1     DepartmentID                 ""  
2       SQLNCHAR      2       100     ""   2     Name                         SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     GroupName                    SQL_Latin1_General_CP1_CI_AS  
4       SQLDATETIME   0       8       ""   4     ModifiedDate                 ""  
```  
  
 Weitere Informationen finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)unterstützt wird.  
  
#### <a name="b-creating-a-non-xml-format-file-for-character-data"></a>B. Erstellen einer Nicht-XML-Formatdatei für Zeichendaten  
 In diesem Beispiel wird eine XML-Formatdatei, `Department.fmt`, für die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` -Tabelle erstellt. Die Formatdatei verwendet Zeichendatenformate und ein nicht standardmäßiges Feldabschlusszeichen (`,`). Der Inhalt der generierten Formatdatei wird nach dem Befehl angezeigt.  
  
 Der Befehl **bcp** enthält die folgenden Qualifizierer.  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**formatnul-f** _format_file_|Gibt eine Nicht-XML-Formatdatei an.|  
|**-c**|Gibt Zeichendaten an.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Geben Sie an der Windows-Eingabeaufforderung den folgenden `bcp` -Befehl ein:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -c -f Department-c.fmt -T  
```  
  
 Die generierte Formatdatei `Department-c.fmt`enthält die folgenden Informationen:  
  
```  
12.0  
4  
1       SQLCHAR       0       7       "\t"     1     DepartmentID                 ""  
2       SQLCHAR       0       100     "\t"     2     Name                         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     "\t"     3     GroupName                    SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       24      "\r\n"   4     ModifiedDate                 ""  
```  
  
 Weitere Informationen finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)unterstützt wird.  
  
#### <a name="c-creating-a-non-xml-format-file-for-unicode-native-data"></a>C. Erstellen einer Nicht-XML-Formatdatei für systemeigene Unicode-Daten  
 Verwenden Sie zum Erstellen einer Nicht-XML-Formatdatei für systemeigene Unicode-Daten für die `HumanResources.Department`-Tabelle den folgenden Befehl:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -N -f Department-n.fmt  
```  
  
 Weitere Informationen zur Verwendung von nativen Unicode-Daten finden Sie unter [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
#### <a name="d-creating-a-non-xml-format-file-for-unicode-character-data"></a>D: Erstellen einer Nicht-XML-Formatdatei für Unicode-Zeichendaten  
 Verwenden Sie zum Erstellen einer Nicht-XML-Formatdatei für Unicode-Zeichendaten für die `HumanResources.Department`-Tabelle den folgenden Befehl:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -T -w -f Department-w.fmt  
```  
  
 Weitere Informationen zur Verwendung von Unicode-Zeichendaten finden Sie unter [Verwenden des Unicode-Zeichenformats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
## <a name="creating-an-xml-format-file"></a>Erstellen einer XML-Formatdatei  
 Geben Sie bei der Ausführung eines **bcp** -Befehls zum Erstellen einer Formatdatei das **format** -Argument an, und verwenden Sie **nul** anstatt eines Datendateipfads. Für die Option **format** ist immer auch die Option **-f** erforderlich. Zum Erstellen einer XML-Formatdatei muss zudem die Option **-x** angegeben werden, wie im Folgenden dargestellt:  
  
 **bcp** _table_or_view_ **format nul-f** _format_file_name_ **-x**  
  
> [!NOTE]  
>  Um eine XML-Formatdatei klar zu kennzeichnen, empfiehlt es sich, die Dateierweiterung XML zu verwenden, beispielsweise "MeineTabelle.xml".  
  
 Informationen zu Struktur und Feldern von XML-Formatdateien finden Sie unter [XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)unterstützt wird.  
  
### <a name="examples"></a>Beispiele  
 Dieser Abschnitt enthält die folgenden Beispiele, die die Verwendung der **bcp** -Befehle zum Erstellen von XML-Formatdateien erläutern.  
  
-   A. Erstellen einer XML-Formatdatei für Zeichendaten  
  
-   B. Erstellen einer XML-Formatdatei für systemeigene Daten  
  
 In diesen Beispielen wird die `HumanResources.Department` -Tabelle der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank verwendet. Die `HumanResources.Department` -Tabelle enthält vier Spalten: `DepartmentID`, `Name`, `GroupName`und `ModifiedDate`.  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBdesc](../../includes/sssampledbdesc-md.md)]  
  
#### <a name="a-creating-an-xml-format-file-for-character-data"></a>A. Erstellen einer XML-Formatdatei für Zeichendaten  
 In diesem Beispiel wird eine XML-Formatdatei, `Department.xml`, für die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]`HumanResources.Department` -Tabelle erstellt. Die Formatdatei verwendet Zeichendatenformate und ein nicht standardmäßiges Feldabschlusszeichen (`,`). Der Inhalt der generierten Formatdatei wird nach dem Befehl angezeigt.  
  
 Der Befehl **bcp** enthält die folgenden Qualifizierer.  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**formatnul-f** _format_file_ **-x**|Gibt die XML-Formatdatei an.|  
|**-c**|Gibt Zeichendaten an.|  
|**-t** `,`|Gibt ein Komma ( **,** ) als Feldabschlusszeichen an.<br /><br /> Hinweis: Wenn von der Datendatei das Standardfeldabschlusszeichen (`\t`) verwendet wird, ist der **-t**-Schalter nicht erforderlich.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Geben Sie an der Windows-Eingabeaufforderung den folgenden `bcp` -Befehl ein:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -c -x -f Department-c..xml -t, -T  
```  
  
 Die generierte Formatdatei, `Department-c.xml`, enthält die folgenden XML-Elemente:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="24"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="DepartmentID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="GroupName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="ModifiedDate" xsi:type="SQLDATETIME"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Informationen zur Syntax dieser Formatdatei finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md). Informationen zu Zeichendaten finden Sie unter [Verwenden des Zeichenformats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md).  
  
#### <a name="b-creating-an-xml-format-file-for-native-data"></a>B. Erstellen einer XML-Formatdatei für systemeigene Daten  
 In diesem Beispiel wird eine XML-Formatdatei, `Department-n.xml`, für die `HumanResources.Department` -Tabelle erstellt. Die Formatdatei verwendet systemeigene Datentypen. Der Inhalt der generierten Formatdatei wird nach dem Befehl angezeigt.  
  
 Der Befehl **bcp** enthält die folgenden Qualifizierer.  
  
|Qualifizierer|BESCHREIBUNG|  
|----------------|-----------------|  
|**formatnul-f** _format_file_ **-x**|Gibt die XML-Formatdatei an.|  
|**-n**|Gibt systemeigene Datentypen an.|  
|**-T**|Gibt an, dass das Hilfsprogramm **bcp** die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe integrierter Sicherheit über eine vertrauenswürdige Verbindung herstellt. Wenn **-T** nicht angegeben wird, müssen Sie **-U** und **-P** angeben, um sich erfolgreich anzumelden.|  
  
 Geben Sie an der Windows-Eingabeaufforderung den folgenden `bcp` -Befehl ein:  
  
```  
bcp AdventureWorks2012.HumanResources.Department format nul -x -f Department-n..xml -n -T  
```  
  
 Die generierte Formatdatei, `Department-n.xml`, enthält die folgenden XML-Elemente:  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativeFixed" LENGTH="2"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NativeFixed" LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="DepartmentID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="GroupName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="ModifiedDate" xsi:type="SQLDATETIME"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Informationen zur Syntax dieser Formatdatei finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md). Informationen zur Verwendung nativer Daten finden Sie unter [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md).  
  
## <a name="mapping-data-fields-to-table-columns"></a>Zuordnen von Datenfeldern zu Tabellenspalten  
 In einer mit **bcp**erstellten Formatdatei werden alle Tabellenspalten in ihrer Reihenfolge beschrieben. Sie können die Formatdatei ändern, um Tabellenzeilen neu anzuordnen oder auszulassen. Auf diese Weise können Sie Formatdateien an Datendateien anpassen, deren Felder nicht direkt Tabellenspalten zugeordnet werden können. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [Verwenden einer Formatdatei zum Zuordnen von Tabellenspalten zu Datendateifeldern &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)   
 [Überspringen einer Tabellenspalte mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Auslassen eines Datenfelds mithilfe einer Formatdatei &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)   
 [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md)  
  
  
