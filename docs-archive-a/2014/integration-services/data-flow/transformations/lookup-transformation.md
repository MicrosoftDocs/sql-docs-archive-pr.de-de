---
title: Transformation für Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptrans.f1
helpviewer_keywords:
- Lookup transformation
- joining columns [Integration Services]
- cache [Integration Services]
- match exactly [Integration Services]
- lookups [Integration Services]
- exact matches [Integration Services]
ms.assetid: de1cc8de-e7af-4727-b5a5-a1f0a739aa09
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 567c5d95c2ee7c15ea5c541f7fe2010d46ba36f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621094"
---
# <a name="lookup-transformation"></a>Transformation für Suche
  Die Transformation für die Suche führt Suchvorgänge aus, indem Daten in Eingabespalten mit Spalten in einem Verweisdataset verknüpft werden. Mithilfe der Transformation für Suche können Sie auf zusätzliche Informationen in einer zugehörigen Tabelle zugreifen, die auf Werten in gemeinsamen Spalten basiert.  
  
 Das Verweisdataset kann eine Cachedatei, eine vorhandene Tabelle oder Sicht, eine neue Tabelle oder das Ergebnis einer SQL-Abfrage sein. Die Transformation für Suche stellt entweder mithilfe eines OLE DB-Verbindungs-Managers oder eines Cacheverbindungs-Managers eine Verbindung mit dem Verweisdataset her. Weitere Informationen finden Sie unter [OLE DB-Verbindungs-Manager](../../connection-manager/ole-db-connection-manager.md) und [Cacheverbindungs-Manager](../../connection-manager/cache-connection-manager.md)  
  
 Es gibt folgende Möglichkeiten, um die Transformation für die Suche zu konfigurieren:  
  
-   Wählen Sie den Verbindungs-Manager aus, den Sie verwenden möchten. Wenn Sie eine Verbindung mit einer Datenbank herstellen möchten, wählen Sie einen OLE DB-Verbindungs-Manager aus. Wenn Sie eine Verbindung mit einer Cachedatei herstellen möchten, wählen Sie einen Cacheverbindungs-Manager aus.  
  
-   Geben Sie die Tabelle oder Sicht an, die das Verweisdataset enthält.  
  
-   Generieren Sie ein Verweisdataset, indem Sie eine SQL-Anweisung angeben.  
  
-   Geben Sie Joins zwischen der Eingabe und dem Verweisdataset an.  
  
-   Fügen Sie der Ausgabe der Transformation für Suche Spalten aus dem Verweisdataset hinzu.  
  
-   Konfigurieren Sie die Optionen für die Zwischenspeicherung.  
  
 Die Transformation für Suche unterstützt die folgenden Datenbankanbieter für den OLE DB-Verbindungs-Manager:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   Oracle  
  
-   DB2  
  
 Die Transformation für Suche versucht, einen Gleichheitsjoin zwischen Werten in der Transformationseingabe und Werten im Verweisdataset auszuführen. (Ein Gleichheitsjoin bedeutet, dass jede Zeile in der Transformationseingabe mindestens einer Zeile aus dem Verweisdataset entsprechen muss.) Wenn ein Gleichheitsjoin nicht ausgeführt werden kann, führt die Transformation für Suche eine der folgenden Aktionen aus:  
  
