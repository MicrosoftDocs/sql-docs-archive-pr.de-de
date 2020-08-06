---
title: Exportieren als PDF-Datei (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608361"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a>Exportieren als PDF-Datei (Berichts-Generator und SSRS)
  Die PDF-Renderingerweiterung rendert Berichte in einem Dateiformat, das in Adobe Acrobat und anderen PDF-Viewern von Drittanbietern geöffnet werden kann, die das Format PDF 1.3 unterstützen. Obwohl PDF 1.3 mit Adobe Acrobat 4.0 oder höheren Versionen kompatibel ist, wird Adobe Acrobat von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erst ab Version 6 unterstützt. Die Renderingerweiterung erfordert keine Adobe-Software, um Berichte zu rendern. Zum Anzeigen oder Drucken von Berichten im PDF-Format sind allerdings PDF-Viewer wie Adobe Acrobat erforderlich.  
  
 Die PDF-Renderingerweiterung unterstützt ANSI-Zeichen und kann Unicode-Zeichen aus folgenden Zeichensätzen übersetzen: Japanisch, Koreanisch, Chinesisch (traditionell), Chinesisch (vereinfacht), Kyrillisch, Hebräisch und Arabisch, mit bestimmten Einschränkungen. Weitere Informationen zu den Einschränkungen finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md).  
  
 Der PDF-Renderer ist ein Renderer für physische Seiten und weist daher ein Paginierungsverhalten auf, das von dem anderer Renderer, wie HTML und Excel, abweicht. Dieses Thema enthält für das PDF-Rendering spezifische Informationen und beschreibt Ausnahmen von den Regeln.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a>Schriftart Einbettung  
 Wenn möglich, bettet die PDF-Renderingerweiterung die Teilmenge jeder Schriftart ein, die benötigt wird, um den Bericht in der PDF-Datei anzuzeigen. Schriftarten, die im Bericht verwendet werden, müssen auf dem Berichtsserver installiert sein. Wenn der Berichtsserver einen Bericht im PDF-Format generiert, verwendet er zum Erstellen von Zeichenzuordnungen in der PDF-Datei die in der Schriftart gespeicherten Informationen, auf die der Bericht verweist. Ist die Schriftart, auf die verwiesen wird, nicht auf dem Berichtsserver installiert, enthält die resultierende PDF-Datei möglicherweise nicht die richtigen Zuordnungen und wird nicht ordnungsgemäß angezeigt.  
  
 Schriftarten werden in die PDF-Datei eingebettet, wenn die folgenden Bedingungen erfüllt sind:  
  
-   Die Berechtigungen zum Einbetten einer Schriftart werden vom Schriftartersteller gewährt. Installierte Schriftarten verfügen über eine Eigenschaft, die angibt, ob der Schriftartersteller das Einbetten der Schriftart in ein Dokument zulassen möchte. Wenn der Eigenschaftenwert EMBED_NOEMBEDDING ist, wird die Schriftart nicht in die PDF-Datei eingebettet. Weitere Informationen finden Sie unter "TTGetEmbeddingType" auf msdn.microsoft.com.  
  
-   Es handelt sich um eine TrueType-Schriftart.  
  
-   Auf die Schriftarten wird mit sichtbaren Elementen in einem Bericht verwiesen. Wenn auf eine Schriftart mit einem Element verwiesen wird, für das die Hidden-Eigenschaft auf True festgelegt ist, ist die Schriftart zur Anzeige gerenderter Daten nicht erforderlich und nicht in der Datei enthalten. Schriftarten werden nur dann eingebettet, wenn sie für die Anzeige der gerenderten Berichtsdaten benötigt werden.  
  
 Wenn von einer Schriftart alle diese Bedingungen erfüllt werden, wird die Schriftart in die PDF-Datei eingebettet. Wenn eine oder mehrere Bedingungen nicht erfüllt sind, wird die Schriftart nicht in die PDF-Datei eingebettet.  
  
> [!NOTE]  
>  Auch wenn die Bedingungen erfüllt sind, gibt es eine Situation, in der die Schriftarten nicht in die PDF-Datei eingebettet werden. Wenn die verwendeten Schriftarten denen in der PDF-Spezifikation entsprechen, die häufig als Typ 1-Standardschriftarten oder Base 14-Schriftarten bezeichnet werden, werden die Schriftarten bei ANSI-Inhalten nicht eingebettet.  
  
  
  
### <a name="fonts-on-the-client-computer"></a>Schriftarten auf dem Clientcomputer  
 Wenn eine Schriftart in der PDF-Datei eingebettet ist, muss diese Schriftart nicht auf dem Computer installiert sein, der zum Anzeigen des Berichts verwendet wird (dem Clientcomputer), damit der Bericht fehlerfrei angezeigt wird.  
  
 Wenn eine Schriftart nicht in der PDF-Datei eingebettet ist, muss auf dem Clientcomputer die zutreffende Schriftart installiert sein, damit der Bericht fehlerfrei angezeigt wird. Wenn die Schriftart nicht auf dem Clientcomputer installiert ist, werden in der PDF-Datei Fragezeichen (?) für die nicht unterstützten Zeichen angezeigt.  
  
