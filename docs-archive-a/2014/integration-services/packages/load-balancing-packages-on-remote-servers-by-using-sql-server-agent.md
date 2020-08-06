---
title: Lastenausgleich von Paketen auf Remoteservern mithilfe des SQL Server-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea7b132d8cf86d2f211da25989df937d0db34ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619193"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a>Lastenausgleich von Paketen auf Remoteservern mithilfe des SQL Server-Agents
  Müssen viele Pakete ausgeführt werden, ist es praktisch, hierfür andere verfügbare Server zu verwenden. Diese Methode, bei der zum Ausführen von Paketen andere Server verwendet werden, während die Steuerung der Pakete über ein übergeordnetes Paket erfolgt, wird als Lastenausgleich bezeichnet. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] wird der Lastenausgleich manuell ausgeführt, wobei die Struktur des Verfahrens von den Besitzern der Pakete festgelegt werden muss. Dabei wird der Lastenausgleich nicht automatisch von den Servern ausgeführt. Des Weiteren müssen die auf den Remoteservern ausgeführten Pakete vollständige Pakete sein. Einzelne Tasks anderer Pakete sind dabei nicht zulässig.  
  
 Der Lastenausgleich ist in den folgenden Szenarien nützlich:  
  
-   Die Pakete können alle gleichzeitig ausgeführt werden.  
  
-   Die Pakete sind umfangreich, und wenn sie nacheinander ausgeführt werden, kann es sein, dass die Ausführung länger dauert als die zulässige Verarbeitungszeit.  
  
 Administratoren und Architekten können bestimmen, ob das Verwenden zusätzlicher Server zum Verarbeiten zur Verbesserung der Prozesse beiträgt.  
  
## <a name="illustration-of-load-balancing"></a>Abbildung des Lastenausgleichs  
 Im folgenden Diagramm wird ein übergeordnetes Paket auf einem Server angezeigt. Das übergeordnete Paket enthält mehrere Tasks Auftrag des SQL Server-Agents ausführen. Mit jedem Task des übergeordneten Pakets wird ein SQL Server-Agent auf einem Remoteserver aufgerufen. Diese Remoteserver enthalten SQL Server-Agent-Aufträge, die einen Schritt für den Aufruf eines Pakets auf diesem Server beinhalten.  
  
 ![Architektur für den SSIS-Lastenausgleich (Übersicht)](../media/loadbalancingoverview.gif "Architektur für den SSIS-Lastenausgleich (Übersicht)")  
  
 Die in dieser Architektur für den Lastenausgleich erforderlichen Schritte stellen keine neuen Konzepte dar. Der Lastenausgleich wird nämlich erreicht, indem vorhandene Konzepte und allgemeine SSIS-Objekte auf neue Art und Weise verwendet werden.  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a>Ausführen von Paketen auf einer Remoteinstanz mithilfe des SQL Server-Agents  
 In der Basisarchitektur für die Remoteausführung von Paketen befindet sich auf der SQL Server-Instanz ein zentrales Paket, mit dem andere Remotepakete gesteuert werden. Im Diagramm wird dieses zentrale Paket, das so genannte übergeordnete SSIS-Paket, angezeigt. Die Instanz, in der sich dieses übergeordnete Paket befindet, steuert die Ausführung von SQL Server-Agent-Aufträgen, mit denen die untergeordneten Pakete ausgeführt werden. Dabei werden die untergeordneten Pakete nicht nach einem festen Zeitplan ausgeführt, der vom SQL Server-Agent auf dem Remoteserver gesteuert wird. Die untergeordneten Pakete werden stattdessen beim Aufruf über das übergeordnete Paket vom SQL Server-Agent gestartet und auf derselben SQL Server-Instanz ausgeführt, auf der sich der SQL Server-Agent befindet.  
  
 Bevor Sie mit dem SQL Server-Agent ein Remotepaket ausführen können, müssen Sie das übergeordnete Paket und die untergeordneten Pakete konfigurieren und die zum Steuern der untergeordneten Pakete verwendeten SQL Server-Agent-Aufträge festlegen. In den folgenden Abschnitten werden weitere Informationen zum Erstellen, Konfigurieren, Ausführen und Verwalten von auf Remoteservern ausgeführten Paketen bereitgestellt. Dieser Prozess beinhaltet die folgenden Schritte:  
  
-   Erstellen und Installieren der untergeordneten Pakete auf Remoteservern.  
  
-   Erstellen der SQL Server-Agent-Aufträge auf Remoteinstanzen, mit denen die Pakete ausgeführt werden.  
  
-   Erstellen des übergeordneten Pakets.  
  
-   Festlegen des Protokollierungsszenarios für die untergeordneten Pakete.  
  
 In der folgenden Tabelle werden Links zu Themen bereitgestellt, mit denen Sie durch den Prozess begleitet werden.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Implementierung von untergeordneten Paketen](../implementation-of-child-packages.md)|Beschreibt die Installation von Paketen und die Erstellung der SQL Server-Agent-Aufträge zum Ausführen der Pakete.|  
|[Implementierung des übergeordneten Pakets](../implementation-of-the-parent-package.md)|Beschreibt die Erstellung des übergeordneten Pakets, in dem viele Tasks "Auftrag des SQL Server-Agents ausführen" enthalten sind. Mit jedem dieser Tasks wird jeweils ein untergeordnetes Paket ausgeführt.|  
|[Protokollierung für Pakete auf Remoteservern, für die ein Lastenausgleich ausgeführt wurde](../logging-for-load-balanced-packages-on-remote-servers.md)|Beschreibt das Protokollierungsszenario für die Remotepakete.|  
  
## <a name="related-tasks"></a>Related Tasks  
 [Planen eines Pakets mit SQL Server-Agent](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
