---
title: Client Zertifikate auf der Berichts Server-Website (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 5ecce26b-99df-4109-8e51-d150d369dff7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 563a64e695ef552a712a5678f56d38fdfbff619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617507"
---
# <a name="client-certificates-on-the-report-server-web-site-upgrade-advisor"></a>Clientzertifikate auf der Berichtsserver-Website (Upgrade Advisor)
  Der Upgrade Advisor hat ein oder mehrere Clientzertifikate auf der IIS-Website gefunden, die die virtuellen Verzeichnisse des Berichtsservers oder des Berichts-Managers hostet.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]die Verwendung von Client Zertifikaten zum Authentifizieren von Benutzern wird von nicht unterstützt. Das Upgrade kann fortgesetzt werden, jedoch werden vom aktualisierten Berichtsserver keine Clientzertifikate verwendet.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Sie müssen eine separate Lösung verwenden, wie beispielsweise ISA Server, damit die Anforderungen für die Authentifizierung mit Clientzertifikaten erfüllt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
