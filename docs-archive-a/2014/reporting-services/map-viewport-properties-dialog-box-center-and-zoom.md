---
title: Eigenschaften des Kartenviewports (Dialog Feld), zentrieren und vergrößern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615854"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a>Eigenschaften des Kartenviewports (Dialogfeld), Zentrieren und zoomen
  Wählen Sie **Zentrieren und zoomen** aus, um im Dialogfeld **Viewporteigenschaften der Karte** die Mittelpunktsicht und den Zoomfaktor für eine Karte festzulegen. Nachdem Sie eine Kartendatenquelle und die Begrenzungen der Karte angegeben haben, die Sie in den Bericht einschließen möchten, können Sie den Ansichtmittelpunkt und den Zoomfaktor angeben, um die Kartenanzeige weiter zu steuern. Die Optionen hängen von der Methode ab, die Sie verwenden, um Werte für Mittelpunkt und Zoom anzugeben. Klicken Sie auf die Schaltfläche **Ausdruck** (*fx*), um einen Ausdruck zu bearbeiten, der den Wert der Option festlegt.  
  
## <a name="options"></a>Optionen  
 **Festlegen eines Ansichtmittelpunktes und einer Zoomstufe**  
 Wählen Sie diese Option aus, um benutzerdefinierte Werte für den Ansichtmittelpunkt und die Zoomstufe anzugeben.  
  
 **Karte zentrieren, um eine Kartenebene anzuzeigen**  
 Wählen Sie diese Option aus, um eine Ebene anzugeben und den Mittelpunkt der Ansicht automatisch auf ihre Kartendaten festzulegen. Legen Sie den Mittelpunkt der Ansicht z. B. auf "LineLayer1" fest.  
  
 **Karte zentrieren, um ein eingebettetes Kartenelement anzuzeigen**  
 Wählen Sie diese Option aus, um den Mittelpunkt der Ansicht auf ein bestimmtes datengebundenes Kartenelement festzulegen. Damit diese Option angegeben werden kann, müssen die räumlichen Daten eine Beziehung mit analytischen Daten aufweisen.  
  
 Legen Sie den Mittelpunkt der Ansicht z. B. auf das Kartenelement fest, für das der Name des Übereinstimmungsfelds [City] und der Übereinstimmungswert "Seattle" lautet.  
  
 **Karte zentrieren, um alle datengebundenen Kartenelemente anzuzeigen**  
 Wählen Sie diese Option aus, um den Mittelpunkt der Ansicht auf alle Kartenelemente in der Ebene festzulegen. Damit diese Option angegeben werden kann, müssen die räumlichen Daten eine Beziehung mit analytischen Daten aufweisen.  
  
 Legen Sie den Mittelpunkt der Ansicht z. B. auf die Polygonblasenebene fest, auf der Orte angezeigt werden und deren Blasengröße sich auf die Einwohnerzahl bezieht. Beim Berechnen des Mittelpunkts für den Viewport werden nur Orte mit einer entsprechenden Einwohnerzahl eingeschlossen.  
  
 **Zentrier- und Zoomoptionen**  
 Wählen Sie eine Option aus, um den Ansichtmittelpunkt und die Zoomstufe anzugeben.  
  
 **Mittelpunkt X anzeigen (%)**  
 Die horizontale Koordinate. Der Standardwert beträgt 50 %. Er legt fest, dass die Ansicht in der Mitte zwischen dem minimalen und dem maximalen horizontalen Wert zentriert wird.  
  
 **Mittelpunkt Y anzeigen (%)**  
 Die vertikale Koordinate. Der Standardwert ist 50 %. Er legt fest, dass die Ansicht in der Mitte zwischen dem minimalen und dem maximalen vertikalen Wert zentriert wird.  
  
 **Vergrößerungsstufe (%)**  
 Der Zoomfaktor. Der Standardwert ist 100 %. Er gibt keine Vergrößerung an.  
  
 **Ansicht auf diese Ebene zentrieren**  
 Gibt den Namen der Ebene an.  
  
 **Ansicht auf das Kartenelement zentrieren, das dieser Bedingung entspricht**  
 Das schreibgeschützte Feld, das angezeigt wird, wird verwendet, um Kartendaten und analytische Daten abzugleichen. Geben Sie den Wert an, der für den Abgleich verwendet werden soll. Die Ansicht wird automatisch auf dieses Kartenelement zentriert. Beispiel: NAME = TEXAS. Standardmäßig ist der Datentyp für die Bedingung "String", und bei der Übereinstimmung wird die Groß-/Kleinschreibung beachtet.  
  
 Für den Abgleich mit einem Feld, das einen anderen Datentyp aufweist, müssen Sie einen Ausdruck schreiben, der diesen Datentyp ergibt. Wenn das Übereinstimmungsfeld z. B. eine fünfstellige Postleitzahl ist, die als ganze Zahl gespeichert wird, müssen Sie zum Angeben der Postleitzahl 98053 den Ausdruck "=98053" verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Karten &#40;Berichts-Generator und SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
