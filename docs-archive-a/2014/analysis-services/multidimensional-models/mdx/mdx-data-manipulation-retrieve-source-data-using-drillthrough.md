---
title: Verwenden von Drillthrough zum Abrufen von Quelldaten (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5601a3ddfa7075ed53330e12c260af88648db990
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618356"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a>Verwenden von DRILLTHROUGH zum Abrufen von Quelldaten (MDX)
  Die [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)-Anweisung wird in MDX (Multidimensional Expressions) dazu verwendet, ein Rowset aus den Quelldaten für eine Cubezelle abzurufen.  
  
 Damit eine `DRILLTHROUGH`-Anweisung für einen Cube ausgeführt werden kann, muss für diesen Cube eine Drillthroughaktion definiert sein. Um eine Drillthroughaktion zu definieren, klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]im Cube-Designer im **Aktionsbereich** auf der Symbolleiste auf **Neue Drillthroughaktion**. In der neuen Drillthroughaktion geben Sie den Aktionsnamen, das Ziel, die Bedingung und die Spalten an, die von der `DRILLTHROUGH`-Anweisung zurückgegeben werden sollen.  
  
## <a name="drillthrough-statement-syntax"></a>Syntax der DRILLTHROUGH-Anweisung  
 Die `DRILLTHROUGH`-Anweisung hat folgende Syntax:  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 Die `SELECT`-Klausel kennzeichnet die Cubezelle, die die Quelldaten enthält, die abgerufen werden sollen. Diese `SELECT`-Klausel ist mit einer normalen MDX-`SELECT`-Anweisung identisch, mit dem einen Unterschied, dass in der `SELECT`-Klausel nur ein Element auf jeder Achse angegeben werden kann. Wenn mehr als ein Element auf einer Achse angegeben wird, tritt ein Fehler auf.  
  
 Die `<Max_Rows>` -Syntax gibt die maximale Anzahl der Zeilen in jedem zurückgegebenen Rowset an. Wenn der OLE DB-Anbieter, der für die Verbindung mit der Datenquelle verwendet wird, `DBPROP_MAXROWS` nicht unterstützt, wird die `<Max_Rows>`-Einstellung ignoriert.  
  
 Die `<First_Rowset>` -Syntax identifiziert die Partition, deren Rowset zuerst zurückgegeben wird.  
  
 Die `<Return_Columns>` -Syntax identifiziert die zugrunde liegenden Datenbankspalten, die zurückgegeben werden sollen.  
  
## <a name="drillthrough-statement-example"></a>Beispiel für die DRILLTHROUGH-Anweisung  
 Das folgende Beispiel zeigt die Verwendung der `DRILLTHROUGH`-Anweisung: In diesem Beispiel fragt die DRILLTHROUGH-Anweisung die Blätter der Dimensionen Store, Product und Time entlang der Stores-Dimension (die Slicerachse) ab und gibt dann die Department-Measuregruppe, die Abteilungs-ID (Department ID) und den Vornamen der/des Angestellten zurück.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten von Daten &#40;MDX&#41;](mdx-data-manipulation-manipulating-data.md)  
  
  
