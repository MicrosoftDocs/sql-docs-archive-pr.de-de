---
title: Verwalten von Caches (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616773"
---
# <a name="managing-caches-xmla"></a>Verwalten von Caches (XMLA)
  Sie können den [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) -Befehl in XML for Analysis (XMLA) verwenden, um den Cache einer angegebenen Dimension oder Partition zu löschen. Das Löschen des Caches zwingt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , den Cache für dieses Objekt neu zu erstellen.  
  
## <a name="specifying-objects"></a>Angeben von Objekten  
 Die [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Eigenschaft des- `ClearCache` Befehls kann nur einen Objekt Verweis für eines der folgenden Objekte enthalten. Bei einem Objektverweis, der sich nicht auf eines der folgenden Objekte bezieht, tritt ein Fehler auf:  
  
 Datenbank  
 Löscht den Cache für alle Dimensionen und Partitionen, die in der Datenbank enthalten sind.  
  
 Dimension  
 Löscht den Cache für die angegebene Dimension.  
  
 Cube  
 Löscht den Cache für alle Partitionen, die in den Measuregruppen für den Cube enthalten sind.  
  
 Measuregruppe  
 Löscht den Cache für alle Partitionen, die in der Measuregruppe enthalten sind.  
  
 Partition  
 Löscht den Cache für die angegebene Partition.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
