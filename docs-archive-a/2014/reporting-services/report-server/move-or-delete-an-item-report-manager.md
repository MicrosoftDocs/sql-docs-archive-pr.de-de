---
title: Verschieben oder Löschen eines Elements (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695285"
---
# <a name="move-or-delete-an-item-report-manager"></a>Verschieben oder Löschen eines Elements (Berichts-Manager)
  Berichte und berichtsbezogene Elemente, die Sie auf einem Berichtsserver veröffentlichen, werden in Ordnern gespeichert. Sie können Elemente in einen anderen Ordner verschieben. Verweise auf diese Elemente werden automatisch vom Berichtsserver verwaltet. Bevor Sie ein Element löschen, ist zu überprüfen, ob Elemente davon abhängen.  
  
## <a name="move-an-item"></a>Verschieben eines Elements  
 Sie können Berichtsserverelemente an andere Speicherorte in der Ordnerhierarchie des Berichtsservers verschieben. Beim Verschieben eines Elements werden auch alle zugehörigen Eigenschaften (einschließlich Sicherheitseinstellungen) an den neuen Speicherort verschoben. Wenn Sie einen Ordner verschieben, werden gleichzeitig alle in diesem Ordner enthaltenen Elemente verschoben.  
  
 Im Berichts-Manager werden die verschiebbaren Elemente in der Ordnerhierarchie angezeigt. In der folgenden Tabelle sind die Symbole für die verschiedenen verschiebbaren Elemente dargestellt.  
  
|Symbol|Verschiebbares Element|  
|----------|-------------------|  
|![Report icon](../media/hlp-16doc.gif "Berichtssymbol")|Bericht|  
|![Symbol für einen verknüpften Bericht](../media/hlp-16linked.gif "Symbol für einen verknüpften Bericht")|Verknüpfter Bericht|  
|![Ordnersymbol](../media/hlp-16folder.gif "Ordnersymbol")|Ordner|  
|![allgemeines Ressourcensymbol](../media/hlp-16file.gif "allgemeines Ressourcensymbol")|Allgemeine Ressource|  
|![Shared data source icon](../media/hlp-16datasource.png "Symbol für freigegebene Datenquelle")|Freigegebene Datenquelle|  
||Freigegebenes Dataset|  
  
 Nicht alle Elemente, mit denen Sie arbeiten, können verschoben werden. Elemente, die einem Bericht zugeordnet sind, z. B. Abonnements oder ein Berichtsverlauf, können nicht verschoben werden. Diese Elemente werden mit den zugehörigen Berichten verschoben. Auch Elemente wie freigegebene Zeitpläne, die außerhalb der Ordnerhierarchie vorhanden sind, können nicht verschoben werden. Sie können ohne die entsprechende Berechtigung keine Elemente verschieben. Die Berechtigung zum Verschieben eines Elements wird erteilt, wenn folgende Tasks in Ihrer Rollenzuweisung für das entsprechende Element ausgewählt sind: "Berichte verwalten", "Modelle verwalten", "Ordner verwalten" und "Datenquellen verwalten".  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a>So verschieben Sie ein Element auf der Inhaltsseite  
  
1.  Start [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;].. /Report-Manager-SSRS-Native-Mode.MD).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu verschiebende Element.  
  
3.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
4.  Klicken Sie im Dropdownmenü auf **Verschieben**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Geben Sie für **Speicherort**den Ordner an, in den Sie das Element verschieben möchten. Sie können den vollqualifizierten Ordnernamen eingeben oder die Strukturansicht verwenden, um zum gewünschten Ordner zu navigieren.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 Alternativ können Sie zum zu verschiebenden Objekt navigieren, auf **Eigenschaften**klicken, und anschließend oben auf der Seite auf **Verschieben** klicken.  
  
## <a name="delete-an-item"></a>Löschen eines Elements  
 Bevor Sie ein Element löschen, ist zu prüfen, ob es von anderen Elementen verwendet wird. Wenn Sie beispielsweise eine freigegebene Datenquelle löschen, werden Berichte und Modelle, die diese Datenquelle verwenden, nicht mehr ausgeführt. Beim Löschen eines Berichts werden auch Abonnements und der Berichtsverlauf, die mit diesem Bericht verknüpft sind, gelöscht. Um abhängige Elemente für ein Element zu suchen, finden Sie weitere Informationen unter [Seite "abhängige Elemente" &#40;Berichts-Manager&#41;]. /Dependent-Items-Page-Report-Manager.MD).  
  
#### <a name="to-delete-a-report-or-item"></a>So löschen Sie einen Bericht oder ein Element  
  
1.  Start [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;].. /Report-Manager-SSRS-Native-Mode.MD).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und suchen Sie das zu löschende Element.  
  
3.  Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
4.  Klicken Sie im Dropdownmenü auf **Löschen**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Inhaltsseite &#40;Berichts-Manager&#41;].. /Contents-Page-Report-Manager.MD)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
