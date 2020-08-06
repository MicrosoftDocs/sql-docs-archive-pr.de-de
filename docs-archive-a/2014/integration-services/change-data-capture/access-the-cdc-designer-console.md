---
title: Zugreifen auf die CDC Designer Console | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4f6e4df0a514cb29e36bcd1270b2537dc3ba68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724881"
---
# <a name="access-the-cdc-designer-console"></a>Zugreifen auf die CDC Designer Console
  Sie können auf die CDC Designer Console über den Computer zugreifen, auf dem Sie die Konsole installiert haben. Weitere Informationen zur Installation finden Sie unter Installation.  
  
 Wenn Sie die CDC Designer Console öffnen, wird das Dialogfeld Verbindung mit SQL Server herstellen geöffnet.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung, mit der auf den CDC Designer zugegriffen wird, muss über UPDATE-Berechtigungen für die MSXDBCDC-Datenbank verfügen. Außerdem muss die Anmeldung auch über die feste Serverrolle `dbcreator` verfügen, um neue Oracle CDC-Instanzen erstellen zu können. Es wird empfohlen, dass die Anmeldung auch über den SELECT-Zugriff auf die verwendeten CDC-Datenbanken verfügt. Andernfalls kann der Benutzer den Status dieser Datenbanken nicht anzeigen.  
  
 Geben Sie im Dialogfeld Verbindung mit SQL Server herstellen die folgenden Informationen ein.  
  
### <a name="server-name"></a>Servername  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
### <a name="authentication"></a>Authentifizierung  
 Wählen Sie eines der folgenden Szenarien aus:  
  
-   **Windows-Authentifizierung**  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, müssen Sie den **Anmeldenamen** und das **Kennwort** für den Benutzer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeben, mit dem Sie eine Verbindung herstellen.  
  
 Der angemeldete Benutzer muss über eine Datenbankrolle verfügen, die den Zugriff auf die MSXCDCDB-Datenbank ermöglicht. Es wird empfohlen, dass der angemeldete Benutzer außerdem Zugriff auf weitere Datenbanken hat, die verwendet werden, da der Benutzer die Daten in diesen Datenbanken sonst nicht anzeigen kann.  
  
### <a name="options"></a>Tastatur  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
 **Verbindungstimeout**  
 Geben Sie den Zeitraum (in Sekunden) ein, wie lange der CDC Service for Oracle auf eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] warten soll, bevor ein Timeout eintritt. Der Standardwert lautet **15**.  
  
 **Ausführungstimeout**  
 Geben Sie den Zeitraum (in Sekunden) ein, wie lange der Oracle CDC-Windows-Dienst auf die Ausführung eines Befehls wartet, bis ein Timeout eintritt. Der Standardwert ist **30**.  
  
 **Verbindung verschlüsseln**  
 Wählen Sie **Verbindung verschlüsseln** für die Kommunikation zwischen dem Oracle CDC Service und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zielinstanz aus, bei der eine verschlüsselte Verbindung verwendet werden soll. **Erweitert**: Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
 **Erweitert**  
 Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
 Weitere Informationen zum Dialogfeld „Erweiterte Verbindungseigenschaften“ finden Sie unter [Erweiterte Verbindungseigenschaften](advanced-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Verbindung erfordert Berechtigungen für den CDC Designer](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
