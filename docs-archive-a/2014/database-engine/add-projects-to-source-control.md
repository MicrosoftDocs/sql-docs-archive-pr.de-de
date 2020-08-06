---
title: Hinzufügen von Projekten zur Quell Code Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- projects [SQL Server Management Studio], adding
ms.assetid: fd4616b2-a564-4a66-ac53-d1f5cba213c2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0afef4ef91e4d80db7e956d03a95a2ecffe1dc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610045"
---
# <a name="add-projects-to-source-control"></a>Hinzufügen von Projekten zur Quellcodeverwaltung
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]-Projektmappen können mehrere Skriptprojekte hosten. Wie Sie ein Projekt zur Quellcodeverwaltung hinzufügen, hängt davon ab, ob die entsprechende Projektmappe der Quellcodeverwaltung unterliegt. Wenn die Projektmappe der Quellcodeverwaltung unterliegt, wird beim Einchecken der Projektmappe das Projekt automatisch der Quellcodeverwaltung hinzugefügt. Weitere Informationen zum Einchecken von Projektmappen finden [Sie unter Einchecken von Dateien](../../2014/database-engine/check-in-files.md).  
  
 Wenn die Projektmappe für dieses Projekt nicht der Quellcodeverwaltung unterliegt, können Sie der Quellcodeverwaltung die Projektmappe hinzufügen. Die Quellcodeverwaltung fügt dann automatisch die Projekte der Projektmappe hinzu. Weitere Informationen zum Hinzufügen von Lösungen zur Quell Code Verwaltung finden [Sie unter Hinzufügen von Lösungen zur Quell](../../2014/database-engine/add-solutions-to-source-control.md)Code Verwaltung.  
  
 Wenn Sie die Projekt Mappe nicht der Quell Code Verwaltung hinzufügen möchten, können Sie das Projekt mit dem Befehl **Auswahl zur Quell Code Verwaltung hinzufügen** manuell hinzufügen.  
  
 Datenbankobjekte werden nicht direkt vom Quellcodeverwaltungsanbieter geschützt. Sie können jedoch Skripts von Datenbankobjekten erstellen und die Skripts unter der Quellcodeverwaltung speichern.  
  
### <a name="to-add-a-project-to-source-control"></a>So fügen Sie der Quellcodeverwaltung ein Projekt hinzu  
  
1.  Wählen Sie im Projektmappen-Explorer ein Projekt aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf **Ausgewählte Projekte zur Quell Code Verwaltung hinzufügen**.  
  
    > [!NOTE]  
    >  Wenn Sie den Befehl **Ausgewählte Projekte zur Quell Code Verwaltung hinzufügen** verwenden, um ein Projekt hinzuzufügen, das zu einer Projekt Mappe mit Quell Code Verwaltung gehört, werden Sie gefragt, ob Sie das Projekt als Unterordner der Lösung für die Quell Code Verwaltung hinzufügen oder das Projekt als separaten Ordner hinzufügen möchten.  
  
3.  Melden Sie sich beim Quellcodeverwaltungsanbieter an, wenn Sie dazu aufgefordert werden.  
  
4.  Das Dialogfeld **zu SourceSafe-Projekt hinzufügen** wird angezeigt. Der Name des Projekts wird im Feld **Projekt** angezeigt.  
  
5.  Öffnen Sie in der Liste **Ordner** den Ordner, in dem Sie das Projekt platzieren möchten. Alternativ können Sie auf **Erstellen** klicken, um einen Ordner mit dem Namen zu erstellen, der im Feld **Projekt** angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Projektmappen und Projekten zur Quellcodeverwaltung](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)  
  
  
