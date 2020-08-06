---
title: Definieren von Farben in einem Diagramm mit einer Palette (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7db137ed87b0c84e43577dcf2936a6287abd8e36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617742"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Definieren von Farben in einem Diagramm mit einer Palette (Berichts-Generator und SSRS)
  Sie können die Farbpalette für ein Diagramm durch Auswählen einer vordefinierten Palette oder durch Definieren einer benutzerdefinierten Palette ändern. Benutzerdefinierte Paletten sind berichtsspezifisch.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>So ändern Sie die Farben im Diagramm mit einer integrierten Farbpalette  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf das Diagramm. Die Eigenschaften für das Diagrammobjekt werden im Bereich Eigenschaften angezeigt.  
  
     Der Objektname (standardmäßig**Chart1** ) wird in der Dropdownliste oben im Bereich „Eigenschaften“ aufgeführt.  
  
3.  Wählen Sie im Abschnitt **Diagramm** für die „Palette“-Eigenschaft eine neue Palette aus der Dropdownliste aus.  
  
    > [!NOTE]  
    >  Sie können die Farben oder die Reihenfolge in einer vordefinierten Palette nicht ändern.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>So definieren Sie eigene Farben im Diagramm mit einer benutzerdefinierten Farbpalette  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche auf das Diagramm. Die Eigenschaften für das Diagrammobjekt werden im Bereich Eigenschaften angezeigt.  
  
3.  Wählen Sie im Abschnitt **Diagramm** für die-Eigenschaft die Option `Palette` **Benutzer**definiert aus.  
  
4.  Klicken Sie in der CustomPaletteColors-Eigenschaft auf die Schaltfläche zum Bearbeiten der Collection ( **…** ). Das Dialogfeld **ReportColorExpression-Auflistungs-Editor** wird geöffnet.  
  
5.  Klicken Sie auf **Hinzufügen** , um eine Farbe hinzuzufügen. Wählen Sie in der Dropdownliste eine Farbe aus, oder wählen Sie Ausdruck, und geben Sie einen hexadezimalen Wert für eine bestimmte Farbe an, z. B. ff6600 für "Orange".  
  
     Weitere Informationen zu Hexadezimalwerten finden Sie unter [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) auf MSDN.  
  
6.  Klicken Sie auf **Hinzufügen** , um der Palette weitere Farben hinzuzufügen.  
  
7.  Abschließend klicken Sie auf **OK**.  
  
 Wenn Sie eine benutzerdefinierte Palette verwenden, können Sie die Reihenfolge der Farben ändern, um die Farbe verschiedener Reihen im Diagramm zu ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Angeben von Farben, die für mehrere Formdiagramme konsistent sind &#40;Berichts-Generator und SSRS&#41;](shape-charts-report-builder-and-ssrs.md)  
  
  
