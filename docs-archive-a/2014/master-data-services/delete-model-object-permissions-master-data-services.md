---
title: Löschen von Berechtigungen für Modellobjekte (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 98da869476e597d76a83b0b86cc9e6e4274a25e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699951"
---
# <a name="delete-model-object-permissions-master-data-services"></a>Löschen von Berechtigungen für Modellobjekte (Master Data Services)
  Löschen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Modellobjektberechtigungen, um erfolgte Zuweisungen zu entfernen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-model-object-permissions"></a>So löschen Sie Modellobjektberechtigungen  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Wählen Sie auf der Seite **Benutzer** oder **Gruppen** die Zeile für den Benutzer oder die Gruppe aus, den bzw. die Sie bearbeiten möchten.  
  
3.  Klicken Sie auf **Ausgewähltem Benutzer bearbeiten**.  
  
4.  Klicken Sie auf die Registerkarte **Modelle** .  
  
5.  Wählen Sie optional ein Modell aus der Liste **Modell** aus.  
  
6.  Wählen Sie im Bereich **Zusammenfassung der Modell Berechtigungen** die Zeile für die Berechtigung aus, die Sie löschen möchten.  
  
7.  Klicken Sie auf **ausgewählte Berechtigung Löschen**.  
  
    > [!NOTE]  
    >  Sie können keine Berechtigung von einem Benutzer entfernen, wenn die Berechtigung von einer Gruppe geerbt wird. Sie müssen stattdessen die Berechtigung von der Gruppe entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
