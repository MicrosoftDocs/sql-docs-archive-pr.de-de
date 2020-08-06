---
title: Metadaten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698403"
---
# <a name="metadata-master-data-services"></a>Metadaten (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] handelt es sich bei benutzerdefinierten Metadaten um Informationen, mit denen Sie die Modellobjekte beschreiben. Sie möchten z. B. die Besitzer eines bestimmten Modells oder einer Entität oder die Quellsysteme verfolgen, die Daten für eine Entität bereitstellen.  
  
 Benutzerdefinierte Metadaten werden von einem Modell verwaltet, das als **Metadaten**bezeichnet wird. Dieses Modell wird bei der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Installation von automatisch eingeschlossen und ähnelt allen anderen MDS-Modellen, mit dem Unterschied, dass Sie keine Versionen erstellen können.  
  
 Nach dem Ausfüllen des Metadatenmodells mit benutzerdefinierten Metadaten können Sie sie in Abonnementsichten einfügen, damit sie von abonnierenden Systemen verwendet werden können.  
  
## <a name="metadata-entities"></a>Metadatenentitäten  
 Das Modell Metadaten umfasst fünf Entitäten, von denen jede einen Typ eines Masterdaten-Modellobjekts darstellt, das benutzerdefinierte Metadaten unterstützt. Beispielsweise enthält die **Definition der modellmetadatendefinition** Elemente, die Modelle darstellen, und die **Attribut Metadaten-Definitions** Entität verfügt über Member, die alle Attribute in allen Modellen darstellen.  
  
 Um Metadaten für ein Modellobjekt zu definieren, füllen Sie die Attribute eines dieser Elemente auf. Beispielsweise können Sie in der Entität **Entitäts-Metadatendefinition** das Beschreibungs Attribut des Price-Members mit dem Text Auffüllen: **dem Produkt Preis, wenn er an einen Kunden verkauft**wird.  
  
 Die Elemente im Metadatenmodell werden automatisch immer dann aktualisiert, wenn Modellobjekte, die benutzerdefinierte Metadaten unterstützen, hinzugefügt oder gelöscht werden.  
  
 Das Metadatenmodell darf nicht versionsspezifisch sein, über hinzugefügte oder geänderte Versionsflags verfügen oder als Modellbereitstellungspaket gespeichert werden. Es hat ansonsten jedoch die gleiche vollständige Funktionalität anderer Masterdatenmodelle. Sie könnten z. B. auf dem Metadatenmodell einen Satz von Geschäftsregeln implementieren, um Datenrichtlinien zu erzwingen.  
  
## <a name="customizing-your-metadata-model"></a>Anpassen des Metadatenmodells  
 Jede Metadaten-Definitionsentität schließt die Attribute Name, Code und Description ein. Sie möchten möglicherweise zusätzliche Attribute erstellen, um die Modellobjekte weiter zu beschreiben.  
  
 Sie könnten z. B. erstellen:  
  
-   Ein domänenbasiertes Attribut mit dem Namen "Besitzer", mit dem Sie den Besitzer jedes Modellobjekts verfolgen.  
  
-   Ein Freiformattribut mit dem Namen "Datum der letzten Überprüfung", mit dem Sie das Datum verfolgen, an dem ein Objekt zuletzt vom Besitzer überprüft wurde.  
  
-   Ein domänenbasiertes Attribut mit dem Namen sources, das Sie zum Nachverfolgen und Verwalten der Quell Systeme verwenden, die mit der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Instanz interagieren.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Fügen Sie einem Modellobjekt Metadaten hinzu.|[Metadaten &#40;Master Data Services hinzufügen&#41;](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Daten &#40;Master Data Services werden exportiert&#41;](overview-exporting-data-master-data-services.md)  
  
  
