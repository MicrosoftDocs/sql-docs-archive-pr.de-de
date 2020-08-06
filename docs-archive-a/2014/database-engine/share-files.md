---
title: Freigeben von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724901"
---
# <a name="share-files"></a>Freigeben von Dateien
  Mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie Elemente über mehrere Quellcodeverwaltungsprojekte freigeben. Wenn Sie ein Element freigeben, werden Änderungen an dem Element in den einzelnen Projekten angezeigt, für die das Element freigegeben ist.  
  
 Benutzern der Quellcodeverwaltung bietet das Freigeben von Elementen die folgenden Vorteile:  
  
-   Das Speichern einzelner Kopien des Elements für die einzelnen Projekte, die freigegebene Elemente verwenden, entfällt. Dadurch wird Speicherplatz auf dem Client und dem Server der Quellcodeverwaltung gespart. Der Quellcodeverwaltungsanbieter speichert das freigegebene Element an einem zentralen Speicherort, und jedes Projekt, für das die Freigabe erfolgt, speichert einen Zeiger zu diesem Speicherort.  
  
-   Inkompatibilitäten der Versionen werden vermieden. Da jedes Projekt, für das das Element freigegeben wird, dieselbe Version des Elements verwendet, vermeiden Sie die Konflikte, die durch unabhängig voneinander geänderten Kopien eines Elements in den einzelnen Projekten entstehen können.  
  
### <a name="to-share-an-item"></a>So geben Sie ein Element frei  
  
1.  Wählen Sie im Projektmappen-Explorer den Ordner oder das Projekt aus, in dem die freigegebenen Dateien platziert werden sollen.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf **Freigeben**.  
  
3.  Navigieren Sie im Dialogfeld **Freigeben mit** in der Verzeichnisliste für das Element, das Sie freigeben möchten, und klicken Sie auf dieses Element.  
  
4.  Klicken Sie auf **Share** (Freigeben).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlagen zur Quellcodeverwaltung](../../2014/database-engine/source-control-basics.md)  
  
  
