---
title: Verwalten (öffnen, entsperren, umbenennen und löschen) eines Data Quality-Projekts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621673"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>Verwalten von Data Quality-Projekten (Öffnen, Entsperren, Umbenennen, Löschen)
  In diesem Thema wird beschrieben, wie ein Data Quality-Projekt mithilfe von [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] verwaltet wird, zum Beispiel das Öffnen, Entsperren, Umbenennen und Löschen eines Data Quality-Projekts.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
  
-   Sie können kein gesperrtes Projekt öffnen, das von einem anderen Benutzer erstellt wurde.  
  
-   Sie können kein Data Quality-Projekt entsperren, umbenennen oder löschen, das von einem anderen Benutzer erstellt wurde.  
  
-   Sie können kein gesperrtes Data Quality-Projekt löschen. Zum Löschen müssen Sie es zunächst entsperren.  
  
-   Sie können nur ein Data Quality-Projekt entsperren, das von Ihnen erstellt wurde.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Sie müssen mindestens ein Data Quality-Projekt verwalten.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle „dqs_kb_editor“ oder „dqs_kb_operator“ in der Datenbank DQS_MAIN verfügen, um ein Data Quality-Projekt zu verwalten.  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> Öffnen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
     Sie können ein unter **Zuletzt verwendetes Data Quality-Projekt** aufgelistetes Data Quality-Projekt auch direkt öffnen, indem Sie darauf klicken.  
  
3.  Wählen Sie auf dem Bildschirm **Projekt öffnen** das zu öffnende Data Quality-Projekt durch Klicken aus, und klicken Sie auf **Weiter**.  
  
4.  Das Data Quality-Projekt wird mit demselben Aktivitätsstatus geöffnet, mit dem es zuletzt geschlossen wurde. Ein Data Quality-Projekt hat die folgenden Status:  
  
    -   Für die Bereinigungs **Aktivität kann** ein Data Quality-Projekt die folgenden Zustände aufweisen: **Bereinigung-** zuordnen, **Bereinigung-** bereinigen, **Bereinigung-Ergebnisse verwalten und anzeigen**und **Bereinigung-Export**.  
  
    -   Für die **Matching** abgleichsaktivität kann ein Data Quality-Projekt die folgenden Zustände aufweisen: " **Matching-Map**", " **Matching-Matching**", " **Matching-vorship**" und " **Matching-Export**".  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> Entsperren eines Data Quality-Projekts  
 Wenn Sie ein Data Quality-Projekt erstellen, ist es gesperrt, um zu verhindern, dass es von anderen Benutzern verwendet oder geändert wird. Sie müssen das Data Quality-Projekt entsperren, nachdem Sie die Arbeit abgeschlossen haben, wenn Sie möchten, dass andere Benutzer am Data Quality-Projekt arbeiten können. Ein Schlosssymbol wird für gesperrte Projekte angezeigt.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein gesperrtes Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Entsperren** . Ein grünes Häkchen wird für das Projekt angezeigt, das angibt, dass es entsperrt wurde.  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a>Umbenennen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Umbenennen** .  
  
4.  Der Name des Data Quality-Projekts kann in der Spalte **Name** bearbeitet werden. Heben Sie einen neuen Namen ein, und drücken Sie die EINGABETASTE.  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a>Löschen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein entsperrtes Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Löschen** .  
  
4.  Eine Bestätigungsmeldung wird angezeigt. Klicken Sie auf **Ja**.  
  
  
