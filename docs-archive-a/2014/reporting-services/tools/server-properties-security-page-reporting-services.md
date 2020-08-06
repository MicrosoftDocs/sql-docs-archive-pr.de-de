---
title: Servereigenschaften (Seite „Sicherheit“) – Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f709d42bf593b4933d9fc1fdc423c195967df382
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619011"
---
# <a name="server-properties-security-page---reporting-services"></a>Servereigenschaften (Seite Sicherheit) – Reporting Services
  Verwenden Sie diese Seite, um Funktionen zu deaktivieren, die potenziell einen Berichtsserver gefährden können. Die Deaktivierung dieser Funktionen führt zu einigen Funktionseinschränkungen, kann jedoch die Gesamtsicherheit durch Verringerung bestimmter Bedrohungen erhöhen.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie anschließend **Eigenschaften**aus. Klicken Sie auf **Sicherheit** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Tastatur  
 **Integrierte Sicherheit von Windows für Berichtsdatenquellen-Verbindungen aktivieren**  
 Geben Sie an, ob eine Verbindung mit einer Berichtsdatenquelle mithilfe des Windows-Sicherheitstokens des Benutzers hergestellt werden kann, der den Bericht angefordert hat.  
  
 Wenn Sie diese Funktion deaktivieren, ist die Funktion Integrierte Sicherheit von Windows in der Eigenschaftenseite der Berichtsdatenquelle nicht mehr verfügbar. Wenn Berichtsdatenquellen für die integrierte Sicherheit von Windows konfiguriert werden, und Sie dann diese Funktion deaktivieren, aktualisiert der Berichtsserver sofort die Datenverbindungseigenschaften aller Datenquellen so, dass sie Anmeldeinformationen anfordern.  
  
 **Ad-hoc-Berichterstellung aktivieren**  
 Geben Sie an, ob Benutzer Ad-hoc-Abfragen von einem Bericht des Berichts-Generators ausführen können, wodurch automatisch neue Berichte generiert werden, sobald ein Benutzer auf die ihn interessierenden Daten klickt.  
  
 Durch Festlegen dieser Option wird bestimmt, ob der Wert der `EnableLoadReportDefinition`-Eigenschaft auf `True` oder `False` festgelegt wird. Wenn Sie diese Option deaktivieren, wird die Eigenschaft auf `False` festgelegt, und der Berichtsserver generiert keine Berichte mit Durchklicken für Berichte, die während des Durchsuchens der Daten erstellt werden. Alle Aufrufe der `LoadReportDefinition`-Methode werden blockiert.  
  
 Die Deaktivierung dieser Option führt zu einem Sicherheitsrisiko, weil böswillige Benutzer einen Denial-of-Service-Angriff ausführen können, bei dem der Berichtsserver mit `LoadReportDefinition`-Anforderungen überlastet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#40;Management Studio Eigenschaften für Berichts Server festlegen&#41;](set-report-server-properties-management-studio.md)   
 [Herstellen einer Verbindung mit einem Berichts Server in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Angeben von Anmelde Informationen und Verbindungsinformationen für Berichtsdaten Quellen] (.. /Report-Data/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.MD [Report Server in Management Studio F1-Hilfe](report-server-in-management-studio-f1-help.md)  
  
  
