---
title: Zeichen folgen Speicher und-Sortierung in tabellarischen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8516f0ad-32ee-4688-a304-e705143642ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3aad4cf16c39897bc0796f4fb161eaf39abdb5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87723109"
---
# <a name="string-storage-and-collation-in-tabular-models"></a>Zeichenfolgenspeicher und -sortierung in Tabellenmodellen
  Zeichenfolgen (Textwerte) werden in einem stark komprimierten Format in Tabellenmodellen gespeichert. Aufgrund dieser Komprimierung erhalten Sie unter Umständen unerwartete Ergebnisse, wenn Sie vollständige Zeichenfolgen oder Teilzeichenfolgen abrufen. Da das Zeichenfolgengebietsschema und die Sortierungen hierarchisch vom nächsten übergeordneten Objekt geerbt werden, wenn die Zeichenfolgensprache nicht explizit definiert wird, können das Gebietsschema und die Sortierung des übergeordneten Objekts beeinflussen, wie die einzelnen Zeichenfolgen gespeichert werden, und ob die Zeichenfolge entsprechend der übergeordneten Sortierung eindeutig ist oder mit ähnlichen Zeichenfolgen zusammengefügt wurde.  
  
 In diesem Thema wird der Mechanismus für die Komprimierung und Speicherung von Zeichenfolgen beschrieben. Außerdem finden Sie Beispiele dazu, wie Sortierung und Sprache die Ergebnisse von Textformeln in Tabellenmodellen beeinflussen.  
  
## <a name="storage"></a>Storage  
 In Tabellenmodellen werden alle Daten stark komprimiert, um eine zu hohe Auslastung des Arbeitsspeichers zu vermeiden. Infolgedessen werden alle Zeichenfolgen, die als lexikalisch äquivalent eingestuft werden können, nur einmal gespeichert. Die erste Instanz der Zeichenfolge wird als kanonische Darstellung verwendet, und anschließend wird jede entsprechende Zeichenfolge im gleichen komprimierten Wert wie das erste Vorkommen indiziert.  
  
 Die Hauptfrage lautet folgendermaßen: Woraus besteht eine lexikalisch äquivalente Zeichenfolge? Zwei Zeichenfolgen werden als lexikalisch äquivalent eingestuft, wenn sie als das gleiche Wort gelten. Wenn Sie zum Beispiel in einem englischen Wörterbuch den Begriff **violin** (Geige) suchen, finden Sie möglicherweise den Eintrag **Violin** oder **violin**, abhängig von den redaktionellen Richtlinien, die für das Wörterbuch gelten, doch im Allgemeinen werden beide Begriffe als identisch bzw. äquivalent betrachtet, und die unterschiedliche Schreibweise mit kleinem bzw. großem Anfangsbuchstaben wird ignoriert. In einem Tabellenmodell ist der entscheidende Faktor, durch den bestimmt wird, ob zwei Zeichenfolgen lexikalisch äquivalent sind, nicht die redaktionelle Richtlinie oder die Benutzereinstellung, sondern das Gebietsschema und die Sortierreihenfolge, die der Spalte zugewiesen sind.  
  
 Daher sollte die Entscheidung, ob Groß- und Kleinschreibung als identisch oder verschieden behandelt werden sollen, von der Sortierung und dem Gebietsschema abhängen. Für ein bestimmtes Wort innerhalb des Gebietsschemas dient das erste Vorkommen des Wortes, das in einer bestimmten Spalte enthalten ist, daher als kanonische Darstellung des Begriffs, und die Zeichenfolge wird in einem nicht komprimiertem Format gespeichert.  Alle anderen Zeichenfolgen werden anhand des ersten Vorkommens getestet, und wenn sie dem Äquivalenztest entsprechen, werden sie dem komprimierten Wert des ersten Vorkommens zugewiesen. Wenn die komprimierten Werte später abgerufen werden, werden sie mit dem nicht komprimierten Wert des ersten Vorkommens der Zeichenfolge dargestellt.  
  
 Ein Beispiel veranschaulicht dieses Verfahren. Die folgende Spalte "Klassifizierung - Englisch" wurde einer Tabelle entnommen, die Informationen zu Pflanzen und Bäumen enthält. Für jede Pflanze (die Namen der Pflanzen werden hier nicht angezeigt) wird in der Klassifizierungsspalte die allgemeine Kategorie der Pflanze angegeben.  
  
