---
title: Skripttask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607933"
---
# <a name="script-task"></a>Skripttask
  Der Skripttask stellt Code zum Ausführen von Funktionen bereit, die in den integrierten Tasks und Transformationen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nicht verfügbar sind. Der Skripttask kann auch Funktionen in einem einzigen Skript zusammenfassen, statt mehrere Tasks und Transformationen zu verwenden. Sie verwenden den Skripttask für einmalige Aktionen in einem Paket (einmalig pro aufgezähltem Objekt), anstatt diese einmalig pro Datenzeile auszuführen.  
  
 Der Skripttask kann für folgende Zwecke verwendet werden:  
  
-   Zugreifen auf Daten mithilfe anderer Technologien, die nicht von integrierten Verbindungstypen unterstützt werden. Beispielsweise kann ein Skript mithilfe von Active Directory Service Interfaces (ADSI) auf Benutzernamen von Active Directory zugreifen und diese extrahieren.  
  
-   Erstellen eines paketspezifischen Leistungsindikators. Beispielsweise kann ein Skript einen Leistungsindikator erstellen, der aktualisiert wird, während ein komplexer Task oder ein Task mit einem geringen Leistungsverhalten ausgeführt wird.  
  
-   Identifizieren, ob angegebene Dateien leer sind bzw. wie viele Zeilen sie enthalten, und deren Auswirkungen auf die Ablaufsteuerung in einem Paket auf Basis dieser Informationen. Enthält eine Datei beispielsweise 0 Zeilen, wird der Wert einer Variablen auf 0 festgelegt, und eine Rangfolgeneinschränkung, die den Wert auswertet, verhindert das Kopieren der Datei mit einem Dateisystemtask.  
  
 Wenn Sie das Skript verwenden müssen, um die gleichen Aktionen für jede Datenzeile einer Gruppe auszuführen, verwenden Sie anstelle des Skripttasks die Skriptkomponente. Eine Skriptkomponente wird beispielsweise verwendet, wenn Sie auswerten möchten, ob eine Portogebühr und das Auslassen von Datenzeilen mit extrem hohen oder niedrigen Beträgen angemessen sind. Weitere Informationen finden Sie unter [Script Component](../data-flow/transformations/script-component.md).  
  
 Falls ein Skript von mehreren Paketen verwendet wird, sollten Sie einen benutzerdefinierten Task erstellen, statt den Skripttask zu verwenden. Weitere Informationen finden Sie unter [Entwickeln eines benutzerdefinierten Tasks](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
 Nachdem Sie entschieden haben, dass die Skriptkomponente für Ihr Paket geeignet ist, müssen Sie das Skript entwickeln, das vom Task verwendet wird, und den Task konfigurieren.  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a>Erstellen und Ausführen des Skripts, das vom Task verwendet wird  
 Der Skripttask verwendet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Tools für Anwendungen (VSTA) als Umgebung zum Erstellen der Skripts und der Engine, mit der die Skripts ausgeführt werden.  
  
 VSTA enthält alle Standardfunktionen der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Umgebung, z.B. den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Editor mit Farbcodierung, IntelliSense und den **Objekt-Explorer**. VSTA verwendet zudem den Debugger, der auch von anderen [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Entwicklungstools verwendet wird. Breakpoints im Skript sind vollständig mit Breakpoints in Tasks und Containern von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] kompatibel. VSTA unterstützt die Programmiersprachen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Zum Ausführen eines Skripts muss VSTA auf dem Computer installiert sein, auf dem das Paket ausgeführt wird. Wenn das Paket ausgeführt wird, lädt der Task die Skript-Engine und führt das Skript aus. Sie können auf externe .NET-Assemblys zugreifen, indem Sie Verweise auf die Assemblys im Projekt hinzufügen.  
  
> [!NOTE]  
>  Anders als in früheren Versionen, in denen Sie angeben konnten, ob die Skripts vorkompiliert sind, werden in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] und nachfolgenden Versionen alle Skripts vorkompiliert. Wenn ein Skript vorkompiliert ist, wird die Sprach-Engine zur Laufzeit nicht geladen, und das Paket wird schneller ausgeführt. Kompilierte binäre Dateien belegen jedoch erheblich mehr Speicherplatz.  
  
## <a name="configuring-the-script-task"></a>Konfigurieren des Skripttasks  
 Es gibt folgende Möglichkeiten, um den Skripttask zu konfigurieren:  
  
-   Stellen Sie das benutzerdefinierte Skript bereit, das von dem Task ausgeführt wird.  
  
-   Geben Sie die Methode im VSTA-Projekt an, die die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Laufzeit als Einstiegspunkt in den Code des Skripttasks aufruft.  
  
-   Geben Sie die Skriptsprache an.  
  
-   Geben Sie optional Listen mit schreibgeschützten und Lese-/Schreibvariablen für die Verwendung im Skript an.  
  
 Diese Eigenschaften können Sie mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
### <a name="configuring-the-script-task-in-the-designer"></a>Konfigurieren des Skripttasks im Designer  
 In der folgenden Tabelle wird das `ScriptTaskLogEntry`-Ereignis beschrieben, das für den Skripttask protokolliert werden kann. Das `ScriptTaskLogEntry` Ereignis wird für die Protokollierung auf der Registerkarte **Details** des Dialog Felds **SSIS-Protokolle konfigurieren** ausgewählt. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) und [Benutzerdefinierte Meldungen für die Protokollierung](../custom-messages-for-logging.md).  
  
|Protokolleintrag|BESCHREIBUNG|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|Gibt die Ergebnisse des Implementierens der Protokollierung innerhalb des Skripts an. Der Task schreibt für jeden Aufruf der `Log`-Methode des `Dts`-Objekts einen Protokolleintrag. Der Task schreibt diese Einträge, wenn der Code ausgeführt wird. Weitere Informationen finden Sie unter [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).|  
  
 Klicken Sie auf die folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Skripttask-Editor &#40;Seite „Allgemein“&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Skripttask-Editor &#40;Seite Skript&#41;](../script-task-editor-script-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer finden Sie im folgenden Thema:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a>Programmgesteuertes Konfigurieren des Skripttasks  
 Weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie im folgenden Thema:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Technischer Artikel [Vorgehensweise: Senden von E-Mails mit Zustellungsbenachrichtigung in C#](https://go.microsoft.com/fwlink/?LinkId=237625)(Gewusst wie: Senden von E-Mails mit Zustellungsbenachrichtigung in C#) auf shareourideas.com  
  
  
