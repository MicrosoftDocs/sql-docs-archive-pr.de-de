---
title: Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- administering Reporting Services
- published reports [Reporting Services], managing
- report servers [Reporting Services], content management
- content management [Reporting Services]
ms.assetid: 641961ac-53a5-4997-9d42-cf4ecce1f892
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b63429c43d4bf8c57b4bb6a1e39b3e8bce1d97e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621332"
---
# <a name="report-server-content-management-ssrs-native-mode"></a>Verwalten von Berichtsserverinhalten (einheitlicher SSRS-Modus)
  In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]verweist die Inhaltsverwaltung auf die Verwaltung von Berichtsserverelementen. Alle Elemente lassen sich durch Eigenschaften und Sicherheitseinstellungen unabhängig verwalten. Alle Elemente können an einen anderen Speicherort im Ordnernamespace des Berichtsservers verschoben werden. Zur effektiven Verwaltung der Elemente muss Ihnen bekannt sein, welche Aufgaben von einem Inhalts-Manager ausgeführt werden.

> [!NOTE]
>  Die Inhaltsverwaltung unterscheidet sich von der Berichtsserververwaltung. Weitere Informationen zum Verwalten einer Umgebung, in der ein Berichtsserver ausgeführt wird, finden Sie unter [Reporting Services-Berichtsserver (einheitlicher Modus)](reporting-services-report-server-native-mode.md).

 Die Inhaltsverwaltung umfasst die folgenden Aufgaben:

-   Sichern Sie die Berichtsserverwebsite und -elemente mithilfe der mit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]bereitgestellten rollenbasierten Sicherheit.

-   Erstellen Sie durch Hinzufügen, Ändern und Löschen von Ordnern eine Ordnerhierarchie für den Berichtsserver.

-   Legen Sie Standardwerte und Eigenschaften fest, die für die mittels Berichtsserver verwalteten Elemente gelten. Beispielsweise können Sie Höchstwerte für die Speicherrichtlinien von Berichtsverläufen festlegen.

-   Erstellen Sie freigegebene Datenquellenelemente, die anstelle von berichtsspezifischen Datenquellenverbindungen verwendet werden können. Ein Verleger oder Inhalts-Manager kann eine andere als die ursprünglich für einen Bericht angegebene Datenquelle auswählen. Beispielsweise, um einen Verweis auf eine Testdatenbank durch einen Verweis auf eine Produktionsdatenbank zu ersetzen.

-   Erstellen Sie freigegebene Zeitpläne, die sich anstelle von berichts- und abonnementspezifischen Zeitplänen verwenden lassen. Dadurch vereinfacht sich im Laufe der Zeit die Verwaltung der Zeitplaninformationen.

-   Erstellen Sie datengesteuerte Abonnements zur Erstellung von Empfängerlisten durch das Abrufen von Daten von einem Datenspeicher.

-   Gleichen Sie Berichtsverarbeitungsanforderungen für den Server ab. Planen Sie dazu die Berichtsverarbeitung und geben Sie an, welche bei Bedarf auszuführen bzw. aus dem Cache zu laden sind.

-   Gewähren Sie anhand von vordefinierten Rollen die Berechtigung zum Ausführen von Verwaltungsaufgaben: **Systemadministrator** und **Inhalts-Manager**. Eine effektive Verwaltung des Berichtsserverinhalts erfordert, dass Sie beiden Rollen zugewiesen sind.

 Tools zum Verwalten von Berichtsserverinhalt schließen [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] bzw. den Berichts-Manager ein. [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] ermöglicht es Ihnen, Standards festzulegen und Funktionen zu aktivieren. Der Berichts-Manager wird verwendet, um Benutzern Zugriff auf Berichtsserverelemente und -vorgänge zu gewähren und Berichte und andere Inhaltstypen sowie alle freigegebenen Elemente und Berichtsverteilungsfunktionen anzuzeigen und zu verwenden. Weitere Informationen finden Sie unter [Reporting Services-Tools](../tools/reporting-services-tools.md).

