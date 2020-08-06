---
title: Verwalten einer Verbunddomäne | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 47821eff-800b-4053-8d36-e42bbc267f54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d68acf42f31d6652615154d5b8b26aa37914ae4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621671"
---
# <a name="managing-a-composite-domain"></a>Verwalten einer Verbunddomäne
  In diesem Thema wird die Verwendung von Verbunddomänen in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) beschrieben. In einigen Fällen können die Daten eines Felds in einer einzelnen Domäne nicht zufriedenstellend dargestellt werden, und Sie können die Daten nur darstellen, indem Sie einzelne Domänen gruppieren. Hierzu erstellen Sie eine Verbunddomäne. Eine Verbunddomäne besteht aus zwei oder mehreren einzelnen Domänen. Sie wird einem Datenfeld zugeordnet, das aus mehreren verwandten Begriffen besteht, die nicht analysiert werden, aber in einem einzelnen zusammengesetzten Wert enthalten sind. Jeder Begriff im Wert wird durch eine andere einzelne Domäne dargestellt. Nachdem Sie einzelne Domänen in Verbunddomänen aufgenommen und dann die Verbunddomäne dem Datenfeld zugeordnet haben, können Sie Wissen zu den Daten in diesem Feld in der Wissensdatenbank erstellen, indem Sie Wissen in den einzelnen Domänen erstellen. Eine Verbunddomäne ist wie eine einzelne Domäne eine semantische Darstellung der Daten in einem einzelnen Datenfeld.  
  
 Die einzelnen Domänen in einer Verbunddomäne müssen einen gemeinsamen Wissensbereich haben. Beispiel: ein Adressenfeld mit Daten für Straße, Ort, Bundesland, Land und Postleitzahl. Die anderen Begriffe in diesem Feld könnten andere Datentypen haben. Ordnen Sie deswegen diese Begriffe den einzelnen Domänen zu. Ein anderes Beispiel ist ein Feld mit dem vollständigen Namen, das Daten für den Vornamen, zweiten Vornamen und Nachnamen aufweist. Um eine Verbunddomäne zu verwenden, müssen Sie die Daten im Feld in anderen einzelnen Domänen analysieren können, wobei eine Verbunddomäne für das Feld und eine einzelne Domäne für einen Teil des Felds erstellt wird.  
  
 Verbunddomänen verfügen über andere Funktionen als einzelne Domänen. Sie können die Werte nicht in der Verbunddomäne ändern, sondern nur in einer einzelnen Domäne. Sie können für Verbunddomänen domänenübergreifende Regeln verwenden, um die Werte in den einzelnen Domänen der Verbunddomäne zu testen. Sie können außerdem die Wertkombinationen anzeigen, die in den Verbunddomänen gefunden werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Durch das Verwenden einer Verbunddomäne erhalten Sie folgende Möglichkeiten:  
  
|||  
|-|-|  
|Sie können eine semantische Darstellung für ein Datenfeld erstellen, das aus mehreren verwandten Begriffen besteht, die nicht analysiert werden.|[Erstellen einer Verbunddomäne](../../2014/data-quality-services/create-a-composite-domain.md)|  
|Wenn Sie einer Verbunddomäne komplexe Daten zuordnen, können Sie die Daten basierend auf Trennzeichen und zusätzlich auf Grundlage des Wissens analysieren. DQS versucht zunächst, mithilfe des Wissens zu den einzelnen Domänen zu bestimmen, wie Teile der komplexen Zeichenfolge in die einzelnen Domänen gehören.|[Erstellen einer Verbunddomäne](../../2014/data-quality-services/create-a-composite-domain.md)|  
|Fügen Sie einen Verweisdatendienst, z. B. einen Dienst zum Behandeln von Adressdaten, an eine Verbunddomäne an.|[Anfügen einer Domäne oder Verbunddomäne an Verweisdaten](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)|  
|Erstellen Sie eine domänenübergreifende Regel, wenn der Wert einer Domäne in einer Verbunddomäne Auswirkungen auf den Wert einer anderen Domäne hat.|[Erstellen einer domänenübergreifenden Regel](../../2014/data-quality-services/create-a-cross-domain-rule.md)|  
|Identifizieren Sie Wertkombinationen, damit DQS ihre Häufigkeit melden kann.|[Verwenden von Wertbeziehungen in einer Verbunddomäne](../../2014/data-quality-services/use-value-relations-in-a-composite-domain.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen einer Wissensdatenbank durch das Ausführen der Wissensermittlung und interaktives Verwalten von Wissen|[Aufbau einer Wissensdatenbank](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|Importieren von Wissen in oder Exportieren von Wissen aus einer Wissensdatenbank.|[Importieren und Exportieren von Wissen](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|Erstellen einer einzelnen Domäne und Hinzufügen von Wissen zur Domäne.|[Verwalten einer Domäne](../../2014/data-quality-services/managing-a-domain.md)|  
  
  
