---
title: Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5558bc5684f2eb9053c935543db0c05d6225daf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615574"
---
# <a name="create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql"></a>Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung (Transact-SQL)
  In diesem Thema wird beschrieben, wie ein Datenbankspiegelungs-Endpunkt in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt wird, der die Windows-Authentifizierung verwendet. Um die Datenbankspiegelung oder [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] unterstützen zu können, benötigt jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Datenspiegelungs-Endpunkt. Eine Serverinstanz kann nur über einen Datenbankspiegelungsendpunkt verfügen, der einen einzelnen Port besitzt. Ein Datenbankspiegelungsendpunkt kann einen beliebigen Port verwenden, der auf dem lokalen System verfügbar ist, wenn der Endpunkt erstellt wird. Alle Datenbankspiegelungssitzungen auf einer Serverinstanz lauschen an diesem Port, und alle eingehenden Verbindungen für die Datenbankspiegelung verwenden diesen Port.  
  
> [!IMPORTANT]  
>  Wenn ein Datenbankspiegelungs-Endpunkt vorhanden und bereits in Gebrauch ist, empfiehlt es sich, diesen Endpunkt zu verwenden. Wenn ein in Gebrauch befindlicher Endpunkt gelöscht wird, kann dies zu Störungen bei vorhandenen Sitzungen führen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **So erstellen Sie einen Datenbankspiegelungsendpunkt:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Die Authentifizierungs- und Verschlüsselungsmethoden der Serverinstanz werden vom Systemadministrator festgelegt.  
  
