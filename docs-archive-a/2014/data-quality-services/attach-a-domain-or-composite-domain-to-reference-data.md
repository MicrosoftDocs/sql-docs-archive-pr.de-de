---
title: Anfügen einer Domäne oder Verbund Domäne an Verweis Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.refdata.f1
- sql12.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d54dcb01823253eeda92cc3a576d73a45de4ef7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609476"
---
# <a name="attach-a-domain-or-composite-domain-to-reference-data"></a>Anfügen einer Domäne oder Verbunddomäne an Verweisdaten
  In diesem Thema wird beschrieben, wie Domänen/Verbund Domänen in einer Data Quality-Wissensdatenbank an einen Verweis Datendienst in Azure Marketplace angefügt werden, um Wissen mit qualitativ hochwertigen Verweis Daten zu erstellen. Jeder Verweisdatendienst enthält ein Schema (Datenspalten). Nachdem eine Domäne oder eine Verbunddomäne an einen Verweisdatendienst angefügt wurde, müssen Sie die angefügte Domäne bzw. die einzelnen Domänen innerhalb der Verbunddomäne den entsprechenden Spalten im Schema des Verweisdatendiensts zuordnen. Indem eine Verbunddomäne an einen Verweisdatendienst angefügt wird, haben Sie die Möglichkeit, nur eine Domäne an einen Verweisdatendienst anzufügen. Daraufhin können Sie den entsprechenden Spalten im Schema des Verweisdatendiensts die einzelnen Domänen innerhalb der Verbunddomäne zuordnen.  
  
