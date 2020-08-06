---
title: Editor für den Task Paket ausführen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618793"
---
# <a name="execute-package-task-editor"></a>Editor für den Task 'Paket ausführen'
  Mit dem Editor für den Task "Paket ausführen" können Sie Task "Paket ausführen" konfigurieren. Der Task Paket ausführen erweitert die Unternehmensfunktionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , indem Paketen das Ausführen anderer Pakete als Teil eines Workflows ermöglicht wird.  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Editors für den Task "Paket ausführen"](#open)  
  
-   [Festlegen der Optionen auf der Seite „Allgemein“](#general)  
  
-   [Festlegen der Optionen auf der Seite "Paket"](#package)  
  
-   [Festlegen der Optionen auf der Seite "Parameterbindungen"](#parameter)  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> Öffnen des Editors für den Task "Paket ausführen"  
  
1.  Öffnen Sie in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projekt, das einen Task „Paket ausführen“ enthält.  
  
2.  Klicken Sie im SSIS-Designer mit der rechten Maustaste auf den Task, und klicken Sie dann auf **Bearbeiten**.  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> Festlegen der Optionen auf der Seite „Allgemein“  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Task "Paket ausführen" an. Dieser Name wird im Tasksymbol als Bezeichnung verwendet.  
  
> [!NOTE]  
>  Tasknamen müssen innerhalb eines Pakets eindeutig sein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Tasks "Paket ausführen" ein.  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> Festlegen der Optionen auf der Seite "Paket"  
 **ReferenceType**  
 Wählen Sie **Projektverweis** für untergeordnete Pakete im Projekt aus. Wählen Sie **Externer Verweis** für untergeordnete Pakete aus, die sich außerhalb des Pakets befinden.  
  
> [!NOTE]  
>  Die Option **ReferenceType** ist schreibgeschützt und auf **Externer Verweis** festgelegt, wenn das Projekt, das das Paket enthält, nicht in das Projektbereitstellungsmodell konvertiert wurde. Weitere Informationen zur Konvertierung finden Sie unter [Bereitstellen von Projekten auf dem Integration Services-Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 **Kennwort**  
 Wenn das untergeordnete Paket kennwortgeschützt ist, stellen Sie das Kennwort für das untergeordnete Paket bereit, oder klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten (...), und erstellen Sie ein neues Kennwort für das untergeordnete Paket.  
  
 `ExecuteOutOfProcess`  
 Geben Sie an, ob das untergeordnete Paket im Prozess des übergeordneten Pakets oder in einem separaten Prozess ausgeführt wird. Standardmäßig ist die executeouesfprocess-Eigenschaft des Tasks "Paket ausführen" auf festgelegt `False` , und das untergeordnete Paket wird im selben Prozess wie das übergeordnete Paket ausgeführt. Wenn Sie diese Eigenschaft auf `true` festlegen, wird das untergeordnete Paket in einem separaten Prozess ausgeführt. Dadurch kann sich der Start des untergeordneten Pakets verlangsamen. Wenn die Eigenschaft auf `true` festgelegt wurde, ist außerdem das Debuggen des Pakets in einer Installation, die nur die Tools enthält, nicht möglich; das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Produkt muss von Ihnen installiert werden. Weitere Informationen finden Sie unter [Installieren von Integration Services](install-windows/install-integration-services.md).  
  
### <a name="referencetype-dynamic-options"></a>Dynamische Optionen für ReferenceType  
  
#### <a name="referencetype--external-reference"></a>ReferenceType = Externer Verweis  
 **Location**  
 Wählen Sie den Speicherort des untergeordneten Pakets aus. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**SQL Server**|Legt den Speicherort als Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]fest.|  
|**Dateisystem**|Legen Sie als Speicherort das Dateisystem fest.|  
  
 **Connection**  
 Wählen Sie den Typ des Speicherorts für das untergeordnete Paket aus.  
  
 **PackageNameReadOnly**  
 Zeigt den Paketnamen an.  
  
#### <a name="referencetype--project-reference"></a>ReferenceType = Projektverweis  
 **PackageNameFromProjectReference**  
 Wählen Sie ein im Projekt enthaltenes Paket als untergeordnetes Paket aus.  
  
### <a name="location-dynamic-options"></a>Dynamische Optionen für Location  
  
#### <a name="location--sql-server"></a>Location = SQL Server  
 **Connection**  
 Wählen Sie einen OLE DB-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**New connection...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md), [OLE DB-Verbindungs-Manager konfigurieren](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **PackageName**  
 Geben Sie den Namen des untergeordneten Pakets an, oder klicken Sie auf die Schaltfläche mit den drei Auslassungspunkten (...), um nach dem Paket zu suchen.  
  
#### <a name="location--file-system"></a>Location = File system  
 **Connection**  
 Wählen Sie einen Dateiverbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**New connection...**>, um einen neuen Verbindungs-Manager zu erstellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
 **PackageNameReadOnly**  
 Zeigt den Paketnamen an.  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> Festlegen der Optionen auf der Seite "Parameterbindungen"  
 Sie können Werte aus dem übergeordneten Paket oder dem Projekt an das untergeordnete Paket übergeben. Das Projekt muss das Projektbereitstellungsmodell verwenden, und das untergeordnete Paket muss im gleichen Projekt enthalten sein wie das übergeordnete Paket.  
  
 Weitere Informationen zum Konvertieren eines Projekts in das Projektbereitstellungsmodell finden Sie unter [Bereitstellen von Projekten auf dem Integration Services-Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).  
  
 **Untergeordneter Paketparameter**  
 Geben Sie einen Namen für den untergeordneten Paketparameter ein, oder wählen Sie diesen aus.  
  
 **Bindungsparameter oder Variable**  
 Wählen Sie den Parameter oder die Variable mit dem Wert aus, den Sie an das untergeordnete Paket übergeben möchten.  
  
 **Add (Hinzufügen)**  
 Klicken Sie, um einen Parameter oder eine Variable einem untergeordneten Paketparameter zuzuordnen.  
  
 **Remove**  
 Klicken Sie, um eine Zuordnung zwischen einem Parameter oder einer Variable und einem untergeordneten Paketparameter zu entfernen.  
  
  