> [!IMPORTANT]  
>  Der RC4-Algorithmus ist veraltet. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Stattdessen wird die Verwendung von AES empfohlen.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE ENDPOINT-Berechtigung oder die Mitgliedschaft in der festen Serverrolle "sysadmin". Weitere Informationen finden Sie unter [GRANT (Endpunktberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-database-mirroring-endpoint-that-uses-windows-authentication"></a>So erstellen Sie einen Datenbankspiegelungs-Endpunkt, der die Windows-Authentifizierung verwendet  
  
1.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, für die Sie einen Endpunkt für die Datenbankspiegelung erstellen möchten.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Ermitteln Sie mithilfe der folgenden Anweisung, ob ein Endpunkt für die Datenbankspiegelung bereits vorhanden ist:  
  
    ```sql
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;
    ```  
  
    > [!IMPORTANT]  
    >  Falls bereits ein Endpunkt der Datenbankspiegelung für die Serverinstanz vorhanden ist, verwenden Sie diesen Endpunkt für alle anderen Sitzungen, die Sie für die Serverinstanz einrichten.  
  
4.  Wenn Sie Transact-SQL zum Erstellen eines Endpunktes verwenden möchten, der mit Windows-Authentifizierung verwendet werden soll, verwenden Sie eine CREATE ENDPOINT-Anweisung. Die Anweisung weist folgende allgemeine Form auf:  
  
     CREATE ENDPOINT *\<endpointName>*  
  
     STATE=STARTED  
  
     AS TCP ( LISTENER_PORT = *\<listenerPortList>* )  
  
     FOR DATABASE_MIRRORING  
  
     (  
  
     [ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]  
  
     ]  
  
     [ [ **,** ] ENCRYPTION = **REQUIRED**  
  
     [ ALGORITHM { *\<algorithm>* } ]  
  
     ]  
  
     [ **,** ] ROLE = *\<role>*  
  
     )  
  
     Hierbei gilt:  
  
    -   *\<endpointName>* ist der eindeutige Name für den Endpunkt der Datenbankspiegelung der Serverinstanz.  
  
    -   STARTED gibt an, dass der Endpunkt gestartet werden und mit der Überwachung auf Verbindungen beginnen soll. Ein Endpunkt der Datenbankspiegelung wird in der Regel im Status STARTED erstellt. Alternativ können Sie eine Sitzung in einem Status STOPPED (die Standardeinstellung) oder DISABLED erstellen.  
  
    -   *\<listenerPortList>* ist eine einzelne Portnummer (*nnnn*), an dem der Server auf Datenbankspiegelungsnachrichten lauschen soll. Nur TCP ist zulässig; wenn Sie ein anderes Protokoll angeben, wird ein Fehler ausgelöst.  
  
         Eine Portnummer kann in einem Computersystem nur einmal verwendet werden. Ein Datenbankspiegelungsendpunkt kann einen beliebigen Port verwenden, der auf dem lokalen System verfügbar ist, wenn der Endpunkt erstellt wird. Verwenden Sie die folgende Transact-SQL-Anweisung, um den Port anzugeben, der zurzeit von TCP-Endpunkten im System verwendet wird:  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  Für jede Serverinstanz ist ein und nur ein eindeutiger Überwachungsport erforderlich.  
  
    -   Bei der Windows-Authentifizierung ist die AUTHENTICATION-Option optional, es sei denn, der Endpunkt soll nur NTLM oder Kerberos zum Authentifzieren von Verbindungen verwenden. *\<authorizationMethod>* gibt die Methode zum Authentifizieren von Verbindungen an: NTLM, KERBEROS oder NEGOTIATE. Die Standardeinstellung, NEGOTIATE, bewirkt, dass der Endpunkt das Aushandlungsprotokoll von Windows verwendet, um NTLM oder Kerberos auszuwählen. Die Verbindungsverhandlung ermöglicht abhängig von der Authentifizierungsebene des gegenüberliegenden Endpunktes Verbindungen mit oder ohne Authentifizierung.  
  
    -   ENCRYPTION wird standardmäßig auf REQUIRED festgelegt. Dies bedeutet, dass alle Verbindungen mit diesem Endpunkt Verschlüsselungen verwenden müssen. Sie können die Verschlüsselung jedoch auch deaktivieren oder als optional für einen Endpunkt festlegen. Die Alternativen lauten folgendermaßen:  
  
        |Wert|Definition|  
        |-----------|----------------|  
        |DISABLED|Gibt an, dass über eine Verbindung gesendete Daten nicht verschlüsselt werden.|  
        |SUPPORTED|Gibt an, dass die Daten nur verschlüsselt werden, wenn der gegenüberliegende Endpunkt SUPPORTED oder REQUIRED angibt.|  
        |REQUIRED|Gibt an, dass über eine Verbindung gesendete Daten verschlüsselt werden müssen.|  
  
         Wenn ein Endpunkt Verschlüsselung erfordert, muss für den anderen Endpunkt ENCRYPTION auf SUPPORTED oder REQUIRED festgelegt werden.  
  
    -   *\<algorithm>* stellt die Option zum Angeben der Verschlüsselungsstandards für den Endpunkt bereit. Der Wert von *\<algorithm>* kann einer der folgenden Algorithmen oder eine Kombination aus Algorithmen sein: RC4, AES, AES RC4 oder RC4 AES.  
  
         AES RC4 gibt an, dass dieser Endpunkt den Verschlüsselungsalgorithmus verhandelt, wobei der AES-Algorithmus bevorzugt wird. RC4 AES gibt an, dass dieser Endpunkt den Verschlüsselungsalgorithmus verhandelt, wobei der RC4-Algorithmus bevorzugt wird. Wenn beide Endpunkte beide Algorithmen angeben, jedoch in unterschiedlicher Reihenfolge, gewinnt der Endpunkt, der die Verbindung annimmt.  
  
        > [!NOTE]  
        >  Der RC4-Algorithmus ist veraltet. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Stattdessen wird die Verwendung von AES empfohlen.  
  
    -   *\<role>* definiert die Rolle bzw. Rollen, die der Server ausführen kann. Die Angabe von ROLE ist erforderlich. Die Rolle des Endpunkts ist jedoch nur für die Datenbankspiegelung relevant. Für [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]wird die Rolle des Endpunkts ignoriert.  
  
         Damit eine Serverinstanz als eine Rolle für eine Datenbankspiegelungssitzung und eine andere Rolle für eine andere Sitzung fungieren kann, geben Sie ROLE=ALL an. Wenn Sie eine Serverinstanz auf die Partner- oder Zeugenrolle beschränken möchten, geben Sie ROLE=PARTNER bzw. ROLE=WITNESS an.  
  
        > [!NOTE]  
        >  Weitere Informationen zu den Optionen für die Daten Bank Spiegelung für verschiedene Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie [unter von den Editionen von SQL Server 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
     Eine vollständige Beschreibung der CREATE ENDPOINT-Syntax finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)erstellt wird, der die Windows-Authentifizierung verwendet.  
  
    > [!NOTE]  
    >  Um einen vorhandenen Endpunkt zu ändern, verwenden Sie [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)erstellt wird, der die Windows-Authentifizierung verwendet.  
  
###  <a name="example-creating-endpoints-to-support-for-database-mirroring-transact-sql"></a><a name="TsqlExample"></a> Beispiel: Erstellen von Endpunkten mit Unterstützung der Datenbankspiegelung (Transact-SQL)  
 Im folgenden Beispiel werden Datenbankspiegelungs-Endpunkte für die Standardserverinstanzen auf drei separaten Computersystemen erstellt:  
  
|Rolle der Serverinstanz|Name des Hostcomputers|  
|-----------------------------|---------------------------|  
|Partner (anfangs die Prinzipalrolle)|`SQLHOST01\.`|  
|Partner (anfangs die Spiegelrolle)|`SQLHOST02\.`|  
|Zeuge|`SQLHOST03\.`|  
  
 In diesem Beispiel verwenden alle drei Endpunkte die Portnummer 7022, wobei jede verfügbare Portnummer möglich wäre. Die Option AUTHENTICATION ist unnötig, da die Endpunkte den Standardtyp, also die Windows-Authentifizierung verwenden. Die Option ENCRYPTION ist ebenfalls überflüssig, da alle Endpunkte das Authentifizierungsverfahren für eine Verbindung aushandeln sollen, was bei der Windows-Authentifizierung das Standardverhalten darstellt. Außerdem erfordern alle Endpunkte die Verschlüsselung, was ebenfalls zum Standardverhalten gehört.  
  
 Jede Serverinstanz ist darauf beschränkt, entweder als Partner oder als Zeuge zu agieren, und der Endpunkt jedes Servers legt die Rolle ausdrücklich fest (ROLE=PARTNER oder ROLE=WITNESS).  
  
> [!IMPORTANT]  
>  Jede Serverinstanz kann nur einen Endpunkt besitzen. Wenn Sie daher wollen, dass eine Serverinstanz in einigen Sitzungen als Partner und in anderen als Zeuge agiert, müssen Sie ROLE=ALL festlegen.  
  
```sql
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  

### <a name="to-configure-a-database-mirroring-endpoint"></a>So konfigurieren Sie einen Datenbankspiegelungs-Endpunkt
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](../availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [Ermöglichen des Verwendens von Zertifikaten für eingehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [Angeben einer Servernetzwerkadresse &#40;Datenbankspiegelung&#41;](specify-a-server-network-address-database-mirroring.md)  
  
-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **So zeigen Sie Informationen zum Datenbankspiegelungs-Endpunkt an**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [Auswählen eines Verschlüsselungsalgorithmus](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)   
 [Angeben einer Servernetzwerkadresse (Datenbankspiegelung)](specify-a-server-network-address-database-mirroring.md)   
 [Beispiel: Einrichten der Datenbankspiegelung mithilfe der Windows-Authentifizierung &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)  
