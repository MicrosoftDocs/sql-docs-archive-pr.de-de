---
title: Seite "anfängliche Datensynchronisierung auswählen" (AlwaysOn-Verfügbarkeits Gruppen-Assistenten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724206"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a>Seite 'Anfängliche Datensynchronisierung auswählen' (AlwaysOn-Verfügbarkeitsgruppen-Assistenten)
  Verwenden Sie die AlwaysOn-Seite **Anfängliche Datensynchronisierung auswählen** , um die Einstellung für die anfängliche Datensynchronisierung neuer sekundärer Datenbanken anzugeben. Diese Seite wird von drei Assistenten gemeinsam genutzt – dem [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], dem [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] und dem [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].  
  
 Die möglichen Optionen sind **Vollständig**, **Nur verknüpfen**oder **Anfängliche Datensynchronisierung überspringen**. Stellen Sie vor dem Auswählen von **Vollständig** oder **Nur verknüpfen** sicher, dass die Umgebung die Voraussetzungen erfüllt.  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Halten Sie Protokollsicherungstasks für die primären Datenbanken während der anfänglichen Datensynchronisierung an.  
  
-   Bei großen Datenbanken können die vollständigen Sicherungs- und Wiederherstellungsvorgänge viel Zeit und umfangreiche Ressourcen in Anspruch nehmen. In solchen Fällen wird empfohlen, die sekundären Datenbanken selbst vorzubereiten. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt [So bereiten Sie sekundäre Datenbanken manuell vor](#PrepareSecondaryDbs).  
  
-   Bei einer vollständigen anfänglichen Datensynchronisierung mus eine Netzwerkfreigabe angegeben werden. Bevor Sie einen Assistenten verwenden, um die vollständige anfängliche Datensynchronisierung auszuführen, wird empfohlen, dass Sie einen Sicherheitsplan für die Zugriffsberechtigungen auf dem Netzwerkfreigabeordner implementieren. Diese Vorsichtsmaßnahme ist wichtig, da auf potenziell vertrauliche Daten in der Sicherungsdatei von jeder Person zugegriffen werden kann, die über eine READ-Berechtigung für den Ordner verfügt. Außerdem wird zum Schutz der Sicherungs- und Wiederherstellungsvorgänge empfohlen, dass Sie die Netzwerkchannels zwischen jeder Serverinstanz sichern, die ein Verfügbarkeitsreplikat und den Netzwerkfreigabeordner hostet.  
  
     Wenn die Sicherungs- und Wiederherstellungsvorgänge besondert gesichert sein müssen, wird empfohlen, dass Sie die Option **Nur verknüpfen** oder **Anfängliche Datensynchronisierung überspringen** aktivieren.  
  
##  <a name="full"></a><a name="Full"></a>Voll  
 Für jede primäre Datenbank werden mit der Option **Vollständig** mehrere Vorgänge in einem Workflow ausgeführt: Erstellen einer vollständigen und Protokollsicherung der primären Datenbank, Erstellen der entsprechenden sekundären Datenbanken durch Wiederherstellen dieser Sicherungen auf jeder Serverinstanz, die ein sekundäres Replikat hostet, und Verknüpfen jeder sekundären Datenbank mit der Verfügbarkeitsgruppe.  
  
 Aktivieren Sie diese Option nur, wenn die Umgebung die folgenden Voraussetzungen zum Verwenden der vollständigen anfänglichen Datensynchronisierung erfüllt und der Assistent die Datensynchronisierung automatisch starten soll.  
  
 **Voraussetzungen für die Verwendung der vollständigen anfänglichen Datensynchronisierung**  
  
-   Alle Datenbankdateipfade müssen auf allen Serverinstanzen, die ein Replikat für die neue Verfügbarkeitsgruppe hosten, identisch sein.  
  
    > [!NOTE]  
    >  Wenn sich die Sicherungs- und Wiederherstellungsdateipfade auf der Serverinstanz, auf der Sie den Assistenten ausführen, und einer beliebigen Serverinstanz unterscheiden, auf der ein sekundäres Replikat gehostet werden soll. Die Sicherungs- und Wiederherstellungsvorgänge müssen manuell mit der WITH MOVE-Option ausgeführt werden. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt [So bereiten Sie sekundäre Datenbanken manuell vor](#PrepareSecondaryDbs).  
  
-   Primäre Datenbanknamen können nicht auf Serverinstanzen vorhanden sein, die ein sekundäres Replikat hosten. Daher kann noch keine der neuen sekundären Datenbanken vorhanden sein.  
  
-   Sie müssen eine Netzwerkfreigabe angeben, damit der Assistent Sicherungen erstellen und auf Sicherungen zugreifen kann. Für das primäre Replikat kann das zum Starten von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] verwendete Konto über Lese- und Schreibberechtigungen für das Dateisystem in einer Netzwerkfreigabe verfügen. Bei sekundären Replikaten muss das Konto über eine Leseberechtigung für die Netzwerkfreigabe verfügen.  
  
    > [!IMPORTANT]  
    >  Die Protokollsicherungen sind Teil der Protokollsicherungskette. Speichern Sie die Protokollsicherungsdateien ordnungsgemäß.  
  
 **Wenn die Voraussetzungen nicht erfüllt sind**  
  
 Der Assistent kann die sekundären Datenbanken für diese Verfügbarkeitsgruppe nicht erstellen. Weitere Informationen zu deren Vorbereitung finden Sie weiter unten in diesem Thema im Abschnitt [So bereiten Sie sekundäre Datenbanken manuell vor](#PrepareSecondaryDbs).  
  
 **Wenn die Voraussetzungen erfüllt sind**  
  
 Wenn alle genannten Voraussetzungen erfüllt sind und der Assistent die vollständige anfängliche Datensynchronisierung ausführen soll, aktivieren Sie die Option **Vollständig** , und geben Sie eine Netzwerkfreigabe an. Dadurch werden vom Assistenten vollständige Datenbank- und Protokollsicherungen jeder ausgewählten Datenbank erstellt und diese Sicherungen in der von Ihnen angegebenen Netzwerkfreigabe abgelegt. Danach erstellt der Assistent auf jeder Serverinstanz, die eines der neuen sekundären Replikate hostet, die sekundären Datenbanken durch Wiederherstellen von Sicherungen mit RESTORE WITH NORECOVERY. Der Assistent verknüpft nach dem Erstellen aller sekundären Datenbanken die neue sekundäre Datenbank mit der Verfügbarkeitsgruppe. Sobald eine sekundäre Datenbank verknüpft ist, werden die Datensynchronisierungen für diese Datenbank gestartet.  
  
 **Freigegebenen Netzwerkspeicherort angeben, auf den von allen Replikaten zugegriffen werden kann**  
 Um Sicherungen zu erstellen und wiederherzustellen, werden Sie vom Assistenten aufgefordert, eine Netzwerkfreigabe anzugeben. Das zum Starten von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat hostet, verwendete Konto muss über Lese- und Schreibberechtigungen für das Dateisystem auf der Netzwerkfreigabe verfügen.  
  
> [!IMPORTANT]  
>  Die Protokollsicherungen sind Teil der Protokollsicherungskette. Speichern Sie ihre Sicherungsdateien ordnungsgemäß.  
  
##  <a name="join-only"></a><a name="Joinonly"></a>Nur beitreten  
 Aktivieren Sie diese Option nur, wenn die neuen sekundären Datenbanken bereits auf jeder Serverinstanz vorhanden sind, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet. Informationen zum Vorbereiten von sekundären Datenbanken finden Sie weiter unten in diesem Abschnitt unter [So bereiten Sie sekundäre Datenbanken manuell vor](#PrepareSecondaryDbs).  
  
 Wenn Sie **Nur verknüpfen**auswählen, versucht der Assistent, jede vorhandene sekundäre Datenbank mit der Verfügbarkeitsgruppe zu verknüpfen.  
  
## <a name="skip-initial-data-synchronization"></a>Anfängliche Datensynchronisierung überspringen  
 Aktivieren Sie diese Option, wenn Sie eigene Datenbank- und Protokollsicherungen für jede primäre Datenbank ausführen und diese auf jeder Serverinstanz, die ein sekundäres Verfügbarkeitsreplikat hostet, wiederherstellen möchten. Nach dem Beenden des Assistenten müssen Sie jede sekundäre Datenbank auf jedem sekundären Replikat verknüpfen.  
  
> [!NOTE]  
>  Weitere Informationen finden Sie unter [Starten der Datenverschiebung auf einer sekundären AlwaysOn-Datenbank &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a>So bereiten Sie sekundäre Datenbanken manuell vor  
 Sie können sekundäre Datenbanken unabhängig von einem [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Assistenten mit einer der beiden folgenden Methoden vorbereiten:  
  
-   Stellen Sie manuell mit RESTORE WITH NORECOVERY eine aktuelle Datenbanksicherung der primären Datenbank wieder her, und stellen Sie dann jede nachfolgende Protokollsicherung mit RESTORE WITH NORECOVERY wieder her. Wenn die primären und sekundären Datenbanken unterschiedliche Dateipfade aufweisen, müssen Sie die WITH MOVE-Option verwenden. Führen Sie diese Wiederherstellungssequenz auf jeder Serverinstanz aus, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet.  Sie können diese Sicherungs- und Wiederherstellungsvorgänge mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder PowerShell ausführen.  
  
     **Weitere Informationen finden Sie unter:**  
  
     [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   Wenn Sie einer Verfügbarkeitsgruppe eine oder mehrere primäre Datenbanken für den Protokollversand hinzufügen, können Sie möglicherweise eine oder mehrere der entsprechenden sekundären Datenbanken aus dem Protokollversand nach [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]migrieren. Weitere Informationen finden Sie unter [Voraussetzungen für das Migrieren vom Protokoll Versand zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).  
  
    > [!NOTE]  
    >  Nachdem Sie alle sekundären Datenbanken für die Verfügbarkeitsgruppe erstellt haben, sofern Sie Sicherungen auf sekundären Replikaten ausführen möchten, müssen Sie die Voreinstellung zur automatisierten Sicherung der Verfügbarkeitsgruppe neu konfigurieren.  
  
     **Weitere Informationen finden Sie unter:**  
  
     [Voraussetzungen für das Migrieren vom Protokoll Versand zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 Wenden Sie nach dem Erstellen einer sekundären Datenbank alle aktuellen Protokollsicherungen auf die neue sekundäre Datenbank an.  
  
 Sie können auch alle sekundären Datenbanken vorbereiten, bevor Sie den Assistenten ausführen. Anschließend wählen Sie auf der Seite **Anfängliche Datensynchronisierung angeben** des Assistenten die Option **Nur verknüpfen** aus, damit der Assistent versucht, die neuen sekundären Datenbanken automatisch mit der Verfügbarkeitsgruppe zu verknüpfen.  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> Verwandte Aufgaben  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
-   [Verwenden des Assistenten für Failover-Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Starten Sie die Daten Verschiebung auf einer sekundären AlwaysOn-Datenbank &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
