---
title: Aktions Formular-Editor (Registerkarte Aktionen, Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08ed03e843ba206f22969f9ada0da5a590a5811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609550"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Aktionsformular-Editor (Registerkarte 'Aktionen', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Im Bereich Aktionsformular-Editor auf der Registerkarte **Aktionen** im Cube-Designer können Sie Standardaktionen erstellen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Aktion ein.  
  
 **Aktionsziel**  
 Erweitern Sie diese Option, um die Optionen **Zieltyp** und **Zielobjekt** anzuzeigen.  
  
 **Zieltyp**  
 Wählen Sie den Typ des Objekts aus, dem die Aktion zugeordnet werden soll. Der Server gibt nur jene Aktionen an den Client zurück, die auf das Objekt vom angegebenen Typ angewendet werden. Die Aktion ist für den Client verfügbar, wenn die **Bedingung** erfüllt ist und die in der folgenden Tabelle angegebenen Objekte ausgewählt sind.  
  
|Wert|Ausgewähltes Objekt|  
|-----------|---------------------|  
|Attributelemente|Ein Element wird aus einer Ebene ausgewählt, die auf dem Attribut unter **Zielobjekt**basiert.|  
|Zellen|Die benannte Menge in **Zielobjekt** wird ausgewählt. Wählen Sie **Alle Zellen** aus, um alle Zellen im Cube auszuwählen.|  
|Cube|Der Cube in **Zielobjekt** wird ausgewählt. Wählen Sie CURRENTCUBE aus, um den aktuellen Cube zu verwenden.<br /><br /> Hinweis: Das Verwenden von CURRENTCUBE stellt eine zusätzliche Portabilität für Fälle bereit, in denen der Cube umbenannt oder die Aktion in andere Cubes kopiert wird. Es wird empfohlen, zum Darstellen des aktuellen Cubes CURRENTCUBE zu verwenden.|  
|Dimensionselemente|Ein Element der Dimension in **Zielobjekt** wird ausgewählt.|  
|Hierarchy|Die Hierarchie in **Zielobjekt** wird ausgewählt.|  
|Hierarchieelemente|Ein Element innerhalb der Hierarchie in **Zielobjekt** wird ausgewählt.|  
|Ebene|Die Ebene in **Zielobjekt** wird ausgewählt.|  
|Ebenenelemente|Ein Element innerhalb der Ebene in **Zielobjekt** wird ausgewählt.|  
  
 **Zielobjekt**  
 Wählen Sie das Objekt aus, dem die Aktion zugeordnet werden soll. Die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz gibt nur die Aktionen an den Client zurück, die auf das ausgewählte Objekt angewendet werden. Die Liste der verfügbaren Objekte wird durch die Auswahl unter **Zieltyp**eingeschränkt.  
  
 **Bedingung (Optional)**  
 Geben Sie einen MDX-Ausdruck (Multidimensional Expressions) ein, der eine optionale Bedingung für das Verwenden in Verbindung mit **Zielobjekt**beschreibt, wodurch die Verfügbarkeit der Aktion weiter eingeschränkt wird. Der Ausdruck muss einen booleschen Wert zurückgeben, der mit "True" anzeigt, dass die Aktion verfügbar ist.  
  
 Ziehen Sie ausgewählte Elemente aus dem Bereich **Berechnungstools** auf diese Option, um die MDX-Syntax für das ausgewählte Element einzuschließen.  
  
 **Aktionsinhalt**  
 Erweitern Sie diese Option, um die Optionen **Typ** und **Aktionsausdruck** anzuzeigen.  
  
 **Type**  
 Wählen Sie den Typ der Aktion aus, der verwendet werden soll, wenn die Aktion ausgeführt wird. Folgende Aktionstypen sind verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Dataset|Gibt einen MDX-Ausdruck (Multidimensional Expressions) zurück, der ein mehrdimensionales Dataset darstellt, das von der Clientanwendung ausgeführt und angezeigt wird.|  
|Proprietär|Gibt eine proprietäre Zeichenfolge zurück, die von Clientanwendungen interpretiert werden kann, die der Einstellung **Anwendung** für diese Aktion zugeordnet sind.|  
|Rowset|Gibt einen MDX-Ausdruck (Multidimensional Expressions) zurück, der ein tabellarisches Rowset darstellt, das von der Clientanwendung ausgeführt und angezeigt wird.|  
|Anweisung|Gibt eine Befehlszeichenfolge zurück, die von der Clientanwendung ausgeführt wird.|  
|URL|Gibt eine URL-Zeichenfolge (Uniform Resource Location) zurück, die von der Clientanwendung normalerweise mit einem Internetbrowser geöffnet wird.|  
  
 Weitere Informationen zu Aktionstypen finden Sie unter [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).  
  
 **Aktionsausdruck**  
 Geben Sie den MDX-Ausdruck (Multidimensional Expressions) ein, der die Zeichenfolge zurückgibt, die von der Aktion an die Clientanwendung zwecks Ausführung zurückgegeben wurde.  
  
 **Zusätzliche Eigenschaften**  
 Erweitern Sie die Option, um die Optionen **Aufruf**, **Anwendung**, **Beschreibung**, **Beschriftung**und **Beschriftung ist MDX** anzuzeigen.  
  
 **Aufruf**  
 Wählen Sie die Einstellung aus, durch die angegeben wird, wann die Aktion ausgeführt werden soll.  
  
> [!NOTE]  
>  Diese Option stellt einer Clientanwendung nur eine Empfehlung für den Ausführungszeitpunkt einer Aktion zur Verfügung. Sie steuert nicht direkt den Aufruf der Aktion.  
  
 Die folgende Tabelle beschreibt die verfügbaren Einstellungen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|Batch|Die Aktion sollte als Teil eines Batchvorgangs oder eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Tasks ausgeführt werden.|  
|Interactive|Die Aktion wird ausgeführt, wenn der Benutzer die Aktion aufruft.|  
|Beim Öffnen|Die Aktion wird ausgeführt, wenn der Cube erstmalig geöffnet wird.|  
  
 **Anwendung**  
 Geben Sie den Namen der Anwendung ein, die die Zeichenfolge interpretieren kann, die von **Aktionsausdruck**zurückgegeben wurde.  
  
 Sie können diese Option auch verwenden, um zu ermitteln, welche Clientanwendung diese Aktion am häufigsten verwendet, oder um entsprechende Symbole neben der Aktion in einem Popupmenü anzuzeigen.  
  
> [!NOTE]  
>  Diese Option stellt nur eine Empfehlung für eine Clientanwendung bereit, die angibt, welche Clientanwendung eine Aktion ausführen soll. Sie steuert nicht direkt den Zugriff auf die Aktion. Clientanwendungen sollten alle Aktionen ausblenden, die anderen Clientanwendungen zugeordnet sind.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der Aktion ein.  
  
 **Caption**  
 Geben Sie die Beschriftung ein, die für die Aktion in der Clientanwendung angezeigt wird, wenn **Beschriftung ist MDX** auf **FALSE**festgelegt ist.  
  
 Geben Sie den MDX-Ausdruck (Multidimensional Expressions) ein, der eine Zeichenfolge für die Beschriftung zurückgibt, wenn **Beschriftung ist MDX** auf **TRUE**festgelegt ist.  
  
 **Beschriftung ist MDX**  
 Wählen Sie **FALSE** aus, um anzuzeigen, dass **Beschriftung** eine Literalzeichenfolge enthält, die eine Beschriftung darstellt, welche für die Aktion in der Clientanwendung angezeigt werden soll.  
  
 Wählen Sie **True** aus, um anzuzeigen, dass **Beschriftung** einen MDX-Ausdruck enthält, der eine Zeichenfolge mit einer Beschriftung zurückgibt, die für die Aktion in der Clientanwendung angezeigt werden soll. Der MDX-Ausdruck muss aufgelöst werden, bevor die Aktion an die Clientanwendung zurückgegeben wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktionen &#40;Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Registerkarte "Aktionen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Aktions Planer &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Berechnungs Tools &#40;Registerkarte "Aktionen", Cube-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Drillthrough-Aktions Formular-Editor &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Berichts Aktions Formular-Editor &#40;Registerkarte Aktionen, Cube-Designer&#41; &#40;Analysis Services-Mehrdimensionale Daten&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
