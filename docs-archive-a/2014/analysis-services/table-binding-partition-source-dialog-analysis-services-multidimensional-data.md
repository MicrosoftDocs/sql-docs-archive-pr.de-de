---
title: Tabellen Bindungs Details (Dialog Feld ' Partitions Quelle ') (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10845e18a2b7c74a8ed3aeec42f710b9706dc94a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616718"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Tabellenbindungsdetail (Dialogfeld 'Partitionsquelle') (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Option **Tabellenbindung** im Dialogfeld **Partitionsquelle** können Sie die Faktentabelle angeben, die die Daten für die Partition bereitstellt. Sie können diesen Bereich anzeigen, indem Sie im Dialogfeld **Partitionsquelle** unter **Bindungstyp** die Option **Tabellenbindung** auswählen.  
  
## <a name="options"></a>Tastatur  
 **Measuregruppe**  
 Zeigt die Measuregruppe für diese Partition an.  
  
 **Suchen in**  
 Wählen Sie die Datenquelle oder Datenquellensicht mit den Quelltabellen für die Partition aus. Die durch die ausgewählte Measuregruppe verwendete Datenquellensicht wird standardmäßig ausgewählt.  
  
 **Tabellenfilter**  
 Geben Sie die Zeichenfolge ein, die verwendet werden soll, um die unter **Verfügbare Tabellen**angezeigten Tabellen auf der Grundlage des Tabellennamens einzuschränken.  
  
 **Suchen nach Tabellen**  
 Wählen Sie diese Option aus, um die Liste der Tabellen unter **Verfügbare Tabellen**zu aktualisieren und die Liste weiter einzuschränken, falls in **Tabellenfilter**eine Zeichenfolge eingegeben wurde.  
  
 **Verfügbare Tabellen**  
 Klicken Sie auf die Option, um die Tabelle auszuwählen, die als Quelltabelle für die Partition verwendet werden soll.  
  
 Wenn in **Tabellenfilter**kein Filter angegeben wird, werden alle Tabellen aufgelistet, die in der unter **Suchen in** angegebenen Datenquelle oder Datenquellensicht enthalten sind, und deren Struktur der Faktentabelle gleicht, die von der unter **Measuregruppe** angegebenen Measuregruppe verwendet wird.  
  
 Wenn in **Tabellenfilter**ein Filter angegeben wird, wird die Liste weiter eingeschränkt, indem der Filter mit den Tabellennamen verglichen wird, die die oben genannten Kriterien erfüllen. Nur die Tabellen, die die in **Tabellenfilter** angegebene Zeichenfolge enthalten, werden angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld ' Partitions Quelle ' &#40;Analysis Services Mehrdimensionale Daten&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
