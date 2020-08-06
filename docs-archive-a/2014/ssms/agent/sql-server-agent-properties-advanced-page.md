---
title: SQL Server-Agent-Eigenschaften (Seite Erweitert)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8ec0d9d7fbd51f9350bf692588f90c292e54f4e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621313"
---
# <a name="sql-server-agent-properties-advanced-page"></a>SQL Server-Agent-Eigenschaften (Seite Erweitert)
  Verwenden Sie diese Seite, um erweiterte Eigenschaften des- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienstanbieter anzuzeigen und zu ändern.  
  
## <a name="options"></a>Tastatur  
 **SQL Server-Ereignisweiterleitung**  
 Durch die Optionen in dieser Kategorie wird die Ereignisweiterleitung aktiviert und konfiguriert.  
  
 **Ereignisse an anderen Server weiterleiten**  
 Leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Ereignisse an einen anderen Server weiter.  
  
 **Server**  
 Wählen Sie den Namen des Servers aus, an den Ereignisse weitergeleitet werden sollen.  
  
 **Ereignisse ohne Behandlung**  
 Leitet nur Ereignisse ohne Behandlung an den angegebenen Server weiter. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent leitet nur Ereignisse weiter, auf die keine Warnung reagiert.  
  
 **Alle Ereignisse**  
 Leitet alle Ereignisse weiter. Wenn eine Warnung in der lokalen Instanz auf das Ereignis reagiert, leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Ereignis weiter und verarbeitet auch die Warnung.  
  
 **Bei diesem Schweregrad des Ereignisses oder darüber**  
 Leitet nur Ereignisse weiter, deren Schweregrad der angegebenen Ebene entspricht oder darüber liegt.  
  
 **Bedingung für 'CPU im Leerlauf'**  
 Durch die Optionen in dieser Kategorie werden die Bedingungen definiert, unter denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Aufträge ausführt, für die CPU-Leerlaufzeitpläne festgelegt sind.  
  
 **Bedingung für 'CPU im Leerlauf' definieren**  
 Definiert die Bedingungen, unter denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent die CPU als im Leerlauf befindlich betrachtet.  
  
 **bei durchschnittlicher CPU-Nutzung unter**  
 Prozentualer Wert der CPU-Nutzung, unter dem die CPU als im Leerlauf befindlich betrachtet wird.  
  
 **und Verbleiben unterhalb dieser Stufe für**  
 Die Zeitspanne, für die die durchschnittliche CPU-Nutzung unterhalb des angegebenen Wertes liegen muss, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Aufträge dem CPU-Leerlaufzeitplan entsprechend ausführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Anfügen von Zeitplänen an Aufträge](create-and-attach-schedules-to-jobs.md)   
 [Verwalten von Ereignissen](manage-events.md)  
  
  
