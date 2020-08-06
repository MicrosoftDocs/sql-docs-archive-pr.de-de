---
title: Festlegen der Eigenschaften des Integration Services Dienstanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 055eadd9a1d59c59dd40675b142eae480763f6f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87726045"
---
# <a name="set-the-properties-of-the-integration-services-service"></a>Festlegen der Eigenschaften des Integration Services-Diensts
    
> [!IMPORTANT]  
>  In diesem Thema wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
 Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst überwacht und verwaltet Pakete in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Bei der erstmaligen Installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] von wird der-Dienst gestartet, und der Starttyp des Dienstanbieter wird auf automatisch festgelegt.  
  
 Nach der Installation des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts können Sie die Eigenschaften des Dienstes entweder mit dem SQL Server-Konfigurations-Manager oder mit dem MMC-Snap-In „Dienste“ festlegen.  
  
 Zur Konfiguration anderer wichtiger Funktionen des Dienstes, wie die Verzeichnisse für die Speicherung und Verwaltung von Paketen, müssen Sie die Konfigurationsdatei des Dienstes ändern. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md).  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a>So legen Sie Eigenschaften des Integration Services-Dienstes mit dem SQL Server-Konfigurations-Manager fest  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, **Microsoft SQL Server**, **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Suchen Sie im **SQL Server-Konfigurations-Manager** -Snap-In in der Diensteliste nach **SQL Server Integration Services** , klicken Sie mit der rechten Maustaste auf **SQL Server Integration Services**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Im Dialogfeld **Eigenschaften von SQL Server Integration Services** können Sie folgende Schritte ausführen:  
  
    -   Klicken Sie auf die Registerkarte **Anmelden** , um die Anmeldeinformationen, wie z. B. den Kontonamen, anzuzeigen.  
  
    -   Klicken Sie auf die Registerkarte **Dienst** , um Informationen zum Dienst, wie z. B. den Namen des Hostcomputers, anzuzeigen und den Startmodus des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienstes anzugeben.  
  
        > [!NOTE]  
        >  Die Registerkarte **Erweitert** enthält keine Informationen zum [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie im Menü **Datei** auf **Beenden** , um das **SQL Server-Konfigurations-Manager** -Snap-In zu schließen.  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a>So legen Sie die Eigenschaften des Integration Services-Diensts mit Diensten fest  
  
1.  Wenn Sie die klassische Ansicht verwenden, klicken Sie in der **Systemsteuerung**auf **Verwaltung**. Wenn Sie die Kategorieansicht verwenden, klicken Sie auf **Leistung und Wartung** und dann auf **Verwaltung**.  
  
2.  Klicken Sie auf **Dienste**.  
  
3.  Suchen Sie im Snap-In **Dienste** in der Diensteliste **SQL Server Integration Services** , klicken Sie mit der rechten Maustaste auf **SQL Server Integration Services**, und klicken Sie anschließend auf **Eigenschaften**.  
  
4.  Im Dialogfeld **Eigenschaften von SQL Server Integration Services** können Sie folgende Schritte durchführen:  
  
    -   Klicken Sie auf die Registerkarte **Allgemein** . Um den Dienst zu aktivieren, wählen Sie entweder den manuellen oder automatischen Starttyp aus. Um den Dienst zu deaktivieren, wählen Sie im Feld **Starttyp** die Option "Deaktivieren" aus. Die Auswahl von "Deaktivieren" führt nicht zum Beenden des Dienstes, falls er gerade ausgeführt wird.  
  
         Wenn der Dienst bereits aktiviert ist, können Sie auf **Beenden** klicken, um den Dienst zu beenden, oder Sie können auf **Starten** klicken, um den Dienst zu starten.  
  
    -   Klicken Sie auf die Registerkarte **Anmelden** , um die Anmeldeinformationen anzuzeigen oder zu bearbeiten.  
  
    -   Klicken Sie auf die Registerkarte **Wiederherstellung** , um die Standardreaktionen des Computers bei Dienstfehlern anzuzeigen. Diese Optionen können Sie entsprechend Ihrer Umgebung anpassen.  
  
    -   Klicken Sie auf die **Abhängigkeiten** -Registerkarte, um eine Liste der abhängigen Dienste anzuzeigen. Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst weist keine Abhängigkeiten auf.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Wenn als Starttyp „Manuell“ oder „Automatisch“ ausgewählt wurde, können Sie optional mit der rechten Maustaste auf **SQL Server Integration Services** klicken und anschließend auf **Starten, Beenden oder Neu starten**klicken.  
  
7.  Klicken Sie im Menü **Datei** auf **Beenden** , um das Snap-In **Dienste** zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten des Integration Services-Diensts](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
