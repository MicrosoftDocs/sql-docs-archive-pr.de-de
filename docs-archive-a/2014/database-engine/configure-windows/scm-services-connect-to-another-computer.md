---
title: Herstellen einer Verbindung mit einem anderen Computer (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622887"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a>Herstellen einer Verbindung mit einem anderen Computer (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]eine Verbindung mit einem anderen Computer herstellen können. Befolgen Sie die erste Prozedur, um die Computerverwaltung von Windows, MMC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console) zu öffnen, stellen Sie eine Verbindung zu dem Computer her, und erweitern die Struktur "Dienste und Anwendungen". Führen Sie das zweite Verfahren zum Erstellen einer Datei mit einem Link zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf einem Remotecomputer aus.  
  
> [!NOTE]  
>  Bei einer Remoteverbindung können einige Aktionen nicht von Configuration Manager ausgeführt werden.  
  
 Zum Starten, Stoppen, Anhalten oder Fortsetzen von Diensten auf einem anderen Computer können Sie auch mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zu dem Server herstellen, mit der rechten Maustaste auf den Server oder den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent und anschließend auf die gewünschte Aktion klicken.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>So stellen Sie eine Verbindung mit einem anderen Computer mit der Computerverwaltung von Windows her  
  
1.  Klicken Sie im Menü **Start** mit der rechten Maustaste auf **Arbeitsplatz**, und klicken Sie dann auf **Verwalten**.  
  
2.  Klicken Sie in **Computerverwaltung**mit der rechten Maustaste auf **Computerverwaltung (lokal)**, und klicken Sie dann auf **Verbindung mit anderem Computer herstellen**.  
  
3.  Geben Sie im Dialogfeld **Computer auswählen** in das Textfeld **Anderen Computer** den Namen des Computers ein, den Sie verwalten möchten, und klicken Sie dann auf **OK**.  
  
     Die Computerverwaltung zeigt die Dienste an, die auf dem Remotecomputer ausgeführt werden. Der Knoten der obersten Ebene wird in **Computerverwaltung** \<*remotecomputer*> geändert.  
  
4.  Erweitern Sie in der Konsolenstruktur **Dienste und Anwendungen**, und erweitern Sie dann **SQL Server-Konfigurations-Manager** , um die Dienste des Remotecomputers zu verwalten.  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>So sichern Sie einen Link zu SQL Server-Konfigurations-Manager für einen anderen Computer  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben Sie im Feld **Öffnen** ein, `mmc -a` um die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console im Autoren Modus zu öffnen.  
  
3.  Klicken Sie im Menü **Datei** auf **Snap-In hinzufügen/entfernen**.  
  
4.  Klicken Sie im Fenster **Snap-In hinzufügen/entfernen** auf **Hinzufügen**.  
  
5.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Computerverwaltung** , und klicken Sie dann auf **Hinzufügen**.  
  
6.  Klicken Sie im Dialogfeld **Computerverwaltung** auf **Anderen Computer**, geben Sie den Namen des zu verwaltenden Remotecomputers ein, und klicken Sie dann auf **Fertig stellen**.  
  
7.  Klicken Sie im Dialogfeld **Eigenständiges Snap-In hinzufügen** auf **Schließen**.  
  
8.  Klicken Sie im Fenster **Snap-In hinzufügen/entfernen** auf **OK**.  
  
9. Erweitern Sie **Computer Verwaltung ( ***\<computer name>*** )** und **Dienste und Anwendungen**.  
  
10. Klicken Sie mit der rechten Maustaste auf **SQL Server-Konfigurations-Manager**, und klicken Sie dann auf **Neues Fenster**.  
  
11. Klicken Sie im Menü **Fenster** auf **Konsolenstamm**, um zum ersten Fenster zurückzuwechseln, und löschen Sie das Fenster.  
  
12. Klicken Sie im Menü **Datei** auf **Speichern**unter, und speichern Sie die Datei im gewünschten Ordner mit einem entsprechenden Namen mit der `.msc` Dateierweiterung. Schließen Sie das Fenster [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.  
  
13. Doppelklicken Sie auf die Datei, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf dem Zielcomputer zu öffnen. Speichern Sie gegebenenfalls einen Link zu der Datei auf dem Desktop oder im Menü **Start** .  
  
> [!CAUTION]  
>  Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf einem Remotecomputer verwenden, ist der Computername nicht offensichtlich, und es ist möglich, versehentlich den falschen Computer zu stoppen oder zu konfigurieren. Überprüfen Sie auf der Registerkarte **Dienst** das Feld **Hostname** , um den Computernamen zu überprüfen, bevor Sie einen Dienst ändern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
