---
title: Installieren und Deinstallieren der odata-Quell Komponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad0a86c6226f408b0495569d0a853dd7340aeca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618190"
---
# <a name="install-and-uninstall-odata-source-component"></a>Installieren und Deinstallieren der OData-Quellkomponente
  Dieses Thema enthält Anweisungen zum Installieren oder Entfernen der OData-Quellkomponente auf dem Computer.  
  
## <a name="installation"></a>Installation  
 Die folgenden Komponenten müssen auf dem Computer installiert sein, um die OData-Quellkomponente installieren zu können.  
  
-   SQL Server Data Tools (zum Entwerfen von Paketen)  
  
-   SQL Server Integration Services (zum Ausführen von Paketen außerhalb von Visual Studio)  
  
 Um die odata-Quell Komponente zu installieren, laden Sie [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999) herunter, und führen Sie eine der folgenden MSI-Dateien aus.  
  
-   ODataSourceForSQLServer2014-amd64.msi für 64-Bit-Plattformen  
  
-   ODataSourceForSQLServer2014-x86.msi für 32-Bit-Plattformen  
  
> [!IMPORTANT]  
>  Mit dem 64-Bit-Installationsprogramm installieren Sie sowohl die 32-Bit- als auch die 64-Bit-Version der OData-Quellkomponente. Das 32-Bit-Installationsprogramm müssen Sie nur ausführen, wenn Sie ein 32-Bit-Betriebssystem verwenden.  
  
## <a name="uninstallation"></a>Deinstallation  
 Die odata-Quell Komponente kann im Menü " **Programme und Funktionen** " deinstalliert werden. Suchen Sie den Eintrag **Microsoft SQL Server SSIS-odata-Quell Komponente (x64)** , und klicken Sie auf **deinstallieren**.  
  
  
