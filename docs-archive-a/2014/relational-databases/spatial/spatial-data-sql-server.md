---
title: Räumliche Daten (SQL Server) | Microsoft-Dokumentation
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4d491420a9eca7c35b89b254a03381c6467c834c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87621953"
---
# <a name="spatial-data-sql-server"></a>Räumliche Daten (SQL Server)
  Räumliche Daten repräsentieren Daten zur physischen Position und Form geometrischer Objekte. Diese Objekte können Punktpositionen oder komplexere Objekte wie Länder, Straßen oder Seen sein.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt zwei Typen von räumlichen Daten: den `geometry`-Datentyp und den `geography`-Datentyp.  
  
-   Der `geometry`-Typ stellt Daten in einem euklidischen (flachen) Koordinatensystem dar.  
  
-   Der `geography`-Typ stellt Daten in einem Erdkugel-Koordinatensystem dar.  
  
 Beide Datentypen werden als .NET CLR (Common Language Runtime)-Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]implementiert.  
  
> [!IMPORTANT]  
>  Laden Sie für eine ausführliche Beschreibung und Beispiele der in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführten räumlichen Funktionen das Whitepaper [Neue räumliche Funktionen in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)herunter.  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Verwandte Aufgaben  
 [Erstellen, Aufbauen und Abfragen von geometry-Instanzen](create-construct-and-query-geometry-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geometry-Datentyps verwendet werden können.  
  
 [Erstellen, Aufbauen und Abfragen von geography-Instanzen](create-construct-and-query-geography-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geography-Datentyps verwendet werden können.  
  
 [Abfragen von nächsten Nachbarn aus räumlichen Daten](query-spatial-data-for-nearest-neighbor.md)  
 Beschreibt das allgemeine Abfragemuster, das zum Suchen der räumlichen Objekte, die einem bestimmten räumlichen Objekt am nächsten liegen, verwendet wird.  
  
 [Erstellen, Ändern und Löschen von räumlichen Indizes](create-modify-and-drop-spatial-indexes.md)  
 Stellt Informationen zum Erstellen, Ändern und Löschen eines räumlichen Indexes bereit.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Übersicht über räumliche Datentypen](spatial-data-types-overview.md)  
 Bietet eine Einführung in die räumlichen Datentypen.  
  
-   [Point](point.md)  
  
-   [LineString](linestring.md)  
  
-   [CircularString](circularstring.md)  
  
-   [CompoundCurve](compoundcurve.md)  
  
-   [Polygon](polygon.md)  
  
-   [CurvePolygon](curvepolygon.md)  
  
-   [MultiPoint](multipoint.md)  
  
-   [MultiLineString](multilinestring.md)  
  
-   [MultiPolygon](multipolygon.md)  
  
-   [GeometryCollection](geometrycollection.md)  
  
 [Übersicht über räumliche Indizes](spatial-indexes-overview.md)  
 Bietet eine Einführung in räumliche Indizes und beschreibt Mosaik und Mosaikschemas.  
  
  
