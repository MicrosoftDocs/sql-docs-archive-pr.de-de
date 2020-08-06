---
title: Pfad Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609296"
---
# <a name="path-properties"></a>Pfadeigenschaften
  Die Datenfluss Objekte im- [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Objektmodell verfügen über allgemeine Eigenschaften und benutzerdefinierte Eigenschaften auf der Ebene der Komponente, Eingaben und Ausgaben sowie Eingabe-und Ausgabespalten. Viele Eigenschaften verfügen über schreibgeschützte Werte, für die zur Laufzeit eine Zuweisung über die Datenfluss-Engine erfolgt.  
  
 In diesem Thema werden die benutzerdefinierten Eigenschaften der Pfade, die Datenflussobjekte verbinden, aufgelistet und beschrieben.  
  
## <a name="path-properties"></a>Pfadeigenschaften  
 Im [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objektmodell implementiert ein Pfad, der Komponenten im Datenfluss verbindet, die Schnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 Die folgende Tabelle beschreibt die konfigurierbaren Eigenschaften der Pfade in einem Datenfluss. Die Datenfluss-Engine weist auch zusätzlichen schreibgeschützten Eigenschaften, die nicht hier aufgelistet sind, Werte zu.  
  
|Eigenschaftenname|Datentyp|BESCHREIBUNG|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Ganze Zahl (Enumeration)|Ein Wert, der angibt, ob eine Anmerkung mit dem Pfad auf der Designeroberfläche angezeigt werden soll. Die möglichen Werte sind `AsNeeded`, `SourceName`, `PathName` und `Never`. Standardwert: `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|Die dem Pfad zugeordnete Eingabe.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|Die dem Pfad zugeordnete Ausgabe.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Integration Services-Pfade](data-flow/integration-services-paths.md)   
 [Allgemeine Eigenschaften](../../2014/integration-services/common-properties.md)   
 [Benutzerdefinierte Eigenschaften der Transformation](data-flow/transformations/transformation-custom-properties.md)   
 [Data Flow-Eigenschaften, die mithilfe von Ausdrücken festgelegt werden können](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
