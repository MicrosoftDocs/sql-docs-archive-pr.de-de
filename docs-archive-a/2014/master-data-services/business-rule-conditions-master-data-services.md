---
title: Geschäftsregelbedingungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d2e0a8c3-4c2e-407c-856e-68d95ebda9ed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 12cd594e978c589f11d71a0dafb357418fad5ef1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621044"
---
# <a name="business-rule-conditions-master-data-services"></a>Geschäftsregelbedingungen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]bestimmen Geschäftsregelbedingungen die Bedingungen, die für eine oder mehrere Aktionen, die ausgeführt werden sollen, den Wert "true" haben müssen.  
  
> [!NOTE]  
>  Bedingungen sind optional. Wenn Sie keine Bedingung angeben, werden immer dann Aktionen ausgeführt, wenn Daten gegen Geschäftsregeln überprüft werden.  
  
## <a name="business-rule-conditions"></a>Geschäftsregelbedingungen  
  
|Bedingungsname|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Ist gleich**|Das ausgewählte Attribut **ist gleich** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Ist nicht gleich**|Das ausgewählte Attribut **ist nicht gleich** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**ist größer als**|Das ausgewählte Attribut **ist größer als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen- und Datumswerte gültig.|  
|**ist größer als oder gleich**|Das ausgewählte Attribut **ist größer als oder gleich** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen- und Datumswerte gültig.|  
|**ist kleiner als**|Das ausgewählte Attribut **ist kleiner als** ein bestimmtes Attribut oder ein bestimmter Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen- und Datumswerte gültig.|  
|**ist kleiner als oder gleich**|Das ausgewählte Attribut **ist kleiner als oder gleich** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text-, Zahlen- und Datumswerte gültig.|  
|**Beginnt mit**|Das ausgewählte Attribut **beginnt mit** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text- und Linkwerte gültig.|  
|**endet mit**|Das ausgewählte Attribut **endet mit** einem bestimmten Attribut oder Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text- und Linkwerte gültig.|  
|**contains**|Das ausgewählte Attribut **enthält** ein bestimmtes Attribut oder einen bestimmten Attributwert bzw. ist leer.<br /><br /> Diese Bedingung ist für Text- und Linkwerte gültig.|  
|**Enthält das Muster**|Das ausgewählte Attribut **enthält das Muster** eines bestimmten Attributs oder Attributwerts bzw. ist leer. Verwenden Sie reguläre Ausdrücke von .NET Framework, um das Muster anzugeben.<br /><br /> Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.<br /><br /> Diese Bedingung ist für Text- und Linkwerte gültig.|  
|**Enthält die Teilmenge**|Das ausgewählte Attribut **enthält die Teilmenge** eines bestimmten Attributs oder Attributwerts. Sie müssen die Startposition für die Suche angeben (1 bedeutet z. B., dass die Suche beim ersten Zeichen beginnt).<br /><br /> Diese Bedingung ist für Text- und Linkwerte gültig.|  
|**hat sich geändert**|Das ausgewählte Attribut **wurde geändert** , seit das letzte Mal Geschäftsregeln auf das Element angewendet wurden. Sie müssen die Änderungsgruppe angeben, zu der das Attribut gehört.<br /><br /> Weitere Informationen zu Änderungsnachverfolgungsgruppen finden Sie unter [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md).<br /><br /> Diese Bedingung ist für Text-, Zahlen-, Datums- und Linkwerte gültig.|  
|**Liegt zwischen**|Das ausgewählte Attribut **liegt zwischen** zwei bestimmten Attributwerten.<br /><br /> Diese Bedingung ist für Text-, Zahlen- und Datumswerte gültig.|  
  
> [!NOTE]  
>  Wenn eine Geschäftsregel eine Bedingung enthält, die zwei Werte vergleicht, und die Regel auf ein Element angewendet wird, wofür beide Werte NULL sind, besteht dieses Element keine Überprüfung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geschäftsregel Aktionen &#40;Master Data Services&#41;](../../2014/master-data-services/business-rule-actions-master-data-services.md)   
 [Master Data Services von Geschäftsregeln &#40;&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)  
  
  
