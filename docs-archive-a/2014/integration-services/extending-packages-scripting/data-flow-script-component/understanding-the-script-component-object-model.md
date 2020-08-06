---
title: Grundlegendes zum Skript-Komponentenobjektmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a11556b00efc5749e8ddb895712d6c61f2459d8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617191"
---
# <a name="understanding-the-script-component-object-model"></a>Grundlegendes zum Skript-Komponentenobjektmodell
  Wie unter [codieren und Debuggen der Skript Komponente] beschrieben (.. /Extending-Packages-Scripting/Data-Flow-Script-Component/Coding-and-Debugging-the-Script-Component.MD, das Skript Komponenten Projekt enthält drei Projekt Elemente:

1.  Das `ScriptMain`-Element, das die `ScriptMain`-Klasse enthält, in die Sie den Code schreiben. Die `ScriptMain`-Klasse erbt von der `UserComponent`-Klasse.

2.  Das `ComponentWrapper`-Element, das die `UserComponent`-Klasse enthält, eine Instanz von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, die die Methoden und Eigenschaften enthält, die Sie verwenden, um Daten zu verarbeiten und mit dem Paket zu interagieren. Das `ComponentWrapper`-Element enthält auch `Connections`- und `Variables`-Auflistungsklassen.

3.  Das `BufferWrapper`-Element, das Klassen enthält, das von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> für jede Eingabe und Ausgabe und typisierte Eigenschaften für jede Spalte erbt.

 Beim Schreiben des Codes in das `ScriptMain`-Element verwenden Sie die in diesem Thema besprochenen Objekte, Methoden und Eigenschaften. Es werden nicht von jeder Komponente alle hier aufgeführten Methoden verwendet. Wenn sie jedoch verwendet werden, geschieht dies in der gezeigten Reihenfolge.

 Die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Basisklasse enthält keinen Implementierungscode für die in diesem Thema erläuterten Methoden. Es ist daher unnötig, aber ungefährlich, Ihrer eigenen Implementierung der Methode einen Aufruf der Basisklassenimplementierung hinzuzufügen.

 Informationen darüber, wie die Methoden und Eigenschaften dieser Klassen in einem bestimmten Skriptkomponententyp zu verwenden sind, finden Sie unter [Additional Script Component Examples (Zusätzliche Skriptkomponentenbeispiele)](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Die Beispielthemen enthalten auch vollständige Codebeispiele.

## <a name="acquireconnections-method"></a>‚AcquireConnections’-Methode
 Quellen und Ziele müssen im Allgemeinen eine Verbindung mit einer externen Datenquelle herstellen. Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Basisklasse, um die Verbindung oder die Verbindungsinformationen von dem entsprechenden Verbindungs-Manager abzurufen.

 Im folgenden Beispiel wird `System.Data.SqlClient.SqlConnection` von einem ADO.NET-Verbindungs-Manager zurückgegeben.

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 Das folgende Beispiel gibt einen vollständigen Pfad- und Dateinamen von einem Verbindungs-Manager für Flatfiles zurück und öffnet anschließend die Datei mithilfe von `System.IO.StreamReader`.

```vb
Private textReader As StreamReader
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    Dim connMgr As IDTSConnectionManager100 = _
        Me.Connections.MyFlatFileSrcConnectionManager
    Dim exportedAddressFile As String = _
        CType(connMgr.AcquireConnection(Nothing), String)
    textReader = New StreamReader(exportedAddressFile)

End Sub
```

## <a name="preexecute-method"></a>‚PreExecute’-Methode
 Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Basisklasse immer dann, wenn Sie eine Verarbeitung nur einmal durchführen müssen, bevor Sie die Verarbeitung einer Datenzeile starten. In einem Ziel können Sie beispielsweise den parametrisierten Befehl, den das Ziel verwendet, so konfigurieren, dass jede Datenzeile in die Datenquelle eingefügt wird.

```vb
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter
...
    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub
```

```csharp
SqlConnection sqlConn; 
SqlCommand sqlCmd; 
SqlParameter sqlParam; 

public override void PreExecute() 
{ 

    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn); 
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int); 
    sqlCmd.Parameters.Add(sqlParam); 
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30); 
    sqlCmd.Parameters.Add(sqlParam); 

}
```

## <a name="processing-inputs-and-outputs"></a>Verarbeiten von Eingaben und Ausgaben

### <a name="processing-inputs"></a>Verarbeiten von Eingaben
 Skriptkomponenten, die als Transformationen oder Ziele konfiguriert sind, weisen eine Eingabe auf.

#### <a name="what-the-bufferwrapper-project-item-provides"></a>Bereitstellungen durch das ‚BufferWrapper’-Projektelement
 Für jede von Ihnen konfigurierte Eingabe enthält das `BufferWrapper`-Projektelement eine Klasse, die von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> abgeleitet ist und denselben Namen hat wie die Eingabe. Jede Eingabepufferklasse enthält die folgenden Eigenschaften, Funktionen und Methoden:

-   Benannte, typisierte Accessoreigenschaften für jede ausgewählte Eingabespalte. Diese Eigenschaften sind schreibgeschützt oder weisen Lese-/Schreibzugriff auf, abhängig von dem für die Spalte auf der Seite **Eingabespalten** des Dialogfelds **Transformations-Editor für Skripterstellung** angegebenen **Verwendungstyp**.

-   Eine **\<column>_IsNull**-Eigenschaft für jede ausgewählte Eingabespalte. Diese Eigenschaft ist ebenfalls schreibgeschützt oder weist Lese-/Schreibzugriff auf, abhängig von dem für die Spalte angegebenen **Verwendungstyp**.

-   Eine **DirectRowTo\<outputbuffer>** -Methode für jede konfigurierte Ausgabe. Sie verwenden diese Methoden beim Filtern von Zeilen in eine von mehreren Ausgaben in derselben `ExclusionGroup`.

-   Eine `NextRow`-Funktion, um die nächste Eingabezeile abzurufen, und eine `EndOfRowset`-Funktion, um zu bestimmen, ob der letzte Datenpuffer verarbeitet wurde. Normalerweise benötigen Sie diese Funktionen nicht, wenn Sie die in der `UserComponent`-Basisklasse implementierten Eingabeverarbeitungsmethoden verwenden. Im nächsten Abschnitt finden Sie weitere Informationen über die `UserComponent`-Basisklasse.

#### <a name="what-the-componentwrapper-project-item-provides"></a>Bereitstellungen durch das ‚ComponentWrapper’-Projektelement
 Das ComponentWrapper-Projektelement enthält eine Klasse mit dem Namen `UserComponent`, die von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> abgeleitet wird. Die `ScriptMain`-Klasse, in die Sie Ihren benutzerdefinierten Code schreiben, wird wiederum von `UserComponent` abgeleitet. Die `UserComponent`-Klasse enthält die folgenden Methoden:

-   Eine überschriebene Implementierung der `ProcessInput`-Methode. Diese Methode wird von der Datenfluss-Engine zur Laufzeit direkt im Anschluss an die `PreExecute`-Methode (und u. U. mehrfach) aufgerufen. `ProcessInput`übergibt die Verarbeitung an die ** \<inputbuffer> _ProcessInput** -Methode. Anschließend sucht die `ProcessInput`-Methode nach dem Ende des Eingabepuffers. Wenn das Ende des Puffers erreicht wurde, ruft sie die überschreibbare `FinishOutputs`-Methode und die private `MarkOutputsAsFinished`-Methode auf. Die `MarkOutputsAsFinished`-Methode ruft dann beim letzten Ausgabepuffer `SetEndOfRowset` auf.

-   Eine überschreibbare Implementierung der **\<inputbuffer>_ProcessInput**-Methode. Diese Standardimplementierung durchläuft jede Eingabezeile einmal und ruft **\<inputbuffer>_ProcessInputRow** auf.

-   Eine überschreibbare Implementierung der **\<inputbuffer>_ProcessInputRow**-Methode. Der Standardimplementierung ist leer. Dies ist die Methode, die Sie normalerweise überschreiben, um den benutzerdefinierten Datenverarbeitungscode zu schreiben.

#### <a name="what-your-custom-code-should-do"></a>Schritte, die der benutzerdefinierte Code ausführen sollte
 Sie können mithilfe der folgenden Methoden Eingaben in die `ScriptMain`-Klasse verarbeiten:

-   Überschreiben Sie **\<inputbuffer>_ProcessInputRow**, um die Daten in jeder Eingabezeile beim Durchlaufen zu verarbeiten.

-   Überschreiben Sie **\<inputbuffer>_ProcessInput** nur dann, wenn Sie beim Durchlaufen der Eingabezeilen noch einen anderen Vorgang ausführen müssen. (Sie müssen z. b. testen, um `EndOfRowset` andere Maßnahmen zu ergreifen, nachdem alle Zeilen verarbeitet wurden.) Ruft ** \<inputbuffer> _ProcessInputRow** auf, um die Zeilen Verarbeitung auszuführen.

-   überschreiben Sie `FinishOutputs`, wenn Sie etwas mit den Ausgaben durchführen müssen, bevor sie geschlossen werden.

 Die `ProcessInput`-Methode stellt sicher, dass diese Methoden zum jeweils richtigen Zeitpunkt aufgerufen werden.

### <a name="processing-outputs"></a>Verarbeiten von Ausgaben
 Skriptkomponenten, die als Quellen oder Transformationen konfiguriert sind, weisen mindestens eine Eingabe auf.

#### <a name="what-the-bufferwrapper-project-item-provides"></a>Bereitstellungen durch das ‚BufferWrapper’-Projektelement
 Für jede von Ihnen konfigurierte Ausgabe enthält das BufferWrapper-Projektelement eine Klasse, die von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> abgeleitet ist und denselben Namen hat wie die Ausgabe. Jede Eingabepufferklasse enthält die folgenden Eigenschaften und Methoden:

-   Benannte, typisierte, lesegeschützte Accessoreigenschaften für jede ausgewählte Ausgabespalte.

-   Eine schreibgeschützte ** \<column> _IsNull** Eigenschaft für jede ausgewählte Ausgabe Spalte, die Sie verwenden können, um den Spaltenwert auf festzulegen `null` .

-   Eine `AddRow`-Methode, um dem Ausgabepuffer eine leere neue Zeile hinzuzufügen.

-   Eine `SetEndOfRowset`-Methode, um der Datenfluss-Engine mitzuteilen, dass keine weiteren Datenpuffer erwartet werden. Außerdem gibt es eine `EndOfRowset`-Funktion, um zu bestimmen, ob der aktuelle Puffer der letzte Datenpuffer ist. Diese Funktionen sind im Allgemeinen nicht erforderlich, wenn Sie die in der Basisklasse implementierten Eingabe Verarbeitungsmethoden verwenden `UserComponent` .

#### <a name="what-the-componentwrapper-project-item-provides"></a>Bereitstellungen durch das ‚ComponentWrapper’-Projektelement
 Das ComponentWrapper-Projektelement enthält eine Klasse mit dem Namen `UserComponent`, die von <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> abgeleitet wird. Die `ScriptMain`-Klasse, in die Sie Ihren benutzerdefinierten Code schreiben, wird wiederum von `UserComponent` abgeleitet. Die `UserComponent`-Klasse enthält die folgenden Methoden:

-   Eine überschriebene Implementierung der `PrimeOutput`-Methode. Diese Methode wird von der Datenfluss-Engine zur Laufzeit vor `ProcessInput` (und nur einmal) aufgerufen. `PrimeOutput` übergibt die Verarbeitung an die `CreateNewOutputRows`-Methode. Wenn die Komponente eine Quelle ist (d. h. die Komponente weist keine Eingaben auf), ruft `PrimeOutput` anschließend die überschreibbare `FinishOutputs`-Methode und die private `MarkOutputsAsFinished`-Methode auf. Die `MarkOutputsAsFinished`-Methode ruft beim letzten Ausgabepuffer `SetEndOfRowset` auf.

-   Eine überschreibbare Implementierung der `CreateNewOutputRows`-Methode. Der Standardimplementierung ist leer. Dies ist die Methode, die Sie normalerweise überschreiben, um den benutzerdefinierten Datenverarbeitungscode zu schreiben.

#### <a name="what-your-custom-code-should-do"></a>Schritte, die der benutzerdefinierte Code ausführen sollte
 Sie können mithilfe der folgenden Methoden Ausgaben in der `ScriptMain`-Klasse verarbeiten:

-   Überschreiben Sie `CreateNewOutputRows` nur, wenn Sie Ausgabezeilen vor der Verarbeitung der Eingabezeilen hinzufügen und füllen können. Sie können beispielsweise `CreateNewOutputRows` in einer Quelle verwenden. In einer Transformation mit asynchronen Ausgaben sollten Sie jedoch `AddRow` während oder nach der Verarbeitung der Eingabedaten aufrufen.

-   überschreiben Sie `FinishOutputs`, wenn Sie etwas mit den Ausgaben durchführen müssen, bevor sie geschlossen werden.

 Die `PrimeOutput`-Methode stellt sicher, dass diese Methoden zum jeweils richtigen Zeitpunkt aufgerufen werden.

## <a name="postexecute-method"></a>‚PostExecute’-Methode
 Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Basisklasse immer dann, wenn Sie eine Verarbeitung nur einmal durchführen müssen, nachdem Sie die Datenzeilen verarbeitet haben. In einer Quelle können Sie beispielsweise den von Ihnen zum Laden von Daten in den Datenfluss verwendeten `System.Data.SqlClient.SqlDataReader` schließen.

> [!IMPORTANT]
>  Die Auflistung von `ReadWriteVariables` ist nur in der `PostExecute`-Methode verfügbar. Sie können daher den Wert einer Paketvariablen nicht direkt inkrementieren, während Sie jede Datenzeile verarbeiten. Erhöhen Sie stattdessen den Wert einer lokalen Variablen, und legen Sie den Wert der Paket Variablen auf den Wert der lokalen Variablen in der-Methode fest, `PostExecute` nachdem alle Daten verarbeitet wurden.

## <a name="releaseconnections-method"></a>‚ReleaseConnections’-Methode
 Quellen und Ziele müssen generell eine Verbindung mit einer externen Datenquelle herstellen. Überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Basisklasse, um die vorher in der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>-Methode geöffnete Verbindung zu schließen und freizugeben.

```vb
    Dim connMgr As IDTSConnectionManager100
...
    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub
```

```csharp
IDTSConnectionManager100 connMgr;

public override void ReleaseConnections()
{

    connMgr.ReleaseConnection(sqlConn);

}
```

![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [Konfigurieren der Skript Komponente im Skript Komponenten-Editor](configuring-the-script-component-in-the-script-component-editor.md) [codieren und Debuggen der Skript Komponente] (.. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md


