---
title: Erstellen oder Löschen eines Serveralias für die Verwendung durch einen Client (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- server alias
helpviewer_keywords:
- aliases [SQL Server], deleting
- aliases [SQL Server], creating
ms.assetid: b687e376-ee33-470d-b65a-87246bfefe6f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bead257b40c33e3640b18890a7d109d774131123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618904"
---
# <a name="create-or-delete-a-server-alias-for-use-by-a-client-sql-server-configuration-manager"></a>Erstellen oder Löschen eines Serveralias für die Verwendung durch einen Client (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie einen Serveralias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe des SQL Server-Konfigurations-Managers erstellen oder löschen können. Bei einem Alias handelt es sich um einen alternativen Namen, der zum Herstellen einer Verbindung verwendet werden kann. In dem Alias eingeschlossen werden erforderliche Elemente einer Verbindungszeichenfolge. Diese Elemente werden mit einem vom Benutzer ausgewählten Namen offen gelegt. Aliase können mit jeder Clientanwendung verwendet werden. Mithilfe von Serveraliasnamen kann der Clientcomputer eine Verbindung mit mehreren Servern über verschiedene Netzwerkprotokolle herstellen, ohne jeweils das Protokoll und die Verbindungsdetails angeben zu müssen. Des Weiteren können mehrere Netzwerkprotokolle gleichzeitig aktiviert sein, auch wenn Sie diese Protokolle nur sporadisch nutzen. Wenn Sie den Server so konfiguriert haben, dass dieser an einer nicht standardmäßigen Portnummer oder Named Pipe lauscht und dabei der SQL Server-Browserdienst deaktiviert ist, erstellen Sie einen Alias, mit dem die neue Portnummer oder Named Pipe angegeben wird.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-create-an-alias"></a>So erstellen Sie einen Alias  
  
1.  Erweitern Sie im SQL Server-Konfigurations-Manager den Eintrag **SQL Server Native Client-Konfiguration**, klicken Sie mit der rechten Maustaste auf **Aliase**, und klicken Sie auf **Neuer Alias**.  
  
2.  Geben Sie im Feld **Aliasname** den Namen des Alias ein. Die Clientanwendungen verwenden diesen Namen, wenn eine Verbindung aufgebaut werden soll.  
  
3.  Geben Sie in das Feld **Server** den Namen oder die IP-Adresse eines Servers ein. Bei einer benannten Instanz hängen Sie den Namen der Instanz an.  
  
4.  Wählen Sie im Feld **Protokoll** das zu verwendende Protokoll für diesen Alias aus. Sobald Sie ein Protokoll angegeben haben, erhält das optionale Eigenschaftsfeld die Bezeichnung "Portnummer", "Pipename" oder "Verbindungszeichenfolge".  
  
 Die in der Hilfe zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager beschriebenen Verbindungszeichenfolgen können für Programmierer hilfreich sein, die ihre eigenen Verbindungszeichenfolgen erstellen. Drücken Sie F1, oder rufen Sie die **Hilfe** auf, um auf diese Informationen, im Dialogfeld **Neuer Alias**, zuzugreifen.  
  
> [!NOTE]  
>  Wenn ein konfigurierter Alias eine Verbindung mit dem falschen Server oder zur falschen Instanz herstellt, deaktivieren Sie das zugeordnete Netzwerkprotokoll, und aktivieren Sie es erneut. Dadurch werden alle zwischengespeicherten Verbindungsinformationen gelöscht, und der Client kann die Verbindung ordnungsgemäß herstellen.  
  
#### <a name="to-delete-an-alias"></a>So löschen Sie einen Alias  
  
1.  Erweitern Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager **SQL Server Native Client-Konfiguration**, und klicken Sie dann auf **Aliase**.  
  
2.  Klicken Sie im Detailbereich mit der rechten Maustaste auf den Alias, den Sie löschen möchten, und klicken Sie dann auf **Löschen**.  
  
  
