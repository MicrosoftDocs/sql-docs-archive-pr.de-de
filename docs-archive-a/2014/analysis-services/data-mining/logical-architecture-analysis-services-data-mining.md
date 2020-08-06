---
title: Logische Architektur (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], about mining structures
- logical architecture [Data Mining]
- architecture [Analysis Services], mining models
- mining models [Analysis Services], about data mining models
- architecture [Analysis Services]
ms.assetid: 4e0cbf46-cc60-4e91-a292-9a69f29746f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: e1af06d7ffe12301f6b8b678f41665e5c3146a13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698900"
---
# <a name="logical-architecture-analysis-services---data-mining"></a>Logische Architektur (Analysis Services - Data Mining)
  Das Data Mining ist ein Prozess, bei dem mehrere Komponenten interagieren.  
  
-   Sie greifen auf Datenquellen in einer SQL Server-Datenbank oder auf eine beliebige andere Datenquelle zu, um diese zum Training, für Tests oder für Vorhersagen zu verwenden.  
  
-   Sie definieren Data Mining-Strukturen und -Modelle mithilfe von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder Visual Studio.  
  
-   Sie verwalten Data Mining-Objekte und erstellen Vorhersagen und Abfragen, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwenden.  
  
-   Nachdem Sie die Lösung fertig gestellt haben, können Sie sie als Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitstellen.  
  
 Der Prozess hinsichtlich der Erstellung dieser Lösungsobjekte wurde bereits an anderer Stelle beschrieben. Weitere Informationen finden Sie unter [Data Mining-Projektmappen](data-mining-solutions.md).  
  

  
