---
title: Einrichten von Anmeldekonten für die Daten Bank Spiegelung oder AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d149016dabd0239bd76eadc8655b6752afd916d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701768"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a>Einrichten von Anmeldekonten für die Datenbankspiegelung oder AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Damit zwei Serverinstanzen eine Verbindung mit dem [Datenbank-Spiegelungsendpunkt](the-database-mirroring-endpoint-sql-server.md) der jeweils anderen Instanz herstellen können, benötigt das Anmeldekonto jeder Instanz Zugriff auf die jeweils andere Instanz. Außerdem benötigt jedes Anmeldekonto die CONNECT-Berechtigung für den Endpunkt der Datenbankspiegelung auf der anderen Instanz.  
  
 Die Auswirkungen dieser Anforderungen sind davon abhängig, ob die Serverinstanzen unter demselben Domänenbenutzerkonto ausgeführt werden:  
  
-   Falls die Serverinstanzen unter demselben Domänenbenutzerkonto ausgeführt werden, sind die richtigen Benutzeranmeldenamen automatisch in beiden **master** -Datenbanken vorhanden. Dadurch wird die Sicherheitskonfiguration für die Datenbankspiegelung und für AlwaysOn-Verfügbarkeitsgruppen vereinfacht.  
  
-   Werden die Serverinstanzen unter verschiedenen Benutzerkonten ausgeführt, müssen Benutzeranmeldungen auf der Serverinstanz, die den Prinzipalserver oder das primäre Replikat hostet, manuell auf der Serverinstanz reproduziert werden, die den Spiegelserver hostet, oder auf allen Serverinstanzen, die das sekundäre Replikat hosten. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Erstellen eines Anmeldenamens für ein anderes Konto](#CreateLogin) und [Erteilen der CONNECT-Berechtigung](#GrantConnect).  
  
    > [!IMPORTANT]  
    >  Um die Umgebungssicherheit zu erhöhen, sollten Sie die Verwendung separater Domänenkonten für die einzelnen Serverinstanzen in Erwägung ziehen.  
  
##  <a name="create-a-login-for-a-different-account"></a><a name="CreateLogin"></a> Erstellen eines Anmeldenamens für ein anderes Konto  
 Falls zwei Serverinstanzen als unterschiedliche Konten ausgeführt werden, muss der Systemadministrator mit der CREATE LOGIN-Anweisung von [!INCLUDE[tsql](../../includes/tsql-md.md)] für jede Serverinstanz einen Anmeldenamen für das Dienststartkonto der Remoteinstanz erstellen. Weitere Informationen finden Sie unter [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
> [!IMPORTANT]  
>  Falls Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem anderen als einem Domänenkonto ausführen, müssen Sie Zertifikate verwenden. Weitere Informationen finden Sie unter [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).  
  
 Damit z. B. die Serverinstanz sqlA, die unter loginA ausgeführt wird, eine Verbindung mit der Serverinstanz sqlB herstellt, die unter loginB ausgeführt wird, muss loginA auf sqlB vorhanden sein, und loginB muss auf sqlA vorhanden sein. Darüber hinaus müssen für eine Datenbank-Spiegelungssitzung, an der eine Zeugenserverinstanz beteiligt ist (sqlC) und bei der die drei Serverinstanzen unter verschiedenen Domänenkonten ausgeführt werden, die folgenden Anmeldenamen erstellt werden:  
  
|Instanz|Erstellen von Anmeldenamen und Erteilen der CONNECT-Berechtigung für ...|  
|--------------------|--------------------------------------------------------------|  
|sqlA|sqlB und sqlC|  
|sqlB|sqlA und sqlC|  
|sqlC|sqlA und sqlB|  
  
> [!NOTE]  
>  Mit dem Netzwerkdienst-Konto kann eine Verbindung hergestellt werden, indem das Computerkonto anstelle eines Domänenbenutzers verwendet wird. Falls das Computerkonto verwendet wird, muss es in der anderen Serverinstanz als Benutzer hinzugefügt werden.  
  
##  <a name="grant-connect-permission"></a><a name="GrantConnect"></a> Erteilen der CONNECT-Berechtigung  
 Nachdem ein Anmeldename in einer Serverinstanz erstellt wurde, muss dem Anmeldenamen die Berechtigung zum Herstellen einer Verbindung mit dem Endpunkt der Datenbankspiegelung der Serverinstanz erteilt werden. Der Systemadministrator erteilt die CONNECT-Berechtigung mithilfe einer GRANT-Anweisung von [!INCLUDE[tsql](../../includes/tsql-md.md)]. Weitere Informationen finden Sie unter [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)konfigurieren.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   [Ermöglicht den Netzwerk Zugriff auf einen Datenbankspiegelungs-Endpunkt mithilfe der Windows-Authentifizierung &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Problembehandlung für die Datenbankspiegelungskonfiguration (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfigurations &#40;SQL Server&#41;](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
