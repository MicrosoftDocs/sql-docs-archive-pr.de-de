---
title: Festlegen von Parametern für einen veröffentlichten Bericht (Reporting Services im integrierten SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d0a2b1a23f382adb9e0cdddbebcded0050d34bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608285"
---
# <a name="set-parameters-on-a-published-report-reporting-services-in-sharepoint-integrated-mode"></a>Festlegen von Parametern für einen veröffentlichten Bericht (Reporting Services im integrierten SharePoint-Modus)
  Bei einem parametrisierten Bericht handelt es sich um einen Bericht, der bei seiner Ausführung Eingabewerte akzeptiert, mit denen die Daten gefiltert werden. Parameter werden beim Erstellen des Berichts definiert. Abhängig von der Definition eines Berichtsparameters in der Berichtsdefinition kann er einen einzelnen Wert, mehrere Werte oder dynamische Werte akzeptieren, die als Reaktion auf eine vorherige Auswahl geändert werden (wenn Sie z. B. eine Produktkategorie auswählen, könnte die nächste Auswahl ein bestimmtes Produkt aus dieser Kategorie sein). Ein Parameter kann einen Standardwert aufweisen, der zur automatischen Ausführung einer gefilterten Version des Berichts verwendet werden kann oder möglicherweise durch einen anderen Wert ersetzt werden kann.  
  
 Diese Eigenschaften können in der Berichtsdefinition oder nach dem Veröffentlichen des Berichts festgelegt werden. Zwar können Sie einige Parametereigenschaften in einem veröffentlichten Bericht ändern, um den Wert und die Anzeigeeigenschaften zu ändern, doch können Sie den Parameternamen oder den Datentyp nicht ändern. Der Parametername und der Datentyp können nur vom Berichtsautor in der Berichtsdefinition geändert werden.  
  
 Wenn Sie einen parametrisierten Bericht ausführen möchten, müssen Ihnen die einzugebenden Werte normalerweise bekannt sein. Manche Berichte enthalten jedoch Dropdownlisten mit gültigen Werten, die Sie auswählen können.  
  
 Zum Festlegen von Parametereigenschaften für einen veröffentlichten Bericht müssen Sie über die Berechtigung Elemente bearbeiten für den Bericht verfügen. Sie können einige oder alle Parametereigenschaften für einen Bericht ändern, den Sie von einer SharePoint-Website aus ausführen. Es ist nicht möglich, einen Bericht zu personalisieren, indem Sie eine Kombination von häufig benötigten Parameterwerten speichern. Alle Standardwerte, die Sie angeben, werden von allen Benutzern verwendet, die den Bericht öffnen.  
  
 Wenn der Bericht in ein für die Anzeige dieses Berichts konfiguriertes Berichts-Viewer-Webpart eingebettet ist, können Sie die Eigenschaften im Berichts-Viewer-Webpart festlegen. Weitere Informationen finden Sie unter [Hinzufügen des Berichts-Viewer-Webparts zu einer Webseite (Reporting Services im integrierten SharePoint-Modus)](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
### <a name="to-run-a-parameterized-report"></a>So führen Sie einen parametrisierten Bericht aus  
  
1.  Öffnen Sie die Bibliothek, die den Bericht enthält.  
  
2.  Klicken Sie auf den Namen des Berichts. Sie müssen im Voraus wissen, welche Berichte Parameter besitzen. Der Bericht enthält kein sichtbares Kennzeichen für die Parametrisierung.  
  
3.  Wenn der Bericht geöffnet wird, geben Sie die zu verwendenden Parameter an. Der Parameterbereich ist je nach im Berichts-Viewer-Webpart festgelegten Eigenschaften sichtbar, reduziert oder ausgeblendet.  
  
    1.  Wenn der Parameterbereich sichtbar ist, wählen Sie einen Wert für jeden Parameter aus.  
  
    2.  Wenn am Rand des Berichts ein dünner farbiger Streifen mit einem Pfeil in der Mitte verläuft, ist der Parameterbereich reduziert. Sie können ihn erweitern, indem Sie auf den Pfeil klicken.  
  
    3.  Wenn der Parameterbereich ausgeblendet ist, können Sie keinen Wert angeben.  
  
4.  Klicken Sie unten im Parameterbereich auf **Anwenden** , um den Bericht auszuführen.  
  
     Es kann vorkommen, dass die angegebene Kombination von Werten nicht das erwartete Ergebnis liefert. Unter Umständen muss der Bericht vom Berichtsautor geändert werden, wenn Sie nicht die gewünschten Informationen erhalten.  
  
5.  Klicken Sie auf **OK**.  
  
### <a name="to-set-parameter-properties"></a>So legen Sie Parametereigenschaften fest  
  
1.  Öffnen Sie die Bibliothek oder den Ordner mit dem Bericht.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Pfeil nach unten.  
  
3.  Klicken Sie auf **Parameter verwalten**. Falls der Bericht Parameter enthält, werden alle Parameter auf der Seite aufgeführt. Die Liste enthält den Parameternamen, den Datentyp, den standardmäßig verwendeten Datenwert und die Angabe, ob er beim Öffnen des Berichts im Parameterbereich sichtbar ist.  
  
4.  Klicken Sie auf einen Parameter in der Liste, um seine Einstellungen zu ändern.  
  
5.  Geben Sie unter Standardwert einen Wert für den Parameter ein. Der Wert wird nicht überprüft. Stellen Sie daher sicher, dass Sie einen für den Bericht geeigneten Wert bereitstellen.  
  
    1.  Wählen Sie **In Berichtsdefinition angegebenen Wertausdruck verwenden** aus, wenn Sie den beim Erstellen des Berichts festgelegten Standardwert verwenden möchten. Wenn von der Berichtsdefinition kein Standardwert bereitgestellt wird, ist diese Option nicht verfügbar.  
  
    2.  Wählen Sie **Standardwert des Berichts überschreiben** aus, wenn Sie einen Ersatzwert für den Standardwert der Berichtsdefinition angeben möchten. Optional können Sie für Berichtsparameter, die Nullwerte annehmen, das Kontrollkästchen **Null** aktivieren, um das Filtern nach diesem Parameter zu verhindern.  
  
    3.  Wählen Sie **Der Parameter enthält keinen Standardwert** aus, wenn jeder Benutzer vor der Verarbeitung des Berichts einen Wert angeben soll. Wenn Sie diese Option auswählen, sollten Sie Anzeigeeinstellungen für die Eingabeaufforderung an den Benutzer festlegen.  
  
     Beachten Sie, dass ein Bericht beim Öffnen durch einen Benutzer automatisch mit den Standardwerten ausgeführt wird, wenn alle Parameter über einen Standardwert verfügen. Wenn der Parameterbereich jedoch angezeigt wird, können Benutzer den Standardwert überschreiben und den Bericht erneut ausführen.  
  
6.  Legen Sie Anzeigeoptionen fest, um zu bestimmen, ob der Parameter sichtbar ist.  
  
    1.  Wählen Sie **Eingabeaufforderung für Benutzer** aus, um den Parameter auf der Seite anzuzeigen. Sie können einen in einem Feld anzuzeigenden Aufforderungstext angeben, der eine kurze Anweisung zum Format oder Typ der Daten enthält, die der Benutzer bereitstellen muss.  
  
    2.  Wählen Sie **Ausgeblendet** aus, wenn ein Standardwert verwendet wird und der Parameter im Parameterbereich nicht sichtbar sein soll.  
  
    3.  Wählen Sie **Intern** aus, wenn ein Standardwert verwendet wird und der Parameter im Parameterbereich oder auf Abonnementseiten nicht sichtbar sein soll.  
  
7.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SharePoint Site and List Permission Reference for Report Server Items (Referenz zu SharePoint-Website- und Listenberechtigungen für Berichtsserverelemente)](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
