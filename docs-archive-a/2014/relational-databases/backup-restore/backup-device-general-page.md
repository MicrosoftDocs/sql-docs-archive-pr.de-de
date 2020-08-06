---
title: Sicherungsmedium (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609274"
---
# <a name="backup-device-general-page"></a>Sicherungsmedium (Seite Allgemein)
  Auf der Seite **Allgemein** können Sie die allgemeinen Eigenschaften eines logischen Sicherungsmediums angeben oder anzeigen.  
  
 **So verwenden Sie SQL Server Management Studio zum Anzeigen des Inhalts eines Sicherungsmediums**  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Tastatur  
 **Mediumname**  
 Hier können Sie den Namen eines vorhandenen logischen Sicherungsmediums anzeigen oder den Namen eines neuen logischen Sicherungsmediums angeben.  
  
 **Band**  
 In der Liste **Band** können Sie das Zielbandmedium anzeigen oder auswählen. Diese Option ist nur verfügbar, wenn ein Bandlaufwerk mit dem Computer verbunden ist, auf dem die Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ausgeführt wird.  
  
> [!NOTE]  
>  Bandsicherungsmedien auf Remotecomputern sind keine gültigen Sicherungsziele.  
  
 **File**  
 Hier können Sie die Zieldatei eines vorhandenen logischen Sicherungsmediums anzeigen oder eine Zieldatei für ein neues logisches Sicherungsmedium angeben.  
  
-   Für ein vorhandenes logisches Sicherungsmedium wird der Pfad der Sicherungsdatei angezeigt. Das Feld **Datei** ist nicht bearbeitbar, und die Schaltfläche zum Durchsuchen ist nicht verfügbar.  
  
-   Für ein neues logisches Sicherungsmedium müssen Sie den Pfad der Sicherungsdatei angeben, für die Sie das logische Sicherungsmedium definieren. Die Datei muss noch nicht vorhanden sein.  
  
     Sie können auf die Schaltfläche zum Durchsuchen rechts vom Textfeld **Datei** klicken, um eine lokale Sicherungsdatei anzugeben. Anschließend können Sie im Dialogfeld **Datenbankdateien suchen** zu jedem Ort auf jedem festen Laufwerk auf dem Computer navigieren, auf dem die Serverinstanz ausgeführt wird. Wenn die Sicherungsdatei noch nicht vorhanden ist, müssen Sie den gewünschten Dateinamen im Feld **Dateiname** dieses Dialogfelds eingeben.  
  
     Alternativ können Sie das Feld **Datei** manuell bearbeiten, um den Standardpfad, den Standarddateinamen und die Standarderweiterung zu überschreiben. Zum Angeben einer Remotedatei als Sicherungsziel geben Sie ihren vollqualifizierten UNC-Namen (Universal Naming Convention) ein. Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.  
  
    > [!IMPORTANT]  
    >  Beim Sichern von Daten über ein Netzwerk können Netzwerkfehler auftreten. Aus diesem Grund wird empfohlen, dass Sie den Sicherungsvorgang nach der Fertigstellung überprüfen. Weitere Informationen finden Sie unter [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).  
  
## <a name="remarks"></a>Bemerkungen  
 Die Sicherungen auf einem Satz von einem oder mehreren Sicherungsmedien bilden einen einzelnen Mediensatz. Ein *Mediensatz* ist eine geordnete Auflistung von Sicherungsmedien, Bändern oder Dateien auf Datenträgern, die in mindestens einem Sicherungsvorgang mithilfe eines festen Typs sowie einer festen Anzahl von Sicherungsmedien beschrieben wurden. Informationen über Mediensätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)ausgeführt wird.  
  
 Das einem logischen Sicherungsmedium entsprechende physische Sicherungsmedium wird initialisiert, wenn die erste Sicherung im Mediensatz auf das logische Sicherungsmedium geschrieben wird. Wenn das physische Sicherungsmedium eine noch nicht vorhandene Datei ist, wird sie jetzt erstellt.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Angeben eines Datenträgers oder ein Bands als Sicherungsziel &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Löschen eines Sicherungsmediums &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
-   [Festlegen des Ablaufdatums für eine Sicherung &#40;SQL Server&#41;](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Anzeigen der Inhalte eines Sicherungsbands oder einer -datei &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Anzeigen der Daten und Protokolldateien in einem Sicherungssatz &#40;SQL Server&#41;](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Anzeigen der Eigenschaften und des Inhalts eines logischen Sicherungsmediums &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Wiederherstellung einer Sicherung von einem Medium &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
