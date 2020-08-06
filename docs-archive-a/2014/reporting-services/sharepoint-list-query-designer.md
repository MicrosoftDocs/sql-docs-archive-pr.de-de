---
title: Abfrage-Designer für SharePoint-Listen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 593de30c-69f0-42a8-8467-16e78647b74c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 018b525cb68972f579aebfbfec70d0b94afc4b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696386"
---
# <a name="sharepoint-list-query-designer"></a>Designer für SharePoint-Listenabfragen
  Berichts-Generator enthält sowohl einen grafischen Abfrage-Designer als auch einen textbasierten Abfrage-Designer. Mit diesen Designern erstellen Sie Abfragen, um die Daten anzugeben, die für ein Berichtsdataset aus einer SharePoint-Website abgerufen werden sollen. Verwenden Sie den grafischen Abfrage-Designer zum Durchsuchen der Metadaten der SharePoint-Liste, interaktiven Erstellen einer Abfrage und Anzeigen der Ergebnisse der Abfrage. Verwenden Sie den textbasierten Abfrage-Designer, um die vom grafischen Abfrage-Designer erstellte Abfrage anzuzeigen, eine Abfrage zu ändern oder die Abfragebefehle einzugeben. Sie können auch eine vorhandene Abfrage aus einer Datei oder einem Bericht importieren.  
  
> [!IMPORTANT]  
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.  
  
## <a name="graphical-query-designer"></a>Grafischer Abfrage-Designer  
 Im grafischen Abfrage-Designer können Sie die SharePoint-Website durchsuchen und den Befehl zum Abrufen der SharePoint-Listendaten für ein Dataset interaktiv erstellen. Sie wählen die Felder aus, die im Dataset enthalten sein sollten, und geben optional Filter an, die die Daten im Dataset begrenzen. Sie können angeben, dass Filter als Parameter verwendet werden und den Wert des Filters zur Laufzeit bereitstellen.  
  
 SharePoint-Listen enthalten viele spezifische SharePoint-Felder, die für Berichte u. U. nicht sinnvoll sind. Der Abfrage-Designer enthält eine Option zum Ausblenden dieser Felder, sodass Sie die gewünschten Felder einfacher und schneller bestimmen können.  
  
 Der grafische Abfrage-Designer ist in drei Bereiche aufgeteilt:  
  
-   Im Bereich "Durchsuchen" wählen Sie die zu verwendenden Listenelemente und Felder aus.  
  
-   Im Bereich "Entwurf" erstellen Sie die Abfrage.  
  
