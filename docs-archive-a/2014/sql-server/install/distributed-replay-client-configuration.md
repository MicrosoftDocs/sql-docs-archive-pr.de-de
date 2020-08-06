---
title: Distributed Replay Client Konfiguration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 53124029483c25ed7894b279283e1de02c647350
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622405"
---
# <a name="distributed-replay-client-configuration"></a>Distributed Replay Client-Konfiguration
  Verwenden Sie die Seite für die **Distributed Replay Client-Konfiguration** des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installations-Assistenten, um die Benutzer anzugeben, denen Sie Administratorberechtigungen für den Distributed Replay Client-Dienst gewähren möchten.  
  
 Benutzer, die über Administratorberechtigungen verfügen, besitzen unbeschränkten Zugriff auf den Distributed Replay Client-Dienst.  
  
## <a name="options"></a>Tastatur  
 **Controllername**  
 Dies ist ein optionaler Parameter, und der Standardwert ist \<*blank*> .  
  
 Geben Sie den Namen des Controllers ein, mit dem der Clientcomputer für den Distributed Replay Client-Dienst kommuniziert. Beachten Sie Folgendes:  
  
-   Der Name muss ein vollqualifizierter Domänenname sein. Ein Host mit dem Namen "server1" kann in der Produkthierarchie von Microsoft z. B. den vollqualifizierten Domänennamen "server1.products.microsoft.com" haben.  
  
-   Wenn Sie bereits einen Controller eingerichtet haben, geben Sie den Namen des Controllers beim Konfigurieren jedes Clients ein.  
  
-   Wenn Sie noch keinen Controller eingerichtet haben, können Sie das Feld für den Controllernamen leer lassen. Sie müssen den Controllernamen jedoch in der **Clientkonfigurationsdatei** manuell eingeben.  
  
 **Arbeitsverzeichnis**  
 Geben Sie das Arbeitsverzeichnis für den Distributed Replay Client-Dienst an.  
  
 Das Standardarbeitsverzeichnis lautet \<*drive letter*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
 **Ergebnisverzeichnis**  
 Geben Sie das Ergebnisverzeichnis für den Distributed Replay Client-Dienst an.  
  
 Das Standardergebnisverzeichnis lautet \<*drive letter*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
  
