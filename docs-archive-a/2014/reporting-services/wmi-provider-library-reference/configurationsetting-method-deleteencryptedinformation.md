---
title: 'DeleteEncryptedInformation-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d00dc3e90816cd04c84f124cdc3d25a9ac122bba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616927"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserver_configurationsetting"></a>DeleteEncryptedInformation-Methode (WMI: MSReportServer_ConfigurationSetting)
  Löscht die verschlüsselten Informationen aus der Berichtsserver-Datenbank  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Methode aufgerufen wird, werden die folgenden Daten gelöscht:  
  
-   Datenquellinformationen, die verschlüsselt werden, einschließlich des Benutzernamens und des Kennworts  
  
-   Abonnementdaten, die mithilfe der Schnittstellen der Übermittlungserweiterung verschlüsselt werden  
  
-   Alle Informationen aus der Schlüsseltabelle der Berichtsserver-Datenbank  
  
 Nach dem Aufruf dieser Methode muss der Benutzer jeden Computer initialisieren, auf dem die Berichtsserver-Datenbank verwendet wird.  
  
 Der Aufruf der „DeleteEncryptedInformation“-Methode hat keinen Einfluss auf die Berichtsserver-Konfigurationsdatei.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
