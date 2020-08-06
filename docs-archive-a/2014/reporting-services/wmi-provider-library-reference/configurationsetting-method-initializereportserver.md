---
title: 'InitializeReportServer-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616916"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a>InitializeReportServer-Methode (WMI: MSReportServer_ConfigurationSetting)
  Initialisiert die angegebene Berichtsdienstinstanz  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *InstallationID*  
 Eine Zeichenfolge, mit der der Verschlüsselungsschlüssel verschlüsselt wird, bevor er zurückgegeben wird  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Methode aufgerufen wird, wird der Verschlüsselungsschlüssel, der auf die sicheren Informationen der Berichtsserverdatenbank zugreift, mit dem öffentlichen Schlüssel des Berichtsservers verschlüsselt, der von *InstallationID*angegeben wird.  
  
 Der angegebene öffentliche Schlüssel des Berichtsservers muss zuvor in die Berichtsserver-Datenbank geschrieben worden sein.  
  
 Die *InitializeReportServer* -Methode muss für einen Berichtsserver aufgerufen werden, der bereits Zugriff auf die sicheren Informationen hat, damit der Verschlüsselungsschlüssel entschlüsselt werden kann. Der resultierende verschlüsselte Verschlüsselungsschlüssel wird dann in der Berichtsserver-Datenbank gespeichert.  
  
 Wenn die [IsInitialized](configurationsetting-property-isinitialized.md) -Eigenschaft des Berichts Servers auf festgelegt ist `true` , wenn die InitializeReportServer-Methode aufgerufen wird, gibt die Methode Erfolg zurück, ohne zu versuchen, den Verschlüsselungsschlüssel zu verschlüsseln.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
