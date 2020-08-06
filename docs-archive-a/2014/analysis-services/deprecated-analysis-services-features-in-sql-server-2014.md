---
title: Veraltete Analysis Services Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- deprecated features [Analysis Services]
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b3de78dfea70196e0c2855167e5ce2fda2369a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718895"
---
# <a name="deprecated-analysis-services-features-in-sql-server-2014"></a>Veraltete Analysis Services-Funktionen in SQL Server 2014
  In diesem Thema werden die als veraltet markierten Funktionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]noch verfügbar sind. Diese Funktionen werden voraussichtlich in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]entfernt. Als veraltet markierte Funktionen sollten in neuen Anwendungen nicht verwendet werden.  
  
## <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Funktionen, die in der nächsten Version von SQL Server nicht unterstützt werden  
 Die folgenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Funktionen werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr unterstützt. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, in denen diese Funktionen zurzeit verwendet werden.  
  
|Category|Als veraltet markierte Funktion|Ersatz|  
|--------------|------------------------|-----------------|  
|MDX-Funktion|CalculationPassValue-Funktion|Keine. Die OLAP-Engine verwaltet den Berechnungsdurchlauf. Diese Funktion wird nicht mehr benötigt.|  
|MDX-Funktion|CalculationCurrentPass-Funktion|Keine. Die OLAP-Engine verwaltet den Berechnungsdurchlauf. Diese Funktion wird nicht mehr benötigt.|  
|Multidimensional Expressions (MDX)|Der Hinweis für den Abfrageoptimierer NON_EMPTY_BEHAVIOR wurde standardmäßig aktiviert.|Der Hinweis für den Abfrageoptimierer NON_EMPTY_BEHAVIOR wird in einer zukünftigen Version standardmäßig deaktiviert sein. Der MDX-Optimierungshinweis kann zu falschen Ergebnissen führen, wenn er nicht ordnungsgemäß verwendet wird.|  
|Andere|Systeminterne Zelleneigenschaft CELL_EVALUATION_LIST|Stellte ursprünglich eine Liste ausgewerteter Formeln bereit, die für eine Zelle gelten. Sie ist in dieser Version von Analysis Services leer.  Die Lösungsreihenfolge wird jetzt im MDX-Skript angegeben. Weitere Informationen finden Sie Untergrund Legendes zu [Durchlauf-und Lösungs Reihenfolge &#40;MDX&#41;](multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|  
|Objekte|COM-Assemblys|COM-Assemblys können ein Sicherheitsrisiko darstellen. COM-Assemblys werden in einer zukünftigen Version nicht mehr unterstützt.|  
  
## <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Funktionen, die in einer zukünftigen Version von SQL Server nicht unterstützt werden  
 Die folgenden Funktionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden in der nächsten Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]noch unterstützt, aber in zukünftigen Versionen entfernt. Die betreffende Version von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde noch nicht festgelegt.  
  
|Category|Als veraltet markierte Funktion|Ersatz|  
|--------------|------------------------|-----------------|  
|Mehrdimensionale Modelle|Remotepartitionen|Keine. Verwenden Sie stattdessen lokale Partitionen. Weitere Informationen finden Sie unter [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md) .|  
|Mehrdimensionale Modelle|Remoteverknüpfte Measuregruppen|Eine remoteverknüpfte Measuregruppe ist eine verknüpfte Measuregruppe, die eine Datenquelle auf einem Remoteserver verwendet. Die Fähigkeit, eine Remotedatenquelle für eine verknüpfte Measuregruppe zu verwenden, ist jetzt als veraltet markiert.<br /><br /> Es gibt keinen Ersatz für diese Funktion. Es wird empfohlen, stattdessen lokale verknüpfte Measuregruppen zu verwenden. Weitere Informationen finden Sie unter [Linked Measure Groups](multidimensional-models/linked-measure-groups.md) .|  
|Mehrdimensionale Modelle|Dimensionales Rückschreiben|Keine. Verwenden Sie das Rückschreiben von Partitionen, wenn Sie Funktionen zum Rückschreiben benötigen. Weitere Informationen finden Sie unter [Festlegen des Rück Schreibens von Partitionen](multidimensional-models/set-partition-writeback.md) .|  
|Mehrdimensionale Modelle|Verknüpfte Dimensionen|Keine. Sie können Dimensionen in zusätzliche Modelle kopieren, statt eine Verknüpfung mit einer Dimension in einem anderen Modell zu verwenden.|  
|MDX|Non_Empty_Behavior-Eigenschaft|Keine. Wenn Sie ein berechnetes Element erstellen, wird durch das falsche Festlegen dieser Eigenschaft die Wahrscheinlichkeit erhöht, dass ungültige Ergebnisse zurückgegeben werden. Durch kürzliche Optimierungen der OLAP-Engine wurden Vorgänge für Datasets mit geringer Dichte verbessert, sodass diese Eigenschaft weniger relevant geworden ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Abwärtskompatibilität](analysis-services-backward-compatibility.md)   
 [Nicht mehr unterstützte Analysis Services-Funktionalität in SQL Server 2014](discontinued-analysis-services-functionality-in-sql-server-2014.md)  
  
  
