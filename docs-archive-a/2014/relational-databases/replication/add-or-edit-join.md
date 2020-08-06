---
title: Hinzufügen und Bearbeiten von Join | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.addeditjoin.f1
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3e17b084a232375734601b515821273d482fcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609164"
---
# <a name="add-or-edit-join"></a>Join hinzufügen und Join bearbeiten
  In den Dialogfeldern **Join hinzufügen** und **Join bearbeiten** können Sie Joinfilter für Mergeveröffentlichungen hinzufügen bzw. bearbeiten.  
  
> [!NOTE]  
>  Für das Bearbeiten in einer vorhandenen Veröffentlichung ist eine neue Momentaufnahme für die Veröffentlichung erforderlich. Wenn eine Veröffentlichung Abonnements besitzt, müssen die Abonnements erneut initialisiert werden. Weitere Informationen zum Ändern von Eigenschaften finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](publish/change-publication-and-article-properties.md).  
  
 Durch einen Joinfilter kann eine Tabelle auf der Grundlage der Filterkriterien einer verknüpften Tabelle in der Veröffentlichung gefiltert werden. Normalerweise wird eine übergeordnete Tabelle mithilfe eines parametrisierten Zeilenfilters gefiltert; anschließend definieren Sie, ganz ähnlich wie beim Definieren eines Joins zwischen Tabellen, einen oder mehrere Joinfilter. Durch die Joinfilter wird der Zeilenfilter so erweitert, dass die Daten in den verknüpften Tabellen nur repliziert werden, wenn sie mit der Joinfilterklausel übereinstimmen.  
  
 Joinfilter folgen normalerweise den Beziehungen zwischen Primär- und Fremdschlüssel, die für die Tabellen, auf die sie angewendet werden, definiert wurden. Sie sind jedoch nicht streng auf diese Primär-/Fremdschlüssel-Beziehungen festgelegt. Der Joinfilter kann auf einer beliebigen Logik basieren, durch die verknüpfte Daten in zwei Artikeltabellen verglichen werden.  
  
> [!IMPORTANT]  
>  Joinfilter können zwar eine unbegrenzte Anzahl von Tabellen umfassen, Filter mit sehr vielen Tabellen können sich jedoch nachteilig auf die Leistung während der Mergeverarbeitung auswirken. Wenn Sie Joinsfilter für fünf oder mehr Tabellen erstellen, sollten Sie andere Lösungen in Betracht ziehen: Kleinere Tabellen, Tabellen, die nicht geändert werden, oder Tabellen, bei denen es sich primär um Nachschlagetabellen handelt, sollten in diesem Fall nicht gefiltert werden. Verwenden Sie Joinfilter nur zwischen Tabellen, die für die Abonnenten partitioniert werden müssen.  
  
## <a name="options"></a>Tastatur  
 Dieses Dialogfeld enthält einen dreistufigen Vorgang zur Erstellung eines Joinfilters zwischen zwei Tabellen. Wenn mehrere Joinfilter erstellt werden sollen, muss der Vorgang mithilfe des Dialogfelds mehrfach ausgeführt werden.  
  
1.  **Überprüfen Sie die gefilterte Tabelle, und wählen Sie die verknüpfte Tabelle aus**  
  
    -   Wenn Sie einen neuen Join hinzufügen, überprüfen Sie, ob es sich bei der Tabelle im Textfeld **Gefilterte Tabelle** um die richtige Tabelle handelt. (Wenn das nicht der Fall ist, klicken Sie auf **Abbrechen**, wählen Sie die richtige Tabelle auf der Seite **Tabellenzeilen filtern** aus, und klicken Sie auf **Join hinzufügen** , um zu diesem Dialogfeld zurückzukehren.) Wählen Sie anschließend eine Tabelle aus dem Dropdownlistenfeld **Verknüpfte Tabelle** aus.  
  
    -   Wenn Sie einen vorhandenen Join bearbeiten, werden die Tabellennamen bereits angegeben und können nicht geändert werden. Um die an dem Join beteiligten Tabellen zu ändern, müssen Sie den vorhandenen Joinfilter auf der Seite **Tabellenzeilen filtern** löschen und einen neuen Join zwischen zwei anderen Tabellen erstellen.  
  
