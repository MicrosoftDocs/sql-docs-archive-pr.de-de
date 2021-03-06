---
title: MSSQLSERVER_17832 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17828 (Database Engine error)
- maxtokensize
- 17832 (Database Engine error)
- login packet (bad)
ms.assetid: bd56ffe4-0855-4ada-8aca-251fbc6ff2ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba214e2cce04ff2583e12ae7cee9b54373390a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696902"
---
# <a name="mssqlserver_17832"></a>MSSQLSERVER_17832
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|17832|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_BAD_LOGIN_PKT|  
|Meldungstext|Das zum Öffnen der Verbindung verwendete Anmeldungspaket weist eine ungültige Struktur auf. Die Verbindung wurde geschlossen. Wenden Sie sich an den Hersteller der Clientbibliothek.%*ls|  
  
## <a name="explanation"></a>Erklärung  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer konnte das Clientanmeldepaket nicht verarbeiten. Das liegt möglicherweise daran, dass das Paket nicht ordnungsgemäß erstellt wurde oder dass das Paket während der Übertragung beschädigt wurde. Es kann auch durch die Konfiguration des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computers verursacht werden. Die aufgeführte IP-Adresse ist die Adresse des Clientcomputers.  
  
### <a name="more-information"></a>Weitere Informationen  
 Bei der Verwendung der Windows-Authentifizierung in einer Kerberos-Umgebung empfängt der Client ein Kerberos-Ticket, das ein Zertifikat mit Berechtigungsattributen (Privilege Attribute Certificate, PAC) enthält. Das PAC enthält verschiedene Typen von Autorisierungsdaten einschließlich Gruppen, in denen der Benutzer Mitglied ist, Rechte, über die der Benutzer verfügt, und welche Richtlinien für den Benutzer gelten. Wenn der Client das Kerberos-Ticket empfängt, werden die in dem PAC enthaltenen Informationen verwendet, um das Zugriffstoken des Benutzers zu generieren. Der Client stellt das Token für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer als Teil des Anmeldungspakets bereit.  
  
 Wenn das Token nicht ordnungsgemäß erstellt wurde oder während der Übertragung beschädigt wurde, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine weiteren Informationen über das Problem anbieten.  
  
 Wenn der Benutzer Mitglied zahlreicher Gruppen ist oder über zahlreiche Richtlinien verfügt, kann das Token bei ihrer Auflistung größer als üblich werden. Wenn das Token größer als der **MaxTokenSize**-Wert des Servercomputers wird, schlägt die Herstellung einer Verbindung durch den Client mit einem allgemeinen Netzwerkfehler (General Network Error, GNE) fehl, und es kann Fehler 17832 auftreten. Dieses Problem beeinflusst möglicherweise nur einige Benutzer: Benutzer mit vielen Gruppen oder Richtlinien. Wenn das Problem in dem **MaxTokenSize**-Wert des Servercomputers besteht, wird Fehler 17832 im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll von einem Fehler mit dem Status 9 begleitet. Weitere Einzelheiten zu Kerberos und **MaxTokenSize** finden Sie unter [KB327825](https://support.microsoft.com/kb/327825).  
  
## <a name="user-action"></a>Benutzeraktion  
 Um dieses Problem zu beheben, erhöhen Sie den **MaxTokenSize**-Wert des Servercomputers so weit, dass er das größte Token aller Benutzer in der Organisation enthalten kann. Um die richtige Tokengröße für die Organisation zu ermitteln, ziehen Sie die Verwendung der Anwendung **Tokensz** in Erwägung.   
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 **So ändern Sie die maxtekensize auf dem Server Computer**  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**.  
  
2.  Geben `regedit` Sie ein, und klicken Sie dann auf **OK**. (Wenn das Dialogfeld **Benutzerkontensteuerung** angezeigt wird, klicken Sie auf **Weiter**.)  
  
3.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**.  
  
4.  Wenn der **MaxTokenSize**-Parameter nicht vorhanden ist, klicken Sie mit der rechten Maustaste auf **Parameter**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **DWORD (32-Bit)** -Wert. Geben Sie dem Registrierungseintrag die Bezeichnung **MaxTokenSize**.  
  
5.  Klicken Sie mit der rechten Maustaste auf **MaxTokenSize**, und klicken Sie anschließend auf **Ändern**.  
  
6.  Geben Sie im Feld **Wertdaten** den gewünschten **MaxTokenSize**-Wert an.  
  
    > [!NOTE]  
    >  Der Hexadezimalwert ffff (Dezimalwert 65535) ist die maximale empfohlene Tokengröße. Durch die Bereitstellung dieses Werts würde das Problem wahrscheinlich gelöst, dies könnte sich jedoch hinsichtlich der Leistung negativ auf den gesamten Computer auswirken. Es wird empfohlen, dass Sie den Mindest-**MaxTokenSize**-Wert festlegen, der das größte Token aller Benutzer in der Organisation zulässt, und dass Sie diesen Wert eingeben.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  Schließen Sie den **Registrierungs-Editor**.  
  
9. Starten Sie den Computer neu.  
  
  
