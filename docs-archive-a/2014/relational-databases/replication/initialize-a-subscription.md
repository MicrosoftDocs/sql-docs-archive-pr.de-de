---
title: Initialisieren eines Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f024d360fdeab477ace09970b4f140a97696c2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609082"
---
# <a name="initialize-a-subscription"></a>Initialisieren eines Abonnements
  Abonnenten in einer Replikationstopologie müssen initialisiert werden, damit sie für jeden Artikel in der Veröffentlichung, die sie abonniert haben, eine Kopie des Schemas sowie alle erforderlichen Replikationsobjekte (gespeicherte Prozeduren, Trigger, Metadatentabellen usw.) erhalten. Darüber hinaus erhält der Abonnent typischerweise einen Anfangsdatensatz. Die Standardinitialisierungsmethode verwendet eine vollständige Momentaufnahme mit Schema, Replikationsobjekten und Daten. Veröffentlichungen können aber auch ohne eine vollständige Momentaufnahme initialisiert werden.  
  
 Weitere Informationen finden Sie unter [Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) und [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
  
