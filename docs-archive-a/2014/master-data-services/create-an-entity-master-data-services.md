---
title: Erstellen einer Entität (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7cefdedd07ee248f12b3b17337878934a2b1aa84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622188"
---
# <a name="create-an-entity-master-data-services"></a>Erstellen einer Entität (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Entität, die Elemente und ihre Attribute enthält.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Es muss ein Modell vorhanden sein. Weitere Informationen finden Sie unter [Erstellen eines Modells &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>So erstellen Sie eine Entität  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Klicken Sie auf **Entität hinzufügen**  
  
5.  Geben Sie im Feld **Entitäts Name** den Namen der Entität ein.  
  
6.  Geben Sie im Feld **Name für Stagingtabellen** einen Namen für die Stagingtabelle ein.  
  
    > [!TIP]  
    >  Verwenden Sie den Modellnamen als einen Teil des Stagingtabellennamens, z.B. *Modelname_Entityname*. Dies erleichtert die Suche nach den Tabellen in der Datenbank. Weitere Informationen zu den Stagingtabellen finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
7.  Optional. Aktivieren Sie das Kontrollkästchen **Codewerte automatisch erstellen** . Weitere Informationen finden Sie unter [automatische Code Erstellung &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).  
  
8.  Wählen Sie in der Liste **explizite Hierarchien und Sammlungen aktivieren** eine der folgenden Optionen aus:  
  
    -   **Nein**. Wählen Sie diese Option aus, wenn Sie die Entität für explizite Hierarchien und Auflistungen nicht aktivieren müssen. Sie können dies später nach Bedarf ändern.  
  
    -   **Ja**. Wählen Sie diese Option aus, wenn Sie die Entität für explizite Hierarchien und Auflistungen aktivieren möchten. Geben Sie im Feld **Name der expliziten Hierarchie** einen Namen ein. Wählen Sie optional erforderliche **Hierarchie aus (alle Blatt Elemente werden eingeschlossen** , um die explizite Hierarchie als erforderliche Hierarchie zu erstellen.  
  
9. Klicken Sie auf **Entität speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen eines Textattributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Erstellen eines Dateiattributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entitäten &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Ändern eines Entitäts namens &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md)   
 [Löschen einer Entität &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
