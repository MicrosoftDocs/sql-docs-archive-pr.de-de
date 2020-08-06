---
title: Verschlüsseln der Sicherung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6a78ae4969982fbfe5295ee4219855f48ac60793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727018"
---
# <a name="backup-encryption"></a>Verschlüsseln der Sicherung
  Dieses Thema bietet eine Übersicht über die Verschlüsselungsoptionen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherungen. Es enthält Details zur Verwendung, zu den Vorteilen und empfohlenen Vorgehensweisen beim Verschlüsseln bei der Sicherung.  
  
  
##  <a name="overview"></a><a name="Overview"></a> Übersicht  
 Ab [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]verfügt SQL Server über die Möglichkeit, die Daten beim Erstellen einer Sicherung zu verschlüsseln. Durch das Angeben des Verschlüsselungsalgorithmus und der Verschlüsselung (ein Zertifikat oder ein asymmetrischer Schlüssel) beim Erstellen einer Sicherung können Sie eine verschlüsselte Sicherungsdatei anlegen. Alle Speicherziele − lokaler und Windows Azure-Speicher − werden unterstützt. Außerdem können Verschlüsselungsoptionen für [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] -Vorgänge konfiguriert werden. Dies ist eine neue Funktion, die in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]eingeführt wurde.  
  
 Um während der Sicherung eine Verschlüsselung durchzuführen, müssen Sie einen Verschlüsselungsalgorithmus und eine Verschlüsselungsmethode angeben, um den Verschlüsselungsschlüssel zu sichern. Folgende Verschlüsselungsoptionen werden unterstützt:  
  
-   **Verschlüsselungsalgorithmus:** Die folgenden Verschlüsselungsalgorithmen werden unterstützt: AES 128, AES 192, AES 256 und Triple DES  
  
-   **Verschlüsselung:** Ein Zertifikat oder asymmetrischer Schlüssel  
  
> [!CAUTION]  
>  Es ist sehr wichtig, das Zertifikat oder den asymmetrischen Schlüssel zu sichern – vorzugsweise an einem anderen Speicherort als die Sicherungsdatei, die zum Verschlüsseln verwendet wurde. Ohne das Zertifikat oder den asymmetrischen Schlüssel können Sie keine Sicherung wiederherstellen, sodass die Sicherungsdatei unbrauchbar ist.  
  
 **Wiederherstellen der verschlüsselten Sicherung:** Die SQL Server-Wiederherstellung erfordert keine Angabe von Verschlüsselungsparametern während der Wiederherstellung. Sie setzt aber voraus, dass das Zertifikat oder der asymmetrische Schlüssel, die zum Verschlüsseln der Sicherungsdatei verwendet werden, in der Instanz verfügbar ist, auf der Sie die Wiederherstellung ausführen. Das Benutzerkonto, unter dem die Wiederherstellung ausgeführt wird, muss über `VIEW DEFINITION`-Berechtigungen für das Zertifikat oder den Schlüssel verfügen. Wenn Sie die verschlüsselte Sicherung in einer anderen Instanz wiederherstellen, müssen Sie sicherstellen, dass das Zertifikat für diese Instanz verfügbar ist.  
  
 Wenn Sie eine Sicherung von einer TDE-verschlüsselten Datenbank wiederherstellen, sollte das TDE-Zertifikat auf der Instanz verfügbar sein, auf der die Wiederherstellung erfolgen soll.  
  
##  <a name="benefits"></a><a name="Benefits"></a> Vorteile  
  
1.  Das Verschlüsseln der Datenbanksicherungen trägt zum Schutz der Daten bei: SQL Server bietet die Option, die Sicherungsdaten beim Erstellen einer Sicherung zu verschlüsseln.  
  
2.  Verschlüsselung kann auch für Datenbanken verwendet werden, die mithilfe von TDE verschlüsselt werden.  
  
3.  Die Verschlüsselung wird für Sicherungen unterstützt, die von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]durchgeführt werden, was zusätzliche Sicherheit für externe Sicherungen bereitstellt.  
  
