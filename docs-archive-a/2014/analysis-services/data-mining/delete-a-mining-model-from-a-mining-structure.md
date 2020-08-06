---
title: Löschen eines Mining Modells aus einer Mining Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72c79dcdccf6225b8e75144f8b090dcab7506c10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621268"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>Löschen eines Miningmodells aus einer Miningstruktur
  Miningmodelle können mit dem Data Mining-Designer, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]oder DMX-Anweisungen gelöscht werden.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Löschen eines Miningmodells mit SQL Server-Datentools  
  
1.  Wählen Sie die Registerkarte **Miningmodelle** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf das zu löschende Modell, und anschließend auf **Löschen**.  
  
     Das Dialogfeld **Objekte löschen** wird angezeigt.  
  
3.  Klicken Sie auf **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Löschen eines Miningmodells mit SQL Server Management Studio  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, die das Modell enthält.  
  
2.  Erweitern Sie **Miningstrukturen**und anschließend **Miningmodelle**.  
  
3.  Klicken Sie mit der rechten Maustaste auf das zu löschende Modell, und anschließend auf **Löschen**.  
  
     Durch Löschen des Modells werden nicht die Trainingsdaten, sondern nur die Metadaten und alle Muster gelöscht, die beim Trainieren des Modells erstellt wurden.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Löschen eines Miningmodells mit DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Miningmodelltasks und Anweisungen](mining-model-tasks-and-how-tos.md)  
  
  
