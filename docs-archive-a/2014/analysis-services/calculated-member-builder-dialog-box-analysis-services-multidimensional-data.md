---
title: Generator für berechnete Elemente (Dialog Feld, Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610295"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Generator für berechnete Elemente' (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie das Dialogfeld **Generator für berechnete Elemente** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um ein berechnetes Element zu erstellen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Name**|Geben Sie den Namen des berechneten Elements ein.|  
|**Übergeordnete Hierarchie**|Wählen Sie die übergeordnete Hierarchie aus, in der das berechnete Element erstellt werden soll.|  
|**Übergeordnetes Element**|Diese Option ist aktiviert, wenn Sie eine übergeordnete Hierarchie (außer der `Measures`-Dimension) mit mehreren Ebenen auswählen. Klicken Sie auf die Schaltfläche (**..**.), um ein übergeordnetes Element auszuwählen. Das übergeordnete Element bestimmt den Speicherort des berechneten Elements in der Dimensionsstruktur.|  
|**Ausdruck**|Geben Sie den MDX-Ausdruck ein, der verwendet wird.|  
|**Überprüfung**|Klicken Sie auf **Überprüfen** , um den in **Ausdruck**definierten MDX-Ausdruck zu testen.|  
|**Metadaten**|Zeigt die Metadaten für das aktuelle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt an, das in den in **Ausdruck**definierten MDX-Ausdruck eingeschlossen werden kann.<br /><br /> Sie können die MDX-Syntax für das ausgewählte Element kopieren, indem Sie mit der rechten Maustaste auf das Element klicken und die Option **Kopieren**auswählen oder indem Sie das ausgewählte Element auf **Ausdruck**ziehen.|  
|**Funktionen**|Zeigt die für die aktuelle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz verfügbaren MDX-Funktionen an. Die aufgelisteten Elemente werden aus dem MDSCHEMA_FUNCTIONS-Schemarowset abgerufen.<br /><br /> Sie können die MDX-Syntax für das ausgewählte Element kopieren, indem Sie mit der rechten Maustaste auf das Element klicken und die Option **Kopieren**auswählen oder indem Sie das ausgewählte Element auf **Ausdruck**ziehen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Multidimensional Expressions &#40;MDX&#41; – Referenz](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
