---
title: Ausblenden eines Elements (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56e834204698369687528c622cf6167a492766f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615836"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a>Ausblenden eines Elements (Berichts-Generator und SSRS)
  Legen Sie die Sichtbarkeit eines Berichtselements fest, wenn Sie ein Element basierend auf einem Berichtsparameter oder einem anderen von Ihnen angegebenen Ausdruck bedingt ausblenden möchten.

 Sie können auch einen Bericht entwerfen, der dem Benutzer ermöglicht, die Sichtbarkeit von Berichtselementen durch Klicken auf Textfelder im Bericht ein- und auszublenden. Beispielsweise kann dies bei einem Drilldownbericht hilfreich sein. Weitere Informationen finden Sie unter [Hinzufügen einer Erweiterungs- oder Reduzieraktion zu einem Element &#40;Berichts-Generator und SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).

 In den folgenden Verfahren wird beschrieben, wie ein Berichtselement in einem gerenderten Bericht basierend auf einer Konstante oder einem Ausdruck ein- oder ausgeblendet wird.

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a>So blenden Sie ein Berichtselement aus

1.  Klicken Sie in der Berichtsentwurfsansicht mit der rechten Maustaste auf das Berichtselement, und öffnen Sie die Seite **Eigenschaften** des Elements.

    > [!NOTE]
    >  Klicken Sie im Datenbereich, um eine ganze Tabelle oder Matrix auszuwählen. Klicken Sie mit der rechten Maustaste auf einen Zeilen-, Spalten- oder Eckziehpunkt, und klicken Sie anschließend auf **Tablix-Eigenschaften**.

2.  Klicken Sie auf **Transparenz.**

3.  Geben Sie unter **Bei erstmaliger Ausführung des Berichts**an, ob das Element ausgeblendet werden soll, wenn der Bericht erstmals angezeigt wird:

    -   Um das Element anzuzeigen, klicken Sie auf **Anzeigen**.

    -   Um das Element auszublenden, klicken Sie auf **Ausblenden**.

    -   Klicken Sie auf **Je nach Ausdruck einblenden/ausblenden**, um einen Ausdruck anzugeben, der zur Laufzeit ausgewertet wird. Geben Sie den Ausdruck ein, oder klicken Sie auf die Ausdrucksschaltfläche (**fx**), um den Ausdruck im Dialogfeld **Ausdruck** zu erstellen.

        > [!NOTE]
        >  Wenn Sie einen Ausdruck für die Sichtbarkeit angeben, legen Sie die Hidden-Eigenschaft des Berichtselements wie im folgenden Bild dargestellt fest. Der ausgewertete Ausdruck zeigt das Berichtselement an, wenn der Wert False lautet, und blendet das Berichtselement aus, wenn der Wert True lautet. 
        > ![Properties_Visibility-Dialogfeld und Eigenschaft „Hidden“](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility-Dialogfeld und Eigenschaft „Hidden“")

4.  Klicken Sie zweimal auf **OK**.

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a>So blenden Sie statische Zeilen in einer Tabelle, Matrix oder Liste aus

1.  Klicken Sie in der Berichtsentwurfsansicht auf die Tabelle, Matrix oder Liste, um die Zeilen- und Spaltenziehpunkte anzuzeigen.

2.  Klicken Sie mit der rechten Maustaste auf den Zeilenziehpunkt, und klicken Sie anschließend auf **Sichtbarkeit anzeigen**. Das Dialogfeld **Sichtbarkeit anzeigen** wird geöffnet.

3.  Um die Sichtbarkeit festzulegen, führen Sie die Schritte 3 und 4 der ersten Prozedur aus.

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a>So blenden Sie statische Spalten in einer Tabelle, Matrix oder Liste aus

1.  Wählen Sie in der Entwurfsansicht die Tabelle, Matrix oder Liste, um die Zeilen- und Spaltenziehpunkte anzuzeigen.

2.  Klicken Sie mit der rechten Maustaste auf den Spaltenziehpunkt, und klicken Sie anschließend auf **Spaltensichtbarkeit**.

3.  Führen Sie im Dialogfeld **Spaltensichtbarkeit** die Schritte 3 und 4 der ersten Prozedur aus.

## <a name="see-also"></a>Weitere Informationen
 [Drilldown-Aktion &#40;Berichts-Generator und SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Hinzufügen einer Erweiterungs-oder Reduzier Aktion zu einem Element &#40;Berichts-Generator und SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [Ausdrucks Beispiele &#40;Berichts-Generator und SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)


