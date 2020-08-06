---
title: Erstellen eines Modelladministrators (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 24efc3961e6ed5b9f41b2321dfcc4fbf16632270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622754"
---
# <a name="create-a-model-administrator-master-data-services"></a>Erstellen eines Modelladministrators (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Erstellen Sie in einen Modell Administrator, wenn eine Gruppe oder ein Benutzer über die Berechtigung **Aktualisieren** für alle Objekte in einem oder mehreren Modellen verfügen soll.  
  
> [!TIP]  
>  Um die Verwaltung zu vereinfachen, erstellen Sie eine Windows-Gruppe oder eine lokale Gruppe, und konfigurieren Sie diese als Modell Administrator. Sie können anschließend der Gruppe Benutzer hinzufügen und diese daraus entfernen, ohne auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zuzugreifen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-model-administrator"></a>So erstellen Sie einen Modelladministrator  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Wählen Sie auf der Seite **Benutzer** oder **Gruppen** die Zeile für den Benutzer oder die Gruppe aus, den bzw. die Sie bearbeiten möchten.  
  
3.  Klicken Sie auf **Ausgewähltem Benutzer bearbeiten**.  
  
4.  Klicken Sie auf die Registerkarte **Modelle** .  
  
5.  Wählen Sie optional ein Modell aus der Liste **Modell** aus.  
  
6.  Klicken Sie auf **Bearbeiten**.  
  
7.  Klicken Sie auf das Modell, dem Sie die Berechtigung zuweisen möchten.  
  
8.  Wählen Sie im Menü die Option **Aktualisieren**aus.  
  
9. Führen Sie die Schritte 7 und 8 für jedes Modell aus, für das Sie die Gruppe bzw. den Benutzer als Administrator definieren möchten.  
  
10. Klicken Sie auf **Speichern**.  
  
## <a name="remarks"></a>Bemerkungen  
 Weisen Sie Objekten oder Hierarchieelementen keine anderen Berechtigungen zu. Wenn Sie dies tun, ist der Benutzer kein Administrator mehr und kann das Modell nicht in einem anderen Funktionsbereich als **Explorer**anzeigen.  
  
 Es gibt eine Ausnahme: Wenn dem **Benutzer auf der** Registerkarte **Hierarchie** Elemente eine Berechtigung **Aktualisieren** zugewiesen ist, wird der Benutzer weiterhin als Modell Administrator betrachtet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)   
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Hierarchie Element Berechtigungen &#40;Master Data Services zuweisen&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
