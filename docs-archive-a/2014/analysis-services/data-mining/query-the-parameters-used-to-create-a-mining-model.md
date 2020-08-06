---
title: Abfragen der Parameter, mit denen ein Mining Modell erstellt wurde | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a3802a0d70579f613accbe6abd310da909751b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717026"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a>Abfragen der Parameter, mit denen ein Miningmodell erstellt wird
  Die Zusammensetzung eines Miningmodells wird nicht nur von den Trainingsfällen beeinflusst, sondern auch von den Parametern, die bei der Erstellung des Modells festgelegt wurden. Daher ist es unter Umständen hilfreich, die Parametereinstellungen eines vorhandenen Modells abzurufen, um das Verhalten des Modells besser zu verstehen. Das Abrufen der Parameter ist auch beim Dokumentieren einer bestimmten Version dieses Modells nützlich.  
  
 Um die Parameter zu finden, die bei der Erstellung des Modells verwendet wurden, erstellen Sie eine Abfrage für eines der Miningmodell-Schemarowsets. In [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]werden diese Schemarowsets als Gruppe von Systemsichten verfügbar gemacht, die einfach mit der Transact-SQL-Syntax abgefragt werden können. In diesem Verfahren wird beschrieben, wie Sie eine Abfrage erstellen, die die Parameter zurückgibt, mit denen das angegebene Miningmodell erstellt wurde.  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a>So öffnen Sie ein Abfragefenster für eine Schemarowsetabfrage  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz, die das abzufragende Modell enthält.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Instanznamen, wählen Sie **Neue Abfrage**und anschließend **DMX**aus.  
  
    > [!NOTE]  
    >   Sie können auch mit der **MDX** -Vorlage eine Abfrage für ein Data Mining-Modell erstellen.  
  
3.  Wenn die Instanz mehrere Datenbanken enthält, wählen Sie aus der Liste **Verfügbare Datenbanken** in der Symbolleiste die Datenbank mit dem Modell aus, das Sie abfragen möchten.  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a>So geben Sie Modellparameter für ein vorhandenes Miningmodell zurück  
  
1.  Geben oder fügen Sie im DMX-Abfragefenster den folgenden Text ein:  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  Wählen Sie im Objekt-Explorer das gewünschte Miningmodell aus, und ziehen Sie es in das DMX-Abfragefenster zwischen die einfachen Anführungszeichen.  
  
3.  Drücken Sie F5, oder klicken Sie auf **Ausführen**.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code gibt eine Liste der Parameter zurück, mit denen das Miningmodell im [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)erstellt wurde. Diese Parameter umfassen die expliziten Werte für Standardwerte, die von den Miningdiensten verwendet werden, die von Anbietern auf dem Server bereitgestellt werden.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 Im Codebeispiel werden die folgenden Parameter für das Clustermodell zurückgegeben:  
  
 eExample-Ergebnisse:  
  
 MINING_PARAMETERS  
  
 CLUSTER_COUNT=10, CLUSTER_SEED=0, CLUSTERING_METHOD=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, MINIMUM_SUPPORT=1, MODELLING_CARDINALITY=10, SAMPLE_SIZE=50000, STOPPING_TOLERANCE=10  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Abfrage Tasks und Anleitungen](data-mining-query-tasks-and-how-tos.md)   
 [Data Mining-Abfragen](data-mining-queries.md)  
  
  
