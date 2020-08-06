---
title: Erstellen einer BI-Semantik Modell Verbindung mit einer Power Pivot-Arbeitsmappe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620578"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a>Herstellen einer BI-Semantikmodellverbindung mit einer PowerPivot-Arbeitsmappe
  Verwenden Sie die Informationen in diesem Thema, um eine BI-Semantikmodellverbindung einzurichten, die zu einer PowerPivot-Arbeitsmappe in der gleichen Farm umleitet.  
  
 Nachdem Sie eine BI-Semantikmodellverbindung erstellt und SharePoint-Berechtigungen konfiguriert haben, können Sie sie als Datenquelle für Excel- oder [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte verwenden.  
  
 Das Thema enthält folgende Abschnitte: Führen Sie jede Aufgabe in der angegebenen Reihenfolge aus.  
  
 [Überprüfen der Voraussetzungen](#bkmk_prereq)  
  
 [Erstellen einer Verbindung](#bkmk_create)  
  
 [Konfigurieren von SharePoint-Berechtigungen für die BI-Semantik Modell Verbindung](#bkmk_permissions)  
  
 [Konfigurieren von SharePoint-Berechtigungen für die Arbeitsmappe](#bkmk_userdb)  
  
 [Next Steps](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a>Voraussetzungen prüfen  
 Sie benötigen Teilnahmeberechtigungen oder weiterreichende Berechtigungen, um eine BI Semantikmodell-Verbindungsdatei zu erstellen.  
  
 Sie benötigen eine Bibliothek, die den Inhaltstyp der BI Semantikmodellverbindung unterstützt. Weitere Informationen finden [Sie unter Hinzufügen eines BI-Semantik Modell-Verbindungs-Inhaltstyps zu einer Bibliothek &#40;PowerPivot für SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).  
  
 Sie müssen die URL der Power Pivot-Arbeitsmappe kennen, für die Sie eine BI-Semantik Modell Verbindung einrichten (z http://adventure-works/shared . b. Dokumente/myworkbook.xlsx). Die Arbeitsmappe muss in der gleichen Farm sein.  
  
 Alle Computer und Benutzer, die Teil der Verbindungssequenz sind, müssen in der gleichen Domäne bzw. vertrauenswürdigen Domäne (bidirektionale Vertrauensstellung) enthalten sein.  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a>Erstellen einer Verbindung  
  
1.  Klicken Sie in der Bibliothek, die die BI-Semantikmodellverbindung enthalten soll, auf **Dokumente** im SharePoint-Menüband. Klicken Sie in „Neues Dokument“ auf den Pfeil nach unten, und wählen Sie **BISM-Verbindungsdatei** aus, um die Seite „Neue BI-Semantikmodellverbindung“ zu öffnen.  
  
     ![Untermenü "Neues Dokument" in einer SharePoint-Bibliothek](../media/ssas-bismconnection-new.gif "Untermenü "Neues Dokument" in einer SharePoint-Bibliothek")  
  
2.  Legen Sie die **Server** -Eigenschaft auf die SharePoint-URL der Power Pivot-Arbeitsmappe (z. b. ** http://mysharepoint/shared Dokumente/myWorkbook.xlsx**fest. In einer Bereitstellung von PowerPivot für SharePoint können Daten auf jeden Server in der Farm geladen werden. Aus diesem Grund geben Datenquellenverbindungen mit PowerPivot-Daten nur den Pfad zur Arbeitsmappe an. Der PowerPivot-Systemdienst bestimmt, welcher Server die Daten lädt.  
  
     Verwenden Sie die **Database** -Eigenschaft nicht. Er wird nicht verwendet, wenn der Speicherort einer Power Pivot-Arbeitsmappe angegeben wird.  
  
     Die Seite sollte ähnlich der folgenden Abbildung aussehen.  
  
     ![BISM-Verbindungsseite mit URL der Arbeitsmappe](../media/ssas-bismconnection-ppvtds.gif "BISM-Verbindungsseite mit URL der Arbeitsmappe")  
  
     Wenn Sie über SharePoint-Berechtigungen an der Arbeitsmappe verfügen, wird optional ein zusätzlicher Überprüfungsschritt ausgeführt, der sicherstellt, dass der Speicherort gültig ist. Wenn Sie nicht über die Berechtigung verfügen, auf die Daten zuzugreifen, wird Ihnen die Option gegeben, die BI-Semantikmodellverbindung ohne die Überprüfungsantwort zu speichern.  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a> Konfigurieren von SharePoint-Berechtigungen für die BI-Semantikmodellverbindung  
 Damit eine BI-Semantikmodellverbindung als Datenquelle für eine Excel-Arbeitsmappe oder einen Reporting Services-Bericht verwendet werden kann, muss das BI-Semantikmodell-Verbindungselement über **Leseberechtigungen** in einer SharePoint-Bibliothek verfügen. Die Berechtigungsebene „Lesen“ schließt die Berechtigung **Elemente öffnen** ein, die das Herunterladen von BI-Semantikmodell-Verbindungsinformationen in eine Excel-Desktopanwendung ermöglicht.  
  
 Es gibt mehrere Möglichkeiten, Berechtigungen in SharePoint zu erteilen. Die folgenden Anweisungen erläutern, wie Sie eine neue Gruppe mit dem Namen **BISM-Benutzer** erstellen, die die Berechtigungsstufe **Lesen** haben.  
  
 Sie müssen Websitebesitzer sein, um Berechtigungen zu ändern.  
  
1.  Klicken Sie in „Websiteaktionen“ auf **Websiteberechtigungen**.  
  
2.  Klicken Sie auf **Gruppe erstellen** , und nennen Sie die neue Gruppe **BISM-Benutzer**.  
  
3.  Wählen Sie die Berechtigungsstufe **Lesen** aus, und klicken Sie auf **Erstellen**.  
  
4.  Wählen Sie **BISM-Benutzer** in „Personen und Gruppen“ aus.  
  
5.  Zeigen Sie auf „Neu“, klicken Sie auf **Benutzer hinzufügen**, und fügen Sie dann Benutzer- oder Gruppenkonten hinzu.  
  
     Diese Benutzer und die Gruppen haben jetzt Leseberechtigungen überall in der Website, einschließlich aller Bibliotheken und Listen, die Berechtigungen von der Websiteebene erben. Wenn diese Berechtigungen zu hoch sind, können Sie diese Gruppe aus bestimmten Bibliotheken, Listen oder Elementen selektiv entfernen.  
  
 Um Berechtigungen auf Elementebene selektiv zu entfernen, gehen Sie wie folgt vor:  
  
1.  Wählen Sie in einer Bibliothek ein Dokument aus. Klicken Sie auf den rechten Pfeil nach unten, und klicken Sie auf **Berechtigungen verwalten**.  
  
2.  Standardmäßig erbt ein Element Berechtigungen. Um die Berechtigungen von einzelnen Dokumenten in dieser Bibliothek zu ändern, klicken Sie auf **Berechtigungsvererbung beenden**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben **BISM-Benutzer**.  
  
4.  Klicken Sie auf **Benutzerberechtigungen entfernen**.  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a> Konfigurieren von SharePoint-Berechtigungen für die Arbeitsmappe  
 Wenn Sie in einer Excel-Arbeitsmappe eine PowerPivot-Datenbank verwenden, bestimmen die SharePoint-Berechtigungen für die Excel-Arbeitsmappe den Datenzugriff auf die BI-Semantikmodellverbindung. Alle Benutzer, die auf die Arbeitsmappe zugreifen, müssen Leseberechtigungen für die Arbeitsmappe haben, um sie als externe Datenquelle zu verwenden.  
  
 Wenn Sie eine Gruppe **BISM-Benutzer** mithilfe der Anweisungen im vorherigen Abschnitt erstellt haben, haben Benutzer- und Gruppenkonten, die Mitglieder von **BISM-Benutzer** sind, ausreichende Berechtigungen für die Arbeitsmappe und für die BI-Semantikmodell-Verbindungsdatei, wenn die Arbeitsmappe geerbte Berechtigungen verwendet.  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> Nächste Schritte  
 Nachdem Sie eine BI-Semantikmodellverbindung erstellt und gesichert haben, können Sie sie als Datenquelle angeben. Weitere Informationen finden Sie unter [Verwenden einer BI-Semantikmodellverbindung in Excel oder Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Power Pivot BI-Semantik Modell Verbindung &#40;. bism-&#41;](power-pivot-bi-semantic-model-connection-bism.md)   
 [Verwenden einer BI-Semantik Modell Verbindung in Excel oder Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)   
 [Erstellen einer BI-Semantikmodellverbindung mit einer tabellarischen Modelldatenbank](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
