---
title: Erneute Bereitstellung von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696950"
---
# <a name="redeployment-of-packages"></a>Erneutes Bereitstellen von Paketen
  Nachdem ein Projekt bereitgestellt wurde, kann es erforderlich werden, die Paketfunktionalität zu aktualisieren oder zu erweitern und anschließend das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, das die aktualisierten Pakete enthält, erneut bereitzustellen. Im Zusammenhang mit dem erneuten Bereitstellen von Paketen sollten Sie die zum Bereitstellungshilfsprogramm gehörenden Konfigurationseigenschaften überprüfen. Beispielsweise können Sie festlegen, dass nach dem erneuten Bereitstellen des Pakets keine Konfigurationsänderungen zulässig sein sollen.  
  
## <a name="process-for-redeployment"></a>Prozess für die erneute Bereitstellung  
 Nachdem Sie die Pakete aktualisiert haben, erstellen Sie das Projekt neu. Kopieren Sie dann den Bereitstellungsordner zum Zielcomputer, und führen Sie dann den Paketinstallations-Assistenten erneut aus.  
  
 Wenn Sie nur wenige Pakete aus dem Projekt aktualisieren, muss eventuell nicht das gesamte Projekt erneut bereitgestellt werden. Um nur wenige Pakete bereitzustellen, können Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellen, diesem neuen Projekt die aktualisierten Pakete hinzufügen und dann das Projekt erstellen und bereitstellen. Die Paketkonfigurationen werden automatisch zusammen mit dem Paket kopiert, wenn Sie das Paket einem anderen Projekt hinzufügen.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Bereitstellen von Paketen mithilfe des Bereitstellungshilfsprogramms](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