### <a name="verifying-fonts-in-a-pdf-file"></a>Überprüfen von Schriftarten in einer PDF-Datei  
 Unterschiede in der PDF-Ausgabe treten meistens dann auf, wenn eine Schriftart, die keine nicht lateinischen Zeichen unterstützt, in einem Bericht verwendet wird und diesem Bericht später nicht lateinische Zeichen hinzugefügt werden. Sie sollten die PDF-Renderingausgabe sowohl auf dem Berichtsserver als auch auf dem Clientcomputer überprüfen, um sicherzustellen, dass der Bericht richtig gerendert wurde.  
  
 Verlassen Sie sich nicht auf die Vorschau des Berichts oder auf den HTML-Export, da der Bericht möglicherweise durch die automatische Schriftartersetzung der grafischen Entwurfsoberfläche bzw. von Microsoft Internet Explorer ordnungsgemäß angezeigt wird. Wenn auf dem Server Unicode-Symbole fehlen, werden die Zeichen durch Fragezeichen (?) ersetzt. Wenn auf dem Clientcomputer eine Schriftart fehlt, werden Zeichen u. U. durch Kästchen (□) ersetzt.  
  
 Die in die PDF-Datei eingebetteten Schriftarten sind in den Eigenschaften der Schriftart enthalten, die als Metadaten mit der Datei gespeichert werden.  
  
##  <a name="metadata"></a><a name="Metadata"></a> Metadaten  
 Zusätzlich zum Berichtslayout schreibt die PDF-Renderingerweiterung folgende Metadaten in das PDF Document Information Dictionary.  
  
|PDF-Eigenschaft|Erstellt von|  
|------------------|------------------|  
|`Title`|Das `Name`-Attribut des `Report`-RDL-Elements|  
|`Author`|Das `Author`-RDL-Element|  
|`Subject`|Das `Description`-RDL-Element|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Produktname und -Version|  
|`Producer`|Name und Version der Renderingerweiterung|  
|`CreationDate`|Berichtsausführungszeit im `datetime`-PDF-Format|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a>Interaktivität  
 Einige interaktive Elemente werden in PDF unterstützt. Im Folgenden werden spezifische Funktionsweisen beschrieben.  
  
### <a name="show-and-hide"></a>Einblenden und Ausblenden  
 Das dynamische Anzeigen und Ausblenden von Elementen wird im PDF-Format nicht unterstützt. Das PDF-Dokument wird in Übereinstimmung mit dem aktuellen Status aller Elemente im Bericht gerendert. Wenn das Element beispielsweise angezeigt wird, wenn der Bericht zum ersten Mal ausgeführt wird, wird es gerendert. Bilder, die ein- und ausgeblendet werden können, werden nicht gerendert, wenn sie beim Exportieren des Berichts ausgeblendet sind.  
  
### <a name="document-map"></a>Dokumentstruktur  
 Wenn im Bericht Dokumentstrukturbezeichnungen vorhanden sind, wird der PDF-Datei eine Dokumentgliederung hinzugefügt. Jede Dokumentstrukturbezeichnung wird als Eintrag in der Dokumentgliederung und somit auch im Bericht angezeigt. In Acrobat wird der Dokumentgliederung nur dann ein Ziellesezeichen hinzugefügt, wenn die Seite, auf der sie sich befindet, gerendert wird.  
  
 Wenn nur eine einzelne Seite gerendert wird, wird keine Dokumentgliederung hinzugefügt. Die Dokumentstruktur wird entsprechend der Schachtelungsebene im Bericht hierarchisch angelegt. Auf die Dokument Gliederung kann in Acrobat auf der Registerkarte "Lesezeichen" zugegriffen werden. Wenn Sie auf einen Eintrag innerhalb der Dokument Gliederung klicken, wechselt das Dokument zum Lesezeichen.  
  
### <a name="bookmarks"></a>Lesezeichen  
 Lesezeichen werden beim PDF-Rendering nicht unterstützt.  
  
### <a name="drillthrough-links"></a>Drillthroughlinks  
 Drillthroughlinks werden beim PDF-Rendering nicht unterstützt. Die Drillthroughlinks werden nicht als klickbare Links gerendert, und Drillthroughberichte können keine Verbindung mit dem Ziel des Drillthroughs herstellen.  
  
### <a name="hyperlinks"></a>Hyperlinks  
 Links in Berichten werden als durch Klicken aktivierbare Links in der PDF-Datei gerendert. Beim Klicken auf den Link öffnet Acrobat den Standardbrowser des Clients und navigiert zur Link-URL.  
  
  
  
##  <a name="compression"></a><a name="Compression"></a>Komprimi  
 Die Bildkomprimierung basiert auf dem ursprünglichen Dateityp des Bilds. Die PDF-Renderingerweiterung komprimiert PDF-Dateien standardmäßig.  
  
 Damit die Bildkomprimierung in der PDF-Datei möglichst erhalten bleibt, werden JPEG-Bilder im JPEG- und alle anderen Bildtypen im BMP-Format gespeichert.  
  
> [!NOTE]  
>  PDF-Dateien bieten keine Unterstützung für das Einbetten von PNG-Bildern.  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a>Geräte Informationseinstellungen  
 Sie können einige Standardeinstellungen für diesen Renderer ändern, indem Sie die Geräteinformationseinstellungen ändern. Weitere Informationen finden Sie unter [PDF Device Information Settings](../pdf-device-information-settings.md).  
  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhaltensweisen &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichts Elementen &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
