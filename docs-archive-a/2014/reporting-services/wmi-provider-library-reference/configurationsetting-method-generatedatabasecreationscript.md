---
title: GenerateDatabaseCreationScript-Methode (WMI-MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616918"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a>GenerateDatabaseCreationScript-Methode (WMI: MSReportServer_ConfigurationSetting)
  Generiert ein SQL-Skript, mit dem eine Berichtsserver-Datenbank erstellt werden kann  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Databasename*  
 Eine Zeichenfolge, die den Namen der zu erstellenden Berichtsserver-Datenbank enthält  
  
 *Lcid*  
 Zur Lokalisierung von Rollennamen verwendeter Wert.  
  
 *IsSharePointMode*  
 Gibt an, ob die Datenbank im einheitlichen Modus oder im SharePoint-Modus erstellt werden soll.  
  
> [!IMPORTANT]  
>  Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wird *issharepointmode* = `True` nicht unterstützt, da im SharePoint-Modus [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ein gemeinsamer SharePoint-Dienst ist und nicht vom WMI-Anbieter gesteuert wird. Es wird empfohlen, diesen Parameter immer auf `False` festzulegen.  
  
 *Skript*  
 [out] Eine Zeichenfolge, die das generierte SQL-Skript enthält  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode generiert ein SQL-Skript, mit dem Berichtsserver-Datenbanken für die Version des Berichtsservers erstellt werden, zu dem derzeit eine Verbindung besteht.  
  
 Der im Parameter *DatabaseName* angegebene Wert muss den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benennungskonventionen für Datenbanken entsprechen.  
  
 Die Methode überprüft beim Generieren des Skripts nicht das Vorhandensein der Datenbank.  
  
 Beim Generieren des Skripts überprüft diese Methode nicht, ob die Berichtsserver-Datenbank vorhanden ist.  
  
 Das generierte Skript unterstützt [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
