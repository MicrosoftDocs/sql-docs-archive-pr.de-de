---
title: Rendern von Berichtselementen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 99ebb4dc-41cc-42ac-82dd-a2b0e31155a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4e0b1dabee096cfbaab53227926633f8d7a3697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617730"
---
# <a name="rendering-report-items-report-builder-and-ssrs"></a>Rendern von Berichtselementen (Berichts-Generator und SSRS)
  Die Zahl, die Größe und der Ort der Berichtselemente beeinflussen, wie die Renderer den Text des Berichts paginieren. Unten finden Sie eine Beschreibung zum Rendering verschiedener Berichtselemente.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="overlapping-report-items"></a>Überlappende Berichtselemente  
 Überlappende Berichtselemente werden in HTML, MHTML, Word, Excel, in der Vorschau oder im Berichts-Viewer nicht unterstützt. Wenn überlappende Elemente vorhanden sind, werden sie verschoben. Die folgenden Regeln werden auf sich überschneidende Berichtselemente angewendet:  
  
-   Wenn die vertikale Überschneidung von Berichtselementen größer ist, wird eines der überlappenden Elemente nach rechts verschoben. Das am weitesten links stehende Element bleibt, wo es positioniert ist.  
  
-   Wenn die horizontale Überschneidung von Berichtselementen größer ist, wird eines der überlappenden Elemente nach unten verschoben. Das am weitesten oben stehende Element bleibt, wo es positioniert ist.  
  
-   Wenn die vertikale und horizontale Überschneidung gleich sind, wird eines der überlappenden Elemente nach rechts verschoben. Das am weitesten links stehende Element bleibt, wo es positioniert ist.  
  
-   Wenn ein Element verschoben werden muss, um eine Überschneidung zu korrigieren, werden nebeneinander liegende Berichtselemente nach unten und/oder nach rechts verschoben, um einen Mindestabstand zwischen dem Element und den Berichtselementen mit Ende darüber und/oder links davon einzuhalten. Nehmen Sie beispielsweise an, dass sich zwei Berichtselemente vertikal überlappen und sich ein drittes Berichtselement 2 Zoll rechts davon befindet. Wenn das überlappende Berichtselement nach rechts verschoben wird, bewegt sich auch das dritte Berichtselement nach rechts, um den Abstand von 2 Zoll zum Berichtselement auf der linken Seite beizubehalten.  
  
 Überlappende Berichtselemente werden in Formaten mit hartem Seitenumbruch unterstützt, unter anderem beim Druck.  
  
## <a name="visibility-and-report-items"></a>Sichtbarkeit und Berichtselemente  
 Berichtselemente können standardmäßig aus- und eingeblendet oder mithilfe von Ausdrücken bedingt aus- und eingeblendet werden. Optional kann die Sichtbarkeit umgeschaltet werden, indem auf ein anderes Berichtselement geklickt wird.  
  
 Die folgenden Sichtbarkeitsregeln sind beim Rendern von Berichtselementen gültig:  
  
-   Wenn ein Berichtselement und sein Inhalt immer ausgeblendet sind (es ist nicht basierend auf einem Ausdruck ausgeblendet, und seine Sichtbarkeit kann nicht durch Klicken auf ein anderes Berichtselement umgeschaltet werden), werden andere Berichtselemente rechts davon oder unterhalb nicht verschoben, um Lücken zu füllen. Wenn beispielsweise ein Rechteck und das Bild darin ausgeblendet sind, wird das Berichtselement, das auf der rechten Seite des Rechtecks beginnt, nicht nach links verschoben und füllt die scheinbare Lücke nicht aus. Der vom Rechteck eingenommene Platz wird beibehalten.  
  
-   Wenn ein Berichtselement und sein Inhalt bedingt ausgeblendet sind (es ist nicht basierend auf einem Ausdruck ausgeblendet, und seine Sichtbarkeit kann durch Klicken auf ein anderes Berichtselement umgeschaltet werden), werden andere Berichtselemente rechts davon oder unterhalb nach links verschoben, um den Platz des verborgenen Elements einzunehmen.  
  
-   Wenn die Sichtbarkeit eines Berichtselements und seines Inhalts durch Klicken auf ein anderes Berichtselement umgeschaltet werden kann, wird die Paginierung nur beim ersten Anzeigen des Berichtselements und seines Inhalts angepasst, um diese aufzunehmen.  
  
