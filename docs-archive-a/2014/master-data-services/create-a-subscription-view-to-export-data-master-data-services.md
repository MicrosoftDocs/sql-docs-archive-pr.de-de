---
title: Erstellen einer Abonnement Sicht (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619891"
---
# <a name="create-a-subscription-view-master-data-services"></a>Erstellen einer Abonnementsicht (Master Data Services)
  Erstellen Sie eine Abonnement Sicht, wenn Sie eine Sicht Ihrer Daten in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Datenbank für die Verwendung durch Abonnement Systeme erstellen möchten.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die entsprechende Berechtigung für den Zugriff auf den Funktionsbereich **Integrationsmanagement** verfügen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-subscription-view"></a>So erstellen Sie eine Abonnementsicht  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Integrationsmanagement**.  
  
2.  Klicken Sie auf der Menüleiste auf **Sichten erstellen**.  
  
3.  Klicken Sie auf der Seite **Abonnement Sichten** auf **Abonnement Sicht hinzufügen**.  
  
4.  Geben Sie im Bereich **Abonnement Sicht erstellen** im Feld **Name der Abonnement Sicht** einen Namen für die Ansicht ein.  
  
5.  Wählen Sie aus der Liste **Modell** ein Modell aus.  
  
6.  Wählen Sie entweder die Option **Version** oder Versionsflag aus, und wählen Sie dann aus der entsprechenden Liste aus. **Version Flag**  
  
    > [!TIP]  
    >  Erstellen Sie auf Grundlage eines Versionsflags eine Abonnementsicht. Wenn Sie eine Version sperren, können Sie das Flag einer geöffneten Version erneut zuweisen, ohne die Abonnementsicht zu aktualisieren.  
  
7.  Wählen Sie entweder die Option **Entität** oder **abgeleitete Hierarchie** aus, und wählen Sie dann aus der entsprechenden Liste aus.  
  
8.  Wählen Sie aus der Liste **Format** ein Format für die Abonnementsicht aus.  
  
9. Wenn Sie **Explizite Ebenen** oder **Abgeleitete Ebenen** aus der Liste **Format** ausgewählt haben, geben Sie die Anzahl der in die Sicht aufzunehmenden Hierarchieebenen ein.  
  
10. Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten &#40;Master Data Services werden exportiert&#41;](overview-exporting-data-master-data-services.md)   
 [&#40;Master Data Services eine Abonnement Sicht löschen&#41;](delete-a-subscription-view-master-data-services.md)   
 [Erstellen eines Versionsflags &#40;Master Data Services&#41;](create-a-version-flag-master-data-services.md)  
  
  
