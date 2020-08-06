---
title: Herstellen einer Verbindung mit einem Berichts Server im einheitlichen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615784"
---
# <a name="connect-to-a-native-mode-report-server"></a>Herstellen einer Verbindung mit einem Berichtsserver im einheitlichen Modus
  Verwenden Sie dieses Dialogfeld, um eine Verbindung mit einer lokalen oder Remote-Berichtsserverinstanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder einer späteren [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Version herzustellen. Dieses Tool kann nicht verwendet werden, um eine Verbindung mit früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsservern herzustellen. Sie können nur jeweils eine Verbindung zu einer Instanz herstellen.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]Einheitlicher [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Modus.  
  
> [!NOTE]  
>  Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager wird nicht zum Konfigurieren und Verwalten des SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendet. Verwenden Sie die SharePoint-Zentraladministration und PowerShell-Skripts zum Konfigurieren eines Berichtsservers im SharePoint-Modus. Weitere Informationen finden Sie unter [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
> [!TIP]  
>  Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) wird mit der Berechtigungsstufe "highestAvailable" installiert. Dieses Verhalten ist beabsichtigt. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager erfordert Kommunikation mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-APIs. Ein Teil der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Kommunikation erfordert eine höhere Stufe oder Administratorprivilegien.  
  
-   Um eine Verbindung zu einer lokalen Berichtsserverinstanz herzustellen, verwenden Sie die Standardwerte, und klicken Sie auf **Verbinden**. Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager gibt den Namen des lokalen Servers vor und erkennt die Standardinstanz. In den meisten Fällen können Sie auf **Verbinden** klicken, ohne die Werte ändern zu müssen. Wenn Sie mehr als eine Instanz installiert haben, müssen Sie diejenige auswählen, die Sie verwenden möchten.  
  
-   Um eine Verbindung zu einer Remote-Berichtsserverinstanz herzustellen, geben Sie den Servernamen ein, klicken Sie auf **Suchen**, wählen Sie die Instanz aus, und klicken Sie dann auf **Verbinden**.  
  
 Um dieses Dialogfeld zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager. Dieses Dialogfeld wird sofort angezeigt, wenn Sie das Tool starten. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **Servername**  
 Geben Sie den Netzwerknamen des Computers ein, auf dem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder eine spätere Version von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert ist. Geben Sie nur den Computernamen ein, kein Präfix oder Schrägstriche.  
  
 **Sich**  
 Suchen Sie den unter **Servername**angegebenen Computer.  
  
 **Berichtsserverinstanz**  
 Wählen Sie aus, zu welcher Instanz Sie eine Verbindung herstellen möchten, wenn mehrere Berichtsserverinstanzen installiert sind. Es stehen nur gültige Instanzen zur Auswahl zur Verfügung. Wenn Sie ältere Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gleichzeitig mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz ausführen, werden diese Instanzen nicht in der Liste angezeigt.  
  
 **Herstellen einer Verbindung**  
 Stellen Sie die Verbindung zum Server und zur Instanz, die Sie angegeben haben, her.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
