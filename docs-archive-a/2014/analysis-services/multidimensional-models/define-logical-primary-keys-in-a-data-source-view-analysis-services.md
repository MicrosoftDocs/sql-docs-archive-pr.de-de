---
title: Definieren logischer Primärschlüssel in einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25092e5d754381c572dcdbfc03e5ee0f29c1df24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618387"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a>Definieren logischer Primärschlüssel in einer Datenquellensicht (Analysis Services)
  Der Datenquellensicht-Assistent und der Datenquellensicht-Designer definieren automatisch einen Primärschlüssel für eine Tabelle, die einer Datenquellensicht basierend auf der zugrunde liegenden Datenbanktabelle hinzugefügt wird.  
  
 Es kann jedoch zeitweise erforderlich sein, einen Primärschlüssel manuell in der Datenquellensicht zu definieren. Aus Leistungs- oder Entwurfsgründen haben Tabellen in einer Datenquelle z. B. möglicherweise keine explizit definierten Primärschlüsselspalten. In benannten Abfragen und Sichten kann die Primärschlüsselspalte einer Tabelle ebenfalls fehlen. Wenn für eine Tabelle, Sicht oder benannte Abfrage kein physischer Primärschlüssel definiert ist, können Sie im Datenquellensicht-Designer manuell einen logischen Primärschlüssel für die Tabelle, Sicht oder benannte Abfrage definieren.  
  
## <a name="set-a-logical-primary-key"></a>Festlegen eines logischen Primärschlüssels  
 Primärschlüssel werden in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] benötigt, um Datensätze in Tabellen eindeutig zu identifizieren, um Schlüsselspalten in Dimensionstabellen zu identifizieren und um Beziehungen zwischen Tabellen, Sichten und benannten Abfragen zu unterstützen. Diese Beziehungen werden verwendet, um Abfragen zum Abrufen von Daten und Metadaten aus zugrunde liegenden Datenquellen zu erstellen und um erweiterte Business Intelligence-Funktionen zu nutzen.  
  
 Jede Spalte kann für den logischen Primärschlüssel verwendet werden, einschließlich einer benannten Berechnung. Wenn Sie einen logischen Primärschlüssel erstellen, wird eine eindeutige Einschränkung in der Datenquellensicht erstellt und als Primärschlüsseleinschränkung markiert. Jeder andere in der ausgewählten Tabelle festgelegte, vorhandene logische Primärschlüssel wird gelöscht.  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, oder stellen Sie eine Verbindung mit der Datenbank her, das bzw. die die Datenquellensicht enthält, in der Sie einen logischen Primärschlüssel festlegen möchten.  
  
2.  Erweitern Sie im Projektmappen-Explorer den Ordner **Datenquellensichten** , und doppelklicken Sie anschließend auf die Datenquellensicht.  
  
     Wenn Sie eine Tabelle oder Sicht suchen möchten, können Sie die Option **Tabelle suchen** verwenden, indem Sie entweder auf das Menü **Datenquellen Sicht** klicken oder mit der rechten Maustaste auf einen geöffneten Bereich der **Tabellen** -oder **Diagramm** Bereiche klicken.  
  
3.  Klicken Sie im Bereich **Tabellen** oder **Diagramm** mit der rechten Maustaste auf die Spalte(n), mit denen Sie einen logischen Primärschlüssel definierten möchten, und klicken Sie anschließend auf **Logischen Primärschlüssel festlegen**.  
  
     Die Option zum Festlegen eines logischen Primärschlüssels steht nur für Tabellen zur Verfügung, die keinen Primärschlüssel aufweisen.  
  
     Beachten Sie, dass die Primärschlüsselspalten nach dem Festlegen des Schlüssels mit einem Schlüsselsymbol gekennzeichnet sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen Sichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Definieren von benannten Berechnungen in einer Datenquellensicht &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
