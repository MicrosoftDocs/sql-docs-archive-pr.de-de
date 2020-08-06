---
title: Cachetransformation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34be3252a3caf344c95e13ae45cc485a8c4ffdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619246"
---
# <a name="cache-transform"></a>Cachetransformation
  Die Transformation für Cachetransformation generiert ein Verweisdataset für die Transformation für Suche, indem Daten aus einer verbundenen Datenquelle im Datenfluss in einen Cacheverbindungs-Manager geschrieben werden. Die Transformation für Suche führt Suchvorgänge aus, indem Daten in Eingabespalten aus einer verbundenen Datenquelle mit Spalten in der Verweisdatenbank verknüpft werden.  
  
 Sie können den Cacheverbindungs-Manager verwenden, wenn Sie die Transformation für Suche für die Ausführung im Vollcachemodus konfigurieren möchten. In diesem Modus wird das Verweisdataset in den Cache geladen, bevor die Transformation für Suche ausgeführt wird.  
  
 Anweisungen dazu, wie die Transformation für Suche im Vollcachemodus mit dem Cacheverbindungs-Manager und der Transformation für Cachetransformation konfiguriert wird, finden Sie unter [Implementieren einer Suchtransformation im Vollcachemodus mit dem Cacheverbindungs-Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).  
  
 Weitere Informationen zum Zwischenspeichern des Verweisdatasets finden Sie unter [Lookup Transformation](lookup-transformation.md).  
  
> [!NOTE]  
>  Die Cachetransformation schreibt nur eindeutige Zeilen in den Cacheverbindungs-Manager.  
  
 In einem einzelnen Paket kann nur eine Cachetransformation Daten in den gleichen Cacheverbindungs-Manager schreiben. Wenn das Paket mehrere Cachetransformationen enthält, schreibt die erste beim Ausführen des Pakets aufgerufene Cachetransformation die Daten in den Verbindungs-Manager. Bei den Schreibvorgängen nachfolgender Cachetransformationen treten Fehler auf.  
  
 Weitere Informationen finden Sie unter [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) und [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).  
  
## <a name="configuration-of-the-cache-transform"></a>Konfiguration der Cachetransformation  
 Sie können den Cacheverbindungs-Manager so konfigurieren, dass die Daten in einer Cachedatei (.caw) gespeichert werden.  
  
 Es gibt folgende Möglichkeiten, die Cachetransformation zu konfigurieren:  
  
-   Geben Sie den Cacheverbindungs-Manager an.  
  
-   Ordnen Sie die Eingabespalten in der Cachetransformation den Zielspalten im Cacheverbindungs-Manager zu.  
  
    > [!NOTE]  
    >  Jede Eingabespalte muss einer Zielspalte zugeordnet werden, und die Spaltendatentypen müssen übereinstimmen. Andernfalls zeigt der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Designer eine Fehlermeldung an.  
  
     Sie können den **Cacheverbindungs-Manager-Editor** verwenden, um Spaltendatentypen, Namen und andere Spalteneigenschaften zu ändern.  
  
 Eigenschaften können Sie mit dem [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Designer festlegen. Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Erweiterter Editor** festlegen können, finden Sie unter [Transformation Custom Properties](transformation-custom-properties.md).  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)   
 [Datenfluss](../data-flow.md)  
  
  
