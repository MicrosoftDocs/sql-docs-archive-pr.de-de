---
title: Zugriff auf den Integration Services-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7dd6fbed4bedc285069306ab4c400f0f67f9f293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610025"
---
# <a name="access-to-the-integration-services-service"></a>Zugriff auf den Integration Services-Dienst
  Über Paketschutzebenen kann gesteuert werden, wer ein Paket bearbeiten und ausführen darf. Zusätzlicher Schutz ist erforderlich, um die Anzahl der Personen einzuschränken, die die Liste der derzeit auf einem Server ausgeführten Pakete anzeigen und die Paketausführung in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]beenden dürfen.  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst zum Auflisten der ausgeführten Pakete verwendet. Mitglieder der Gruppe der Windows-Administratoren können alle aktuell ausgeführten Pakete anzeigen und ihre Ausführung beenden. Benutzer, die nicht zur Administratoren-Gruppe gehören, können nur solche ausgeführten Pakete anzeigen und deren Ausführung beenden, wenn sie selbst die Ausführung gestartet haben.  
  
 Es ist wichtig, den Zugriff auf Computer einzuschränken, auf denen ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst ausgeführt wird. Dies gilt besonders für einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst, der Remoteordner auflisten kann. Jeder authentifizierte Benutzer kann die Auflistung von Paketen anfordern. Auch wenn der Dienst den Dienst nicht findet, listet der Dienst Ordner auf. Diese Ordnernamen können für böswillige Benutzer von Nutzen sein. Wenn ein Administrator den Dienst so konfiguriert hat, dass Ordner auf einem Remotecomputer aufgelistet werden, können die Benutzer auch Ordnernamen anzeigen, die sie normalerweise nicht anzeigen könnten.  
  
  
