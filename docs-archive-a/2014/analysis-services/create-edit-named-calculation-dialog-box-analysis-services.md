---
title: Benannte Berechnung erstellen/bearbeiten (Dialog Feld) (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b6777feb47a1ce6b601d0190e413b4baae35f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608107"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Benannte Berechnung erstellen/bearbeiten (Dialog Feld) (Analysis Services)
  Mithilfe des Dialogfelds **Benannte Berechnung erstellen/bearbeiten** können Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine benannte Berechnung für eine Tabelle in einer Datenquellensicht definieren oder ändern. Führen Sie zum Anzeigen des Dialogfelds **Benannte Berechnung erstellen/bearbeiten** einen der folgenden Schritte aus:  
  
-   Klicken Sie im Bereich **Symbolleiste** von **Datenquellensicht-Designer** auf **Neue benannte Berechnung**.  
  
-   Klicken Sie im Bereich **Tabellen** oder **Diagramm** des **Datenquellensicht-Designers** mit der rechten Maustaste auf eine Tabelle, und wählen Sie **Neue benannte Berechnung** aus.  
  
-   Klicken Sie im Bereich **Diagramm** des **Datenquellensicht-Designers** mit der rechten Maustaste auf den Namen einer benannten Berechnung, und wählen Sie **Benannte Berechnung bearbeiten** aus.  
  
## <a name="options"></a>Tastatur  
 **Spaltenname**  
 Geben Sie den Namen der benannten Berechnung ein.  
  
 **Beschreibung**  
 Geben Sie die optionale Beschreibung der benannten Berechnung ein.  
  
 **Ausdruck**  
 Geben Sie einen gültigen SQL-Ausdruck ein, der einen skalaren Wert zurückgibt. Der Ausdruck wird an den Anbieter gesendet und im folgenden Ausdruck überprüft:  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 Der Ausdruck kann Verweise auf andere Tabellen in Form einer untergeordneten SELECT-Anweisung enthalten. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Datenquellensicht-Designer &#40;Analysis Services – Mehrdimensionale Daten&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
