---
title: Verbinden mit einem SQL Server-Hilfsprogramm | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609888"
---
# <a name="connect-to-a-sql-server-utility"></a>Verbinden mit einem SQL Server-Hilfsprogramm
  Bevor Sie eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm herstellen können, müssen Sie einen Steuerungspunkt für das Hilfsprogramm erstellen. Weitere Informationen finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](sql-server-utility-features-and-tasks.md).

 Um die Ressourcenintegrität von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuzeigen und zu verwalten, stellen Sie mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm her.

 So stellen Sie über SSMS eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm her:

1.  Starten Sie SSMS.

2.  Stellen Sie in SSMS eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.

3.  Klicken Sie auf **Ansicht** und dann auf **Hilfsprogramm-Explorer**.

4.  Klicken Sie im Navigationsbereich des Hilfsprogramm-Explorers auf ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Mit Hilfsprogramm verbinden**.

5.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** den Namen der UCP-Instanz an, und klicken Sie dann auf **Verbinden**.

6.  Zeigen Sie den Navigationsbereich des Hilfsprogramm-Explorers an, um eine Strukturansicht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen im UCP einzublenden.

 Beim Erstellen eines neuen UCPs werden Sie ebenfalls mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm verbunden. Weitere Informationen finden Sie unter [Erstellen eines Steuerungspunkts für das SQL Server-Hilfsprogramm &#40;SQL Server-Hilfsprogramm&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).

## <a name="see-also"></a>Weitere Informationen
 [SQL Server-Hilfsprogramm Features und Aufgaben](sql-server-utility-features-and-tasks.md) [anzeigen Resource Health Richtlinien Ergebnisse &#40;SQL Server-Hilfsprogramm&#41;](view-resource-health-policy-results-sql-server-utility.md)


