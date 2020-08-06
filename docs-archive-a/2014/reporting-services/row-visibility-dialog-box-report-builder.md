---
title: Dialog Feld ' Sichtbarkeit der Zeile ' (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615279"
---
# <a name="row-visibility-dialog-box-report-builder"></a>Zeilensichtbarkeit (Dialogfeld) (Berichts-Generator)
  Mit dem Dialogfeld **Sichtbarkeit anzeigen** können Sie die ausgewählte Zeile beim ersten Ausführen des Berichts anzeigen oder ausblenden oder die Sichtbarkeit der Zeile mit einem anderen Berichtselement aktivieren bzw. deaktivieren.  
  
## <a name="options"></a>Tastatur  
 **Bei erstmaliger Ausführung des Berichts**  
 Wählen Sie eine Option aus, um die ursprüngliche Anzeige der Zeile im Bericht anzugeben.  
  
 **Anzeigen**  
 Wählen Sie diese Option aus, um die Zeile anzuzeigen.  
  
 **Hide**  
 Wählen Sie diese Option aus, um die Zeile auszublenden.  
  
 **Anzeigen oder Ausblenden auf Grundlage eines Ausdrucks**  
 Wählen Sie diese Option aus, um die ursprüngliche Sichtbarkeit mithilfe eines Ausdrucks zu variieren.  
  
 Geben Sie einen Ausdruck ein, der das Element ausblendet, wenn der `Boolean` Wert `True` ausgewertet wird, oder der das Element anzeigt, wenn `False` ausgewertet wird. Klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*), um den Ausdruck zu bearbeiten.  
  
 **Sichtbarkeit kann von diesem Berichtselement ein-/ausgeschaltet werden**  
 Wählen Sie diese Option aus, um ein Umschaltbild anzuzeigen, mit dem der Benutzer diese Zeile in einem HTML Berichts-Viewer anzeigen oder ausblenden kann.  
  
 Sie müssen den Namen eines Textfelds im Bericht eingeben oder wählen, in dem ein Umschaltbild angezeigt werden soll. Beispiel: Textbox1 Das gewählte Textfeld muss im aktuellen oder enthaltenden Bereich für dieses Berichtselement enthalten sein. Beispiel: Wenn Sie die Sichtbarkeit von Zeilen umschalten möchten, die mit einer untergeordneten Gruppe verknüpft sind, wählen Sie ein Textfeld in einer Zeile, die mit der übergeordneten Gruppe verknüpft ist. Wählen Sie ein Textfeld, das in demselben enthaltenden Bereich enthalten ist wie das Diagramm, um die Sichtbarkeit eines Diagramms umzuschalten. Beispiel: der Berichtshauptteil oder ein Rechteck.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Hinzufügen einer Erweiterungs-oder Reduzier Aktion zu einem Element &#40;Berichts-Generator und SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Images &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
