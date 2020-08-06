---
title: Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619578"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a>Aktivieren und Deaktivieren des clientseitige Drucks für Reporting Services
  Das [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX-Steuerelement **RSClientPrint**bietet Client seitiges Drucken für Berichte, die in einem Browser angezeigt werden. Vom Steuerelement wird ein benutzerdefiniertes Dialogfeld zum Drucken angezeigt, das die Funktionen enthält, die in Druckdialogfeldern üblicherweise vorkommen. Dazu zählen Druckvorschau, Seitenauswahl zum Angeben bestimmter Seiten und Bereiche, Seitenränder und Ausrichtung. Clientseitiges Drucken ist standardmäßig aktiviert, Sie können diese Funktion jedoch auf Wunsch deaktivieren.  
  
> [!NOTE]  
>  Zum Herunterladen von ActiveX-Steuerelementen sind Administratorberechtigungen erforderlich.  
  
## <a name="downloading-the-activex-control"></a>Herunterladen des ActiveX-Steuerelements  
 Benutzer, die die Druckfunktion verwenden möchten, müssen das ActiveX-Steuerelement, von dem die Clientdruckfunktionalität bereitgestellt wird, herunterladen und installieren. Wenn ein Benutzer zum ersten Mal auf der Berichts Symbolleiste auf das **Drucker** Symbol klickt, wird das Microsoft-ActiveX-Steuerelement auf den Computer heruntergeladen. Nachdem das Steuerelement heruntergeladen wurde, wird das Dialogfeld **Drucken** angezeigt, wenn der Benutzer auf das **Drucker** Symbol klickt.  
  
 Abhängig von den Browsereinstellungen bestehen folgende Möglichkeiten: Der Benutzer wird zur Installation des Steuerelements aufgefordert, die Installation des Steuerelements wird verhindert, oder das Steuerelement wird unbeaufsichtigt im Hintergrund installiert.  
  
 Für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer werden Einstellungen für das herunterladen und die Installation von ActiveX-Steuerelementen über den Knoten **ActiveX-Steuerelemente und Plug-ins** auf der Seite **Sicherheitseinstellungen** für die Webinhalts Zone angegeben. Von folgenden Einstellungen wird bestimmt, ob Benutzer das Druckensteuerelement herunterladen und ausführen können. Das Verhalten basiert auf Einstellungen der Webzonensicherheit:  
  
-   Download von signierten ActiveX-Steuerelementen.  
  
-   ActiveX-Steuerelemente ausführen, die für die Skripterstellung sicher sind.  
  
-   ActiveX-Steuerelemente und Plug-Ins ausführen.  
  
 Benutzer, die **RSClientPrint** zum Ausführen von Client seitigem Drucken verwenden möchten, müssen Folgendes aktivieren:  
  
-   **Herunterladen von signierten ActiveX** -Steuerelementen und **Skript-ActiveX-Steuer** Element, das für die Installation als sicher  
  
-   **Führen Sie ActiveX-Steuerelemente und Plug-ins** für fortlaufende Druckvorgänge aus.  
  
 Das **RSClientPrint** -ActiveX-Steuerelement wird signiert, d. h., es enthält ein gültiges digitales Zertifikat aus [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="enabling-and-disabling-client-side-printing"></a>Aktivieren und Deaktivieren des clientseitigen Druckens  
 Berichts Server Administratoren können die Druckfunktion deaktivieren, indem Sie die Berichts Server-System Eigenschaft **EnableClientPrinting** auf festlegen `false` . Dadurch wird das clientseitige Drucken für alle von diesem Server verwalteten Berichte deaktiviert. Standardmäßig ist **EnableClientPrinting** auf festgelegt `true` . Sie können das clientseitige Drucken folgendermaßen deaktivieren:  
  
-   Für einen **Berichtsserver im einheitlichen Modus**:  
  
    1.  Starten Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorrechten.  
  
    2.  Stellen Sie eine Verbindung mit einer Berichtsserverinstanz in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]her.  
  
    3.  Klicken Sie mit der rechten Maustaste auf den Berichtsserverknoten, und klicken Sie anschließend auf **Eigenschaften**. Wenn die Option **Eigenschaften** deaktiviert ist, überprüfen Sie, ob [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] mit Administratorrechten gestartet wurde.  
  
    4.  Wählen Sie **Download aktivieren für das ActiveX-Client-Druck Steuerelement aus**.  
  
    5.  Klicken Sie auf **OK**.  
  
-   Für einen **Berichtsserver im SharePoint-Modus**:  
  
    1.  Klicken Sie in der SharePoint-Zentraladministration auf **Anwendungsverwaltung**.  
  
    2.  Klicken Sie auf **Dienstanwendungen verwalten**.  
  
    3.  Klicken Sie auf den Namen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Dienst Anwendung, und klicken Sie dann im SharePoint-Menüband auf **Verwalten** .  
  
    4.  Klicken Sie auf **Systemeinstellungen**.  
  
    5.  Wählen Sie **Clientdruck aktivieren**aus. Die Option **Clientdruck aktivieren** befindet sich weiter unten auf der Seite.  
  
    6.  Klicken Sie auf **OK**.  
  
-   Schreiben Sie ein Skript oder einen Code, um die Berichts Server-System Eigenschaft **EnableClientPrinting** auf festzulegen.`false.`  
  
 Im folgenden Beispielskript wird eine Methode zum Deaktivieren des clientseitigen Druckens erläutert. Kompilieren Sie den folgenden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Code, und führen Sie ihn anschließend aus, um die Eigenschaft **EnableClientPrinting** auf **FALSE**festzulegen. Führen Sie nach der Ausführung des Codes einen Neustart von IIS aus.  
  
### <a name="sample-script"></a>Beispielskript  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
