---
title: Kreuz Validierungs Formeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 878d88f695b2cdbf3c999c54568304accc54e3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616846"
---
# <a name="cross-validation-formulas"></a>Kreuzvalidierungsformeln
  Wenn Sie einen Kreuzvalidierungsbericht generieren, enthält dieser in Abhängigkeit des Miningmodelltyps (d.h. der zum Erstellen des Modells verwendet Algorithmus) Genauigkeitsmeasures für jedes Modell, den Datentyp des vorhersagbaren Attributs und ggf. den vorhersagbaren Attributwert.  
  
 In diesem Abschnitt werden die im Kreuzvalidierungsbericht verwendeten Measures aufgeführt und die Berechnungsmethode beschrieben.  
  
 Eine Aufschlüsselung der Genauigkeitsmeasures nach Modelltyp finden Sie unter [Measures im Kreuzvalidierungsbericht](measures-in-the-cross-validation-report.md).  
  
## <a name="formulas-used-for-cross-validation-measures"></a>Für Kreuzvalidierungsmeasures verwendete Formeln  
  
> [!NOTE]  
>  **Wichtig:** Diese Genauigkeitsmeasures werden für jedes Zielattribut berechnet. Sie können für jedes Attribut einen Zielwert bestimmen oder weglassen. Wenn ein Fall in einem Dataset über keinen Wert für das Zielattribut verfügt, wird der Fall so behandelt, als hätte er einen Spezialwert, der als *fehlender Wert*bezeichnet wird. Zeilen, die fehlende Werte aufweisen, werden beim Berechnen des Genauigkeitsmeasures für ein bestimmtes Zielattribut nicht gezählt. Da die Ergebnisse für jedes Attribut einzeln berechnet werden, wird das Ergebnis für das Zielattribut nicht beeinflusst, wenn Werte für das Zielattribut, jedoch nicht für andere Attribute vorhanden sind.  
  
|"Measure"|Gilt für|Implementierung|  
|-------------|----------------|--------------------|  
|**True positiv**|Diskretes Attribut, Wert wird angegeben|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|**Richtig negativ**|Diskretes Attribut, Wert wird angegeben|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Fall enthält den Zielwert nicht.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
|**Falsch positiv**|Diskretes Attribut, Wert wird angegeben|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist gleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert enthält.|  
|**Falsch negativ**|Diskretes Attribut, Wert wird angegeben|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Tatsächlicher Wert ist ungleich dem Zielwert.<br /><br /> Modell hat vorhergesagt, dass der Fall den Zielwert nicht enthält.|  
|**Bestanden/fehlgeschlagen**|Diskretes Attribut, kein festgelegtes Ziel|Anzahl der Fälle, die diese Bedingungen erfüllen:<br /><br /> Erfolgreich, wenn der vorhergesagte Status mit der höchsten Wahrscheinlichkeit gleich dem Eingabestatus ist und die Wahrscheinlichkeit größer als der Wert von **Statusschwellenwert**ist.<br /><br /> Andernfalls fehlgeschlagen.|  
|**Skilift**|Diskretes Attribut. Zielwert kann angegeben werden, ist aber nicht erforderlich.|Die mittlere logarithmische Wahrscheinlichkeit für alle Zeilen mit Werten für das Zielattribut, wobei die logarithmische Wahrscheinlichkeit pro Fall als Log(ActualProbability/MarginalProbability) berechnet wird. Um den Mittelwert zu berechnen, wird die Summe der Protokollierungswahrscheinlichkeitswerte durch die Anzahl der Zeilen im Eingabedataset dividiert, wobei Zeilen mit fehlenden Werten für das Zielattribut ausgeschlossen werden.<br /><br /> Als Prognosegüte kann ein negativer oder ein positiver Wert angegeben werden. Ein positiver Wert steht für ein effektives Modell, das die Zufallsvorhersage übertrifft.|  
|**Protokoll Bewertung**|Diskretes Attribut. Zielwert kann angegeben werden, ist aber nicht erforderlich.|Logarithmus der tatsächlichen Wahrscheinlichkeit für jeden Fall, summiert und dann dividiert durch die Anzahl von Zeilen im Eingabedataset, ohne die Zeilen mit fehlenden Werten für das Zielattribut.<br /><br /> Da die Wahrscheinlichkeit als Dezimalbruch dargestellt wird, sind logarithmische Ergebnisse immer negative Zahlen. Je näher das Ergebnis an 0 liegt, desto besser ist es.|  
|**Fallwahrscheinlichkeit**|Cluster|Summe der Clusterwahrscheinlichkeitsergebnisse für alle Fälle, dividiert durch die Anzahl der Fälle in der Partition, ohne die Zeilen mit fehlenden Werten für das Zielattribut.|  
|**Mittlerer absoluter Fehler**|Kontinuierliches Attribut|Summe der absoluten Fehler für alle Fälle in der Partition, dividiert durch die Anzahl der Fälle in der Partition.|  
|**Wurzel des mittleren quadratischen Fehlers**|Kontinuierliches Attribut|Quadratwurzel des mittleren Fehlers für die Partition zum Quadrat.|  
|**RMSE (Root Mean Squared Error = Wurzel der mittleren Fehlerquadratsumme)**|Diskretes Attribut. Zielwert kann angegeben werden, ist aber nicht erforderlich.|Quadratwurzel des Mittelwerts der quadrierten Komplemente des Wahrscheinlichkeitsergebnisses, dividiert durch die Anzahl der Fälle in der Partition, ohne die Zeilen mit fehlenden Werten für das Zielattribut.|  
|**RMSE (Root Mean Squared Error = Wurzel der mittleren Fehlerquadratsumme)**|Diskretes Attribut, kein festgelegtes Ziel|Quadratwurzel des Mittelwerts der quadrierten Komplemente des Wahrscheinlichkeitsergebnisses, dividiert durch die Anzahl der Fälle in der Partition, ohne die Fälle mit fehlenden Werten für das Zielattribut.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Testen und validieren &#40;Data Mining-&#41;](testing-and-validation-data-mining.md)   
 [Kreuzvalidierung &#40;Analysis Services – Data Mining&#41;](cross-validation-analysis-services-data-mining.md)  
  
  
