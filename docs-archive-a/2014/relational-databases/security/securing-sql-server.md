---
title: Sichern von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- database objects [SQL Server], security
- SQL Server, security
- operating systems [SQL Server], security
- security [SQL Server], planning
- applications [SQL Server], security
ms.assetid: 4d93489e-e9bb-45b3-8354-21f58209965d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b8cb69c88d1f8eee98093c8fc8227db8e67ed7fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697682"
---
# <a name="securing-sql-server"></a>Sichern von SQL Server
  Das Sichern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann als eine Reihe von Schritten betrachtet werden, die vier Bereiche betreffen: die Plattform, die Authentifizierung, die Objekte (einschließlich der Daten) und die Anwendungen, die auf das System zugreifen. In den folgenden Themen werden Sie durch das Erstellen und Implementieren eines effektiven Sicherheitsplans geführt.  
  
 Weitere Informationen zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit finden Sie auf der [SQL Server](https://go.microsoft.com/fwlink/?LinkID=31629) -Website. Dazu gehören ein Handbuch mit empfohlenen Vorgehensweisen sowie eine Sicherheitsprüfliste. Auf der Site finden Sie außerdem die neuesten Informationen und Downloads zu Service Packs.  
  
## <a name="platform-and-network-security"></a>Plattform- und Netzwerksicherheit  
 Die Plattform für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält die physische Hardware und die Netzwerksysteme zum Verbinden von Clients mit den Datenbankservern, sowie binäre Dateien zum Verarbeiten von Datenbankanforderungen.  
  
### <a name="physical-security"></a>Physische Sicherheit  
 Durch die empfohlenen Vorgehensweisen für physische Sicherheit wird der Zugriff auf den physischen Server und Hardwarekomponenten beschränkt. Verwenden Sie beispielsweise abgeschlossene Räume mit eingeschränktem Zugang für die Datenbankserverhardware und für Netzwerkgeräte. Beschränken Sie außerdem den Zugriff auf Sicherungsmedien durch Aufbewahren der Medien an einem sicheren, getrennten Ort.  
  
 Das Implementieren der physischen Netzwerksicherheit beginnt mit dem Fernhalten unbefugter Benutzer vom Netzwerk. Die folgende Tabelle enthält weitere Informationen zu Netzwerksicherheitsinformationen.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] und Netzwerkzugriff auf andere Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|"Konfigurieren und Sichern der Serverumgebung" in der Onlinedokumentation von [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
  
### <a name="operating-system-security"></a>Sicherheit des Betriebssystems  
 Service Packs und Upgrades für Betriebssysteme enthalten wichtige Sicherheitserweiterungen. Wenden Sie alle Updates und Upgrades nach dem Testen mit den Datenbankanwendungen auf das Betriebssystem an.  
  
 Firewalls stellen ebenfalls effektive Möglichkeiten zum Implementieren von Sicherheit zur Verfügung. Eine Firewall trennt oder beschränkt logisch den Netzwerkverkehr und kann zum Verstärken der Datensicherheitsrichtlinie der Organisation konfiguriert werden. Wenn Sie eine Firewall verwenden, wird die Sicherheit auf Betriebssystemebene erhöht, indem ein Punkt zur Verfügung gestellt wird, auf den der Sicherheitsmaßstab ausgerichtet werden kann. Die folgende Tabelle enthält weitere Informationen zum Verwenden einer Firewall mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Konfigurieren einer Firewall für das Funktionieren mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|  
|Konfigurieren einer Firewall für das Funktionieren mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[Konfigurieren einer Windows-Firewall für den Zugriff auf den SSIS-Dienst](../../integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)|  
|Konfigurieren einer Firewall für das Funktionieren mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|  
|Öffnen bestimmter Ports für eine Firewall zum Zulassen des Zugriffs auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|Konfigurieren von Unterstützung für den erweiterten Schutz für die Authentifizierung mit Channelbindung und Dienstbindung|[Herstellen einer Verbindung mit der Datenbank-Engine unter Verwendung von Erweiterter Schutz](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)|  
  
 Die Oberflächenreduzierung stellt eine Sicherheitsmaßnahme dar, die das Beenden oder Deaktivieren nicht verwendeter Komponenten beinhaltet. Mithilfe der Oberflächenreduzierung kann die Sicherheit verbessert werden, da weniger Möglichkeiten für Angriffe auf das System vorhanden sind. Der wichtigste Aspekt beim Beschränken des Oberflächenbereichs von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] liegt im Ausführen erforderlicher Dienste mit "geringsten Rechten" durch ausschließliches Erteilen von entsprechenden Rechten an Dienste und Benutzer. Die folgende Tabelle enthält weitere Informationen zu Diensten und Systemzugriff.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)|  
  
 Wenn Ihr [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -System Internetinformationsdienste (Internet Information Services, IIS) verwendet, sind zusätzliche Schritte zum Sichern der Plattformoberfläche erforderlich. Die folgende Tabelle enthält Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Internetinformationsdiensten.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|IIS-Sicherheit mit [!INCLUDE[ssEW](../../includes/ssew-md.md)]|"IIS-Sicherheit" in der Onlinedokumentation von [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Authentifizierung|[Authentifizierung in Reporting Services](../../reporting-services/extensions/security-extension/authentication-in-reporting-services.md)|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)] und IIS-Zugriff|"Internetinformationsdienste-Sicherheitsflussdiagramm" in der Onlinedokumentation von [!INCLUDE[ssEW](../../includes/ssew-md.md)]|  
  
