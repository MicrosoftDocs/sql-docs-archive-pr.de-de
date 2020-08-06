---
title: Transformations-Editor für Suche (Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696982"
---
# <a name="lookup-transformation-editor-general-page"></a>Transformations-Editor für Suche (Seite 'Allgemein')
  Auf der Seite **Allgemein** des Dialogfelds Transformations-Editor für Suche können Sie den Cachemodus und den Verbindungstyp auswählen sowie angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Vollcache**  
 Das Verweisdataset wird generiert und in den Cache geladen, bevor die Transformation für Suche ausgeführt wird.  
  
 **Teilcache**  
 Das Verweisdataset wird während der Ausführung der Transformation für Suche generiert. Die Zeilen mit übereinstimmenden Einträgen im Verweisdataset und die Zeilen ohne übereinstimmende Einträge im Dataset werden in den Cache geladen.  
  
 **Kein Cache**  
 Das Verweisdataset wird während der Ausführung der Transformation für Suche generiert. Es werden keine Daten in den Zwischenspeicher geladen.  
  
 **Cacheverbindungs-Manager**  
 Die Transformation für Suche wird für die Verwendung eines Cacheverbindungs-Managers konfiguriert. Diese Option ist nur verfügbar, wenn die Option Vollcache ausgewählt ist.  
  
 **Teilcache**  
 Die Transformation für Suche wird für die Verwendung eines OLE DB-Verbindungs-Managers konfiguriert.  
  
 **Angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen**  
 Wählen Sie eine Option für die Behandlung von Zeilen aus, die nicht mindestens einem Eintrag im Verweisdataset entsprechen.  
  
 Wenn Sie **Zeilen an Ausgabe nicht übereinstimmender Einträge umleiten**auswählen, werden die Zeilen an eine Ausgabe nicht übereinstimmender Einträge weitergeleitet und nicht als Fehler behandelt. Die Option **Fehler** auf der Seite **Fehlerausgabe** des Dialogfelds **Transformations-Editor für Suche** ist nicht verfügbar.  
  
 Wenn Sie im Listenfeld **Angeben, wie Zeilen ohne übereinstimmende Einträge behandelt werden sollen** eine andere Option auswählen, werden die Zeilen als Fehler behandelt. In diesem Fall ist die Option **Fehler** auf der Seite **Fehlerausgabe** verfügbar.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogeintrag [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) (Suchcachemodi) auf blogs.msdn.com  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cacheverbindungs-Manager](connection-manager/cache-connection-manager.md)   
 [Transformations-Editor für Suche &#40;Verbindungs Seite&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Transformations-Editor für Suche &#40;Seite "Spalten"&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor für Suche &#40;Seite "Erweitert"&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
