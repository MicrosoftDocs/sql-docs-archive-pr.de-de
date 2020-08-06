---
title: Erstellen einer Dokumentstruktur (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c200a97b-67f2-499f-8374-3ed1ebe3f33c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9dad0f8e6ee1d9b9ada44fda0eec5908f27cfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616440"
---
# <a name="create-a-document-map-report-builder-and-ssrs"></a>Erstellen einer Dokumentstruktur (Berichts-Generator und SSRS)
  Eine Dokumentstruktur stellt einen Satz von Navigationslinks zu Berichtselementen in einem gerenderten Bericht bereit. Wenn Sie einen Bericht anzeigen, der eine Dokumentstruktur enthält, wird neben dem Bericht ein Seitenbereich angezeigt. Durch Klicken auf Links in der Dokumentstruktur kann der Benutzer zu bestimmten Seiten in einem Bericht springen, die ein bestimmten Element anzeigen. In diesem Bereich werden Berichtsabschnitte und Gruppen in Form einer Hierarchie aus Links angeordnet. Durch Klicken auf Elemente in der Dokumentstruktur wird der Bericht aktualisiert und der Bereich des Berichts angezeigt, der dem Element in der Dokumentstruktur entspricht.  
  
 Zum Hinzufügen von Links zur Dokumentstruktur legen Sie die `DocumentMapLabel`-Eigenschaft des Berichtselements auf Text fest, den Sie erstellen möchten, oder auf einen Ausdruck, der zu dem Text ausgewertet wird, den Sie in der Dokumentstruktur anzeigen möchten. Sie können der Dokumentstruktur auch die eindeutigen Werte für eine Tabelle oder eine Matrixgruppe hinzufügen. Beispielsweise ist für eine auf Farbe basierende Gruppe jede einzelne Farbe ein Link zur Berichtsseite, die die Gruppeninstanz der jeweiligen Farbe anzeigt.  
  
 Sie können auch eine URL für einen Bericht erstellen, die die Anzeige der Dokumentstruktur überschreibt, sodass Sie den Bericht ohne Anzeigen der Dokumentstruktur ausführen können. Durch Klicken auf die Schaltfläche **Dokumentstruktur ein-/ausblenden** auf der Symbolleiste des Berichts-Viewers können Sie die Anzeige ein- bzw. ausblenden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="document-maps-and-rendering-extensions"></a><a name="DocMapRenderExtensions"></a> Dokumentstrukturen und Renderingerweiterungen  
 Die Dokumentstruktur ist für die Verwendung in der HTML-Renderingerweiterung vorgesehen, z.B. in der Vorschau und im Berichts-Viewer. Andere Renderingerweiterungen verwenden andere Verfahren zum Darstellen einer Dokumentstruktur:  
  
-   PDF rendert eine Dokumentstruktur in Form des Lesezeichen-Bereichs.  
  
-   Excel rendert eine Dokumentstruktur in Form eines benannten Arbeitsblatts, das eine Hierarchie aus Links einschließt. Berichtsbereiche werden in verschiedenen Arbeitsblättern gerendert, die zusammen mit der Dokumentstruktur in dieselbe Arbeitsmappe eingebunden werden.  
  
-   Word schließt eine Dokumentstruktur als Inhaltsverzeichnis ein.  
  
-   Atom, TIFF, XML und CSV berücksichtigen Dokumentstrukturen nicht.  
  
 Weitere Informationen finden Sie unter [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen (Berichts-Generator und SSRS)](../report-builder/interactive-functionality-different-report-rendering-extensions.md).  
  
##  <a name="AddRptItemToMap"></a>   
#### <a name="to-add-a-report-item-to-a-document-map"></a>So fügen Sie einer Dokumentstruktur ein Berichtselement hinzu  
  
1.  Wählen Sie das Berichtselement, wie Tabelle, Matrix oder Messgerät, das Sie der Dokumentstruktur hinzufügen möchten, in der Entwurfsansicht. Die Berichtselementeigenschaften werden im Bereich Eigenschaften angezeigt.  
  
    > [!NOTE]  
    >  Klicken Sie auf eine Zelle, um die Zeilen- und Spaltenziehpunkte anzuzeigen, und klicken Sie dann auf den Eckziehpunt, wenn Sie einen Tablix-Datenbereich wählen möchten.  
  
2.  Geben Sie im Eigenschaften Bereich den Text ein, der in der Dokumentstruktur in der-Eigenschaft angezeigt `DocumentMapLabel` werden soll, oder geben Sie einen Ausdruck ein, der zu einer Bezeichnung ausgewertet wird. Geben Sie beispielsweise **Umsatzdiagramm**ein.  
  
    > [!NOTE]  
    >  Wenn der Eigenschaftenbereich nicht angezeigt wird, klicken Sie in der Registerkarte **Ansicht** in der Gruppe **Ein-/Ausblenden** auf die Option **Eigenschaften**.  
  
3.  Wiederholen Sie Schritt 1und 2 für jedes Berichtselement, das in der Dokumentstruktur angezeigt werden soll.  
  
4.  Klicken Sie auf **Ausführen**. Der Bericht wird ausgeführt, und die Dokumentstruktur zeigt die Bezeichnungen an, die Sie erstellt haben. Klicken Sie auf einen beliebigen Link, um zur Berichtsseite zu wechseln, die dieses Element enthält.  
  
 
  
##  <a name="AddUniqueValuesToMap"></a>   
#### <a name="to-add-unique-group-values-to-a-document-map"></a>So fügen Sie einer Dokumentstruktur eindeutige Gruppenwerte hinzu  
  
1.  Wählen Sie in der Entwurfsansicht die Tabelle, Matrix oder Liste aus, die die Gruppe enthält, die in der Dokumentstruktur angezeigt werden soll. Im Gruppierungsbereich werden die Zeilen- und Spaltengruppen angezeigt.  
  
2.  Klicken Sie im Bereich Zeilengruppen mit der rechten Maustaste auf die Gruppe, und klicken Sie anschließend auf **Gruppe bearbeiten**. Die Seite **Allgemein** des Dialogfelds **Tablix-Gruppeneigenschaften** wird angezeigt.  
  
3.  Klicken Sie auf **Erweitert**.  
  
4.  Geben Sie im Listenfeld **Dokumentstruktur** einen Ausdruck ein, oder wählen Sie einen Ausdruck aus, der dem Gruppenausdruck entspricht.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Wiederholen Sie die Schritte 1-4 für jede Gruppe, die in der Dokumentstruktur angezeigt werden soll.  
  
7.  Klicken Sie auf **Ausführen**. Der Bericht wird ausgeführt, und die Dokumentstruktur zeigt die Gruppenwerte an. Klicken Sie auf einen beliebigen Link, um zur Berichtsseite zu wechseln, die dieses Element enthält.  
  
 
  
##  <a name="HideMapWhenViewRpt"></a>   
#### <a name="to-hide-the-document-map-when-you-view-a-report"></a>So blenden Sie die Dokumentstruktur aus, wenn Sie einen Bericht anzeigen  
  
1.  Wechseln Sie im Berichts-Manager zu dem Bericht, der die Dokumentstruktur aufweist.  
  
     Für die [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] -Beispielberichte gibt beispielsweise die folgende URL den Bericht mit dem Namen des Produktkatalogs an.  
  
    ```  
    http://localhost/Reports/Pages/Report.aspx?ItemPath=%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    ```  
  
2.  Kopieren Sie den Berichtspfad auf dem Server. In dem Beispiel lautet der Berichtspfad `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`.  
  
3.  Erstellen Sie eine neue URL mit den folgenden drei Komponenten:  
  
    -   Dem Berichts-Viewer auf dem Berichtsserver: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`  
  
    -   Dem Namen des Berichts, den Sie in Schritt 1 kopiert haben, z. B: `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`  
  
    -   Den Geräteinformationsparametern, die das Ausblenden der Dokumentstruktur angeben: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`  
  
     Die folgende URL besteht aus diesen drei Komponenten, die in der Reihenfolge angefügt werden, in der sie aufgelistet sind.  
  
    ```  
    http://localhost/ReportServer/Pages/ReportViewer.aspx?  
    %2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    &rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False  
    ```  
  
     Um diese URL zu verwenden, kopieren Sie sie, und entfernen Sie alle Zeilenumbrüche.  
  
4.  Fügen Sie die URL in den Berichts-Manager ein, und drücken Sie dann die EINGABETASTE. Der Bericht wird ausgeführt, und die Dokumentstruktur ist ausgeblendet.  
  
> [!NOTE]  
>  Weitere Informationen zum Herunterladen von Beispielberichten finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte für Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
>   
>  Weitere Informationen finden Sie unter "URL-Zugriff" in der [Reporting Services-Dokumentation](https://go.microsoft.com/fwlink/?linkid=121312) in der SQL Server-Onlinedokumentation.  
  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [Finding and Viewing Reports in Report Manager (Report Builder and SSRS) (Suchen und Anzeigen von Berichten in Berichts-Manager (Berichts-Generator und SSRS))](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