##  <a name="report-server-items"></a><a name="bkmk_ReportServerItems"></a>Berichts Server Elemente
 Zu Berichtsserverelementen gehören Berichte, freigegebene Datenquellen, freigegebene Datasets, Berichtsteile, Ressourcen (Elemente, die auf einem Berichtsserver gespeichert, jedoch nicht von diesem verarbeitet werden) und Ordner. Elemente können von anderen Elementen abhängen. Beispielsweise kann ein Bericht von den freigegebenen Datenquellen abhängen, auf die er verweist. Wenn Sie ein abhängiges Element verschieben, aktualisiert der Berichtsserver die Verweisinformationen automatisch.

 Sie können Berichtsserverelemente an andere Speicherorte in der Ordnerhierarchie des Berichtsservers verschieben. Beim Verschieben eines Elements werden auch alle zugehörigen Eigenschaften (einschließlich Sicherheitseinstellungen) an den neuen Speicherort verschoben. Wenn Sie einen Ordner verschieben, werden gleichzeitig alle in diesem Ordner enthaltenen Elemente verschoben.

 Im Berichts-Manager werden die verschiebbaren Elemente in der Ordnerhierarchie angezeigt. In der folgenden Tabelle sind die Symbole für die verschiedenen verschiebbaren Elemente dargestellt.

|Symbol|Verschiebbares Element|
|----------|-------------------|
|![Berichtssymbol](../media/hlp-16doc.gif "Berichtssymbol")|Bericht|
|![Symbol für einen verknüpften Bericht](../media/hlp-16linked.gif "Symbol für einen verknüpften Bericht")|Verknüpfter Bericht|
|![Ordnersymbol](../media/hlp-16folder.gif "Ordnersymbol")|Ordner|
|![allgemeines Ressourcensymbol](../media/hlp-16file.gif "allgemeines Ressourcensymbol")|Allgemeine Ressource|
|![Symbol für freigegebene Datenquelle](../media/hlp-16datasource.png "Symbol für freigegebene Datenquelle")|Freigegebene Datenquelle|
||Freigegebenes Dataset|

 Nicht alle Elemente, mit denen Sie arbeiten, können verschoben werden. Elemente, die einem Bericht zugeordnet sind, z. B. Abonnements oder ein Berichtsverlauf, können nicht verschoben werden. Diese Elemente werden mit den zugehörigen Berichten verschoben. Auch Elemente wie freigegebene Zeitpläne, die außerhalb der Ordnerhierarchie vorhanden sind, können nicht verschoben werden. Sie können ohne die entsprechende Berechtigung keine Elemente verschieben. Die Berechtigung zum Verschieben eines Elements wird erteilt, wenn folgende Tasks in Ihrer Rollenzuweisung für das entsprechende Element ausgewählt sind: "Berichte verwalten", "Modelle verwalten", "Ordner verwalten" und "Datenquellen verwalten".

##  <a name="folders"></a><a name="bkmk_Folders"></a> Ordner
 Eine Ordnerhierarchie wird für die Adressierung von Elementen verwendet, die von einem Berichtsserver gespeichert und verwaltet werden.  Standardmäßig besteht die Ordnerstruktur aus einem Stammknoten (Home) und reservierten Ordnern, die die optionale Funktion "Meine Berichte" unterstützen. Zusätzliche Ordner sind benutzerdefiniert. Berichtsserverordner sind hilfreich, falls Sie dieselbe Ebene des Zugriffs auf mehrere Elemente gewähren möchten. Berechtigungen, die Sie für den Ordner festlegen, können von Elementen im Ordner sowie von zusätzlichen verzweigten Ordnern geerbt werden. Sie können beispielsweise einen Ordnersatz unter dem Ordner "Home" erstellen, Teamberechtigungen für jeden Ordner zuweisen und dann Teammitgliedern ermöglichen, Ordner unter dem Teamordner je nach Bedarf anzupassen.

 Bei Verwendung eines Browsers für die direkte Verbindung mit einem Berichtsserver entspricht der Stammknoten der Ordnerstruktur dem Namen des virtuellen Berichtsserververzeichnisses. Über den Stammknoten können Sie Ordner je nach Bedarf erstellen, ändern und löschen, um den Berichtsserverinhalt zu organisieren. Sie können Inhalt zu einem Ordner hinzufügen, Elemente zwischen Ordnern verschieben, Ordnernamen oder Speicherorte ändern sowie nicht mehr benötigte Ordner löschen.

 Ordner sind virtuelle Container für veröffentlichte Elemente, auf die Sie über den Berichts-Manager oder eine Browserverbindung mit dem Berichtsserver zugreifen. Weder die Ordner noch ihr Inhalt sind tatsächlich in einem Dateisystem vorhanden. Stattdessen werden sie in der Berichtsserver-Datenbank gespeichert, und es wird über den Webdienst-Endpunkt des Berichtsservers darauf zugegriffen. Der Ordnernamespace des Berichtsservers stellt eine Hierarchie aus einem Stammknoten, aus vordefinierten und benutzerdefinierten Ordnern dar. Durch den Namespace werden die auf einem Berichtsserver gespeicherten Elemente eindeutig identifiziert. Er stellt ein Adressierungsschema zum Angeben von Elementen in einer URL bereit. Wenn Sie einen Bericht auswählen oder danach suchen, wird der Ordnerpfad für diesen Bericht Teil der URL.

 Ihre Arbeitsweise mit Ordnern hängt von den Aufgaben ab, die Bestandteil Ihrer Rollenzuweisung sind. Falls Sie die Standardsicherheit verwenden, können Inhalts-Manager und Verleger Ordner erstellen und verwalten. Wenn Sie benutzerdefinierte Rollenzuweisungen verwenden, muss die Rollenzuweisung Aufgaben für die Ordnerverwaltung enthalten. Weitere Informationen zu Rollenzuweisungen und Tasks finden Sie unter [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](../security/granting-permissions-on-a-native-mode-report-server.md) und [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md).

 Berichtsserverordner können die folgenden Elemente enthalten:

-   Berichte

-   Freigegebene Datenquellen

-   Freigegebene Datasets

-   Berichtsteile

-   Ressourcen (Elemente, die auf einem Berichtsserver gespeichert, aber nicht von ihm verarbeitet werden)

-   Andere Ordner

### <a name="reserved-folders"></a>Reservierte Ordner
 Vordefinierte Ordner sind von Reporting Services reserviert und können weder verschoben noch umbenannt oder gelöscht werden. Die benutzerdefinierten Ordner schließen alle Ordner ein, die von einem Benutzer oder Berichtsadministrator mit der Berechtigung zum Hinzufügen von Elementen zu einem Ordner erstellt wurden.

 In der folgenden Tabelle sind die vordefinierten Ordner beschrieben, auf denen die Ordnerhierarchie aufbaut und die ein Framework für eine Reihe von Funktionen bieten.

|Ordner|Zweck|
|------------|-------------|
|-Startseite|Der Stammknoten der Ordnerhierarchie.|
|Benutzer|Dieser Ordner wird angezeigt, wenn Sie die Funktion "Meine Berichte" aktivieren. Er enthält Unterordner für alle Benutzer der Funktion Meine Berichte und ist nur für Berichtsserveradministratoren verfügbar. Der Name des Unterordners entspricht dem Namen des Benutzers.|
|Meine Berichte|Stellt einen persönlichen Arbeitsbereich für jeden Benutzer bereit.|

### <a name="creating-folders"></a>Erstellen von Ordnern
 Sie können einen Ordner in einem verfügbaren Ordner in der Hierarchie erstellen.

 Fall Sie Ordner zur Beschränkung des Zugriffs auf bestimmte Berichte und Modelle erstellen, müssen Sie Rollenzuweisungen festlegen, mit denen Benutzer den Inhalt von im Ordnerpfad enthaltenen, übergeordneten Ordnern durchsuchen jedoch nicht anzeigen können.

### <a name="modifying-folder-properties"></a>Ändern der Ordnereigenschaften
 Nachdem Sie einen Ordner erstellt haben, können Sie dessen Eigenschaften ändern, um den Ordner umzubenennen, eine Beschreibung hinzuzufügen oder zu ändern sowie den Ordner an einen anderen Speicherort zu verschieben. Diese Eigenschaften finden Sie auf der Eigenschaftenseite Allgemein für den Ordner. Weitere Informationen zum Festlegen von Eigenschaften, die den Zugriff auf einen Ordner steuern, finden Sie unter [Sichere Ordner](../security/secure-folders.md).

