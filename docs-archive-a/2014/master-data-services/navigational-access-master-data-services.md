---
title: Navigationszugriff (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607859"
---
# <a name="navigational-access-master-data-services"></a>Navigationszugriff (Master Data Services)
  Der Navigationszugriff gilt für die Modellobjektsicherheit, die auf der Registerkarte **Modelle** zugewiesen wird.  
  
 Navigationszugriff ist der Zugriff auf höhere Ebenen als die Ebene, für die Sie Sicherheit zugewiesen haben.  
  
 In diesem Beispiel werden einer Entität Berechtigungen zugewiesen, der Navigationszugriff wird daher auf der Modellebene gewährt.  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entitäten**  
  
 Wenn Sie einer Entität, den Blattelementen oder konsolidierten Elementen Berechtigungen zuweisen, bedeutet Navigationszugriff, dass Sie den Namen und den Code für alle Elemente lesen oder aktualisieren können. Sie können auch den Modellnamen lesen.  
  
 **Attribute**  
  
 Wenn Sie einem Attribut Berechtigungen zuweisen, bedeutet Navigationszugriff, dass Sie den Namen und den Code für alle Elemente in der Entität lesen oder aktualisieren können. Sie können auch den Modellnamen lesen.  
  
 **Sammlungen**  
  
 Wenn Sie Auflistungen Berechtigungen zuweisen, können Sie den Namen, Code, die Beschreibung und Besitzer-ID lesen oder aktualisieren. Sie können auch den Modellnamen lesen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
