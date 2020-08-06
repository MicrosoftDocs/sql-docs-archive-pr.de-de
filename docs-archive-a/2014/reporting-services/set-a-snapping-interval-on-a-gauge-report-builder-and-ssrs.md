---
title: Festlegen eines Richtungs Intervalls auf einem Messgerät (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdc2a621c4406791838d97e93f47cd32fa9d5f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719459"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a>Festlegen eines Ausrichtungsintervalls auf einem Messgerät (Berichts-Generator und SSRS)
  Durch das Ausrichtungsintervall wird das Vielfache festgelegt, auf das Werte gerundet werden. Standardmäßig zeigt das Messgerät auf den exakten Wert des Felds, das Sie im Datenbereich angegeben haben. Eventuell möchten Sie jedoch, dass der exakte Wert nach oben oder unten gerundet wird, sodass der Zeiger an einem vordefinierten Intervall ausgerichtet wird. Beispiel: Wenn der Wert auf dem Messgerät 34,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 35. Wenn der Wert auf dem Messgerät 31,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 30.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a>So legen Sie ein Ausrichtungsintervall auf einem Messgerät fest  
  
1.  Klicken Sie auf eine der Nummern des Messgeräts, um die Skala auszuwählen.  
  
2.  Öffnen Sie den Bereich Eigenschaften.  
  
    > [!NOTE]  
    >  Wenn der Bereich Eigenschaften nicht angezeigt wird, klicken Sie auf die Registerkarte **Ansicht** , und aktivieren Sie dann das Kontrollkästchen **Eigenschaften** .  
  
3.  Klicken Sie in der Eigenschaft **Zeiger** auf die Schaltfläche (...). Der Zeigerauflistungs-Editor wird geöffnet.  
  
4.  Legen Sie die Eigenschaft **SnappingEnabled** auf fest `True` .  
  
5.  Legen Sie das **SnappingInterval** auf einen Wert fest, der das Richtungs Intervall darstellt. Der Zeiger wird am nächsten Rundungsvielfachen des angegebenen Werts ausgerichtet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Skalen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formatieren von Zeigern auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
