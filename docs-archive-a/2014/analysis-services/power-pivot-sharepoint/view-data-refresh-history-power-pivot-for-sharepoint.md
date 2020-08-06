---
title: Anzeigen des Daten Aktualisierungs Verlaufs (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- data refresh history [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 4c8d8aa8-794d-4f72-ace3-78d0e688e1a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: c7a858aedcbca7aa1436ff06bdf9ebc61724f511
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723189"
---
# <a name="view-data-refresh-history-powerpivot-for-sharepoint"></a>Anzeigen des Daten Aktualisierungs Verlaufs (PowerPivot für SharePoint)
  Der Verlauf der Datenaktualisierung ist ein Datensatz aller Datenaktualisierungsaktivitäten für PowerPivot-Daten in einer Excel-Arbeitsmappe. Datenaktualisierungsvorgänge werden für eine Analysis Services-Serverinstanz in einer SharePoint-Farm nach einem von Ihnen vorgegebenen Zeitplan ausgeführt. Standardmäßig wird der Datenaktualisierungsverlauf ein Jahr lang beibehalten. Ein Farmadministrator kann jedoch eine andere Beibehaltungsrichtlinie für Verwendungs- und Ereignisverläufe angeben. Diese bestimmt, wie lange Datensätze für Datenaktualisierungen beibehalten werden.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 | SharePoint 2010  
  
 **In diesem Thema:**  
  
 [Voraussetzungen](#prereq)  
  
 [Anzeigen des Datenaktualisierungsverlaufs für eine einzelne Arbeitsmappe](#viewhistory)  
  
 [Anzeigen des Datenaktualisierungsverlaufs für alle Arbeitsmappen](#viewITOps)  
  
 [Verwenden von Verlaufsinformationen](#pageelements)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> Voraussetzungen  
 Zum Anzeigen des Datenaktualisierungsverlaufs müssen Sie mindestens über Teilnahmeberechtigungen verfügen.  
  
 Die Datenaktualisierung muss für eine Arbeitsmappe, die PowerPivot-Daten enthält, aktiviert und geplant sein. Wenn Sie keine Datenaktualisierung geplant haben, wird anstelle von Verlaufsinformationen die Seite zur Definition des Zeitplans angezeigt.  
  
##  <a name="view-data-refresh-history-for-an-individual-workbook"></a><a name="viewhistory"></a>Anzeigen des Daten Aktualisierungs Verlaufs für eine einzelne Arbeitsmappe  
  
1.  Öffnen Sie auf einer SharePoint-Website die Bibliothek, die eine Excel-Arbeitsmappe mit PowerPivot-Daten enthält.  
  
     Es gibt keinen visuellen Indikator dafür, welche Arbeitsmappen in einer SharePoint-Bibliothek PowerPivot-Daten enthalten. Sie müssen im Voraus wissen, welche Arbeitsmappe aktualisierbare PowerPivot-Daten enthält.  
  
2.  Wählen Sie die Arbeitsmappe aus, und klicken Sie dann auf den rechts angezeigten Pfeil nach unten.  
  
3.  Wählen Sie **PowerPivot-Datenaktualisierung verwalten**aus.  
  
 Die Verlaufsseite wird mit einem vollständigen Datensatz aller Aktualisierungsaktivitäten angezeigt, die für PowerPivot-Daten in der aktuellen Excel-Arbeitsmappe ausgeführt werden.  
  
##  <a name="view-data-refresh-history-for-all-workbooks"></a><a name="viewITOps"></a>Anzeigen des Daten Aktualisierungs Verlaufs für alle Arbeitsmappen  
 Mithilfe des PowerPivot-Management-Dashboards in der Zentraladministration können Farmadministratoren und Dienstanwendungsadministratoren eine umfassende Ansicht des Datenaktualisierungsverlaufs und -status für alle PowerPivot-Arbeitsmappen abrufen. Weitere Informationen finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
##  <a name="use-history-information"></a><a name="pageelements"></a>Verwenden von Verlaufs Informationen  
 Die Seite Verlauf der Datenaktualisierung enthält ausführliche Informationen zu jedem Aktualisierungsvorgang. Mithilfe der Informationen auf dieser Seite können Sie feststellen, ob eine Aktualisierung ausgeführt wurde bzw. warum ein Fehler aufgetreten ist.  
  
|Element|BESCHREIBUNG|  
|----------|-----------------|  
|Name|Gibt den Dateinamen der Excel-Arbeitsmappe an, die PowerPivot-Daten enthält.|  
|Aktueller Status|Die Werte lauten **Geplant**, **Wird aktualisiert**, **Erfolgreich beendet**oder **Fehler**.<br /><br /> **Geplant** wird beim erstmaligen Erstellen des Zeitplans angezeigt. Nachdem die Datenaktualisierung zum ersten Mal ausgeführt wurde, wird diese Statusmeldung nicht mehr angezeigt.<br /><br /> **Wird aktualisiert** gibt an, dass die Datenaktualisierung ausgeführt wird. Eine Anforderung befindet sich entweder in der Verarbeitungswarteschlange oder wird aktiv auf dem Server ausgeführt.<br /><br /> **Erfolgreich beendet** gibt an, dass der letzte Datenaktualisierungsvorgang abgeschlossen und die aktualisierte Arbeitsmappe wieder in die SharePoint-Bibliothek eingecheckt wurde.<br /><br /> **Fehler** gibt an, dass der letzte Datenaktualisierungsvorgang nicht erfolgreich war. Die aktualisierten Daten wurden nicht gespeichert. Die Arbeitsmappe enthält die gleichen Daten wie vor der Datenaktualisierung.|  
|Letzte erfolgreiche Aktualisierung|Gibt das Datum an, zu dem die letzte Datenaktualisierung erfolgreich abgeschlossen wurde.|  
|Nächste planmäßige Aktualisierung|Gibt das Datum an, zu dem die nächste Datenaktualisierung geplant ist.<br /><br /> Über den Link **Zeitplan konfigurieren** rufen Sie die Seite zum Definieren des Zeitplans auf. Wenn Sie über Teilnahmeberechtigungen für die Arbeitsmappe verfügen, können Sie auf den Link klicken, um die Zeitplaninformationen anzuzeigen und zu ändern, über die die unbeaufsichtigte Datenaktualisierung für PowerPivot-Daten in der Arbeitsmappe gesteuert wird.|  
|Gestartet|**Gestartet** gibt im Abschnitt mit Verlaufsdetails die tatsächliche Verarbeitungszeit an. Die tatsächliche Verarbeitungszeit kann von der geplanten Zeit abweichen. Die Verarbeitung wird gestartet, sobald genügend Arbeitsspeicher auf dem Server verfügbar ist. Wenn der Server sehr ausgelastet ist, kann die Verarbeitung auch einige Stunden nach der angegebenen Startzeit beginnen.|  
|Abgeschlossen|**Abgeschlossen** gibt im Abschnitt mit Verlaufsdetails an, wann der Datenaktualisierungsvorgang beendet wurde. Das Datum und die Uhrzeit geben an, wann die Arbeitsmappe wieder in die Bibliothek eingecheckt wurde.<br /><br /> Bei einem Datenaktualisierungsfehler wird die Fehlerursache anhand mindestens einer Fehlermeldung erläutert. Sie können jeden Datensatz erweitern, um ausführliche Statusinformationen anzuzeigen. Jede Datenquelle wird einzeln mit der jeweiligen Erfolgsmeldung oder der Fehlermeldung aufgeführt, die erklärt, warum die Datenaktualisierung nicht abgeschlossen wurde.|  
|Time|Gibt die kumulierte Zeit vom Beginn der Datenaktualisierung bis zu ihrem Ende an.|  
|Status|Stellt einen Verlaufsdatensatz mit Informationen dazu bereit, ob ein Aktualisierungsvorgang erfolgreich oder fehlerhaft war.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)   
 [Planen einer Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [PowerPivot-Datenaktualisierung](power-pivot-data-refresh.md)  
  
  