|Klassifizierung - Englisch|  
|-------------------------------|  
|trEE|  
|PlAnT|  
|trEE|  
|PlAnT|  
|Plant|  
|Struktur|  
|PlAnT|  
|trEE|  
|tree|  
|PlAnT|  
|trEE|  
  
 Möglicherweise stammten die Daten aus zahlreichen verschiedenen Quellen, sodass die Schreibweise und die Verwendung von Akzenten inkonsistent war und die Unterschiede unverändert in der relationalen Datenbank gespeichert wurden. Im Allgemeinen sind die Werte jedoch entweder **Plant** oder **Tree**, wobei sich nur die Schreibweise (groß/klein) unterscheidet.  
  
 Wenn diese Werte in ein tabellarisches Modell geladen werden, das die Standardsortierung und die Sortierreihenfolge für Englisch (USA) verwendet, ist die Groß-/Kleinschreibung nicht wichtig, sodass für die gesamte Spalte nur zwei Werte gespeichert werden:  
  
|Klassifizierung - Englisch|  
|-------------------------------|  
|trEE|  
|PlAnT|  
  
 Wenn Sie in Ihrem Modell die Spalte " **Klassifizierung-Englisch**" verwenden, sehen Sie, wo Sie die Anlagen Klassifizierung anzeigen, nicht die ursprünglichen Werte mit den unterschiedlichen Verwendungsmöglichkeiten von Groß-und Kleinbuchstaben, sondern nur die erste Instanz. Der Grund hierfür ist, dass alle Groß- und Kleinschreibungsvarianten von **tree** in dieser Sortierung und diesem Gebietsschema als äquivalent betrachtet werden. Daher wurde nur eine Zeichenfolge beibehalten, und die erste Instanz der Zeichenfolge, die vom System gefunden wird, wird gespeichert.  
  
> [!WARNING]  
>  Möglicherweise möchten Sie festlegen, welche Zeichenfolge als erste gespeichert werden soll (unter Berücksichtigung der von Ihnen als korrekt eingestuften Schreibweise), doch dies kann sich als sehr schwierig erweisen. Es existiert keine einfache Möglichkeit, im Voraus zu bestimmen, welche Zeile zuerst von der Engine verarbeitet werden soll, vorausgesetzt, dass alle Werte als identisch eingestuft werden. Stattdessen sollten beim Festlegen des Standardwerts alle Zeichenfolgen bereinigt werden, bevor das Modell geladen wird.  
  
## <a name="locale-and-collation-order"></a>Gebietsschema und die Sortierreihenfolge  
 Wenn Zeichenfolgen (Textwerte) miteinander verglichen werden, wird Äquivalenz normalerweise durch den kulturellen Aspekt bestimmt, der die Interpretation solcher Zeichenfolgen beeinflusst. In einigen Kulturen kann sich die Bedeutung einer Zeichenfolge durch einen Akzent oder die Großschreibung eines Zeichens vollständig ändern. Daher werden solche Unterschiede in der Regel berücksichtigt, wenn sie Äquivalenz für eine bestimmte Sprache oder einen Bereich festlegen.  
  
 Wenn Sie Ihren Computer verwenden, ist er normalerweise bereits entsprechend Ihren eigenen kulturellen Erwartungen und dem linguistischen Verhalten konfiguriert, und Zeichenfolgenoperationen wie das Sortieren und Vergleichen von Textwerten verhalten sich erwartungsgemäß. Die Einstellungen, die sprachspezifisches Verhalten steuern, werden durch die **Gebietsschema- und Regionseinstellungen** in Windows definiert. Anwendungen lesen diese Einstellungen und ändern deren Verhalten entsprechend. In einigen Fällen verfügt eine Anwendung möglicherweise über eine Funktion, die Ihnen das Ändern des kulturellen Verhaltens der Anwendung oder der Methode zum Zeichenfolgenvergleich ermöglicht.  
  
 Wenn Sie eine Tabellenmodelldatenbank erstellen, erbt die Datenbank standardmäßig diese kulturellen und linguistischen Einstellungen im Formular einer Sprachen-ID und -sortierung.  
  
