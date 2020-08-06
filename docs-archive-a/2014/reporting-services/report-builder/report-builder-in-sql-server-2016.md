---
title: Berichts-Generator in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2fb8994272eb24594239551d623021f7b87694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609690"
---
# <a name="report-builder-in-sql-server-2014"></a>Berichts-Generator in SQL Server 2014
  Berichts-Generator ist eine Berichterstellungsumgebung für Geschäftsbenutzer, die lieber in der vertrauten [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office-Umgebung arbeiten. Beim Entwurf eines Berichts geben Sie an, wo die Daten abgerufen werden sollen, welche Daten abgerufen werden sollen und wie die Daten angezeigt werden sollen. Bei der Ausführung des Berichts übernimmt der Berichtsprozessor alle angegebenen Informationen, ruft die Daten ab und kombiniert sie mit dem Berichtslayout, um den Bericht zu generieren. Sie können Berichte im Berichts-Generator in der Vorschau anzeigen oder auf einem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus veröffentlichen, damit auch andere Benutzer den Bericht ausführen können.  
  
 Der Bericht in dieser Abbildung enthält eine Matrix mit Zeilen- und Spaltengruppen, Sparklines, Indikatoren und einem Zusammenfassungskreisdiagramm in der Eckzelle sowie eine Karte mit zwei Sätzen geografischer Daten, die durch Farbe und Kreisgröße dargestellt werden.  
  
 ![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")  
  
##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a>Erstellung eines Jump-Start-Berichts  
  
-   **Starten Sie den Bericht mit Berichts teilen, die** von einem anderen Benutzer in Ihrem Team erstellt wurden. Berichtsteile sind Berichtselemente, die separat auf einem Berichtsserver oder einer in einen Berichtsserver integrierten SharePoint-Website veröffentlicht wurden. Sie können in anderen Berichten wiederverwendet werden. Berichtselemente wie Tabellen, Matrizen, Diagramme und Bilder können als Berichtsteile veröffentlicht werden.  
  
-   **Beginnen Sie mit einem freigegebenen DataSet** , das von einer anderen Person in Ihrem Team erstellt wurde. Freigegebene Datasets sind auf einer freigegebenen Datenquelle basierende Abfragen, die auf einem Berichtsserver oder einer in einen Berichtsserver integrierten SharePoint-Website gespeichert werden.  
  
-   **Mit dem Tabellen-, Matrix- oder Diagramm-Assistenten** Wählen Sie eine Datenquellenverbindung aus, verschieben Sie Felder per Drag &amp; Drop, um eine Datasetabfrage zu erstellen, wählen Sie das Layout und Format aus, und passen Sie den Bericht an.  
  
-   **Mit dem Karten-Assistenten** erstellen Sie Berichte, die aggregierte Daten vor einem geografischen oder geometrischen Hintergrund anzeigen. Kartendaten können räumliche Daten aus einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage oder einer ESRI-Shape-Datei (Environmental Systems Research Institute, Inc.) sein. Sie können auch einen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Bing Map-Kachelhintergrund hinzufügen.  
  

  
##  <a name="design-your-report"></a><a name="DesignRept"></a>Entwerfen des Berichts  
  
-   **Erstellen Sie Berichte mit Tabellen-, Matrix-, Diagramm- und Freiformberichtslayouts.** Erstellen Sie Tabellenberichte für spaltenbasierte Daten, Matrixberichte wie Kreuztabellenberichte oder PivotTable-Berichte für zusammengefasste Daten, Diagrammberichte für grafische Daten und Freiformberichte für alles übrige. In Berichten können andere Berichte und Diagramme sowie Listen, Grafiken und Steuerelementen für dynamische, webbasierte Anwendungen eingebettet werden.  
  
-   **Erstellen Sie Berichte aus einer Vielzahl von Datenquellen.** Erstellen Sie Berichte mit Daten aus beliebigen Datenquellen Typen, die über einen von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verwalteten Datenanbieter, OLE DB-Anbieter oder eine ODBC-Datenquelle verfügen. Sie können Berichte erstellen, die relationale und mehrdimensionale Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken, Oracle-Hyperion- sowie anderen Datenbanken enthalten. Sie können eine XML-Datenverarbeitungserweiterung verwenden, um Daten von jeder XML-Datenquelle abzurufen. Mit Tabellenwertfunktionen können Sie benutzerdefinierte Datenquellen entwerfen.  
  
-   **Bearbeiten Sie vorhandene Berichte.** Mithilfe Berichts-Generator können Sie Berichte anpassen und aktualisieren, die in Berichts-Designer erstellt wurden [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
-   **Ändern Sie die Daten** durch Filtern, gruppieren und Sortieren von Daten oder durch Hinzufügen von Formeln oder Ausdrücken.  
  
-   **Fügen Sie Diagramme, Messgeräte, Sparklines und Indikatoren hinzu** , um Daten in einem visuellen Format zusammenzufassen und große Mengen aggregierter Informationen auf einen Blick darzustellen.  
  
-   **Fügen Sie interaktive Features hinzu**, z. B. Dokumentstrukturen, Schaltflächen zum Anzeigen/Ausblenden und Drillthroughlinks zu Unterberichten und Drillthroughberichten. Verwenden Sie Parameter und Filter, um Daten für benutzerdefinierte Sichten zu filtern.  
  
-   **Betten Sie Bilder und andere Ressourcen ein, oder verweisen Sie auf sie,** einschließlich externer Inhalte.  
  

  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a>Verwalten des Berichts  
  
-   **Speichern Sie die Berichtsdefinition** auf Ihrem Computer oder auf dem Berichtsserver, wo Sie sie verwalten und für andere Personen freigeben können.  
  
-   **Wählen Sie ein Präsentationsformat aus**, wenn Sie den Bericht öffnen oder nachdem Sie ihn geöffnet haben. Sie können ein weborientiertes, seitenorientiertes oder ein Desktopanwendungsformat auswählen. Zu den Formaten gehören HTML, MHTML, PDF, XML, CSV, TIFF, Word und Excel.  
  
-   **Richten Sie Abonnements ein.** Nachdem Sie den Bericht auf dem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus veröffentlicht haben, können Sie ihn so konfigurieren, dass er zu einer bestimmten Zeit ausgeführt wird. Sie können auch einen Berichtsverlauf erstellen und E-Mail-Abonnements einrichten.  
  
-   **Generieren Sie Datenfeeds** aus dem Bericht, indem Sie die Reporting Services Atom-Renderingerweiterung verwenden.  
  
> [!NOTE]  
>  Veröffentlichte Berichte werden auf einem Berichtsserver oder einem Berichtsserver im integrierten SharePoint-Modus von einem Berichtsserveradministrator verwaltet. Berichtsserveradministratoren können die Sicherheit definieren, Eigenschaften festlegen und Vorgänge planen, wie Berichtsverlauf und E-Mail-Übermittlung von Berichten. Sie können freigegebene Zeitpläne und freigegebene Datenquellen erstellen und zur allgemeinen Verwendung zur Verfügung stellen. Administratoren verwalten auch alle Berichtsserverordner. Welche Verwaltungsaufgaben ausgeführt werden können, hängt von den Berechtigungen des Benutzers ab.  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> In diesem Abschnitt  
 [Neues im Berichts-Generator für SQL Server 2014](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 Beschreibt die neuen Funktionen in dieser Version des Berichts-Generators, einschließlich Karten.  
  
 [Lernprogramm: Erstellen eines Quick-Diagrammberichts offline](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 Enthält eine Einführung in Berichts-Generator und die verfügbaren Assistenten, damit Sie Berichte erstellen können. Das Lernprogramm enthält eine Reihe von Daten, mit denen Sie arbeiten können, ohne eine Verbindung mit einer Datenquelle herstellen zu müssen.  
  
 [Planen eines Berichts &#40;Berichts-Generator&#41;](../report-design/planning-a-report-report-builder.md)  
 Enthält Informationen zu den Punkten, die Sie vor dem Erstellen des Berichts beachten sollten.  
  
 [Berichterstellungskonzepte &#40;Berichts-Generator und SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 Enthält Definitionen der Schlüsselkonzepte, die in der Dokumentation zum Berichts-Generator verwendet werden.  
  
 [Berichtsentwurfsansicht &#40;Berichts-Generator&#41;](report-design-view-report-builder.md)  
 Erläutert die unterschiedlichen Bereiche und Abschnitte der Berichtsentwurfsansicht.  
  
 [Freigegebene Dataset-Entwurfsansicht &#40;Berichts-Generator&#41;](shared-dataset-design-view-report-builder.md)  
 Erläutert die unterschiedliche Bereiche und Abschnitte der Entwurfsansicht für freigegebene Datasets.  
  
 [Tastenkombinationen &#40;Berichts-Generator&#41;](keyboard-shortcuts-report-builder.md)  
 Bietet einen Überblick über die verfügbaren Tastenkombinationen für die Navigation und das Entwerfen von Berichten im Berichts-Generator.  
  
 [Starten Sie Berichts-Generator &#40;Berichts-Generator&#41;](start-report-builder.md)  
 Erläutert, wie die beiden Versionen von Berichts-Generator gestartet werden: eigenständige Version und [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]-Version.  
  
  
