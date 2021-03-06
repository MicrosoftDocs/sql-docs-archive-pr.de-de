---
title: Erstellen des Dialogfeldes der Webanwendung (Konfigurations-Manager für Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.createapp.f1
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1894c4d07f49dd0214166a822eef223b6b51905d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621549"
---
# <a name="create-web-application-dialog-box-master-data-services-configuration-manager"></a>Webanwendung erstellen (Dialogfeld im Konfigurations-Manager für Master Data Services)
  Im Dialogfeld **Webanwendung erstellen** können Sie die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung erstellen. Diese Webanwendung wird auf der Website erstellt, die Sie auf der Seite **Webkonfiguration** ausgewählt haben.  
  
## <a name="web-application"></a>Webanwendung.  
 Der Webserver stellt den Inhalt für diese Webanwendung aus dem Ordner [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **WebApplication** im Dateisystem bereit. Dieser Speicherort wird während des Setups angegeben. der Pfad lautet standardmäßig *Laufwerk*: \Programme\Microsoft SQL server\120\master Data services\webapplication.  
  
|Name des Steuerelements|BESCHREIBUNG|  
|------------------|-----------------|  
|Virtueller Pfad|Wählen Sie den virtuellen Pfad aus, unter dem Sie die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung erstellen möchten. Ein virtueller Pfad ist Teil der URL, die für den Zugriff auf eine Webanwendung verwendet wird.<br /><br /> Diese Liste wird nach den virtuellen Anwendungspfaden gefiltert, unter denen die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung erstellt werden kann. Sie können keine [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung unter einer anderen [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung erstellen.|  
|Alias|Geben Sie einen Namen für die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung ein, oder verwenden Sie den Standardnamen. Dieser Name wird in einer URL verwendet, um von einem Webbrowser aus auf die Webanwendung zuzugreifen.|  
  
## <a name="application-pool"></a>Anwendungspool  
  
|Name des Steuerelements|BESCHREIBUNG|  
|------------------|-----------------|  
|**Name**|Geben Sie einen eindeutigen Anzeigenamen für einen neuen Anwendungspool ein, oder verwenden Sie den Standardnamen. Diesem Anwendungspool wird die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung hinzugefügt.<br /><br /> Anwendungspools verfügen über immanente Grenzen, durch die Anwendungen in einem Anwendungspool daran gehindert werden, Einfluss auf Anwendungen in einem anderen Anwendungspool zu nehmen.|  
|**Benutzername**|Geben Sie einen Domänen- und Benutzernamen aus Active Directory ein. Dieses Konto entspricht der Identität des Anwendungspools, in dem die Webanwendung ausgeführt wird. Dieses Konto sollte mit dem Konto identisch sein, das Sie beim Erstellen der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank als Dienstkonto angegeben haben.<br /><br /> Das Konto wird für den Datenbankzugriff der mds_exec-Datenbankrolle in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank hinzugefügt. Weitere Informationen finden Sie unter [Datenbankanmeldenamen, -benutzer und -rollen &#40;Master Data Services&#41;](database-logins-users-and-roles-master-data-services.md). Es wird darüber hinaus einer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Windows-Gruppe wie **MDS_ServiceAccounts**hinzugefügt. Ihr wurden Berechtigungen auf das temporäre Kompilierungsverzeichnis, **MDSTempDir**im Dateisystem erteilt. Weitere Informationen finden Sie unter [Ordner- und Dateiberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/folder-and-file-permissions-master-data-services.md).|  
|**Kennwort**|Geben Sie das Kennwort für das angegebene Benutzerkonto ein.|  
|**Kennwort bestätigen**|Geben Sie das Kennwort für das angegebene Benutzerkonto erneut ein. Die Felder **Kennwort** und **Kennwort bestätigen** müssen das gleiche Kennwort enthalten.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Die Webkonfigurations Seite &#40;Konfigurations-Manager für Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md)   
 [Einrichten der Datenbank und Website für Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Webanwendungs Anforderungen &#40;Master Data Services&#41;](install-windows/web-application-requirements-master-data-services.md)   
 [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
