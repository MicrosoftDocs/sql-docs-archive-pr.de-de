---
title: Optionen für Anforderung für Verteilungsprofil für Spaltenlänge (Datenprofilerstellungs-Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c0ebb6f1e0a6df2c0e47311f7b8217c5ce6f2df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617236"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a>Optionen für Anforderung für Verteilungsprofil für Spaltenlänge (Datenprofilerstellungs-Task)
  Verwenden Sie den Bereich **Anforderungseigenschaften** der Seite **Profilanforderungen** , um die Optionen für die im Anforderungsbereich ausgewählte **Anforderung für Verteilungsprofil für Spaltenlänge** festzulegen. Ein Verteilungsprofil für die Spaltenlänge dokumentiert alle eindeutigen Längen von Zeichenfolgenwerten in der ausgewählten Spalte sowie den Prozentsatz der Zeilen in der Tabelle, die jede Länge darstellt. Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. ungültige Werte. Beispiel: Sie erstellen ein Profil einer Spalte mit den Codes der US-amerikanischen Bundesstaaten, die zwei Zeichen lang sind, und entdecken Werte, die länger als zwei Zeichen sind.  
  
> [!NOTE]  
>  Die in diesem Thema beschriebenen Optionen werden auf der Seite **Profilanforderungen** im **Editor für den Datenprofilerstellungs-Task**angezeigt. Weitere Informationen zu dieser Seite des Editors finden Sie unter [Editor für den Datenprofilerstellungs-Task &#40;Seite „Profilanforderungen“&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Weitere Informationen zum Verwenden des Datenprofilerstellungs-Tasks finden Sie unter [Einrichten von Datenprofilerstellungs-Tasks](data-profiling-task.md). Weitere Informationen zum Verwenden des Datenprofil-Viewers zum Analysieren der Ausgabe des Datenprofilerstellungs-Tasks finden Sie unter [Datenprofil-Viewer](data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Optionen für Anforderungseigenschaften  
 Für eine **Anforderung für Verteilungsprofil für Spaltenlänge**zeigt der Bereich **Anforderungseigenschaften** die folgenden Gruppen von Optionen an:  
  
-   **Daten**, die die Optionen **TableOrView** und **Spalte** enthalten  
  
-   **Allgemein**  
  
-   **Optionen**  
  
### <a name="data-options"></a>Datenoptionen  
 **ConnectionManager**  
 Wählen Sie den vorhandenen [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager aus, der den .NET-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) verwendet, um eine Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herzustellen, die die Tabelle oder Sicht enthält, für die ein Profil erstellt werden soll.  
  
 **TableOrView**  
 Wählen Sie die vorhandene Tabelle oder die Sicht aus, die die Spalte enthält, für die ein Profil erstellt werden soll.  
  
 Weitere Informationen finden Sie im Abschnitt "TableorView-Optionen" in diesem Thema.  
  
 **Spalte**  
 Wählen Sie die vorhandene Spalte aus, für die ein Profil erstellt werden soll. Wählen Sie **(\*)** aus, um ein Profil für alle Spalten zu erstellen.  
  
 Weitere Informationen finden Sie im Abschnitt "Spaltenoptionen" in diesem Thema.  
  
#### <a name="tableorview-options"></a>TableOrView-Optionen  
 **Schema**  
 Gibt das Schema an, zu dem die ausgewählte Tabelle gehört. Diese Option ist schreibgeschützt.  
  
 **Table**  
 Zeigt den Namen der ausgewählten Tabelle an. Diese Option ist schreibgeschützt.  
  
#### <a name="column-options"></a>Spaltenoptionen  
 **IsWildCard**  
 Gibt an, ob der Platzhalter **(\*)** ausgewählt wurde. Diese Option wird auf **TRUE** festgelegt, wenn Sie **(\*)** ausgewählt haben, um ein Profil für alle Spalten zu erstellen. Die Option wird auf **False** festgelegt, wenn Sie eine einzelne Spalte ausgewählt haben, für die ein Profil erstellt werden soll. Diese Option ist schreibgeschützt.  
  
 **ColumnName**  
 Zeigt den Namen der ausgewählten Spalte an. Diese Option ist leer, wenn Sie **(\*)** ausgewählt haben, um ein Profil für alle Spalten zu erstellen. Diese Option ist schreibgeschützt.  
  
 **StringCompareOptions**  
 Diese Option gilt nicht für das Verteilungsprofil für Spaltenlänge.  
  
### <a name="general-options"></a>Allgemeine Optionen  
 **RequestID**  
 Geben Sie einen beschreibenden Namen ein, um diese Profilanforderung zu kennzeichnen. In der Regel müssen Sie den automatisch generierten Wert nicht ändern.  
  
### <a name="options"></a>Tastatur  
 **IgnoreLeadingSpaces**  
 Geben Sie an, ob führende Leerzeichen ignoriert werden sollen, wenn das Profil Zeichenfolgenwerte vergleicht. Der Standardwert für diese Option ist **False**.  
  
 **IgnoreTrailingSpaces**  
 Geben Sie an, ob nachfolgende Leerzeichen ignoriert werden sollen, wenn das Profil Zeichenfolgenwerte vergleicht. Der Standardwert für diese Option ist **True**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Editor für den Datenprofilerstellungs-Task &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)   
 [Schnellprofilformular für eine einzelne Tabelle &#40;Datenprofilerstellungs-Task&#41;](single-table-quick-profile-form-data-profiling-task.md)  
  
  
