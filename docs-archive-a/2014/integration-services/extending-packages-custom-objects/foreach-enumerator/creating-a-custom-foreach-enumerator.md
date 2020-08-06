---
title: Erstellen eines benutzerdefinierten Foreach-Enumerators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d99970d466aa53d25a80f0600f1fce7819e94956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615452"
---
# <a name="creating-a-custom-foreach-enumerator"></a>Erstellen eines benutzerdefinierten Foreach-Enumerators
  Die Schritte zum Erstellen eines benutzerdefinierten Foreach-Enumerators ähneln denen jedes anderen benutzerdefinierten Objekts für [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Erstellen Sie eine neue Klasse, die von der Basisklasse erbt. Für einen Foreach-Enumerator ist <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> die Basisklasse.  
  
-   Weisen Sie das Attribut zu, das den Typ des Objekts für die Klasse identifiziert. Für einen Foreach-Enumerator ist <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> das Attribut.  
  
-   Überschreiben Sie die Implementierung der Methoden und Eigenschaften der Basisklasse. Für einen Foreach-Enumerator ist die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>-Methode die wichtigste.  
  
-   Entwickeln Sie optional eine individuelle Benutzeroberfläche. Für einen Foreach-Enumerator ist dazu eine Klasse erforderlich, die die <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI>-Schnittstelle implementiert.  
  
 Ein benutzerdefinierter Enumerator wird vom <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>-Container gehostet. Zur Laufzeit ruft der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>-Container die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>-Methode des benutzerdefinierten Enumerators auf. Der benutzerdefinierte Enumerator gibt ein Objekt zurück, mit dem die `IEnumerable`-Schnittstelle implementiert wird, wie beispielsweise `ArrayList`. <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> führt anschließend eine Iteration über jedes Element in der Auflistung durch, gibt den Wert des aktuellen Elements durch eine benutzerdefinierte Variable an und führt die Ablaufsteuerung im Container aus.  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a>Erste Schritte mit einem benutzerdefinierten ForEach-Enumerator  
  
### <a name="creating-projects-and-classes"></a>Erstellen von Projekten und Klassen  
 Da alle verwalteten Foreach-Enumeratoren von der <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>-Basisklasse abgeleitet sind, besteht der erste Schritt beim Erstellen eines benutzerdefinierten Foreach-Enumerators darin, in Ihrer bevorzugten verwalteten Programmiersprache ein Klassenbibliotheksprojekt anzulegen und eine Klasse zu generieren, die von der Basisklasse erbt. In dieser abgeleiteten Klasse überschreiben Sie die Methoden und Eigenschaften der Basisklasse, um die benutzerdefinierten Funktionen zu implementieren.  
  
 Erstellen Sie in der gleichen Lösung ein zweites Klassenbibliotheksprojekt für die individuelle Benutzeroberfläche. Für eine einfache Bereitstellung sollten Sie eine eigene Assembly für die Benutzeroberfläche verwenden, da Sie so den Foreach-Enumerator oder seine Benutzeroberfläche unabhängig aktualisieren und erneut bereitstellen können.  
  
 Konfigurieren Sie beide Projekte für das Signieren der Assemblys, die bei der Erstellung erzeugt werden, mit einer Schlüsseldatei mit starkem Namen.  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a>Anwenden des DtsForEachEnumerator-Attributs  
 Wenden Sie das <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>-Attribut der Klasse zu, die Sie erstellt haben, um sie als Foreach-Enumerator zu kennzeichnen. Dieses Attribut stellt Entwurfszeitinformationen bereit, z. B. Name und Beschreibung des Foreach-Enumerators. Die- `Name` Eigenschaft wird in der Dropdown Liste der verfügbaren Enumeratoren auf der Registerkarte **Sammlung** des Dialog Felds **foreach-Schleifen-Editor** angezeigt.  
  
 Verwenden Sie die <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A>-Eigenschaft, um den Foreach-Enumerator mit der individuellen Benutzeroberfläche zu verknüpfen. Um das für diese Eigenschaft erforderliche öffentliche Schlüsseltoken zu erhalten, können Sie **sn.exe -t** verwenden. Damit zeigen Sie das öffentliche Schlüsseltoken aus der Schlüsselpaardatei (.snk) an, die Sie für das Signieren der Benutzeroberflächenassembly verwenden möchten.  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a>Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Enumerators  
 Die Schritte zum Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Foreach-Enumerators in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ähneln denen für andere Arten benutzerdefinierter Objekte stark. Weitere Informationen finden Sie unter [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) (Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten).  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Codieren eines benutzerdefinierten Foreach-Enumerators](coding-a-custom-foreach-enumerator.md)   
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
