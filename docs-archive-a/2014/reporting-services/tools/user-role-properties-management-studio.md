---
title: Benutzerrolleneigenschaften (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f79953abdf5e3d1cdb03de8c5feeb6b2de34ab7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700664"
---
# <a name="user-role-properties-management-studio"></a>Benutzerrolleneigenschaften (Management Studio)
  Mithilfe dieser Seite sehen Sie, welche Aufgaben in einer Rollendefinition auf Elementebene eingeschlossen sind. Mit dieser Seite können Sie außerdem die Aufgabenliste oder eine Rollenbeschreibung ändern.  
  
 Eine Rollendefinition auf Elementebene ist eine benannte Auflistung von Aufgaben, die Benutzer in Bezug auf ein bestimmtes Element ausführen können (d. h. für einen Ordner, Bericht, eine Ressource oder freigegebene Datenquelle). Rollendefinitionen werden im Berichts-Manager einem Benutzer oder einer Gruppe zum Erstellen einer Rollenzuweisung zugewiesen. Die Aufgaben in der Rollendefinition beschreiben die Aktionen, die der Benutzer oder die Gruppe ausführen können.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält zahlreiche vordefinierte Rollendefinitionen auf Elementebene, die Sie verwenden können. Sie können die Rollendefinitionen ändern, indem Sie die deren Aufgabenliste ändern. Die Bearbeitung einer Rollendefinition wirkt sich auf alle Rollenzuweisungen aus, die diese Rollendefinition enthalten.  
  
> [!NOTE]  
>  Benutzerrollenzuweisungen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für die SharePoint-Integration konfiguriert, werden auf dieser Seite schreibgeschützte Informationen zu den Berechtigungsstufen und -rollen angezeigt, die auf der SharePoint-Website definiert sind.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen der Rollendefinition an.  
  
 **Beschreibung**  
 Zeigt eine Beschreibung der Rollendefinition an. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]wird diese Beschreibung nur auf dieser Seite angezeigt. Im Berichts-Manager hilft diese Beschreibung Benutzern bei der Entscheidung, ob die Rolle in einer Rollenzuweisung verwendet werden soll.  
  
 **Aufgabe**  
 Führt alle Tasks auf Elementebene auf, die für die Rollendefinition ausgewählt werden können. Sie können in der vordefinierten Aufgabenliste Elemente hinzufügen oder löschen, um zu definieren, wie Benutzer über die Rolle auf ein bestimmtes Element zugreifen können. Sie können keine neuen Tasks erstellen oder vorhandene Tasks ändern. Die Aufgabenliste einer Rollendefinition wird nur in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angezeigt.  
  
 **Taskbeschreibung**  
 Bietet Informationen zu den einzelnen Tasks. Taskbeschreibungen können Sie nicht ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben auf Elementebene](../security/tasks-and-permissions-item-level-tasks.md)   
 [Rollendefinitionen](../security/role-definitions.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md)   
 [Vordefinierte Rollen](../security/role-definitions-predefined-roles.md)  
  
  
