---
title: Broker (Ereigniskategorie) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23f839416e3404bfdf0a7e61d1b1e8dbbb90ec95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609268"
---
# <a name="broker-event-category"></a>Broker (Ereigniskategorie)
  Die **Broker** -Ereigniskategorie enthält allgemeine Service Broker-Ereignisse.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Broker:Activation (Ereignisklasse)](broker-activation-event-class.md)|Ein Ereignis, das generiert wird, wenn durch eine Warteschlangenüberwachung eine gespeicherte Aktivierungsprozedur gestartet wird.|  
|[Broker:Connection-Ereignisklasse](broker-connection-event-class.md)|Ein Ereignis, das generiert wird, um den Status einer von Service Broker verwalteten Transportverbindung zu melden.|  
|[Broker:Conversation-Ereignisklasse](broker-conversation-event-class.md)|Ein Ereignis, das generiert wird, um den Fortschritt einer Konversation zu melden.|  
|[Broker:Conversation Group-Ereignisklasse](broker-conversation-group-event-class.md)|Ein Ereignis, das generiert wird, wenn die Datenbank eine Konversationsgruppe erstellt oder löscht.|  
|[Broker:Corrupted Message (Ereignisklasse)](broker-corrupted-message-event-class.md)|Ein Ereignis, das zum Angeben einer fehlerhaften, von der Datenbank erhaltenen Nachricht generiert wird.|  
|[Broker:Forwarded Message Dropped-Ereignisklasse](broker-forwarded-message-dropped-event-class.md)|Ein Ereignis, das generiert wird, wenn SQL Server eine Service Broker-Nachricht löscht, die hätte weitergeleitet werden sollen.|  
|[Broker:Forwarded Message Sent-Ereignisklasse](broker-forwarded-message-sent-event-class.md)|Ein Ereignis, das generiert wird, wenn SQL Server eine Service Broker-Nachricht weiterleitet.|  
|[Broker:Message Classify (Ereignisklasse)](broker-message-classify-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker das Routing für eine Nachricht bestimmt.|  
|[Broker:Message Drop (Ereignisklasse)](broker-message-drop-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker eine empfangene Nachricht nicht beibehalten kann, die in dieser Instanz an einen Dienst weitergeleitet werden sollte.|  
|[Broker:Remote Message Ack (Ereignisklasse)](broker-remote-message-ack-event-class.md)|Ein Ereignis, das generiert wird, wenn Service Broker eine Nachrichtenbestätigung sendet oder empfängt.|  
  
 Service Broker bietet auch zwei Sicherheitsüberwachungsereignisse. Weitere Informationen zu diesen Ereignissen finden Sie unter [Audit Broker Login (Ereignisklasse)](audit-broker-login-event-class.md) und [Audit Broker Conversation (Ereignisklasse)](audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberwachung-Ereigniskategorie](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
