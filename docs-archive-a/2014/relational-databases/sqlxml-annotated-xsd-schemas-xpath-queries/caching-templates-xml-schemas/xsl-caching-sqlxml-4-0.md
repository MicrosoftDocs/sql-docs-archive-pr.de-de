---
title: XSL-Zwischenspeichern (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: rothja
ms.author: jroth
ms.openlocfilehash: e41f247c34c1b40bedfdf6924a45afe5f63735b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700916"
---
# <a name="xsl-caching-sqlxml-40"></a>XSL-Zwischenspeichern (SQLXML 4.0)
  Das Zwischenspeichern von XSL-Stylesheets verbessert die Leistung. Bei der ersten Ausführung bleibt ein XSL-Stylesheet im Arbeitsspeicher, wenn das XSL-Zwischenspeichern auf ON festgelegt wurde. Dies verbessert die Leistung bei der nachfolgenden Verarbeitung. Die Standardeinstellung ist ON.  
  
 Sie können die XSL-Cachegröße festlegen, indem Sie den folgenden Schlüssel in der Registrierung hinzufügen:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Die XSL-Cachegröße sollte auf Basis des vorhandenen Arbeitsspeichers und der Anzahl der von Ihnen verwendeten XSL-Stylesheets festgelegt werden. Der Standardwert von **XSLCacheSize** lautet 31. Sie können die Cachegröße erhöhen, wenn der XSL-Zugriff langsam erscheint, oder die Cachegröße verringern, wenn der Arbeitsspeicher zu gering ist.  
  
 Für bessere Leistung wird empfohlen, dass Sie **XSLCacheSize** auf einen höheren Wert als die Anzahl der von Ihnen üblicherweise verwendeten XSL-Stylesheets festlegen. Wenn **XSLCacheSize** auf einen niedrigeren Wert als die Anzahl Ihrer XSL-Stylesheets festgelegt ist, sinkt die Leistung mit zunehmender Anzahl von XSL-Stylesheets. Der **XSLCacheSize** kann auf ein Maximum von 128 festgelegt werden.  
  
 Jedes Mal, wenn das zwischengespeicherte XSL-Stylesheet verwendet wird, wird die Änderungszeit der XSL-Datei überprüft, um festzustellen, ob sie aktualisiert werden muss. Das liegt daran, dass die Datenträgerkopie neuer als die Cachekopie ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zwischenspeichern von Vorlagen &#40;SQLXML 4,0&#41;](template-caching-sqlxml-4-0.md)   
 [Schema Caching &#40;SQLXML 4,0&#41;](schema-caching-sqlxml-4-0.md)  
  
  
