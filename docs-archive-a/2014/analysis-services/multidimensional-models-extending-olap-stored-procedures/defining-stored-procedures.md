---
title: Definieren von gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc1f028f822d2289ee79702feb2494487040977c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700425"
---
# <a name="defining-stored-procedures"></a>Definieren von gespeicherten Prozeduren
  Sie können gespeicherte Prozeduren verwenden, um externe Routinen von aufzurufen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Sie können den Aufruf von externen Routinen über eine gespeicherte Prozedur in jeder beliebigen CLR-Sprache (Common Language Runtime) schreiben, z. B. C, C++, C#, Visual Basic oder Visual Basic .NET. Eine gespeicherte Prozedur kann einmal erstellt werden und dann in zahlreichen Kontexten aufgerufen werden, z. B. von anderen gespeicherten Prozeduren, berechneten Measures oder Clientanwendungen. Gespeicherte Prozeduren vereinfachen die Entwicklung und Implementierung von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbanken, da gemeinsamer Code nur einmal entwickelt werden muss und an einem einzelnen Ort gespeichert werden kann. Mit gespeicherten Prozeduren kann Anwendungen Geschäftsfunktionalität hinzugefügt werden, die von der systemeigenen Funktionalität von MDX nicht bereitgestellt wird.  
  
 Dieser Abschnitt enthält die Informationen, die zum Verständnis, Entwurf und zur Implementierung von gespeicherten Prozeduren erforderlich sind.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Entwerfen von gespeicherten Prozeduren](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Beschreibt das Entwerfen von Assemblys zum Verwenden mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Erstellen gespeicherter Prozeduren](creating-stored-procedures.md)|Beschreibt das Erstellen von Assemblys für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Aufrufen gespeicherter Prozeduren](calling-stored-procedures.md)|Stellt Informationen zum Verwenden von Assemblys in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereit.|  
|[Zugreifen auf den Abfragekontext in gespeicherten Prozeduren](accessing-query-context-in-stored-procedures.md)|Beschreibt das Zugreifen auf Informationen zum Gültigkeitsbereich und Kontext mit Assemblys.|  
|[Festlegen der Sicherheit für gespeicherte Prozeduren](setting-security-for-stored-procedures.md)|Beschreibt das Konfigurieren der Sicherheit für Assemblys in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Debuggen gespeicherter Prozeduren](debugging-stored-procedures.md)|Beschreibt das Debuggen von Assemblys in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung von mehrdimensionalen Modellassemblys](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
