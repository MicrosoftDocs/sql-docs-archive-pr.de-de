---
title: Erstellen einer Bibliothek für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c14ed699e94c7d8ed0f6f3d727e9ba6e355b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726710"
---
# <a name="creating-a-data-processing-extension-library"></a>Erstellen einer Bibliothek für Datenverarbeitungserweiterungen
  Jede von Ihnen erstellte [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung sollte einen eindeutigen Namespace erhalten und in eine Bibliothek oder Assemblydatei integriert werden. Der exakte Name des Namespace ist unerheblich, er muss jedoch eindeutig sein und darf nicht zusammen mit einer anderen Erweiterung verwendet werden. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] verwendet den Namespace <xref:Microsoft.ReportingServices.DataProcessing> für die Datenverarbeitungserweiterungen, die mit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geliefert werden. Sie sollten eigene eindeutige Namespaces für die Datenverarbeitungserweiterungen Ihres Unternehmens erstellen.  
  
 Folgendes Beispiel zeigt den Code, mit dem Sie eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung beginnen sollten, die Namespaces verwendet, welche die Datenverarbeitungsschnittstellen und jegliche Hilfsprogrammklassen enthalten.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 Wenn Sie eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung kompilieren, müssen Sie für den Compiler einen Verweis auf Microsoft.ReportingServices.Interfaces.dll angeben, da die Schnittstellen der Datenverarbeitungserweiterungen sich dort befinden. Der <xref:Microsoft.ReportingServices.DataProcessing>-Namespace wird für die Implementierung der Datenverarbeitungsschnittstellen benötigt, und der <xref:Microsoft.ReportingServices.Interfaces>-Namespace wird für die Implementierung der <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstelle benötigt. Beispiel: Wenn alle Dateien, die den Code für die Implementierung einer in C# geschriebenen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung enthalten, sich in einem Verzeichnis mit der Erweiterung .cs befänden, würde folgender Befehl von diesem Verzeichnis ausgegeben, um die in CompanyName.ExtensionName.dll gespeicherten Dateien zu kompilieren.  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 Im folgenden Codebeispiel wird der Befehl angezeigt, der für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]-Dateien mit der Erweiterung „.vb“ verwendet werden würde.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  Sie können die Datenverarbeitungserweiterung auch mit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] entwerfen, entwickeln und erstellen. Weitere Informationen zum Entwickeln von Assemblys in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] finden Sie in der Dokumentation zu [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
