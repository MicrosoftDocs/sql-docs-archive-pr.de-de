---
title: Hinzufügen einer Enumeration zu einer Ablauf Steuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59b8569880fdf1a49f5f2ca1f6841841f9790af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617247"
---
# <a name="add-enumeration-to-a-control-flow"></a>Hinzufügen einer Enumeration zu einer Ablaufsteuerung
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] umfasst den Foreach-Schleifencontainer. Dabei handelt es sich um ein Ablaufsteuerungselement, mit dem Sie auf einfache Weise eine Schleifenkonstruktion zum Aufzählen der Dateien und Objekte in der Ablaufsteuerung eines Pakets einbinden können. Weitere Informationen finden Sie unter [Foreach-Schleifencontainer](control-flow/foreach-loop-container.md).  
  
 Der Foreach-Schleifencontainer bietet keine Funktionalität, sondern stellt lediglich eine Struktur bereit, in der Sie eine wiederholbare Ablaufsteuerung erstellen, einen Enumeratortyp angeben und den Enumerator konfigurieren. Sie müssen mindestens einen Task in den Foreach-Schleifencontainer einschließen, um eine Containerfunktionalität bereitzustellen. Weitere Informationen finden Sie unter [Integration Services-Tasks](control-flow/integration-services-tasks.md).  
  
 Der Foreach-Schleifencontainer kann eine Ablaufsteuerung mit mehreren Tasks und weiteren Containern einschließen. Das Hinzufügen von Tasks und Containern zu einem Foreach-Schleifencontainer ähnelt dem Hinzufügen von Tasks und Containern zu einem Paket, nur ziehen Sie die Tasks und Container nicht auf das Paket, sondern auf den Foreach-Schleifencontainer. Falls der Foreach-Schleifencontainer mehrere Tasks oder Container umfasst, können Sie diese wie bei einem Paket mithilfe von Rangfolgeneinschränkungen verbinden. Weitere Informationen finden Sie unter [Rangfolgeneinschränkungen](control-flow/precedence-constraints.md).  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a>So implementieren Sie einen Foreach-Schleifencontainer in einer Ablaufsteuerung  
  
1.  Fügen Sie den Foreach-Schleifencontainer zum Paket hinzu. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
2.  Fügen Sie dem Foreach-Schleifencontainer Tasks und Container hinzu. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) .  
  .  
  
3.  Verbinden Sie Tasks und Container im Foreach-Schleifencontainer mithilfe von Rangfolgeneinschränkungen. Weitere Informationen finden Sie unter [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Konfigurieren Sie den Foreach-Schleifencontainer. Weitere Informationen finden Sie unter [Konfigurieren eines Foreach-Schleifencontainers](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablauf Steuerung](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Gruppieren oder Deaktivieren von Komponenten](group-or-ungroup-components.md)   
 [Rang folgen Einschränkungen](control-flow/precedence-constraints.md)   
 [Hinzufügen einer Iterationen zu einer Ablauf Steuerung](add-iteration-to-a-control-flow.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)  
  
  
