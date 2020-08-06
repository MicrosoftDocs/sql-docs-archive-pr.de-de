---
title: 'Auftrags Schritt-Eigenschaften: neuer Auftrags Schritt (Seite "Erweitert") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722181"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a>Auftragsschritteigenschaften: Neuer Auftragsschritt (Seite „Erweitert“)
  Mithilfe dieser Seite können Sie die Eigenschaften eines-Agent- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Auftrags Schritts anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Aktion bei Erfolg**  
 Legt fest, welche Aktion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent bei erfolgreicher Auftragsausführung ausführen soll.  
  
 **Wiederholungsversuche**  
 Legt fest, wie oft vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent versucht werden soll, einen fehlgeschlagenen Auftragsschritt erneut auszuführen.  
  
 **Wiederholungsintervall (Min)**  
 Legt fest, wie lange der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent bis zum nächsten Wiederholungsversuch warten soll.  
  
 **Aktion bei Fehler**  
 Legt fest, welche Aktion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent bei Fehlschlagen des Auftrags ausführen soll.  
  
## <a name="options-for-transact-sql-job-steps"></a>Optionen für Transact-SQL-Auftragsschritte  
 **Ausgabedatei**  
 Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll. Diese Option ist nur für Mitglieder der festen Serverrolle **sysadmin** verfügbar.  
  
 **...**  
 Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
 **Anzeigen**  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
 **Ausgabe an vorhandene Datei anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Datei an. Andernfalls wird der vorige Inhalt der Datei bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **In Tabelle protokollieren**  
 Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
 **Anzeigen**  
 Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
 **Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **Schrittausgabe in Verlauf einschließen**  
 Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
 **Ausführen als Benutzer**  
 Wenn Sie Mitglied der festen Serverrolle **sysadmin** sind, können Sie für die Ausführung dieses Auftragsschritts einen anderen SQL-Anmeldenamen auswählen.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Optionen für Auftragsschritte des Betriebssystems (CmdExec)  
 **Ausgabedatei**  
 Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll.  
  
 **...**  
 Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
 **Anzeigen**  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
 **Ausgabe an vorhandene Datei anfügen**  
 Fügt die Auftragsschrittausgabe bei jeder Ausführung des Schritts an den vorhandenen Inhalt der Datei an.  
  
 **In Tabelle protokollieren**  
 Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
 **Anzeigen**  
 Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
 **Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **Schrittausgabe in Verlauf einschließen**  
 Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="options-for-powershell-job-steps"></a>Optionen für PowerShell-Auftragsschritte  
 **Ausgabedatei**  
 Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll.  
  
 **...**  
 Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
 **Anzeigen**  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
 **Ausgabe an vorhandene Datei anfügen**  
 Fügt die Auftragsschrittausgabe bei jeder Ausführung des Schritts an den vorhandenen Inhalt der Datei an.  
  
 **In Tabelle protokollieren**  
 Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
 **Anzeigen**  
 Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
 **Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **Schrittausgabe in Verlauf einschließen**  
 Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Optionen für Auftragsschritte des Replikation-Warteschlangenlesers  
 **Server**  
 Legt fest, welcher Server für einen Auftragsschritt des Replikation-Warteschlangenlesers verwendet werden soll.  
  
 **Datenbank**  
 Legt fest, welche Datenbank für einen Auftragsschritt des Replikation-Warteschlangenlesers verwendet werden soll.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services  
 **Ausgabedatei**  
 Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll. Diese Option ist nur für Mitglieder der festen Serverrolle **sysadmin** verfügbar.  
  
 **...**  
 Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
 **Anzeigen**  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
 **Ausgabe an vorhandene Datei anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Datei an. Andernfalls wird der vorige Inhalt der Datei bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **In Tabelle protokollieren**  
 Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
 **Anzeigen**  
 Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
 **Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
 Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
 **Schrittausgabe in Verlauf einschließen**  
 Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Auftragsschritten](manage-job-steps.md)  
  
  
