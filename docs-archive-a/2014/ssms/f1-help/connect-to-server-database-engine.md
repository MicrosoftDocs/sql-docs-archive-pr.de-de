---
title: Verbindung mit Server herstellen (Datenbank-Engine) (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.connectoserverunknownservertype.f1
- sql12.swb.connection.login.sqlserver.f1
- sql12.swb.connection.login.sqlce.f1
- sql12.swb.manageSS2k.f1
- sql12.swb.connecttoce.f1
- sql12.swb.connecttoce.connectionproperties.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca227d1a3bbc13160962ba2fcad23ff011c950f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717257"
---
# <a name="connect-to-server-database-engine"></a>Verbindung mit Server herstellen (Datenbank-Engine)
  Verwenden Sie dieses Dialogfeld, um Optionen bei der Verbindungsherstellung mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] anzuzeigen oder anzugeben. In den meisten Fällen können Sie eine Verbindung herstellen, indem Sie im Feld **Servername** den Computernamen des Datenbankservers eingeben und dann auf **Verbinden**klicken. Geben Sie beim Herstellen der Verbindung mit [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]den Computernamen gefolgt von **\sqlexpress**an.  
  
 Viele Faktoren können Auswirkungen auf die Fähigkeit zum Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]haben.  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über den Objekt-Explorer registrieren, wählen Sie den Typ des Servers aus, mit dem die Verbindung hergestellt werden soll: [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über „Registrierte Server“ registrieren, ist das Feld **Servertyp** schreibgeschützt, wobei der Feldeintrag mit dem in der Komponente „Registrierte Server“ angezeigten Servertyp übereinstimmt. Zum Registrieren eines anderen Servertyps wählen Sie auf der Symbolleiste Registrierte Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)]oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aus, bevor Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Wählen Sie die Serverinstanz aus, mit der eine Verbindung hergestellt werden soll. Standardmäßig wird die Serverinstanz angezeigt, mit der zuletzt eine Verbindung bestanden hat.  
  
> [!NOTE]  
>  Um eine Verbindung mit einer aktiven Instanz von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] herzustellen, verwenden Sie das Named Pipes-Protokoll unter Angabe des Pipenamens, z. B. „np:\\\\.\pipe\3C3DF6B1-2262-47\tsql\query“. Weitere Informationen finden Sie in der Dokumentation von [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
 **Authentifizierung**  
 Beim Herstellen einer Verbindung mit einer Instanz von sind zwei Authentifizierungs Modi verfügbar [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
 **Windows-Authentifizierungsmodus (Windows-Authentifizierung)**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Der Windows Authentifizierungsmodus ermöglicht Benutzern die Verbindung über ein Windows-Benutzerkonto.  
  
 **SQL Server-Authentifizierung**  
 Wenn ein Benutzer eine Verbindung mit einem angegebenen Benutzernamen und einem Kennwort von einer nicht vertrauenswürdigen Verbindung herstellt, führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Authentifizierung durch, indem überprüft wird, ob ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt. Wenn kein Anmeldekonto in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingerichtet wurde, schlägt die Authentifizierung fehl, und der Benutzer erhält eine Fehlermeldung.  
  
> [!IMPORTANT]  
>  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
 **Benutzername**  
 Geben Sie den Benutzernamen für die Verbindung ein. Diese Option ist nur verfügbar, wenn Sie die Windows-Authentifizierung für die Verbindungsherstellung ausgewählt haben.  
  
 **Anmeldung**  
 Geben Sie den Anmeldenamen für die Verbindung ein. Diese Option ist nur verfügbar, wenn Sie zum Verbinden die Authentifizierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die Anmeldung ein. Sie können diese Option nur bearbeiten, wenn Sie zum Verbinden die Authentifizierung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgewählt haben.  
  
 **Herstellen einer Verbindung**  
 Klicken Sie hier, um eine Verbindung mit dem oben ausgewählten Server herzustellen.  
  
 **Optionen**  
 Klicken Sie auf diese Schaltfläche, um zusätzliche Optionen für die Serververbindung anzuzeigen, z. B. zum Registrieren eines Servers oder zum Speichern des Kennworts.  
  
  
