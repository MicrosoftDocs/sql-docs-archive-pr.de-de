---
title: Sicherheit von Datenbankobjekten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695785"
---
# <a name="database-object-security-master-data-services"></a>Sicherheit von Datenbankobjekten (Master Data Services)
  In der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank werden Daten in mehreren Datenbanktabellen gespeichert und in Sichten angezeigt. Daher können Informationen, die Sie in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung gesichert haben, für Benutzern mit Zugriff auf die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank sichtbar sein.  
  
 So kann das Mitarbeitermodell beispielsweise Informationen zu den Mitarbeitergehältern oder das Kontomodell Informationen zu den Unternehmensfinanzen enthalten. Sie können einem Benutzer in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Benutzeroberfläche den Zugriff auf diese Modelle verweigern, aber Benutzer mit Zugriff auf die Datenbank können diese Daten anzeigen.  
  
 Um den Benutzern nur spezifische Daten zur Verfügung zu stellen, können Sie Datenbankobjekten Berechtigungen zuweisen. Weitere Informationen über das Erteilen von Berechtigungen finden Sie unter [GRANT (Objektberechtigungen) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql). Weitere Informationen zum Sichern von SQL Server finden Sie unter [Securing SQL Server](../relational-databases/security/securing-sql-server.md).  
  
 Die folgenden Tasks erfordern Zugriff auf die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank:  
  
-   [Bereitstellen von Daten](#Staging)  
  
-   [Überprüfen von Daten im Hinblick auf Geschäftsregeln](#rules)  
  
-   [Löschen von Versionen](#Versions)  
  
-   [Sofortiges Anwenden von Hierarchieelementberechtigungen](#Hierarchy)  
  
-   [Ändern des Systemadministratorkontos](#SysAdmin)  
  
-   [Konfigurieren von Systemeinstellungen](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a>Staging von Daten  
 In der folgenden Tabelle weist jedes sicherungsfähige Element „Name“ als Teil des Namens auf. Dies gibt den Namen der Stagingtabelle an, die angegeben wird, wenn eine Entität erstellt wird. Weitere Informationen finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
|Aktion|Sicherungsfähige Elemente|Berechtigungen|  
|------------|----------------|-----------------|  
|Laden Sie Blattelemente und ihre Attribute in die Stagingtabelle.|stg.name_Leaf|Erforderlich: INSERT<br /><br /> Optional: SELECT und UPDATE|  
|Laden Sie die Daten aus der Blattstagingtabelle in die entsprechenden MDS-Datenbanktabellen.|stg.udp_name_Leaf|Führen Sie|  
|Laden Sie konsolidierte Elemente und ihre Attribute in die Stagingtabelle.|stg.name_Consolidated|Erforderlich: INSERT<br /><br /> Optional: SELECT und UPDATE|  
|Laden Sie die Daten aus der konsolidierten Stagingtabelle in die entsprechenden MDS-Datenbanktabellen.|stg.udp_name_Consolidated|Führen Sie|  
|Laden Sie die Beziehungen zwischen den Blatt-und konsolidierten Elementen in einer expliziten Hierarchie in die Stagingtabelle.|stg.name_Relationship|Erforderlich: INSERT<br /><br /> Optional: SELECT und UPDATE|  
|Laden Sie die Daten aus der Beziehungsstagingtabelle in die entsprechenden MDS-Tabellen.|stg.udp_name_Relationship|Führen Sie|  
|Zeigen Sie Fehler an, die aufgetreten sind, als Daten aus den Stagingtabellen in die MDS-Datenbanktabellen eingefügt wurden.|stg.udp_name_Relationship|SELECT|  
  
 Weitere Informationen finden Sie unter [Datenimport &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a>Validieren von Daten anhand von Geschäftsregeln  
  
|Aktion|Sicherungsfähiges Element|Berechtigungen|  
|------------|---------------|-----------------|  
|Überprüfen einer Version der Daten anhand von Geschäftsregeln|mdm.udpValidateModel|Führen Sie|  
  
 Weitere Informationen finden Sie unter [Gespeicherte Überprüfungsprozedur &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
##  <a name="deleting-versions"></a><a name="Versions"></a>Löschen von Versionen  
  
|Aktion|Sicherungsfähige Elemente|Berechtigungen|  
|------------|----------------|-----------------|  
|Bestimmen der ID der zu löschenden Version|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Löschen einer Version eines Modells|mdm.udpVersionDelete|Führen Sie|  
  
 Weitere Informationen finden Sie unter [Löschen einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a>Sofortiges Anwenden von Hierarchie Element Berechtigungen  
  
|Aktion|Sicherungsfähige Elemente|Berechtigungen|  
|------------|----------------|-----------------|  
|Sofortiges Anwenden von Elementberechtigungen|mdm.udpSecurityMemberProcessRebuildModel|Führen Sie|  
  
 Weitere Informationen finden Sie unter [Sofortiges Anwenden von Elementberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a>Ändern des System Administrator Kontos  
  
|Aktion|Sicherungsfähige Elemente|Berechtigungen|  
|------------|----------------|-----------------|  
|Bestimmen der SID des neuen Administrators|mdm.tblUser|SELECT|  
|Ändern des Systemadministrator Kontos|mdm.udpSecuritySetAdministrator|Führen Sie|  
  
 Weitere Informationen finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a>Konfigurieren von System Einstellungen  
 Sie können bestimmte Systemeinstellungen konfigurieren, um das Verhalten in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]zu steuern. Sie können diese Einstellungen in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] oder, wenn Sie über die Zugriffsberechtigung UPDATE verfügen, direkt in die Datenbanktabelle mdm.tblSystemSetting anpassen. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit &#40;Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)  
  
  
