---
title: Ausblenden von Legendenelementen im Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 20444432f580ffaf1c5f4de1320b06319f973a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621358"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>Ausblenden von Legendenelementen im Diagramm (Berichts-Generator und SSRS)
  Standardmäßig werden alle einem Nicht-Formdiagramm hinzugefügten Reihen in der Legende als Element hinzugefügt. Für Kreis-, Ring-, Trichter- und Pyramidendiagramme werden für alle dem Diagramm hinzugefügten Reihen der Legende einzelne Datenpunkte hinzugefügt.  
  
 Sie können in der Legende beliebige Elemente ausblenden. Wenn Sie ein Legendenelement ausblenden, wird dieses immer noch im Diagramm angezeigt. Dies ist hilfreich in Situationen, in denen für eine dem Diagramm hinzugefügte Reihe keine weiteren Informationen angezeigt werden sollen. Wenn Sie dem Diagramm beispielsweise eine berechnete Reihe (z. B. einen gleitenden Durchschnitt) hinzugefügt haben, empfiehlt es sich u. U., diesen Eintrag in der Legende auszublenden, sodass nur für die ursprüngliche Reihe weitere Informationen angezeigt werden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>So blenden Sie ein in der Legende angezeigtes Element aus  
  
1.  Klicken Sie mit der rechten Maustaste auf die auszublendende Reihe, und wählen Sie die Option **Reiheneigenschaften**aus.  
  
2.  Klicken Sie auf **Legende**. Aktivieren Sie die Option **Diese Reihe in Legende nicht anzeigen** .  
  
    > [!NOTE]  
    >  Eine Reihe kann nicht für eine Gruppe ausgeblendet und für andere angezeigt werden. Wenn Sie dem Bereich **Reihengruppen** ein Feld hinzugefügt haben, werden alle zu dieser Gruppe gehörenden Reihen ausgeblendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Ändern des Texts eines Legendenelements (Berichts-Generator und SSRS)](chart-legend-change-item-text-report-builder.md)   
 [Hinzufügen eines gleitenden Durchschnitts zu einem Diagramm (Berichts-Generator und SSRS)](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Legendeneigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
