---
title: Aktivieren der Paket Protokollierung in SQL Server Data Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618813"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a>Aktivieren der Paketprotokollierung in SQL Server Data Tools
  In diesem Verfahren wird beschrieben, wie einem Paket Protokolle hinzugefügt werden, die Protokollierung auf Paketebene konfiguriert wird und die Protokollierungskonfiguration in eine XML-Datei gespeichert wird. Sie können Protokolle nur auf der Paketebene hinzufügen, das Paket muss jedoch keine Protokollierung durchführen, um die Protokollierung in den Containern zu ermöglichen, die im Paket enthalten sind.  
  
> [!IMPORTANT]  
>  Wenn Sie das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen, überschreibt der Protokolliergrad, den Sie für die Paketausführung festgelegt haben, die Paketprotokollierung, die Sie mit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]konfigurieren.  
  
 Die Container im Paket verwenden standardmäßig dieselbe Protokollierungskonfiguration wie der übergeordnete Container. Weitere Informationen zum Festlegen der Protokollierungsoptionen für einzelne Container finden Sie unter [Konfigurieren der Protokollierung mithilfe einer gespeicherten Konfigurationsdatei](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).  
  
### <a name="to-enable-logging-in-a-package"></a>So aktivieren Sie die Protokollierung in einem Paket  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Menü **SSIS** auf **Protokollierung**.  
  
3.  Wählen Sie einen Protokollanbieter in der Liste **Anbietertyp** aus, und klicken Sie dann auf **Hinzufügen**.  
  
4.  Wählen Sie in der Spalte **Konfiguration** einen Verbindungs-Manager aus, oder klicken Sie auf **\<New connection>** , um einen neuen Verbindungs-Manager des entsprechenden Typs für den Protokollanbieter zu erstellen. Verwenden Sie je nach ausgewähltem Anbieter einen der folgenden Verbindungs-Manager.  
  
    -   Verwenden Sie für Textdateien einen Dateiverbindungs-Manager. Weitere Informationen finden Sie unter [File Connection Manager](connection-manager/file-connection-manager.md)  
  
    -   Verwenden Sie für [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]einen Dateiverbindungs-Manager.  
  
    -   Verwenden Sie für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]einen OLE DB-Verbindungs-Manager. Weitere Informationen finden Sie unter [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).  
  
    -   Führen Sie für das Windows-Ereignisprotokoll keine Aktion durch. [!INCLUDE[ssIS](../includes/ssis-md.md)] erstellt das Protokoll automatisch.  
  
    -   Verwenden Sie für XML-Dateien einen Dateiverbindungs-Manager.  
  
5.  Wiederholen Sie die Schritte 3 und 4 für jedes im Paket zu verwendende Protokoll.  
  
    > [!NOTE]  
    >  Ein Paket kann mehrere Protokolle pro Typ verwenden.  
  
6.  Aktivieren Sie wahlweise das Kontrollkästchen für das Paket, wählen Sie die für die Paketprotokollierung zu verwendenden Protokolle aus, und klicken Sie dann auf die Registerkarte **Details** .  
  
7.  Wählen Sie auf der Registerkarte **Details** die Option **Ereignisse** , um alle Protokolleinträge zu protokollieren, oder löschen Sie **Ereignisse** , um einzelne Ereignisse auszuwählen.  
  
8.  Klicken Sie wahlweise auf **Erweitert** , um die zu protokollierenden Informationen anzugeben.  
  
    > [!NOTE]  
    >  Standardmäßig werden alle Informationen protokolliert.  
  
9. Klicken Sie auf der Registerkarte **Details** auf **Speichern**. Das Dialogfeld **Speichern unter** wird angezeigt. Suchen Sie den Ordner, in dem Sie die Protokollierungskonfiguration speichern möchten, geben Sie einen Dateinamen für die neue Protokollkonfiguration ein, und klicken Sie dann auf **Speichern**.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Protokollierung](performance/integration-services-ssis-logging.md)   
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
