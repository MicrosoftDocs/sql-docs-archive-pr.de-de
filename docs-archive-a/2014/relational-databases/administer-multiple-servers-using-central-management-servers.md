---
title: Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3906165b595f6faa15812f70377a3bc0f550e52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699837"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern
  Sie können mehrere Server verwalten, indem Sie zentrale Verwaltungsserver festlegen und Servergruppen erstellen.  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a>Vorteile von zentralen Verwaltungsservern und Servergruppen  
 Eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], die als zentraler Verwaltungsserver festgelegt wurde, verwaltet die Servergruppen, die die Verbindungsinformationen für Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] enthalten. [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen und Richtlinien der richtlinienbasierten Verwaltung können gleichzeitig für Servergruppen ausgeführt werden. Sie können auch die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Protokolldateien in Instanzen anzeigen, die von einem zentralen Verwaltungsserver verwaltet werden. Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die älter sind als [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] , können nicht als zentraler Verwaltungsserver festgelegt werden.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen können auch für lokale Servergruppen in registrierten Servern ausgeführt werden.  
  
### <a name="related-tasks"></a>Related Tasks  
 Um einen zentralen Verwaltungsserver und Servergruppen zu erstellen, verwenden Sie das Fenster **Registrierte Server** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Beachten Sie, dass der zentrale Verwaltungsserver nicht Mitglied einer Gruppe sein kann, die er verwaltet. Weitere Informationen zum Erstellen von zentralen Verwaltungsservern und Servergruppen finden Sie unter [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
