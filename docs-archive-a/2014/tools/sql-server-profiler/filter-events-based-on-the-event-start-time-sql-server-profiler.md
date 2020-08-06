---
title: Filtern von Ereignissen anhand der Ereignisstartzeit (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723246"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>Filtern von Ereignissen nach Ereignisstartzeit (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Ablaufverfolgungsereignisse basierend auf der Ereignisstartzeit filtern.  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>So filtern Sie ein Ereignis basierend auf der Ereignisstartzeit  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie dann eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften**wird angezeigt.  
  
    > [!NOTE]  
    >  Bei der Auswahl von **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten**wird das Dialogfeld **Ablaufverfolgungseigenschaften**nicht angezeigt. Stattdessen beginnt die Ablaufverfolgung. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras**auf **Optionen**, und deaktivieren Sie das Kontrollkästchen **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** .  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Geben Sie im Feld **Vorlage verwenden**eine Ablaufverfolgungsvorlage aus.  
  
4.  Geben Sie optional ein Ziel für die Ablaufverfolgungsergebnisse an.  
  
5.  Klicken Sie im Menü **Ereignisauswahl**auf die Spaltenüberschrift **StartTime** . Sie können auch mit der rechten Maustaste auf die Spaltenüberschrift klicken und dann auf **Spaltenfilter bearbeiten** klicken, um das Dialogfeld **Filter bearbeiten** zu starten.  
  
6.  Erweitern Sie **größer als** oder **kleiner als**, und geben Sie dann einen `datetime` Wert in das Feld ein, das unterhalb des Vergleichs Operators angezeigt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
