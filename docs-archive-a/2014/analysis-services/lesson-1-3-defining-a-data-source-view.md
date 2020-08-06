---
title: Definieren einer Datenquellen Sicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af00938a-5a06-4fae-b2fc-f3fb0ca3cea5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d59c5fbe5fd4a07596745447567a72499ddabd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608053"
---
# <a name="defining-a-data-source-view"></a>Definieren einer Datenquellensicht
  Nach dem Definieren der Datenquellen für ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt besteht der nächste Schritt im Allgemeinen im Definieren einer Datenquellensicht für das Projekt. Eine Datenquellensicht ist eine einheitliche Sicht der Metadaten von den angegebenen Tabellen und Sichten, die von den Datenquellen im Projekt definiert werden. Das Speichern der Metadaten in der Datenquellensicht ermöglicht das Arbeiten mit den Metadaten während der Entwicklung ohne offene Verbindung mit einer zugrunde liegenden Datenquelle. Weitere Informationen finden Sie unter [Datenquellsichten in mehrdimensionalen Modellen](multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
 In der folgenden Aufgabe definieren Sie eine Datenquellensicht, die fünf Tabellen aus der Datenquelle **AdventureWorksDW2012** umfasst.  
  
### <a name="to-define-a-new-data-source-view"></a>So definieren Sie eine Datenquellensicht  
  
1.  Klicken Sie im Projektmappen-Explorer (auf der rechten Seite des Microsoft Visual Studio-Fensters) mit der rechten Maustaste auf **Datenquellensichten**und anschließend auf **Neue Datenquellensicht**.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**. Die Seite **Datenquelle auswählen** wird angezeigt.  
  
3.  Unter **Relationale Datenquellen**ist die **Adventure Works DW 2012** -Datenquelle ausgewählt. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Um eine auf mehreren Datenquellen basierende Datenquellensicht zu erstellen, definieren Sie zuerst eine auf einer einzelnen Datenquelle basierende Datenquellensicht. Diese Datenquelle wird dann als primäre Datenquelle bezeichnet. Anschließend können Sie Tabellen und Sichten aus einer sekundären Datenquelle hinzufügen. Beim Entwerfen von Dimensionen, die Attribute enthalten, die auf zugehörigen Tabellen in mehreren Datenquellen basieren, können Sie eine [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquelle als primäre Datenquelle definieren und deren verteilte Abfrage-Engine-Funktionen verwenden.  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** Tabellen und Sichten aus der Liste von Objekten aus, die in der ausgewählten Datenquelle verfügbar sind. Sie können diese Liste filtern, sodass das Auswählen von Tabellen und Sichten einfacher wird.  
  
    > [!NOTE]  
    >  Klicken Sie auf die Schaltfläche zum Vergrößern rechts oben, sodass das Fenster im Vollbildmodus angezeigt wird. Dadurch lässt sich die vollständige Liste von verfügbaren Objekten leichter anzeigen.  
  
     Wählen Sie in der Liste **Verfügbare Objekte** die folgenden Objekte aus. Um mehrere Tabellen auszuwählen, halten Sie beim Klicken die STRG-TASTE gedrückt:  
  
    -   **DimCustomer (dbo)**  
  
    -   **DimDate (dbo)**  
  
    -   **DimGeography (dbo)**  
  
    -   **DimProduct (dbo)**  
  
    -   **FactInternetSales (dbo)**  
  
5.  Klicken Sie **>** hierauf, um die ausgewählten Tabellen der Liste **enthaltene Objekte** hinzuzufügen.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Stellen Sie im Namensfeld sicher, dass **Adventure Works DW 2012** angezeigt wird, und klicken Sie anschließend auf **Fertig stellen**.  
  
     Die **Adventure Works DW 2012** -Datenquellensicht wird im Ordner **Datenquellensichten** im Projektmappen-Explorer angezeigt. Der Inhalt der Datenquellensicht wird auch im Datenquellensicht-Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]angezeigt. Der Designer enthält die folgenden Elemente:  
  
    -   Einen Bereich **Diagramm** , in dem die Tabellen und deren Beziehungen grafisch dargestellt werden.  
  
    -   Einen Bereich **Tabellen** , in dem die Tabellen und deren Schemaelemente in einer Strukturansicht angezeigt werden.  
  
    -   Einen Bereich **Diagrammplaner** , in dem Sie Unterdiagramme erstellen können, sodass Sie Untermengen der Datenquellensicht anzeigen können.  
  
    -   Eine für den Datenquellensicht-Designer spezifische Symbolleiste.  
  
8.  Klicken Sie auf die Schaltfläche [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] development environment, click the **Maximize** button.  
  
9. Zur Anzeige der Tabellen im Bereich **Diagramm** in einer 50-Prozent-Darstellung, klicken Sie auf das **Vergrößern** -Symbol in der Symbolleiste des Datenquellensicht-Designers. Dadurch werden die Spaltendetails jeder Tabelle ausgeblendet.  
  
10. Zum Ausblenden des Projektmappen-Explorers klicken Sie auf die Schaltfläche **Automatisch im Hintergrund** , bei der es sich um das Pushpin-Symbol in der Titelleiste handelt. Um den Projektmappen-Explorer wieder anzuzeigen, positionieren Sie den Mauszeiger über der Registerkarte Projektmappen-Explorer auf der rechten Seite der Entwicklungsumgebung. Zum Ausblenden des Projektmappen-Explorers klicken Sie erneut auf die Schaltfläche **Automatisch im Hintergrund** .  
  
11. Wenn die Fenster nicht standardmäßig ausgeblendet sind, klicken Sie in der Titelleiste des Fensters für Eigenschaften sowie des Fensters des Projektmappen-Explorers auf **Automatisch im Hintergrund** .  
  
     Sie können nun alle Tabellen und deren Beziehungen im Bereich **Diagramm** anzeigen. Beachten Sie, dass drei Beziehungen zwischen der FactInternetSales-Tabelle und der DimDate-Tabelle vorhanden sind. Jedem Verkauf sind drei Daten zugeordnet: ein Bestelldatum, ein Fälligkeitsdatum und ein Lieferdatum. Um die Details einer Beziehung anzuzeigen, doppelklicken Sie auf den Beziehungspfeil im Bereich **Diagramm** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ändern von Standardtabellennamen](lesson-1-4-modifying-default-table-names.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellsichten in mehrdimensionalen Modellen](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
