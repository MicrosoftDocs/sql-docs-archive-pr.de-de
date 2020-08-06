---
title: Überlegungen zur Installation von SQL Server mit SysPrep | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e1792eeb-2874-4653-b20e-3063f4eb4e5d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 537bb3c55990a68f17697789953c4f15fe023434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701558"
---
# <a name="considerations-for-installing-sql-server-using-sysprep"></a>Überlegungen zur Installation von SQL Server mit SysPrep
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep ermöglicht Ihnen die Vorbereitung einer eigenständigen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem Computer und den Abschluss der Konfiguration zu einem späteren Zeitpunkt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep umfasst einen aus zwei Schritten bestehenden Prozess zur Konfiguration einer eigenständigen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Schritte umfassen Folgendes:  
  
-   [Vorbereiten eines Images](#BKMK_PrepareImage)  
  
     Dieser Schritt beendet den Installationsvorgang, nachdem die Produktbinärdateien installiert wurden, ohne den Computer, das Netzwerk oder kontospezifische Informationen für die vorzubereitende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz zu konfigurieren.  
  
-   [Abschließen des Images](#BKMK_CompleteImage)  
  
     In diesem Schritt können Sie die Konfiguration einer vorbereiteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]abschließen. Während dieses Schritts können Sie Informationen zum Computer, zum Netzwerk und zum Konto bereitstellen.  
  
 Weitere Informationen zum Installieren von mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syationp finden Sie unter [Install SQL Server 2014 using syationp](install-sql-server-using-sysprep.md).  
  
## <a name="common-uses-for-ssnoversion-sysprep"></a>Allgemeine Verwendungsmöglichkeiten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 Sie können die SysPrep-Funktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie folgt verwenden:  
  
-   Mit dem Schritt "Image vorbereiten" können Sie eine oder mehrere nicht konfigurierte Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem gleichen Computer vorbereiten. Sie können diese vorbereiteten Instanzen mit dem Schritt "Image abschließen" auf demselben Computer konfigurieren.  
  
-   Sie können die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupkonfigurationsdatei der vorbereiteten Instanz erfassen und sie verwenden, um zusätzliche nicht konfigurierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen auf mehreren Computern für eine spätere Konfiguration vorzubereiten.  
  
-   In Verbindung mit dem Windows-Systemvorbereitungstool (auch als Windows SysPrep bezeichnet) können Sie ein Image des Betriebssystems einschließlich der nicht konfigurierten vorbereiteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Quellcomputer erstellen. Dann können Sie das Betriebssystemimage auf mehreren Computern bereitstellen. Nachdem Sie die Konfiguration des Betriebssystems abgeschlossen haben, können Sie die vorbereiteten Instanzen mit dem Schritt "Image abschließen" von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup konfigurieren.  
  
     Das Windows SysPrep-Tool wird verwendet, um Windows-Betriebssystemimages vorzubereiten. Es wird verwendet, um ein benutzerdefiniertes Image des Betriebssystems aufzuzeichnen, das überall in einer Organisation bereitgestellt werden kann. Weitere Informationen zu SysPrep und den Verwendungsmöglichkeiten finden Sie unter [Erläuterungen zu SysPrep](https://go.microsoft.com/fwlink/?LinkId=143546).  
  
## <a name="installation-media-considerations"></a>Überlegungen zu Installationsmedien  
 Wenn Sie eine Vollversion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden, berücksichtigen Sie Folgendes:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen außer Express Edition:  
  
    -   Der Schritt "Image vorbereiten" verwendet die Evaluierungsedition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Produktbinärdateien zu installieren. Nach dem Abschließen der Instanz hängt die Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von der Produkt-ID ab, die während des Schritts "Image abschließen" bereitgestellt wurde.  
  
    -   Wenn Sie eine Produkt-ID für die Evaluierungsedition bereitstellen, wird der Evaluierungszeitraum so festgelegt, dass er 180 Tage nach dem Abschließen der vorbereiteten Instanz abläuft.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Express-Editionen:  
  
    -   Um eine Instanz einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express-Edition vorzubereiten, verwenden Sie die Express-Installationsmedien.  
  
    -   Sie können keine Produkt-IDs für eine vorbereitete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express-Editionen angeben.  
  
## <a name="supported-ssnoversion-installations"></a>Unterstützte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationen  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt SysPrep alle Funktionen und Tools von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Sie können mehrere Instanzen für parallele Installationen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder früheren Versionen vorbereiten. Die Funktionen dieser Instanzen müssen SysPrep unterstützen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wird am Ende des Schritts "Image vorbereiten" automatisch installiert und abgeschlossen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer werden automatisch vorbereitet, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie werden abgeschlossen, wenn Sie mithilfe des Schritts "Image abschließen" die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz abschließen.  
  
 Informationen zu den unterstützten Editionen von finden Sie unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [von den-Editionen unterstützte Funktionen SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Beim Konfigurieren einer vorbereiteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können Sie ein Editionsupgrade ausführen. Diese Option wird nicht für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express-Editionen unterstützt.  
  
 Ab [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failoverclusterinstallationen über die Befehlszeile.  
  
## <a name="ssnoversion-sysprep-limitations"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 Das Reparieren einer vorbereiteten Instanz wird nicht unterstützt. Wenn Setup während des Schritts "Vorbereiten eines Images" oder "Abschließen des Images" fehlschlägt, müssen Sie die Deinstallation ausführen.  
  
##  <a name="prepare-image"></a><a name="BKMK_PrepareImage"></a> Vorbereiten eines Images  
 Während des Schritts zur Imagevorbereitung werden das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produkt und die zugehörigen Funktionen installiert, die Installation wird jedoch nicht konfiguriert.  
  
 Die zu installierenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen und der Installationsort für die Installationsdateien des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produkts können während dieses Schritts angegeben werden. Sie können eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit der Option **Vorbereiten eines Images von einer eigenständigen Instanz für die SysPrep-Bereitstellung** auf der Seite **Erweitert** des **Installationscenters** oder von der Eingabeaufforderung vorbereiten.  
  
-   Sie können mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf demselben Computer vorbereiten, und sie können später abgeschlossen werden.  
  
-   Sie können für SysPrep-Installationen den vorhandenen vorbereiteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützte Funktionen hinzufügen oder sie aus ihnen entfernen.  
  
 Nach der Vorbereitung der Instanz wird eine Verknüpfung im **Startmenü** verfügbar, mit der Sie die Konfiguration der vorbereiteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]abschließen können.  
  
##  <a name="complete-image"></a><a name="BKMK_CompleteImage"></a> Abschließen des Images  
 Sie können die vorbereiteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit beiden der folgenden Methoden abschließen:  
  
-   Verwenden Sie die Verknüpfung im Startmenü.  
  
-   Greifen Sie auf den Schritt **Abschließen eines Images von einer vorbereiteten eigenständigen Instanz** auf der Seite **Erweitert** des **Installationscenters**zu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)  
  
  
