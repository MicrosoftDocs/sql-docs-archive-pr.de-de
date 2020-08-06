---
title: Datenbank sichern (Seite „Sicherungsoptionen“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ffd527ba4334244c7fd4c5d4a73099093cb8520b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622733"
---
# <a name="back-up-database-backup-options-page"></a>Datenbank sichern (Seite 'Sicherungsoptionen')
  Auf der Seite  **Sicherungsoptionen** des Dialogfelds **Datenbank sichern** können Sie die Optionen zur Sicherung der Datenbank anzeigen und ändern.  
  
 **So erstellen Sie eine Sicherung mithilfe von SQL Server Management Studio**  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  Sie können einen Datenbank-Wartungsplan definieren, um Datenbanksicherungen zu erstellen. Weitere Informationen finden Sie unter [Wartungspläne](../maintenance-plans/maintenance-plans.md) und [Verwenden des Wartungsplanungs-Assistenten](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
> [!NOTE]  
>  Wenn Sie eine Sicherungsaufgabe mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angeben, können Sie das entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) -Skript generieren, indem Sie auf die Schaltfläche **Skript** klicken und anschließend ein Ziel für das Skript auswählen.  
  
## <a name="options"></a>Tastatur  
  
### <a name="backup-set"></a>Sicherungssatz  
 Mit den Optionen des Bereichs **Sicherungssatz** können Sie optionale Informationen zu dem durch den Sicherungsvorgang erstellten Sicherungssatz angeben.  
  
 **Name**  
 Geben Sie den Namen des Sicherungssatzes an. Vom System wird automatisch ein Standardname vorgeschlagen, der auf dem Datenbanknamen und dem Sicherungstyp basiert.  
  
 Informationen über Sicherungssätze finden Sie unter [Mediensätze, Medienfamilien und Sicherungssätze &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Sicherungssatzes ein.  
  
 **Sicherungssatz läuft ab**  
 Wählen Sie eine der folgenden Optionen für den Ablauf. Diese Option ist deaktiviert, wenn **URL** als Sicherungsziel ausgewählt ist.  
  
|||  
|-|-|  
|**Nachher**|Geben Sie die Anzahl von Tagen an, die verstreichen müssen, bevor dieser Sicherungssatz abläuft und überschrieben werden kann. Dieser Wert kann zwischen 0 und 99999 Tagen liegen. Ein Wert von 0 Tagen bedeutet, dass der Sicherungssatz nicht abläuft.<br /><br /> Der Standardwert für den Sicherungsablauf ist der Wert, der in der Option **Standardbeibehaltung für Sicherungsmedien (in Tagen)** festgelegt wurde. Um auf diese Option zuzugreifen, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Servernamen, und wählen Sie **Eigenschaften**aus. Klicken Sie dann im Dialogfeld **Servereigenschaften** auf die Seite **Datenbankeinstellungen** .|  
|**On**|Geben Sie ein bestimmtes Datum an, an dem der Sicherungssatz abläuft und überschrieben werden kann.|  
  
### <a name="compression"></a>Komprimierung  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (oder höher) unterstützt die [Sicherungskomprimierung](backup-compression-sql-server.md).  
  
 **Sicherungskomprimierung festlegen**  
 Wählen Sie in [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (oder höher) einen der folgenden Werte für die Sicherungskomprimierung aus:  
  
|||  
|-|-|  
|**Standardservereinstellungen verwenden**|Klicken Sie hier, um die Standardeinstellung auf Serverebene zu verwenden.<br /><br /> Diese Standardeinstellung wird durch die Serverkonfigurationsoption **Komprimierungsstandard für Sicherung** festgelegt. Informationen zum Anzeigen der aktuellen Einstellung dieser Option finden Sie unter [Anzeigen oder Konfigurieren der Serverkonfigurationsoption „Standardeinstellung für die Sicherungskomprimierung“](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).|  
|**Sicherung komprimieren**|Klicken Sie hier, um die Sicherung unabhängig von der Standardeinstellung auf Serverebene zu komprimieren.<br /><br /> **\*\* Wichtig \*\*** Standardmäßig steigt die CPU-Nutzung durch die Komprimierung erheblich, und die durch die Komprimierung zusätzlich genutzten CPU-Ressourcen können sich negativ auf gleichzeitige Vorgänge auswirken. Daher ist es u. U. sinnvoll, in einer Sitzung, bei der die CPU-Nutzung durch die [Ressourcenkontrolle](../resource-governor/resource-governor.md) eingeschränkt ist, komprimierte Sicherungen mit niedriger Priorität zu erstellen. Weitere Informationen finden Sie unter [Einschränken der CPU-Nutzung durch die Sicherungskomprimierung mithilfe der Ressourcenkontrolle &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).|  
|**Sicherung nicht komprimieren**|Klicken Sie hier, um unabhängig von der Standardeinstellung auf Serverebene eine nicht komprimierte Sicherung zu erstellen.|  
  
### <a name="encryption"></a>Verschlüsselung  
 Um eine verschlüsselte Sicherung zu erstellen, aktivieren Sie das Kontrollkästchen **Sicherung verschlüsseln** . Wählen Sie einen Verschlüsselungsalgorithmus für den Verschlüsselungsschritt aus, und geben Sie ein Zertifikat oder einen asymmetrischen Schlüssel aus der Liste der vorhandenen Zertifikate und asymmetrischen Schlüssel an. Folgende Algorithmen stehen für die Verschlüsselung zur Verfügung:  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
> [!TIP]  
>  Die Verschlüsselungsoption ist deaktiviert, wenn Sie ausgewählt haben, dass die Sicherung an einen vorhandenen Sicherungssatz angefügt werden soll.  
>   
>  Es ist ratsam, das Zertifikat bzw. die Schlüssel zu sichern und an einem anderen Speicherort als dem der verschlüsselten Sicherung zu speichern.  
>   
>  Es werden nur Schlüssel aus der erweiterbaren Schlüsselverwaltung (Extensible Key Management, EKM) unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Sichern des Transaktionsprotokolls bei beschädigter Datenbank &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
