---
title: Neuer freigegebener Zeitplan (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newschedule.f1
ms.assetid: b2c69586-d98e-4933-827d-f5e6c15c5203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6afd406730f815d3ab61e59cdebd21d564daa74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615796"
---
# <a name="new-shared-schedule-management-studio"></a>Neuer freigegebener Zeitplan (Management Studio)
  Mithilfe dieser Seite können Sie einen freigegebenen Zeitplan zur Ausführung veröffentlichter Berichte und Abonnements erstellen. Feigegebene Zeitpläne können anstelle berichts- oder abonnementspezifischer Zeitpläne verwendet werden. Zentralisierte Zeitplaninformationen und die Möglichkeit, geplante Vorgänge anhalten und fortsetzen zu können, sind zwei Schlüsselfunktionen, die freigegebene Zeitpläne von elementspezifischen Zeitplänen unterscheiden.  
  
 Nicht alle Kombinationen der Häufigkeit können in einem einzelnen Zeitplan unterstützt werden. Wenn ein Bericht z. B. um 00:00 Uhr und um 16:00 Uhr an jedem Freitag ausgeführt werden soll, müssen Sie zwei Tageszeitpläne erstellen, in denen der Freitag als Ausführungstag angegeben ist. Der erste Zeitplan hat eine Startzeit von 00:00 Uhr, und für den zweiten ist eine Startzeit von 16:00 Uhr festgelegt.  
  
 Die Verarbeitung von Zeitplänen basiert auf der Ortszeit des Berichtsservers, auf dem der Zeitplan gehostet und verarbeitet wird.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einem Berichtsserver herstellen. Klicken Sie mit der rechten Maustaste auf **Freigegebener Zeitplan**, und wählen Sie dann **Neuer Zeitplan**aus. Um den Zeitplan zu speichern, muss der SQL Server-Agent-Dienst ausgeführt werden.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2012-Editionen unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für den freigegebenen Zeitplan ein. Dieser Name wird in Dropdownlisten angezeigt, wenn Benutzer einen freigegebenen Zeitplan für Berichte und Abonnements auswählen. Stellen Sie sicher, dass Sie einen aussagekräftigen Namen angeben, der in eine Liste passt und den freigegebenen Zeitplan gut von einem anderen unterscheidet. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = +, $/*\< >  
  
 " /  
  
 **Diesen Zeitplan ausführen ab**  
 Geben Sie ein Startdatum für diesen Zeitplan an.  
  
 **Dieser Zeitplan endet am**  
 Geben Sie ein Ablaufdatum für diesen Zeitplan an.  
  
 **Typ**  
 Gibt an, ob die Wiederholungsoption hauptsächlich auf Stunden, Tagen, Wochen oder Monaten basiert.  
  
 **Stunde (Serienmuster)**  
 Wählen Sie Optionen für die Ausführung eines geplanten Vorgangs in Stundenintervallen aus (um einen Bericht z. B. alle 6 Stunden auszuführen). Das Intervall kann in Stunden und Minuten angegeben werden.  
  
 **Tag (Serienmuster)**  
 Wählen Sie Optionen für die Ausführung eines geplanten Vorgangs in Tagesintervallen aus (um einen Bericht z. B. alle 2 Tage auszuführen). Sie können das Intervall in Tagen und mit der Stunde und Minute der Ausführung des Zeitplans angeben.  
  
 **Woche (Serienmuster)**  
 Wählen Sie Optionen für die Ausführung eines geplanten Vorgangs in Wochenintervallen aus. Dies gilt auch für den Fall, dass das zu wiederholende Muster auf Wochen basiert (wenn Sie einen Bericht z. B. jede zweite Woche ausführen wollen). Sie können bei einem wöchentlichen Zeitplan den Tag, die Stunde und die Minute für die Ausführung des Zeitplans angeben.  
  
 **Monat (Serienmuster)**  
 Wählen Sie Optionen für die Ausführung eines geplanten Vorgangs in Monatsintervallen aus. Dies gilt auch für den Fall, dass das zu wiederholende Muster auf Monaten basiert. Sie können bei einem monatlichen Zeitplan den Tag, die Stunde und die Minute für die Ausführung des Zeitplans angeben. Sie können im Zeitplan bestimmte Monate auslassen.  
  
 **Einmal**  
 Wählen Sie diese Option aus, um einen Zeitplan zu erstellen, der zu einem bestimmten Termin einmal ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](../subscriptions/create-modify-and-delete-schedules.md)   
 [Zeitpläne](../subscriptions/schedules.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)  
  
  