-   Falls im Verweisdataset kein entsprechender Eintrag vorhanden ist, wird kein Join ausgeführt. Standardmäßig werden bei Verwendung einer Transformation für Suche die Zeilen ohne übereinstimmende Einträge als Fehler behandelt. Sie haben jedoch die Möglichkeit, die Transformation für Suche so zu konfigurieren, dass die Zeilen an eine Ausgabe nicht übereinstimmender Einträge weitergeleitet werden. Weitere Informationen finden Sie unter [Transformations-Editor für Suche &#40;Seite „Allgemein“&#41;](../../lookup-transformation-editor-general-page.md) und [Transformations-Editor für Suche &#40;Seite „Fehlerausgabe“&#41;](../../lookup-transformation-editor-error-output-page.md).  
  
-   Sind in der Verweistabelle mehrere übereinstimmende Einträge vorhanden, gibt die Transformation für Suche nur den ersten übereinstimmenden Eintrag zurück, der von der Suchabfrage zurückgegeben wird. Wenn mehrere übereinstimmende Einträge gefunden werden, wird von der Transformation für Suche nur dann ein Fehler bzw. eine Warnung generiert, wenn die Transformation für das Laden des gesamten Verweisdatasets in den Cache konfiguriert ist. In diesem Fall, wird von der Transformation für Suche eine Warnung generiert, wenn die Transformation während des Füllens des Caches mehrere übereinstimmende Einträge erkennt.  
  
 Der Join kann ein zusammengesetzter Join sein. Das bedeutet, dass Sie mehrere Spalten in der Transformationseingabe mit Spalten im Verweisdataset verknüpfen können. Die Transformation unterstützt Joinspalten eines beliebigen Datentyps, außer DT_R4, DT_R8, DT_TEXT, DT_NTEXT oder DT_IMAGE. Weitere Informationen finden Sie unter [Integration Services Datentypen](../integration-services-data-types.md).  
  
 Normalerweise werden Werte aus dem Verweisdataset der Transformationsausgabe hinzugefügt. Beispielsweise kann die Transformation für die Suche einen Produktnamen aus einer Tabelle mithilfe eines Wertes aus einer Eingabespalte extrahieren und den Produktnamen dann der Transformationsausgabe hinzufügen. Die Werte aus der Verweistabelle können Spaltenwerte ersetzen oder können neuen Spalten hinzugefügt werden.  
  
 Bei den von der Transformation für die Suche ausgeführten Suchvorgängen wird nach Groß-/Kleinschreibung unterschieden. Um Fehler bei der Suche aufgrund von unterschiedlicher Groß-/Kleinschreibung bei den Daten zu vermeiden, konvertieren Sie die Daten zunächst mit der Transformation für Zeichenzuordnung in Groß- oder Kleinbuchstaben. Anschließend fügen Sie der SQL-Anweisung, mit der die Verweistabelle generiert wird, die UPPER- oder LOWER-Funktion hinzu. Weitere Informationen finden Sie unter [Transformation zum Zuordnen der Zeichen](character-map-transformation.md), [UPPER &#40;Transact-SQL&#41;](/sql/t-sql/functions/upper-transact-sql) und [LOWER &#40;Transact-SQL&#41;](/sql/t-sql/functions/lower-transact-sql).  
  
 Die Transformation für Suche weist die folgenden Ein- und Ausgaben auf:  
  
-   Eingabe.  
  
-   Ausgabe übereinstimmender Einträge. Bei der Ausgabe übereinstimmender Einträge werden in der Transformationseingabe die Zeilen behandelt, die mindestens einem Eintrag im Verweisdataset entsprechen.  
  
-   Ausgabe nicht übereinstimmender Einträge. Bei der Ausgabe nicht übereinstimmender Einträge in der Eingabe werden die Zeilen verarbeitet, die nicht mindestens einem Eintrag im Verweisdataset entsprechen. Wenn Sie die Transformation für Suche so konfigurieren, dass die Zeilen ohne übereinstimmende Einträge als Fehler behandelt werden, werden die Zeilen an die Fehlerausgabe weitergeleitet. Andernfalls würde die Transformation diese Zeilen an die Ausgabe nicht übereinstimmender Einträge weiterleiten.  
  
    > [!NOTE]  
    >  In [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)] hatte die Transformation für Suche nur eine Ausgabe. Weitere Informationen zum Ausführen einer Transformation für Suche, die in erstellt wurde [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , finden Sie unter [Aktualisieren von Such Transformationen](../../../sql-server/install/upgrade-lookup-transformations.md).  
  
-   Fehlerausgabe.  
  
## <a name="caching-the-reference-dataset"></a>Zwischenspeichern des Verweisdatasets  
 In einem speicherresidenten Cache werden das Verweisdataset und eine Hashtabelle gespeichert, mit der die Daten indiziert werden. Der Cache bleibt speicherresident, bis die Ausführung des Pakets abgeschlossen ist. Sie können den Cache in einer Cachedatei (.caw) persistent speichern.  
  
 Wenn Sie den Cache in einer Datei persistent speichern, lädt das System den Cache schneller. Dies verbessert die Leistung der Transformation für Suche und des Pakets. Bei Verwendung einer Cachedatei arbeiten Sie mit Daten, die weniger aktuell sind als die Daten in der Datenbank.  
  
 Im Folgenden finden Sie weitere Vorteile einer persistenten Speicherung des Caches in einer Datei:  
  
-   ***Die Cachedatei kann für mehrere Pakete freigegeben werden. Weitere Informationen finden Sie unter***  [Implementieren einer Suchtransformation im Vollcachemodus mit der Transformation für Cacheverbindungs-Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  ***.***  
  
-   Die Cachedatei kann mit einem Paket bereitgestellt werden. ***Die Daten können dann auf mehreren Computern verwendet werden.*** Weitere Informationen finden Sie unter [Erstellen und Bereitstellen eines Cache für die Transformation für Suche](create-and-deploy-a-cache-for-the-lookup-transformation.md).  
  
-   Sie können die Rohdatendatei-Quelle zum Lesen der Daten aus der Cachedatei verwenden. Dann können Sie die Daten mithilfe anderer Datenflusskomponenten umwandeln oder verschieben. Weitere Informationen finden Sie unter [Raw File Source](../raw-file-source.md).  
  
    > [!NOTE]  
    >  Der Cacheverbindungs-Manager unterstützt keine mithilfe des Rohdatendatei-Ziels erstellten oder geänderten Cachedateien.  
  
-   Mit dem Task Dateisystem können Sie für die Cachedatei Vorgänge ausführen und Attribute festlegen. Weitere Informationen finden Sie unter [File System Task](../../control-flow/file-system-task.md).  
  
 Folgende die Optionen für die Zwischenspeicherung sind verfügbar:  
  
-   Das Verweisdataset wird durch die Verwendung einer Tabelle, Sicht oder SQL-Abfrage generiert und in den Cache geladen, bevor die Transformation für Suche ausgeführt wird. Für den Zugriff auf das Dataset verwenden Sie den OLE DB-Verbindungs-Manager.  
  
     Diese Option für die Zwischenspeicherung ist kompatibel mit der Option für die vollständige Zwischenspeicherung, die für die Transformation für Suche in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]verfügbar ist.  
  
-   Das Verweisdataset wird aus einer verbundenen Datenquelle im Datenfluss oder aus einer Cachefile generiert und in den Cache geladen, bevor die Transformation für Suche ausgeführt wird. Für den Zugriff auf das Dataset verwenden Sie den Cacheverbindungs-Manager und optional die Cachetransformation. Weitere Informationen finden Sie unter [Cacheverbindungs-Manager](../../connection-manager/cache-connection-manager.md) und [Cachetransformation](cache-transform.md).  
  
-   Das Verweisdataset wird durch die Verwendung einer Tabelle, Sicht oder SQL-Abfrage während der Ausführung der Transformation für Suche generiert. Die Zeilen mit übereinstimmenden Einträgen im Verweisdataset und die Zeilen ohne übereinstimmende Einträge im Dataset werden in den Cache geladen.  
  
     Wenn die Speichergröße des Caches überschritten wird, entfernt die Transformation zum Suchen automatisch die am seltensten verwendeten Zeilen aus dem Cache.  
  
     Diese Option für die Zwischenspeicherung ist kompatibel mit der Option für die teilweise Zwischenspeicherung, die für die Transformation für Suche in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]verfügbar ist.  
  
-   Das Verweisdataset wird durch die Verwendung einer Tabelle, Sicht oder SQL-Abfrage während der Ausführung der Transformation für Suche generiert. Es werden keine Daten zwischengespeichert.  
  
     Diese Option für die Zwischenspeicherung ist kompatibel mit der Option für keine Zwischenspeicherung, die für die Transformation für Suche in [!INCLUDE[ssISversion2005](../../../includes/ssisversion2005-md.md)]verfügbar ist.  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterscheiden sich in der Art des Zeichenfolgenvergleichs. Wenn die Transformation für Suche so konfiguriert ist, dass das Verweisdataset in den Cache geladen wird, bevor die Transformation für Suche ausgeführt wird, führt [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] den Suchvergleich im Cache aus. Andernfalls verwendet der Suchvorgang eine parametrisierte SQL-Anweisung, und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] führt den Suchvergleich aus. Dies bedeutet, dass die Transformation für Suche je nach Cachetyp möglicherweise eine unterschiedliche Anzahl von Übereinstimmungen aus der gleichen Suchtabelle zurückgibt.  
  
