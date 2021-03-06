---
title: Protokollieren und Definieren von Protokolleinträgen in einer Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- logs [Integration Services], custom
- custom log entries [Integration Services]
- custom data flow components [Integration Services], logging
- data flow components [Integration Services], logging
ms.assetid: 2190dba9-59b5-480b-b8e9-21d5a54c5917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14dfec71679bbe455ae8be5face98b776a80b9e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697001"
---
# <a name="logging-and-defining-log-entries-in-a-data-flow-component"></a>Protokollieren und Definieren von Protokolleinträgen in einer Datenflusskomponente
  Benutzerdefinierte Datenflusskomponenten können mithilfe der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.PostLogMessage%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle Nachrichten an einen vorhandenen Protokolleintrag senden. Darüber hinaus können sie auch mithilfe der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>-Methode oder ähnlichen Methoden der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle Informationen für den Benutzer anzeigen. Bei dieser Vorgehensweise entsteht jedoch durch das Auslösen und Behandeln zusätzlicher Ereignisse Arbeitsaufwand, und die Benutzer sind dazu gezwungen, ausführliche Informationsmeldungen zu durchsuchen, um schließlich zu den für sie relevanten Nachrichten zu gelangen. Um für die Benutzer Ihrer Komponente benutzerdefinierte Protokollinformationen mit einer eindeutigen Bezeichnung bereitzustellen, können Sie, wie nachstehend beschrieben, einen benutzerdefinierten Protokolleintrag verwenden.  
  
## <a name="registering-and-using-a-custom-log-entry"></a>Registrieren und Verwenden eines benutzerdefinierten Protokolleintrags  
  
### <a name="registering-a-custom-log-entry"></a>Registrieren eines benutzerdefinierten Protokolleintrags  
 Um einen benutzerdefinierten Protokolleintrag für die Verwendung durch Ihre Komponente zu registrieren, überschreiben Sie die <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterLogEntries%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>-Basisklasse. Im folgenden Beispiel wird ein benutzerdefinierter Protokolleintrag registriert und ein Name sowie eine Beschreibung bereitgestellt.  
  
```csharp  
using Microsoft.SqlServer.Dts.Runtime;  
...  
private const string MyLogEntryName = "My Custom Component Log Entry";  
private const string MyLogEntryDescription = "Log entry from My Custom Component ";  
...  
    public override void RegisterLogEntries()  
    {  
      this.LogEntryInfos.Add(MyLogEntryName,  
        MyLogEntryDescription,  
        Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT);  
    }  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
...  
Private Const MyLogEntryName As String = "My Custom Component Log Entry"   
Private Const MyLogEntryDescription As String = "Log entry from My Custom Component "  
...  
Public  Overrides Sub RegisterLogEntries()   
  Me.LogEntryInfos.Add(MyLogEntryName, _  
    MyLogEntryDescription, _  
    Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT)   
End Sub  
```  
  
 Die <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency>-Enumeration stellt einen Hinweis für die Laufzeit bereit, wie häufig das Ereignis protokolliert wird:  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_OCCASIONAL>: Ereignis wird nur manchmal protokolliert, nicht während jeder Ausführung.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>: Ereignis wird während jeder Ausführung mit konstanter Häufigkeit protokolliert.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_PROPORTIONAL>: Ereignis wird mit einer zur fertiggestellten Menge der Arbeit proportionalen Häufigkeit protokolliert.  
  
 Das oben stehende Beispiel verwendet <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSLogEntryFrequency.DTSLEF_CONSISTENT>, da die Komponente erwartet, jeweils einen Eintrag pro Ausführung zu protokollieren.  
  
 Nach der Registrierung des benutzerdefinierten Protokolleintrags und dem Hinzufügen einer Instanz Ihrer benutzerdefinierten Komponente zur Oberfläche des Datenfluss-Designers zeigt das Dialogfeld **Protokollierung** im Designer einen neuen Protokolleintrag mit dem Namen „My Custom Component Log Entry“ (Protokolleintrag meiner benutzerdefinierten Komponente) in der Liste der verfügbaren Protokolleinträge an.  
  
### <a name="logging-to-a-custom-log-entry"></a>Protokollieren eines benutzerdefinierten Protokolleintrags  
 Nach der Registrierung des benutzerdefinierten Protokolleintrags kann die Komponente jetzt benutzerdefinierte Meldungen protokollieren. Das folgende Beispiel schreibt während der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>-Methode, die den Text einer von der Komponente verwendeten SQL-Anweisung enthält, einen benutzerdefinierten Protokolleintrag.  
  
```csharp  
public override void PreExecute()  
{  
  DateTime now = DateTime.Now;  
  byte[] additionalData = null;  
  this.ComponentMetaData.PostLogMessage(MyLogEntryName,  
    this.ComponentMetaData.Name,  
    "Command Sent was: " + myCommand.CommandText,  
    now, now, 0, ref additionalData);  
}  
```  
  
```vb  
Public  Overrides Sub PreExecute()   
  Dim now As DateTime = DateTime.Now   
  Dim additionalData As Byte() = Nothing   
  Me.ComponentMetaData.PostLogMessage(MyLogEntryName, _  
    Me.ComponentMetaData.Name, _  
    "Command Sent was: " + myCommand.CommandText, _  
    now, now, 0, additionalData)   
End Sub  
```  
  
 Wenn der Benutzer jetzt das Paket nach Auswählen von „My Custom Component Log Entry“ (Protokolleintrag meiner benutzerdefinierten Komponente) im Dialogfeld **Protokollierung** ausführt, dann enthält das Protokoll einen Eintrag, der eindeutig mit „User::My Custom Component Log Entry“ (Benutzer::Protokolleintrag meiner benutzerdefinierten Komponente) gekennzeichnet ist. Dieses neue Protokoll enthält den Text der SQL-Anweisung, den Zeitstempel und alle zusätzlichen Daten, die vom Entwickler protokolliert wurden.  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Protokollierung &#40;SSIS&#41;](../../performance/integration-services-ssis-logging.md)  
  
  
