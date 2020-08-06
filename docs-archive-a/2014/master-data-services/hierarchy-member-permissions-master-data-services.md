---
title: Berechtigungen für Hierarchieelemente (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81716dbd0ad08b6e92a2edb8f1d142b46bf3d24d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619180"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>Berechtigungen für Hierarchieelemente (Master Data Services)
  Berechtigungen für Hierarchieelemente sind optional und sollten nur verwendet werden, wenn ein Benutzer beschränkten Zugriff auf bestimmte Elemente erhalten soll. Wenn Sie keine Berechtigungen auf der Registerkarte **Hierarchieelemente** zuweisen, basieren die Berechtigungen eines Benutzers ausschließlich auf den Berechtigungen, die auf der Registerkarte **Modelle** zugewiesen wurden.  
  
 Berechtigungen für Hierarchie Elemente werden in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Benutzeroberfläche (UI) im Funktionsbereich **Benutzer-und Gruppenberechtigungen** auf der Registerkarte **Hierarchie** Elemente zugewiesen. Diese Berechtigungen legen fest, auf welche Elemente ein Benutzer im Funktionsbereich **Explorer** der Benutzeroberfläche zugreifen kann.  
  
 Auf der Registerkarte **Hierarchieelemente** wird jede Hierarchie als Baumstruktur dargestellt. Wenn Sie eine Berechtigung für einen Knoten in der Struktur zuweisen, erben alle untergeordneten Elemente diese Berechtigung, sofern sie nicht auf einer niedrigeren Ebene explizit zugewiesen wurde.  
  
> [!NOTE]  
>  Wenn Sie einem Hierarchieknoten eine Berechtigung zuweisen, werden alle Elemente in den anderen Knoten auf gleicher oder höherer Ebene implizit verweigert.  
  
 Im **Explorer**werden die Elementberechtigungen überall dort angewendet, wo das Element angezeigt wird. Ein **Member mit der** Berechtigung schreibgeschützt ist beispielsweise in allen Entitäten, Hierarchien und Auflistungen, zu denen er gehört, schreibgeschützt.  
  
 Berechtigungen für Hierarchieelemente gelten für die Modellversion, denen sie zugewiesen werden, sowie für alle zukünftigen Kopien der Version. Sie gelten nicht für Vorgängerversionen der Version, der sie zugewiesen wurden.  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Schreibgeschützt**|Die Elemente werden zwar angezeigt, können vom Benutzer jedoch nicht geändert werden. Darüber hinaus kann der Benutzer keine Elemente in expliziten Hierarchien oder Auflistungen verschieben, denen die Elemente angehören.<br /><br /> Hinweis: Wenn Sie **root**die Schreib **geschützte Berechtigung zuweisen** , sind die Elemente unter **root** schreibgeschützt. in expliziten Hierarchien und Auflistungen kann der Benutzer jedoch **Elemente in den Stamm verschieben und dem** Stamm neue **Member hinzufügen.**|  
|**Aktualisieren**|Die Elemente werden angezeigt und können vom Benutzer geändert werden. Der Benutzer kann die Elemente außerdem in beliebigen expliziten Hierarchien oder Auflistungen verschieben, denen die Elemente angehören.|  
|**Deny** (Verweigern)|Die Elemente werden nicht angezeigt.|  
  
 Auf der Registerkarte **Hierarchieelemente** werden die zugewiesenen Berechtigungen nicht sofort wirksam. Wie häufig die Berechtigungen angewendet werden, hängt von der Einstellung **Member security processing interval setting** (Intervall für die Verarbeitung der Mitgliedersicherheit) ab, die Sie in der Tabelle „Systemeinstellungen“ der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank vornehmen. Eine Anleitung für die sofortige Anwendung von Elementberechtigungen finden Sie unter [Sofortiges Anwenden von Elementberechtigungen &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)neue Elemente hinzufügen.  
  
> [!NOTE]  
>  Sie können rekursiven Hierarchien, abgeleiteten Hierarchien mit expliziten Abschlüssen und abgeleiteten Hierarchien mit ausgeblendeten Ebenen keine Hierarchieelementberechtigungen zuweisen.  
  
## <a name="possible-overlapping-permissions"></a>Mögliche Überlappungen bei Berechtigungen  
 Wenn Sie Elementen eine Berechtigung zuweisen, müssen möglicherweise überlappende Berechtigungen aufgelöst werden.  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>Wenn ein Element mehreren Hierarchien angehört  
 Das gleiche Element kann in zwei oder mehr Hierarchien enthalten sein.  
  
-   Wenn einem Hierarchie Knoten die Berechtigung **Aktualisieren** zugewiesen und einem anderen der **Lese**Zugriff zugewiesen ist **, sind die**Elemente im Knoten schreibgeschützt.  
  
-   Wenn einem Hierarchie Knoten **die Berechtigung** **Aktualisieren** oder schreibgeschützt zugewiesen wird und ein anderer Knoten **Deny**zugewiesen ist, werden die Elemente im Knoten nicht angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hierarchie Element Berechtigungen &#40;Master Data Services zuweisen&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Wie Berechtigungen &#40;Master Data Services bestimmt werden&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Mitglieder &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md)   
 [Sofortiges Anwenden von Elementberechtigungen &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)  
  
  