### <a name="sql-server-operating-system-files-security"></a>SQL Server-Betriebssystemdateisicherheit  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Betriebssystemdateien zum Betrieb und zur Datenspeicherung verwendet. Die empfohlene Vorgehensweise für die Dateisicherheit erfordert, den Zugriff auf diese Dateien zu beschränken. Die folgende Tabelle enthält Informationen zu diesen Dateien.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Programmdateien|[Dateispeicherorte für Standard- und benannte Instanzen von SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Service Packs und Upgrades stellen erweiterte Sicherheit zur Verfügung. Informationen zum Bestimmen des neuesten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbaren Service Packs finden Sie auf der Website von [SQL Server](https://go.microsoft.com/fwlink/?LinkID=31629) .  
  
 Mithilfe des folgenden Skripts können Sie das auf dem System installierte Service Pack bestimmen:  
  
```  
SELECT CONVERT(char(20), SERVERPROPERTY('productlevel'));  
GO  
```  
  
## <a name="principals-and-database-object-security"></a>Prinzipale und Datenbankobjektsicherheit  
 Prinzipale sind die Personen, Gruppen und Prozesse, denen Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erteilt wurde. „Sicherungsfähige Elemente“ sind der Server, die Datenbank und Objekte in der Datenbank. Jedes der Elemente verfügt über einen Berechtigungssatz, der zum Reduzieren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Oberflächenbereichs konfiguriert werden kann. In der folgenden Tabelle sind Informationen zu Prinzipalen und sicherungsfähigen Elementen enthalten.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Benutzer, Rollen und Prozesse von Servern und Datenbanken|[Prinzipale &#40;Datenbank-Engine&#41;](authentication-access/principals-database-engine.md)|  
|Server- und Datenbankobjektsicherheit|[Sicherungsfähige Elemente](securables.md)|  
|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitshierarchie|[Berechtigungshierarchie &#40;Datenbank-Engine&#41;](permissions-hierarchy-database-engine.md)|  
  
### <a name="encryption-and-certificates"></a>Verschlüsselung und Zertifikate  
 Durch Verschlüsselung werden keine Probleme der Zugriffssteuerung gelöst. Sie erhöht jedoch die Sicherheit, indem Datenverluste selbst im seltenen Fall einer überbrückten Zugriffssteuerung beschränkt werden. Wenn der Datenbankhostcomputer beispielsweise falsch konfiguriert wurde und ein böswilliger Benutzer Zugriff auf sensible Daten wie Kreditkartennummern gewinnt, sind die gestohlenen Informationen nutzlos, wenn sie verschlüsselt wurden. Die folgende Tabelle enthält weitere Informationen zur Verschlüsselung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Die Verschlüsselungshierarchie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Verschlüsselungshierarchie](encryption/encryption-hierarchy.md)|  
|Implementieren sicherer Verbindungen|[Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)|  
|Verschlüsselungsfunktionen|[Kryptografiefunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/cryptographic-functions-transact-sql)|  
  
 Zertifikate sind "Softwareschlüssel", die für zwei Server freigegeben sind, durch die eine sichere Kommunikation über starke Authentifizierung möglich ist. Zertifikate können in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Erweitern der Objekt- und Verbindungssicherheit erstellt und verwendet werden. Die folgende Tabelle enthält Informationen zum Verwenden von Zertifikaten mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erstellen eines Zertifikats zum Verwenden mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)|  
