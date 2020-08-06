---
title: Zwischenspeichern eines Berichts (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e359e6c7a40b267979137ef2b3a285667a6fdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619609"
---
# <a name="cache-a-report-report-manager"></a>Zwischenspeichern eines Berichts (Berichts-Manager)
  Eine Möglichkeit, die Leistung zu verbessern, ist die Konfiguration von Zwischenspeichereigenschaften für einen Bericht. Beim Zwischenspeichern eines Berichts wird eine Kopie des gerenderten Berichts für einen kurzen Zeitraum gespeichert. Der erste Benutzer, der den Bericht anfordert, muss warten, bis die gesamte Verarbeitung abgeschlossen ist, bevor er den Bericht anzeigen kann. Nachfolgende Benutzer, die den Bericht innerhalb des Zeitraums der Zwischenspeicherung anfordern, können ihn sofort anzeigen, da die Verarbeitung bereits durchgeführt wurde.  
  
 Es gibt Einschränkungen in Bezug auf die Berichtstypen, die Sie zwischenspeichern können. Ein Bericht kann z. B. nicht zwischengespeichert werden, wenn die Berichtsausgabe je nach Benutzeridentität variiert oder wenn Daten mithilfe des Sicherheitstokens des Benutzers abgerufen werden, der den Bericht anfordert. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>So planen Sie den Ablauf eines zwischengespeicherten Berichts  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** . Navigieren Sie zum Bericht, für den Sie Zwischenspeichereigenschaften festlegen möchten, zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4.  Klicken Sie im linken Bereich auf **Verarbeitungsoptionen**.  
  
5.  Wählen Sie auf der Seite die Option **Diesen Bericht immer mit den neuesten Daten ausführen**.  
  
6.  Wählen Sie eine der folgenden zwei Cacheoptionen aus, und konfigurieren Sie den Ablauf wie folgt:  
  
    -   Wenn die zwischengespeicherte Kopie nach einem bestimmten Zeitraum ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Diese Kopie soll nach der folgenden Anzahl von Minuten ablaufen**. Geben Sie die Anzahl von Minuten für den Berichtsablauf ein.  
  
    -   Wenn eine zwischengespeicherte Kopie nach einem bestimmten Zeitplan ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Diese Kopie soll gemäß dem folgenden Zeitplan ablaufen.** Klicken Sie auf **Konfigurieren**, oder wählen Sie einen freigegebenen Zeitplan für die Steuerung des Berichtsablaufs aus.  
  
7.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsverarbeitungseigenschaften](set-report-processing-properties.md)   
 [Zwischenspeichern von Berichten &#40;SSRS&#41;](caching-reports-ssrs.md)  
  
  
