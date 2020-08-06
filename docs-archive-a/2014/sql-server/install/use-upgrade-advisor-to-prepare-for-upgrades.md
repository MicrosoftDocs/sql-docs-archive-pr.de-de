---
title: Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e53d895cb19a172d0810ae9d6c2bda3406732da1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700575"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a>Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades
  Mit dem Upgrade Advisor von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie Upgrades auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vorbereiten. Upgrade Advisor analysiert die installierten Komponenten früherer Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und generiert einen Bericht mit den Problemen, die entweder vor oder nach dem Upgrade behoben werden müssen.  
  
## <a name="how-upgrade-advisor-works"></a>Funktionsweise des Upgrade Advisors  
 Wenn Sie Upgrade Advisor ausführen, wird die Startseite des Upgrade Advisors angezeigt. Sie können von der Startseite aus die folgenden Tools ausführen:  
  
-   Analyse-Assistent des Upgrade Advisors  
  
-   Berichts-Viewer des Upgrade Advisors  
  
-   Hilfe zum Upgrade Advisor  
  
 Führen Sie bei der erstmaligen Verwendung des Upgrade Advisors den Analyse-Assistenten des Upgrade Advisors aus, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten zu analysieren. Wenn der Assistent die Analyse abgeschlossen hat, können die resultierenden Berichte im Berichts-Viewer des Upgrade Advisors angezeigt werden. Jeder Bericht bietet Links zu Informationen in der Hilfe zum Upgrade Advisor, mit denen Sie bekannte Probleme beheben oder ihre Auswirkungen reduzieren können.  
  
## <a name="upgrade-advisor-analysis"></a>Analyse mit dem Upgrade Advisor  
 Der Upgrade Advisor analysiert die folgenden Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 Bei der Analyse werden die Objekte überprüft, auf die zugegriffen werden kann, z. B. Skripts, gespeicherte Prozeduren, Trigger und Ablaufverfolgungsdateien. Der Upgrade Advisor kann keine Desktopanwendungen und verschlüsselten gespeicherten Prozeduren analysieren.  
  
 Die Ausgabe erfolgt als XML-Bericht. Zeigen Sie den XML-Bericht mithilfe des Berichts-Viewers des Upgrade Advisors an.  
  
> [!NOTE]  
>  Berichte können ein "other upgrade issues"-Element enthalten. Dieses Element ist mit einer Liste von Problemen verknüpft, die vom Upgrade Advisor nicht erkannt werden, jedoch möglicherweise auf dem Server oder in den Anwendungen vorhanden sind. Sie müssen die Liste nicht erkennbarer Probleme überprüfen und bestimmen, ob Sie aufgrund der nicht erkennbaren Probleme Änderungen am Server oder an den Anwendungen vornehmen müssen.  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a>Installieren und Ausführen des Upgrade Advisors  
 Der Speicherort für das Installieren des Upgrade Advisors für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist abhängig davon, was analysiert werden soll. Upgrade Advisor unterstützt die Remoteanalyse aller unterstützten Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, können Sie den Upgrade Advisor auf einem beliebigen Computer installieren, der eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen kann und die Voraussetzungen des Upgrade Advisors erfüllt. Weitere Informationen finden Sie unter [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Der Upgrade Advisor ist in einem Feature Pack verfügbar.  
  
 Die Voraussetzungen für die Installation und Ausführung von Upgrade Advisor lauten wie folgt:  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2, Windows 7 SP1 und [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.  
  
-   Windows Installer ab Version 4.5. Sie können Windows Installer von der [Windows Installer Website](https://www.microsoft.com/download/details.aspx?id=8483)installieren.  
  
-   Microsoft .NET Framework 4. .NET Framework 4 ist auf dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Produkt Medium und auf der [Downloadseite für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=209895)verfügbar.  
  
    -   Um .NET Framework 4 von den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Medien zu installieren, suchen Sie das Stammverzeichnis des Datenträgerlaufwerks. Doppelklicken Sie dann auf den Ordner \redist und auf den Ordner DotNetFrameworks, und führen Sie dotNetFx40_Full_x86_x64.exe aus (für 32-Bit- oder für 64-Bit-Betriebssysteme).  
  
 Klicken Sie auf der Downloadseite auf die Schaltfläche zum Herunterladen, um den Upgrade Advisor aus dem Web zu installieren. Sie können die Installation sofort ausführen oder die Datei SQLUA.msi speichern, um die Installation später auszuführen. Wenn Sie von der Produkt-CD installieren, führen Sie SQLUA.msi direkt vom Produkt Datenträger aus.  
  
 Nachdem Sie den Upgrade Advisor installiert haben, können Sie ihn über das **Startmenü** öffnen:  
  
-   Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] , und klicken Sie dann auf ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.  
  
 Weitere Informationen finden Sie in der Dokumentation im Upgrade Advisor-Download sowie in den Versionshinweisen zu [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit mehreren Versionen und Instanzen von SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [Unterstützte Versions- und Editionsupgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Abwärtskompatibilität](../../../2014/getting-started/backward-compatibility.md)  
  
  
