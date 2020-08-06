---
title: Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607774"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Beim Senden eines Resultsets an [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte die erweiterte gespeicherte Prozedur wie folgt die entsprechende API abrufen:  
  
-   Die **srv_sendmsg** -Funktion kann in beliebiger Reihenfolge aufgerufen werden, bevor oder nachdem alle Zeilen (sofern vorhanden) mit **srv_sendrow**gesendet wurden. Alle Nachrichten müssen an den Client gesendet werden, bevor der Abschluss Status mit **srv_senddone**gesendet wird.  
  
-   Die **srv_sendrow** -Funktion wird einmal für jede an den Client gesendete Zeile aufgerufen. Alle Zeilen müssen an den Client gesendet werden, bevor Nachrichten, Statuswerte oder Abschluss Status mit **srv_sendmsg**, dem **srv_status** -Argument von **srv_pfield**oder **srv_senddone**gesendet werden.  
  
-   Beim Senden einer Zeile, für die nicht alle Spalten mit **srv_describe** definiert wurden, wird von der Anwendung eine Informations Fehlermeldung ausgegeben, und es wird ein Fehler an den Client zurückgegeben. In diesem Fall wird die Zeile nicht gesendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen erweiterter gespeicherter Prozeduren](creating-extended-stored-procedures.md)  
  
  
