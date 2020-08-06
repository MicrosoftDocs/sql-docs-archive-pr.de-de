---
title: Projekte (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fed02e84b154a86788b350812ad8fd5137c14b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621819"
---
# <a name="projects-sql-server-management-studio"></a>Projekte (SQL Server Management Studio)
  Ein [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] -Projekt ist eine Sammlung logisch verbundener Skripts und Dateien, die zusammen zur Verwaltung und Entwicklung von Datenbanken gespeichert werden können.  
  
## <a name="script-project-overview"></a>Übersicht über das Skriptprojekt  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skriptprojekte werden in der Projektmappen-Explorer-Komponente von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]angezeigt. Ein Skriptprojekt kann null oder mehr Projektdateien enthalten. Sie können einer Projektmappe ein Projekt hinzufügen oder mehrere Projekte innerhalb einer Projektmappe kombinieren.  
  
 Projekte können Folgendes umfassen:  
  
-   **Verbindungen**. Eine dauerhafte Verbindung in einem Projekt enthält Anmeldeinformationen, den Servernamen, die Standarddatenbank, das bevorzugte Protokoll, den Authentifizierungstyp und Verbindungseigenschaften. Verbindungsinformationen lassen sich optional auch zusammen mit einem Skript speichern (siehe unten).  
  
-   **SQLScripts**. Häufig verwendete SQL-Skripts für den Benutzer. Wenn Sie im Projekt auf eine SQL-Datei doppelklicken, wird das ausgewählte Skript vom SQL-Editor geöffnet.  
  
-   **MDX-, DMX- und XMLA-Skripts**. Häufig verwendete MDX-Skripts für den Benutzer. Wenn Sie im Projekt auf eine MDX-Datei doppelklicken, wird das ausgewählte Skript vom Editor geöffnet.  
  
-   **Verschiedenes**. Dieser Ordner kann für Dateien verwendet werden, die sich nicht problemlos einem der anderen standardmäßigen Knotentypen zuordnen lassen. Dazu zählen z. B. Textdateien mit Projektzielen.  
  
 Projekte können auch in ein Quellcodeverwaltungs-System integriert werden.  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a>Herstellen einer Verbindung mit einer SQL Server-Instanz aus einem Skriptprojekt  
 Ein Skriptprojekt kann Verbindungen zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten. Sie können eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einem Projekt durch Klicken auf die Verbindung herstellen. Daraufhin wird ein SQL-Skriptfenster geöffnet, das mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden ist, die in der ausgewählten Verbindung definiert ist. Beim Öffnen eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - oder MDX-Skripts mit einer Verbindung, von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wird, werden Sie zum Angeben des Kennworts aufgefordert. Dabei wird nach dem Öffnen des Editors und Laden des Skripts das Dialogfeld **Verbindung mit SQL Server herstellen** angezeigt.  
  
 Die Verbindung wird geschlossen, sobald das entsprechende Fenster geschlossen wird.  
  
 Mit dem Eigenschaftenfenster in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]können Sie Informationen zu einer Verbindung ändern.  
  
## <a name="project-tasks"></a>Projekttasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie ein neues Projekt in einer Projektmappe erstellt wird.|[Create a Project (Erstellen eines Projekts)](create-a-project.md)|  
|Beschreibt, wie einer Projektmappe ein vorhandenes Projekt hinzugefügt wird.|[Hinzufügen eines vorhandenen Projekts zu einer Projektmappe](add-an-existing-project-to-a-solution.md)|  
|Beschreibt, wie der Standardspeicherort zum Speichern von Projektdateien geändert wird.|[Ändern des Standardspeicherorts für Projekte](change-the-default-location-for-projects.md)|  
|Beschreibt, wie die aktuellen Eigenschaften eines Projekts angezeigt werden.|[Anzeigen der Projekteigenschaften](view-project-properties.md)|  
|Beschreibt, wie einem Projekt neue Elemente hinzugefügt werden, z. B. Verbindungen oder Skriptdateien.|[Hinzufügen neuer Elemente zu einem Projekt](add-new-items-to-a-project.md)|  
|Beschreibt, wie die Verbindungsinformationen für eine Abfrage festgelegt werden.|[Verknüpfen einer Abfrage mit einer Verbindung in einem Projekt](associate-a-query-with-a-connection-in-a-project.md)|  
|Beschreibt, wie die Verbindungsinformationen für eine Abfrage geändert werden.|[Ändern der mit einer Abfrage verknüpften Verbindung](change-the-connection-associated-with-a-query.md)|  
|Beschreibt, wie Verbindungseigenschaften geändert werden.|[Anzeigen oder Ändern der Eigenschaften einer Verbindung in einem Projekt](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Projektmappen-Explorer](solution-explorer.md)   
 [Lösungen &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Quellcodeverwaltung des Projektmappen-Explorers](../../database-engine/solution-explorer-source-control.md)  
  
  
