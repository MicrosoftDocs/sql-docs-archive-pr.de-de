---
title: Daten Definitions Abfragen (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 153369979737dded52609843cd30cf914315e9cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616274"
---
# <a name="data-definition-queries-data-mining"></a>Datendefinitionsabfragen (Data Mining)
  Beim Data Mining umfasst die Kategorie *Datendefinitionsabfrage* DMX-Anweisungen und XMLA-Befehle, die folgende Operationen ausführen:  
  
-   Erstellen, Ändern oder Bearbeiten von Data Mining-Objekten, z. B. eines Modells.  
  
-   Definieren der Datenquelle, die für das Training oder für Vorhersagen verwendet werden soll.  
  
-   Exportieren oder Importieren von Miningmodellen und Miningstrukturen.  
  
 [Erstellen von Datendefinitionsabfragen](#bkmk_Create)  
  
-   [Datendefinitionsabfragen in SQL Server-Datentools](#bkmk_ssdt)  
  
-   [Datendefinitionsabfragen in SQL Server Management Studio](#bkmk_SSMS)  
  
 [Erstellen von Skripts für Datendefinitionsanweisungen](#bkmk_Scripts)  
  
 [Erstellen von Skripts für Datendefinitionsanweisungen](#bkmk_Export)  
  
##  <a name="creating-data-definition-queries"></a><a name="bkmk_Create"></a>Erstellen von Daten Definitions Abfragen  
 Sie können Datendefinitionsabfragen (Anweisungen) mit dem Generator für Vorhersageabfragen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen, oder das DMX-Abfragefenster in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwenden. Datendefinitionsanweisungen in DMX sind Teil der Datendefinitionssprache (Data Definition Language, DDL) von Analysis Services.  
  
 Informationen zur Syntax bestimmter Datendefinitionsanweisungen finden Sie unter [DMX-Referenz &#40;Data Mining-Erweiterungen&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
###  <a name="data-definition-queries-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a>Daten Definitions Abfragen in SQL Server Data Tools  
 Der Data Mining-Assistent in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ist das bevorzugte Tool zum Erstellen und Ändern von Miningmodellen und Miningstrukturen und zum Definieren der Datenquellen, die in Vorhersageabfragen und beim Training verwendet werden.  
  
 Wenn Sie jedoch wissen möchten, welche Anweisungen vom Assistenten an den Server gesendet werden, um Datenstrukturen oder Miningmodelle zu erstellen, können Sie die Datendefinitionsanweisungen mithilfe von SQL Server Profiler aufzeichnen. Weitere Informationen finden Sie unter [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Um die Anweisungen anzuzeigen, die zum Definieren von Datenquellen für Training oder Vorhersagen verwendet werden, können Sie die **SQL-Sicht** im Generator für Vorhersageabfragen verwenden. Manchmal ist es hilfreich, mit dem Generator für Vorhersageabfragen zunächst grundlegende Abfragen für das Training und Testen von Modellen zu erstellen, um so eine richtige Syntax zu erhalten. Anschließend können Sie zur **SQL-Sicht** wechseln und die Abfrage manuell bearbeiten. Weitere Informationen finden Sie unter [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md).  
  
###  <a name="data-definition-queries-in-sql-server-management-studio"></a><a name="bkmk_SSMS"></a>Daten Definitions Abfragen in SQL Server Management Studio  
 Bei Data Mining-Objekten können Sie die folgenden Aktionen mithilfe von Datendefinitionsabfragen ausführen:  
  
-   Erstellen bestimmter Modelltypen, z.B. eines Clusteringmodells oder eines Entscheidungsstrukturmodells, mit [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
-   Ändern einer vorhandenen Miningstruktur durch Hinzufügen eines Modells oder Ändern der Spalten mit [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx). Beachten Sie, dass Sie ein Miningmodell nicht mit DMX ändern können. Sie fügen einer vorhandenen Struktur lediglich neue Modelle hinzu.  
  
-   Erstellen einer Kopie eines Miningmodells und Ändern der Kopie mit [SELECT INTO &#40;DMX&#41;](/sql/dmx/select-into-dmx).  
  
-   Definieren des Datasets für das Training eines Modells mit [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) und einer Datenquellenabfrage, z.B. OPENROWSET.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] stellt Abfragevorlagen bereit, die Ihnen beim Erstellen von Datendefinitionsabfragen helfen können. Weitere Informationen finden Sie unter [Use Analysis Services Templates in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md).  
  
 Im Allgemeinen ist in den Vorlagen, die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] bereitgestellt werden, nur die allgemeine Syntaxdefinition enthalten, die Sie dann durch Eingaben im Fenster **Abfrage** oder über das Dialogfeld für Parametereingaben anpassen müssen.  
  
 Ein Beispiel zur Eingabe von Parametern über die Benutzeroberfläche finden Sie unter [Erstellen einer SINGLETON-Vorhersageabfrage aus einer Vorlage](create-a-singleton-prediction-query-from-a-template.md).  
  
###  <a name="scripting-data-definition-statements"></a><a name="bkmk_Scripts"></a>Skripterstellung für Daten Definitions Anweisungen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt mehrere Skript- und Programmiersprachen bereit, in denen Sie Data Mining-Objekte erstellen und ändern sowie Datenquellen definieren können.  Obwohl DMX zur schnelleren Verarbeitung von Data Mining-Tasks entworfen wurde, können Sie auch XMLA und AMO verwenden, um in Skripts oder benutzerdefiniertem Code Objekte zu bearbeiten.  
  
 Das Data Mining Add-In für Excel beinhaltet ebenfalls viele Abfragevorlagen und stellt den **Erweiterten Abfrage-Editor**bereit, der Sie beim Erstellen komplexer DMX-Anweisungen unterstützt. Sie können eine Abfrage interaktiv erstellen und dann zur SQL-Sicht wechseln, um die DMX-Anweisung aufzuzeichnen.  
  
##  <a name="exporting-and-importing-models"></a><a name="bkmk_Export"></a>Exportieren und Importieren von Modellen  
 Sie können die Definition eines Modells und seine erforderliche Struktur sowie die Datenquellen mithilfe der Datendefinitionsanweisungen in DMX exportieren und anschließend diese Definition auf einem anderen Server importieren. Das Exportieren und Importieren ist die schnellste und einfachste Möglichkeit, Data Mining-Modelle und Miningstrukturen zwischen Instanzen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zu verschieben. Weitere Informationen finden Sie unter [Verwaltung von Data Mining-Lösungen und -Objekten](management-of-data-mining-solutions-and-objects.md).  
  
> [!WARNING]  
>  Wenn das Modell auf Daten aus einer Cubedatenquelle basiert, können Sie das Modell nicht mithilfe von DMX exportieren. Verwenden Sie stattdessen eine Sicherung und anschließende Wiederherstellung.  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> Verwandte Aufgaben  
 Die folgende Tabelle enthält Links zu verschiedenen Aufgaben im Zusammenhang mit Datendefinitionsabfragen.  
  
|||  
|-|-|  
|Arbeiten mit Vorlagen für DMX-Abfragen.|[Verwenden von Analysis Services-Vorlagen in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|Entwerfen verschiedenster Abfragen mit dem Generator für Vorhersageabfragen.|[erstellt eine Vorhersage mithilfe des Generators für Vorhersageabfragen](create-a-prediction-query-using-the-prediction-query-builder.md)|  
|Aufzeichnen von Abfragedefinitionen mit SQL Server Profiler und Verwenden von Ablaufverfolgungen zum Überwachen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[Verwenden von SQL Server Profiler zum Überwachen von Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|Erfahren Sie mehr zu den Skriptsprachen und Programmiersprachen, die für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereitgestellt werden.|[XML for Analysis-Referenz &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)<br /><br /> [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|Erfahren Sie, wie Modelle in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwaltet werden.|[Exportieren und Importieren von Data Mining-Objekten](export-and-import-data-mining-objects.md)<br /><br /> [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx)<br /><br /> [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx)|  
|Erfahren Sie mehr über OPENROWSET und andere Möglichkeiten zum Abfragen von externen Daten.|[&#60;source data query&#62;](/sql/dmx/source-data-query)-Klausel (Quellabfrage-Klausel).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Assistent &#40;Analysis Services – Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md)  
  
  
