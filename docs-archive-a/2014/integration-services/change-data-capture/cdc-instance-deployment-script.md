---
title: CDC Instance Deployment Script | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6deea884168c2329e312eeaa2be16c28a955cca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724878"
---
# <a name="cdc-instance-deployment-script"></a>CDC Instance Deployment Script
  In diesem Abschnitt wird das Dialogfeld CDC Instance Deployment Script beschrieben, in dem das Bereitstellungsskript der CDC-Instanz angezeigt wird. Dieses Skript kann verwendet werden, um die CDC-Datenbank mit ihren Artefakten auf einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz neu zu erstellen.  
  
 Nach Abschluss des Bereitstellungsskripts sollten Sie Folgendes sicherstellen:  
  
-   Das Bereitstellungsskript setzt voraus, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz für Oracle CDC mit der Oracle CDC Service Configuration Console oder mit dem vom Programm erstellten **prepare script** (Vorbereitungsskript) vorbereitet wurde.  
  
-   Der Teil des Skripts, der zum Aktivieren der Datenbank für CDC verwendet wird, muss von einem `sysadmin`ausgeführt werden.  
  
-   Das Skript behält das Oracle Log Mining-Kennwort nicht bei. Das Kennwort muss manuell festgelegt werden, nachdem das Skript ausgeführt und der Oracle CDC Service gestartet wurde.  
  
 Aktivieren Sie im Dialogfeld **CDC Instance Deployment Script** die folgenden Optionen.  
  
 **Speichern unter**  
 Speichert das Skript in einer Textdatei, die Sie an einem beliebigen Speicherort ablegen können. Sie können die Datei mit dem Skript auf einen beliebigen anderen Server kopieren, um es dort auszuführen.  
  
 **Copy**  
 Kopiert das Skript in die Zwischenablage. Sie können das Skript dann in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder einen beliebigen Texteditor einfügen, um die Skripts später auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorbereiten von SQL Server für CDC](prepare-sql-server-for-cdc.md)  
  
  
