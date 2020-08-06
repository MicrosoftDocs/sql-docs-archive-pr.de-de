---
title: SQL Server-Ziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcd65007e1e6af36386cb2ceba1f7242305b81a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697033"
---
# <a name="sql-server-destination"></a>SQL Server-Ziel
  Das SQL Server-Ziel stellt eine Verbindung mit einer lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank her und kopiert Daten per Massenladen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen und -Sichten. Sie können das SQL Server-Ziel nicht in Paketen verwenden, die auf eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank auf einem Remoteserver zugreifen. Die Pakete sollten stattdessen ein OLE DB-Ziel verwenden. Weitere Informationen finden Sie unter [OLE DB Destination](ole-db-destination.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer, die Pakete ausführen, die das SQL Server-Ziel einschließen, müssen über die Berechtigung "Erstellen globaler Objekte" verfügen. Sie können diese Berechtigung Benutzern erteilen, indem Sie das Tool Lokale Sicherheitsrichtlinie im Menü **Verwaltung** verwenden. Wenn Sie beim Ausführen eines Pakets, das das SQL Server-Ziel verwendet, eine Fehlermeldung erhalten, sollten Sie sicherstellen, dass das Konto, mit dem das Paket ausgeführt wird, über die Berechtigung "Erstellen globaler Objekte" verfügt.  
  
## <a name="bulk-inserts"></a>Masseneinfügungen  
 Wenn Sie versuchen, das SQL Server-Ziel zum Massenladen von Daten in eine Remote-Datenbank von SQL Server zu verwenden, wird eine Fehlermeldung der folgenden Form angezeigt: "Ein OLE DB-Datensatz ist verfügbar." Quelle: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Beschreibung: "Massenladen war nicht möglich, weil das SSIS-Dateizuordnungsobjekt 'Global\DTSQLIMPORT' nicht geöffnet werden konnte. Betriebssystemfehlercode 2 (Die angegebene Datei wurde nicht gefunden.). Stellen Sie sicher, dass Sie auf einen lokalen Server mit der Windows-Sicherheit zugreifen.""  
  
 Das SQL Server-Ziel bietet das gleiche Hochgeschwindigkeitseinfügen von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie der Masseneinfügungstask. Mit dem SQL Server-Ziel kann jedoch ein Paket Transformationen auf Spaltendaten anwenden, bevor die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen werden.  
  
 Zum Laden von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sollten Sie das Verwenden des SQL Server-Ziels anstelle des OLE DB-Ziels in Erwägung ziehen.  
  
### <a name="bulk-insert-options"></a>Masseneinfügungsoptionen  
 Falls das SQL Server-Ziel einen Datenzugriffsmodus für schnelles Laden verwendet, können Sie die folgenden Optionen für schnelles Laden angeben:  
  
-   Identitätswerte aus der importierten Datendatei beibehalten oder von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zugewiesene eindeutige Werte verwenden.  
  
-   NULL-Werte während des Massenladevorgangs beibehalten.  
  
-   Während des Massenimportvorgangs Einschränkungen der Zieltabelle oder -sicht überprüfen.  
  
-   Sperre auf Tabellenebene für die Dauer des Massenladevorgangs abrufen.  
  
-   INSERT-Trigger, die für die Zieltabelle definiert sind, während des Massenladevorgangs ausführen.  
  
-   Die Nummer der ersten Zeile in der Eingabe angeben, die während des Masseneinfügungsvorgangs geladen werden soll.  
  
-   Die Nummer der letzten Zeile in der Eingabe angeben, die während des Masseneinfügungsvorgangs geladen werden soll.  
  
-   Die maximal zulässige Anzahl von Fehlern angeben, bevor der Massenladevorgang abgebrochen wird. Jede Zeile, die nicht importiert werden kann, wird als ein Fehler gezählt.  
  
-   Die Spalten in der Eingabe angeben, die sortierte Daten enthalten.  
  
 Weitere Informationen zu Massenladeoptionen finden Sie unter [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
#### <a name="performance-improvements"></a>Leistungsverbesserungen  
 Sie sollten die Standardoptionen wie folgt ändern, um die Leistung einer Masseneinfügung und des Zugriffs auf Tabellendaten während des Masseneinfügungsvorgangs zu verbessern:  
  
-   Überprüfen Sie während des Massenimportvorgangs keine Einschränkungen der Zieltabelle oder -sicht.  
  
-   Führen Sie während des Massenladevorgangs keine INSERT-Trigger aus, die für die Zieltabelle definiert sind.  
  
-   Wenden Sie keine Sperre auf die Tabelle an. Auf diese Weise ist die Tabelle während des Masseneinfügungsvorgangs weiterhin für andere Benutzer und Anwendungen verfügbar.  
  
## <a name="configuration-of-the-sql-server-destination"></a>Konfiguration des SQL Server-Ziels  
 Es gibt folgende Möglichkeiten, um das SQL Server-Ziel zu konfigurieren:  
  
-   Geben Sie die Tabelle oder Sicht an, in die die Daten massengeladen werden sollen.  
  
-   Passen Sie den Massenladevorgang durch Angeben von Optionen an, wie z. B., ob Einschränkungen überprüft werden sollen.  
  
-   Geben Sie an, ob für alle Zeilen ein Commit in einem Batch ausgeführt werden soll, oder legen Sie die maximale Anzahl von Zeilen fest, für die ein Commit als Batch ausgeführt werden soll.  
  
-   Geben Sie ein Timeout für den Massenladevorgang an.  
  
 Dieses Ziel verwendet einen OLE DB-Verbindungs-Manager zum Herstellen einer Verbindung mit einer Datenquelle, und der Verbindungs-Manager gibt den zu verwendenden OLE DB-Anbieter an. Weitere Informationen finden Sie unter [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
 Ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt stellt auch das Datenquellenobjekt bereit, von dem Sie einen OLE DB-Verbindungs-Manager erstellen können. Auf diese Weise sind Datenquellen und Datenquellensichten für das SQL Server-Ziel verfügbar.  
  
 Das SQL Server-Ziel besitzt eine Eingabe. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Ziel-Editor für SQL** festlegen können:  
  
-   [Ziel-Editor für SQL &#40;Seite „Verbindungs-Manager“&#41;](../sql-destination-editor-connection-manager-page.md)  
  
-   [Ziel-Editor für SQL &#40;Seite „Zuordnungen“&#41;](../sql-destination-editor-mappings-page.md)  
  
-   [Ziel-Editor für SQL &#40;Seite „Erweitert“&#41;](../sql-destination-editor-advanced-page.md)  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des SQL Server-Ziels](sql-server-destination-custom-properties.md)  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum Festlegen von Eigenschaften anzuzeigen:  
  
-   [Massenladen von Daten mithilfe des SQL Server-Ziels](sql-server-destination.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Massenladen von Daten mithilfe des SQL Server-Ziels](sql-server-destination.md)  
  
-   [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Technischer Artikel [Möglicherweise wird bei UAC-fähigen Systemen der Fehler "Die SSIS-Masseneinfügung kann zum Einfügen von Daten nicht vorbereitet werden" angezeigt](https://go.microsoft.com/fwlink/?LinkId=199482)auf support.microsoft.com.  
  
-   Technischer Artikel [The Data Loading Performance Guide (Leistungsleitfaden für das Laden von Daten)](https://go.microsoft.com/fwlink/?LinkId=233700)auf msdn.microsoft.com  
  
-   Technischer Artikel [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701)(Verwenden von SQL Server Integration Services für das Massenladen von Daten) auf simple-talk.com.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenfluss](data-flow.md)  
  
  
