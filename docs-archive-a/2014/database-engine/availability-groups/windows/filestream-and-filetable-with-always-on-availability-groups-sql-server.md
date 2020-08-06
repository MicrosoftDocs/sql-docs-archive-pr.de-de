---
title: FILESTREAM und FILETABLE mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7de7b4d66890bb5f1fe49799844f666de81f4db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617276"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a>FILESTREAM und FileTable bei AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema enthält Informationen zur Verwendung der FILESTREAM- und FileTable-Funktionen mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Alle FILESTREAM-Funktionen werden unterstützt. Nach einem Failover kann sowohl auf lesbaren sekundären Replikaten als auch auf dem neuen primären Replikat auf FILESTREAM-Daten zugegriffen werden.  
  
 Die FileTable-Funktionalität wird teilweise unterstützt. Nach einem Failover kann auf dem primären Replikat auf FileTable-Daten zugegriffen werden, nicht jedoch auf FileTable-Daten auf lesbaren sekundären Replikaten.  
  
 **In diesem Thema:**  
  
-   [Voraussetzungen](#Prerequisites)  
  
-   [Verwenden von Virtual Network Namen (vnns) für FILESTREAM-und FILETABLE-Zugriff](#vnn)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
-   [Verwandte Inhalte](#RelatedContent)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   Bevor Sie eine Datenbank, die FILESTREAM mit oder ohne FileTable verwendet, zu einer Verfügbarkeitsgruppe hinzufügen, stellen Sie sicher, dass FILESTREAM auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet, aktiviert worden ist. Weitere Informationen finden Sie unter [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).  
  
##  <a name="using-virtual-network-names-vnns-for-filestream-and-filetable-access"></a><a name="vnn"></a> Verwenden von virtuellen Netzwerknamen (VNNs) für den Zugriff auf FILESTREAM- und FileTable-Daten  
 Wenn Sie FILESTREAM auf einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]aktivieren, wird eine Freigabe auf Instanzebene erstellt, um Zugriff auf die FILESTREAM-Daten zu gewähren. Sie greifen auf diese Freigabe zu, indem Sie den Computernamen im folgende Format angeben:  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 In einer AlwaysOn-Verfügbarkeitsgruppe wird der Name des Computers jedoch mit einem Virtuellen Netzwerknamen (kurz VNN) virtualisiert. Wenn der Computer das primäre Replikat in einer Verfügbarkeitsgruppe ist und Datenbanken in der Verfügbarkeitsgruppe FILESTREAM-Daten enthalten, dann wird auch eine Freigabe im Bereich des VNNs erstellt, um Zugriff auf die FILESTREAM-Daten zu bieten. Dies wirkt sich nicht auf den Transact-SQL-Zugriff auf FILESTREAM-Daten aus. Anwendungen, die Dateisystem-APIs verwenden, müssen jedoch die Freigabe im Bereich des VNNs verwenden. Diese Freigabe hat einen Pfad im folgenden Format:  
  
 `\\<VNN>\<filestream_share_name>`  
  
 Diese Freigabe im VNN-Bereich wird erstellt, wenn eines der folgenden Ereignisse auftritt.  
  
-   Sie fügen eine Datenbank hinzu, die FILESTREAM-Daten zu einer AlwaysOn-Verfügbarkeitsgruppe für das primäre Replikat enthält. In diesem Fall ist die Freigabe `\\<computer_name>\<filestream_share_name>` bereits vorhanden. Die Freigabe `\\<VNN>\<filestream_share_name>` wird erstellt.  
  
-   Sie aktivieren FILESTREAM für E/A-Streamingzugriff auf Datei für ein primäres Replikat, das Verfügbarkeitsgruppen enthält. Die folgenden Freigaben werden erstellt:  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  `\\<VNN1>\<filestream_share_name>` für die Verfügbarkeitsgruppe 1.  
  
    3.  `\\<VNN2>\<filestream_share_name>` für die Verfügbarkeitsgruppe 2.  
  
 Diese Freigaben im VNN-Bereich werden auch an alle sekundären Replikate weitergegeben.  
  
 Wenn die Datenbank, die FILESTREAM- oder FileTable-Daten enthält, zu einer AlwaysOn-Verfügbarkeitsgruppe gehört:  
  
-   Die FILESTREAM-Funktion und die FileTable-Funktion akzeptieren oder geben virtuelle Netzwerknamen (VNNs) statt Computernamen zurück. Weitere Informationen zu diesen Funktionen finden Sie unter [Filestream- und FileTable-Funktionen &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).  
  
-   Bei allen Zugriffen auf FILESTREAM- oder FileTable-Daten über Dateisystem-APIs sollten VNNs statt der Computernamen verwendet werden.  
  
 Wenn die Datenbank Teil einer Verfügbarkeitsgruppe ist und die Anwendung versucht, mit einem Computernamen im Format `\\<computer_name>\<filestream_share_name>` auf die Freigabe zuzugreifen, dann wird ein Fehler ausgelöst.  
  
 Wenn die Datenbank kein Teil einer Verfügbarkeitsgruppe ist und die Anwendung versucht, auf die Freigabe mit einem Pfad im VNN-Bereich zuzugreifen, dann wird die Anforderung möglicherweise erfolgreich ausgeführt. In diesem Fall wird der virtuelle Netzwerkname in den Computernamen aufgelöst. Von dieser Vorgehensweise wird jedoch stark abgeraten, da der Pfad im VNN-Bereich nicht mehr gültig ist, wenn die Verfügbarkeitsgruppe gelöscht wird.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Aktivieren und Konfigurieren von FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [Aktivieren der erforderlichen Komponenten für FileTable](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
 Keine.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
