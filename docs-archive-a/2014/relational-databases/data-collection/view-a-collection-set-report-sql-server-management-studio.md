---
title: Anzeigen eines Sammlungssatzberichts (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621011"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>Anzeigen eines Sammlungssatzberichts (SQL Server Management Studio)
  Nachdem Sie das Verwaltungs-Data Warehouse konfiguriert haben, können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]einen Sammlungssatzbericht anzeigen. Berichte werden für die Systemdatensammlungssätze bereitgestellt, die während des Setups installiert werden. Dazu gehören die folgenden Berichte:  
  
-   Zusammenfassung der Datenträgerverwendung  
  
-   Abfragestatistik - Verlauf  
  
-   Serveraktivität - Verlauf  
  
 Mit dieser Prozedur wird der Bericht für den Sammlungssatz **Datenträgerverwendung** angezeigt. Sie können den gleichen allgemeinen Schritten folgen, um die Berichte für die anderen Systemdaten-Sammlungssätze anzuzeigen.  
  
### <a name="to-view-a-collection-set-report"></a>So zeigen Sie einen Sammlungssatzbericht an  
  
1.  Die Tabellen für einen Bericht werden beim ersten Hochladen der gesammelten Daten erstellt. Wenn Sie versuchen, einen Bericht vor diesem ersten Upload anzuzeigen, tritt ein Fehler auf, und es wird kein Bericht angezeigt. Um Daten für den Sammlungssatz „Datenträgerverwendung“ hochzuladen, erweitern Sie im Objekt-Explorer nacheinander den Ordner **Verwaltung** , **Datensammlung**sowie **Systemdaten-Sammlungssätze**, klicken Sie mit der rechten Maustaste auf den Sammlungssatz **Datenträgerverwendung** , und klicken Sie dann auf **Sammeln und jetzt hochladen**.  
  
2.  Um den Bericht anzuzeigen, erweitern Sie im Objekt-Explorer den Ordner **Verwaltung** , klicken Sie mit der rechten Maustaste auf **Datensammlung**, zeigen Sie auf **Berichte**und dann auf **Verwaltungs-Data Warehouse**, und klicken Sie auf **Zusammenfassung der Datenträgerverwendung**.  
  
    > [!NOTE]  
    >  Einige Berichte könnten eine Kalenderschaltfläche unter der Datensammlungszeitachse anzeigen. Klicken Sie auf diese Schaltfläche, um auf den **Kalender für Datensammlungsberichte**zuzugreifen.  
  
#### <a name="data-collection-report-calendar"></a>Kalender für Datensammlungsberichte  
 Verwenden Sie dieses Dialogfeld, um das Startdatum, die Startzeit und die Dauer der Daten anzugeben, über die ein Bericht erstellt werden soll. Sie können z. B. einen Bericht über die Datenträgerverwendung eines Servers für einen bestimmten 12-Stunden-Zeitraum am letzten Mittwoch erstellen.  
  
 **Startdatum**  
 Geben Sie ein Anfangsdatum für die Berichtsdaten ein, oder wählen Sie ein Datum aus dem Kalender aus.  
  
 **Startzeit**  
 Geben Sie eine Anfangszeit für die Berichtsdaten ein, oder wählen Sie ein Datum durch Klicken auf die Pfeile aus.  
  
 **Duration**  
 Geben Sie den Zeitraum an, der in den Bericht aufgenommen werden soll. Der Standardwert ist 240 Minuten. Die möglichen Auswahlwerte sind 15 Minuten, 60 Minuten, 240 Minuten(4 Stunden), 720 Minuten (12 Stunden) und 1440 Minuten (24 Stunden).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datensammlung](data-collection.md)   
 [Benutzerdefinierte Berichte in Management Studio](../../ssms/object/custom-reports-in-management-studio.md)   
 [Konfigurieren des Verwaltungs-Data Warehouses &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
