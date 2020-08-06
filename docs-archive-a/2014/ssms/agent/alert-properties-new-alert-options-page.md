---
title: 'Warnungs Eigenschaften: neue Warnung (Seite "Optionen") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722226"
---
# <a name="alert-properties-new-alert-options-page"></a>Eigenschaften von Warnungen: Neue Warnung (Seite „Optionen“)
  Mithilfe dieser Seite können Sie Optionen für-Agent-Warnungen anzeigen und ändern [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Tastatur  
 **E**  
 Schließt Fehlertext des Ereignisses ggf. in E-Mail-Benachrichtigungen ein.  
  
 **Pager**  
 Schließt Fehlertext des Ereignisses ggf. in Pagerbenachrichtigungen ein.  
  
 **NET SEND**  
 Schließt Fehlertext des Ereignisses ggf. in NET SEND-Benachrichtigungen ein.  
  
 **Zusätzlich zu sendende Warnbenachrichtigung**  
 Geben Sie hier zusätzlichen Text ein, der in die Benachrichtigungsmeldungen aufgenommen werden soll.  
  
 **Antwortverzögerung**  
 Geben Sie eine Verzögerung für das wiederholte Auftreten des Ereignisses an. Einige Ereignisse können innerhalb einer kurzen Zeitspanne häufig auftreten. In diesem Fall könnte es sinnvoll sein, zwar über das Auftreten des Ereignisses informiert zu werden, nicht aber für jedes Auftreten eine Meldung zu erhalten. Verwenden Sie diese Option, um ein Timeout anzugeben. Nachdem die Warnung auf ein Ereignis reagiert hat, wartet der-Agent mit einer Verzögerung auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die angegebene Verzögerung, bevor erneut reagiert wird, unabhängig davon, ob das Ereignis während der Verzögerung auftritt.  
  
 **Minuten**  
 Geben Sie eine Verzögerung in Minuten an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
 **Vorsprung**  
 Geben Sie eine Verzögerung in Sekunden an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Warnungen](alerts.md)  
  
  