-   Die Sprachen-ID definiert den Zeichensatz, den Sie entsprechend der Kultur für die Zeichenfolgen verwenden möchten.  
  
-   Die Sortierung definiert die Reihenfolge der Zeichen und ihrer Äquivalenz.  
  
 Wichtig: Eine Sprachen-ID kennzeichnet nicht nur eine Sprache, sondern auch das Land oder die Region, in dem bzw. der die Sprache verwendet wird. Jede Sprachen-ID weist auch eine Standardsortierungsspezifikation auf. Weitere Informationen zu Sprachen-IDs finden Sie unter [Von Microsoft zugewiesene Gebietsschemabezeichner (LCIDs)](https://msdn.microsoft.com/goglobal/bb964664.aspx). Sie können die LCID DEC-Spalte verwenden, um die richtige ID zu erhalten, wenn Sie einen Wert manuell einfügen. Weitere Informationen zum SQL-Konzept von Sortierungen finden Sie unter [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations). Informationen zu den Sortierungskennzeichnern und den Vergleichsstilen für Windows-Sortierungsnamen finden Sie unter [Name der Windows-Sortierung &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql). Das Thema [SQL Server-Sortierungsname &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) ordnet die Namen der Windows-Sortierung den für SQL verwendeten Namen zu.  
  
 Sobald die Tabellenmodelldatenbank erstellt wurde, erben alle neuen Objekte im Modell die Sprach- und Sortierattribute von den Datenbankattributen. Dies gilt für alle Objekte. Der Vererbungspfad beginnt beim Objekt und sucht das übergeordnete Element für jedes zu erbende Sprach- und Sortierattribut. Wenn keine Attribute gefunden werden, wird der Vorgang am Anfang fortgesetzt, und die Sprach- und Sortierattribute werden auf der Datenbankebene gesucht. Anders ausgedrückt: Wenn Sie keine Sprach-und Sortierattribute für ein Objekt angeben, erbt das Objekt standardmäßig die Attribute des nächsten übergeordneten Elements.  
  
 Für Spalten werden die Sprach-und Sortierattribute bei der Erstellung gemäß den folgenden Regeln geerbt:  
  
1.  Das übergeordnete Dimensionsobjekt wird nach Sprach- und Sortierattributen durchsucht. Wenn beide Werte vorhanden sind, werden sie in die Spaltenattribute kopiert. Wenn nur ein Wert vorhanden ist, wird der andere Wert vom vorhandenen Wert abgeleitet, und beide Werte werden. zugewiesen Falls kein Wert vorhanden ist, fahren Sie mit dem nächsten Schritt fort.  
  
2.  Das Datenbankobjekt wird mit der gleichen Methode durchsucht, die in Schritt 1 für Dimensionen beschrieben wurde. Wenn keine Attribute gefunden werden, fahren Sie mit dem nächsten Schritt fort.  
  
3.  Das Serverobjekt wird mit der gleichen Methode durchsucht, die in Schritt 1 für Dimensionen beschrieben wurde. Wenn keine Attribute gefunden werden, wird in der Spalte die Windows-Sprachen-ID verwendet, und das Sortierattribut wird von diesem Wert abgeleitet.  
  
 Wichtig: Normalerweise haben die Sprachen-ID und die Sortierreihenfolge in der Quelldatenbank nur wenige oder gar keine Auswirkungen auf die Speicherung von Werten in der Tabellenmodellspalte. Eine Ausnahme liegt vor, wenn die Quelldatenbank die angeforderten Werte transformiert oder filtert.  
  
  
