---
title: Installieren von Updates an der Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3ced6cd72bfc972743d0f9d8c7c2a9ce57dfdd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609395"
---
# <a name="installing-updates-from-the-command-prompt"></a>Installieren von Updates an der Eingabeaufforderung
  Testen und ändern Sie die Installationsskripts, um die Anforderungen Ihrer Organisation zu erfüllen.  
  
## <a name="sample-syntax-for-installation"></a>Beispielsyntax zur Installation  
 Der Name des Updatepakets kann variieren und enthält möglicherweise Komponenten zu Sprache, Version und Prozessor. Anwenden eines Updates über eine Eingabeaufforderung. Dabei wird <Paketname> mit dem Namen des Updatepakets ersetzt:  
  
-   Aktualisieren einer einzelnen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und aller freigegebenen Komponenten wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Verwaltungstools: Sie können die Instanz entweder mit dem InstanceName-Parameter oder dem InstanceID-Parameter angeben. Um eine vorbereitete Instanz von zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie den instanceId-Parameter<package_name # C1.exe/QS/IAcceptSQLServerLicenseTerms/Action = Patch/instanceName = MyInstance oder <package_name # C3.exe/QS/IAcceptSQLServerLicenseTerms/Action = Patch/InstanceId = angeben \<Instance ID> .  
  
-   Setup ist in der Lage, die neuesten Produktupdates in die Installation des Hauptprodukts zu integrieren, sodass das Hauptprodukt und geeignete Updates gleichzeitig installiert werden. Sie können eine Installation der Datenbank-Engine-Instanz für das Produkt Update vorbereiten: setup.exe/q/IAcceptSQLServerLicenseTerms/Action = prepareImage/UpdateEnabled = true/UpdateEnabled = true/UpdateSource = \<path where the update is downloaded> /InstanceId = \<Instance ID> /Features = SQLEngine.  
  
-   Aktualisierung nur von freigegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten, wie z. B. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Verwaltungstools: <Paketname>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
  
-   Aktualisieren aller Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Computer und aller freigegebenen Komponenten, wie z. B. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Verwaltungstools: <Paketname>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.  
  
 Entfernen eines Updates über eine Eingabeaufforderung. Dabei wird <Paketname> mit dem Namen des Updatepakets ersetzt:  
  
-   Entfernen eines Updates aus einer einzelnen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und aus allen freigegebenen Komponenten, z. B. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Verwaltungstools: <Paketname>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.  
  
-   Ausschließliches Entfernen eines Updates aus freigegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten, z. B. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Verwaltungstools: <Paketname>.exe /qs /Action=RemovePatch  
  
    > [!NOTE]  
    >  Mit dem Updateinstallationsprogramm wird sichergestellt, dass die freigegebenen Komponenten stets mindestens die Version der Instanz auf höchster Ebene aufweisen.  
  
## <a name="supported-command-prompt-parameters"></a>Unterstützte Befehlszeilenparameter  
  
> [!IMPORTANT]  
>  Anmeldeinformationen sollten nach Möglichkeit zur Laufzeit angegeben werden. Wenn Sie Anmeldeinformationen in einer Skriptdatei speichern müssen, sollten Sie die Datei schützen, um nicht autorisierten Zugriff zu verhindern.  
  
|Schalter|BESCHREIBUNG|  
|------------|-----------------|  
|**/?**|Zeigt Hilfe zur unbeaufsichtigten Installation an der Eingabeaufforderung an.|  
|**/action=Patch oder /action=RemovePatch**|Gibt die Installationsaktion an: Patch oder RemovePatch.|  
|**/allinstances**|Wendet das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Update auf alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und auf alle freigegebenen, nicht instanzabhängigen Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an.|  
|**/instanceName = instanceName** <sup>1</sup>|Wendet das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Update auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Namen InstanceName und auf alle freigegebenen, nicht instanzabhängigen Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an.|  
|**/InstanceID=Inst1**|Wendet das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Update auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Inst1 und auf alle freigegebenen, nicht instanzabhängigen Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an.|  
|**/quiet**|Führt Setup für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Update im unbeaufsichtigten Modus aus.|  
|**/qs**|Zeigt nur das Statusdialogfeld in der Benutzeroberfläche an.|  
|**/UpdateEnabled**|Gibt an, ob Produktupdates von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ermittelt und eingeschlossen werden sollen. Gültige Werte sind True und False oder 1 und 0. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup schließt standardmäßig alle gefundenen Updates ein.|  
|**/IAcceptSQLServerLicenseTerms**|Nur erforderlich, wenn der /Q-Parameter oder der /QS-Parameter für die unbeaufsichtigte Installation angegeben wird.|  
  
 <sup>1</sup> Sie können diesen Parameter nicht angeben, um ein Update auf eine vorbereitete Instanz von anzuwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie müssen stattdessen den /instanceID-Parameter angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über die SQL Server-Wartungsinstallation](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  
