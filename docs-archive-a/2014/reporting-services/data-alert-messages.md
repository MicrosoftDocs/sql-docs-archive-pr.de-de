---
title: Datenwarnmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d50c3dd24c0057f695a9318c5eef7ad9e7540a45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619649"
---
# <a name="data-alert-messages"></a>Datenwarnmeldungen
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Datenwarnungen übermitteln zwei Typen von Datenwarnmeldungen per E-Mail: Meldungen mit Datenwarnungsergebnissen und Meldungen mit Fehlerbeschreibungen. Durch Meldungen mit Ergebnissen werden alle Empfänger über Änderungen der Berichtsdaten informiert, die von allgemeinem Interesse und wichtig für Geschäftsentscheidungen sind. Tritt aus einem unbestimmten Grund ein Fehler auf, und sind die Ergebnisse nicht verfügbar, wird stattdessen die Fehlermeldung gesendet.

 Der Eigentümer der Datenwarnungsdefinition kann auch Informationen zur Datenwarnungsinstanz im Datenwarnungs-Manager anzeigen. Weitere Informationen finden Sie unter [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).

##  <a name="data-alert-messages"></a><a name="DataAlertMessages"></a>Daten Warnmeldungen
 Die folgenden Bilder zeigen eine Datenwarnmeldung mit Ergebnissen und eine Warnmeldung mit einer Fehlerbeschreibung.

 **Ergebnismeldung**

 ![E-Mail mit Datenwarnung mit Ergebnissen](media/rs-alertmessageresults.gif "E-Mail mit Datenwarnung mit Ergebnissen")

 **Fehlermeldung**

 ![Datenwarnmeldung mit Fehlermeldung](media/rs-alertmessageerrror.gif "Datenwarnmeldung mit Fehlermeldung")

 Die Meldungen beinhalten die gleichen Informationstypen.

1.  **Im Auftrag von** enthält den Namen des Erstellers der Datenwarnungsdefinition.

2.  Haben Sie in der Warnungsdefinition eine Beschreibung angegeben, wird diese unterhalb von **Im Auftrag von**angezeigt.

3.  **Warnungsergebnisse** zeigen die Zeilen im Berichtsdatenfeed, der die in der Warnungsdefinition angegebenen Regeln erfüllt, in einem Tabellenformat oder eine Fehlermeldung an. Die Anzahl der angezeigten Zeilen ist unbeschränkt.

4.  **Gehe zu Bericht** ist ein Link zum Bericht, auf dem die Warnungsdefinition basiert. Wenn der Link nicht gültig ist, da der Bericht verschoben oder gelöscht wurde, wird eine Fehlermeldung angezeigt.

5.  **Regel(n)** listet die Regeln und Klauseln in der Warnungsdefinition auf. Anhand dieser Informationen lassen sich die Warnungsergebnisse leichter überprüfen und verstehen. Des Weiteren lassen sich die Regeln in der Datenwarnungsdefinition identifizieren, die Sie ggf. zum Eingrenzen oder Erweitern der Ergebnisse ändern möchten.

6.  **Berichtsparameter** listet die Parameter und Parameterwerte auf, mit denen der Bericht ausgeführt wurde. Parameter und Parameterwerte vereinfachen den Einblick in die Warnungsergebnisse.

7.  **Kontextwerte** beinhalten die Namen und Werte von Berichtselementen, die sich außerhalb der Berichtsdatenbereiche befinden. Die Elemente sind in der Regel Textfelder. Es kann sich zum Beispiel um ein Textfeld mit einem konstanten Wert wie dem Betreff oder der Beschreibung eines Berichts handeln.

 Der einzige Unterschied zwischen den zwei Meldungstypen ist Element 5, **Warnungsergebnisse**. Tritt bei der Erstellung einer Datenwarnungsinstanz oder Datenwarnmeldung ein Fehler auf, zeigt **Warnungsergebnisse** eine Fehlermeldung mit der Beschreibung des Problems an. Die Fehlermeldung wird an alle Empfänger gesendet und informiert diese, dass die erwarteten Warnungsergebnisse, die die Empfänger u. U. auch für Geschäftsentscheidungen benötigen, nicht verfügbar sind.

 

##  <a name="related-tasks"></a><a name="HowTo"></a> Verwandte Aufgaben
 Dieser Abschnitt listet Prozeduren zum Erstellen und Bearbeiten der Datenwarnungsdefinitionen auf, die viele der in den Datenwarnmeldungen angezeigten Informationen bieten.

-   [Create a Data Alert in Data Alert Designer (Erstellen einer Datenwarnung im Datenwarnungs-Designer)](create-a-data-alert-in-data-alert-designer.md)

-   [Edit a Data Alert in Alert Designer (Bearbeiten einer Datenwarnung im Warnungs-Designer)](edit-a-data-alert-in-alert-designer.md)



## <a name="see-also"></a>Weitere Informationen
 [Datenwarnungs-Designer](../../2014/reporting-services/data-alert-designer.md) [Reporting Services Daten Warnungen](../ssms/agent/alerts.md)


