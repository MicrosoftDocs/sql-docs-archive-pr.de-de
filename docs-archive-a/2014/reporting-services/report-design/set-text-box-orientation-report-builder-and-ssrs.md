---
title: Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS) |- Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d509f1df29203fa5def79b61b74ae9db8f40d204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608282"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS)
  Ein Textfeld kann in verschiedene Richtungen ausgerichtet werden: horizontal, vertikal (der Text wird von unten nach oben gelesen) oder um 270 Grad gedreht (Text wird von unten nach oben gelesen). Da die Ausrichtung für das Textfeld und nicht den Text selbst festgelegt wird, gilt sie für den gesamten Text im Textfeld. Sie können keine anderen Ausrichtungen für Teile des Texts angeben. Passen Sie die Spaltenbreite und die Zeilenhöhe manuell an, damit der gedrehte Text vollständig angezeigt wird.  
  
 Die "Write Mode"-Eigenschaft, mit der Sie die Textausrichtung angeben, ist im Dialogfeld " **Text Feldeigenschaften** " nicht verfügbar. Zum Festlegen der Eigenschaft müssen Sie das Eigenschaftenfenster öffnen und die Eigenschaft dort festlegen. Die verfügbaren Werte für die Eigenschaft "beschreitingmode" sind **Horizontal** (Text Lesevorgang von links nach rechts), **vertikal** (Text wird von oben nach unten gelesen), **Rotate270** (Text wird von unten nach oben gelesen). Sie müssen die Spaltenbreite und die Zeilenhöhe manuell anpassen, damit der Text vollständig angezeigt wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>So legen Sie die Textausrichtung fest  
  
1.  Erstellen Sie einen neuen Bericht, oder öffnen Sie einen vorhandenen Bericht.  
  
2.  Wenn der Eigenschaftenbereich nicht geöffnet ist, klicken Sie auf die Registerkarte **Ansicht** , und aktivieren Sie das Kontrollkästchen **Eigenschaften** .  
  
3.  Klicken Sie auf das Textfeld, für das die Textausrichtung geändert werden soll.  
  
4.  Suchen Sie im Eigenschaften Bereich nach der Eigenschaft "beschreitingmode", und wählen Sie in der Dropdown Liste die Textausrichtung aus, die auf das Textfeld angewendet werden soll.  
  
    > [!NOTE]  
    >  Wenn die Eigenschaften im Eigenschaftenbereich in Kategorien angeordnet sind, befindet sich WritingMode in der Kategorie **Lokalisierung** .  
  
5.  Wählen Sie im Listenfeld **Horizontal**, **Vertical**oder **Rotate270**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Text Felder &#40;Berichts-Generator und SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Tutorial: Formatieren von Text (Berichts-Generator)](../tutorial-format-text-report-builder.md)  
  
  
