---
title: 'Vorgehensweise: Ausführen des Analyse-Assistenten für den Upgrade Advisor | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Analysis Wizard
ms.assetid: d7d2a1e2-1179-4c05-9b0f-555b04dd1199
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7c3e5e8a52c3b166b076aedb122e68f860037edf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621842"
---
# <a name="how-to-run-the-upgrade-advisor-analysis-wizard"></a>Gewusst wie: Ausführen des Analyse-Assistenten des Upgrade Advisors
  Der Analyse-Assistent des Upgrade Advisors wird über die Startseite des Upgrade Advisors gestartet. In diesem Thema wird beschrieben, wie Sie den Analyse-Assistenten des Upgrade Advisors ausführen.  
  
> [!IMPORTANT]
>  Wenn Sie den Analyse-Assistenten des Upgrade Advisors ausführen, speichert Upgrade Advisor die Berichte im Standardberichtsordner. Der Berichts-Viewer zeigt jedoch nur die fünf zuletzt gespeicherten Berichte an. Der Standard Speicherort für die Berichte lautet meine Dokumente \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade advisor\110\reports.  
  
### <a name="to-run-the-upgrade-advisor-analysis-wizard"></a>So führen Sie den Analyse-Assistenten des Upgrade Advisors aus  
  
1.  Klicken Sie auf der Startseite des Upgrade Advisors auf **Analyse-Assistenten des Upgrade Advisors starten**.  
  
2.  Geben Sie auf der Seite ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten** den Namen des zu überprüfenden Servers in das Feld **Servername** ein, und klicken Sie dann auf **erkennen**. Verwenden Sie die folgenden Richtlinien für den Servernamen:  
  
    -   Um nicht gruppierte Instanzen zu scannen, geben Sie den Computernamen ein.  
  
    -   Um gruppierte Instanzen zu scannen, geben Sie den virtuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Namen ein.  
  
    -   Um nicht gruppierte Komponenten zu scannen, die auf einem Knoten eines Clusters installiert sind, geben Sie den Knoten Namen ein.  
  
    > [!WARNING]  
    >  Verbindungen mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die nicht auf den Standardport für Client-Verbindungen (1433) festgelegt ist, werden vom Upgrade Advisor nicht unterstützt. Wenn Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herstellen möchten, die nicht den Standardport (1433) verwendet, erstellen Sie einen Alias mithilfe die IP-Adresse und des Ports. Weitere Informationen zum Konfigurieren von Client Protokollen und Erstellen eines Alias für- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanzen finden Sie unter [Konfigurieren von Client Protokollen](../../database-engine/configure-windows/configure-client-protocols.md).  
    >   
    >  Wenn Sie nicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Computer installiert haben, auf dem Sie den Upgrade Advisor ausführen, klicken Sie auf **Start**und dann auf Ausführen `cliconfg` . Dadurch wird das Dialogfeld ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Netzwerk-Hilfsprogramm** geöffnet. Verwenden Sie die Registerkarte **Alias** , um den Alias zu erstellen.  
  
3.  Überprüfen Sie die Liste der erkannten Komponenten, ändern Sie die Auswahl nach Bedarf, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Verbindungsparameter** die Instanz von aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie scannen möchten, wählen Sie die Authentifizierungsmethode aus, und geben Sie ggf. Benutzername und Kennwort ein, und klicken Sie dann auf **weiter**.  
  
     Der Name der Standardinstanz lautet MSSQLSERVER.  
  
5.  Geben Sie für ausgewählte Komponenten die angeforderten Informationen ein. Weitere Informationen zu einzelnen Dialogfeldern finden Sie unter [Referenz zur Benutzeroberfläche des Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
6.  Überprüfen Sie auf der Seite **Upgrade Advisor-Einstellungen bestätigen** die von Ihnen eingegebenen Informationen. Wenn Sie den Upgradebericht einreichen möchten, können Sie **Berichte Senden an [!INCLUDE[msCoName](../../includes/msconame-md.md)] ** auswählen. Sie können auch die Datenschutzrichtlinie überprüfen.  
  
7.  Klicken Sie auf **Ausführen** , um die Instanz von zu analysieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
8.  Wenn die Analyse abgeschlossen ist, klicken Sie auf **Bericht starten** , um die erkannten Upgradeprobleme anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Starten des Upgrade Advisors](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Ausführen des Upgrade Advisors &#40;Benutzeroberfläche&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
