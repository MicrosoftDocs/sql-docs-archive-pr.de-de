---
title: Überwachungstransformation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695873"
---
# <a name="audit-transformation"></a>Überwachungstransformation
  Mithilfe der Überwachungstransformation werden in den Datenfluss eines Pakets Daten zur Umgebung, in der das Paket ausgeführt wird, eingeschlossen. Dem Datenfluss kann z. B. der Name des Pakets, Computers und Operators hinzugefügt werden. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enthält Systemvariablen, die diese Informationen bereitstellen.  
  
## <a name="system-variables"></a>Systemvariablen  
 In der folgenden Tabelle sind die Systemvariablen beschrieben, die von der Überwachungstransformation verwendet werden können.  
  
|Systemvariable|Index|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|0|Der GUID, der die Ausführungsinstanz des Pakets identifiziert.|  
|`PackageID`|1|Der eindeutige Bezeichner des Pakets.|  
|`PackageName`|2|Der Paketname.|  
|`VersionID`|3|Die Paketversion.|  
|`ExecutionStartTime`|4|Der Zeitpunkt, zu dem das Paket gestartet wurde.|  
|`MachineName`|5|Der Computername.|  
|`UserName`|6|Der Anmeldename der Person, die das Paket gestartet hat.|  
|`TaskName`|7|Der Name des Datenflusstasks, dem die Überwachungstransformation zugeordnet ist.|  
|**TaskId**|8|Der eindeutige Bezeichner des Datenflusstasks.|  
  
## <a name="configuration-of-the-audit-transformation"></a>Konfiguration der Überwachungstransformation  
 Zum Konfigurieren der Überwachungstransformation stellen Sie den Namen einer neuen Ausgabespalte bereit, die der Transformationsausgabe hinzugefügt werden soll, und ordnen dann der Ausgabespalte die Systemvariable zu. Eine einzelne Systemvariable kann mehreren Spalten zugeordnet werden.  
  
 Diese Transformation weist je eine Eingabe und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Überwachung** festlegen können, finden Sie unter [Audit Transformation Editor](../../audit-transformation-editor.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
  
