---
title: Dimensionstyp angeben (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.bidimensionproperties.f1
ms.assetid: 3215282a-532d-4ff2-b721-286f088967fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2f1644c8b123616bb79d328eb1862ec927c6062
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620562"
---
# <a name="specify-dimension-type-dimension-wizard"></a>Dimensionstyp angeben (Dimensions-Assistent)
  Mithilfe der Seite **Dimensionstyp angeben** können Sie den Dimensionstyp definieren und der Dimension spezielle Attributtypen hinzufügen, die mit der ausgewählten Dimension verknüpft sind.  
  
> [!NOTE]  
>  Diese Seite wird nur angezeigt, wenn Sie auf der Seite **Dimensionstyp auswählen** die Option **Standarddimension** ausgewählt haben.  
  
## <a name="options"></a>Tastatur  
 **Dimensionstyp**  
 Wählen Sie den Dimensionstyp für die Dimension aus. In der folgenden Tabelle sind die verfügbaren Dimensionstypen aufgelistet.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Konten**|Kontodimensionen enthalten Daten und Metadaten, die eine Kontenliste darstellen.<br /><br /> Weitere Informationen zu Kontodimensionen finden Sie unter [Erstellen eines Finanzkontos des über- und untergeordneten Typs Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).|  
|**BillOfMaterials**|Stücklisten (oder BOM)-Dimensionen sind reguläre Dimensionen, in denen Daten und Metadaten Informationen zum Bestand sowie zur Produktion darstellen, z. B. Teilelisten für Produkte.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Kanal**|Kanaldimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten Kanalinformationen darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Währung**|Währungsdimensionen enthalten Daten und Metadaten, durch die Währungsinformationen dargestellt werden.<br /><br /> Weitere Informationen zu Währungsdimensionen finden Sie unter [Erstellen einer Währungstypdimension](multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).|  
|**Folgend**|Kundendimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten Kunden- oder Kontaktinformationen darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Geografie**|Geografiedimensionen sind reguläre Dimensionen, in denen Daten und Metadaten geografische Informationen darstellen, z. B. Städte oder Postleitzahlen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Organization**|Organisationsdimensionen sind reguläre Dimensionen, in denen Daten und Metadaten Organisationsinformationen darstellen, z. B. zu Mitarbeitern oder Filialen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Produkte**|Produktdimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten Produktinformationen darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Promotion**|Höherstufungsdimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten Marketinginformationen zur Höherstufung darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Quantitative**|Quantitative Dimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten quantitative Informationen darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Rates**|Ratendimensionen enthalten Daten und Metadaten, die Informationen zu Wechselkursen und der Währungsumrechnung darstellen.|  
|**Regulär**|Reguläre Dimensionen sind der häufigste Dimensionstyp, der in verwendet wird [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Szenario**|Szenariodimensionen sind reguläre Dimensionen, in denen die Daten und Metadaten Informationen zur Planung oder zu strategischen Analysen darstellen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
|**Zeit**|Zeitdimensionen enthalten zeitlich orientierte Daten und Metadaten.<br /><br /> Weitere Informationen zu Zeitdimensionen finden Sie unter [Erstellen einer Datentypdimension](multidimensional-models/database-dimensions-create-a-date-type-dimension.md).|  
|**Hilfsprogramm**|Hilfsprogrammdimensionen sind reguläre Dimensionen, in denen Daten und Metadaten Informationen darstellen, die nicht ohne weiteres mit anderen Dimensionstypen übereinstimmen.<br /><br /> Weitere Informationen zu regulären Dimensionen finden Sie unter [Dimensionstypen](multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md).|  
  
## <a name="dimension-attributes-options"></a>Optionen für Dimensionsattribute  
  
> [!NOTE]  
>  Die Optionen in diesem Abschnitt sind nur verfügbar, wenn der ausgewählte **Dimensionstyp** mit speziellen Attributtypen verknüpft ist. Nicht alle Dimensionstypen sind mit speziellen Attributtypen verknüpft.  
  
 **Darunter**  
 Wählen Sie diese Option aus, um den Attributtyp in die Dimension einzuschließen.  
  
 **Attributtyp**  
 Zeigt den Attributtyp an, der mit dem in **Dimensionstyp** ausgewählten Dimensionstyp verknüpft ist. Weitere Informationen zu Attributtypen finden Sie unter [Type-Element &#40;DimensionAttribute&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-dimensionattribute-assl).  
  
 **Dimensionsattribut**  
 Wählen Sie das Dimensionsattribut aus, dem der Dimensions-Assistent den speziellen Attributtyp zuordnen soll, der in **Attributtyp**angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