4.  Diese Funktion unterstützt mehrere Verschlüsselungsalgorithmen bis zu AES 256 Bit. So können Sie einen Algorithmus auswählen, der Ihren Anforderungen entspricht.  
  
5.  Sie können Verschlüsselungsschlüssel in EKM-Anbieter (Extended Key Management) integrieren.  
  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Voraussetzungen zum Verschlüsseln einer Sicherung:  
  
1.  **Erstellen eines Datenbankhauptschlüssels für die Masterdatenbank:** Der Datenbank-Hauptschlüssel ist ein symmetrischer Schlüssel, der zum Schützen von privaten Schlüsseln der in der Datenbank vorhandenen Zertifikate und asymmetrischen Schlüssel verwendet wird. Weitere Informationen finden Sie unter [Verschlüsselungsschlüssel für SQL Server und Datenbank &#40;Datenbank-Engine&#41;](../security/encryption/sql-server-and-database-encryption-keys-database-engine.md).  
  
2.  Erstellen Sie ein Zertifikat oder einen asymmetrischen Schlüssel, der für die Sicherungsverschlüsselung verwendet wird. Weitere Informationen zum Erstellen eines Zertifikats finden Sie unter [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql). Weitere Informationen zum Erstellen eines asymmetrischen Schlüssels finden Sie unter [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).  
  
    > [!IMPORTANT]  
    >  Nur asymmetrische Schlüssel, die sich in einer erweiterten Schlüsselverwaltung (Extended Key Management, EKM) befinden, werden unterstützt.  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Folgende Einschränkungen gelten für die Verschlüsselungsoptionen:  
  
-   Wenn Sie einen asymmetrischen Schlüssel verwenden, um die Sicherungsdaten zu verschlüsseln, werden nur asymmetrische Schlüssel, die sich im EKM-Anbieter befinden, unterstützt.  
  
-   SQL Server Express und SQL Server Web unterstützen keine Verschlüsselung während der Sicherung. Das Wiederherstellen von einer verschlüsselten Sicherung in eine SQL Server Express- oder SQL Server Web-Instanz wird allerdings unterstützt.  
  
-   Frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können verschlüsselte Sicherungen nicht lesen.  
  
-   Das Anfügen an einen vorhandenen Sicherungssatz wird für verschlüsselte Sicherungen nicht unterstützt.  
  
  
##  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 **So verschlüsseln Sie eine Sicherung oder stellen Daten aus einer verschlüsselten Sicherung wieder her:**  
  
 `VIEW DEFINITION`-Berechtigung für das Zertifikat oder den asymmetrischen Schlüssel, der verwendet wird, um die Datenbanksicherung zu verschlüsseln.  
  
> [!NOTE]  
>  Der Zugriff auf das TDE-Zertifikat ist nicht erforderlich, um eine durch TDE geschützte Datenbank zu sichern oder wiederherzustellen.  
  
##  <a name="backup-encryption-methods"></a><a name="Methods"></a> Methoden zur Sicherungsverschlüsselung  
 Die folgenden Abschnitte enthalten eine kurze Einführung in die Schritte zum Verschlüsseln der Daten während der Sicherung. Eine vollständige exemplarische Vorgehensweise der einzelnen Schritte, die Sie beim Verschlüsseln der Sicherung mithilfe von Transact-SQL ausführen, finden Sie unter [Erstellen einer verschlüsselten Sicherung](create-an-encrypted-backup.md).  
  
### <a name="using-sql-server-management-studio"></a>Verwendung von SQL Server Management Studio  
 Sie können eine Sicherung verschlüsseln, wenn Sie die Datenbanksicherung in einem der folgenden Dialogfelder erstellen:  
  
1.  [Datenbank sichern &#40;Seite 'Sicherungsoptionen'&#41;](back-up-database-backup-options-page.md) – Auf der Seite **Sicherungsoptionen** können Sie **Verschlüsselung** auswählen und den Verschlüsselungsalgorithmus und das Zertifikat oder den asymmetrischen Schlüssel angeben, der für die Verschlüsselung verwendet werden soll.  
  
2.  [Verwendung des Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) – Wenn Sie einen Sicherungstask auswählen, können Sie auf der Registerkarte **Optionen** der Seite **Define Backup ()Task** (Sicherungstask () definieren) die Option **Sicherungsverschlüsselung**auswählen und den Verschlüsselungsalgorithmus und das Zertifikat oder den Schlüssel angeben, das bzw. der für die Verschlüsselung verwendet werden soll.  
  
### <a name="using-transact-sql"></a>Transact-SQL  
 Es folgt eine Transact-SQL-Beispielanweisung zum Verschlüsseln der Sicherungsdatei:  
  
```sql
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO
```  
  
 Die vollständige Syntax der Transact-SQL-Anweisung finden Sie unter [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="using-powershell"></a>PowerShell  
 In diesem Beispiel werden die Verschlüsselungsoptionen erstellt und als Parameterwert im Cmdlet **Backup-SqlDatabase** verwendet, um eine verschlüsselte Sicherung zu erstellen.  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  
Backup-SqlDatabase -ServerInstance . -Database "MyTestDB" -BackupFile "MyTestDB.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="recommended-practices"></a><a name="RecommendedPractices"></a> Empfohlene Vorgehensweisen  
 Erstellen Sie eine Sicherung des Verschlüsselungszertifikats und der Schlüssel an einem anderen Speicherort als dem lokalen Computer, auf dem die Instanz installiert ist. Zur Wiederherstellung in Notfallszenarien sollten Sie eine Sicherung des Zertifikats oder des Schlüssels an einem anderen Ort aufbewahren. Sie können eine verschlüsselte Sicherung nicht ohne das Zertifikat wiederherstellen, das verwendet wird, um die Sicherung zu verschlüsseln.  
  
 Zur Wiederherstellung einer verschlüsselten Sicherung sollte das ursprüngliche Zertifikat, das beim Erstellen der Sicherung mit übereinstimmendem Fingerabdruck verwendet wurde, auf der Instanz verfügbar sein, auf der die Wiederherstellung erfolgt. Deshalb sollte das Zertifikat beim Ablauf nicht verlängert oder geändert werden. Die Verlängerung kann zum Aktualisieren des Zertifikats führen, was die Änderung des Fingerabdrucks auslöst, sodass das Zertifikat für die Sicherungsdatei ungültig wird. Das Konto, unter dem die Wiederherstellung ausgeführt wird, sollte über die VIEW DEFINITION-Berechtigung für das Zertifikat oder den asymmetrischen Schlüssel verfügen, das bzw. der für die Verschlüsselung während der Sicherung verwendet wird.  
  
 Sicherungen für Datenbanken in Verfügbarkeitsgruppen werden in der Regel auf dem bevorzugten Sicherungsreplikat ausgeführt.  Wenn eine Sicherung auf einem anderen Replikat als dem wiederhergestellt wird, von dem die Sicherung erstellt wurde, stellen Sie sicher, dass das ursprüngliche, für die Sicherung verwendete Zertifikat auf dem Replikat verfügbar ist, auf dem die Wiederherstellung erfolgt.  
  
 Wenn TDE für die Datenbank aktiviert wurde, wählen Sie andere Zertifikate oder asymmetrische Schlüssel zum Verschlüsseln der Datenbank und der Sicherung aus, um die Sicherheit zu erhöhen.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
|Thema/Aufgabe|BESCHREIBUNG|  
|-----------------|-----------------|  
|[Erstellen einer verschlüsselten Sicherung](create-an-encrypted-backup.md)|Beschreibt die grundlegenden Schritte, die erforderlich sind, um eine verschlüsselte Sicherung zu erstellen.|  
|[Verwaltete SQL Server-Sicherung in Azure: Beibehaltungs- und Speichereinstellungen](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)|Beschreibt die grundlegenden Schritte, die erforderlich sind, um [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] mit den angegebenen Verschlüsselungsoptionen zu konfigurieren.|  
|[Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|Enthält ein Beispiel zum Erstellen einer verschlüsselten Sicherung, die durch Schlüssel im Azure-Schlüsseltresor geschützt ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)  
  
  
