---
title: Überprüfung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8de26a7eec2048ee12b661d55c0d374f5230b68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618070"
---
# <a name="validation-master-data-services"></a>Überprüfung (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]werden Daten überprüft, um deren Genauigkeit sicherzustellen. Ein Teil der Überprüfung erfolgt automatisch und ein Teil basiert auf Geschäftsregeln, die von Administratoren erstellt werden.  
  
## <a name="when-data-validation-occurs"></a>Durchführen von Überprüfungen  
 Die Überprüfung tritt zu unterschiedlichen Zeiten auf und wird in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Webanwendung unterschiedlich angezeigt.  
  
|Überprüfungstyp|Standards bestimmt durch|Zeitpunkt des Auftretens|Angezeigt in der MasterData Manager-Webbenutzeroberfläche als|Angezeigt im Add-In für Excel als|Werden Daten im MDS-Repository gespeichert?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Überprüfung anhand Geschäftsregeln|MDS-Administrator|Automatisch beim Hinzufügen oder Bearbeiten von Daten.<br /><br /> Manuell, wenn ein Benutzer Geschäftsregeln anwendet.<br /><br /> Manuell, wenn ein Administrator im Funktionsbereich **Versionsverwaltung** der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung eine Version anhand von Geschäftsregeln überprüft.|Überprüfungsfehler|ValidationStatus|Ja|  
|Datentyp und Inhaltsüberprüfung|MDS-Administrator beim Erstellen von Modellobjekten (z. B. Länge oder Datentyp eines Attributs)|Automatisch beim Hinzufügen oder Bearbeiten von Daten|Eingabefehler|InputStatus|Nein|  
|Datentyp und Inhaltsüberprüfung|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automatisch beim Hinzufügen oder Bearbeiten von Daten|Eingabefehler|InputStatus|Nein|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie Geschäftsregeln zum Überprüfen von Daten, und veröffentlichen Sie sie.|[Erstellen und Veröffentlichen einer Geschäftsregel &#40;Master Data Services&#41;](create-and-publish-a-business-rule-master-data-services.md)|  
|Überprüfen Sie eine Version der Daten anhand von Geschäftsregeln. Nur Administratoren.|[Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Überprüfen Sie bestimmte Teilmengen der Daten anhand von Geschäftsregeln. Alle Benutzer mit Zugriffsberechtigung auf den Funktionsbereich **Explorer** .|[Überprüfen von bestimmten Elementen auf Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Überprüfen Sie bestimmte Teilmengen der Daten anhand von Geschäftsregeln. Alle Benutzer mit der Zugriffsberechtigung auf den Funktionsbereich **Explorer** und die mit [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]arbeiten.|[Anwenden von Geschäftsregeln &#40;MDS-Add-In für Excel&#41;](microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
