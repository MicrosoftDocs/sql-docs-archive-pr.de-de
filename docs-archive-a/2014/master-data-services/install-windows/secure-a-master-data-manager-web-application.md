---
title: Sichern einer Master Data Manager-Webanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f2ee807c2cd474542f701226d08427ade8279e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722894"
---
# <a name="secure-a-master-data-manager-web-application"></a>Schützen einer Master Data Manager-Webanwendung
  Sie können die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung per HTTPS schützen.  
  
> [!NOTE]  
>  Für die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung kann entweder HTTP oder HTTPS verwendet werden, jedoch nicht beides.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie die Prozedur aus  
  
-   Sie müssen Administrator auf dem Webserver sein, auf dem [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] installiert ist.  
  
-   Auf dem Webserver muss MDS installiert sein, und es muss eine Webanwendung vorhanden sein. Weitere Informationen finden Sie unter [Installieren von Master Data Services](install-master-data-services.md) und [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>So schützen Sie die Master Data Manager-Webanwendung per HTTPS  
  
1.  Nachdem Sie sich vergewissert haben, dass die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung per HTTP ordnungsgemäß konfiguriert wurde, erstellen Sie in IIS ein Zertifikat. Weitere Informationen finden Sie unter [Konfigurieren von Serverzertifikaten in IIS 7.0](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  Klicken Sie im Bereich **Verbindungen** unter **Websites**auf die Website, auf der die [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung gehostet wird.  
  
3.  Klicken Sie im Bereich **Aktionen** auf **Bindungen**.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
5.  Wählen Sie in der Liste die Option **https**.  
  
6.  Wählen Sie das SSL-Zertifikat aus.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Optional. Um HTTP zu entfernen, damit Benutzer nur per HTTPS auf die Website zugreifen können, klicken Sie in der Liste auf die Zeile mit **http**. Klicken Sie auf **Entfernen** , und klicken Sie im Bestätigungsdialogfeld auf **Ja**.  
  
    > [!IMPORTANT]  
    >  Nachdem HTTP entfernt wurde, müssen die basicHttp- und wsHttpBinding-Konfiguration geändert werden.  
  
9. Klicken Sie zum Schließen des Dialogfelds **Sitebindungen** auf **Schließen**.  
  
10. Öffnen Sie nun die Datei web.config von *Laufwerk*: \Programme\Microsoft SQL server\120\master Data services\webapplication.  
  
11. Suchen Sie nach der Zeichenfolge `<security mode="Message">` , und ändern Sie diese in `<security mode="Transport">`.  
  
12. Speichern und schließen Sie die Datei. Wenn Sie einen Fehler erhalten, kann dies daran liegen, dass Sie die Benutzerkontensteuerung aktiviert haben. Weitere Informationen finden Sie unter [Deaktivieren der Benutzerkontensteuerung](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx). Benutzer sollten jetzt per HTTPS auf die Website zugreifen können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Master Data Manager-Webanwendung &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
