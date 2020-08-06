---
title: Datenprofil-Viewer F1-Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609977"
---
# <a name="data-profile-viewer-f1-help"></a>Datenprofil-Viewer (F1-Hilfe)
  Verwenden Sie den Datenprofil-Viewer, um die Ausgabe des Datenprofilerstellungs-Tasks anzuzeigen.  
  
 Weitere Informationen zum Verwenden des Datenprofil-Viewers finden Sie unter [Datenprofil-Viewer](control-flow/data-profile-viewer.md). Weitere Informationen zum Verwenden des Datenprofilerstellungs-Tasks, der die Profilausgabe erstellt, die Sie im Datenprofil-Viewer analysieren, finden Sie unter [Einrichten von Datenprofilerstellungs-Tasks](control-flow/data-profiling-task.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Öffnen**  
 Klicken Sie, um nach der gespeicherten Datei zu suchen, die die Ausgabe des Datenprofilerstellungs-Tasks enthält.  
  
 Bereich**Profile**  
 Erweitern Sie die Struktur im Bereich **Profile** , um die Profile anzuzeigen, die in der Ausgabe enthalten sind. Wählen Sie ein Profil aus, um die Ergebnisse für dieses Profil anzuzeigen.  
  
 Bereich**Meldung**  
 Zeigt Statusmeldungen an.  
  
 Bereich**Drilldown**  
 Zeigt die Datensätze an, die mit einem Wert in der Ausgabe übereinstimmen, wenn die vom Datenprofilerstellungs-Task verwendete Datenquelle verfügbar ist.  
  
 Beispiel: Wenn Sie die Ausgabe eines Verteilungsprofils für Spaltenwert für eine Spalte US-Bundesstaat anzeigen, enthält der Bereich **Detaillierte Wertverteilung** möglicherweise eine Zeile für "WA". Doppelklicken Sie auf die Zeile im Bereich **Detaillierte Wertverteilung** , um die Datenreihen anzuzeigen, bei denen der Wert der Bundesstaatspalte im Drilldownbereich „WA“ lautet.  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
  
### <a name="profile-type--column-length-distribution-profile"></a>Profiltyp = Verteilungsprofil für Spaltenlänge  
  
#### <a name="column-length-distribution-profile---column-pane"></a>Verteilungsprofil für Spaltenlänge – \<column>-Bereich  
 **Mindestlänge**  
 Zeigt die Mindestlänge der Werte in dieser Spalte an.  
  
 **Maximale Länge**  
 Zeigt die maximale Länge der Werte in dieser Spalte an.  
  
 **Führende Leerstellen ignorieren**  
 Zeigt an, ob dieses Profil mit einem `IgnoreLeadingSpaces`-Wert von True oder False berechnet wurde. Diese Eigenschaft wurde auf der Seite **Profilanforderungen** vom Editor für den Datenprofilerstellungs-Task festgelegt.  
  
 **Nachfolgende Leerzeichen ignorieren**  
 Zeigt an, ob dieses Profil mit einem `IgnoreTrailingSpaces`-Wert von True oder False berechnet wurde. Diese Eigenschaft wurde auf der Seite **Profilanforderungen** vom Editor für den Datenprofilerstellungs-Task festgelegt.  
  
 **Zeilenanzahl**  
 Zeigt die Anzahl der Zeilen in der Tabelle oder Sicht an.  
  
#### <a name="detailed-length-distribution-pane"></a>Bereich 'Detaillierte Längenverteilung'  
 **Länge**  
 Zeigt die in der Spalte, für die ein Profil erstellt wurde, gefundenen Spaltenlängen an.  
  
 **Count**  
 Zeigt die Anzahl von Zeilen an, in denen der Wert der Spalte, für die ein Profil erstellt wurde, die in der Spalte **Länge** angezeigte Länge hat.  
  
 **Percentage**  
 Zeigt den Prozentsatz der Zeilen an, in denen der Wert der Spalte, für die ein Profil erstellt wurde, die in der Spalte **Länge** angezeigte Länge hat.  
  
### <a name="profile-type--column-null-ratio-profile"></a>Profiltyp = Profil für Spalten-NULL-Verhältnis  
  
#### <a name="column-null-ratio-profile---column-pane"></a>Profil für Spalten-NULL-Verhältnis – \<column>-Bereich  
 **NULL-Anzahl**  
 Zeigt die Anzahl der Zeilen an, in denen die Spalte, für die ein Profil erstellt wurde, einen NULL-Wert aufweist.  
  
 **NULL-Prozentsatz**  
 Zeigt den Prozentsatz der Zeilen an, in denen die Spalte, für die ein Profil erstellt wurde, einen NULL-Wert aufweist.  
  
 **Zeilenanzahl**  
 Zeigt die Anzahl der Zeilen in der Tabelle oder Sicht an.  
  
### <a name="profile-type--column-pattern-profile"></a>Profiltyp = Spaltenmusterprofil  
  
#### <a name="column-pattern-profile---column-pane"></a>Spaltenmusterprofil – \<column>-Bereich  
 **Zeilenanzahl**  
 Zeigt die Anzahl der Zeilen in der Tabelle oder Sicht an.  
  
#### <a name="pattern-distribution-pane"></a>Bereich 'Musterverteilung'  
 **Muster**  
 Zeigt das für die Spalte, für die ein Profil erstellt wurde, berechnete Muster an.  
  
 **Percentage**  
 Zeigt den Prozentsatz der Zeilen an, deren Werte mit dem in der Spalte **Muster** angezeigten Muster übereinstimmen.  
  
### <a name="profile-type--column-statistics-profile"></a>Profiltyp = Spaltenstatistikprofil  
  
#### <a name="column-statistics-profile---column-pane"></a>Spaltenstatistikprofil – \<column>-Bereich  
 **Mindestanforderungen**  
 Zeigt den in der Spalte, für die ein Profil erstellt wurde, gefundenen Mindestwert an.  
  
 **Maximum**  
 Zeigt den in der Spalte, für die ein Profil erstellt wurde, gefundenen Höchstwert an.  
  
 **Mean**  
 Zeigt den Durchschnitt der in der Spalte, für die ein Profil erstellt wurde, gefundenen Werte an.  
  
 **Standardabweichung**  
 Zeigt die Standardabweichung der in der Spalte, für die ein Profil erstellt wurde, gefundenen Werte an.  
  
### <a name="profile-type--column-value-distribution-profile"></a>Profiltyp = Verteilungsprofil für Spaltenwert  
  
#### <a name="column-value-distribution-profile---column-pane"></a>Verteilungsprofil für Spaltenwerte – \<column>-Bereich  
 **Anzahl unterschiedlicher Werte**  
 Zeigt die Anzahl unterschiedlicher Werte an, die in der Spalte, für die ein Profil erstellt wurde, gefunden wurden.  
  
 **Zeilenanzahl**  
 Zeigt die Anzahl der Zeilen in der Tabelle oder Sicht an.  
  
#### <a name="detailed-value-distribution-pane"></a>Bereich 'Detaillierte Wertverteilung'  
 **Wert**  
 Zeigt die in der Spalte, für die ein Profil erstellt wurde, gefundenen unterschiedlichen Werte an.  
  
 **Count**  
 Zeigt die Anzahl von Zeilen an, in denen die Spalte, für die ein Profil erstellt wurde, den in der Spalte **Wert** angezeigten Wert aufweist.  
  
 **Percentage**  
 Zeigt den Prozentsatz der Zeilen an, in denen die Spalte, für die ein Profil erstellt wurde, den in der Spalte **Wert** angezeigten Wert aufweist.  
  
### <a name="profile-type--candidate-key-profile"></a>Profiltyp = Kandidatenschlüsselprofil  
  
#### <a name="candidate-key-profile---table-pane"></a>Kandidatenschlüsselprofil – \<table>-Bereich  
 **Schlüsselspalten**  
 Zeigt die Spalten an, die als Kandidatenschlüssel für die Profilerstellung ausgewählt wurden.  
  
 **Schlüsselstärke**  
 Zeigt die Stärke (als Prozentsatz) der Kandidatenschlüsselspalte oder Kombination von Spalten an. Eine Schlüsselstärke von weniger als 100 % gibt an, dass doppelte Werte vorhanden sind.  
  
#### <a name="key-violations-pane"></a>Bereich 'Schlüsselverletzungen'  
 **\<column1>, \<column2> usw.**  
 Zeigt die doppelten Werte an, die in der Spalte, für die ein Profil erstellt wurde, gefunden wurden.  
  
 **Count**  
 Zeigt die Anzahl der Zeilen an, in denen die angegebene Spalte den in der ersten Spalte angezeigten Wert aufweist.  
  
### <a name="profile-type--functional-dependency-profile"></a>Profiltyp = Funktionales Abhängigkeitsprofil  
  
#### <a name="functional-dependency-profile-pane"></a>Bereich 'Funktionales Abhängigkeitsprofil'  
 **Bestimmende Spalten**  
 Zeigt die als determinante Spalte ausgewählte(n) Spalte(n) an. In dem Beispiel, in dem dieselbe US-Postleitzahl immer denselben Bundesstaat angeben sollte, ist die Postleitzahl die determinante Spalte.  
  
 **Abhängige Spalten**  
 Zeigt die als abhängige Spalte ausgewählte(n) Spalte(n) an. In dem Beispiel, in dem dieselbe US-Postleitzahl immer denselben Bundesstaat angeben sollte, ist der Bundesstaat die abhängige Spalte.  
  
 **Funktionale Abhängigkeitsstärke**  
 Zeigt die Stärke (als Prozentsatz) der funktionalen Abhängigkeit zwischen Spalten an. Eine Schlüsselstärke von weniger als 100 % gibt an, dass es Fälle gibt, in denen der determinante Wert den abhängigen Wert nicht bestimmt. In dem Beispiel, in dem dieselbe US-Postleitzahl immer denselben Bundesstaat angeben sollte, deutet dies wahrscheinlich darauf hin, dass einige Bundesstaatenwerte ungültig sind.  
  
#### <a name="functional-dependency-violations-pane"></a>Bereich 'Funktionale Abhängigkeitsverletzungen'  
  
> [!NOTE]  
>  Ein hoher Prozentsatz an fehlerhaften Werten in den Daten könnte zu unerwarteten Werten aus einem funktionalen Abhängigkeitsprofil führen. Beispiel: 90 % der Zeilen haben den Bundesstaatenwert "WI" für den PLZ-Wert "98052". Das Profil meldet Zeilen, die den korrekten Bundesstaatenwert "WA" aufweisen, als Verletzungen.  
  
 **\<determinant column name>**  
 Zeigt den Wert der determinanten Spalte oder einer Kombination aus Spalten in dieser Instanz einer funktionalen Abhängigkeitsverletzung an.  
  
 **\<dependent column name>**  
 Zeigt den Wert der abhängigen Spalte in dieser Instanz einer funktionalen Abhängigkeitsverletzung an.  
  
 **Unterstützte Anzahl**  
 Zeigt die Anzahl der Zeilen an, in denen der Wert der determinanten Spalte die abhängige Spalte festlegt.  
  
 **Verletzungsanzahl**  
 Zeigt die Anzahl der Zeilen an, in denen der Wert der determinanten Spalte die abhängige Spalte nicht festlegt. (In diesen Zeilen ist der abhängige Wert der Wert, der in der Spalte **\<dependent column name>** angezeigt wird.)  
  
 **Unterstützter Prozentsatz**  
 Zeigt den Prozentsatz der Zeilen an, in denen die determinante Spalte die abhängige Spalte festlegt.  
  
### <a name="profile-type--value-inclusion-profile"></a>Profiltyp = Wertinklusionsprofil  
  
#### <a name="value-inclusion-profile-pane"></a>Bereich 'Wertinklusionsprofil'  
 **Untergeordnete Spalten**  
 Zeigt die Spalte oder Kombination aus Spalten an, für die ein Profil erstellt wurde, um zu ermitteln, ob sie sich in den übergeordneten Spalten befinden.  
  
 **Übergeordnete Spalten**  
 Zeigt die Spalte oder Kombination aus Spalten an, für die ein Profil erstellt wurde, um zu ermitteln, ob sie die Werte aus den untergeordneten Spalten enthalten.  
  
 **Inklusionsstärke**  
 Zeigt die Stärke (als Prozentsatz) der Überlappung zwischen Spalten an. Eine Schlüsselstärke von weniger als 100 % gibt an, dass es Fälle gibt, in denen der untergeordnete Wert nicht in den übergeordneten Werten enthalten ist.  
  
#### <a name="inclusion-violations-pane"></a>Bereich 'Inklusionsverletzungen'  
 **\<column1>, \<column2> usw.**  
 Zeigt die Werte aus der bzw. den untergeordneten Spalte(n) an, die nicht in der bzw. den übergeordneten Spalte(n) gefunden wurden.  
  
 **Count**  
 Zeigt die Anzahl der Zeilen an, in denen die angegebene Spalte den in der ersten Spalte angezeigten Wert aufweist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenprofil-Viewer](control-flow/data-profile-viewer.md)   
 [Datenprofilerstellungs-Task und -Viewer](control-flow/data-profiling-task-and-viewer.md)  
  
  
