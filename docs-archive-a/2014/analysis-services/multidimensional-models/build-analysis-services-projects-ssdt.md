---
title: Erstellen von Analysis Services Projekten (SSDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], building
- Business Intelligence Development Studio, project building [Analysis Services]
ms.assetid: caac03cb-b2b4-4652-8913-3dd39c4b0127
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e447da20df3d7894df1a9afcf4888a4d9799e37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722002"
---
# <a name="build-analysis-services-projects-ssdt"></a>Erstellen von Analysis Services-Projekten (SSDT)
  Sie können in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt auf ähnliche Weise wie ein beliebiges Programmierungsprojekt in Visual Studio erstellen. Beim Erstellen eines Projekts wird eine Gruppe von XML-Dateien im Ausgabeverzeichnis erstellt. Diese XML-Dateien verwenden ASSL (Analysis Services Scripting Language). Hierbei handelt es sich um den XML-Dialekt, den die Clientanwendungen, einschließlich [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , zum Kommunizieren mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz verwenden, um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte zu erstellen oder zu ändern. Diese XML-Dateien werden zum Bereitstellen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objektdefinitionen in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt auf einer angegebenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz verwendet.  
  
## <a name="building-a-project"></a>Erstellen eines Projekts  
 Beim Erstellen eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] im Ausgabeordner eine vollständige Gruppe von XML-Dateien mit allen notwendigen ASSL-Befehlen erstellt, die zum Erstellen aller [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankobjekte im Projekt erforderlich sind. Wenn das Projekt zuvor erstellt und für die aktive Konfiguration die inkrementelle Bereitstellung angegeben wurde, dann wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] außerdem eine XML-Datei mit ASSL-Befehlen zum Ausführen eines inkrementellen Updates für die bereitgestellten Objekte erstellt. Diese XML-Datei wird in den Projektordner \\..\obj\<Aktive Konfiguration>\> geschrieben. Durch inkrementelle Builds können Sie beim Bereitstellen und Verarbeiten eines sehr umfangreichen Projekts oder einer sehr großen Datenbank Zeit sparen.  
  
> [!NOTE]  
>  Mithilfe des Befehls Rebuild All kann die Einstellung für die inkrementelle Bereitstellung ignoriert werden.  
  
 Beim Erstellen eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts werden die Objektdefinitionen im Projekt überprüft. Dabei werden auch sämtliche Assemblys, auf die verwiesen wird, überprüft. Erstellungsfehler werden zusammen mit dem AMO-Fehlertext (Analysis Management Objects) im Fenster Aufgabenliste angezeigt. Sie können auf einen Fehler klicken, um den zum Korrigieren des Fehlers erforderlichen Designer zu öffnen.  
  
 Mit einer erfolgreichen Überprüfung wird nicht sichergestellt, dass Objekte während der Bereitstellung auf dem Zielserver erstellt oder nach der Bereitstellung erfolgreich verarbeitet werden können. Die folgenden Situationen können eine erfolgreiche Bereitstellung oder die Verarbeitung nach der Bereitstellung verhindern:  
  
-   Sicherheitsüberprüfungen für den Server werden nicht ausgeführt. Demzufolge kann die Bereitstellung durch Sperren verhindert werden.  
  
-   Physische Speicherorte auf dem Server werden nicht überprüft.  
  
-   Details von Datenquellensichten werden nicht mit der tatsächlichen Datenquelle auf dem Zielserver verglichen.  
  
 Ist die Überprüfung erfolgreich, werden in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] die XML-Dateien generiert. Nach der Erstellung enthält der Ausgabeordner die in der folgenden Tabelle beschriebenen Dateien.  
  
|Dateien (im Ordner bin)|BESCHREIBUNG|  
|-----------------------------|-----------------|  
|*Projectname*.asdatabase|Enthält die ASSL-Elemente, die die Metadaten für die Objekte des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts in einer Bereitstellungsskriptdatei definieren. Diese Datei wird von der Bereitstellungs-Engine zum Bereitstellen der Objekte in einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank verwendet.|  
|*Projectname*.configsettings|Enthält während der Bereitstellung verwendete Konfigurationseinstellungen, die Sie direkt oder im Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ändern können (z. B. die Verbindungszeichenfolge für die Datenquellen).|  
|*Projectname*.deploymenttargets|Enthält die während der Bereitstellung verwendeten Zieleinstellungen, die Sie direkt oder im Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ändern können (z. B. den Server- und Datenbanknamen).|  
|*Projectname*.deploymentoptions|Enthält verschiedene während der Bereitstellung verwendete Optionseinstellungen, die Sie direkt oder im Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ändern können (z. B. Speicherorte).|  
|*AssemblyName* / *dllName.* dll|Separate Ordner für jede Assembly, auf die verwiesen wird. In jedem Ordner sind jeweils die DLL für die Assembly, sämtliche Assemblys, auf die verwiesen wird, und sämtliche zugeordneten PDB-Dateien für Ausgabedebuginformationen enthalten.|  
  
|Dateien (im Ordner obj)|BESCHREIBUNG|  
|-----------------------------|-----------------|  
|\<Configuration Name>\LastBuilt.xml|Enthält den Zeitstempel und den Hashcode, der den Zeitpunkt identifiziert, als das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt zum letzten Mal erstellt wurde.|  
  
 Diese XML-Dateien enthalten keine \<Create> -und- \<Alter> Tags, die während der Bereitstellung erstellt werden.  
  
 Assemblys, auf die verwiesen wird (hiervon ausgeschlossen sind Assemblys des Standardsystems und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Assemblys), werden ebenfalls in das Ausgabeverzeichnis kopiert. Wenn Verweise auf andere Projekte einer Projektmappe vorhanden sind, werden diese Projekte als Erstes erstellt, jeweils mit der entsprechenden Projektkonfiguration und den über die Projektverweise erstellten Erstellungsabhängigkeiten. Anschließend werden sie in den Projektausgabeordner kopiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Skriptsprache &#40;ASSL&#41; Referenz](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  
