---
title: Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621108"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a>Optionen für Verlaufsattribute (Assistent für langsam veränderliche Dimensionen)
  Mithilfe des Dialogfelds **Optionen für Verlaufsattribute** können Sie Verlaufsattribute nach Anfangs- und Enddatum anzeigen oder sie in einer speziell zu diesem Zweck erstellten Spalte aufzeichnen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Einzelne Spalte zum Anzeigen der aktuellen und abgelaufenen Datensätze verwenden**  
 Wenn Sie eine einzelne Spalte für zum Aufzeichnen des Status von Verlaufsattributen verwenden, sind folgende Optionen verfügbar:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Spalte mit Indikator für aktuellen Datensatz**|Wählen Sie eine Spalte aus, in der der aktuelle Datensatz angezeigt werden soll.|  
|**Wert, wenn aktuell**|Verwenden Sie entweder **True** oder **Current** , um anzuzeigen, dass der Datensatz aktuell ist.|  
|**Wert, wenn abgelaufen**|Verwenden Sie entweder **False** oder **Abgelaufen** , um anzuzeigen, dass der Datensatz ein abgelaufener Wert ist.|  
  
 **Start- und Enddatum zum Identifizieren aktueller und abgelaufener Datensätze verwenden**  
 Die Dimensionstabelle für diese Option muss eine Datumsspalte enthalten. Wenn Sie die Verlaufsattribute nach Start- und Enddatum anzeigen, sind folgende Optionen verfügbar:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|**Spalte mit Startdatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Startdatum enthalten soll.|  
|**Spalte mit Enddatum**|Wählen Sie die Spalte in der Dimensionstabelle aus, die das Enddatum enthalten soll.|  
|**Variable zum Festlegen von Datumswerten**|Wählen Sie eine Variable für die Datumswerte aus der Liste aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