## <a name="related-tasks"></a>Related Tasks  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen. Weitere Einzelheiten finden Sie in den folgenden Hilfethemen:  
  
-   [Implementieren einer Suche im Modus "Kein Cache" oder "Teilcache"](implement-a-lookup-in-no-cache-or-partial-cache-mode.md)  
  
-   [Implementieren einer Suchtransformation im Vollcachemodus mit der Transformation für Cacheverbindungs-Manager](../../connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)  
  
-   [Implementieren einer Suchtransformation im Vollcachemodus mit dem OLE DB-Verbindungs-Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Video [How to: Implement a Lookup Transformation in Full Cache Mode](https://go.microsoft.com/fwlink/?LinkId=131031)(Vorgehensweise: Implementieren einer Suchtransformation im Vollcachemodus) unter msdn.microsoft.com  
  
-   Blog-Artikel [Best Practices for Using the Lookup Transformation Cache Modes](https://go.microsoft.com/fwlink/?LinkId=146623)(Bewährte Vorgehensweisen für die Verwendung des Cachemodus der Transformation für Suche) unter blogs.msdn.com  
  
-   Blogeintrag [Suchmuster: Keine Beachtung von Groß-/Kleinschreibung](https://go.microsoft.com/fwlink/?LinkId=157782)auf blogs.msdn.com.  
  
-   Beispiel [Transformation für Suche](https://go.microsoft.com/fwlink/?LinkId=267528)auf msftisprodsamples.codeplex.com.  
  
     Informationen zum Installieren von [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Produktbeispielen und Beispieldatenbanken finden Sie unter [SQL Server Integration Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=267527).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transformation für Fuzzysuche](fuzzy-lookup-transformation.md)   
 [Transformation für Begriffs Suche](term-lookup-transformation.md)   
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
