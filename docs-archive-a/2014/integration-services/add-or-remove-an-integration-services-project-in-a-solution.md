---
title: Hinzufügen oder Entfernen eines Integration Services Projekts in einer Projekt Mappe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607959"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a>Hinzufügen oder Entfernen eines Integration Services-Projekts in einer Projektmappe
  In den folgenden Verfahren wird beschrieben, wie ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt zu einer Projektmappe hinzugefügt bzw. aus dieser entfernt wird.  
  
 Sie können nur ein Projekt zu einer vorhandenen Projektmappe hinzufügen oder aus einer Projektmappe entfernen, wenn die Projektmappe in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]sichtbar ist. Wenn Sie die Option Projekt Mappe **immer anzeigen** in ausgewählt haben [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] zeigt eine Projekt Mappe auch dann an, wenn diese Projekt Mappe nur ein Projekt enthält. Andernfalls zeigt [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine Projektmappe nur an, wenn diese mehr als ein Projekt enthält. Die zusätzlichen Projekte können entweder [!INCLUDE[ssIS](../includes/ssis-md.md)] -Projekte oder Projekte anderer Typen sein.  
  
## <a name="adding-an-integration-services-project"></a>Hinzufügen eines Integration Services-Projekts  
 Beim Hinzufügen eines Projekts können Sie mit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ein neues, leeres Projekt erstellen oder ein bereits für eine andere Projektmappe erstelltes Projekt hinzufügen. Sie können ein Projekt nur einer vorhandenen Projektmappe hinzufügen, wenn die Projektmappe in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]sichtbar ist.  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a>So fügen Sie einer Projektmappe ein neues SQL Server Integration Services-Projekt hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Projektmappe, der Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzufügen möchten, und führen Sie eine der folgenden Aktionen aus:  
  
    -   Klicken Sie mit der rechten Maustaste auf die Projektmappe, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
    -   Zeigen Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** im Fensterbereich **Vorlagen** auf **Integration Services-Projekt** .  
  
3.  Bearbeiten Sie optional den Projektnamen und den Speicherort.  
  
4.  Klicken Sie auf **OK**.  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a>So fügen Sie einer Projektmappe ein vorhandenes SQL Server Integration Services-Projekt hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Projektmappe, der Sie ein vorhandenes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzufügen möchten, und führen Sie eine der folgenden Aktionen aus:  
  
    -   Klicken Sie mit der rechten Maustaste auf die Projektmappe, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Projekt**.  
  
    -   Klicken Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Projekt**.  
  
2.  Suchen Sie im Dialogfeld **Vorhandenes Projekt hinzufügen** das Projekt, das Sie hinzufügen möchten, und klicken Sie dann auf **Öffnen**.  
  
3.  Das Projekt wird dem Projektmappenordner im **Projektmappen-Explorer**hinzugefügt.  
  
## <a name="removing-an-integration-services-project"></a>Entfernen eines Integration Services-Projekts  
 Sie können ein Projekt aus einer Projektmappe nur entfernen, wenn die Projektmappe in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]sichtbar ist. Nachdem die Projektmappe sichtbar ist, können alle Projekte, außer einem Projekt, entfernt werden. Sobald nur ein Projekt verbleibt, wird der Projektmappenordner in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] nicht mehr angezeigt, und das Löschen des letzten Projekts ist nicht möglich.  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a>So entfernen Sie ein Integration Services-Projekts aus einer Projektmappe  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Projektmappe, aus der Sie ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt entfernen möchten.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Projekt entladen**.  
  
3.  Klicken Sie auf **OK**, um das Entfernen zu bestätigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41;-Projekte](integration-services-ssis-projects-and-solutions.md)   
 [Erstellen eines neuen Integration Services Projekts](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
