---
title: Verweise auf DataSources- und DataSets-Auflistungen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 560a42daf4d4580adde5b6100fe23f2c646fff08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621375"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a>Verweise auf DataSources- und DataSets-Auflistungen (Berichts-Generator und SSRS)
  Die `DataSources`-Auflistung enthält alle in einem Bericht verwendeten Datenquellen. Die `DataSets`-Auflistung enthält alle Datasets für alle Datenquellen in einem Bericht. Verwenden Sie den Bereich **Berichtsdaten** für eine hierarchische Sicht von Berichtsdatasets, die unter der Datenquelle organisiert werden, auf die sie verweisen. Wenn Sie Verweise auf diese Auflistungen einschließen, werden bei der Vorschau des Berichts keine Werte angezeigt. Die Auflistungen sind erst verfügbar, nachdem der Bericht auf einem Berichtsserver veröffentlicht wurde.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a>DataSources  
 Die `DataSources`-Auflistung stellt die Auflistung der Datenquellen dar, auf die in einer veröffentlichten Berichtsdefinition verwiesen wird. Sie können diese Informationen in den Bericht einschließen, um die Quelle der Berichtsdaten zu dokumentieren. Diese Auflistung ist im **Vorschaumodus** nicht verfügbar. In der folgenden Tabelle sind die Variablen in der `DataSources`-Auflistung beschrieben.  
  
|**Variable**|`Type`|**Beschreibung**|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|Der vollständige Pfad der Datenquellendefinition auf dem Berichtsserver. Sie können eine Liste der von einem Bericht verwendeten Datenquellen im Rahmen eines Berichtsverlaufs mit einbeziehen. Im folgenden Beispiel wird der vollständige Pfad für die Datenquelle mit dem Namen AdventureWorks2012 angezeigt:<br /><br /> `/DataSources/AdventureWorks2012`.|  
|`Type`|`String`|Der Typ des Datenanbieters für die Datenquelle. Beispiel: `SQL`.|  
  
## <a name="datasets"></a>DataSets  
 Die `DataSets`-Auflistung stellt die Datasets dar, auf die in einer Berichtsdefinition verwiesen wird. Sie können die Abfrage in einem Textfeld in den Bericht einschließen, sodass ein Benutzer, der wissen möchte, welche Daten in dem Bericht enthalten sind, den ursprünglichen Befehlstext sehen kann. Diese Auflistung ist im **Vorschaumodus** nicht verfügbar. In der folgenden Tabelle sind die Elemente der `DataSets`-Auflistung beschrieben.  
  
|**Member**|`Type`|**Beschreibung**|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|Mit dieser Abfrage werden für Datenbanken-Datenquellen die Daten aus der Datenquelle abgerufen. Besteht die Abfrage aus einem Ausdruck, ist dies der ausgewertete Ausdruck.|  
|`RewrittenCommandText`|`String`|Der erweiterte CommandText-Wert für den Datenanbieter. Dieser wird in der Regel für Berichte mit Abfrageparametern verwendet, die Berichtsparametern zugeordnet werden. Die Eigenschaft wird vom Datenanbieter festgelegt, wenn die Parameterverweise des Befehlstexts auf die konstanten Werte erweitert werden, die für die zugeordneten Berichtsparameter ausgewählt wurden.|  
  
### <a name="using-query-expressions"></a>Verwenden von Abfrageausdrücken  
 Mithilfe von Ausdrücken können Sie die in einem Dataset enthaltene Abfrage definieren. Auf diese Weise können Sie Berichte entwerfen, in denen die Abfrage abhängig von Benutzereingaben, Daten in anderen Datasets oder anderen Variablen geändert wird. Weitere Informationen zu Abfragen finden Sie unter [Eingebettete und freigegebene Datasets (Berichts-Generator und SSRS)](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
