---
title: Protokollversand-Überwachungseinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725865"
---
# <a name="log-shipping-monitor-settings"></a>Protokollversand-Überwachungseinstellungen
  Mithilfe dieser Seite können Sie die Eigenschaften des Protokollversand-Überwachungsservers konfigurieren und ändern.  
  
 Eine Erläuterung zu den Konzepten des Protokollversands finden Sie unter [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 **Überwachungsserverinstanz**  
 Zeigt den Namen der Serverinstanz an, die zurzeit als Überwachungsserver für die Protokollversandkonfiguration konfiguriert ist.  
  
 **Herstellen einer Verbindung**  
 Wählen Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus, die als Überwachungsserver verwendet werden soll, und stellen Sie die entsprechende Verbindung her. Das zum Verbinden verwendete Konto muss Mitglied der festen Serverrolle sysadmin auf der sekundären Serverinstanz sein.  
  
 **Identität des Auftragsproxykontos annehmen (normalerweise ist dies das Dienstkonto des SQL Server-Agents der Serverinstanz, in der der Auftrag ausgeführt wird)**  
 Legt fest, dass der Protokollversand beim Verbinden mit der Überwachungsserverinstanz die Identität des vom SQL Server-Agent verwendeten Proxykontos annimmt. Stellen Sie sicher, dass Sicherungs-, Kopier- und Wiederherstellungsprozesse eine Verbindung mit dem Überwachungsserver herstellen können, damit der Status der Protokollversandvorgänge aktualisiert werden kann.  
  
 **Folgende SQL Server-Anmeldung verwenden**  
 Ermöglichen Sie dem Protokollversand beim Herstellen der Verbindung mit der Überwachungsserverinstanz die Verwendung einer bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung. Stellen Sie sicher, dass Sicherungs-, Kopier- und Wiederherstellungsprozesse eine Verbindung mit dem Überwachungsserver herstellen können, damit der Status der Protokollversandvorgänge aktualisiert werden kann. Wählen Sie diese Option aus, wenn der Protokollversand eine bestimmte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung verwenden soll, und geben Sie dann den Anmeldenamen und das Kennwort an.  
  
 **Verlauf löschen nach**  
 Geben Sie an, für welchen Zeitraum die Verlaufsinformationen des Protokollversands auf dem Überwachungsserver aufbewahrt werden, bevor sie gelöscht werden.  
  
 **Auftragsname**  
 Gibt den Namen des vom SQL Server-Agent bereitgestellten Warnungsauftrags an, mit dem der Protokollversand Warnungen auslöst, wenn beim Sichern oder Wiederherstellen Schwellenwerte überschritten werden. Wenn Sie den Auftrag erstmalig erstellen, können Sie den Namen durch Eingabe in das entsprechende Feld ändern.  
  
 **Zeitplan**  
 Gibt den aktuellen Zeitplan des vom SQL Server-Agent bereitgestellten Warnungsauftrags an.  
  
 **Bearbeiten**  
 Ändert die Parameter des vom SQL Server-Agent bereitgestellten Warnungsauftrags.  
  
 **Diesen Auftrag deaktivieren**  
 Hält den vom SQL Server-Agent bereitgestellten Warnungsauftrag an.  
  
  
