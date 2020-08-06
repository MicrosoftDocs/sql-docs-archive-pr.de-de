---
title: Sicherungs Verschlüsselungsschlüssel (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d82a9b594e4a7ef7ceeb6737932e7e42a7f6fb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617527"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a>Sichern von Verschlüsselungsschlüsseln (einheitlicher SSRS-Modus)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet einen Verschlüsselungsschlüssel, um sensible Daten zu sichern, die in der Berichtsserver-Datenbank gespeichert werden. Mit dem gesicherten Verschlüsselungsschlüssel wird der Zugriff auf verschlüsselte Verbindungszeichenfolgen und Anmeldeinformationen sichergestellt. Sie müssen über eine Sicherungskopie dieses Schlüssels verfügen, wenn Sie die Berichtsserver-Datenbank auf einen anderen Computer verschieben möchten oder wenn Sie den Benutzernamen oder das Kennwort für das Berichtsserver-Dienstkonto ändern möchten. Beide Vorgänge erfordern eine Wiederherstellung des Schlüssels anhand einer zuvor erstellten Sicherungskopie.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.  
  
 Klicken Sie im Navigationsbereich des **-Konfigurations-Managers auf** Verschlüsselungsschlüssel [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und anschließend auf **Sichern**, um das Dialogfeld Sicherungsverschlüsselungsschlüssel zu öffnen. Dieses Dialogfeld wird auch angezeigt, wenn Sie das Dienstkonto auf der Dienstkontoseite im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager aktualisieren. Weitere Informationen zum [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager finden Sie unter [Konfigurations-Manager für Reporting Services &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Datei Speicherort**  
 Geben Sie einen Dateinamen sowie einen Speicherort für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für den symmetrischen Schlüssel an. Der symmetrische Schlüssel wird nie als Nur-Text-Datei gespeichert. Sie müssen ein Kennwort eingeben, um die Datei zu schützen.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, das die Datei vor nicht autorisiertem Zugriff schützt. Benutzer, denen das Kennwort nicht bekannt ist, können den in der Datei enthaltenen Schlüssel nicht wiederherstellen. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet eine Richtlinie für sichere Kennwörter. Kennwörter müssen aus mindestens 8 Zeichen bestehen und eine Kombination aus Buchstaben (in Groß- und Kleinschreibung) sowie Zahlen und mindestens ein Symbol enthalten.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort erneut ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Verschlüsselungsschlüssel &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
