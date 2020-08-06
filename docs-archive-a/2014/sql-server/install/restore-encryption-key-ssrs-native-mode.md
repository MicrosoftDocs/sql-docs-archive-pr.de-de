---
title: Wiederherstellen des Verschlüsselungsschlüssels (einheitlicher SSRS-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.restoreencryptionkey.F1
ms.assetid: 11ce51e5-f5d4-40b6-88d8-9360fb50e66c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3047e81b3f79219064f81a3492afe6460e1e4966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608231"
---
# <a name="restore-encryption-key-ssrs-native-mode"></a>Wiederherstellen von Verschlüsselungsschlüsseln (einheitlicher SSRS-Modus)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet einen Verschlüsselungsschlüssel, um sensible Daten zu sichern, die in der Berichtsserver-Datenbank gespeichert werden. Um einen ununterbrochenen Zugriff auf verschlüsselte Daten sicherzustellen, ist es wichtig, eine Sicherung des Verschlüsselungsschlüssels vorzunehmen für den Fall, dass Sie diesen später aufgrund von Änderungen im Dienstkonto oder im Rahmen einer geplanten Migration wiederherstellen müssen. Dieses Thema bietet eine Übersicht darüber, wie mithilfe des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Managers Schlüssel wiederhergestellt werden können.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.  
  
 Zum Wiederherstellen des Schlüssels müssen Sie zuvor eine Sicherungskopie des Schlüssels in eine kennwortgeschützte Datei gespeichert haben. Während der Wiederherstellung des Schlüssels ersetzt der Berichtsserver einen vorhandenen Schlüssel durch den Schlüssel in der kennwortgeschützten Datei. Der in dieser Datei gespeicherte Schlüssel muss mit dem Schlüssel identisch sein, der zum Entschlüsseln und Verschlüsseln von Daten verwendet wird.  
  
 Um zu überprüfen, ob Sie einen gültigen Schlüssel wiederhergestellt haben, zeigen Sie im Berichts-Manager Abonnements oder Berichte mit einer Datenquelle an, die gespeicherte Anmeldeinformationen verwendet. Wenn beim Öffnen einer Abonnementdefinitionsseite der Fehler "Der Berichtsserver kann nicht auf verschlüsselte Daten zugreifen" angezeigt wird, oder wenn Sie beim Öffnen eines Berichts, der zuvor gespeicherte Anmeldeinformationen für die Berichtsdatenquelle verwendet hat, zur Eingabe der Anmeldeinformationen aufgefordert werden, haben Sie einen ungültigen Schlüssel wiederhergestellt.  
  
 Wenn Sie einen ungültigen Schlüssel wiederherstellen, der sich von dem Schlüssel zum Verschlüsseln von Daten unterscheidet, können momentan in der Berichtsserver-Datenbank gespeicherte Daten nicht entschlüsselt werden. Falls Sie einen ungültigen Schlüssel wiederherstellen, sollten Sie unverzüglich eine Sicherungskopie des richtigen Schlüssels wiederherstellen, sofern verfügbar. Wenn Sie keine Sicherungskopie des Schlüssels, mit dem die Daten verschlüsselt wurden, vorliegen haben, müssen Sie alle verschlüsselten Daten löschen. Klicken Sie auf der Seite **Verschlüsselungsschlüssel** auf die Schaltfläche [Löschen](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md) , um diesen Schritt auszuführen. Nach dem Löschen des verschlüsselten Inhalts müssen Sie alle Abonnements manuell aktualisieren und alle gespeicherten Anmeldeinformationen, die für Berichte und datengesteuerte Abonnements auf dem Berichtsserver definiert wurden, erneut festlegen.  
  
## <a name="restore-encryption-key-dialog"></a>Verschlüsselungsschlüssel wiederherstellen (Dialogfeld)  
 Informationen dazu, wo Sie die Configuration Manager finden, finden Sie unter [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [Konfigurations-Manager für Reporting Services &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Klicken Sie im Navigationsbereich des **-Konfigurations-Managers auf** Verschlüsselungsschlüssel [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und anschließend auf **Wiederherstellen**, um das Dialogfeld Verschlüsselungsschlüssel wiederherstellen zu öffnen. Dieses Dialogfeld wird auch angezeigt, wenn Sie das Dienstkonto auf der Dienstkontoseite im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager aktualisieren. Weitere Informationen zu  
  
## <a name="options"></a>Tastatur  
 **Datei Speicherort**  
 Wählen Sie die kennwortgeschützte Datei aus, die eine Kopie des symmetrischen Schlüssels enthält. Standardmäßig wird die Dateinamenerweiterung SNK verwendet.  
  
 **Kennwort**  
 Geben Sie das Kennwort zum Entsperren der Datei ein. Nur für Benutzer, die wissen, dass das Kennwort den Schlüssel wiederherstellen kann. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet eine Richtlinie für sichere Kennwörter. Kennwörter müssen aus mindestens 8 Zeichen bestehen und eine Kombination aus Buchstaben (in Groß- und Kleinschreibung) sowie Zahlen und mindestens ein Symbol enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurations-Manager für Reporting Services F1-Hilfe Themen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Löschen und erneutes Erstellen von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [SSRS-Verschlüsselungsschlüssel: Speichern verschlüsselter Berichtsserverdaten](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Verschlüsselungsschlüssel &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
