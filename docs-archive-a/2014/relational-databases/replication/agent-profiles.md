---
title: Agentprofile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.profiles.perfprofiles.f1
helpviewer_keywords:
- Agent Profiles dialog box
ms.assetid: 0422e99c-e688-419b-bb4c-c7bebeef1d8d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7584670088da1ac7a9c81f1f8f0cbdce8b040c7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615960"
---
# <a name="agent-profiles"></a>Agentprofile
  Mithilfe des Dialogfelds **Agentprofile** können Sie Agentprofile verwalten. Agentprofile stellen eine einfache Möglichkeit dar, die Laufzeitparameter jedes Agents zu verwalten. Jeder Agent verfügt über ein Standardprofil, und einige Agents verfügen über zusätzliche vordefinierte Profile. Der Merge-Agent verfügt z. B. über ein Profil für langsame Verbindungen, das für Verbindungen mit geringer Bandbreite angelegt wurde. Die vordefinierten Profile reichen für die meisten Anwendungen aus, aber Sie können auch benutzerdefinierte Profile erstellen, mit denen Sie das Verhalten der Agents je nach Bedarf anpassen können.  
  
## <a name="options"></a>Tastatur  
 **Seite auswählen**  
 Wählen Sie im linken Bereich einen Agent aus. Im rechten Bereich werden daraufhin die Profile für diesen Agent angezeigt.  
  
 **Standardwert für Neu**  
 Wählen Sie das Profil aus, das verwendet werden soll, wenn für einen Agent des angegebenen Typs Aufträge erstellt werden. Wenn Sie z. B. mehrere Abonnements für eine Mergeveröffentlichung erstellen, wird für den Auftrag des Merge-Agents für jedes Abonnement das ausgewählte Profil verwendet. Wenn Sie das Profil für vorhandene Aufträge ändern möchten, wählen Sie ein Profil aus, und klicken Sie auf **Vorhandene Agents ändern**.  
  
 **Name**  
 Der Name des Profils.  
  
 **Typ**  
 Der Typ des Profils: **Benutzer** (benutzerdefiniert) oder **System** (vordefiniert).  
  
 **Eigenschaften (...)**  
 Klicken Sie auf diese Option, um die Werte anzuzeigen, die für jeden Parameter im Agentprofil verwendet werden.  
  
 **Neu**  
 Klicken Sie hier, um ein neues Profil zu erstellen.  
  
 **Löschen**  
 Wählen Sie ein benutzerdefiniertes Profil aus, und klicken Sie auf **Löschen** , um dieses Profil zu löschen. Vordefinierte Profile können nicht gelöscht werden.  
  
 **Vorhandene Agents ändern**  
 Wählen Sie ein Profil aus, und klicken Sie dann auf **Vorhandene Agents ändern** , um anzugeben, dass alle vorhandenen Aufträge für einen Agent des angegebenen Typs das ausgewählte Profil verwenden sollen. Wenn Sie z. B. mehrere Abonnements für eine Mergeveröffentlichung erstellt haben und das Profil so ändern möchten, dass die Merge-Agentaufträge für alle diese Abonnements das **Agentprofil für langsame Links**verwenden, wählen Sie dieses Profil aus, und klicken Sie auf **Vorhandene Agents ändern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit Replikations-Agent-Profilen](agents/work-with-replication-agent-profiles.md)   
 [Replikations-Agents (Übersicht)](agents/replication-agents-overview.md)   
 [Replikations-Agent-Profile](agents/replication-agent-profiles.md)  
  
  
