---
title: Task „Fehlermeldungen übertragen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952acc28a79fef7e7351c97400e05bc7ba5b9243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607921"
---
# <a name="transfer-error-messages-task"></a>Fehlermeldungen übertragen (Task)
  Der Task „Fehlermeldungen übertragen“ überträgt eine oder mehrere benutzerdefinierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlermeldungen zwischen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Benutzerdefinierte Meldungen sind Meldungen mit einem Bezeichner gleich oder größer als 50000. Meldungen mit einem Bezeichner kleiner als 50000 sind Systemfehlermeldungen und können nicht mithilfe des Tasks "Fehlermeldungen übertragen" übertragen werden.  
  
 Der Task Fehlermeldungen übertragen kann so konfiguriert werden, dass alle Fehlermeldungen oder nur die angegebenen Fehlermeldungen übertragen werden. Benutzerdefinierte Fehlermeldungen stehen möglicherweise in einer Vielzahl von verschiedenen Sprachen zur Verfügung, und der Task kann so konfiguriert werden, dass nur Meldungen in ausgewählten Sprachen zur Verfügung stehen. Auf dem Zielserver muss eine Version der Meldung in us_english vorhanden sein, die Codepage 1033 verwendet, bevor Sie andere Sprachversionen auf diesen Server übertragen können.  
  
 Die sysmessages-Tabelle in der master-Datenbank enthält alle Fehlermeldungen, sowohl Systemfehlermeldungen als auch benutzerdefinierte Fehlermeldungen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden.  
  
 Die zu übertragenden benutzerdefinierten Meldungen sind auf dem Ziel möglicherweise schon vorhanden. Eine Fehlermeldung wird als doppelte Fehlermeldung definiert, wenn der Bezeichner und die Sprache identisch sind. Es gibt folgende Möglichkeiten, um den Task "Fehlermeldungen übertragen" zur Verarbeitung bereits vorhandener Fehlermeldungen zu konfigurieren:  
  
-   Vorhandene Fehlermeldungen überschreiben.  
  
-   Der Task erzeugt einen Fehler, wenn doppelte Meldungen vorhanden sind.  
  
-   Doppelte Fehlermeldungen auslassen.  
  
 Zur Laufzeit stellt der Task "Fehlermeldungen übertragen" mithilfe eines oder zweier SMO-Verbindungs-Manager eine Verbindung mit dem Quell- und Zielserver her. Der SMO-Verbindungs-Manager wird unabhängig vom Task "Fehlermeldungen übertragen" konfiguriert, und im Task "Fehlermeldungen übertragen" wird dann darauf verwiesen. Im SMO-Verbindungs-Manager wird der Server sowie der für den Zugriff auf den Server zu verwendende Authentifizierungsmodus angegeben. Weitere Informationen finden Sie unter [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
 Der Task "Fehlermeldungen übertragen" unterstützt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Quelle und ein Ziel. Es gibt keinerlei Beschränkungen, welche Version Sie als Quelle oder Ziel verwenden.  
  
## <a name="events"></a>Events  
 Der Task löst ein Informationsereignis aus, das die Anzahl der übertragenen Fehlermeldungen meldet.  
  
 Der Task "Fehlermeldungen übertragen" meldet keinen schrittweisen Fortschritt der Fehlermeldungsübertragung; er meldet nur 0 % und 100 % der Ausführung.  
  
## <a name="execution-value"></a>Ausführungswert  
 Der in der `ExecutionValue`-Eigenschaft des Tasks definierte Ausführungswert gibt die Anzahl der zu übertragenden Fehlermeldungen zurück. Indem der `ExecValueVariable`-Eigenschaft des Tasks "Fehlermeldungen übertragen" eine benutzerdefinierte Variable zugewiesen wird, können Informationen über die Fehlermeldungsübertragung anderen Objekten im Paket zur Verfügung gestellt werden. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md) und [Verwenden von Variablen in Paketen](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Protokolleinträge  
 Der Task "Fehlermeldungen übertragen" enthält die folgenden benutzerdefinierten Protokolleinträge:  
  
-   TransferErrorMessagesTaskStartTransferringObjects   Dieser Protokolleintrag meldet, dass die Übertragung begonnen hat. Der Protokolleintrag enthält die Startzeit.  
  
-   TransferErrorMessagesTaskFinishedTransferringObjects   Dieser Protokolleintrag meldet das Beenden der Übertragung. Der Protokolleintrag enthält die Beendigungszeit.  
  
 Zusätzlich meldet ein Protokolleintrag für das `OnInformation`-Ereignis die Anzahl der übertragenen Fehlermeldungen. Für jede Fehlermeldung auf dem Ziel, die überschrieben wird, wird außerdem ein Protokolleintrag für das `OnWarning event` geschrieben.  
  
## <a name="security-and-permissions"></a>Sicherheit und Berechtigungen  
 Um neue Fehlermeldungen zu erstellen, muss der Benutzer, von dem das Paket ausgeführt wird, auf dem Zielserver Mitglied der sysadmin- oder serveradmin-Serverrolle sein.  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a>Konfiguration des Tasks "Fehlermeldungen übertragen"  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task „Fehlermeldungen übertragen“ &#40;Seite „Allgemein“&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Editor für den Task „Fehlermeldungen übertragen“ &#40;Seite „Nachrichten“&#41;](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um Informationen zum programmgesteuerten Festlegen dieser Eigenschaften anzuzeigen:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
