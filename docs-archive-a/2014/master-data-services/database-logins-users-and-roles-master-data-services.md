---
title: Datenbankanmeldenamen, -benutzer und -rollen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eadd6fb4d5b9798920d65119386aa2c58afebfa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721538"
---
# <a name="database-logins-users-and-roles-master-data-services"></a>Datenbankanmeldenamen, -benutzer und -rollen (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] enthält Anmeldenamen, Benutzer und Rollen, die automatisch auf der [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] -Instanz installiert werden, die die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank hostet. Diese Anmeldenamen, Benutzer und Rollen sollten nicht geändert werden.  
  
## <a name="logins"></a>Anmeldungen  
  
|Anmelden|BESCHREIBUNG|  
|-----------|-----------------|  
|`mds_dlp_login`|Ermöglicht die Erstellung von UNSAFE-Assemblys.<br /><br /> –Deaktivierter Anmeldename mit willkürlich generiertem Kennwort.<br /><br /> - Wird für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank dbo zugeordnet.<br /><br /> - Für msdb wird mds_clr_user diesem Anmeldenamen zugeordnet.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).|  
|`mds_email_login`|Aktiviert den für Benachrichtigungen verwendeten Anmeldenamen.<br /><br /> Für msdb und die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank wird mds_email_user diesem Anmeldenamen zugeordnet.|  
  
## <a name="msdb-users"></a>msdb-Benutzer  
  
|Benutzer|BESCHREIBUNG|  
|----------|-----------------|  
|`mds_clr_user`|Nicht verwendet.<br /><br /> Wird mds_dlp_login zugeordnet.|  
|`mds_email_user`|Wird für Benachrichtigungen verwendet.<br /><br /> Wird mds_email_login zugeordnet.<br /><br /> Ist ein Element der Rolle DatabaseMailUserRole.|  
  
## <a name="master-data-services-database-users"></a>Master Data Services-Datenbankbenutzer  
  
|Benutzer|BESCHREIBUNG|  
|----------|-----------------|  
|`mds_email_user`|Wird für Benachrichtigungen verwendet.<br /><br /> Verfügt über die SELECT-Berechtigung für das mdm-Schema.<br /><br /> Verfügt über die EXECUTE-Berechtigung für den benutzerdefinierten Tabellentyp mdm.MemberGetCriteria.<br /><br /> Verfügt über die EXECUTE-Berechtigung für die gespeicherte Prozedur mdm.udpNotificationQueueActivate.|  
|**mds_schema_user**|Besitzt die mdm- und mdq-Schemas. Das Standardschema ist mdm.<br /><br /> Ist keinem Anmeldenamen zugeordnet.|  
|**mds_ssb_user**|Wird zum Ausführen von Service Broker-Tasks verwendet.<br /><br /> Verfügt über die Berechtigungen DELETE, INSERT, REFERENCES, SELECT und UPDATE für alle Schemas.<br /><br /> Ist keinem Anmeldenamen zugeordnet.|  
  
## <a name="master-data-services-database-role"></a>Master Data Services-Datenbankrolle  
  
|Role|BESCHREIBUNG|  
|----------|-----------------|  
|`mds_exec`|Diese Rolle enthält das Konto, das Sie in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] festlegen, wenn Sie eine [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung erstellen und ein Konto für den Anwendungspool festlegen. Die Rolle mds_exec verfügt über die nachfolgenden Berechtigungen.<br /><br /> **Execute** -Berechtigung für alle Schemas.<br /><br /> **Alter**-, **Insert**-und **Select** -Berechtigung für die folgenden Tabellen:<br />mdm.tblStgMember<br />mdm.tblStgMemberAttribute<br />mdm.tbleStgRelationship<br /><br /> **Select** -Berechtigung für die folgenden Tabellen:<br />mdm.tblUser<br />mdm.tblUserGroup<br />mdm.tblUserPreference<br /><br /> **Select** -Berechtigung für diese Sichten:<br />mdm.viw_SYSTEM_SECURITY_NAVIGATION<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br />mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>Schemas  
  
|Role|BESCHREIBUNG|  
|----------|-----------------|  
|`mdm`|Enthält alle [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank- und Service Broker-Objekte außer die im mdq-Schema enthaltenen Funktionen.|  
|`mdq`|Enthält [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbankfunktionen, die sich auf das Filtern von Elementergebnissen auf Grundlage von regulären Ausdrücken oder Ähnlichkeiten beziehen und die zum Formatieren von Benachrichtigungs-E-Mails vorgesehen sind.|  
|**stg**|Enthält [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbanktabellen, gespeicherte Prozeduren und Sichten, die sich auf den Stagingprozess beziehen. Löschen Sie keines dieser Objekte. Weitere Informationen zum Stagingprozess finden Sie unter [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
