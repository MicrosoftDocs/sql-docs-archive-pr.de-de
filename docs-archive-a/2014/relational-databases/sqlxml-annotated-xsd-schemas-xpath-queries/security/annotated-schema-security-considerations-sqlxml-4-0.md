---
title: Überlegungen zur Schema Sicherheit mit Anmerkungen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
author: rothja
ms.author: jroth
ms.openlocfilehash: 098f554410a846ed0223d17117b51025dfcf7897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608474"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Überlegungen zur Sicherheit von Schemas mit Anmerkungen (SQLXML 4.0)
  Im Folgenden werden Sicherheitsrichtlinien zur Verwendung von Schemas mit Anmerkungen gegeben:  
  
-   Vermeiden Sie die Verwendung der Standardzuordnung in den Zuordnungsschemas. Die Standardzuordnung macht die Datenbankinformationen (Tabellen- und Spaltennamen) im resultierenden XML-Dokument verfügbar, da standardmäßig die Elementnamen den Tabellennamen und die Attributnamen den Spaltennamen zugeordnet werden. Daher hat jeder Benutzer, der das XML-Dokument einsehen kann, auch Zugriff auf die Tabellen- und Spalteninformationen in der Datenbank, was ein mögliches Sicherheitsrisiko bedeutet. Geben Sie daher willkürlich gewählte Element- und Attributnamen im Schema an, und verwenden Sie Anmerkungen zur expliziten Zuordnung derselben zu den Tabellen und Spalten. Auf diese Weise wird das Sicherheitsrisiko vermieden. Weitere Informationen zum Verwenden der Standard Zuordnung beim Erstellen von XSD-Schemas finden Sie [unter Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Die mithilfe von Anmerkungen angegebene explizite Zuordnung macht die Datenbankinformationen (wie Tabellennamen und Spaltennamen) verfügbar. Daher werden Sie es möglicherweise vorziehen, diese Schemas nicht öffentlich verfügbar zu machen.  
  
-   Bestimmte Abfragen wie solche, die für ein Zuordnungsschema mit Rekursion angegeben werden (mit auf einen höheren Wert festgelegter `max-depth`-Anmerkung), benötigen eventuell mehr Zeit zur Ausführung. Sie können optional ein Timeout Limit angeben, indem Sie die Eigenschaft Befehls Timeout (in Sekunden) festlegen. Beispiel:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XSD-Schemas mit Anmerkungen in SQLXML 4.0](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
