---
title: HTML-Viewer und die Berichtssymbolleiste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML Viewer [Reporting Services]
- report toolbar [Reporting Services]
ms.assetid: cd86b319-babd-45af-a6a4-f659fdcc40c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17b9d4de348807ce5e75b0e67ef36a835ba10cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726690"
---
# <a name="html-viewer-and-the-report-toolbar"></a>HTML-Viewer und die Berichtssymbolleiste
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] stellt einen HTML-Viewer bereit, in dem die Berichte bedarfsgesteuert angezeigt werden können, so wie sie vom Berichtsserver angefordert werden. Der HTML-Viewer stellt ein Framework für das Anzeigen von Berichten in HTML zur Verfügung. Er enthält eine Berichtssymbolleiste, einen Parameterabschnitt, einen Abschnitt mit den Anmeldeinformationen und eine Dokumentstruktur. Die Berichtssymbolleiste im HTML-Viewer enthält Funktionen zum Bearbeiten von Berichten. Dazu zählen auch Exportoptionen, mit deren Hilfe ein Bericht in anderen Formaten als HTML angezeigt werden kann. Der Parameterabschnitt und die Dokumentstruktur werden nur angezeigt, wenn Sie Berichte öffnen, die zum Verwenden von Parametern und eines Dokumentstruktur-Steuerelements konfiguriert sind.  
  
> [!NOTE]  
>  Zwar können Sie die Berichtssymbolleiste nicht ändern, jedoch können Sie die Parameter in einer Berichts-URL so konfigurieren, dass sie in einem Bericht ausgeblendet wird. Weitere Informationen zum Ausblenden der Berichtssymbolleiste finden Sie unter [URL-Zugriffsparameterverweis](url-access-parameter-reference.md).  
  
