---
title: Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aeb99e725c5c61a6dc66c83e53afbc43b1224582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616409"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS)
  Wenn Sie rekursive Daten anzeigen möchten, bei denen die Beziehung zwischen übergeordnetem und untergeordnetem Element durch Felder im Dataset dargestellt wird, können Sie den Datenbereichs Gruppen Ausdruck basierend auf dem untergeordneten Feld festlegen und die übergeordnete Eigenschaft basierend auf dem übergeordneten Feld festlegen.  
  
 Eine hierarchische Anzeige von Daten wird häufig für rekursive Hierarchiegruppen verwendet, z. B. für Angestellte in einem Unternehmensdiagramm. Das Dataset enthält eine Liste mit Mitarbeitern und Managern, wobei die Namen der Manager auch in der Mitarbeiterliste enthalten sind.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Erstellen von rekursiven Hierarchien  
 Sie müssen den Gruppenausdruck auf das Feld festlegen, das die untergeordneten Daten enthält, und die übergeordnete Eigenschaft der Gruppe auf das Feld, das die übergeordneten Daten enthält, um eine rekursive Hierarchie in einem Tablix-Datenbereich zu erstellen. Legen Sie z.B. für ein Dataset, das Felder für die Mitarbeiter-ID und die Manager-ID enthält (wobei die Mitarbeiter an die Manager berichten) den Gruppenausdruck auf die Mitarbeiter-ID und die übergeordnete Eigenschaft auf die Manager-ID fest.  
  
 Eine Gruppe, die als rekursive Hierarchie definiert ist (also eine Gruppe, die die übergeordnete Eigenschaft verwendet), kann nur über einen einzelnen Gruppenausdruck verfügen. Mit der `Level`-Funktion können Sie die Auffüllung in Textfeldern bestimmen, um die Mitarbeiternamen entsprechend ihrer Ebene in der Hierarchie einzurücken.  
  
 Weitere Informationen finden Sie unter [Hinzufügen oder Löschen einer Gruppe in einem Datenbereich (Berichts-Generator und SSRS)](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) und [Erstellen einer rekursiven Hierarchiegruppe (Berichts-Generator und SSRS)](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Aggregatfunktionen zur Unterstützung der Rekursion  
 Sie können Reporting Services-Aggregatfunktionen verwenden, die den Parameter *Rekursiv* akzeptieren, um Zusammenfassungsdaten für eine rekursive Hierarchie zu berechnen. Die folgenden Funktionen akzeptieren `Recursive` als Parameter: [Sum](report-builder-functions-sum-function.md), [AVG](report-builder-functions-avg-function.md), count, Count [,](report-builder-functions-countdistinct-function.md) [count](report-builder-functions-count-function.md), [zähltrows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [var](report-builder-functions-var-function.md)und [VarP](report-builder-functions-varp-function.md). Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
