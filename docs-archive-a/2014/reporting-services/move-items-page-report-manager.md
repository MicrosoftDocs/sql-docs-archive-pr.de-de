---
title: Seite "Elemente verschieben" (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98ff306caf634a5f0478e2eba03c2313b24be274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723581"
---
# <a name="move-items-page-report-manager"></a>Elemente verschieben (Seite, Berichts-Manager)
  Auf der Seite Elemente verschieben können Sie einen Bericht, Ordner oder ein anderes Element an einen neuen Speicherort auf dem Berichtsserver verschieben. Sie können den Pfad des neuen Speicherortes eingeben oder die Strukturansicht verwenden, um zu einem neuen Speicherort im Namespace des Berichtsservers zu wechseln. Sie können nur die Elemente verschieben, für die Sie über die entsprechende Berechtigung verfügen und die auf dem aktuellen Berichtsserver gespeichert sind.  
  
 Wenn Sie ein Element verschieben, auf das durch ein anderes Element verwiesen wird (z. B. eine freigegebene Datenquelle oder ein freigegebenes Modell, auf die oder das viele Berichte verweisen), wird der Pfad zu diesem Element automatisch aktualisiert. Durch das Verschieben einer freigegebenen Datenquelle wird die Datenquellenverbindung der Berichte und Modelle, die diese verwenden, nicht unterbrochen. Wenn Sie eine freigegebene Datenquelle oder ein freigegebenes Modell in einen Ordner verschieben, für den die Benutzer keine Berechtigung haben, können sie immer noch jeden Bericht ausführen, der auf diese Quelle oder dieses Modell verweist. Das Element ist jedoch in der Ordnerhierarchie für sie nicht sichtbar.  
  
 Geben Sie für **Speicherort**den vollständigen Pfad zum Ordner an, wobei Sie mit dem Namen des Stammordners beginnen. Sie können den Pfadnamen eingeben oder die Strukturansicht verwenden, um zu dem gewünschten Ordner zu wechseln.  
  
> [!NOTE]  
>  Nicht alle Elemente können verschoben werden. Reservierte Ordner wie Home, Meine Berichte und Benutzerordner können nicht verschoben werden. Der Berichtsverlauf oder Momentaufnahmen können ebenfalls nicht an andere Speicherorte verschoben werden. Verlauf und Momentaufnahmen werden immer zusammen mit dem Bericht gespeichert, auf dem sie basieren, und der Zugriff auf sie erfolgt ebenfalls über diesen Bericht.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgende Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a>So öffnen Sie die Seite "Elemente verschieben" auf der Seite "Inhalt" in der Detailansicht  
  
1.  Öffnen Sie den Berichts-Manager, und navigieren Sie zu dem Ordner mit dem zu verschiebenden Element. Sie können auch Elemente von der Homepage des Berichts-Managers verschieben.  
  
2.  Klicken Sie auf der Symbolleiste auf **Detailansicht**.  
  
    > [!NOTE]  
    >   Wenn nur die **Kachelansicht**angezeigt wird, sind Sie bereits in der **Detailansicht**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben einem Element, und klicken Sie dann auf der Symbolleiste auf **Verschieben** . Sie können mehr als ein Kontrollkästchen aktivieren, wenn Sie mehrere Elemente an den gleichen neuen Speicherort verschieben möchten.  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a>So öffnen Sie die Seite 'Elemente verschieben' auf der Seite 'Inhalt' in der Kachelansicht  
  
1.  Öffnen Sie den Berichts-Manager, und navigieren Sie zu dem Ordner mit dem zu verschiebenden Element. Sie können auch Elemente von der Homepage des Berichts-Managers verschieben.  
  
2.  Klicken Sie auf der Symbolleiste auf **Kachelansicht**.  
  
    > [!NOTE]  
    >   Wenn nur **Detailansicht**angezeigt wird, sind Sie bereits in der Kachelansicht ****.  
  
3.  Zeigen Sie auf ein Element, und klicken Sie auf den Dropdownpfeil.  
  
4.  Klicken Sie im Dropdownmenü auf **Verschieben**.  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a>So öffnen Sie die Seite 'Elemente verschieben' von der Seite 'Allgemeine Eigenschaften' eines Elements  
  
1.  Öffnen Sie den Berichts-Manager, und navigieren Sie zu dem Ordner mit dem zu verschiebenden Element. Sie können auch Elemente von der Homepage des Berichts-Managers verschieben.  
  
2.  Zeigen Sie auf ein Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für ein Element geöffnet.  
  
4.  Klicken Sie auf der Elementsymbolleiste auf **Verschieben**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Allgemeine Eigenschaften (Seite), Ordner &#40;Berichts-Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md)   
 [Allgemeine Eigenschaften (Seite), Berichte &#40;Berichts-Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Allgemeine Eigenschaften (Seite), Ressourcen &#40;Berichts-Manager&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md)   
 [Allgemeine Eigenschaften (Seite), freigegebene Datenquellen &#40;Berichts-Manager&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