### <a name="deleting-folders-and-folder-contents"></a>Löschen von Ordnern und Ordnerinhalten
 Beim Löschen eines Ordners werden alle darin enthaltenen Elemente gelöscht. Vor dem Löschen eines Ordners sollten Sie feststellen, ob er Elemente enthält, auf die andere Elemente in einem anderen Bereich der Ordnerhierarchie verweisen bzw. die von solchen Elementen verwendet werden. Zu solchen Elementen, auf die verwiesen wird, zählen Berichtsdefinitionen, die verknüpfte Berichte, freigegebene Datenquellen und Ressourcen unterstützen.

 Beim Löschen eines Berichts mit einem oder mehreren verknüpften Berichten, die auf diesen Bericht verweisen, werden die verknüpften Berichte nach dem Löschen des Berichts ungültig. Es ist nicht möglich, im Voraus zu wissen, welche verknüpften Berichte betroffen sind. In einem Bericht werden nämlich keine Informationen zu verknüpften Berichten, die auf diesem Bericht basieren, gespeichert. Sie können jedoch die Eigenschaften eines verknüpften Berichts prüfen, um festzustellen, auf welchem Bericht er basiert. Im Gegensatz dazu werden in freigegebenen Datenquellenelementen alle Berichte aufgeführt, die aktuell das Element verwenden. Auf diese Weise können Sie auf einfache Weise bestimmen, ob die Verbindungsinformationen verwendet werden. Weitere Informationen finden Sie unter [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](../report-data/create-modify-and-delete-shared-data-sources-ssrs.md). Zudem identifizieren Ressourcen, die von Berichten verwendet werden, diese Berichte nicht.

 Überlegen Sie vor dem Löschen eines Ordners, ob der Berichtsverlauf eines Berichts, den Sie löschen möchten, oder eine berichtsspezifische Struktur (z. B. ein datengesteuertes Abonnement), das Bestandteil eines Berichts ist, erhalten bleiben muss. Falls Sie solche Informationen benötigen, verschieben Sie das Element in einen anderen Ordner, bevor Sie den Ordner löschen.

 Die Sichtbarkeit eines Elements in einem Ordner hängt sowohl von den Rollenzuweisungen (d. h. Berechtigung zum Anzeigen eines Elements) als auch von den Anzeigeoptionen für den jeweiligen Ordner ab. Im Berichts-Manager können Sie die Seite Inhalt auf Listenansicht oder Detailansicht festlegen. In einigen Fällen kann ein Bericht oder ein Element in der Listenansicht ausgeblendet sein. Zeigen Sie einen Ordner unbedingt in der Detailansicht an, bevor Sie seinen Inhalt löschen.

