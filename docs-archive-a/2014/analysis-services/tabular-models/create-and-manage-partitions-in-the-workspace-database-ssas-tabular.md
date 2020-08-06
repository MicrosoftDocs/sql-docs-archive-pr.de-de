---
title: Erstellen und Verwalten von Partitionen in der Arbeitsbereichs Datenbank (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3824dd4763e516dc5e8e34a9ec815d3969f4eb79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616208"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a>Erstellen und Verwalten von Partitionen in der Arbeitsbereichsdatenbank (SSAS – tabellarisch)
  Durch Partitionen wird eine Tabelle logisch unterteilt. Die einzelnen Partitionen können dann unabhängig voneinander oder parallel mit anderen Partitionen verarbeitet (aktualisiert) werden. Durch Partitionen kann sich die Skalierbarkeit und Verwaltbarkeit großer Datenbanken verbessern. Standardmäßig verfügt jede Tabelle über eine Partition, die alle Spalten einschließt. In den Tasks in diesem Thema wird beschrieben, wie Partitionen in der Arbeitsbereichs Datenbank des Modells mithilfe des Dialog Felds **Partitions-Manager** in erstellt und verwaltet werden.[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 Nachdem ein Modell für eine andere Analysis Services-Instanz bereitgestellt wurde, können Datenbankadministratoren Partitionen im (bereitgestellten) Modell mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen und verwalten. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Tabellenmodellpartitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md).  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So erstellen Sie eine neue Partition](#bkmk_create_new)  
  
-   [So kopieren Sie eine Partition](#bkmk_copy)  
  
-   [So löschen Sie eine Partition](#bkmk_delete)  
  
> [!NOTE]  
>  Partitionen in der Arbeitsbereichsdatenbank des Modells können nicht mithilfe des Dialogfelds Partitions-Manager zusammengeführt werden. Partitionen können in einem bereitgestellten Modell nur mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zusammengeführt werden.  
  
## <a name="tasks"></a>Aufgaben  
 Um Partitionen zu erstellen und zu verwalten, verwenden Sie das Dialogfeld **Partitions-Manager** . Sie öffnen das Dialogfeld **Partitions-Manager** , indem Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf das Menü **Tabelle** und dann auf **Partitionen**klicken.  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a>So erstellen Sie eine neue Partition  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, für die Sie eine Partition definieren möchten.  
  
2.  Klicken Sie auf das Menü **Tabelle** und dann auf **Partitionen**.  
  
3.  Überprüfen Sie, ob im **Partitions-Manager**im Listenfeld **Tabelle** die richtige Tabelle angezeigt wird, oder wählen Sie die zu partitionierende Tabelle aus, und klicken Sie auf **Neu**.  
  
4.  Geben Sie in **Partitionsname**einen Namen für die Partition ein. Der Name der Standardpartition wird für jede neue Partition inkrementell erhöht.  
  
5.  Sie können die in die Partition einzufügenden Zeilen und Spalten auswählen, indem Sie den Tabellenvorschaumodus oder eine SQL-Abfrage verwenden, die im Abfrage-Editor-Modus erstellt wurde.  
  
     Klicken Sie nahe der oberen rechten Ecke des Vorschaufensters auf die Schaltfläche **Tabellenvorschau** , um den Tabellenvorschaumodus (Standard) zu verwenden. Wählen Sie die in die Partition einzuschließenden Spalten aus, indem Sie das Kontrollkästchen neben dem Spaltennamen aktivieren. Um Zeilen zu filtern, klicken Sie mit der rechten Maustaste auf einen Zellenwert, und klicken Sie auf **Nach dem Wert der ausgewählten Zelle filtern**.  
  
     Klicken Sie nahe der oberen rechten Ecke des Vorschaufensters auf die Schaltfläche **Abfrage-Editor** , um eine SQL-Anweisung zu verwenden. Geben Sie anschließend im Abfragefenster eine SQL-Abfrage-Anweisung ein (oder kopieren und fügen Sie die Anweisung aus einem anderen Text ein). Um die Anweisung zu überprüfen, klicken Sie auf **Überprüfen**. Um den Abfrage-Designer zu verwenden, klicken Sie auf **Entwurf**.  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a> So kopieren Sie eine Partition  
  
1.  Überprüfen Sie, ob im **Partitions-Manager**im Listenfeld **Tabelle** die richtige Tabelle angezeigt wird, oder wählen Sie die Tabelle mit der zu kopierenden Partition aus.  
  
2.  Wählen Sie in der Liste **Partitionen** die zu kopierende Partition aus, und klicken Sie auf **Kopieren**.  
  
3.  Geben Sie in **Partitionsname**einen neuen Namen für die Partition ein.  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a>So löschen Sie eine Partition  
  
1.  Überprüfen Sie, ob im **Partitions-Manager**im Listenfeld **Tabelle** die richtige Tabelle angezeigt wird, oder wählen Sie die zu löschende Partition aus.  
  
2.  Wählen Sie in der Liste **Partitionen** die zu löschende Partition aus, und klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Partitionen &#40;tabellarischen SSAS-&#41;](partitions-ssas-tabular.md)   
 [Verarbeiten von Partitionen in der Arbeitsbereichs Datenbank &#40;tabellarischen SSAS-&#41;](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
