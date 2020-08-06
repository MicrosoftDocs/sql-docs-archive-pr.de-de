---
title: Verwalten des Integration Services Dienstanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- services [Integration Services], configuring
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39b0db4e2ff9611910af5cd8fadb112ea75855ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617171"
---
# <a name="manage-the-integration-services-service"></a>Verwalten des Integration Services-Diensts
    
> [!IMPORTANT]  
>  In diesem Thema wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
 Wenn Sie die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Komponente von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installieren, wird auch der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst installiert. Standardmäßig wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst gestartet, und der Starttyp des Dienstes ist auf automatisch festgelegt. Sie müssen jedoch auch [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] installieren, um den Dienst zur Verwaltung gespeicherter und ausgeführter [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete verwenden zu können.  
  
> [!NOTE]  
>  Mit der-Version von können Sie keine Verbindung mit einer Instanz des- [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Dienstanbieter herstellen [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] . Das heißt, im Dialogfeld **Verbindung mit Server herstellen** können Sie keinen Server eingeben, auf dem nur die [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] -Version des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts ausgeführt wird. Sie können jedoch die Konfigurationsdatei für den Dienst von der [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] -Version von [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] aus bearbeiten und so Pakete verwalten, die in einer Instanz von [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]gespeichert sind. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md).  
  
 Es kann nur eine einzige Instanz des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienstes auf einem Computer installiert werden. Der Dienst ist nicht spezifisch für eine bestimmte Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]. Sie melden sich beim Dienst mit dem Namen des Computers an, auf dem er ausgeführt wird.  
  
 Sie können den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst mithilfe eines der folgenden Snap-Ins für Microsoft Management Console (MMC) verwalten: SQL Server-Konfigurations-Manager oder -Dienste. Bevor Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Pakete verwalten können, muss der Dienst gestartet werden.  
  
 Standardmäßig wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst für die Verwaltung von Paketen in der msdb-Datenbank der Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)] konfiguriert, die zur selben Zeit wie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]installiert wird. Wenn eine Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)] nicht zur selben Zeit installiert wird, wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst so konfiguriert, dass Pakete in der msdb-Datenbank der lokalen Standardinstanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]verwaltet werden. Zur Verwaltung von Paketen, die in einer benannten Instanz oder einer Remoteinstanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]bzw. in mehreren Instanzen von [!INCLUDE[ssDE](../includes/ssde-md.md)]gespeichert sind, müssen Sie die Konfigurationsdatei ändern. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md).  
  
 Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst ist standardmäßig so konfiguriert, dass ausgeführte Pakete angehalten werden, sobald der Dienst angehalten wird. Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst wartet jedoch nicht darauf, dass die Pakete angehalten werden, und einige Pakete können weiterhin ausgeführt werden, nachdem der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst angehalten wurde.  
  
 Wenn der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst angehalten wird, können Sie weiterhin Pakete mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Import/Export-Assistenten, dem [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer, dem Paketausführungsprogramm und der **dtexec** -Eingabeaufforderung (dtexec.exe) ausführen. Sie können die ausgeführten Pakete jedoch nicht überwachen.  
  
 Standardmäßig wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst im Kontext des NETWORK SERVICE-Kontos ausgeführt.  
  
 Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst schreibt in das Windows-Ereignisprotokoll. Sie können Dienstereignisse in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]anzeigen. Sie können Dienstereignisse auch mithilfe der Windows-Ereignisanzeige anzeigen.  
  
### <a name="to-set-properties-of-integration-services-service-using-the-services-snap-in"></a>So legen Sie die Eigenschaften des Integration Services-Dienstes mit dem Dienste-Snap-In fest  
  
-   [Festlegen der Eigenschaften des Integration Services-Diensts](../../2014/integration-services/set-the-properties-of-the-integration-services-service.md)  
  
### <a name="to-view-service-events-for-integration-services-service"></a>So zeigen Sie Dienstereignisse für den Integration Services-Dienst an  
  
-   [Anzeigen von Ereignissen für den Integration Services-Dienst](../../2014/integration-services/view-events-for-the-integration-services-service.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services Dienst &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md)   
 [Konfigurieren des Integration Services Service &#40;SSIS-Dienst&#41;](configuring-the-integration-services-service-ssis-service.md)   
 [SQL Server-Import/Export-Assistent](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [dtexec (Hilfsprogramm)](packages/dtexec-utility.md)   
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)  
  
  