##  <a name="resources"></a><a name="bkmk_Resources"></a> Ressourcen
 Eine Ressource ist ein verwaltetes Element, das auf einem Berichtsserver gespeichert wird, jedoch nicht vom Berichtsserver verarbeitet wird. In der Regel stellt eine Ressource externen Inhalt für die Benutzerberichterstattung bereit. Beispiele beinhalten ein Bild als JPG-Datei, eine ESRI-Shape-Datei mit räumlichen Daten oder eine HTML-Datei mit einer Beschreibung der in einem Bericht verwendeten Geschäftsregeln. Die JPG-, SHP- oder HTML-Datei wird auf dem Berichtsserver gespeichert, wobei der Berichtsserver die Datei jedoch direkt an den Browser weiterleitet, ohne sie zuerst zu verarbeiten. Weitere Informationen finden Sie unter [Images &#40;Berichts-Generator und SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) und im Abschnitt "Hinzufügen von Daten zu einer Karte" in [Maps &#40;Berichts-Generator und SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md).

### <a name="adding-and-viewing-a-resource"></a>Hinzufügen und Anzeigen einer Ressource
 Um einem Berichtsserver eine Ressource hinzuzufügen, laden Sie eine Datei hoch oder veröffentlichen sie:

|Vorgang|Dateityp|
|---------------|---------------|
|Upload|Zum Hochladen einer Ressource verwenden Sie den Berichts-Manager, wenn der Berichtsserver im einheitlichen Modus ausgeführt wird, oder eine Anwendungsseite auf einer SharePoint-Website, wenn der Berichtsserver im integrierten SharePoint-Modus ausgeführt wird. Weitere Informationen finden Sie unter [Hochladen einer Datei oder eines Berichts &#40;Berichts-Manager&#41;](../reports/upload-a-file-or-report-report-manager.md) oder [Hochladen von Dokumenten in eine SharePoint-Bibliothek &#40;Reporting Services im SharePoint-Modus&#41;]. /Upload-Documents-to-a-SharePoint-Library-Reporting-Services-in-SharePoint-Mode.MD).|
|Veröffentlichen|Alle Dateien in einem Projekt, die keine Berichte, Berichtsteile, Datenquellen oder Datasets darstellen, werden als Ressourcen hochgeladen. Fügen Sie zum Veröffentlichen einer Ressource einem Projekt im Berichts-Designer ein vorhandenes Objekt hinzu, und veröffentlichen Sie das Projekt dann auf einem Berichtsserver.|

 Alle Ressourcen stehen als Dateien, die anschließend auf einen Berichtsserver hochgeladen werden, in einem Dateisystem bereit. Außer der standardmäßigen Größenbeschränkung von 4 MB in ASP.NET gibt es keine Einschränkungen bezüglich der hochzuladenden Dateien. Zum Veröffentlichen als Ressource auf einem Berichtsserver sind jedoch einige Dateitypen, die über entsprechende MIME-Typen verfügen, besser geeignet als andere. Ressourcen, die auf HTML- und JPG-Dateien basieren, werden z.B. in einem Browserfenster geöffnet, wenn der Benutzer auf die Ressource klickt. Die HTML-Datei wird als Webseite und die JPG-Datei als Bild gerendert. Andererseits können Ressourcen ohne entsprechende MIME-Typen, die auf Desktopanwendungsdateien basieren, beispielsweise im Browserfenster möglicherweise nicht gerendert werden.

 Ob eine Ressource von den Benutzern eines Berichts angezeigt werden kann, hängt von den Anzeigemöglichkeiten des Browsers ab. Da Ressourcen nicht vom Berichtsserver verarbeitet werden, muss der Browser die Ansichtsfunktionen zum Rendern eines bestimmten MIME-Typs bereitstellen. Falls der Browser den Inhalt nicht rendern kann, können Benutzer, die die Ressource anzeigen, nur die allgemeinen Eigenschaften der Ressource sehen.

### <a name="securing-and-managing-a-resource"></a>Sichern und verwalten von Ressourcen
 Ressourcen sind neben Berichten, freigegebenen Datenquellen, freigegebenen Zeitplänen und Ordnern als benannte Objekte in der Ordnerhierarchie des Berichtservers vorhanden. Sie können nach Ressourcen suchen, sie anzeigen, sichern und Einstellungen festlegen, wie es für jedes andere auf einem Berichtsserver gespeicherte Objekt möglich ist. Zum Anzeigen oder Verwalten einer Ressource muss Ihre Rollenzuweisung die Aufgaben zum Anzeigen und Verwalten von Ressourcen umfassen.

### <a name="referencing-an-image-resource-from-a-report"></a>Verweisen auf eine Bildressource von einem Bericht
 Ressourcen können ein Bild enthalten, auf das Sie in einem Bericht verweisen. Wenn die Berichtsanforderungen die Verwendung von externen Bildern umfassen, ziehen Sie die folgenden Vorteile beim Speichern des Bilds als Ressource in Betracht:

-   Zentrale Speicherung in der Berichtsserver-Datenbank: Wenn Sie die Berichtsserver-Datenbank und ihren Inhalt auf einen anderen Computer übertragen, wird das externe Bild im Bericht beibehalten. Sie müssen keine Bilddateien nachverfolgen, die auf einem Datenträger auf unterschiedlichen Computern gespeichert sind.

-   Gesichert durch Rollenzuweisungen statt Dateisystemsicherheit: Die gleichen Berechtigungen, die zum Anzeigen eines Berichts verwendet werden, können auch auf die Ressource angewendet werden. Im Gegensatz dazu müssen Sie beim Speichern des Bilds auf einem Datenträger sicherstellen, dass entweder das anonyme Benutzerkonto oder das Konto für die unbeaufsichtigte Ausführung über die Berechtigung zum Zugreifen auf die Datei verfügt.

 Sie können eine Bildressource in einem Bericht verwenden, indem Sie die Bilddatei dem Projekt hinzufügen und es mit dem Bericht veröffentlichen. Nach dem Veröffentlichen des Bilds können Sie den Bildverweis im Bericht aktualisieren, sodass er auf die Ressource auf dem Berichtsserver verweist, und dann nur den Bericht erneut veröffentlichen, um die Änderungen zu speichern. Sie können anschließend das Bild unabhängig vom Bericht aktualisieren, indem Sie die Ressource erneut veröffentlichen. Der Bericht verwendet die aktuelle Version des Bilds, die auf dem Berichtsserver verfügbar ist.

 Weitere Informationen finden Sie unter [Aktualisieren einer Ressource &#40;Berichts-Manager&#41;](update-a-resource-report-manager.md).

##  <a name="my-reports"></a><a name="bkmk_MyReports"></a>Meine Berichte
 Der Ordner Meine Berichte ist ein persönlicher Arbeitsbereich für jeden Benutzer, der sich bei einem Berichtsserver mit einem gültigen Domänenkonto anmeldet. Dieser spezielle Ordner bietet Speicherplatz für derzeit bearbeitete Berichte, für Berichte, die nicht für die allgemeine Weitergabe gedacht sind, oder für Berichte, die für einen speziellen Zweck geändert wurden. Es ist nicht möglich, die Anzahl oder die Größe der im Ordner Meine Berichte gespeicherten Elemente einzuschränken oder einen Ordner Meine Berichte für Benutzer freizugeben.

 Meine Berichte ordnet den Namen eines virtuellen Ordners, der für jeden Benutzer sichtbar ist (Meine Berichte) einem Masterordner Benutzerordner und einem eindeutigen Unterordner basierend auf dem Benutzernamen zu. Wenn ein Benutzer auf seinen Ordner Meine Berichte zugreift, wird der Benutzer in Wirklichkeit an seinen Unterordner unter Benutzerordner weitergeleitet. Jeder Unterordner enthält Speicherplatz für die Berichte und Elemente, die ein Benutzer zu seinem Ordner "Meine Berichte" hinzufügt.

 Der Ordner "Benutzerordner" wird beim Installieren des Berichtsservers erstellt. Nachfolgende benutzerbasierte Unterordner werden erstellt, wenn ein Benutzer Meine Berichte zum ersten Mal öffnet (z. B. durch Klicken auf Meine Berichte im Berichts-Manager). Ordnernamen weisen folgendes Format auf:

```
/Users Folders/<username>/My Reports
```

 Nur Benutzern mit gültigen Systemkonten werden Ordner zugewiesen. Enthält ein Benutzername Sonderzeichen, wird er mit den entsprechenden Escapezeichen erstellt. Die entsprechenden Escapezeichen sind in der folgenden Tabelle aufgeführt.

|Zeichen|Escapewert|Beispiel|
|---------------|------------------|-------------|
|(Leerzeichen)|[ ]|*Vorname Nachname* wird zu *Vorname[ ]Nachname*|
|\ (umgekehrter Schrägstrich)|Wird durch ein einzelnes Leerzeichen ersetzt|*Domänenname\Benutzername* wird zu *Domänenname Benutzername*|
|@ (at-Zeichen)|[at]|*Benutzername* @hotmail.com wird zu *username*[at] hotmail. com|
|& (kaufmännisches Und-Zeichen)|[amp]|*Benutzername* @ *Unternehmen* & *Company.com* wird zu *username*[at]*Company*[amp]*Company.com*|
|$ (Dollarzeichen)|[dollar]|*Benutzer*  $ *Name* wird zu *Benutzer*[] [Dollar]*Name*|

 Die Funktion "Meine Berichte" ist optional. Bei der Installation eines Berichtsservers wird "Meine Berichte" standardmäßig deaktiviert. Weitere Informationen zum Aktivieren dieser Funktion finden Sie unter [Aktivieren und Deaktivieren von "Meine Berichte"](enable-and-disable-my-reports.md). Weitere Informationen finden Sie unter [Sichern von Meine Berichte](../security/secure-my-reports.md).

## <a name="tasks"></a>Tasks
 [Hochladen von Dateien in einen Ordner](upload-files-to-a-folder.md)

 [Erstellen, Löschen oder Ändern eines Ordners &#40;Berichts-Manager&#41;](create-delete-or-modify-a-folder-report-manager.md)

 [Aktualisieren einer Ressource &#40;Berichts-Manager&#41;](update-a-resource-report-manager.md)

 [Hochladen von Dateien in einen Ordner](upload-files-to-a-folder.md)

## <a name="see-also"></a>Weitere Informationen
 [Reporting Services Tools](../tools/reporting-services-tools.md) [Rollen und Berechtigungen &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md) [Reporting Services Berichte &#40;SSRS&#41;](../reports/reporting-services-reports-ssrs.md)


