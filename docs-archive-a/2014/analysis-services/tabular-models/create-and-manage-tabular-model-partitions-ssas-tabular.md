---
title: Erstellen und Verwalten von Tabellen Modell Partitionen (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58c408c712d6ac4b6bd590bd0f8c895dc1a88700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620525"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a>Erstellen und Verwalten von Tabellenmodellpartitionen (SSAS – tabellarisch)
  Durch Partitionen wird eine Tabelle logisch unterteilt. Jede Partition kann unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden. Während der Modellerstellung werden die für ein Modell definierten Partitionen in ein bereitgestelltes Modell dupliziert. Nach der Bereitstellung können Sie diese Partitionen mit dem Dialogfeld **Partitionen** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mithilfe eines Skripts verwalten. In den Tasks in diesem Thema wird beschrieben, wie Partitionen für ein bereitgestelltes Modell erstellt und verwaltet werden.  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So erstellen Sie eine neue Partition](#bkmk_create_new)  
  
-   [So kopieren Sie eine Partition](#bkmk_copy)  
  
-   [So führen Sie zwei oder mehr Partitionen zusammen](#bkmk_merge)  
  
-   [So löschen Sie eine Partition](#bkmk_delete)  
  
## <a name="tasks"></a>Aufgaben  
 Um Partitionen für die bereitgestellte Datenbank eines tabellarischen Modells zu erstellen und zu verwalten, verwenden Sie das Dialogfeld **Partitionen** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Um das Dialogfeld **Partitionen** anzuzeigen, klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf eine Tabelle und klicken dann auf **Partitionen**.  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a>So erstellen Sie eine neue Partition  
  
1.  Klicken Sie im Dialogfeld **Partitionen** auf die Schaltfläche **Neu** .  
  
2.  Geben Sie in **Partitionsname**einen Namen für die Partition ein. Der Name der Standardpartition wird für jede neue Partition inkrementell erhöht.  
  
3.  Geben Sie unter **SQL-Anweisung**eine SQL-Abfrageanweisung in das Abfragefenster ein, durch die die Spalten und Klauseln definiert werden, die Sie in die Partition einschließen möchten, oder fügen Sie sie ein.  
  
4.  Um die Anweisung zu überprüfen, klicken Sie auf **Syntax überprüfen**.  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a> So kopieren Sie eine Partition  
  
1.  Wählen Sie im Dialogfeld **Partitionen** in der Liste **Partitionen** die Partition aus, die Sie kopieren möchten, und klicken Sie dann auf die Schaltfläche **Kopieren** .  
  
2.  Geben Sie in **Partitionsname**einen neuen Namen für die Partition ein.  
  
3.  Bearbeiten Sie die SQL-Abfrageanweisung unter **SQL-Anweisung**.  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> So führen Sie Partitionen zusammen  
  
-   Wählen Sie im Dialogfeld **Partitionen** in der Liste **Partitionen** mithilfe von STRG-Klicken die Partitionen aus, die Sie zusammenführen möchten, und klicken Sie dann auf die Schaltfläche **Zusammenführen** .  
  
> [!IMPORTANT]  
>  Beim Zusammenführen von Partitionen werden die Partitionsmetadaten nicht aktualisiert. Administratoren müssen die SQL-Anweisung ändern, damit bei den Verarbeitungsvorgängen der resultierenden Partition alle Daten in der zusammengeführten Partition verarbeitet werden.  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a>So löschen Sie eine Partition  
  
-   Wählen Sie im Dialogfeld **Partitionen** in der Liste **Partitionen** die Partition aus, die Sie löschen möchten, und klicken Sie dann auf die Schaltfläche **Löschen** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellarische Modell Partitionen &#40;tabellarischen SSAS-&#41;](partitions-ssas-tabular.md)   
 [Verarbeiten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](process-tabular-model-partitions-ssas-tabular.md)  
  
  
