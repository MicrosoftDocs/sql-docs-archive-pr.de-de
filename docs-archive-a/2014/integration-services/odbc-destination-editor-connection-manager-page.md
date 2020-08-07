---
title: Ziel-Editor für ODBC (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e4fc1073bb187c0864d2991459a358a7f81d066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718583"
---
# <a name="odbc-destination-editor-connection-manager-page"></a>Ziel-Editor für ODBC (Verbindungs-Manager-Seite)
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **Ziel-Editor für ODBC** können Sie den ODBC-Verbindungs-Manager für das Ziel auswählen. Außerdem können Sie auf dieser Seite eine Tabelle oder Sicht aus der Datenbank auswählen.  
  
 Weitere Informationen zum ODBC-Ziel finden Sie unter [ODBC Destination](data-flow/odbc-destination.md).  
  
 **So öffnen Sie die Seite "Verbindungs-Manager" des Ziel-Editors für ODBC**  
  
## <a name="task-list"></a>Aufgabenliste  
  
-   Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das das ODBC-Ziel enthält.  
  
-   Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das ODBC-Ziel.  
  
-   Klicken Sie im **Ziel-Editor für ODBC**auf **Verbindungs-Manager**.  
  
## <a name="options"></a>Tastatur  
  
### <a name="connection-manager"></a>Ziel-Editor für Dimensionsverarbeitung  
 Wählen Sie in der Liste einen vorhandenen ODBC-Verbindungs-Manager aus, oder klicken Sie auf Neu, um eine neue Verbindung zu erstellen. Sie können eine Verbindung mit jeder von ODBC unterstützten Datenbank erstellen.  
  
### <a name="new"></a>Neu  
 Klicken Sie auf **Neu**. Das Dialogfeld **ODBC-Verbindungs-Manager konfigurieren** , in dem Sie einen neuen Verbindungs-Manager erstellen können, wird geöffnet.  
  
### <a name="data-access-mode"></a>Datenzugriffsmodus  
 Wählen Sie die Methode zum Laden von Daten in das Ziel aus. Die Optionen sind in der folgenden Tabelle aufgeführt:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|Tabellenname - Batch|Wählen Sie diese Option aus, um das ODBC-Ziel im Batchmodus zu konfigurieren. Bei Auswahl dieser Option sind die folgenden Optionen verfügbar:|  
||**Name der Tabelle oder Sicht**: Wählen Sie in der Liste eine verfügbare Tabelle oder Sicht aus.<br /><br /> Diese Liste enthält nur die ersten 1000 Tabellen. Wenn die Datenbank mehr als 1000 Tabellen enthält, können Sie den Anfang eines Tabellennamens eingeben oder das Platzhalterzeichen (\*) verwenden, um einen beliebigen Teil des Namens einzugeben und die gewünschten Tabellen anzuzeigen.<br /><br /> **Batchgröße**: Geben Sie die Größe des Batches für das Massenladen ein. Dies ist die Anzahl von Zeilen, die als Batch geladen werden.|  
|Tabellenname - Zeile für Zeile|Wählen Sie diese Option aus, um das ODBC-Ziel so zu konfigurieren, dass jede Zeile einzeln in die Zieltabelle eingefügt wird. Bei Auswahl dieser Option ist die folgende Option verfügbar:|  
||**Name der Tabelle oder Sicht**: Wählen Sie in der Liste eine verfügbare Tabelle oder Sicht in der Datenbank aus.<br /><br /> Diese Liste enthält nur die ersten 1000 Tabellen. Wenn die Datenbank mehr als 1000 Tabellen enthält, können Sie den Anfang eines Tabellennamens eingeben oder das Platzhalterzeichen (*) verwenden, um einen beliebigen Teil des Namens einzugeben und die gewünschten Tabellen anzuzeigen.|  
  
### <a name="preview"></a>Vorschau  
 Klicken Sie auf **Vorschau** , um die ersten 200 Zeilen (max.) für die ausgewählte Tabelle anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Eigenschaften des ODBC-Ziels](data-flow/odbc-destination-custom-properties.md)   
 [Ziel-Editor für ODBC &#40;Seite Zuordnungen&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)   
 [Ziel-Editor für ODBC &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  
