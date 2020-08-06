---
title: Autorisierung in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7420b45175ca0b0a5fc66da4a7939b07b79c75b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618516"
---
# <a name="authorization-in-reporting-services"></a>Autorisierung in Reporting Services
  Unter Autorisierung versteht man den Prozess der Beurteilung, ob einer Identität die angeforderte Zugriffsart auf eine bestimmte Ressource in der Berichtsserver-Datenbank erteilt wird. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verwendet eine Autorisierungarchitektur auf Rollenbasis, bei der ein Benutzer Zugriff auf eine bestimmte Rolle ausgehend von der Rollenzuweisung für die Anwendung erhält. Sicherheitserweiterungen für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthalten eine Implementierung einer Autorisierungskomponente, über die ein Benutzer Zugriff erhält, sobald er sich auf dem Berichtsserver authentifiziert hat. Die Autorisierung wird gestartet, wenn ein Benutzer versucht, einen Vorgang im System oder auf einem Berichtsserverelement über die SOAP-API und den URL-Zugriff auszuführen. Dies wird durch die Sicherheitserweiterungsschnittstelle **IAuthorizationExtension**ermöglicht. Wie vorher angegeben, erben alle Erweiterungen von **IExtension** die Basisschnittstelle für jede Erweiterung, die Sie bereitstellen. **IExtension** und **IAuthorizationExtension** sind Elemente des **Microsoft.ReportingServices.Interfaces** -Namespace.

## <a name="checking-access"></a>Zugriffsprüfung
 Bei der Autorisierung ist der Schlüssel für jede benutzerdefinierte Implementierung der Sicherheit die in der <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>-Methode implementierte Zugriffsüberprüfung. <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> wird immer aufgerufen, wenn ein Benutzer versucht, auf dem Berichtsserver einen Vorgang auszuführen. Die Methode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> wird für jeden Vorgangstyp überladen. Für Ordnervorgänge könnte ein Beispiel für eine Zugriffsprüfung folgendermaßen aussehen:

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 Der Berichtsserver ruft die Methode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> auf, indem der Name des angemeldeten Benutzers, ein Benutzertoken, die Sicherheitsbeschreibung für das Element und der angeforderte Vorgang übergeben werden. Hier würden Sie die Sicherheitsbeschreibung auf den Benutzernamen und die entsprechende Berechtigung zur Durchführung der Anforderung überprüfen, dann würden Sie mit `true` anzeigen, dass der Zugriff erteilt wird, oder mit `false`, dass der Zugriff verweigert wird.

## <a name="security-descriptors"></a>Sicherheitsbeschreibungen
 Wenn Sie Autorisierungsrichtlinien für Elemente in der Berichtsserver-Datenbank festlegen, gibt eine Clientanwendung (z. B. der Berichts-Manager) die Benutzerinformationen an die Sicherheitserweiterung weiter, zusammen mit einer Sicherheitsrichtlinie für das Element. Die Sicherheitsrichtlinie und die Benutzerinformationen werden zusammen als Sicherheitsbeschreibung bezeichnet. Eine Sicherheitsbeschreibung enthält die folgenden Informationen für ein Element in der Berichtsserver-Datenbank:

-   Gruppe oder Benutzer, der eine bestimmte Berechtigung hat, Vorgänge in dem Element auszuführen.

-   Elementtyp.

-   Eine freigegebene Zugriffssteuerungsliste, die den Zugriff auf das Element kontrolliert.

 Sicherheitsbeschreibungen werden mit den Webdienstmethoden <xref:ReportService2010.ReportingService2010.SetPolicies%2A> und <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> erstellt.

### <a name="authorization-flow"></a>Autorisierungsablauf
 Die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Autorisierung wird von der Sicherheitserweiterung gesteuert, die derzeit für die Ausführung auf dem Server konfiguriert ist. Die Autorisierung ist rollenbasiert und auf die Berechtigungen und Vorgänge beschränkt, die von der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Sicherheitsarchitektur bereitgestellt werden. Das folgende Diagramm veranschaulicht den Prozess der Autorisierung von Benutzern für die Bearbeitung von Elementen in der Berichtsserver-Datenbank:

 ![Ablauf der Sicherheitsautorisierung von Reporting Services](../../media/rosettasecurityextensionauthorizationflow.gif "Ablauf der Sicherheitsautorisierung von Reporting Services")

 Wie in diesem Diagramm angezeigt, befolgt die Autorisierung diese Reihenfolge:

1.  Sobald die Clientanwendungen authentifiziert sind, stellen sie über die Webdienstmethoden der Reporting Services Anforderungen an den Berichtsserver. Ein Authentifizierungsticket wird in Form eines Cookies im HTTP-Header jeder Webanforderung weitergeleitet.

2.  Das Cookie wird vor jeder Zugriffsprüfung überprüft.

3.  Sobald das Cookie überprüft wird, ruft der Berichtsserver <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> auf, und dem Benutzer wird eine Identität gegeben.

4.  Der Benutzer versucht, einen Vorgang über den Reporting Services-Webdienst auszuführen.

5.  Der Berichtsserver ruft die Methode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> auf.

6.  Die Sicherheitsbeschreibung wird abgerufen und an eine benutzerdefinierte Sicherheitserweiterungsimplementierung von <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> übergeben. Zu diesem Zeitpunkt wird der Benutzer, die Gruppe oder der Computer mit der Sicherheitsbeschreibung des Elements verglichen, auf das gerade ein Zugriff erfolgt. Danach erfolgt die Autorisierung zur Durchführung des angeforderten Vorgangs.

7.  Wenn der Benutzer autorisiert ist, führt der Webdienst den Vorgang durch und gibt eine Antwort an die aufrufende Anwendung zurück.


