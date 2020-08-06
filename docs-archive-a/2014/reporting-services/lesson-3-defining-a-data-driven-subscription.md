---
title: 'Lektion 3: Definieren eines datengesteuerten Abonnements | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726581"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a>Lesson 3: Defining a Data-Driven Subscription
  In dieser Lektion verwenden Sie die datengesteuerten Abonnementseiten für folgende Zwecke: um eine Verbindung mit einer Abonnementdatenquelle herzustellen, um eine Abfrage zu erstellen, die Abonnementdaten abruft, und um das Resultset den Berichts- und Übermittlungsoptionen zuzuordnen.  
  
> [!NOTE]  
>  Prüfen Sie vor dem Starten, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird. Ist dies nicht der Fall, können Sie das Abonnement nicht speichern.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie Lektion 1 und Lektion 2 abgeschlossen haben und dass die Berichtsdatenquelle gespeicherte Anmeldeinformationen verwendet.  Weitere Informationen finden Sie unter [Lektion 2: Ändern der Eigenschaften der Berichtsdatenquelle](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md).  
  
 Inhalte dieses Themas:  
  
-   [Starten des Assistenten für datengesteuerte Abonnements](#bkmk_startwizard)  
  
-   [Schritt 1 - Beschreibung definieren](#bkmk_definesubscription)  
  
-   [Schritt 2 - Verbindung mit der Abonnentendatenquelle definieren](#bkmk_defineconnectiontosubscriber)  
  
-   [Schritt 3 - Abfrage für das Abrufen von Abonnentendaten definieren](#bkmk_definequery)  
  
-   [Schritt 4 - Übermittlungsoptionen festlegen](#bkmk_set_deliveryoptions)  
  
-   [Schritt 5 - Parameterwert zum Variieren der Berichtsausgabe konfigurieren](#bkmk_configure_parameter)  
  
-   [Schritt 6 - Abonnement planen](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a>Starten des Assistenten für datengesteuerte Abonnements  
  
1.  Klicken Sie im Berichts-Manager auf **Home**, und navigieren Sie zum Ordner mit dem Bericht **Sales Orders** .  
  
2.  Klicken Sie im Kontextmenü des Berichts auf **Verwalten**und dann auf die Registerkarte **Abonnements** .  
  
3.  Klicken Sie auf **Neues datengesteuertes Abonnement**. Wenn diese Schaltfläche nicht angezeigt wird, verfügen Sie möglicherweise nicht über Inhalts-Manager-Berechtigungen.  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a>Schritt 1: Definieren einer Beschreibung  
  
1.  Geben Sie **Lieferung Verkaufsauftrag** bei Beschreibung ein.  
  
2.  Wählen Sie **Windows-Dateifreigabe** für **Angeben, wie die Empfänger benachrichtigt werden**.  
  
3.  Wählen Sie **Nur für dieses Abonnement angeben**und klicken Sie dann auf **Weiter**.  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a>Schritt 2: Definieren einer Verbindung mit der Abonnentendaten Quelle  
  
1.  Wählen Sie **Microsoft SQL Server** als Quelldatentyp aus.  
  
2.  Geben Sie unter Verbindungszeichenfolge die folgende Verbindungszeichenfolge ein:  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  "Abonnenten" ist die Datenbank, die Sie in Lektion 1 erstellt haben.  
  
3.  Klicken Sie auf **Anmeldeinformationen, die sicher im Berichtsserver gespeichert sind**.  
  
4.  Geben Sie unter **Benutzername** und **Kennwort**Ihren Benutzernamen und Ihr Kennwort für die Domäne ein. Geben Sie unter **Benutzername**sowohl die Domäne als auch das Benutzerkonto an.  
  
    > [!NOTE]  
    >  Die Anmeldeinformationen, die für die Verbindung mit einer Abonnentendatenquelle verwendet werden, werden nicht an [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]zurückgegeben. Wenn Sie das Abonnement später ändern, müssen Sie das Kennwort zum Herstellen der Verbindung mit der Datenquelle erneut eingeben.  
  
5.  Wählen Sie **Als Windows-Anmeldeinformationen verwenden, wenn eine Verbindung zur Datenquelle hergestellt wird**aus, und klicken Sie dann auf **Weiter**.  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a>Schritt 3: Definieren einer Abfrage zum Abrufen von Abonnentendaten  
  
1.  Geben Sie im Abfragefeld folgende Abfrage ein:  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  Geben Sie ein Timeout von 30 Sekunden an.  
  
3.  Klicken Sie auf **Überprüfen**, und klicken Sie dann auf **Weiter**.  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a>Schritt 4: Festlegen von Übermittlungs Optionen  
  
1.  Wählen Sie für **Dateiname**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie das Feld **Reihenfolge**aus.  
  
2.  Wählen Sie für **Pfad**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie in "Wert festlegen" den Namen einer öffentlichen Dateifreigabe ein, für die Sie Schreibberechtigungen besitzen (z. B. `\\mycomputer\public\myreports`).  
  
3.  Wählen Sie für **Renderformat**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie **Format**aus.  
  
4.  Wählen Sie für den **Schreibmodus**die Option **Geben Sie einen statischen Wert an** aus, und wählen Sie **AutoIncrement**aus.  
  
5.  Wählen Sie für **Dateierweiterung**die Option **Geben Sie einen statischen Wert an** aus, und wählen Sie **True**aus.  
  
6.  Wählen Sie für **Benutzernamen**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie Ihr Domänenbenutzerkonto an. Geben Sie ihn in folgendem Format ein: `<domain>\<account>`. Das Benutzerkonto muss über Berechtigungen zum Pfad verfügen, den Sie in den vorherigen Schritten konfiguriert haben.  
  
7.  Wählen Sie für **Kennwort**die Option **Geben Sie einen statischen Wert an**aus. Geben Sie Ihr Kennwort ein. Achten Sie darauf, dass Sie das Kennwort richtig eingeben. Das Kennwort wird nicht durch den Assistenten überprüft.  
  
8.  Klicken Sie auf **Weiter**.  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a>Schritt 5: Konfigurieren eines Parameter Werts, um die Ausgabe zu melden  
  
1.  Wählen Sie für **OrderNumber**die Option **Rufen Sie den Wert aus der Datenbank ab**aus. Wählen Sie in "Wert" die Option **Reihenfolge**aus. Klicken Sie auf **Weiter**.  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a>Schritt 6: Planen eines Abonnements  
  
1.  Klicken Sie auf **Nach einem Zeitplan, der für dieses Abonnement erstellt wurde**und dann auf **Weiter**.  
  
2.  Klicken Sie in **Zeitplandetails**auf **Einmal**.  
  
3.  Geben Sie eine Startzeit an, die ein paar Minuten nach der aktuellen Zeit liegt.  
  
4.  Klicken Sie auf **Fertig stellen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Beim Ausführen des Abonnements werden vier Berichtsdateien an die von Ihnen angegebene Dateifreigabe übermittelt, eine für jeden Auftrag in der *Abonnenten* -Datenquelle. Jede Übermittlung muss im Hinblick auf die Daten (sie müssen sich auf einen bestimmten Auftrag beziehen), das Renderingformat und das Dateiformat eindeutig sein. Sie können jeden Bericht von dem freigegebenen Ordner aus öffnen, um sicherzustellen, dass jede Version entsprechend den von Ihnen festgelegten Abonnementoptionen angepasst wurde.  
  
 ![Liste der vom Abonnement erstellten Dateien](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "Liste der vom Abonnement erstellten Dateien")  
  
 Die Abonnementseite im Berichts-Manager enthält das **Letzte Ausführungsdatum** und den **Status** des Abonnements.  
  
> [!NOTE]  
>  Aktualisieren Sie die Seite, nachdem das Abonnement ausgeführt wurde, um die aktualisierten Informationen zu sehen.  
  
 ![Abonnementergebnisse im Berichts-Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Abonnementergebnisse im Berichts-Manager")  
  
 Dies ist der letzte Schritt im Lernprogramm "Definieren eines datengesteuerten Abonnements". Weitere Informationen zu anderen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Tutorials finden Sie unter [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines datengesteuerten Abonnements &#40;SSRS-Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md)   
 [Erstellen, ändern und Löschen eines datengesteuerten Abonnements](subscriptions/create-modify-and-delete-data-driven-subscriptions.md)   
 [Verwenden einer externen Datenquelle für Abonnentendaten &#40;datengesteuertes Abonnement&#41;](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
