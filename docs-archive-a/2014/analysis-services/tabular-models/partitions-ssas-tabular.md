---
title: Partitionen (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 708b9bdf-8c0b-4476-809a-8f616be23a58
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9db296cfe33bb056a500f85ad184674774ecfc45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696158"
---
# <a name="partitions-ssas-tabular"></a>Partitionen (SSAS – tabellarisch)
  Durch Partitionen wird eine Tabelle logisch unterteilt. Jede Partition kann unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden. Partitionen, die während der Modellerstellung mit dem Dialogfeld Partitionen in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt werden, beziehen sich auf die Arbeitsbereichsdatenbank des Modells. Beim Bereitstellen des Modells werden die für die Arbeitsbereichsdatenbank des Modells definierten Partitionen in der bereitgestellten Modelldatenbank dupliziert. Mithilfe des Dialogfelds Partitionen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie weitere Partitionen für eine bereitgestellte Modelldatenbank erstellen und verwalten.  In diesem Thema werden Partitionen beschrieben, die während der Modellerstellung unter Verwendung des Dialogfelds Partitions-Manager in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt wurden. Informationen zum Erstellen und Verwalten von Partitionen für ein bereitgestelltes Modell finden Sie unter [Erstellen und Verwalten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile](#bkmk_benefits)  
  
-   [Verwandte Aufgaben](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> Vorteile  
 Durch Partitionen in tabellarischen Modellen werden Tabellen in logische Partitionsobjekte unterteilt. Anschließend kann jede Partition unabhängig von anderen Partitionen verarbeitet werden. Eine Tabelle kann z. B. bestimmte Rowsets mit Daten enthalten, die selten geändert werden, während andere Rowsets Daten enthalten, die häufig geändert werden. In diesen Fällen ist es nicht erforderlich, sämtliche Daten zu verarbeiten, wenn tatsächlich nur ein Teil der Daten verarbeitet werden soll. Mit Partitionen können Daten, die häufig verarbeitet werden müssen, und Daten, die weniger häufig verarbeitet werden müssen, voneinander getrennt werden.  
  
 Bei einem effizienten Modellentwurf werden Partitionen genutzt, um unnötige Verarbeitungsschritte und die daraus resultierende Belastung der Analysis Services-Serverprozessoren zu eliminieren und gleichzeitig sicherzustellen, dass bestimmte Daten so häufig verarbeitet und aktualisiert werden, dass immer die neuesten Daten aus den Datenquellen bereitgestellt werden. Die Implementierung und Verwendung von Partitionen während der Modellerstellung kann sich erheblich von der Implementierung und Verwendung von Partitionen für bereitgestellte Modelle unterscheiden. Sie sollten bedenken, dass Sie während der Modellerstellungsphase möglicherweise nur mit einem Bruchteil der Daten arbeiten, die letztendlich im bereitgestellten Modell enthalten sind.  
  
### <a name="processing-partitions"></a>Verarbeitung von Partitionen  
 Bereitgestellte Modelle werden mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verarbeitet, oder indem ein Skript ausgeführt wird, in dem der Verarbeitungsbefehl sowie Verarbeitungsoptionen und -einstellungen angegeben sind. Beim Erstellen von Modellen mit [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]können Sie Verarbeitungsvorgänge mithilfe des Befehls Verarbeiten im Menü Modell oder auf der Symbolleiste Modell ausführen. Ein Verarbeitungsvorgang kann für eine Partition, eine Tabelle oder beides angegeben werden.  
  
 Beim Ausführen eines Verarbeitungsvorgangs wird unter Verwendung der Datenverbindung eine Verbindung mit der Datenquelle hergestellt. In die Modelltabellen werden neue Daten importiert, es werden Beziehungen und Hierarchien für die einzelnen Tabellen neu erstellt, und Berechnungen in berechneten Spalten und Measures werden neu berechnet.  
  
 Indem Sie eine Tabelle weiter in logische Partitionen unterteilen, können Sie selektiv bestimmen, welche Daten in den einzelnen Partitionen, wann und wie verarbeitet werden. Wenn Sie ein Modell bereitstellen, kann die Verarbeitung der Partitionen manuell im Dialogfeld Partitionen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erfolgen oder mithilfe eines Skripts ausgeführt werden, das einen Verarbeitungsbefehl ausführt.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Partitionen in der Arbeitsbereichsdatenbank des Modells  
 Mit dem Partitions-Manager in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]können Sie neue Partitionen erstellen sowie Partitionen bearbeiten, zusammenführen oder löschen. Der Partitions-Manager bietet zwei Modi zum Auswählen von Tabellen, Zeilen und Spalten für eine Partition: den Tabellenvorschaumodus und den SQL-Abfragemodus. Zwar werden alle Partitionen unter Verwendung einer SQL-Abfrage definiert, durch die Verwendung des Tabellenvorschaumodus können Sie jedoch die Daten in der Vorschau anzeigen und auswählen, die Sie in die Partition einschließen möchten. Die SQL-Abfrage wird automatisch erstellt und für Sie überprüft. Da der Tabellenvorschaumodus mit der Tabellenvorschau im Dialogfeld Tabelleneigenschaften bearbeiten und der Seite Tabellenvorschau des Tabellenimport-Assistenten identisch ist, können in der Vorschau maximal 50 Zeilen angezeigt werden.  
  
### <a name="partitions-in-a-deployed-model-database"></a>Partitionen in der Datenbank eines bereitgestellten Modells  
 Wenn Sie ein Modell bereitstellen, werden die Partitionen für die Datenbank des bereitgestellten Modells in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]als Datenbankobjekte dargestellt. Im Dialogfeld Partitionen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]können Sie Partitionen für ein bereitgestelltes Modell erstellen, bearbeiten, zusammenführen und löschen. Die Verwaltung von Partitionen für ein bereitgestelltes Modell in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] wird nicht in diesem Thema behandelt. Informationen zum Verwalten von Partitionen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] finden Sie unter [Erstellen und Verwalten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> Verwandte Aufgaben  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Erstellen und Verwalten von Partitionen in der Arbeitsbereichsdatenbank &#40;SSAS – tabellarisch&#41;](workspace-database-ssas-tabular.md)|Beschreibt, wie Partitionen in der Arbeitsbereichsdatenbank des Modells mit dem Partitions-Manager in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt und verwaltet werden.|  
|[Verarbeiten von Partitionen in der Arbeitsbereichs Datenbank &#40;tabellarischen SSAS-&#41;](process-partitions-in-the-workspace-database-ssas-tabular.md)|Beschreibt, wie Partitionen in der Arbeitsbereichsdatenbank des Modells verarbeitet (aktualisiert) werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Directquery-Modus &#40;tabellarischen SSAS-&#41;](directquery-mode-ssas-tabular.md)   
 [Verarbeiten von Daten &#40;SSAS – tabellarisch&#41;](../process-data-ssas-tabular.md)  
  
  
