---
title: Verwenden der DQS-Standard-Wissensdatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3261c7af28bb5710ede203d1fe27c6540286e9f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610047"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Verwenden der DQS-Standard-Wissensdatenbank
  In diesem Thema wird die Standard-Wissensdatenbank **DQS-Daten**beschrieben, die mit [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) installiert wird. Dies ist eine vordefinierte Standardwissensdatenbank, die die folgenden Domänen enthält:  
  
-   **Land/Region**: Enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zweibuchstabige Abkürzung, dreibuchstabige Abkürzung und dreistelligen Code für jeden Standort.  Der führende Wert wird auf den langen Landnamen festgelegt.  
  
-   **Land/Region (dreibuchstabig führend)**: Enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zweibuchstabige Abkürzung, dreibuchstabige Abkürzung und dreistelligen Code für jeden Standort.  Führende Werte ist auf die dreibuchstabige Abkürzung des Lands festgelegt.  
  
-   **Land/Region (zweibuchstabig führend)**: Enthält die konventionellen langen Namen (offizieller Name wie von Land/Region festgelegt) und Kurznamen (allgemeiner Name, der in Listen, auf Karten usw. verwendet wird), zweibuchstabige Abkürzung, dreibuchstabige Abkürzung und dreistelligen Code für jeden Standort.  Führender Wert ist auf die zweibuchstabige Abkürzung des Lands festgelegt.  
  
-   **US - Countys**: Enthält eine Liste von US-Countys.  
  
-   **US - Nachname**: Enthält eine Liste von Nachnamen, die in der Volkszählung 2000 mindestens 100 Mal vorkamen.  
  
-   **US - Orte**: Enthält eine Liste von Orten für die 50 Staaten, das District of Columbia und Puerto Rico, die aus der Volkszählung 2010 stammen.  
  
-   **US - Bundesstaat**: Enthält den konventionellen langen (offiziellen) Namen und die zweibuchstabige Abkürzung für jeden Staat der USA. Führender Wert ist auf den konventionellen Staatennamen festgelegt.  
  
-   **US-Bundesstaat (zwei buchstabige Überschrift)**: enthält den konventionellen langen (offiziellen) Namen und die zwei buchstabige Abkürzung für jeden Staat in US. Führender Wert ist auf die zweibuchstabige Abkürzung des Bundesstaats festgelegt.  
  
## <a name="using-the-default-knowledge-base"></a>Verwenden der Standard-Wissensdatenbank  
 Sie können die DQS-Standardwissensdatenbank (DQS-Daten) auf folgende Weise verwenden:  
  
-   Schnelles Starten und Ausführen eines Data Quality-Bereinigungsprojekts mithilfe der Standardwissensdatenbank, ohne zuerst in DQS eine neue Wissensdatenbank erstellen zu müssen.  
  
-   Ausführen der Aktivitäten Domänenverwaltung, Wissensermittlung oder Abgleichsrichtlinie für die Standardwissensdatenbank. Klicken Sie hierzu auf dem **Data Quality Client Home Screen** auf [Wissensdatenbank öffnen](../../2014/data-quality-services/data-quality-client-home-screen.md), wählen Sie die Wissensdatenbank **DQS-Daten** auf dem Bildschirm **Wissensdatenbank öffnen** aus, und wählen Sie dann die erforderliche Aktivität im Bereich **Aktivität auswählen** aus. Klicken Sie zum Fortfahren auf **Weiter** .  
  
-   Erstellen einer neuen Wissensdatenbank mithilfe der Standardwissensdatenbank. Informationen zum Erstellen einer Wissensdatenbank aus einer vorhandenen Wissensdatenbank finden Sie unter [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).  
  
-   Verwendung in der [Komponente zur DQS-Bereinigung in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) und im [Master Data Services-Add-In für Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [DQS-Wissensdatenbanken und -Domänen](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