## <a name="report-toolbar"></a>Berichtssymbolleiste  
 Die Berichtssymbolleiste bietet Funktionen zum Navigieren, Zoomen, Aktualisieren, Suchen, Exportieren, Drucken sowie Datenfeedfunktionen für Berichte, die in der HTML-Renderingerweiterung gerendert werden.  
  
 Die Druckfunktionalität ist optional. Wenn verfügbar, wird ein Druckersymbol auf der Berichtssymbolleiste angezeigt. Wenn Sie erstmalig auf das Druckersymbol klicken, wird ein ActiveX-Steuerelement heruntergeladen, das Sie installieren müssen. Sobald das Steuerelement installiert ist, wird durch Klicken auf das Druckersymbol ein Dialogfeld Drucken geöffnet, in dem Sie einen der auf Ihrem Computer installierten Drucker auswählen können. Die Druckverfügbarkeit ist von den Server- und Browsereinstellungen abhängig. Weitere Informationen finden Sie unter [Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS)](report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) und [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 In der folgenden Abbildung ist die Berichtssymbolleiste dargestellt. Die tatsächlich angezeigte Berichtssymbolleiste kann Unterschiede zu dieser Abbildung aufweisen, da möglicherweise andere Berichtsfunktionen verwendet werden oder andere Renderingoptionen verfügbar sind.  
  
 ![Berichtssymbolleiste](media/htmlviewer-toolbar.gif "Berichtssymbolleiste")  
  
 In der folgenden Tabelle sind häufig verwendete Funktionen der Berichtssymbolleiste erläutert. Jede Funktion wird durch das Steuerelement identifiziert, das Sie für den Zugriff auf die entsprechende Funktion verwenden.  
  
|Symbol oder Steuerelement||To|  
|------------------------------|-|--------|  
|![Steuerelemente für die Seitennavigation](media/htmlviewer-pagenav.gif "Steuerelemente für die Seitennavigation")|**Steuerelemente für die Seitennavigation**|Öffnen der ersten oder letzten Seite eines Berichts, seitenweises Durchführen eines Bildlaufs durch einen Bericht und Öffnen einer bestimmten Seite in einem Bericht. Um eine bestimmte Seite anzuzeigen, geben Sie die Seitenzahl ein, und drücken Sie die EINGABETASTE.|  
|![Steuerelemente für die Seitenanzeige](media/htmlviewer-pagesize.gif "Steuerelemente für die Seitenanzeige")|**Steuerelemente für die Seitenanzeige**|Vergrößern oder Verkleinern der Berichtsseite. Sie können die Größe der Anzeige prozentual ändern oder mithilfe von **Seitenbreite** die horizontale Breite eines Berichts im Browserfenster anpassen bzw. mithilfe von **Gesamte Seite** die vertikale Länge eines Berichts im Browserfenster anpassen. Die Option **Zoom** wird von [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer ab Version 5.5 unterstützt.|  
|![Suchen (Feld)](media/htmlviewer-search.gif "Suchen (Feld)")|**Suchen (Feld)**|Suchen nach Inhalten im Bericht durch das Eingeben eines oder mehrerer Wörter, nach denen Sie suchen möchten (die maximale Länge beträgt 256 Zeichen). Bei der Suche wird die Groß- und Kleinschreibung beachtet, und sie beginnt bei der aktuell ausgewählten Seite oder beim aktuell markierten Abschnitt. Nur sichtbarer Inhalt wird in Suchvorgänge eingeschlossen. Wenn Sie nach weiteren Vorkommen desselben Wertes suchen möchten, klicken Sie auf **Weiter**.|  
|![Exportformate](media/htmlviewer-export.GIF "Exportformate")|**Exportformate**|Öffnen eines neuen Browserfensters und Rendern des Berichts im ausgewählten Format. Welche Formate verfügbar sind, ist durch die auf dem Berichtsserver installierten Renderingerweiterungen bestimmt. Das TIFF-Format wird zum Drucken empfohlen. Klicken Sie auf **Exportieren** , um den Bericht im ausgewählten Format anzuzeigen.|  
|![Dokumentstruktur (Symbol)](media/htmlviewer-docmap.GIF "Dokumentstruktur (Symbol)")|**Dokumentstruktur (Symbol)**|Ein- oder Ausblenden des Dokumentstrukturbereichs in einem Bericht mit Dokumentstruktur. Eine Dokumentstruktur ist ein Steuerelement für die Berichtsnavigation, das mit dem Navigationsbereich auf einer Website vergleichbar ist. Sie können auf Elemente in der Dokumentstruktur klicken, um zu einer bestimmten Gruppe, Seite oder zu einem Unterbericht zu wechseln.|  
|![Drucker (Symbol)](media/printer-icon.gif "Drucker (Symbol)")|**Drucker (Symbol)**|Öffnen des Dialogfelds Drucken, in dem Sie die Druckoptionen festlegen und einen Bericht drucken können. Bei der erstmaligen Verwendung werden Sie nach dem Klicken auf das Symbol aufgefordert, ein Steuerelement zum Drucken herunterzuladen.|  
||**Einblenden und Ausblenden (Symbole)**|Einblenden oder Ausblenden von Feldern mit Parameterwerten und der Schaltfläche **Bericht anzeigen** in einem Bericht mit Parametern.|  
|![Schaltfläche zum Aktualisieren des Browsers auf der Berichtssymbolleiste](media/htmlviewer-refresh.GIF "Browser aktualisieren (Schaltfläche) auf der Berichtsymbolleiste")|**Bericht aktualisieren (Symbol)**|Aktualisieren des Berichts. Daten für Liveberichte werden aktualisiert. Zwischengespeicherte Berichte werden vom jeweiligen Speicherort neu geladen.|  
|![htmlviewer_datafeed](media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|**Datenfeed (Symbol)**|Aus Berichten generierte Datenfeeds.|  
  
### <a name="about-export-formats"></a>Informationen zu Exportformaten  
 Mithilfe der Berichtssymbolleiste können Sie einen Bericht in einer Vielzahl von Formaten anzeigen. Welche Formate verfügbar sind, ist durch die auf dem Berichtsserver installierten Renderingerweiterungen bestimmt. Wenn Sie ein neues Format auswählen, wird der Bericht in einem zweiten Browserfenster angezeigt. Dabei wird ein mit dem ausgewählten Exportformat verbundener Viewer verwendet. Falls für das gewünschte Format kein Viewer verfügbar ist, können Sie ein anderes Format auswählen.  
  
 In einer standardmäßigen Berichtsserverinstallation sind folgende Exportformate enthalten. Die Liste der für Sie verfügbaren Exportformate kann Unterschiede zu dieser Liste aufweisen.  
  
|Exportformat|BESCHREIBUNG|  
|-------------------|-----------------|  
|XML|Zeigt einen Bericht in der XML-Syntax an. Für in XML angezeigte Berichte wird ein neues Browserfenster geöffnet.|  
|CSV|Zeigt einen Bericht in einem durch Trennzeichen getrennten Format. Der Bericht wird in einer Anwendung geöffnet, die mit dem CSV-Dateityp verknüpft ist.|  
|Acrobat-Datei (PDF-Datei)|Zeigt einen Bericht mithilfe eines clientbasierten PDF-Viewers an. Sie benötigen für dieses Format den PDF-Viewer eines Drittanbieters (z. B. Acrobat Reader).|  
|Excel|Zeigt den Bericht in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel an.|  
|Webarchiv|Zeigt den Bericht in einem MIME-codierten HTML-Format an, das Bilder und verknüpften Inhalt zusammen mit einem Bericht speichert.|  
|TIFF-Datei|Zeigt den Bericht im Standard-TIFF-Viewer an. Bei manchen [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Clients ist dies die Windows Bild- und Faxanzeige. Wählen Sie dieses Format aus, um einen Bericht in einem seitenbasierten Layout anzuzeigen.|  
  
## <a name="parameters"></a>Parameter  
 Parameter sind Werte, die zum Auswählen spezifischer Daten verwendet werden. (Sie werden vor allem zum Vervollständigen einer Abfrage verwendet, mit deren Hilfe die Daten für den Bericht ausgewählt werden, oder zum Filtern des Resultsets.) Zu den häufig in Berichten verwendeten Parametern zählen Daten, Namen und IDs. Wenn Sie einen Wert für einen Parameter angeben, enthält der Bericht nur die mit diesem Wert übereinstimmenden Daten, z. B. Mitarbeiterdaten auf der Grundlage eines Parameters für die Mitarbeiter-ID. Parameter entsprechen Feldern im Bericht. Nachdem Sie einen Parameter angegeben haben, klicken Sie zum Abrufen der Daten auf **Bericht anzeigen** .  
  
 Der Autor eines Berichts definiert die für diesen Bericht gültigen Parameterwerte. Auch ein Berichtsadministrator kann Parameterwerte festlegen. Wenn Sie nicht wissen, welche Parameterwerte für einen Bericht gültig sind, können Sie sich an den Autor oder Administrator des Berichts wenden.  
  
## <a name="credentials"></a>Anmeldeinformationen  
 Anmeldeinformationen sind Werte für Benutzernamen und Kennwort, mit deren Hilfe der Zugriff auf eine Datenquelle gewährt wird. Nachdem Sie Ihre Anmeldeinformationen angegeben haben, klicken Sie zum Abrufen der Daten auf **Bericht anzeigen** . Wenn für einen Bericht eine Anmeldung erforderlich ist, können die Daten, zu deren Anzeige Sie berechtigt sind, von den Daten abweichen, die ein anderer Benutzer sieht. Demnach können zwei Benutzer denselben Bericht ausführen und unterschiedliche Ergebnisse erhalten. Einige Berichte enthalten zudem verborgene Bereiche, die auf der Grundlage von Benutzeranmeldeinformationen oder einer im Bericht getroffenen Auswahl eingeblendet werden. Verborgene Bereiche im Bericht sind von Suchvorgängen ausgeschlossen, sodass andere Suchergebnisse angezeigt werden, wenn alle Teile des Berichts sichtbar sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Suchen, anzeigen und Verwalten von Berichten &#40;Berichts-Generator und SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
