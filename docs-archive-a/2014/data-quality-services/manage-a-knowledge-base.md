---
title: Verwalten einer Wissensdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cc5fdd87ddb3ea687db10a29d7001564fd8ff107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621686"
---
# <a name="manage-a-knowledge-base"></a>Verwalten einer Wissensdatenbank
  In diesem Thema wird beschrieben, wie Verwaltungsfunktionen für eine Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ausgeführt werden. Sie können eine Wissensdatenbank löschen, entsperren, umbenennen, vorgenommene Anpassungen verwerfen und die Eigenschaften der Wissensdatenbank anzeigen.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Um eine Wissensdatenbank zu verwalten, muss die Wissensdatenbank bereits erstellt und entweder veröffentlicht (wenn sie eine andere Person erstellt hat) oder geschlossen (wenn Sie sie erstellt haben) worden sein.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle "dqs_kb_editor" oder "dqs_administrator" in der DQS_MAIN-Datenbank verfügen, um eine Wissensdatenbank zu öffnen.  
  
##  <a name="manage-a-knowledge-base"></a><a name="Manage"></a>Verwalten einer Wissensdatenbank  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie auf dem [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Wissensdatenbank öffnen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Wissensdatenbank in der Wissensdatenbanktabelle.  
  
4.  Im Kontextmenü können Sie folgende Schritte ausführen:  
  
    1.  **Öffnen**: Klicken Sie auf diese Option, um die Wissensdatenbank in der Aktivität zu öffnen, die im Bereich **Aktivität auswählen** ausgewählt ist.  
  
    2.  **Entsperren**: Sie können die Wissensdatenbank entsperren, wenn Sie die Wissensdatenbank im Rahmen der Domänenverwaltungs-, Wissensermittlungs- und Abgleichsrichtlinienaktivitäten bearbeitet und die Wissensdatenbank geschlossen haben. Wenn Sie die Wissensdatenbank entsperren, kann sie von einer anderen Person geöffnet und bearbeitet werden. Dieser Befehl ist nicht verfügbar, wenn sich die Wissensdatenbank nicht in einem Aktivitätszustand befindet. Weitere Informationen finden Sie unter [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Arbeit verwerfen**: Klicken Sie auf diese Option, wenn die Wissensdatenbank bearbeitet wird, wie durch einen Eintrag im Feld Status in der Tabelle angezeigt wird. Dieser Befehl ist nicht verfügbar, wenn sich die Wissensdatenbank nicht in einem Aktivitätszustand befindet oder wenn die Wissensdatenbank gesperrt ist. Weitere Informationen finden Sie unter [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Umbenennen**: Klicken Sie auf diese Option, um das Wissensdatenbankfeld der Tabelle für die Wissensdatenbank, auf die Sie mit der rechten Maustaste geklickt haben, bearbeiten zu können. Ändern Sie den Namen, und klicken Sie dann auf diese Wissensdatenbank und eine andere Wissensdatenbank in dem Feld, um die Namensänderung zu bestätigen.  
  
    5.  **Löschen**: Klicken Sie auf diese Option, um die Wissensdatenbank aus der DQS_MAIN-Datenbank auf dem [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]zu entfernen.  
  
    6.  **Eigenschaften**: Klicken Sie auf diese Option, um die Eigenschaften für die Datenbank im schreibgeschützten Modus anzuzeigen.  
  
        1.  **Quell-Wissensdatenbank**: Wissensdatenbank, auf der diese Datenbank basiert. Diese ist optional.  
  
        2.  **Status**: Gibt an, ob sich die Wissensdatenbank **In Arbeit** und in einer bestimmten Wissensverwaltungsaktivität befindet. Dabei gilt der Status, als sie zum letzten Mal geschlossen wurde. Die Wissensdatenbank kann den Status **In Arbeit**haben – in dem Fall ist sie in einer Wissensverwaltungssitzung, jedoch nicht in einer bestimmten Aktivität geöffnet -, oder sie kann sich im Status **In Arbeit** sowie in einer Wissensverwaltungsaktivität befinden. In dem Fall ist die Wissensdatenbank in einer Wissensverwaltungssitzung und in einer bestimmten Aktivität geöffnet.  
  
        3.  **Ist Gesperrt**: Der Wert ist **True** , wenn die Wissensdatenbank gesperrt wurde, und **False** , wenn sie nicht gesperrt wurde.  
  
        4.  **Enthält nicht veröffentlichten Inhalt**: Der Wert ist True, wenn die Wissensdatenbank Inhalt enthält, der nicht durch eine Veröffentlichung gespeichert wurde, und False, wenn dies nicht der Fall ist.  
  
        5.  **Gesperrt von**: Name des Benutzers, der die Wissensdatenbank geschlossen und dabei gesperrt hat.  
  
        6.  **Sperrdatum**: Datum der Sperrung.  
  
        7.  **Erstellt von**: Name des Benutzers, der die Wissensdatenbank erstellt hat, und das entsprechende Netzwerk.  
  
        8.  **Erstellungsdatum**: Datum der Erstellung.  
  
##  <a name="follow-up-after-managing-a-knowledge-base"></a><a name="FollowUp"></a>Nachverfolgung: nach dem Verwalten einer Wissensdatenbank  
 Der nächste Schritt nach dem Verwalten einer Wissensdatenbank hängt davon ab, welche Aktion Sie für die Wissensdatenbank durchgeführt haben:  
  
-   Wenn Sie die Wissensdatenbank geöffnet haben, fahren Sie mit der Aktivität fort, die Sie ausgewählt haben.  
  
-   Wenn Sie die Wissensdatenbank entsperrt haben, kann diese von einer anderen Person im angegebenen Status geöffnet und bearbeitet werden.  
  
-   Wenn Sie die Anpassungen der Wissensdatenbank verworfen haben, ist sie im zuletzt veröffentlichten Status verfügbar.  
  
-   Wenn Sie die Wissensdatenbank umbenannt haben, müssen Sie die Wissensdatenbank mit dem neuen Namen öffnen, um sie zu bearbeiten.  
  
-   Wenn Sie sie löschen, müssen Sie eine andere Wissensdatenbank für die Bearbeitung auswählen oder eine neue erstellen.  
  
  
