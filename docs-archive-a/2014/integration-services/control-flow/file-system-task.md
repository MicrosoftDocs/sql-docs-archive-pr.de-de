---
title: Task „Dateisystem“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce3d31ceb720704fb61c33043a4c7319607caff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607949"
---
# <a name="file-system-task"></a>Task Dateisystem
  Der Task Dateisystem führt Operationen für Dateien und Verzeichnisse im Dateisystem aus. Beispielsweise kann ein Paket mit dem Task Dateisystem Verzeichnisse und Dateien erstellen, verschieben oder löschen. Darüber hinaus können Sie mit dem Task Dateisystem Attribute für Dateien und Verzeichnisse festlegen. Beispielsweise können mit dem Task Dateisystem Dateien als ausgeblendet oder schreibgeschützt festgelegt werden.  
  
 Für alle Operationen mit dem Task Dateisystem wird eine Quelle verwendet, wobei es sich um eine Datei oder ein Verzeichnis handeln kann. Beispiele für Quellen sind die Datei, die von dem Task kopiert wird, oder das Verzeichnis, das von dem Task gelöscht wird. Die Quelle kann mithilfe eines Dateiverbindungs-Managers angegeben werden, der auf das Verzeichnis oder die Datei verweist, oder durch Eingabe des Namens einer Variablen, die den Quellpfad enthält. Weitere Informationen finden Sie unter [File Connection Manager](../connection-manager/file-connection-manager.md) und [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
 Für die Vorgänge zum Kopieren und Verschieben von Dateien und Verzeichnissen und zum Umbenennen von Dateien wird ein Ziel und eine Quelle verwendet. Das Ziel wird mithilfe eines Dateiverbindungs-Managers oder einer Variablen angegeben. Vorgänge mit dem Task Dateisystem können so konfiguriert werden, dass Zieldateien und -verzeichnisse überschrieben werden dürfen. Der Vorgang, bei dem ein neues Verzeichnis erstellt wird, kann so konfiguriert werden, dass ein vorhandenes Verzeichnis verwendet wird. Dieses weist den angegebenen Namen auf, und es wird kein Fehler erzeugt, wenn das Verzeichnis bereits besteht.  
  
## <a name="predefined-file-system-operations"></a>Vordefinierte Dateisystemvorgänge  
 Der Task Dateisystem enthält vordefinierte Vorgänge. In der folgenden Tabelle werden diese Vorgänge beschrieben.  
  
|Vorgang|BESCHREIBUNG|  
|---------------|-----------------|  
|Verzeichnis kopieren|Kopiert einen Ordner zwischen Speicherorten.|  
|Datei kopieren|Kopiert eine Datei zwischen Speicherorten.|  
|Erstellen eines Verzeichnisses|Erstellt einen Ordner im angegebenen Speicherort.|  
|Verzeichnis löschen|Löscht einen Ordner im angegebenen Speicherort.|  
|Verzeichnisinhalt löschen|Löscht alle Dateien und Ordner in einem Ordner.|  
|Datei löschen|Löscht eine Datei im angegebenen Speicherort.|  
|Verzeichnis verschieben|Verschiebt einen Ordner zwischen Speicherorten.|  
|Datei verschieben|Verschiebt eine Datei zwischen Speicherorten.|  
|Datei umbenennen|Benennt eine Datei im angegebenen Speicherort um.|  
|Festlegen von Attributen|Legt Attribute für Dateien und Ordner fest. Zu den Attributen zählen Archive, Hidden, Normal, ReadOnly und System. Normalerweise sind keine Attribute angegeben, und die Kombination mit anderen Attributen ist nicht möglich. Alle anderen Attribute können in Kombination mit anderen Attributen verwendet werden.|  
  
 Der Task Dateisystem wird in einer einzelnen Datei oder in einem einzelnen Verzeichnis ausgeführt. Daher unterstützt dieser Task nicht die Verwendung von Platzhalterzeichen, um denselben Vorgang in mehreren Dateien auszuführen. Damit der Task Dateisystem einen Vorgang in mehreren Dateien oder Verzeichnissen wiederholt, platzieren Sie den Task Dateisystem in einem Foreach-Schleifencontainer, wie in den folgenden Schritten beschrieben.  
  
-   **Konfigurieren des Foreach-Schleifencontainers** Legen Sie auf der Seite **Auflistung** des Foreach-Schleifen-Editors den Enumerator auf **Foreach-Dateienumerator** fest, und geben Sie den Platzhalterausdruck als Enumeratorkonfiguration für **Dateien**an. Ordnen Sie auf der Seite **Variablenzuordnungen** des Foreach-Schleifen-Editors eine Variable zu, mit der die Dateinamen nacheinander an den Task Dateisystem übergeben werden.  
  
-   **Hinzufügen und Konfigurieren eines Tasks 'Dateisystem'** Fügen Sie dem Foreach-Schleifencontainer einen Task Dateisystem hinzu. Legen Sie auf der Seite **Allgemein** des Editors für den Task **Dateisystem** die Eigenschaft **SourceVariable** oder DestinationVariable auf die im Foreach-Schleifencontainer definierte Variable fest.  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a>Verfügbare benutzerdefinierte Protokolleinträge für den Task 'Dateisystem'  
 In der folgenden Tabelle wird der benutzerdefinierte Protokolleintrag für den Task "Dateisystem" beschrieben. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) und [Benutzerdefinierte Meldungen für die Protokollierung](../custom-messages-for-logging.md).  
  
|Protokolleintrag|BESCHREIBUNG|  
|---------------|-----------------|  
|`FileSystemOperation`|Berichtet den vom Task durchgeführten Vorgang. Der Protokolleintrag wird geschrieben, wenn der Dateisystemvorgang begonnen wird, und schließt Informationen über die Quelle und das Ziel ein.|  
  
## <a name="configuring-the-file-system-task"></a>Konfigurieren des Tasks Dateisystem  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf die folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task „Dateisystem“ &#40;Seite „Allgemein“&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer finden Sie im folgenden Thema:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
 Weitere Informationen zum programmgesteuert Festlegen dieser Eigenschaften finden Sie im folgenden Thema:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] schließt einen Task zum Herunterladen und Hochladen von Datendateien und zum Verwalten von Verzeichnissen auf Servern ein. Weitere Informationen finden Sie unter [FTP Task](ftp-task.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
