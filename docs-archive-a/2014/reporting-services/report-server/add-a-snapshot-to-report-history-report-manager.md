---
title: Hinzufügen einer Momentaufnahme zum Berichtsverlauf (Berichts-Manager) | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 84d4c264ab0b82fca2a34e6356b53113d63e6994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619626"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a>Hinzufügen einer Momentaufnahme zum Berichtsverlauf (Berichts-Manager)

Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Ein Berichtsmomentaufnahme ist ein Bericht, der Layoutinformationen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Während für bedarfsgesteuerte Berichte aktuelle Abfrageergebnisse abgerufen werden, wenn Sie den Bericht auswählen, werden Berichtsmomentaufnahmen anhand eines Zeitplans verarbeitet und anschließend auf einem Berichtsserver gespeichert. Wenn Sie eine Berichtsmomentaufnahme zum Anzeigen auswählen, ruft der Berichtsserver den gespeicherten Bericht aus der Berichtsserver-Datenbank ab und zeigt die Daten und das Layout an, die zum Zeitpunkt der Momentaufnahmeerstellung für den Bericht aktuell waren.  
  
Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Durch das verzögerte Rendering wird eine Momentaufnahme portabel. Der Bericht kann jeweils im richtigen Format für das anfordernde Gerät oder den anfordernden Webbrowser gerendert werden.  
  
## <a name="to-manually-add-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf manuell Momentaufnahmen hinzu

1. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.
  
2. Klicken Sie im Dropdownmenü auf **Berichtsverlauf anzeigen**.  
  
3. Klicken Sie auf **Neue Momentaufnahme**. In der Spalte **Ausführungszeitpunkt** wird eine neue Momentaufnahme erstellt.  
  
    > [!NOTE]
    > Dazu muss der Berichtsverlauf vom Administrator auf **Verlauf kann manuell erstellt werden**konfiguriert sein. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs &#40;Berichts-Manager&#41;](../reports/limit-report-history-report-manager.md).

4. Klicken Sie auf **Anwenden**.

## <a name="to-automatically-add-all-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf automatisch alle Momentaufnahmen hinzu  
  
1. Für einen Bericht, der bereits für die Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, können Sie zusätzliche Eigenschaften festlegen, um bei jeder Aktualisierung der Momentaufnahme eine Kopie der Momentaufnahme im Berichtsverlauf zu speichern.  
  
2. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.  
  
3. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4. Klicken Sie auf **Momentaufnahmeoptionen**.  
  
5. Aktivieren Sie das Kontrollkästchen **Alle Berichtsausführungs-Momentaufnahmen im Verlauf speichern**.  
  
6. Klicken Sie auf **Anwenden**.  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>So fügen Sie basierend auf einem Zeitplan automatisch Momentaufnahmen zum Berichtsverlauf hinzu  
  
1. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Klicken Sie auf **Momentaufnahmeoptionen**.  
  
4. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie einen der folgenden Schritte aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  
  
    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  
  
5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren von Ausführungseigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../reports/configure-execution-properties-for-a-report-report-manager.md)
- [Öffnen und Schließen eines Berichts (Berichts-Manager)](../reports/open-and-close-a-report-report-manager.md)
- [Einschränken des Berichtsverlaufs (Berichts-Manager)](../reports/limit-report-history-report-manager.md)
- [Zeitpläne](../subscriptions/schedules.md)   
- [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)