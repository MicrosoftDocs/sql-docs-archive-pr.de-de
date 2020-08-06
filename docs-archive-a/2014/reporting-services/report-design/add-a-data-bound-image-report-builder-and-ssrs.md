---
title: Hinzufügen eines datengebundenen Bilds (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608304"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Hinzufügen eines datengebundenen Bilds (Berichts-Generator und SSRS)
  Ein Bericht kann einen Verweis auf ein Bild enthalten, das in einer Datenbank gespeichert ist. Ein solches Bild wird als *datengebundenes Bild*bezeichnet. Bilder, die neben Produktnamen in einer Produktliste angezeigt werden, sind Beispiele für datengebundene Bilder.  
  
 Für das Hinzufügen eines datengebundenes Bilds zu einem Seitenkopf oder -fuß sind zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [Seitenkopf- und Seitenfußzeilen (Berichts-Generator und SSRS)](page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>So fügen Sie ein datengebundenes Bild hinzu  
  
1.  Erstellen Sie in der Berichtsentwurfsansicht eine Tabelle mit einer Datenquellenverbindung und einem Dataset mit einem Feld, das binäre Bilddaten enthält. Weitere Informationen finden Sie unter [Tabellen &#40;Berichts-Generator und SSRS&#41;](tables-report-builder-and-ssrs.md).  
  
2.  Fügen Sie eine Spalte in die Tabelle ein. Weitere Informationen finden Sie unter [Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS)](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Klicken Sie im Menü **Einfügen** auf **Bild**und dann in die Datenzeile der neuen Spalte.  
  
4.  Geben Sie im Dialogfeld **Bildeigenschaften** auf der Seite **Allgemein** einen Namen im Textfeld Name ein, oder übernehmen Sie den Standardnamen.  
  
5.  (Optional) Geben Sie im Textfeld **QuickInfo** Text ein, der angezeigt wird, wenn der Benutzer in dem in HTML gerenderten Bericht auf das Bild zeigt.  
  
6.  Wählen Sie unter **Bildquelle auswählen**die Option **Datenbank**aus.  
  
7.  Wählen Sie unter **Dieses Feld verwenden**das Feld aus, das Bilder im Bericht enthält.  
  
8.  Wählen Sie unter **Diesen MIME-Typ verwenden** den MIME-Typ oder das Dateiformat des Bilds aus, beispielsweise BMP.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Ein Bildplatzhalter wird auf der Berichtsentwurfsoberfläche angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bilder &#40;Berichts-Generator und SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Einbetten eines Bilds in einen Bericht &#40;Berichts-Generator und SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Hinzufügen eines externen Bilds &#40;Berichts-Generator und SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
