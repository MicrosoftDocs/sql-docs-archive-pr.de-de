---
title: Eigenschaften des Verfügbarkeitsreplikats (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 313314baf009cdfb6109e63e9b65e369ac314f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725006"
---
# <a name="availability-replica-properties-general-page"></a>Eigenschaften des Verfügbarkeitsreplikats (Seite Allgemein)
  Verwenden Sie dieses Dialogfeld, um die Eigenschaften eines Verfügbarkeitsreplikats anzuzeigen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So zeigen Sie Verfügbarkeitsreplikateigenschaften an**  
  
-   [Anzeigen von Verfügbarkeitsreplikateigenschaften &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
-   [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
 **Name der Verfügbarkeitsgruppe**  
 Der Name der Verfügbarkeitsgruppe. Dies ist ein vom Benutzer angegebener Name, der innerhalb des Windows Server-Failoverclusters (WSFC) eindeutig sein muss.  
  
 **Serverinstanz**  
 Entspricht dem Servernamen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz, die dieses Replikat hostet, sowie bei einer nicht standardmäßigen Instanz dem Instanznamen.  
  
 **Rolle**  
 **Primärer Server/verwaltete Instanz**  
 Derzeit das primäre Replikat.  
  
 **Sekundärer Server/verwaltete Instanz**  
 Derzeit ein sekundäres Replikat.  
  
 **Wird aufgelöst**  
 Die Replikatrolle wird derzeit zur primären oder sekundären Rolle aufgelöst.  
  
 **Verfügbarkeitsmodus**  
 Der Verfügbarkeitsmodus des Replikats. Folgende Werte sind möglich:  
  
 **Asynchroner Commit**  
 Das primäre Replikat kann einen Commit für Transaktionen ausführen, ohne das Schreiben des Protokolls auf den Datenträger durch das sekundäre Replikat abzuwarten.  
  
 **Synchroner Commit**  
 Das primäre Replikat wartet mit dem Ausführen des Commits für eine bestimmte Transaktion, bis das sekundäre Replikat die Transaktion auf den Datenträger geschrieben hat.  
  
 Weitere Informationen finden Sie unter [Verfügbarkeits Modi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md).  
  
 **Failover mode**  
 Der Failovermodus des Replikats. Folgende Werte sind möglich:  
  
 **Automatisch**  
 Automatisches Failover. Das Replikat ist ein Ziel für automatische Failover. Diese Option wird nur unterstützt, wenn der Verfügbarkeitsmodus auf synchrone Commits festgelegt wird.  
  
 **Manuell**  
 Manuelles Failover. Ein Failover des Replikats kann nur manuell vom Datenbankadministrator ausgeführt werden.  
  
 **Verbindungen in primärer Rolle**  
 Der unterstützte Clientverbindungstyp, wenn das Replikat die primäre Rolle besitzt.  
  
 **Alle Verbindungen zulassen**  
 Für die Datenbanken im primären Replikat sind alle Verbindungen zugelassen. Dies ist die Standardeinstellung.  
  
 **Verbindungen mit Lese-/Schreibzugriff zulassen**  
 Verbindungen, bei denen die Verbindungseigenschaft für den Anwendungszweck auf **ReadOnly** festgelegt ist, werden nicht zugelassen. Wenn die Eigenschaft für den Anwendungszweck auf **ReadWrite** festgelegt ist oder keine Verbindungseigenschaft für den Anwendungszweck festgelegt wurde, wird die Verbindung zugelassen.  
  
 **Lesbares sekundäres Replikat**  
 Gibt an, ob ein Verfügbarkeitsreplikat, das die sekundäre Rolle ausführt (also einem sekundären Replikat entspricht), Verbindungen von Clients zulassen kann. Folgende Werte sind möglich:  
  
 **Nein**  
 Es werden keine direkten Verbindungen mit sekundären Datenbanken dieses Replikats zugelassen. Sie sind für den Lesezugriff nicht verfügbar. Dies ist die Standardeinstellung.  
  
 **Nur beabsichtigte Lesevorgänge**  
 Es sind nur direkte, schreibgeschützte Verbindungen mit sekundären Datenbanken dieses Replikats zulässig. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 **Ja**  
 Alle Verbindungen zu sekundären Datenbanken dieses Replikats sind zugelassen, aber nur für Lesezugriff. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 Weitere Informationen finden Sie unter [aktive sekundäre Replikate: lesbare sekundäre Replikate (AlwaysOn-Verfügbarkeitsgruppen)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 **Sitzungstimeout (Sekunden)**  
 Der Timeoutzeitraum in Sekunden. Der Timeoutzeitraum ist die maximale Zeit, die das Replikat für den Empfang einer Meldung von einem anderen Replikat abwartet, bevor die Verbindung zwischen dem primären und sekundären Replikat als fehlerhaft betrachtet wird. Das Sitzungstimeout erkennt, ob sekundäre Replikate mit dem primären Replikat verbunden sind. Bei der Erkennung einer fehlerhaften Verbindung mit einem sekundären Replikat betrachtet das primäre Replikat das sekundäre Replikat als nicht synchronisiert und weist diesem den Wert NOT_SYNCHRONIZED zu. Ein sekundäres Replikat versucht einfach, erneut eine Verbindung herzustellen, wenn eine fehlgeschlagene Verbindung mit dem primären Replikat erkannt wird.  
  
> [!NOTE]  
>  Sitzungstimeouts verursachen keine automatischen Failovers.  
  
 **Endpunkt-URL**  
 Entspricht der Zeichenfolgendarstellung des vom Benutzer angegebenen Datenbankspiegelungs-Endpunkts, der von Verbindungen zwischen primären und sekundären Replikaten für die Datensynchronisierung verwendet wird. Informationen zur Syntax von Endpunkt-URLs finden Sie unter [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