-   Im Bereich "Ergebnisse" zeigen Sie die Abfrageergebnisse an.  
  
 Die folgende Abbildung zeigt den grafischen Abfrage-Designer bei der Verwendung mit SharePoint-Listen.  
  
 ![rsQD_Relational_Graphical_SharePoint](media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
 [SharePoint-Listen](#DatabaseView)  
 Zeigt SharePoint-Listen und die Felder in jedem Element in der Liste an.  
  
 [Ausgewählte Felder](#SelectedFields)  
 Zeigt eine Liste der SharePoint-Listenfeldnamen aus den ausgewählten Elementen im Bereich "SharePoint-Listen" an. Diese Felder werden zur Feldauflistung für das Berichtsdataset.  
  
 [Angewendete Filter](#AppliedFilters)  
 Zeigt eine Liste von Feldern und Filterkriterien für Tabellen oder Sichten in der Datenbanksicht an.  
  
 [Abfrageergebnisse](#QueryResults)  
 Zeigt Beispieldaten für das Resultset für die automatisch generierte Abfrage an.  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a>Bereich "SharePoint-Listen"  
 Im Bereich "SharePoint-Listen" werden die Metadaten für Datenbankobjekte angezeigt, zu deren Anzeige Sie berechtigt sind. Diese Berechtigungen werden durch die Datenquellenverbindung und die Anmeldeinformationen bestimmt. In der hierarchischen Sicht werden Datenbankobjekte nach Datenbankschema angeordnet angezeigt. Erweitern Sie den Knoten für jedes Schema, um Tabellen, Sichten, gespeicherte Prozeduren und Tabellenwertfunktionen anzuzeigen. Erweitern Sie die Tabelle oder Sicht, um die einzelnen Spalten anzuzeigen.  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a>Bereich "ausgewählte Felder"  
 Im Bereich "Ausgewählte Felder" werden die Listenelementfelder angezeigt, die Sie für SharePoint-Listenelemente auswählen. Die Felder, die in diesem Bereich angezeigt werden, werden zur Feldauflistung für das Berichtsdataset. Nachdem Sie ein Dataset und eine Abfrage erstellt haben, verwenden Sie den Berichtsdatenbereich, um die Feldauflistung für ein Berichtsdataset anzuzeigen. Diese Felder stellen die Daten dar, die Sie in Tabellen, Diagrammen und anderen Berichtselementen bei der Anzeige eines Berichts anzeigen können.  
  
 Aktivieren oder deaktivieren Sie im Bereich "SharePoint-Listen" die Kontrollkästchen für die Tabellen- oder Sichtfelder, um diesem Bereich Felder hinzuzufügen bzw. Felder zu entfernen.  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a>Bereich angewendete Filter  
 Im Bereich "Angewendete Filter" werden die Kriterien angezeigt, mit denen die Anzahl von Datenzeilen begrenzt wird, die zur Laufzeit abgerufen werden. In diesem Bereich angegebene Kriterien werden verwendet, um eine [!INCLUDE[tsql](../includes/tsql-md.md)] -WHERE-Klausel zu generieren. Wenn Sie die Parameteroption auswählen, wird automatisch ein Berichtsparameter erstellt. Mit Berichtsparametern, die auf Abfrageparametern basieren, kann ein Benutzer Werte für die Abfrage angeben, um die Daten in dem Bericht zu steuern.  
  
 Die folgenden Spalten werden angezeigt:  
  
-   **Feldname** Zeigt den Namen des Felds an, für das die Kriterien angewendet werden sollen.  
  
-   **Operator** Zeigt den Operator an, der im Filterausdruck verwendet werden soll.  
  
-   **Wert** Zeigt den Wert an, der im Filterausdruck verwendet werden soll.  
  
-   **Parameter** Zeigt die Option an, mit der ein Abfrageparameter der Abfrage hinzugefügt werden kann. Verwenden Sie die Dataseteigenschaften, um die Beziehung zwischen Abfrageparameter und Berichtsparameter anzuzeigen.  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> Bereich Abfrageergebnisse  
 Im Bereich Abfrageergebnisse werden die Ergebnisse für die automatisch generierte Abfrage angezeigt, die mit den Auswahlen in den anderen Bereichen angegeben wird. Die Spalten im Resultset entsprechen den Feldern, die Sie im Bereich Ausgewählte Felder angeben. Die Zeilendaten werden mit den Filtern begrenzt, die Sie im Bereich Angewendete Filter angeben.  
  
 Diese Daten stellen Werte aus der Datenquelle zum Zeitpunkt der Abfrageausführung dar. Die Daten werden nicht in der Berichtsdefinition gespeichert. Die eigentlichen Daten in dem Bericht werden bei der Verarbeitung des Berichts abgerufen.  
  
 Die Sortierreihenfolge im Resultset wird von der Reihenfolge bestimmt, in der die Daten aus der Datenquelle abgerufen werden. Die Sortierreihenfolge kann geändert werden, indem die Abfrage geändert wird oder nachdem die Daten für den Bericht abgerufen wurden.  
  
### <a name="graphical-query-designer-toolbar"></a>Symbolleiste für den grafischen Abfrage-Designer  
 Die Symbolleiste des relationalen Abfrage-Designers stellt die folgenden Schaltflächen bereit, mit denen Sie eine Abfrage angeben oder die Ergebnisse der Abfrage anzeigen können.  
  
|Schaltfläche|Beschreibung|  
|------------|-----------------|  
|**Als Text bearbeiten**|Wechselt zum textbasierten Abfrage-Designer, um die automatisch generierte Abfrage anzuzeigen oder die Abfrage zu ändern.|  
|**Importieren**|Importiert eine vorhandene Abfrage aus einer Datei oder einem Bericht. Die Dateitypen SQL und RDL werden unterstützt.|  
|**Abfrage ausführen**|Führen Sie die Abfrage aus. Das Resultset wird im Bereich mit den Abfrageergebnissen angezeigt.|  
|**Verborgene Felder anzeigen**|Blendet die Felder ein oder aus, die automatisch von SharePoint erstellt, normalerweise aber nicht in Berichten verwendet werden (z. B. "ProgId" und "Level" für SharePoint-Linkelemente). Durch das Ausblenden dieser Felder wird die Feldliste verkürzt, sodass sie einfacher zu verwenden ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage-Designer in Reporting Services](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
