---
title: Clustered-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Clustered Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fdc87bb7b691580f7efd5ccd7b333d88a3aa78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696557"
---
# <a name="clustered-property-sqlservice-class"></a>Clustered-Eigenschaft (SqlService-Klasse)
  Ruft den booleschen Eigenschaftswert ab, der angibt, ob der Dienst Teil einer gruppierten Instanz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.Clustered [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob der Dienst Teil einer gruppierten Instanz ist: `true`, wenn der Dienst Teil einer gruppierten Instanz ist, bzw. `false`, wenn der Dienst nicht Teil einer gruppierten Instanz ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
