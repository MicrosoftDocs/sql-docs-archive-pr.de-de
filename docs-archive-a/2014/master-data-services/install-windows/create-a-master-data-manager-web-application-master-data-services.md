---
title: Erstellen einer Master Data Manager-Webanwendung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609921"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a>Erstellen einer Master Data Manager-Webanwendung (Master Data Services)
  Die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung stellt eine Oberfläche für Benutzer für das Arbeiten mit Masterdaten und für Administratoren für das Konfigurieren und Verwalten von MDS bereit.  
  
 Eine Webanwendung muss immer in einer Website enthalten sein. Um eine Webanwendung zu erstellen, gehen Sie folgendermaßen vor:  
  
-   Verwenden Sie die Standardwebsite, und erstellen Sie dann die Webanwendung,  
  
-   Verwenden Sie eine vorhandene Website, und erstellen Sie dann die Webanwendung, oder  
  
-   Erstellen Sie eine neue Website, die automatisch eine Webanwendung erstellt.  
  
 Nachdem Sie die Webanwendung erstellt haben, ordnen Sie die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank der Webanwendung zu.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Weitere Informationen zu den Anforderungen für den Computer, auf dem die Webanwendung gehostet wird, finden Sie unter [Anforderungen für die Webanwendung &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md).  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>So erstellen Sie eine Master Data Manager-Webanwendung in einer neuen Website  
 Wenn Sie eine neue Website erstellen, ist die Stammwebanwendung die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung. Die Webanwendung wird auch einem neuen Anwendungspool hinzugefügt.  
  
> [!NOTE]  
>  Bei diesem Verfahren können Sie keinen virtuellen Pfad und Alias der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung angeben. Wenn Sie einen virtuellen Pfad und Alias für [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]angeben möchten, müssen Sie eine Webanwendung in einer vorhandenen Website erstellen, die noch nicht als [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung konfiguriert wurde.  
  
 Darüber hinaus unterstützt [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] das Erstellen von Websites, die nur HTTP-Bindungen aufweisen. Um eine HTTPS-Bindung hinzuzufügen, erstellen Sie eine neue Website und eine Anwendung in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Weitere Informationen finden Sie dann unter [Schützen einer Master Data Manager-Webanwendung](secure-a-master-data-manager-web-application.md) .  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a>So erstellen Sie eine Master Data Manager-Webanwendung in einer neuen Website  
  
1.  Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Webkonfiguration** in der Liste Website die Option **Neue Website erstellen**aus.  
  
4.  Geben Sie im Dialogfeld **Website erstellen** Informationen für eine neue Website an. Weitere Informationen zu den Benutzeroberflächenoptionen im Dialogfeld finden Sie unter [Website erstellen (Dialogfeld) &#40;Konfigurations-Manager für Master Data Services&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md).  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>So erstellen Sie eine Master Data Manager-Webanwendung in einer vorhandenen Website  
 Wenn Sie in einer vorhandenen Website eine Webanwendung erstellen, können Sie den virtuellen Pfad und Alias der Webanwendung auswählen. Die Webanwendung wird einem neuen Anwendungspool hinzugefügt.  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a>So erstellen Sie eine Master Data Manager-Webanwendung in einer vorhandenen Website  
  
1.  Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Webkonfiguration** aus der Dropdownliste **Website** die Website aus, in der Sie die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung erstellen möchten.  
  
4.  Klicken Sie auf **Anwendung erstellen**.  
  
5.  Geben Sie im Dialogfeld **Webanwendung erstellen** Informationen für eine neue Webanwendung an. Weitere Informationen zu den Benutzeroberflächenoptionen im Dialogfeld finden Sie unter [Webanwendung erstellen (Dialogfeld) &#40;Konfigurations-Manager für Master Data Services&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Ordnen Sie die Webanwendung einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank zu. Weitere Informationen finden Sie unter [Zuordnen einer Master Data Services-Datenbank und -Webanwendung](associate-a-master-data-services-database-and-web-application.md).  
  
-   Wenn Sie den Inhalt mit Secure Sockets Layer (SSL) verschlüsseln möchten, können Sie die Website, die die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung hostet, optional so konfigurieren, dass diese eine HTTPS-Bindung verwendet. Konfigurieren Sie das Serverzertifikat für den Webserver, eine HTTPS-Bindung und die SSL-Einstellungen für die Website mithilfe eines IIS (Internet Information Services)-Tools, z. B. IIS-Manager. Weitere Informationen finden Sie unter [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Master Data Services](install-master-data-services.md)  
  
  