##  <a name="data-mining-source-data"></a><a name="bkmk_SourceData"></a> Data Mining-Quelldaten  
 Die Daten, die Sie beim Data Mining verwenden, werden nicht in der Data Mining-Lösung gespeichert. Es werden nur die Bindungen gespeichert. Die Daten können sich in einer Datenbank befinden, die in einer vorherigen Version von SQL Server erstellt wurde, oder in einem CRM-System oder sogar einer Flatfile. Wenn für die Struktur oder das Modell ein Training auf Grundlage der Verarbeitung erfolgt, wird eine statistische Zusammenfassung der Daten erstellt und in einem Cache gespeichert, der zur Verwendung in späteren Vorgängen beibehalten oder nach der Verarbeitung gelöscht werden kann. Weitere Informationen finden Sie unter [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md).  
  
 Sie kombinieren ungleichartige Daten innerhalb des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquellensicht-Objekts (DSV), das im oberen Bereich der Datenquelle eine Abstraktionsebene bereitstellt. Sie können Joins zwischen Tabellen festlegen oder Tabellen hinzufügen, die eine n:1-Beziehung aufweisen, um geschachtelte Tabellenspalten zu erstellen. Die Definitionen dieser Objekte, der Datenquelle und der Datenquellensicht werden innerhalb der Projektmappe mit den Dateinamenerweiterungen *.ds oder \*.dsv gespeichert. Weitere Informationen zum Erstellen und Verwenden von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenquellen und Datenquellen Sichten finden Sie [unter Data Sources supported &#40;SSAS Multidimensional&#41;](../multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 Sie können Datenquellen und Datenquellensichten auch definieren und ändern, indem Sie AMO oder XMLA verwenden. Weitere Informationen zum programmgesteuerten Arbeiten mit diesen Objekten finden Sie unter [Übersicht über logische Architektur &#40;Analysis Services – Mehrdimensionale Daten&#41;](../multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md).  
  

  
##  <a name="mining-structures"></a><a name="bkmk_Structures"></a>Mining Strukturen  
 Eine Data Mining-Struktur ist ein logischer Datencontainer, der die Datendomäne definiert, aus der die Miningmodelle erstellt werden. Eine einzelne Miningstruktur kann mehrere Miningmodelle unterstützen.  
  
 Wenn Sie die Daten in der Data Mining-Lösung verwenden müssen, liest Analysis Services die Daten aus der Quelle aus und erzeugt einen Cache mit Aggregaten und weiteren Informationen. Standardmäßig wird dieser Cache beibehalten, damit Trainingsdaten wiederverwendet werden können, um zusätzliche Modelle zu unterstützen. Wenn Sie den Cache löschen müssen, ändern Sie die `CacheMode`-Eigenschaft des Miningstrukturobjekts in den Wert `ClearAfterProcessing`. Weitere Informationen finden Sie unter [AMO-Klassen für Data Mining](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] können Sie die Daten auch in Trainings- und Testdatensätze unterteilen, damit Sie Ihre Data Mining-Modelle mit einem repräsentativen, zufällig ausgewählten Satz von Daten testen können. Die Daten werden eigentlich nicht getrennt gespeichert. Im Strukturcache werden die Falldaten eher mit einer Eigenschaft markiert, die angibt, ob der jeweilige Fall für Trainings- oder für Testzwecke verwendet wird. Wenn der Cache gelöscht wird, können diese Informationen nicht abgerufen werden.  
  
 Weitere Informationen finden Sie unter [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md).  
  
 Eine Data Mining-Struktur kann geschachtelte Tabellen enthalten. In einer geschachtelten Tabelle werden weitere Details zu dem Fall bereitgestellt, der in der primären Datentabelle modelliert ist. Weitere Informationen finden Sie unter [Geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](nested-tables-analysis-services-data-mining.md).  
  
 
  
##  <a name="mining-models"></a><a name="bkmk_Models"></a>Mining Modelle  
 Vor der Verarbeitung stellt ein Data Mining-Modell lediglich eine Kombination aus Metadateneigenschaften dar. Diese Eigenschaften spezifizieren eine Miningstruktur, einen Data Mining-Algorithmus und eine bestimmte Auflistung von Parameter- und Filtereinstellungen, die sich auf die Art der Verarbeitung der Daten auswirken. Weitere Informationen finden Sie unter [Miningmodelle &#40;Analysis Services – Data Mining&#41;](mining-models-analysis-services-data-mining.md).  
  
 Wenn Sie das Modell verarbeiten, werden die im Cache der Miningstruktur gespeicherten Trainingsdaten dazu verwendet, Muster zu generieren. Dies geschieht auf der Grundlage sowohl der statistischen Eigenschaften der Daten als auch der vom Algorithmus und dessen Parametern definierten Heuristik. Dies wird als *trainieren* des Modells bezeichnet.  
  
 Das Ergebnis des Trainings stellt einen Satz von Zusammenfassungsdaten dar. Diese sind im *Modellinhalt*enthalten, der die gefundenen Muster beschreibt und Regeln bereitstellt, mit deren Hilfe Vorhersagen generiert werden können. Weitere Informationen finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).  
  
 In beschränkten Fällen kann die logische Struktur des Modells auch in eine Datei exportiert werden, die Modellformeln und Datenbindungen gemäß dem Standardformat der PMML (Predictive Model Markup Language) darstellt. Diese logische Struktur kann in andere Systeme importiert werden, die PMML verwenden. Außerdem kann das so beschriebene Modell dann zur Vorhersage verwendet werden. Weitere Informationen finden Sie unter [Grundlegendes zur SELECT-Anweisung (DMX)](/sql/dmx/understanding-the-dmx-select-statement).  
  

  
##  <a name="custom-data-mining-objects"></a><a name="bkmk_CustomObjects"></a>Benutzerdefinierte Data Mining-Objekte  
 Andere Objekte, die Sie im Zusammenhang mit einem Data Mining-Projekt verwenden, wie z. B. Genauigkeitsdiagramme oder Vorhersageabfragen, werden nicht innerhalb der Lösung beibehalten. Für sie kann aber mit ASSL ein Skript erstellt werden, oder sie können mit AMO erstellt werden.  
  
 Darüber hinaus können Sie die über eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbaren Dienste und Funktionen durch das Hinzufügen der folgenden benutzerdefinierten Objekte erweitern:  
  
 **Angepasste Assemblys**  
 .NET-Assemblys können mit einer beliebigen Reklamationssprache für CLR oder COM definiert und anschließend mit einer Instanz des SQL-Servers registriert werden. Assemblydateien werden von der Position geladen, die von der Anwendung definiert wird. Außerdem wird eine Kopie zusammen mit den Daten auf dem Server gespeichert. Die Kopie der Assemblydatei wird verwendet, um die Assembly bei jedem Start des Diensts zu laden.  
  
 Weitere Informationen finden Sie unter [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-models/multidimensional-model-assemblies-management.md).  
  
 **Benutzerdefinierte gespeicherte Prozeduren**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Data Mining unterstützt die Verwendung von gespeicherten Prozeduren, damit diese mit Data Mining-Objekten funktionieren können. Sie können eigene gespeicherte Prozeduren erstellen, um die Funktionalität zu erweitern und um einfacher mit von Vorhersageabfragen und Inhaltsabfragen zurückgegebenen Daten arbeiten zu können.  
  
 [Definieren von gespeicherten Proze](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
 Die folgenden gespeicherten Prozeduren werden zur Durchführung einer Kreuzvalidierung unterstützt.  
  
 [Data Mining-gespeicherte Prozeduren &#40;Analysis Services – Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
 Darüber hinaus enthält [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viele gespeicherte Systemprozeduren, die intern für Data Mining verwendet werden. Obwohl die gespeicherten Systemprozeduren für die interne Verwendung ausgelegt sind, können Sie Ihnen unter Umständen nützliche Verknüpfungen bieten. Microsoft behält sich das Recht vor, diese gespeicherten Prozeduren je nach Bedarf zu ändern. Daher wird hinsichtlich einer produktiven Nutzung empfohlen, dass Sie Abfragen mit DMX, AMO oder XMLA erstellen.  
  
 **Benutzerdefinierte Plug-In-Algorithmen**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt einen Mechanismus zum Erstellen von eigenen Algorithmen und zum anschließenden Hinzufügen von Algorithmen bereit, die als neuer Data Mining-Dienst für die Serverinstanz fungieren.  
  
 Analysis Services verwendet COM-Schnittstellen zum Kommunizieren mit den Plug-In-Algorithmen. Weitere Informationen darüber, wie neue Algorithmen implementiert werden, finden Sie unter [Plugin Algorithms](plugin-algorithms.md).  
  
 Sie müssen jeden neuen Algorithmus registrieren, bevor Sie diesen verwenden können. Um einen Algorithmus zu registrieren, fügen Sie die erforderlichen Metadaten für den jeweiligen Algorithmus in der INI-Datei der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]hinzu. Sie müssen jeder Instanz, bei der Sie die Verwendung des entsprechenden Algorithmus beabsichtigen, diese Informationen hinzufügen. Nachdem Sie den Algorithmus hinzugefügt haben, können Sie die Instanz neu starten. Sie können das MINING_SERVICES-Schemarowset verwenden, um den neuen Algorithmus anzuzeigen, einschließlich der Optionen und Anbieter, welche der Algorithmus unterstützt.  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Objekt Verarbeitung für mehrdimensionale Modelle](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