> [!WARNING]  
>  Die an einen Verweisdatendienst angefügte Verbunddomäne ist in der Domänen-Dropdownliste verfügbar, während Domänen den Spalten in Schema des Verweisdatendiensts zugeordnet werden. Ordnen Sie die Verbunddomäne keiner Spalte im Schema des Verweisdatendiensts zu; Sie dürfen den entsprechenden Spalten im Schema des Verweisdatendiensts nur einzelne Domänen innerhalb einer Verbunddomäne zuordnen. Andernfalls tritt ein Fehler auf.  
  
 Das Schema eines Verweisdatendiensts kann über eine erforderliche Spalte verfügen, die mit der entsprechenden Domäne zugeordnet werden muss, wenn Sie einen Verweisdatendienst verwenden möchten. Die erforderliche Spalte in einem Verweisdatenschema wird mit einem „(M)“ im Spaltennamen gekennzeichnet. So ist **AddressLine** beispielsweise die erforderliche Schemaspalte in **Melissa Data (Adressdaten)**, und **CompanyName** ist die erforderliche Schemaspalte in **Digital Trowel Inc. (US-Unternehmen und professionelle Daten für SQL-Benutzer)**.  
  
 In diesem Thema erstellen wir vier Domänen: **Adresszeile**, **Ort**, **Bundesland** und **PLZ**, unter einer Verbunddomäne, **Adressüberprüfung**, fügen die Verbunddomäne an den Verweisdatendienst **Melissa Data (Adressüberprüfung)** an und ordnen die einzelnen Domänen innerhalb der Verbunddomäne anschließend den entsprechenden Spalten im Schema des Verweisdatendiensts zu.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Sie müssen [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) konfiguriert haben, um Verweisdatendienste zu verwenden. Siehe [Konfigurieren von DQS zum Verwenden von Verweisdaten](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
#### <a name="permissions"></a>Berechtigungen  
 Sie müssen über die dqs_kb_editor-Rolle in der DQS_MAIN-Datenbank verfügen, um Domänen Verweisdaten zuzuordnen.  
  
##  <a name="map-domains-to-reference-data-from-melissa-data"></a><a name="Map"></a>Zuordnen von Domänen zu Verweis Daten aus Melissa Data  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm unter **Wissensdatenbank-Verwaltung**auf **Neue Wissensdatenbank**.  
  
3.  Geben Sie im Bildschirm **Neue Wissensdatenbank** einen Namen für die neue Wissensdatenbank ein, klicken Sie auf die Aktivität **Domänenverwaltung** , und klicken Sie auf **Erstellen**.  
  
4.  Klicken Sie im Bildschirm **Domänenverwaltung** auf das Symbol **Domäne erstellen** , um eine Domäne zu erstellen. Erstellen Sie die folgenden vier Domänen: **Adresszeile**, **Ort**, **Bundesland**und **PLZ**.  
  
5.  Klicken Sie auf das Symbol **Verbunddomäne erstellen** , um eine Verbunddomäne zu erstellen. Geben Sie im Dialogfeld **Verbunddomäne erstellen** im Feld **Name der Verbunddomäne** den Text **Adressenüberprüfung** ein, und schließen Sie alle Domänen ein, die unter Schritt 3 in der Verbunddomäne erstellt wurden. Klicken Sie auf **OK**.  
  
6.  Wählen Sie im Bereich **Domäne** auf der linken Seite die Verbunddomäne aus, indem Sie auf **Adressenüberprüfung**klicken, und klicken Sie dann auf der rechten Seite auf die Registerkarte **Verweisdaten** .  
  
7.  Klicken Sie auf das Symbol **Durchsuchen** .  
  
8.  Im Dialogfeld **Onlinekatalog der Reference Data Service-Anbieter** :  
  
    1.  Aktivieren Sie unter **DataMarket Data Quality Services** das Kontrollkästchen **Melissa Data (Adressüberprüfung)**.  
  
    2.  Ordnen Sie die Spalten des Verweisdatendiensts Melissa Data (Adressüberprüfung) den entsprechenden Domänen (Adresszeile, Ort, Bundesland und PLZ) zu. Sie ordnen die Spalten zu, indem Sie in der Spalte **RDS-Schema** eine Verweisdatendienst-Spalte auswählen und dann die entsprechende Domäne in der Spalte **Domäne** auswählen. Um mehr Zeilen in der Tabelle hinzuzufügen, klicken Sie auf das Symbol **Schemaeintrag hinzufügen** .  
  
    3.  Klicken Sie auf **OK** , um die Änderungen zu speichern, und schließen Sie das Dialogfeld **Onlinekatalog der Reference Data Service-Anbieter** .  
  
         ![Dialogfeld "Onlinekatalog der Reference Data Service-Anbieter"](../../2014/data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Dialogfeld "Onlinekatalog der Reference Data Service-Anbieter"")  
  
        > [!NOTE]  
        >  -   Im Dialogfeld **Online Katalog der Verweis Datenanbieter** zeigt der Knoten **datamarket Data Quality Services** alle Reference Data Service-Anbieter an, die Sie in Azure Marketplace abonniert haben. Wenn Sie in DQS direkte Drittanbieter von Online-Verweisdatendiensten konfiguriert haben, werden diese unter einem anderen Knoten mit der Bezeichnung **Direkte Drittanbieter-Onlineanbieter** angezeigt (zu diesem Zeitpunkt nicht verfügbar, da keine direkten Drittanbieter von Online-Verweisdatendiensten in DQS konfiguriert sind).  
  
9. Sie kehren zur Registerkarte **Verweis Daten** zurück. Ändern Sie im Bereich **Anbieter Einstellungen** ggf. die Werte in den folgenden Feldern:  
  
    -   **Schwellenwert für Autokorrektur**: Korrekturen aus dem Verweisdatendienst mit einem Vertrauensgrad über den Schwellenwerten werden automatisch vorgenommen. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,9 für 90 % ein.  
  
    -   **Vorgeschlagene Kandidaten**: Anzahl der vorgeschlagenen Kandidaten aus dem Verweisdatendienst, die angezeigt werden sollen.  
  
    -   **Minimaler Vertrauensgrad**: Vorschläge aus dem Verweisdatendienst mit einem Vertrauensgrad, der niedriger als dieser Wert ist, werden ignoriert. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,6 für 60 % an.  
  
10. Klicken Sie auf **Fertig stellen** , um die Wissensdatenbank zu veröffentlichen. Eine Bestätigungsmeldung wird angezeigt, nachdem die Wissensdatenbank erfolgreich veröffentlicht wurde.  
  
 Sie können diese Wissensdatenbank jetzt für Bereinigungs Aktivitäten in einem Data Quality-Projekt verwenden, um US-Adressen in den Quelldaten zu standardisieren und zu bereinigen, basierend auf den von Melissa Data über Azure Marketplace bereitgestellten Kenntnissen.  
  
##  <a name="follow-up-after-mapping-a-domain-to-reference-data"></a><a name="FollowUp"></a> Nachverfolgung: Nach dem Zuordnen einer Domäne zu Verweisdaten  
 Erstellen Sie ein Data Quality-Projekt, und führen Sie die Bereinigungsaktivität für die Quelldaten aus, die US-Adressen enthalten, indem Sie diese mit der in diesem Thema erstellten Wissensdatenbank vergleichen. Siehe [Bereinigen von Daten mit Wissen über &#40;externe&#41; Verweisdaten](../../2014/data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verweis Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)   
 [Datenbereinigung](../../2014/data-quality-services/data-cleansing.md)  
  
  
