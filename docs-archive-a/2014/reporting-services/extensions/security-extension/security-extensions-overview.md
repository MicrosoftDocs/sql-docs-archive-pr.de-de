---
title: Übersicht über Sicherheitserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
ms.assetid: 24ccd795-6506-457c-93ac-6a9dd6bb9a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9cd6c2a1518b724a7faafecdb2926505694e9707
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618509"
---
# <a name="security-extensions-overview"></a>Übersicht über Sicherheitserweiterungen
  Eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Sicherheitserweiterung ermöglicht die Authentifizierung und Autorisierung von Benutzern oder Gruppen. Das heißt, verschiedene Benutzer können sich bei einem Berichtsserver anmelden und anhand ihrer Identitäten verschiedene Aufgaben oder Vorgänge ausführen. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verwendet standardmäßig eine Windows-basierte Authentifizierungserweiterung, die mit Windows-Kontoprotokollen die Identitäten von Benutzern überprüft, die angeben, im System über Konten zu verfügen. In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] werden Benutzer mithilfe eines rollenbasierten Sicherheitssystems authentifiziert. Das rollenbasierte Sicherheitsmodell von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ähnelt den rollenbasierten Sicherheitsmodellen anderer Technologien.

 Da Sicherheitserweiterungen auf einer offenen und erweiterbaren API beruhen, können Sie neue Authentifizierungs- und Autorisierungserweiterungen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] erstellen. Im Folgenden sehen Sie ein Beispiel einer typischen Sicherheitserweiterungsimplementierung, die mit formularbasierter Authentifizierung und Autorisierung arbeitet:

 ![Reporting Services-Sicherheitserweiterungsprozess](../../media/rosettasecurityextensionflow.gif "Reporting Services-Sicherheitserweiterungsprozess")

 Wie in der Abbildung dargestellt, treten Authentifizierung und Autorisierung folgendermaßen auf:

1.  Ein Benutzer versucht über eine URL auf den Berichts-Manager zuzugreifen und wird zu einem Formular umgeleitet, das Anmeldeinformationen von Benutzern für die Clientanwendung sammelt.

2.  Der Benutzer gibt die Anmeldeinformationen an das Formular.

3.  Die Anmeldeinformationen des Benutzers werden mithilfe der <xref:ReportService2010.ReportingService2010.LogonUser%2A>-Methode an den Reporting Services-Webdienst übermittelt.

4.  Der Webdienst ruft die vom Benutzer angegebene Sicherheitserweiterung auf und überprüft, ob der Benutzername und das Kennwort in der benutzerdefinierten Sicherheitsinstanz vorhanden sind.

5.  Nach der Authentifizierung erstellt der Webdienst für die Startseite des Berichts-Managers ein Authentifizierungsticket (auch "Cookie" genannt), verwaltet das Ticket und überprüft die Rolle des Benutzers.

6.  Der Webdienst gibt das Cookie an den Browser zurück und zeigt die entsprechende Benutzeroberfläche im Berichts-Manager an.

7.  Nachdem der Benutzer authentifiziert wurde, sendet der Browser Anforderungen an den Berichts-Manager, während das Cookie im HTTP-Header übertragen wird. Diese Anforderungen sind Reaktionen auf Benutzeraktionen im Berichts-Manager.

8.  Das Cookie wird zusammen mit der angeforderten Benutzeroperation im HTTP-Header an den Webdienst übertragen.

9. Das Cookie wird überprüft. Wenn es gültig ist, gibt der Berichtsserver die Sicherheitsbeschreibung und andere im Zusammenhang mit der angeforderten Operation stehende Informationen aus der Berichtsserver-Datenbank zurück.

10. Wenn das Cookie gültig ist, ruft der Berichtsserver die Sicherheitserweiterung auf und überprüft, ob der Benutzer zur Ausführung der bestimmten Operation autorisiert ist.

11. Wenn der Benutzer autorisiert ist, führt der Berichtsserver die angeforderte Operation aus und gibt die Steuerung an den Aufrufer zurück.

12. Nach der Authentifizierung des Benutzers verwendet der URL-Zugriff des Berichtsservers dasselbe Cookie. Das Cookie wird im HTTP-Header übertragen.

13. Der Benutzer fordert so lange Operationen auf dem Berichtsserver an, bis die Sitzung beendet ist.

## <a name="when-to-implement-a-security-extension"></a>Sinnvolles Implementieren von Sicherheitserweiterungen
 Es wird empfohlen, immer die Windows-Authentifizierung zu verwenden. In den folgenden Fällen ist jedoch möglicherweise eine benutzerdefinierte Authentifizierung und Autorisierung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] angemessener:

-   Sie haben eine Internet- oder Extranetanwendung, die keine Windows-Konten nutzen kann.

-   Sie haben benutzerdefinierte Benutzer und Rollen, die ein übereinstimmendes Autorisierungsschema in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]bereitstellen müssen.

## <a name="see-also"></a>Weitere Informationen
 [Implementieren einer Sicherheits Erweiterung](../security-extension/implementing-a-security-extension.md) [Konfigurieren Berichts-Manager für die Übergabe von benutzerdefinierten Authentifizierungs Cookies](../../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)


