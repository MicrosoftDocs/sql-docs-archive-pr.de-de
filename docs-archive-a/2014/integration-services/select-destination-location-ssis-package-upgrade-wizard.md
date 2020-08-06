---
title: Ziel Speicherort auswählen (SSIS-Paket Upgrade-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9411157434c3dbb9fb033f7b63b5e6041fd8f75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622771"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a>Zielspeicherort auswählen (SSIS Paketupgrade-Assistent)
  Auf der Seite **Zielspeicherort auswählen** können Sie das Ziel angeben, an dem die aktualisierten Pakete gespeichert werden sollen.  
  
> [!NOTE]  
>  Diese Seite ist nur verfügbar, wenn Sie den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Paketupgrade-Assistenten in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder an der Eingabeaufforderung ausführen.  
  
 **So führen Sie den SSIS Paketupgrade-Assistenten aus**  
  
-   [Aktualisieren von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Statische Optionen  
 **An Quellspeicherort speichern**  
 Speichert die aktualisierten Pakete an demselben Speicherort, der auf der Seite **Quellspeicherort auswählen** des Assistenten festgelegt wurde.  
  
 Wenn die ursprünglichen Pakete im Dateisystem gespeichert sind und der Assistent diese Pakete sichern soll, wählen Sie die Option **An Quellspeicherort speichern** aus. Weitere Informationen finden Sie unter [Aktualisieren von Integration Services-Paketen mit dem SSIS Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
 **Neuen Zielspeicherort auswählen**  
 Speichert die aktualisierten Pakete an dem Zielspeicherort, der auf dieser Seite angegeben ist.  
  
 **Paketquelle**  
 Gibt an, wo die Upgradepakete gespeichert werden sollen. Für diese Option sind die in der folgenden Tabelle aufgeführten Werte verfügbar.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Dateisystem**|Gibt an, dass die aktualisierten Pakete in einem Ordner auf dem lokalen Computer gespeichert werden sollen.|  
|**SSIS-Paketspeicher**|Gibt an, dass die aktualisierten Pakete im Integration Services-Paketspeicher gespeichert werden sollen. Der Paketspeicher besteht aus dem Satz von Dateisystemordnern, die vom Integration Services-Dienst verwaltet werden. Weitere Informationen finden Sie unter [Paketverwaltung &#40;SSIS-Dienst&#41;](service/package-management-ssis-service.md).<br /><br /> Bei Auswahl dieses Werts werden die entsprechenden dynamischen Optionen **Paketquelle** angezeigt.|  
|**Microsoft SQL Server**|Gibt an, dass die aktualisierten Pakete in einer vorhandenen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]gespeichert werden sollen.<br /><br /> Bei Auswahl dieses Werts werden die entsprechenden dynamischen Optionen **Paketquelle** angezeigt.|  
  
 **Ordner**  
 Geben Sie den Namen eines Ordners ein, in dem die aktualisierten Pakete gespeichert werden, oder klicken Sie auf **Durchsuchen** , und suchen Sie den Ordner.  
  
 **Durchsuchen**  
 Suchen Sie nach dem Ordner, in dem die aktualisierten Pakete gespeichert werden sollen.  
  
## <a name="package-source-dynamic-options"></a>Dynamische Paketquellenoptionen  
  
### <a name="package-source--ssis-package-store"></a>Paketquelle = SSIS-Paketspeicher  
 **Server**  
 Geben Sie den Namen des Servers ein, auf dem die Upgradepakete gespeichert werden sollen, oder wählen Sie einen Server aus der Liste aus.  
  
### <a name="package-source--microsoft-sql-server"></a>Paketquelle = Microsoft SQL Server  
 **Server**  
 Geben Sie den Namen des Servers ein, auf dem die Upgradepakete gespeichert werden sollen, oder wählen Sie diesen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Wählen Sie diese Option aus, um für die Herstellung einer Verbindung mit dem Server die Windows-Authentifizierung zu verwenden.  
  
 **SQL Server Authentifizierung verwenden**  
 Wählen Sie diese Option aus, um für die Herstellung einer Verbindung mit dem Server die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung zu verwenden. Wenn Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwenden, müssen Sie einen Benutzernamen und ein Kennwort angeben.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen ein, der bei der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwendet werden soll, um eine Verbindung mit dem Server herzustellen.  
  
 **Kennwort**  
 Geben Sie das Kennwort ein, das bei der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung verwendet werden soll, um eine Verbindung mit dem Server herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Integration Services-Paketen](install-windows/upgrade-integration-services-packages.md)  
  
  
