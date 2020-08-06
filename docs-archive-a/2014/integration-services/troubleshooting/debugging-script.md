---
title: Debuggen von Skript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Script task [Integration Services], debugging
- debugging [Integration Services], scripts
- scripts [Integration Services], debugging
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7926f806f20f76c7aaac0c22b970addc5e93a78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721566"
---
# <a name="debugging-script"></a>Debuggen von Skript
  Sie erstellen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) die Skripts, die vom Skripttask und der Skriptkomponente verwendet werden.  
  
 Sie legen Breakpoints in VSTA fest und erstellen sie. Breakpoints können in VSTA sowie im Dialogfeld **Breakpoints festlegen** des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers verwaltet werden. Weitere Informationen finden Sie unter [Debugging Control Flow](debugging-control-flow.md).  
  
 Das Dialogfeld **Breakpoints festlegen** schließt die Skriptbreakpoints ein. Diese Breakpoints werden am Ende der Breakpointliste angezeigt und enthalten die Zeilennummer und den Namen der Funktion, in der der Breakpoint vorkommt. Skriptbreakpoints können Sie im Dialogfeld **Breakpoints festlegen** löschen.  
  
 Zur Laufzeit werden die Breakpoints, die in Codezeilen im Skript festgelegt sind, in die Breakpoints integriert, die für das Paket oder die Tasks und Container im Paket festgelegt sind. Der Debugger kann ab einem Breakpoint im Skript bis zu einem für das Paket, den Task oder den Container festgelegten Breakpoint ausgeführt werden, oder umgekehrt. Beispielsweise können für ein Paket Breakpoints für die Unterbrechungsbedingungen festgelegt sein, die auftreten, wenn das Paket die Ereignisse **OnPreExecute** und **OnPostExecute** empfängt, und die auch einen Skripttask mit Breakpoints in den Skriptzeilen aufweisen. In diesem Szenario kann die Ausführung vom Paket an der Unterbrechungsbedingung angehalten werden, die dem **OnPreExecute** -Ereignis zugeordnet ist, bis zu den Breakpoints im Skript ausgeführt werden und schließlich bis zur Unterbrechungsbedingung ausgeführt werden, die dem **OnPostExecute** -Ereignis zugeordnet ist.  
  
 Weitere Informationen zum Debuggen des Skripttasks und der Skriptkomponente finden Sie unter [Coding and Debugging the Script Task](../extending-packages-scripting/task/coding-and-debugging-the-script-task.md) und [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-visual-studio-for-applications"></a>So legen Sie in Visual Studio für Applikationen einen Breakpoint fest  
  
-   [Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente](../extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tools zur Problembehandlung für die Paketentwicklung](troubleshooting-tools-for-package-development.md)  
  
  
