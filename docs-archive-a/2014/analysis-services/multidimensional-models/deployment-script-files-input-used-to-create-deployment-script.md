---
title: Grundlegendes zu den zum Erstellen des Bereitstellungs Skripts verwendeten Eingabedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618378"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a>Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien
  Wenn Sie ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt erstellen, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generiert XML-Dateien für das Projekt. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] legt diese XML-Dateien im Ausgabeordner des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Projekts ab. Standardmäßig erfolgt die Ausgabe in den Ordner \Bin. In der folgenden Tabelle werden die von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellten Dateien aufgeführt.  
  
|XMLA-Datei|BESCHREIBUNG|  
|---------------|-----------------|  
|\<*project name*>. asdatabase|Enthält die deklarativen Definitionen für alle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte im Projekt.|  
|\<*project name*>deploymenttargets|Enthält den Namen der Instanz und der Datenbank von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in der die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte erstellt werden.|  
|\<*project name*>. configsettings|Enthält umgebungsspezifische Einstellungen wie Verbindungsinformationen für die Datenquelle und Speicherorte für die Objektspeicherung. Einstellungen in dieser Datei überschreiben die Einstellungen in der \<*project name*> . asdatabase-Datei.|  
|\<*project name*>. deploymentoptions|Enthält Bereitstellungsoptionen, z. B. ob es sich um eine Transaktionsbereitstellung handelt und ob die bereitgestellten Objekte nach der Bereitstellung verarbeitet werden sollen.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] speichert Kennwörter nie in den Projektdateien.  
  
## <a name="modifying-the-input-files"></a>Ändern der Eingabedateien  
 Durch Ändern der Werte in den Eingabedateien oder der aus den Eingabedateien abgerufenen Werte können das Bereitstellungs Ziel, die Konfigurationseinstellungen und die Bereitstellungs Optionen geändert werden, ohne die gesamte \<*project name*> ASDATABASE-Datei zu bearbeiten (oder eine gesamte XMLA-Skriptdatei, wenn Sie ein Skript aus einer vorhandenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank generieren). Durch die Möglichkeit, einzelne Dateien zu ändern, können Sie auf einfache Weise verschiedene Bereitstellungsskripts für unterschiedliche Zwecke erstellen.  
  
 In den folgenden Themen wird erläutert, wie Sie Werte in den verschiedenen Eingabedateien ändern:  
  
-   [Angeben des Installationszieles](deployment-script-files-specifying-the-installation-target.md)  
  
-   [Angeben von Bereitstellungsoptionen für Partitionen und Rollen](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [Angeben von Verarbeitungsoptionen](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen des Bereitstellungs-Assistenten für Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Grundlegendes zum Analysis Services-Bereitstellungsskript](understanding-the-analysis-services-deployment-script.md)  
  
  
