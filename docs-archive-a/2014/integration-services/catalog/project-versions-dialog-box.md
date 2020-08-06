---
title: Projektversionen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 998dd194c2a056121fd6f7a404e75c7080b85aa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721682"
---
# <a name="project-versions-dialog-box"></a>Projektversionen (Dialogfeld)
  Verwenden Sie das Dialogfeld **Projektversionen** , um Versionen eines Projekts anzuzeigen und eine frühere Version wiederherzustellen.  
  
 Sie können frühere Versionen auch in der Sicht [catalog.object_versions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) anzeigen und die gespeicherte Prozedur [catalog.restore_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) verwenden, um frühere Versionen wiederherzustellen.  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Dialogfelds "Projektversionen"](#open_dialog)  
  
-   [Wiederherstellen einer Projektversion](#restore)  
  
##  <a name="open-the-project-versions-dialog-box"></a><a name="open_dialog"></a> Öffnen des Dialogfelds "Projektversionen"  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Server her.  
  
     Dies bedeutet, dass eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz hergestellt werden muss, die als Host für die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Datenbank fungiert.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den Knoten **Integration Services-Kataloge** , um den Knoten **SSISDB** anzuzeigen.  
  
4.  Der **SSISDB** -Knoten enthält einen oder mehrere Ordner, wovon jeder ein oder mehrere Projekte enthält. Erweitern Sie den Ordner, der das gewünschte Projekt enthält.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Versionen**.  
  
 Im Dialogfeld **Projektversionen** wird in der Tabelle **Versionen** die Liste der Versionen des Projekts angezeigt, die auf dem Server bereitgestellt wurden, und zwar mit Bereitstellungsdatum und -zeit der Version, Wiederherstellungsdatum und -zeit der Version (wenn eine Wiederherstellung stattgefunden hat), der Versionsbeschreibung und einem Versionsbezeichner. Die derzeit aktive Version wird durch ein Häkchen in der **aktuellen** Spalte der Tabelle angegeben.  
  
##  <a name="restore-a-project-version"></a><a name="restore"></a> Wiederherstellen einer Projektversion  
 Um eine frühere Version eines Projekts wiederherzustellen, wählen Sie die Version in der Tabelle **Versionen** aus, und klicken Sie dann auf **Ausgewählte Version wiederherstellen**. Das Projekt wird in der ausgewählten Version wiederhergestellt, und diese Version wird mit einem Häkchen in der **aktuellen** Spalte der Tabelle **Versionen** angegeben.  
  
  
