---
title: Überwachen und Reagieren auf Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: afdf1beffd6099fce84f03a8ba65f7de9abb8f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699182"
---
# <a name="monitor-and-respond-to-events"></a>Überwachen und Reagieren auf Ereignisse
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Der-Agent kann Ereignisse überwachen und automatisch auf *Ereignisse*reagieren, wie z. b. Nachrichten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , bestimmte Leistungsbedingungen und Windows-Verwaltungsinstrumentation (WMI)-Ereignisse.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Warnungen](alerts.md)  
 Enthält Informationen zum Benennen von Warnungen und Auswählen von Ereignissen oder Leistungsbedingungen, für die Warnungen ausgegeben werden.  
  
 [Erstellen eines benutzerdefinierten Ereignisses](create-a-user-defined-event.md)  
 Enthält Informationen zum Erstellen von Ereignissen, die nicht von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vordefiniert sind.  
  
 [Operatoren](operators.md)  
 Enthält Informationen zum Erstellen von Aliasen für Administratoren, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Versenden von Benachrichtigungen verwendet werden können, wenn Aufträge einen Fehler erzeugen oder erfolgreich ausgeführt werden.  
  
## <a name="about-monitoring-and-responding-to-events"></a>Informationen zum Überwachen von und Reagieren auf Ereignisse  
 Automatische Reaktionen auf Ereignisse werden als *Warnungen*bezeichnet. Sie können Warnungen für Ereignisse definieren um anzugeben, wie vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf das Auftreten dieser Ereignisse reagiert werden soll. Von einer Warnung kann auf ein Ereignis reagiert werden, indem ein Administrator benachrichtigt oder ein Auftrag ausgeführt wird, oder indem beide Aktionen ausgeführt werden. Von einer Warnung kann ein Ereignis auch an das Microsoft Windows-Anwendungsprotokoll auf einem anderen Computer weitergeleitet werden. Sie können beispielsweise angeben, dass bei einem Ereignis mit dem Schweregrad 19 sofort ein Operator benachrichtigt wird. Durch das Definieren von Warnungen können Datenbankadministratoren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]effektiver überwachen und verwalten.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent reagiert nur auf Ereignisse, für die eine Warnung definiert ist. Die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zum Überwachen von Ereignissen verwendete Methode hängt vom Typ des Ereignisses ab.  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnung für einen Leistungsindikator definiert ist, wird der Leistungsindikator direkt vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent überwacht. Bei einem WMI-Ereignis wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent eine Ereignisabfrage für das WMI-Ereignis registriert.  
  
 Um auf Meldungen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu reagieren, wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent das Windows-Anwendungsprotokoll überwacht. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent kann nur auf Meldungen reagieren, die in diesem Protokoll aufgeführt sind. Standardmäßig protokolliert SQL Server die folgenden Meldungen im Windows-Anwendungsprotokoll:  
  
-   sysmessages-Fehler des Schweregrades 19 oder höher.  
  
     Wenn auch bestimmte sysmessages-Fehler mit einem Schweregrad niedriger als 19 protokolliert werden sollen, verwenden Sie die gespeicherte Prozedur „sp_altermessage“, um solche Fehler als „immer protokolliert“ zu kennzeichnen.  
  
-   Jede RAISERROR-Anweisung, die durch Verwenden der WITH LOG-Syntax aufgerufen wurde.  
  
     Das Verwenden von RAISERROR WITH LOG wird empfohlen, um von einer Instanz von SQL Server in das Windows-Anwendungsprotokoll zu schreiben.  
  
-   Jedes mithilfe von „xp_logevent“ protokollierte Anwendungsereignis.  
  
    > [!NOTE]  
    >  Das Protokollieren von Anwendungsereignissen belegt Protokollspeicher und kann dazu führen, dass das Windows-Anwendungsprotokoll die Maximalgröße überschreitet. Stellen Sie sicher, dass das Windows-Anwendungsprotokoll über eine ausreichende Größe verfügt, damit es nicht zu einem Verlust von SQL Server-Ereignisinformationen kommt.  
  
 Wenn von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Meldung protokolliert wird, vergleicht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst die Meldung mit den Warnungen, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administrator definiert worden sind.  
  
 Unabhängig von der Ereignisquelle reagiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf das Ereignis, indem die Tasks ausgeführt werden, die in der Warnung für das Ereignis angegeben worden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_altermessage &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
  
