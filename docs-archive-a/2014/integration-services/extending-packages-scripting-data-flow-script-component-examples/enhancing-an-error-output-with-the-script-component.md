---
title: Erweitern einer Fehlerausgabe mit der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18637aa1e147ce989645ae859681929f4d0c438a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622225"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Erweitern einer Fehlerausgabe mit der Skriptkomponente
  Standardmäßig enthalten die beiden zusätzlichen Spalten in einer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlerausgabe (ErrorCode und ErrorColumn) nur numerische Codes, die eine Fehlernummer darstellen, und die ID der Spalte, in der der Fehler auftrat. Diese numerischen Werte sind ohne die entsprechende Fehlerbeschreibung nur von begrenztem Nutzen.  
  
 In diesem Thema wird beschrieben, wie Sie mithilfe der Skriptkomponente den im Datenfluss vorhandenen Fehlerausgabedaten eine Spalte zur Fehlerbeschreibung hinzufügen. Im Beispiel wird die Fehlerbeschreibung einem bestimmten vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercode hinzugefügt. Dazu wird die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle verwendet, die von der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>-Eigenschaft der Skriptkomponente bereitgestellt wird.  
  
> [!NOTE]  
>  Wenn Sie eine Komponente erstellen möchten, die Sie einfacher in mehreren Datenflusstasks und Paketen wiederverwenden können, empfiehlt es sich, den Code in diesem Skriptkomponentenbeispiel als Ausgangspunkt für eine benutzerdefinierte Datenflusskomponente zu verwenden. Weitere Informationen finden Sie unter [Entwickeln einer benutzerdefinierten Datenflusskomponente](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie mit einer Skriptkomponente, die als Transformation konfiguriert ist, den im Datenfluss vorhandenen Fehlerausgabedaten eine Spalte zur Fehlerbeschreibung hinzugefügt wird.  
  
 Weitere Informationen zum Konfigurieren der Skript Komponente für die Verwendung als Transformation im Datenfluss finden Sie unter [Erstellen einer synchronen Transformation mit der Skript Komponente](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)und [Erstellen einer asynchronen Transformation mit der Skript Komponente](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>So konfigurieren Sie dieses Skriptkomponentenbeispiel  
  
1.  Konfigurieren Sie vor dem Erstellen der neuen Skriptkomponente eine Upstreamkomponente im Datenfluss, um Zeilen zur zugehörigen Fehlerausgabe umzuleiten, sobald ein Fehler auftritt oder Daten abgeschnitten werden. Zu Testzwecken sollten Sie eine Komponente so konfigurieren, dass auf jeden Fall Fehler auftreten, beispielsweise, indem Sie eine Transformation zum Suchen zwischen zwei Tabellen konfigurieren, und die Suche einen Fehler meldet.  
  
2.  Fügen Sie der Datenfluss-Designeroberfläche eine neue Skriptkomponente hinzu, und konfigurieren Sie sie als Transformation.  
  
3.  Verbinden Sie die Fehlerausgabe der Upstreamkomponente mit der neuen Skriptkomponente.  
  
4.  Öffnen Sie den **Transformations-Editor für Skripterstellung**, und wählen Sie auf der Seite **Skript** für die **ScriptLanguage**-Eigenschaft die Skriptsprache aus.  
  
5.  Klicken Sie auf **Skript bearbeiten**, um die IDE der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Tools for Applications (VSTA) zu öffnen und den unten dargestellten Beispielcode einzufügen.  
  
6.  Schließen Sie VSTA.  
  
7.  Wählen Sie im Transformations-Editor für Skripterstellung auf der Seite **Eingabe Spalten** die Spalte ErrorCode aus.  
  
8.  Fügen Sie auf der Seite **Eingaben und Ausgaben** eine neue Ausgabe Spalte des Typs mit dem `String` Namen **ErrorDescription**hinzu. Vergrößern Sie die Standardlänge der neuen Spalte auf 255, damit auch lange Meldungen angezeigt werden können.  
  
9. Schließen Sie den **Transformations-Editor für Skripterstellung**.  
  
10. Fügen Sie die Ausgabe der Skriptkomponente an ein geeignetes Ziel an. Ein Flatfileziel ist die einfachste Möglichkeit zur Konfiguration bei Ad-hoc-Tests.  
  
11. Führen Sie das Paket aus.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehlerbehandlung in Daten](../data-flow/error-handling-in-data.md)   
 [Verwenden von Fehlerausgaben in einer Datenflusskomponente](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Erstellen einer synchronen Transformation mit der Skriptkomponente](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
