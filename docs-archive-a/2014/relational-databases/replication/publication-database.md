---
title: Veröffentlichungsdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 511e5f2e2caa934313ba96fb3dbc4cadddace968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608550"
---
# <a name="publication-database"></a>Veröffentlichungsdatenbank
  Bei der Veröffentlichungsdatenbank handelt es sich um die Datenbank auf dem Verleger, die als Quelle der zu replizierenden Daten und Datenbankobjekte fungiert. Die in einer Replikation verwendeten Veröffentlichungsdatenbanken müssen aktiviert werden. Die Datenbank wird aktiviert, wenn ein Mitglied der festen Serverrolle **sysadmin** Folgendes ausführt:  
  
-   Erstellt eine Veröffentlichung auf der betreffenden Datenbank mithilfe des Assistenten für neue Veröffentlichung.  
  
-   Wählt die Datenbank im Dialogfeld **Verlegereigenschaften** aus.  
  
-   Führt **sp_replicationdboption** aus und legt für die Option **publish** (bei Momentaufnahme- oder Transaktionsveröffentlichungen) oder die Option **merge publish** (bei Mergeveröffentlichungen) **True**fest.  
  
## <a name="options"></a>Tastatur  
 **Datenbanken**  
 Wählen Sie den Namen der Datenbank aus, die die Daten und Datenbankobjekte enthält, die veröffentlicht werden sollen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
