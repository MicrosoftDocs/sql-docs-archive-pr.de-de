---
title: Erstellen und Verwalten von KPIs (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e9d7ef77939efe407ed6ab0d725a6d788c58b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616210"
---
# <a name="create-and-manage-kpis-ssas-tabular"></a>Erstellen und Verwalten von KPIs (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie ein KPI (Key Performance Indicator) in einem tabellarischen Modell erstellt, bearbeitet oder gelöscht wird. Um einen KPI zu erstellen, wählen Sie ein Measure aus, das den Basiswert des KPIs ergibt. Anschließend wählen Sie im Dialogfeld Key Performance Indicator ein zweites Measure oder einen absoluten Wert aus, das bzw. der einen Zielwert ergibt. Sie können dann Statusschwellenwerte definieren, mit denen die Leistung zwischen dem Basis- und dem Zielmeasure gemessen wird.  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So erstellen Sie einen KPI](#bkmk_create_KPI)  
  
-   [So bearbeiten Sie einen KPI](#bkmk_edit_KPI)  
  
-   [So löschen Sie einen KPI und das basismeasure](#bkmk_delete)  
  
-   [So löschen Sie einen KPI, behalten aber das Basismeasure bei](#bkmk_delete_KPI)  
  
## <a name="tasks"></a>Aufgaben  
  
> [!IMPORTANT]  
>  Bevor Sie einen KPI erstellen, müssen Sie zuerst ein Basismeasure generieren, das einen Wert ergibt. Anschließend erweitern Sie das Basismeasure zu einem KPI. Das Erstellen von Measures wird in einem anderen Thema beschrieben: [Erstellen und Verwalten von Measures &#40;SSAS – tabellarisch&#41;](measures-ssas-tabular.md). Für einen KPI ist zudem ein Zielwert erforderlich. Dieser Wert kann von einem anderen vordefinierten Measure stammen oder ein absoluter Wert sein. Nachdem Sie ein Basismeasure zu einem KPI erweitert haben, können Sie den Zielwert auswählen und die Statusschwellenwerte im Dialogfeld Key Performance Indicator definieren.  
  
###  <a name="to-create-a-kpi"></a><a name="bkmk_create_KPI"></a> So erstellen Sie einen KPI  
  
1.  Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) fungieren soll, und klicken Sie dann im Kontextmenü auf **KPI erstellen**.  
  
2.  Wählen Sie im Dialogfeld **Key Performance Indicator** unter **Zielwert definieren**eine der folgenden Optionen aus:  
  
     Klicken Sie auf **Measure**, und wählen Sie dann ein Zielmeasure aus dem Listenfeld aus.  
  
     Wählen Sie **Absoluter Wert**aus, und geben Sie einen numerischen Wert ein.  
  
3.  Klicken Sie in **Statusschwellenwerte definieren**auf den Schieberegler, um den niedrigen und hohen Schwellenwert festzulegen.  
  
4.  Klicken Sie in **Symbolart auswählen**auf einen Bildtyp.  
  
5.  Klicken Sie auf **Beschreibungen**, und geben Sie Beschreibungen für KPI, Wert, Status und Ziel ein.  
  
> [!TIP]  
>  Sie können die Funktion In Excel analysieren verwenden, um den KPI zu testen. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](analyze-in-excel-ssas-tabular.md)definieren.  
  
###  <a name="to-edit-a-kpi"></a><a name="bkmk_edit_KPI"></a> So bearbeiten Sie einen KPI  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **KPI-Einstellungen bearbeiten**.  
  
###  <a name="to-delete-a-kpi-and-the-base-measure"></a><a name="bkmk_delete"></a> So löschen Sie einen KPI und das Basismeasure  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **Löschen**.  
  
###  <a name="to-delete-a-kpi-but-keep-the-base-measure"></a><a name="bkmk_delete_KPI"></a>So löschen Sie einen KPI, behalten aber das basismeasure bei  
  
-   Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure, das als Basismeasure (Wert) des KPI fungiert, und klicken Sie dann auf **KPI löschen**.  
  
## <a name="alt-shortcuts"></a>ALT-Tastenkombinationen  
  
|Benutzeroberflächenabschnitt|Tastaturbefehl|  
|----------------|-----------------|  
|KPI-Basismeasure|ALT+B|  
|KPI-Status|ALT+S|  
|"Measure"|ALT+M|  
|Absoluter Wert|ALT+A|  
|Statusschwellenwerte definieren|ALT+C|  
|Symbolart auswählen|ALT+I|  
|Trend|ALT+T|  
|Beschreibungen|ALT+D|  
|Trend|ALT+T|  
  
## <a name="see-also"></a>Weitere Informationen  
 [KPIs &#40;tabellarischen SSAS-&#41;](kpis-ssas-tabular.md)   
 [Measures &#40;tabellarischen SSAS-&#41;](measures-ssas-tabular.md)   
 [Erstellen und Verwalten von Measures &#40;SSAS – tabellarisch&#41;](create-and-manage-measures-ssas-tabular.md)  
  
  
