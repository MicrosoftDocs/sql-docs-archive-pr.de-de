---
title: Abgeleitete Hierarchien mit expliziten Abschlüssen (Master Data Services) |Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609925"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>Abgeleitete Hierarchien mit expliziten Abschlüssen (Master Data Services)
  Wenn in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]die Ebenen aus einer expliziten Hierarchie als oberste Ebenen einer abgeleiteten Hierarchie verwendet werden, wird dies als abgeleitete Hierarchie mit explizitem Abschluss bezeichnet.

 Die explizite Hierarchie muss auf der gleichen Entität wie die Entität am oberen Ende der abgeleiteten Hierarchie basieren.

 In der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Benutzeroberfläche erstellen Sie diesen Hierarchietyp durch Ziehen einer expliziten Hierarchie in die oberste Ebene einer abgeleiteten Hierarchie.

 ![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")

## <a name="derived-hierarchy-with-explicit-cap-example"></a>Beispiel für eine abgeleitete Hierarchie mit explizitem Abschluss
 In diesem Beispiel stammen die Elemente in der expliziten Hierarchie aus der Entität Subcategory. In der abgeleiteten Hierarchie stammen die Elemente der obersten Ebene auch aus der Entität Unterkategorie.

 ![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")

 Durch die Verwendung der expliziten Hierarchie am oberen Rand einer abgeleiteten Hierarchie wird die abgeleitete Hierarchie unregelmäßig.

## <a name="rules"></a>Regeln

-   Sie können nicht mehr als eine explizite Hierarchie in einer abgeleiteten Hierarchie mit explizitem Abschluss haben.

-   Sie können die gleiche explizite Hierarchie als Abschluss für mehrere abgeleitete Hierarchien verwenden.

-   Sie können keine Hierarchieelementberechtigungen an abgeleitete Hierarchien mit expliziten Abschlüssen zuweisen. Wenn Sie der expliziten Hierarchie oder der abgeleiteten Hierarchie einzeln Berechtigungen zuweisen, wirken sich die Berechtigungen auf beide Hierarchien aus.

## <a name="related-tasks"></a>Related Tasks

|Taskbeschreibung|Thema|
|----------------------|-----------|
|Erstellen Sie eine abgeleitete Hierarchie.|[Erstellen einer abgeleiteten Hierarchie &#40;Master Data Services&#41;](create-a-derived-hierarchy-master-data-services.md)|
|Erstellen Sie eine explizite Hierarchie.|[Erstellen einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|Löschen Sie eine vorhandene abgeleitete Hierarchie.|[Löschen einer abgeleiteten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a>Verwandte Inhalte

-   [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


