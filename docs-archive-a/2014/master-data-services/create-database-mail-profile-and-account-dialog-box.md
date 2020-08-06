---
title: Dialog Feld "Datenbank-E-Mail Profil und Konto erstellen" (Konfigurations-Manager für Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.dbmailprofileacct.f1
ms.assetid: b93ea3d4-9f22-490e-8e26-d766b454aed6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 027aee541c1e73bc71db7e9fa14914e52bf78bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699969"
---
# <a name="create-database-mail-profile-and-account-dialog-box-master-data-services-configuration-manager"></a>Datenbank-E-Mail-Profil und -Konto erstellen (Dialogfeld im Konfigurations-Manager für Master Data Services)
  Verwenden Sie das Dialogfeld **Datenbank-E-Mail-Profil und -Konto erstellen** , um ein Datenbank-E-Mail-Profil und -Konto für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank zu erstellen. Dieses Profil wird verwendet, um Benutzer und Gruppen per E-Mail über die nicht erfolgreiche Überprüfung einer Geschäftsregel zu benachrichtigen.  
  
## <a name="database-mail-profile-and-account"></a>Datenbank-E-Mail-Profil und -Konto  
 Ein *Datenbank-E-Mail Profil* ist eine Sammlung von Datenbank-E-Mail-Konten. Ein *Datenbank-E-Mail-Konto* enthält Informationen, mit deren Hilfe [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] E-Mail-Nachrichten an einen SMTP-Server sendet. Wenn Sie das Profil und das Konto in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]erstellen, wird dem Profil das Konto automatisch hinzugefügt, und E-Mails werden unter Verwendung dieser Kontoinformationen gesendet.  
  
> [!NOTE]  
>  In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] können Sie weder vorhandene Datenbank-E-Mail-Profile und -Konten aktualisieren noch mehrere Konten für ein Profil konfigurieren. Verwenden Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] - oder Transact-SQL-Skripts, um erweiterte Aufgaben mit Datenbank-E-Mail auszuführen. Weitere Informationen finden Sie im Abschnitt [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) in der SQL Server-Onlinedokumentation.  
  
|Name des Steuerelements|BESCHREIBUNG|  
|------------------|-----------------|  
|**Profilname**|Geben Sie einen Namen für das neue Datenbank-E-Mail-Profil ein. Dieser Name muss in den für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank konfigurierten Datenbank-E-Mail-Profilen eindeutig sein.<br /><br /> Nachdem Sie dieses Profil erstellt haben, ist es verfügbar und auf der Seite **Datenbank** von [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]ausgewählt.|  
|**Kontoname**|Geben Sie einen Namen für das neue Datenbank-E-Mail-Konto ein, das diesem Profil zugewiesen werden soll. Dieser Name muss in den für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank konfigurierten Datenbank-E-Mail-Konten eindeutig sein. Dieses Konto entspricht weder einem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konto noch einem Windows-Benutzerkonto.|  
  
## <a name="outgoing-smtp-mail-server"></a>Postausgangsserver (SMTP)  
  
|Name des Steuerelements|BESCHREIBUNG|  
|------------------|-----------------|  
|**E-Mail-Adresse**|Geben Sie den Namen der E-Mail-Adresse für das Konto ein. Dies ist die e-Mail-Adresse, von der aus e-Mail gesendet wird. Sie muss im Format *email_name* @ *domain_name*sein. Ein Beispiel für eine E-Mail-Adresse ist sales@contoso.com.|  
|**Anzeigename**|Optionale Einstellung. Geben Sie den Namen ein, der in den von diesem Konto aus versendeten E-Mails angezeigt wird. Ein Beispiel für den Anzeigenamen ist Contoso Sales Group.|  
|**E-Mail-Antwortadresse**|Optionale Einstellung. Geben Sie die E-Mail-Adresse ein, die für Antworten auf E-Mails von diesem Konto verwendet wird. Ein Beispiel für eine E-Mail-Antwortadresse ist admin@contoso.com.|  
|**SMTP-Server**|Geben Sie den Namen oder die IP-Adresse des SMTP-Servers ein, der von diesem Konto zum Senden von E-Mails verwendet wird. Ein Beispiel für das SMTP-Server Format ist `smtp.` *<COMPANY_NAME>* `.com` . Informationen hierzu erhalten Sie von Ihrem E-Mail-Administrator.|  
|**Portnummer**|Geben Sie die Portnummer des SMTP-Servers für dieses Konto ein. Port 25 ist der SMTP-Standardport.|  
|**Für diesen Server ist eine sichere Verbindung (SSL) erforderlich**|Verschlüsselt die Kommunikation mit SSL (Secure Sockets Layer).|  
  
## <a name="smtp-authentication"></a>SMTP-Authentifizierung  
 Datenbank-E-Mail kann mit den Anmeldeinformationen von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], mit von Ihnen angegebenen anderen Anmeldeinformationen oder anonym gesendet werden. Wenn der E-Mail-Server eine Authentifizierung erfordert, empfiehlt es sich, ein bestimmtes Benutzerkonto für Datenbank-E-Mail zu erstellen. Dieses Benutzerkonto sollte über minimale Berechtigungen verfügen und für keinen anderen Zweck verwendet werden.  
  
|Name des Steuerelements|BESCHREIBUNG|  
|------------------|-----------------|  
|**Windows-Authentifizierung mithilfe der Anmeldeinformationen des Datenbank-Engine-Diensts**|Geben Sie an, dass Datenbank-E-Mail die Anmelde Informationen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Windows-Dienst Kontos für die Authentifizierung auf dem SMTP-Server verwenden soll.|  
|**Standardauthentifizierung**|Geben Sie an, dass für Datenbank-E-Mail ein bestimmter Benutzername und ein bestimmtes Kennwort verwendet werden sollen, damit sie auf dem SMTP-Server authentifiziert werden kann. Diese Informationen werden nur zur Authentifizierung mit dem E-Mail-Server verwendet, das Konto muss keinem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Benutzer bzw. keinem Benutzer auf dem Computer entsprechen, auf dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausgeführt wird.|  
|**Benutzername**|Geben Sie den Namen des Benutzerkontos ein, das von Datenbank-E-Mail für die Anmeldung beim SMTP-Server verwendet wird. Ein Benutzername ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.|  
|**Kennwort**|Geben Sie das Kennwort ein, mit dem sich Datenbank-E-Mail beim SMTP-Server anmeldet. Ein Kennwort ist erforderlich, wenn der SMTP-Server die Standardauthentifizierung erfordert.|  
|**Kennwort bestätigen**|Geben Sie das Kennwort zur Bestätigung erneut ein.|  
|**Anonyme Authentifizierung**|Geben Sie an, dass der SMTP-Server keine Authentifizierung erfordert. Datenbank-E-Mail verwendet keinerlei Anmeldeinformationen zur Authentifizierung auf dem SMTP-Server.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Die Seite "Daten Bank Konfiguration" &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Einrichten von Datenbank und Website für Master Data Services](set-up-the-database-and-website-for-master-data-services.md)  
  
  
