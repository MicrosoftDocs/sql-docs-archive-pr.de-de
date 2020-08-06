---
title: Ausführen von Windows PowerShell-Schritten in SQL Server-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8c100e2eaf1f9b706087bd991fbc268540c29a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617144"
---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a>Ausführen von Windows PowerShell-Schritten in SQL Server-Agent
  Führen Sie die SQL Server PowerShell-Skripts mithilfe des SQL Server-Agent nach Zeitplan aus.  
  
1.  **Vorbereitungen:**  [Einschränkungen](#LimitationsRestrictions)  
  
2.  **So führen Sie PowerShell in SQL Server Agent mit folgenden Auftragsschritten aus:**  [PowerShell-Auftragsschritt](#PShellJob), [Eingabeaufforderungs-Auftragsschritt](#CmdExecJob)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Es gibt mehrere Typen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Auftragsschritten. Jeder Typ ist einem Subsystem zugeordnet, das eine bestimmte Umgebung implementiert, wie eine Replikations-Agent- oder Eingabeaufforderungsumgebung. Sie können Windows PowerShell-Skripts schreiben und die Skripts dann mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent in Aufträge integrieren, die zu festgelegten Zeiten oder in Reaktion auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Ereignisse ausgeführt werden. Windows PowerShell-Skripts können mit entweder einem Eingabeaufforderungs-Auftragsschritt oder einem PowerShell-Auftragsschritt ausgeführt werden.  
  
1.  Verwenden Sie einen PowerShell-Auftragsschritt, damit das Subsystem des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent das Hilfsprogramm `sqlps` ausführt, das PowerShell 2.0 startet und das `sqlps`-Modul importiert.  
  
2.  Verwenden Sie einen Auftragsschritt an einer Eingabeaufforderung, um &lt;ui&gt;PowerShell.exe&lt;/ui&gt; auszuführen, und geben Sie ein Skript an, das das `sqlps`-Modul importiert.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
  
> [!CAUTION]  
>  Jeder Auftragsschritt des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agents, der PowerShell mit dem Modul `sqlps` ausführt, startet einen Prozess, der etwa 20 MB Arbeitsspeicher in Anspruch nimmt. Die gleichzeitige Ausführung einer großen Anzahl von Windows PowerShell-Auftragsschritten kann sich negativ auf die Leistung auswirken.  
  
##  <a name="create-a-powershell-job-step"></a><a name="PShellJob"></a>Erstellen eines PowerShell-Auftrags Schritts  
 **So erstellen Sie einen PowerShell-Auftragsschritt**  
  
1.  Erweitern Sie **SQL Server-Agent**, erstellen Sie einen neuen Auftrag, oder klicken Sie mit der rechten Maustaste auf einen vorhandenen Auftrag, und klicken Sie dann auf **Eigenschaften**. Weitere Informationen zum Erstellen eines Auftrags finden Sie unter [Erstellen von Aufträgen](../ssms/agent/create-jobs.md).  
  
2.  Klicken Sie im Dialogfeld **Auftragseigenschaften** auf die Seite **Schritte** und dann auf **Neu**.  
  
3.  Geben Sie im Dialogfeld **Neuer Auftragsschritt** unter **Schrittname**einen Schrittnamen für den Auftrag ein.  
  
4.  Klicken Sie in der Liste **Typ** auf **PowerShell**.  
  
5.  Wählen Sie in der Liste **Ausführen als** das Proxykonto mit den Anmeldeinformationen für den Auftrag aus.  
  
6.  Geben Sie im Feld **Befehl** die PowerShell-Skriptsyntax ein, die für den Auftragsschritt ausgeführt wird. Klicken Sie alternativ auf **Öffnen** , und wählen Sie eine Datei aus, die die Skriptsyntax enthält.  
  
7.  Klicken Sie auf die Seite **Erweitert** , um die folgenden Optionen für den Auftragsschritt festzulegen: welche Aktion bei der erfolgreichen oder fehlerhaften Ausführung des Auftragsschrittes jeweils auszuführen ist, wie oft der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent versuchen soll, den Auftragsschritt auszuführen, und wie viele Wiederholungsversuche unternommen werden sollen.  
  
##  <a name="create-a-command-prompt-job-step"></a><a name="CmdExecJob"></a>Erstellen eines Eingabeaufforderungs-Auftrags Schritts  
 **So erstellen Sie einen CmdExec-Auftragsschritt**  
  
1.  Erweitern Sie **SQL Server-Agent**, erstellen Sie einen neuen Auftrag, oder klicken Sie mit der rechten Maustaste auf einen vorhandenen Auftrag, und klicken Sie dann auf **Eigenschaften**. Weitere Informationen zum Erstellen eines Auftrags finden Sie unter [Erstellen von Aufträgen](../ssms/agent/create-jobs.md).  
  
2.  Klicken Sie im Dialogfeld **Auftragseigenschaften** auf die Seite **Schritte** und dann auf **Neu**.  
  
3.  Geben Sie im Dialogfeld **Neuer Auftragsschritt** unter **Schrittname**einen Schrittnamen für den Auftrag ein.  
  
4.  Wählen Sie in der Liste **Typ** den Eintrag **Betriebssystem (CmdExec)** aus.  
  
5.  Wählen Sie in der Liste **Ausführen als** das Proxykonto mit den Anmeldeinformationen für den Auftrag aus. Standardmäßig werden CmdExec-Auftragsschritte im Kontext des Kontos des SQL Server-Agent-Dienstes ausgeführt.  
  
6.  Geben Sie in das Feld **Prozessexitcode eines erfolgreichen Befehls** einen Wert zwischen 0 und 999999 ein.  
  
7.  Geben Sie im Feld **Befehl** "powershell.exe" zusammen mit Parametern, die das auszuführende PowerShell-Skript angeben, ein.  
  
8.  Klicken Sie auf die Seite **Erweitert** , um Optionen für Auftragsschritte festzulegen, z. B. welche Aktion bei der erfolgreichen oder fehlerhaften Ausführung des Auftragsschrittes jeweils auszuführen ist, wie oft der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent versuchen soll, den Auftragsschritt auszuführen, und in welche Datei der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent die Auftragsschrittausgabe schreiben soll. Nur Mitglieder der festen Serverrolle **sysadmin** können die Auftragsschrittausgabe in eine Betriebssystemdatei schreiben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-PowerShell](sql-server-powershell.md)  
  
  