2.  **Erstellen Sie die Joinanweisung**  
  
    -   Wenn Sie einen neuen Join hinzufügen, wählen Sie **Anweisung mit dem Generator erstellen** oder **Joinanweisung manuell schreiben**aus. Wenn Sie bereits begonnen haben, den Join manuell zu schreiben, können Sie den Generator nicht mehr verwenden.  
  
         Wenn Sie auswählen, dass der Generator verwendet werden soll, verwenden Sie die Spalten im Raster (**Konjunktion**, **Gefilterte Tabellenspalte**, **Operator**und **Verknüpfte Tabellenspalte**), um eine Joinanweisung zu erstellen. Jede Spalte im Raster enthält ein Dropdownlistenfeld, mit dessen Hilfe Sie zwei Spalten und einen Operator ( **=** , **<>** , **<=** , **\<**, **>=** , **>** , **like**) auswählen können. Die Ergebnisse werden im Textbereich **Vorschau** angezeigt. Wenn mehr als ein Spaltenpaar an dem Join beteiligt ist, wählen Sie in der**Conjunction** -Spalte eine Konjunktion ( **AND**oder **OR** ) aus, und geben Sie zwei weitere Spalten und einen weiteren Operator ein.  
  
         Wenn Sie ausgewählt haben, dass die Anweisung manuell geschrieben wird, schreiben Sie die Joinanweisung im Textbereich **Joinanweisung** . Um Spalten mit Drag und Drop in den Textbereich **Joinanweisung** zu verschieben, verwenden Sie die Listenfelder **Gefilterte Tabellenspalten** und **Verknüpfte Tabellenspalten** .  
  
    -   Wenn Sie einen vorhandenen Join bearbeiten, müssen Sie die Änderungen manuell vornehmen.  
  
3.  **Geben Sie Joinoptionen an**  
  
    -   Wenn es sich bei der Spalte, die Sie mit der gefilterten Tabelle verknüpfen, um eine eindeutige Spalte handelt, wählen Sie **Eindeutiger Schlüssel**aus. Der Mergeprozess verfügt über spezielle Leistungsoptimierungen, sofern die Spalte eindeutig ist.  
  
        > [!CAUTION]  
        >  Durch Auswahl dieser Option kennzeichnen Sie, ob es sich bei der Beziehung zwischen der untergeordneten und der übergeordneten Tabelle in einem Joinfilter um eine 1:1- oder eine 1:n-Beziehung handelt. Wählen Sie diese Option nur aus, wenn es eine Einschränkung für die verknüpfte Spalte in der übergeordneten Tabelle gibt, durch die die Eindeutigkeit sichergestellt wird. Wenn die Option nicht richtig festgelegt wird, kann eine mangelnde Konvergenz der Daten die Folge sein.  
  
    -   Nur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Standardmäßig werden Änderungen durch die Mergereplikation während der Synchronisierung zeilenweise verarbeitet. Damit miteinander verbundene Änderungen als Einheit verarbeitet werden, wählen Sie **Logischer Datensatz**aus. Diese Option ist nur verfügbar, wenn die Anforderungen für die Verwendung logischer Datensätze durch den Artikel und die Veröffentlichung erfüllt werden. Weitere Informationen finden Sie im Abschnitt „Überlegungen zum Verwenden logischer Datensätze“ in [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Nachdem Sie einen Filter hinzugefügt oder bearbeitet haben, klicken Sie auf **OK** , um die Änderungen zu speichern und das Dialogfeld zu schließen. Der von Ihnen angegebene Filter wird analysiert und für die Tabelle in der SELECT-Klausel ausgeführt. Wenn die Filteranweisung Syntaxfehler oder andere Probleme enthält, werden Sie benachrichtigt und können die Filteranweisung bearbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Filtern von veröffentlichten Daten](publish/filter-published-data.md)   
 [Join Filters](merge/join-filters.md)   
 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)  
  
  
