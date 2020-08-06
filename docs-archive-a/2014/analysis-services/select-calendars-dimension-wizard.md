---
title: Kalender auswählen (Dimensions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618922"
---
# <a name="select-calendars-dimension-wizard"></a>Kalender auswählen (Dimensions-Assistent)
  Auf der Seite **Kalender auswählen** können Sie für eine gegebene Zeitdimension zusätzliche Hierarchien zur Darstellung von Geschäfts-, Berichts-, Produktions- oder ISO 8601-Kalendern (International Organization for Standardization, Internationale Organisation für Normung) erstellen.  
  
> [!NOTE]  
>   Diese Seite wird nur angezeigt, wenn auf der Seite **Dimensionstyp auswählen** die Option **Serverzeitdimension** oder auf der Seite **Erstellungsmethode auswählen** die Option **Dimension ohne eine Datenquelle erstellen** und auf der Seite **Dimensionstyp auswählen** die Option **Zeitdimension** ausgewählt wurden.  
  
## <a name="options"></a>Tastatur  
 **Geschäftskalender**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Geschäftskalender zu erstellen.  
  
 **Starttag und -monat**  
 Wählen Sie Tag und Monat für den Beginn des Geschäftskalenders aus.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Geschäftskalender** verfügbar.  
  
 **Benennungskonvention für Geschäftskalender**  
 Wählen Sie eine Benennungskonvention für den Geschäftskalender aus. Wählen Sie entweder **Kalenderjahrname** oder **Kalenderjahrname +1**aus.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Geschäftskalender** verfügbar.  
  
 **Berichtskalender (oder Marketingkalender)**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Berichtskalender zu erstellen.  
  
 **Startwoche und -monat**  
 Wählen Sie Woche und Monat für den Beginn des Berichtskalenders aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Berichtskalender (oder Marketingkalender)** verfügbar.  
  
 **Muster: Woche nach Monat**  
 Wählen Sie das Muster Woche nach Monat für den Berichtskalender aus.  
  
> [!NOTE]  
>  Diese Option ist nur bei Auswahl von **Berichtskalender (oder Marketingkalender)** verfügbar.  
  
 In der folgenden Tabelle werden die für das Muster Woche nach Monat verfügbaren Optionen aufgeführt.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Woche 445**|Der erste und zweite Monat im Quartal haben jeweils vier Wochen, während der dritte Monat im Quartal fünf Wochen hat.|  
|**Woche 454**|Der erste und dritte Monat im Quartal haben jeweils vier Wochen, während der zweite Monat im Quartal fünf Wochen hat.|  
|**Woche 544**|Der erste Monat im Quartal hat 5 Wochen, während der zweite und dritte Monat im Quartal jeweils vier Wochen haben.|  
  
 **Produktionskalender**  
 Wählen Sie diese Option aus, um eine Zeithierarchie basierend auf einem Produktionskalender zu erstellen.  
  
 **Startwoche und -monat**  
 Wählen Sie Woche und Monat für den Beginn des Produktionskalenders aus.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Produktionskalender** verfügbar.  
  
 **Quartal mit zusätzlichen Zeiträumen**  
 Wählen Sie das Quartal mit den zusätzlichen Zeiträumen aus, oder geben Sie ein entsprechendes Quartal ein.  
  
> [!NOTE]  
>   Diese Option ist nur bei Auswahl von **Produktionskalender** verfügbar.  
  
 **ISO 8601-Kalender**  
 Wählen Sie diese Option aus, um eine Hierarchie basierend auf einem ISO 8601-Kalender zu erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions-Assistent F1-Hilfe](dimension-wizard-f1-help.md)   
 [Dimensionen &#40;Analysis Services Mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
