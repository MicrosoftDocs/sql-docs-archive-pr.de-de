---
title: Paketeigenschaften (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616641"
---
# <a name="package-properties-dialog-box"></a>Paketeigenschaften (Dialogfeld)
  Im Dialogfeld **Paketeigenschaften** können Sie Eigenschaften für Pakete anzeigen, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server gespeichert sind.  
  
 Weitere Informationen finden Sie unter [Integration Services-Server &#40;SSIS&#41;](integration-services-ssis-server-and-catalog.md).  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Dialogfelds "Paketeigenschaften"](#open_dialog)  
  
-   [Konfigurieren der Optionen](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> Öffnen des Dialogfelds "Paketeigenschaften"  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server her.  
  
     Sie stellen eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, die die SSISDB-Datenbank hostet.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den **SSISDB** -Knoten.  
  
4.  Erweitern Sie den Ordner mit dem Paket, für das Sie die Eigenschaften anzeigen möchten.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Paket, und wählen Sie **Eigenschaften**aus.  
  
##  <a name="configure-the-options"></a><a name="options"></a> Konfigurieren der Optionen  
 Auf der Seite **Allgemein** können Sie die Eigenschaften des ausgewählten Pakets anzeigen.  
  
 Alle Eigenschaften auf der Seite **Allgemein** sind schreibgeschützt.  
  
 **Name**  
 Zeigt den Namen des Pakets an.  
  
 **Bezeichner**  
 Listet die ID des Pakets auf.  
  
 **Einstiegspunkt**  
 Der Wert `True` gibt an, dass das Paket direkt gestartet wird. Der Wert `False` gibt an, dass das Paket von einem anderen Paket mit dem Task "Paket ausführen" gestartet wird. Standardwert: `True`.  
  
 Sie können diese Eigenschaft in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] für das übergeordnete Paket und die untergeordneten Pakete festlegen, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket und anschließend auf **Einstiegspunktpaket**klicken.  
  
 **Beschreibung**  
 Zeigt die optionale Beschreibung des Pakets an.  
  
  
