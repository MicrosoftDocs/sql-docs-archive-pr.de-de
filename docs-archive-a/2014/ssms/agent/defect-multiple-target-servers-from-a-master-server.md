---
title: Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699224"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Defect Multiple Target Servers from a Master Server
  In diesem Thema wird beschrieben, wie Sie den Austritt mehrerer Zielserver aus einer Multiserver-Verwaltungskonfiguration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]vollziehen. Führen Sie die folgenden Schritte auf dem Masterserver aus.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>So tragen Sie bei einem Masterserver mehrere Zielserver aus  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server, der als Masterserver konfiguriert ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserververwaltung**, und klicken Sie dann auf **Zielserver verwalten**.  
  
3.  Klicken Sie auf **Anweisungen bereitstellen**, und klicken Sie in der Liste **Anweisungstyp** auf **Austragen**.  
  
4.  Führen Sie unter **Empfänger**eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Alle Zielserver** , um alle Zielserver dieses Masterservers auszutragen. Verwenden Sie diese Option, wenn die aktuelle Multiserververwaltungskonfiguration vollständig deinstalliert werden soll.  
  
    -   Klicken Sie auf **Diese Zielserver**, und klicken Sie dann auf das entsprechende Feld **Auswählen** , um einige, aber nicht alle Zielserver dieses Masterservers auszutragen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)   
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)   
 [Vollziehen des Austritts eines Zielservers aus einem Masterserver](defect-a-target-server-from-a-master-server.md)  
  
  
