---
title: Aufnehmen von Indikatoren und Messgeräten in einen Messgerätbereich (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1107745f54cd94abd7507a3e9b5a706ca5402de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723474"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a>Aufnehmen von Indikatoren und Messgeräten in einen Messgerätbereich (Berichts-Generator und SSRS)
  Der Messgerätbereich ist der Container der obersten Ebene, der mindestens ein Messgerät und/oder einen Indikator enthält. Indikatoren können in Messgeräte eingebettet werden oder neben ihnen im Messgerätbereich eingefügt werden.  
  
 Wenn der Indikator und das Messgerät im Messgerätbereich angrenzen und Daten aus anderen Feldern anzeigen, empfiehlt es sich, Bezeichnungen hinzufügen, um unmissverständlich anzuzeigen, welche Daten das Messgerät und der Indikator übermitteln.  
  
 Messgerät- und Indikatoroptionen können mit Ausdrücken festgelegt werden. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a>So betten Sie einen Indikator in einem Messgerät ein  
  
1.  Öffnen Sie einen vorhandenen Bericht, oder erstellen Sie einen neuen Bericht, der eine Tabelle und eine Matrix mit den anzuzeigenden Daten enthält. Weitere Informationen finden Sie unter [Tabellen &#40;Berichts-Generator und SSRS&#41;](tables-report-builder-and-ssrs.md) oder [Matrizen &#40;Berichts-Generator und SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Fügen Sie eine Spalte in die Tabelle oder Matrix ein. Weitere Informationen finden Sie unter [Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS)](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Datenbereiche** auf **Messgerät**, und klicken Sie danach auf eine Zelle in der neuen Spalte. Das Dialogfeld **Messgerättyp auswählen** wird angezeigt.  
  
4.  Klicken Sie auf **Radial**. Das erste radiale Messgerät wird ausgewählt.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Klicken Sie auf das Messgerät. Der Bereich **Messgerätdaten** wird geöffnet.  
  
7.  Klicken Sie im Bereich **Werte** im Listenfeld **(Keine Angabe)** auf das Feld, dessen Werte im Messgerät angezeigt werden sollen. Sie können auch das Feld, das verwendet werden soll, aus dem Berichtsdataset ziehen.  
  
8.  Klicken Sie mit der rechten Maustaste auf das Messgerät, klicken Sie auf **Indikator hinzufügen**und anschließend auf **Untergeordnet**. Das Dialogfeld **Indikatorart auswählen** wird geöffnet.  
  
9. Klicken Sie im linken Bereich des Dialogfelds **Indikatorart auswählen** auf den gewünschten Indikatortyp und dann auf den Indikatorsatz.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. Klicken Sie auf den Indikator. Der Bereich **Messgerätdaten** wird geöffnet.  
  
12. Klicken Sie im Bereich **Werte** im Listenfeld **(Keine Angabe)** auf das Feld, dessen Werte Sie als Indikator anzeigen lassen möchten. Sie können auch das Feld, das verwendet werden soll, aus dem Berichtsdataset ziehen.  
  
     Das Feld kann sowohl das gleiche als auch ein anderes Feld als das sein, das Sie im Messgerät verwenden.  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a>So zeigen Sie einen Indikator und ein Messgerät nebeneinander an  
  
1.  Öffnen Sie einen vorhandenen Bericht, oder erstellen Sie einen neuen Bericht, der eine Tabelle und eine Matrix mit den anzuzeigenden Daten enthält. Weitere Informationen finden Sie unter [Tabellen &#40;Berichts-Generator und SSRS&#41;](tables-report-builder-and-ssrs.md) oder [Matrizen &#40;Berichts-Generator und SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Fügen Sie eine Spalte in die Tabelle oder Matrix ein. Weitere Informationen finden Sie unter [Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS)](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Datenbereiche** auf **Messgerät**, und klicken Sie danach auf eine Zelle in der eingefügten Spalte. Das Dialogfeld **Messgerättyp auswählen** wird angezeigt.  
  
4.  Klicken Sie auf **Radial**. Das erste radiale Messgerät wird ausgewählt.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Klicken Sie auf das Messgerät. Der Bereich **Messgerätdaten** wird geöffnet.  
  
7.  Klicken Sie im Bereich **Werte** im Listenfeld **(Keine Angabe)** auf das Feld, dessen Werte im Messgerät angezeigt werden sollen. Sie können auch das Feld, das verwendet werden soll, aus dem Berichtsdataset ziehen.  
  
8.  Klicken Sie mit der rechten Maustaste auf das Messgerät, klicken Sie auf **Indikator hinzufügen**und anschließend auf **Angrenzend**. Das Dialogfeld **Indikatorart auswählen** wird geöffnet.  
  
9. Klicken Sie im linken Bereich des Dialogfelds **Indikatorart auswählen** auf den gewünschten Indikatortyp und dann auf den Indikatorsatz.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. Klicken Sie auf den Indikator. Der Bereich **Messgerätdaten** wird geöffnet.  
  
12. Klicken Sie im Bereich **Werte** im Listenfeld **(Keine Angabe)** auf das Feld, dessen Werte Sie als Indikator anzeigen lassen möchten. Sie können auch das Feld, das verwendet werden soll, aus dem Berichtsdataset ziehen.  
  
     Das Feld kann sowohl das gleiche als auch ein anderes Feld als das sein, das Sie im Messgerät verwenden.  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
14. Klicken Sie mit der rechten Maustaste auf den Bereich „Messgerät“, und klicken Sie anschließend auf **Bezeichnung hinzufügen**. Dem Messgerät wird eine Bezeichnung hinzugefügt. Wiederholen Sie diesen Schritt noch einmal.  
  
     Der Messgerätbereich verfügt über zwei Bezeichnungen.  
  
15. Ziehen Sie jede Bezeichnung an eine Stelle in der Nähe des Messgeräts oder Indikators.  
  
16. Klicken Sie mit der rechten Maustaste auf die Bezeichnung in der Nähe des Messgeräts, klicken Sie auf **Bezeichnungseigenschaften**, und geben Sie den Text ein, der im Feld **Text** angezeigt werden soll.  
  
17. Klicken Sie mit der rechten Maustaste auf den Indikator in der Nähe des Messgeräts, klicken Sie auf **Bezeichnungseigenschaften**, und geben Sie den Text ein, der im Feld **Text** angezeigt werden soll.  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
