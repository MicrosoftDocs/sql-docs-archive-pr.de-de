---
title: Anzeigen von Fehlern, die während des Stagingprozesses auftreten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3b39d039b29090f3021c764126ebb782ce25cbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699878"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>Anzeigen von Fehlern, die während des Stagingprozesses auftreten (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie Fehler anzeigen, die während des Stagingprozesses auftreten. In der Datenbank [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] gibt es zwei Sichten, die Fehler anzeigen:  
  
-   stg.viw_name_MemberErrorDetails für Blatt- oder konsolidierte Elementupdates.  
  
-   stg.viw_name_RelationshipErrorDetails für Hierarchiebeziehungsupdates.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   In der Datenbank [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] müssen Sie entweder für stg.viw_name_MemberErrorDetails oder stg.viw_name_RelationshipErrorDetails über SELECT-Berechtigungen verfügen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>So zeigen Sie bereitstellende Fehler an  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
2.  Öffnen Sie eine neue Abfrage.  
  
3.  Geben Sie den folgenden Text ein, und ersetzen Sie den Namen durch den Namen der Stagingtabelle, z. B. viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Führen Sie die Abfrage aus. Fehlerdetails werden im **ErrorDescription** -Feld angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zu Fehlermeldungen finden Sie unter [Fehler des Stagingprozesses &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Problembehandlung des Stagingprozesses (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
