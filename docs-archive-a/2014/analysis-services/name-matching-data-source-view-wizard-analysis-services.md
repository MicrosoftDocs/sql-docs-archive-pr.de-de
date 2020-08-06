---
title: Namens Übereinstimmung (Datenquellen Sicht-Assistent) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50cc46db7f582e0aea1570dadc956336ef8be074
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618343"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a>Namensübereinstimmung (Datenquellensicht-Assistent) (Analysis Services)
  Mithilfe der Seite **Namensübereinstimmung** können Sie das Kriterium auswählen, das zum Ermitteln möglicher Beziehungen zwischen den für die Datenquellensicht ausgewählten Tabellen und den anderen Tabellen im Schema verwendet wird. Wenn keine physischen Fremdschlüsselbeziehungen zwischen den Tabellen vorhanden sind, hilft dieses Kriterium dabei, verwandte Tabellen zu kennzeichnen und der Datenquellensicht hinzuzufügen. Die logischen Beziehungen, die durch die Namensübereinstimmung identifiziert sind, werden ebenfalls der Datenquellensicht hinzugefügt.  
  
> [!NOTE]  
>  Diese Seite wird nur angezeigt, wenn Sie eine Datenquelle auswählen, die mehrere Tabellen enthält, in der aber keine Fremdschlüsselbeziehungen zwischen den Tabellen bestehen.  
  
## <a name="options"></a>Tastatur  
 **Logische Beziehungen nach übereinstimmenden Spalten erstellen**  
 Legt fest, dass ein Namensübereinstimmungskriterium verwendet wird, um mögliche logische Abhängigkeiten und Beziehungen zwischen den Tabellen, die für die Datenquellensicht ausgewählt wurden, und den anderen Tabellen im Schema zu ermitteln. Wenn Sie dieses Kontrollkästchen deaktivieren, wird kein Kriterium für die Namensübereinstimmung verwendet, um logische Beziehungen zwischen den Tabellen in der Datenquelle zu identifizieren.  
  
 **Fremdschlüsselübereinstimmungen**  
 Wählen Sie das Kriterium aus, dass für das Erstellen logischer Beziehungen zwischen Tabellen und Sichten in der Datenquelle verwendet werden soll. Nicht alphanumerische Zeichen werden in übereinstimmenden Zeichenfolgen ignoriert. Die Zeichenfolgen "Customer ID", "Customer_ID" und "CustomerID" stimmen z. B. überein. Wählen Sie eine der Optionen in der folgenden Tabelle aus, um Beziehungen unter den angegebenen Bedingungen zu erstellen.  
  
|Select|Erstellte Beziehung|  
|------------|---------------|  
|**Gleicher Name wie Primärschlüssel**|Eine logische Beziehung zu jeder Tabelle mit einem Spaltennamen, der mit dem Namen der Primärschlüsselspalte in einer ausgewählten Tabelle übereinstimmt.|  
|**Gleicher Name wie Zieltabelle**|Eine logische Beziehung zu jeder Tabelle mit einem Spaltennamen, der mit dem Namen der ausgewählten Tabelle übereinstimmt.|  
|**Zieltabellenname und Primärschlüsselname**|Eine logische Beziehung zu einer beliebigen Tabelle, in der ein Spaltenname mit dem ausgewählten Tabellennamen übereinstimmt, der wiederum mit dem Namen der Primärschlüsselspalte für die ausgewählte Tabelle verkettet ist. Nicht alphanumerische Zeichen innerhalb der Verkettung werden ignoriert ("Product ID", "Product_ID" und "ProductID" stimmen z. B. überein).|  
  
 **Beschreibung und Beispiel**  
 Zeigt eine Beschreibung und ein Beispiel des ausgewählten Kriteriums an.  
  
  
