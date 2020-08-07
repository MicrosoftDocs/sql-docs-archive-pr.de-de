---
title: IP-Adress Einschränkung erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700629"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>IP-Adresseinschränkung erkannt (Upgrade Advisor)
  Der Upgrade Advisor hat mindestens eine IP-Adresseinschränkung auf der IIS-Website gefunden, die den Berichtsserver bzw. die virtuellen Verzeichnisse des Berichts-Managers hostet. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt keine systeminterne Unterstützung für IP-Adresseinschränkungen bereit.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheimischen.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Das Setup kann keine IP-Adresseinschränkungen für URLs definieren, die für einen aktualisierten Berichtsserver erstellt wurden. Das Upgrade kann fortgesetzt werden, jedoch werden keine IP-Adresseinschränkungen für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-URLs definiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach dem Upgrade ISA Server, Ihre Firewallsoftware oder eine andere Lösung, um Anforderungen spezifischer IP-Adressen an den Berichtsserver zuzulassen oder abzuweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
