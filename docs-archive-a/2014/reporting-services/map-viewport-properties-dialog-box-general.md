---
title: Eigenschaften des Kartenviewports (Dialog Feld), allgemein | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608384"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Eigenschaften des Kartenviewports (Dialogfeld), Allgemein
  Wählen Sie im Dialogfeld **Viewporteigenschaften zuordnen** den Bereich **Allgemein** aus, um das Koordinatensystem, die Projektion und die Begrenzungsoptionen zu ändern.  
  
## <a name="options"></a>Tastatur  
 **Koordinatensystem**  
 Geben Sie den Typ des Koordinatensystems an, das für die Kartendaten verwendet wird.  
  
-   **Planar** Wählen Sie diese Option aus, wenn Kartendaten als x- und y-Koordinaten vorliegen, z. B. zum Erstellen von Plänen.  
  
-   **Geografisch** Wählen Sie diese Option aus, wenn Kartendaten in Längen- und Breitenkoordinaten vorliegen, z. B. für Orte.  
  
 **Projektion**  
 Geben Sie die Methode an, die verwendet werden soll, um geografische Koordinaten auf eine zweidimensionale Oberfläche zu projizieren. Wählen Sie eine Projektion aus, die mit den visuell darzustellenden Daten kompatibel ist. Die vier räumlichen Eigenschaften, die von der Projektion betroffen sind, sind Bereich, Form, Entfernung und Richtung. Bei Ansichten der Erde hängt eine gute Auswahl der Projektion von der Mittelpunktansicht, den Kartenbegrenzungen und dem Zoomfaktor ab.  
  
 Jede der folgenden Projektionen wahrt mindestens eine der folgenden räumlichen Eigenschaften:  
  
-   **Equirectangular** Wählen Sie diese Option aus, um Längen- und Breitengrad als kartesische Koordinaten zu verwenden.  
  
-   **Mercator** Wählen Sie diese gängige Projektion für kleinere Bereiche, zum Erzielen von weniger Verzerrung um den Äquator oder wenn Sie eine Kartenebene mit einer vorhandenen Kachelebene hinzufügen möchten, die die Mercator-Projektion verwendet.  
  
-   **Robinson** Wählen Sie diese Option, damit große Bereich weniger verzerrt sind, die vom Äquator bis zu den Polen reichen. Diese Projektion wurde von Arthur H. Robinson im Jahr 1963 entwickelt.  
  
-   **Fahey** Wählen Sie diese Option, damit große Bereich weniger verzerrt sind, die vom Äquator bis zu den Polen reichen. Diese Projektion wurde von Lawrence Fahey im Jahr 1975 entwickelt.  
  
-   **Eckert1** Wählen Sie diese Option, um äquidistante Parallelen für die Breitengrade und gerade Linien für die Längenmeridiane zu verwenden.  
  
-   **Eckert3** Wählen Sie diese Option, um äquidistante Parallelen für die Breitengrade und gekrümmte Linien für die Längenmeridiane zu verwenden.  
  
-   **HammerAitoff** Wählen Sie diese Option für Pol- oder Weltkarten.  
  
-   **Wagner3** Wählen Sie diese Option für Weltkarten.  
  
-   **Bonne** Wählen Sie diese Option, um die Welt wie in einem Atlas anzuzeigen.  
  
 **Seitenumbruchoptionen**  
 Wählen Sie Optionen aus, um anzugeben, wie der Inhalt an eine Berichtsseite angepasst wird.  
  
 **Begrenzungsoptionen**  
 Geben Sie die Unter- und die Obergrenzen für Koordinaten an, um zu steuern, welcher Teil der Karte im Bericht angezeigt wird.  
  
 **Minimum (X)**  
 Niedrigster X-Wert. Nur für **Planar** verfügbar.  
  
 **Maximum (X)**  
 Höchster X-Wert. Nur für **Planar** verfügbar.  
  
 **Minimum (Y)**  
 Niedrigster Y-Wert. Nur für **Planar** verfügbar.  
  
 **Maximum (Y)**  
 Höchster Y-Wert. Nur für **Planar** verfügbar.  
  
 **Minimale Länge**  
 Niedrigster Längenwert. Nur für **Geografisch** verfügbar.  
  
 **Maximale Länge**  
 Höchster Längenwert. Nur für **Geografisch** verfügbar.  
  
 **Minimale Breite**  
 Niedrigster Breitenwert. Nur für **Geografisch** verfügbar.  
  
 **Maximale Breite**  
 Höchster Breitenwert. Nur für **Geografisch** verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Karten &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