|Verwenden eines Zertifikats mit Datenbankspiegelung|[Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
  
## <a name="application-security"></a>Anwendungssicherheit  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gehört das Schreiben sicherer Clientanwendungen.  
  
 Weitere Informationen zum Sichern von Clientanwendungen auf Netzwerkebene finden Sie unter [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).  
  
## <a name="sql-server-security-tools-utilities-views-and-functions"></a>SQL Server-Sicherheitstools, -Hilfsprogramme, -Sichten und -Funktionen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Tools, Hilfsprogramme, Sichten und Funktionen zum Konfigurieren und Verwalten der Sicherheit zur Verfügung gestellt.  
  
### <a name="sql-server-security-tools-and-utilities"></a>SQL Server-Sicherheitstools und -Hilfsprogramme  
 Die folgende Tabelle enthält Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools und -Hilfsprogrammen zum Konfigurieren und Verwalten der Sicherheit.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Herstellen einer Verbindung mit, Konfigurieren und Steuern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[Verwenden von SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)|  
|Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Ausführen von Abfragen an der Eingabeaufforderung|[SQLCMD-Hilfsprogramm](../../tools/sqlcmd-utility.md)|  
|Netzwerkkonfiguration und Steuerung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[SQL Server-Konfigurations-Manager](../sql-server-configuration-manager.md)|  
|Aktivieren und Deaktivieren von Funktionen mit der richtlinienbasierten Verwaltung|[Verwalten von Servern mit der richtlinienbasierten Verwaltung](../policy-based-management/administer-servers-by-using-policy-based-management.md)|  
|Bearbeiten symmetrischer Schlüssel für einen Berichtsserver|[rskeymgmt-Hilfsprogramm &#40;SSRS&#41;](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)|  
  
### <a name="sql-server-security-catalog-views-and-functions"></a>SQL Server-Sicherheitskatalogsichten und -Funktionen  
 In [!INCLUDE[ssDE](../../includes/ssde-md.md)] werden Sicherheitsinformationen in zahlreichen Sichten und Funktionen dargestellt, die für Leistung und Nützlichkeit optimiert sind. Die folgende Tabelle enthält Informationen zu Sicherheitssichten und -funktionen.  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherheitskatalogsichten, durch die Informationen zu Berechtigungen, Rollen, Prinzipalen usw. auf Datenbankebene und Serverebene zurückgegeben werden. Außerdem sind Katalogsichten mit Informationen zu Verschlüsselungsschlüsseln, Zertifikaten und Anmeldeinformationen vorhanden.|[Sicherheitskatalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/security-catalog-views-transact-sql)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsfunktionen, durch die Informationen zum aktuellen Benutzer, zu Berechtigungen und zu Schemas zurückgegeben werden.|[Sicherheitsfunktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/security-functions-transact-sql)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit.|[Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
 [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
