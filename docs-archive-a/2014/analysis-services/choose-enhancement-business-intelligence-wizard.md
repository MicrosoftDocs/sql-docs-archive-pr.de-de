---
title: Erweiterung auswählen (Business Intelligence-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.bienhancement.f1
ms.assetid: 39e2f36c-2c02-4a71-af8f-5dbd373190dc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ea2729bd6be20e377676d37fc87ec66da145d1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615698"
---
# <a name="choose-enhancement-business-intelligence-wizard"></a>Erweiterung auswählen (Business Intelligence-Assistent)
  Auf der Seite **Erweiterung auswählen** wählen Sie die Business Intelligence-Erweiterung aus, die dem Cube oder der Dimension hinzugefügt werden soll.  
  
## <a name="options"></a>Tastatur  
 **Verfügbare Erweiterungen**  
 Wählen Sie die hinzuzufügende Business Intelligence-Erweiterung aus. In der folgenden Tabelle sind die verfügbaren Erweiterungen aufgelistet.  
  
|Erweiterung|BESCHREIBUNG|  
|-----------------|-----------------|  
|**Zeitintelligenz definieren**|Fügen Sie einer ausgewählten Hierarchie zusätzliche Zeitsichten hinzu. Zu diesen Sichten gehören Zeitraum bis Datum, gleitender Durchschnitt und Zeitraumvergleich.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Kontointelligenz definieren**|Weisen Sie Elementen eines Kontoattributs Standardbuchhaltungsklassifikationen, z. B. Einnahmen und Ausgaben, zu.<br /><br /> Wenn die Aggregationsfunktion des Measures auf *ByAccount*festgelegt ist, verwendet die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz die Buchhaltungsklassifikationen, um über einen Zeitraum ein Measure für die Elemente eines Kontoattributs zu aggregieren.|  
|**Dimensionsintelligenz definieren**|Mit der Dimensionsintelligenz geben Sie einen Standardunternehmenstyp für eine Dimension und gültige Typen für die Dimensionsattribute an. Diese Typspezifikationen können von Clientanwendungen bei der Datenanalyse verwendet werden.|  
|**Unären Operator angeben**|Geben Sie einen unären Operator an, um die den Elementen in einer Über-/Unterordnungshierarchie zugeordnete Standardaggregation zu ersetzen.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Benutzerdefinierte Elementformel erstellen**|Erstellen Sie eine benutzerdefinierte Elementformel, um die Standardaggregation zu ersetzen, die einem Dimensionselement mit einem anderen Operator zugeordnet ist.|  
|**Attributreihenfolge angeben**|Geben Sie die Reihenfolge der Elemente eines ausgewählten Attributs an. Die Elemente können nach dem Namen oder Schlüssel eines ausgewählten Attributs oder nach dem Namen oder Schlüssel eines mit dem ausgewählten Attribut verknüpften Attributs sortiert werden. Standardmäßig werden Elemente nach dem Namen des ausgewählten Attributs sortiert.|  
|**Rück Schreiben von Dimensionen aktivieren**|Aktivieren Sie die manuelle Änderung der Dimensionsstruktur. Updates für eine Dimension mit aktiviertem Schreibzugriff werden direkt in der Dimensionstabelle aufgezeichnet.|  
|**Semiadditives Verhalten definieren**|Definieren Sie manuell die Aggregationsmethode für einzelne Measures oder Elemente eines Kontotypattributs. Wenn der Cube eine Kontodimension enthält, können Sie das semiadditive Verhalten mithilfe der Option **Kontointelligenz definieren** auf der Grundlage des Kontotyps automatisch festlegen.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
|**Währungsumrechnung definieren**|Definieren Sie Regeln zum Umrechnen und Analysieren multinationaler Daten im Cube. Umrechnungsregeln werden auf Cubeebene mithilfe eines MDX-Skripts (Multidimensional Expressions) angewendet, das vom Business Intelligence-Assistenten generiert wird.<br /><br /> Hinweis: Diese Option ist nur für Cubes verfügbar.|  
  
 **Beschreibung**  
 Stellt eine kurze Beschreibung der ausgewählten Business Intelligence-Erweiterung bereit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Business Intelligence Wizard (F1-Hilfe)](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Der Dimensions-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
