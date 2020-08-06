---
title: Create-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 407f16c3898e56cd393e36c39ed799b83e0092ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695018"
---
# <a name="create-element-dta"></a>Create-Element (DTA)
  Enthält Informationen zu den Indizes, Statistiken oder Heapstrukturen in einer benutzerspezifischen Konfiguration.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich pro physischem Entwurfsstrukturtyp (Indizes, Statistiken oder Heapstrukturen).|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Recommendation-Element &#40;DTA&#41;](recommendation-element-dta.md)|  
|**Untergeordnete Elemente**|[Index-Element &#40;DTA&#41;](index-element-dta.md)<br /><br /> `Statistics`-Element (Weitere Informationen finden Sie unter [Datenbankoptimierungsratgeber XML-Schema](https://schemas.microsoft.com/sqlserver/) )<br /><br /> `Heap`-Element (Weitere Informationen finden Sie unter [Datenbankoptimierungsratgeber XML-Schema](https://schemas.microsoft.com/sqlserver/) )|  
  
## <a name="remarks"></a>Bemerkungen  
 Dieses Element hat den Namen **CreateTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Es wird zum Erstellen von Indizes, Statistiken und Heapstrukturen für eine benutzerspezifische Konfiguration verwendet. Dieses `Create`-Element ist nicht mit den anderen Typen identisch, mit denen Sichten (`CreateViewType`) oder Partitionierungen (`CreatePType`) erstellt werden können. Informationen zu diesen anderen Elementtypen finden Sie im [Datenbankoptimierungsratgeber XML-Schema](https://schemas.microsoft.com/sqlserver/) `Create` .  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
