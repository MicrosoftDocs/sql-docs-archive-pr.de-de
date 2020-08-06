---
title: Erstellen und Verwalten von Perspektiven (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d0029ff61aa05e2e83f34833c3d0af17ddb3beb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609499"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>Erstellen und Verwalten von Perspektiven (SSAS – tabellarisch)
  Eine Perspektive definiert sichtbare Teilmengen eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte des Modells bereitstellen. In den Tasks in diesem Thema wird beschrieben, wie Perspektiven mithilfe des Dialogfelds **Perspektiven** im Modell-Designer erstellt und verwaltet werden.  
  
 Dieses Thema umfasst folgende Aufgaben:  
  
-   [So fügen Sie eine Perspektive hinzu](#bkmk_add)  
  
-   [So bearbeiten Sie eine Perspektive](#bkmk_edit)  
  
-   [So benennen Sie eine Perspektive um](#bkmk_rename)  
  
-   [So löschen Sie eine Perspektive](#bkmk_delete)  
  
-   [So kopieren Sie eine Perspektive](#bkmk_copy)  
  
## <a name="tasks"></a>Aufgaben  
 Zum Erstellen von Perspektiven verwenden Sie das Dialogfeld **Perspektiven** , in dem Sie Perspektiven hinzufügen, bearbeiten, löschen, kopieren und anzeigen können. Um das Dialogfeld **Perspektiven** anzuzeigen, klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf das Menü **Modell** und dann auf **Perspektiven**.  
  
###  <a name="to-add-a-perspective"></a><a name="bkmk_add"></a> So fügen Sie eine Perspektive hinzu  
  
-   Zum Hinzufügen einer neuen Perspektive klicken Sie auf **Neue Perspektive**. Anschließend können Sie die einzufügenden Feldobjekte aktivieren und deaktivieren und einen Namen für die neue Perspektive angeben.  
  
     Wenn Sie eine leere Perspektive erstellen, die alle Felder mit Feldobjekten enthält, wird dem Benutzer, der diese Perspektive verwendet, eine leere Feldliste angezeigt. Perspektiven sollten mindestens eine Tabelle und eine Spalte enthalten.  
  
###  <a name="to-edit-a-perspective"></a><a name="bkmk_edit"></a>So bearbeiten Sie eine Perspektive  
  
-   Zum Ändern einer Perspektive aktivieren und deaktivieren Sie Felder in der Spalte der Perspektive, wodurch Feld Objekte der Perspektive hinzugefügt bzw. daraus entfernt werden.  
  
###  <a name="to-rename-a-perspective"></a><a name="bkmk_rename"></a>So benennen Sie eine Perspektive um  
  
-   Wenn Sie mit dem Mauszeiger auf die Spaltenüberschrift einer Perspektive (den Namen der Perspektive) zeigen, wird die Schaltfläche **Umbenennen** angezeigt. Klicken Sie auf **Umbenennen**, um die Perspektive umzubenennen. Geben Sie dann einen neuen Namen ein, oder bearbeiten Sie den vorhandenen Namen.  
  
###  <a name="to-delete-a-perspective"></a><a name="bkmk_delete"></a>So löschen Sie eine Perspektive  
  
-   Wenn Sie mit dem Mauszeiger auf die Spaltenüberschrift einer Perspektive (den Namen der Perspektive) zeigen, wird die Schaltfläche **Löschen** angezeigt. Klicken Sie zum Löschen der Perspektive auf die Schaltfläche **Löschen** , und klicken Sie im Bestätigungsfenster auf **Ja** .  
  
###  <a name="to-copy-a-perspective"></a><a name="bkmk_copy"></a>So kopieren Sie eine Perspektive  
  
-   Wenn Sie mit dem Mauszeiger auf die Spaltenüberschrift einer Perspektive zeigen, wird die Schaltfläche **Kopieren** angezeigt. Klicken Sie auf die Schaltfläche **Kopieren** , um eine Kopie dieser Perspektive zu erstellen. Rechts neben den vorhandenen Perspektiven wird eine Kopie der ausgewählten Perspektive als neue Perspektive hinzugefügt. Die neue Perspektive erbt den Namen der kopierten Perspektive, und an das Ende des Namens wird die Anmerkung *-Kopieren* angefügt. Wenn beispielsweise eine Kopie der *Sales* -Perspektive erstellt wird, wird die neue Perspektive als *Sales-Copy*bezeichnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Perspektiven &#40;tabellarischen SSAS-&#41;](perspectives-ssas-tabular.md)   
 [Hierarchien &#40;SSAS – tabellarisch&#41;](hierarchies-ssas-tabular.md)  
  
  
