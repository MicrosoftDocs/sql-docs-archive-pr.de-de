---
title: Integration Services-Transformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618153"
---
# <a name="integration-services-transactions"></a>Integration Services-Transaktionen
  Pakete verwenden Transaktionen, um die von Tasks ausgeführten Datenbankaktionen in unteilbare Einheiten einzubinden und somit die Integrität der Daten zu erhalten. Alle [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Containertyppakete, For-Schleifen-Container, Foreach-Schleifen-Container und Sequenzcontainer sowie die Taskhosts, die die einzelnen Tasks kapseln, können so konfiguriert werden, dass sie Transaktionen verwenden. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt für das Konfigurieren von Transaktionen drei Optionen bereit: **NotSupported**, **Supported**und **Required**.  
  
-   **Required** bedeutet, dass der Container eine Transaktion startet, es sei denn, eine andere Transaktion ist bereits durch den übergeordneten Container gestartet worden. Wenn bereits eine Transaktion vorhanden ist, nimmt der Container an dieser Transaktion teil. Wenn beispielsweise ein Paket, für das die Unterstützung von Transaktionen nicht konfiguriert wurde, einen Sequenzcontainer enthält, der die Option **Required** verwendet, startet der Sequenzcontainer eine eigene Transaktion. Wenn das Paket jedoch mit der Option **Required** konfiguriert wurde, nimmt der Sequenzcontainer an der Pakettransaktion teil.  
  
-   **Supported** bedeutet, dass der Container keine Transaktion startet, sondern an der durch den übergeordneten Container gestarteten Transaktion teilnimmt. Wenn beispielsweise ein Paket mit vier SQL ausführen-Tasks eine Transaktion startet und alle vier Tasks die Option **Supported** verwenden, wird für die entsprechenden Datenbankaktualisierungen ein Rollback ausgeführt, wenn einer der Tasks einen Fehler auslöst. Wenn das Paket keine Transaktion startet, sind die vier SQL ausführen-Tasks nicht durch eine Transaktion gebunden, und das Rollback wird lediglich für den fehlgeschlagenen Task ausgeführt.  
  
-   **NotSupported** bedeutet, dass der Container keine Transaktion startet, und auch an keiner vorhandenen Transaktion teilnimmt. Eine von einem übergeordneten Container gestartete Transaktion hat keine Auswirkung auf untergeordnete Container, deren Konfiguration keine Transaktionen zulässt. Wenn ein Paket beispielsweise so konfiguriert ist, dass es eine Transaktion startet, und ein For-Schleifen-Container des Pakets die Option **NotSupported** verwendet, kann für keinen der Tasks in der For-Schleife ein Rollback ausgeführt werden, falls ein Fehler auftritt.  
  
 Sie konfigurieren Transaktionen, indem Sie für den Container die TransactionOption-Eigenschaft festlegen. Diese Eigenschaft können Sie mithilfe des Fensters **Eigenschaften** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]oder programmgesteuert festlegen.  
  
> [!NOTE]  
>  Mit der `TransactionOption`-Eigenschaft wird festgelegt, ob der von einem Container angeforderte Wert der `IsolationLevel`-Eigenschaft angewendet wird. Weitere Informationen finden Sie in der Beschreibung der- `IsolationLevel` Eigenschaft im Thema Festlegen von [Paket Eigenschaften](set-package-properties.md).  
  
### <a name="to-configure-a-package-to-use-transactions"></a>So konfigurieren Sie das Verwenden von Transaktionen für ein Paket  
  
-   [Konfigurieren eines Pakets für die Verwendung von Transaktionen](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Blog-Artikel [How to Use Transactions in SQL Server Integration Services (SSIS)](https://go.microsoft.com/fwlink/?LinkId=157783)(Verwenden von Transaktionen in SQL Server Integration Services (SSIS)) unter www.mssqltips.com  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geerbte Transaktionen](../../2014/integration-services/inherited-transactions.md)   
 [Mehrere Transaktionen](../../2014/integration-services/multiple-transactions.md)  
  
  
