---
title: Editor für den Task Datenbanken übertragen (Seite Datenbanken) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df4452e28a32463a7825e9c64cfd053f98c53ee8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694642"
---
# <a name="transfer-database-task-editor-databases-page"></a>Editor für den Task Datenbanken übertragen (Seite Datenbanken)
  Verwenden Sie die Seite **Datenbanken** des Dialogfelds **Editor für den Task Datenbanken übertragen** , um die Eigenschaften für die im Task Datenbanken übertragen verwendeten Quell- und Zieldatenbanken anzugeben. Der Task Datenbanken übertragen kopiert oder verschiebt eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank zwischen zwei Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dieser Task kann auch verwendet werden, um eine Datenbank innerhalb desselben Servers zu kopieren. Weitere Informationen zu diesem Task finden Sie unter [Datenbanken übertragen (Task)](control-flow/transfer-database-task.md).  
  
## <a name="options"></a>Tastatur  
 **SourceConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<New connection...>** , um eine neue Verbindung mit dem Quellserver zu erstellen.  
  
 **DestinationConnection**  
 Wählen Sie in der Liste einen SMO-Verbindungs-Manager aus, oder klicken Sie auf **\<New connection...>** , um eine neue Verbindung mit dem Zielserver zu erstellen.  
  
 **DestinationDatabaseName**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank auf dem Zielserver an.  
  
 Um dieses Feld automatisch mit dem Namen der Quelldatenbank aufzufüllen, geben Sie zuerst die **SourceConnection** (Quellverbindung) und den **SourceDatabaseName** (Quelldatenbanknamen) an.  
  
 Um die Datenbank auf dem Zielserver umzubenennen, geben Sie in diesem Feld den neuen Namen an.  
  
 **DestinationDatabaseFiles**  
 Gibt die Namen und Speicherorte der Datenbankdateien auf dem Zielserver an.  
  
 Um dieses Feld automatisch mit den Namen und Speicherorten der Quelldatenbankdateien aufzufüllen, geben Sie zuerst die **SourceConnection**(Quellverbindung), den **SourceDatabaseName**(Quelldatenbanknamen) und die **SourceDatabaseFiles** (Quelldatenbankdateien) an.  
  
 Um die Datenbankdateien umzubenennen oder neue Speicherorte auf dem Zielserver anzugeben, tragen Sie in diesem Feld die Quelldatenbankinformationen ein und klicken dann auf die Schaltfläche zum Durchsuchen. Bearbeiten Sie im Dialogfeld **Zieldatenbankdateien** die Einträge für **Zieldatei**, **Zielordner**oder **Netzwerkdateifreigabe**.  
  
> [!NOTE]  
>  Wenn Sie die Datenbankdateien über die Schaltfläche zum Durchsuchen auswählen, wird der Dateispeicherort in der Notation des lokalen Laufwerks angegeben, z.B. C:\\. Diese müssen Sie durch die Notation der Netzwerkfreigabe ersetzen, einschließlich des Computernamens und des Freigabenamens. Wenn die standardmäßige Administrationsfreigabe verwendet wird, müssen Sie die $-Notation verwenden und über Administratorzugriff auf die Freigabe verfügen.  
  
 **DestinationOverwrite**  
 Geben Sie an, ob die Datenbank auf dem Zielserver überschrieben werden kann.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**True**|Zielserverdatenbank überschreiben.|  
|**False**|Zielserverdatenbank nicht überschreiben.|  
  
> [!CAUTION]  
>  Die Daten in der Zielserverdatenbank werden überschrieben, wenn Sie für **DestinationOverwrite** **True**angeben. Dies kann zu Datenverlusten führen. Um dies zu vermeiden, sollten Sie die Zielserverdatenbank an einem anderen Speicherort sichern, bevor Sie den Task Datenbanken übertragen ausführen.  
  
 **Aktion**  
 Gibt an, ob der Task die Datenbank auf den Zielserver kopiert ( **Kopieren** ) oder verschiebt ( **Verschieben** ).  
  
 **Methode**  
 Gibt an, ob der Task ausgeführt wird, während sich die Datenbank auf dem Quellserver im Online- oder Offlinemodus befindet.  
  
 Um eine Datenbank im Offlinemodus zu übertragen, muss der Benutzer, der das Paket ausführt, ein Mitglied der festen Serverrolle **sysadmin** sein.  
  
 Um eine Datenbank im Onlinemodus zu übertragen, muss der Benutzer, der das Paket ausführt, ein Mitglied der festen Serverrolle **sysadmin** oder der Besitzer (**dbo**) der ausgewählten Datenbank sein.  
  
 **SourceDatabaseName**  
 Wählen Sie den Namen der zu kopierenden oder zu verschiebenden Datenbank aus.  
  
 **SourceDatabaseFiles**  
 Klicken Sie auf die Schaltfläche zum Durchsuchen, um die Datenbankdateien auszuwählen.  
  
 **ReattachSourceDatabase**  
 Geben Sie an, ob der Task versuchen soll, die Quelldatenbank wieder anzufügen, falls ein Fehler auftritt.  
  
 Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**True**|Quelldatenbank wieder anfügen.|  
|**False**|Quelldatenbank nicht wieder anfügen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services-Tasks](control-flow/integration-services-tasks.md)   
 [Editor für den Task Datenbanken übertragen &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [SMO-Verbindungs-Manager](connection-manager/smo-connection-manager.md)  
  
  
