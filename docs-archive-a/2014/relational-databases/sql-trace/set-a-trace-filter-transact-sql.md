---
title: SetBoolValue-Methode (SqlServiceAdvancedProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0c7142d6f192e94e9850b3c1a8a9481dc15a222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697649"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>SetBoolValue-Methode (SqlServiceAdvancedProperty-Klasse)
  Legt den booleschen Wert einer Eigenschaft fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Booleer Wert*|Ein boleescher Wert, der den Wert der erweiterten Eigenschaft angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Eingenschaftswert muss ein boolescher Wert sein, damit die Eigenschaft auf einen boleeschen Wert festgelegt werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