## <a name="keeping-report-items-together-on-a-single-page"></a>Beibehalten von Berichtselementen auf einer einzigen Seite  
 Viele Berichtselemente innerhalb eines Berichts können implizit oder explizit auf einer Seite beibehalten werden, indem die Eigenschaften zum Beibehalten bei der Gruppe oder zum Zusammenhalten festgelegt werden. Berichtselemente werden immer auf derselben Seite gerendert, wenn das Berichtselement keine logischen Seitenumbrüche enthält und kleiner ist als der verwendbare Seitenbereich. Wenn ein Berichtselement nicht vollständig auf die Seite passt, auf der es normalerweise beginnen würde, wird vor dem Berichtselement ein harter Seitenumbruch eingefügt, sodass es auf der nächsten Seite angezeigt wird. Bei Renderern mit weichem Seitenumbruch wird die Seite größer, um das Berichtselement unterzubringen.  
  
 Wenn das Berichtselement immer ausgeblendet ist, werden die Regeln zum Zusammenhalten von Elementen ignoriert.  
  
 Die folgenden Elemente werden immer zusammengehalten:  
  
-   Bilder.  
  
-   Linien.  
  
-   Diagramme, Messgeräte und Zuordnungen.  
  
-   Eine einzelne Zeile in einem Datenbereich, der separat auf einer anderen Seite angezeigt wird, durch Auswählen der Option zum Beibehalten bei der Gruppe. So wird implizit eine einzelne Zeile mit mindestens einer Instanz der Gruppe zusammengehalten, sodass die Zeile nicht einzeln steht. Sie können diese Option in einem Datenbereich oder in einer Gruppe festlegen.  
  
-   Kopfzeilenbereich eines Datenbereichs.  
  
-   Kopfzeilenbereich eines Datenbereichs und die erste Zeile der Daten.  
  
-   Berichtselemente, die in einem Tablix-Datenbereich ein- und ausgeschaltet werden können.  
  
### <a name="priority-order"></a>Prioritätsreihenfolge.  
 Aufgrund der Größenbeschränkungen der Seite können Konflikte zwischen den Regeln zum Zusammenhalten von Berichtselementen entstehen. Wenn Konflikte auftreten, wird die folgende Prioritätsreihenfolge verwendet, um Elemente beim Rendern zusammenzuhalten:  
  
-   Linien, Diagramme und Bilder.  
  
-   Fenster und verwaistes Steuerelement.  
  
-   Wiederholte Spaltenkopfzeilen und Zeilenheader.  
  
     Kopfzeilen haben Vorrang gegenüber Fußzeilen. Innere wiederholte Gruppen haben Priorität über äußere Gruppen. Elemente mit der Eigenschaft `RepeatWith`, die näher am Zieldatenbereich liegen, haben Priorität über Elemente, die weiter vom Datenbereich entfernt liegen.  
  
-   Kleine Berichts Elemente, z. b. Textfelder oder Rechtecke, mit einer expliziten keepzusammeneigenschaft, die auf festgelegt ist `true` .  
  
-   Große Berichts Elemente, wie z. b. unter Berichte oder ein nicht Inneres Tablix--Element, bei dem eine explizite keepzusammeneigenschaft auf festgelegt ist `true` .  
  
-   Tablix-Datenbereiche mit einer expliziten keepzusammeneigenschaft, die auf festgelegt ist `true` .  
  
### <a name="subreports"></a>Unterberichte  
 Ein Unterbericht wird als Rechteck mit einem anderen Bericht gerendert, der in einer separaten Berichts-RDL-Datei definiert ist. Eine Unterberichtsdatei muss auf einem Berichtsserver veröffentlicht werden, bevor der übergeordnete Bericht darauf zugreifen kann.  
  
 Beim Rendern von Unterberichten gelten folgende Regeln:  
  
-   Unterberichte können so groß werden wie der definierte Text in der RDL-Datei, die den Unterbericht definiert. Wenn die RDL-Datei für den Unterbericht beispielsweise angibt, dass der Text des Unterberichts 5 Zoll breit ist, wird der Unterbericht im übergeordneten Bericht 5 Zoll breit sein.  
  
-   Unterberichte erben Spalteneinstellungen vom übergeordneten Bericht. Spalteneinstellungen, die in der ursprünglichen RDL definiert werden, werden immer ignoriert.  
  
-   Nur der Text des Unterberichts wird gerendert. Kopf- und Fußzeilenbereiche, die in der RDL-Datei des Unterberichts definiert werden, werden nicht gerendert, wenn der Unterbericht im übergeordneten Bericht gerendert wird.  
  
-   Unterberichte verfügen über eine explizite KeepTogether-Eigenschaft. Wenn `true` festgelegt ist, werden, wenn möglich, alle Elemente im Unterbericht auf einer Seite zusammengehalten.  
  
-   Wenn ein Unterbericht nicht aufgeführt werden kann, wird er im Bericht als Textfeld mit einer Fehlermeldung angezeigt. Die für den Unterbericht angewendeten Stileigenschaften werden stattdessen auf das Textfeld angewendet.  
  
-   Wenn ein Unterbericht durch einen Seitenumbruch geteilt ist, steuert die Einstellung **Rahmen an Seitenumbruch auslassen** , ob die Rahmen auf dem Unterbericht geschlossen oder offen sind.  
  
 Weitere Informationen zu Unterberichten finden Sie unter [Unterberichte (Berichts-Generator und SSRS)](subreports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
