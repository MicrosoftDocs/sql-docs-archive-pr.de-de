---
title: Aktivieren von Drillthrough für ein Mining Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6adfc389776f91132e527130f50f61c9783d9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608919"
---
# <a name="enable-drillthrough-for-a-mining-model"></a>Aktivieren von Drillthrough für ein Miningmodell
  Wenn Sie Drillthrough für ein Miningmodell aktiviert haben, können Sie beim Durchsuchen des Modells detaillierte Informationen über die Fälle abrufen, die für die Erstellung des Modells verwendet wurden. Zum Anzeigen dieser Informationen benötigen Sie die erforderlichen Berechtigungen. Außerdem muss die Struktur bereits verarbeitet worden sein.  
  
 **Berechtigungen:** Damit ein Benutzer einen Drillthrough in Modell- oder Strukturdaten ausführen kann, muss er Mitglied einer Rolle sein, die über [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) -Berechtigungen für das Miningmodell oder die Miningstruktur verfügt. Drillthroughberechtigungen werden getrennt für die Struktur und das Modell festgelegt.  
  
-   Mit Drillthrough-Berechtigungen für das Modell können Sie einen Drillthrough des Modells durchführen, auch wenn Sie keine Berechtigungen für die Struktur besitzen.  
  
-   Mit Drillthroughberechtigungen für die Struktur können Sie außerdem mit der Funktion [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) Strukturspalten in Drillthroughabfragen für das Modell einbeziehen. Sie können auch die Trainings-und Testfälle in der Struktur Abfragen, indem Sie die Option Select... Aus \<structure> . Fälle-Syntax.  
  
 **Zwischenspeichern von Trainingsfällen:** Beim Drillthrough werden Informationen über die Trainingsfälle in der Miningstruktur abgerufen. Diese Informationen werden zwischengespeichert, wenn die Struktur verarbeitet wird. Wenn Sie alle zwischengespeicherten Daten durch Ändern der <xref:Microsoft.AnalysisServices.MiningStructureCacheMode>-Eigenschaft in `ClearAfterProcessing` löschen, funktioniert der Drillthrough nicht.  
  
> [!NOTE]  
>  Wenn die Trainingsfälle nicht zwischengespeichert wurden, müssen Sie die <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> -Eigenschaft in **KeepTrainingCases** ändern und das Modell anschließend erneut verarbeiten, bevor Sie die Falldaten anzeigen können.  
  
 Weitere Informationen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>So aktivieren Sie Drillthrough für ein Miningmodell  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf der Registerkarte **Miningmodelle** mit der rechten Maustaste auf den Namen des Miningmodells, für das Sie Drillthrough aktivieren möchten, und wählen Sie anschließend **Eigenschaften**aus.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf **AllowDrillThrough**, und wählen Sie **true**aus.  
  
3.  Klicken Sie auf der Registerkarte **Mining Modelle** mit der rechten Maustaste auf das Modell, und wählen Sie **Modell verarbeiten**aus.  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>So aktivieren Sie das Zwischenspeichern für eine Miningstruktur  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf der Registerkarte **Miningstruktur** mit der rechten Maustaste auf den Namen der Miningstruktur.  
  
2.  Öffnen Sie das Fenster **Eigenschaften** .  
  
3.  Suchen Sie im Fenster **Eigenschaften** die **CacheMode** -Eigenschaft, und wählen Sie dann **KeepTrainingCases** in der Liste aus.  
  
4.  Aktivieren Sie im Menü **Datenbank** die Option **Verarbeiten**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md)  
  
  
