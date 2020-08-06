---
title: 'Befehlszeilen-Verwaltungs Tool: SqlLocalDB.exe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d21a6a8879e981e52bd2e7d3bd05a37e65d8cf4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609229"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>Verwaltungstool für Befehlszeilen: SqlLocalDB.exe
  SqlLocalDB.exe ist ein einfaches Tool, das dem Benutzer die einfache Verwaltung der LocalDB-Instanzen in der Befehlszeile ermöglicht. Es wird als einfacher Wrapper um die LocalDB Instanz-API implementiert. Wie in vielen ähnlichen SQL Server-Tools (zum Beispiel SQLCMD) werden Parameter als Befehlszeilenargumente an SqlLocalDB übergeben, und die Ausgabe wird an die Konsole gesendet.  
  
 SqlLocalDB ermöglicht Entwicklern die Verwendung von LocalDB, ohne Code zum Aufrufen der API schreiben zu müssen und ohne von anderen Tools abhängig zu sein, die dies erledigen müssten.  
  
## <a name="sqllocaldb-options"></a>SqlLocalDB-Optionen  
 SqlLocalDB unterstützt die folgenden Optionen.  
  
|Option|Funktionsbeschreibung|  
|------------|------------------|  
|`-?`|Druckt Hilfetext.|  
|`create&#124;c "instance name" [version-number] [-s]`|Erstellt eine neue LocalDB-Instanz mit einem angegebenen Namen und einer Version.<br /><br /> Wenn der [Versionsnummer]-Parameter weggelassen wird, wird standardmäßig die SqlLocalDB-Buildversion verwendet.<br /><br /> -s startet die neue LocalDB-Instanz nach dem Erstellen.|  
|`delete&#124;d "instance name"`|Löscht die LocalDB-Instanz mit dem angegebenen Namen.|  
|`start&#124;s "instance name"`|Startet die LocalDB-Instanz mit dem angegebenen Namen.|  
|`stop&#124;p "instance name" [-i&#124;-k]`|Beendet die LocalDB-Instanz mit dem angegebenen Namen, nachdem die Ausführung aktueller Abfragen beendet wird.<br /><br /> -i fordert das Herunterfahren der LocalDB-Instanz mit der NOWAIT-Option an.<br /><br /> -k bricht den LocalDB-Instanzprozess ohne Kontaktieren ab.|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|Gibt die angegebene private Instanz mithilfe des angegebenen freigegebenen Namens frei. Wenn die Benutzer-SID oder der Kontoname weggelassen wird, wird standardmäßig der aktuelle Benutzer verwendet.|  
|`unshare&#124;u "shared name"`|Hebt die Freigabe der angegebenen freigegebenen LocalDB-Instanz auf.|  
|`info&#124;i`|Listet alle vorhandenen LocalDB-Instanzen im Besitz des aktuellen Benutzers und aller freigegebenen LocalDB-Instanzen auf.|  
|`info&#124;i "instance name"`|Druckt die Informationen zur angegebenen LocalDB-Instanz.|  
|`versions&#124;v`|Listet alle auf dem Computer installierten LocalDB-Versionen auf.|  
|||  
|`trace&#124;t on&#124;off`|Aktiviert und deaktiviert die Ablaufverfolgung.|  
  
 SqlLocalDB behandelt Leerzeichen als Trennzeichen. Sie müssen die Instanznamen mit Anführungszeichen umschließen, die Leerzeichen und Sonderzeichen enthalten. Beispiel:  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
