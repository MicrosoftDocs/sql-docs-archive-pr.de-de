---
title: Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719537"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler
  Zur weiteren Klassifizierung von Ausnahmen gibt [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zusätzliche Fehlerinformationen in der **InnerText**-Eigenschaft der untergeordneten Elemente in der **Detail**-Eigenschaft der SOAP-Ausnahme zurück. Da die **Detail**-Eigenschaft ein **XmlNode**-Objekt ist, können Sie mit folgendem Code auf den inneren Text des untergeordneten **Message**-Elements zugreifen.  
  
 Eine Liste aller verfügbaren untergeordneten Elemente, die in der **Detail**-Eigenschaft enthalten sind, finden Sie unter [Detail-Eigenschaft](../soapexception-class/detail-property.md). Weitere Informationen finden Sie unter "Detail Eigenschaft" in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 Folgende Codezeile gibt den spezifischen Fehlercode wieder, der in der SOAP-Ausnahme zur Konsole zurückgegeben wird. Sie können den Fehlercode auch auswerten und bestimmte Aktionen ausführen.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einführung in die Ausnahmebehandlung in Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException-Klasse](../soapexception-class/reporting-services-soapexception-class.md)   
 [Tabelle für SoapException-Fehler](../soapexception-class/soapexception-errors-table.md)  
  
  
