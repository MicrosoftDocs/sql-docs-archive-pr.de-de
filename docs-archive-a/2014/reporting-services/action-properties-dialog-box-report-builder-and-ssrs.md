---
title: Aktions Eigenschaften (Dialog Feld) (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619661"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a>Aktionseigenschaften (Dialogfeld) (Berichts-Generator und SSRS)
  Das Dialogfeld **Aktion** kann verwendet werden, um Linkoptionen für Diagramme, Messgeräte und Kartenelemente zu aktivieren, die Links unterstützen. Definieren Sie eine Aktion, damit ein Benutzer auf den Bereicht klicken und einen Link mit einer URL, einem anderen Bericht auf demselben Berichtsserver oder auf einer SharePoint-Site, die in einen Berichtsserver integriert ist, oder mit einer anderen Stelle in demselben Bericht herstellen kann.  
  
## <a name="options"></a>Tastatur  
 **Als Aktion aktivieren**  
 Wählen Sie eine Option aus, um anzugeben, welche Aktion ausgeführt werden soll, wenn Benutzer auf das Element klicken.  
  
 **None**  
 Wählen Sie diese Option aus, um anzugeben, dass für dieses Element keine Aktion ausgeführt wird.  
  
 **Gehe zu Bericht**  
 Wählen Sie diese Option aus, um einen Link zu einem Drillthroughbericht auf einem Berichtsserver zu erstellen. Bei Auswahl von **Gehe zu Bericht**werden folgende zusätzliche Optionen angezeigt.  
  
 **Bericht angeben**  
 Geben Sie den Namen des Berichts ein, den Sie als Drillthroughbericht verwenden möchten, oder wählen Sie ihn aus. Drillthroughberichte müssen sich auf dem gleichen Berichtsserver wie dieser Bericht befinden.  
  
 Verwenden Sie für einen Bericht, der auf einem für den einheitlichen Modus konfigurierten Berichtsserver veröffentlicht wurde, einen vollständigen oder relativen Pfad ohne die Dateinamenerweiterung. Falls sich der Bericht in demselben Ordner befindet wie der aktuelle Bericht, verwenden Sie nur den Namen des Berichts. Falls sich der Bericht in einem anderen Ordner auf demselben Berichtsserver befindet, verwenden Sie einen relativen oder vollständigen Pfad. Ein relativer Pfad beginnt mit dem aktuellen Ordner und enthält dann weitere übergeordnete Ordner in der Ordnerhierarchie, beispielsweise ../Ordner2/Bericht1. Ein vollständiger Pfad beginnt mit /, dem Basisordner. Beispiel: /Berichte/Bericht1.  
  
 Verwenden Sie für einen Bericht, der auf einem im integrierten SharePoint-Modus konfigurierten Berichtsserver veröffentlicht wurde, eine vollqualifizierte URL einschließlich der Dateinamenerweiterung (.rdl). Beispielsweise http:// *\<SharePointservername>/\<site>* /Documents/Report1.RDL. Relative Pfade werden nicht unterstützt.  
  
 Weitere Informationen finden Sie unter [Angeben von Pfaden zu externen Elementen &#40;Berichts-Generator und SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) in der [Dokumentation zu Report Builder](https://go.microsoft.com/fwlink/?LinkId=154494) auf msdn.microsoft.com.  
  
 **Diese Parameter zum Ausführen des Berichts verwenden**  
 Fügen Sie eine Liste von Parametern hinzu, die an den Drillthroughbericht übergeben werden sollen. Die Parameternamen müssen mit den für den Zielbericht definierten Parametern übereinstimmen. Verwenden Sie die Schaltflächen **Hinzufügen** und **Löschen** , um Parameter hinzuzufügen oder zu löschen, und sortieren Sie die Liste der Parameter mithilfe des Aufwärts- und Abwärtspfeils.  
  
 **Add**  
 Fügen Sie einen neuen Parameter hinzu, der an den Drillthroughbericht übergeben werden soll.  
  
 **Löschen**  
 Löschen Sie einen Parameter für den Drillthroughbericht.  
  
 **Pfeil nach oben**  
 Verschiebt den Parameter in der Liste nach oben.  
  
 **Pfeil nach unten**  
 Verschiebt den Parameter in der Liste nach unten.  
  
 **Name**  
 Geben Sie den Namen eines im Drillthroughbericht definierten Parameters ein.  
  
 **Wert**  
 Sie können einen Wert zur Übergabe für den benannten Parameter im Drillthroughbericht eingeben oder auswählen. Klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*), um den Ausdruck zu bearbeiten.  
  
 **Auslassen**  
 Wählen Sie diese Option aus, um zu verhindern, dass der Parameter ausgeführt wird. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Zum Aktivieren des Kontrollkästchens klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*) und geben entweder **true** ein oder erstellen einen Ausdruck. Das Kontrollkästchen wird aktiviert, wenn Sie im Dialogfeld **Ausdruck** auf **OK** klicken.  
  
 **Gehe zu Lesezeichen**  
 Wählen Sie diese Option aus, um einen Link zu einem Lesezeichen im aktuellen Bericht zu definieren. Bei Auswahl von **Gehe zu Lesezeichen**wird die folgende zusätzliche Option angezeigt.  
  
 **Lesezeichen auswählen**  
 Sie können die Lesezeichen-ID eingeben oder auswählen, zu der der Bericht springen soll, wenn Benutzer auf den Link klicken. Klicken Sie auf die Ausdrucks Schaltfläche (**FX**), um den Ausdruck zu ändern. Bei der Lesezeichen-ID kann es sich entweder um eine statische ID oder einen Ausdruck handeln, der zu einer Lesezeichen-ID ausgewertet wird. Der Ausdruck kann ein Feld mit einer Lesezeichen-ID enthalten.  
  
 Sie müssen zuerst die Lesezeicheneigenschaft eines Berichtselements festlegen, um einen Link zu einem Lesezeichen zu erstellen. Wählen Sie ein Berichtselement, und geben Sie im Bereich Eigenschaften einen Wert oder einen Ausdruck für die Lesezeichen-ID ein, um die Lesezeicheneigenschaft festzulegen. Beispiel: SalesChart oder 5TopSales.  
  
 **Gehe zu URL**  
 Wählen Sie diese Option aus, um einen Link zu einer Webseite zu definieren. Sie können die URL einer Webseite oder einen Ausdruck, der zur URL einer Webseite ausgewertet wird, eingeben oder auswählen. Klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*), um den Ausdruck zu ändern. Der Ausdruck kann ein Feld mit einer URL enthalten. Bei Auswahl von **Gehe zu URL**wird die folgende zusätzliche Option angezeigt.  
  
 **URL auswählen**  
 Geben Sie die URL des Elements ein. Verwenden Sie für ein Element, das auf einem für den einheitlichen Modus konfigurierten Berichtsserver veröffentlicht wurde, einen vollständigen oder relativen Pfad. Beispielsweise http:// *\<servername>* /Images/image1.jpg. Verwenden Sie für ein Element, das auf einem im integrierten SharePoint-Modus konfigurierten Berichts Server veröffentlicht wurde, eine voll qualifizierte URL (z *\<SharePointservername>/\<site>* . b. http:///Documents/images/image1.jpg).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Berichts-Generator Hilfe zu Dialog Feldern, Bereichen und Assistenten](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Berichts Parameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Fügen Sie einen unter Bericht und Parameter &#40;Berichts-Generator und SSRS hinzu&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
