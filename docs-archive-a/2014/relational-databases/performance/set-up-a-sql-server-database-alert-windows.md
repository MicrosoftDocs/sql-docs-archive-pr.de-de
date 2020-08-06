---
title: Einrichten einer SQL Server-Datenbankwarnung (Windows) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 090eeda2c134857df18d083ce06d460214aa4dfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622604"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a>Einrichten einer SQL Server-Datenbankwarnung (Windows)
  Sie können mithilfe des Systemmonitors eine Warnung erstellen, die ausgelöst wird, wenn ein Schwellenwert für einen Leistungsindikator des Systemmonitors erreicht wird. Als Reaktion auf die Warnung kann der Systemmonitor eine Anwendung starten, wie z. B. eine benutzerdefinierte Anwendung, die für das Verarbeiten der Warnung geschrieben wurde. Sie können beispielsweise eine Warnung erstellen, die ausgelöst wird, wenn die Anzahl der Deadlocks einen bestimmten Wert überschreitet.  
  
 Warnungen können auch mit Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent definiert werden. Weitere Informationen finden Sie unter [Warnungen](../../ssms/agent/alerts.md).  
  
### <a name="to-set-up-a-sql-server-database-alert"></a>So richten Sie eine SQL Server-Datenbankwarnung ein  
  
1.  Erweitern Sie in der Navigationsstruktur des Fensters Leistung die Option **Leistungsprotokolle und Warnungen**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Warnungen**, und klicken Sie dann auf **Neue Warnungseinstellungen**.  
  
3.  Geben Sie im Dialogfeld **Neue Warnungseinstellungen** einen Namen für die neue Warnung ein, und klicken Sie dann auf **OK**.  
  
4.  Fügen Sie im Dialogfeld für die neue Warnung auf der Registerkarte **Allgemein** einen **Kommentar**hinzu, und klicken Sie auf **Hinzufügen** , um der Warnung einen Leistungsindikator hinzuzufügen.  
  
     Jede Warnung muss mindestens einen Leistungsindikator aufweisen.  
  
5.  Wählen Sie im Dialogfeld Leistungsindikatoren hinzufügen in der Liste **Leistungsobjekt** ein SQL Server-Objekt aus, und wählen Sie dann in der Liste **Leistungsindikatoren wählen**einen Leistungsindikator aus.  
  
6.  Klicken Sie auf **Hinzufügen**, um der Warnung den Leistungsindikator hinzuzufügen. Sie können weitere Leistungsindikatoren hinzufügen, oder klicken Sie auf **Schließen** , um zum Dialogfeld für die neue Warnung zurückzukehren.  
  
7.  Klicken Sie im Dialogfeld für die neue Warnung in der Liste **Warnung bei Wert** auf **größer als**oder **kleiner als** , und geben Sie dann in das Feld **Limit**einen Schwellenwert ein.  
  
     Die Warnung wird generiert, wenn der Wert für den Leistungsindikator größer oder kleiner als der Schwellwert ist (je nachdem, ob Sie auf **größer als** oder **kleiner als**geklickt haben).  
  
8.  Legen Sie in den Feldern **Daten erfassen alle** die Stichprobenfrequenz fest.  
  
9. Legen Sie auf der Registerkarte **Aktion** die Aktionen fest, die jedes Mal ausgeführt werden, wenn die Warnung ausgelöst wird.  
  
10. Legen Sie auf der Registerkarte **Zeitplan** den Beginn und das Ende des Zeitplans für die Warnungssuche fest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server-Datenbankwarnung](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
