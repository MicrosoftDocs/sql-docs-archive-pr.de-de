---
title: Vorschau der ausgewählten Tabelle (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725057"
---
# <a name="preview-selected-table-ssas"></a>Vorschau der ausgewählten Tabelle (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie die Daten in der ausgewählten Tabelle in der Vorschau anzeigen, die Spalten auswählen, die im Datenimport enthalten sein sollen, und Daten in den ausgewählten Spalten filtern. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Nicht alle Zeilen in der Tabelle werden angezeigt. Die festgelegten Filter werden jedoch während des Imports auf alle Daten in der Tabelle angewendet.  
  
 Für Datenquellen mit Windows-Authentifizierung werden die Anmeldeinformationen des aktuellen Benutzers verwendet, um die im Dialogfeld Vorschau anzeigen und filtern angezeigten Daten abzurufen. Für andere Datenquellen werden die in der Verbindungszeichenfolge angegebenen Anmeldeinformationen zum Abrufen der Daten verwendet.  
  
 Die Darstellung der Daten auf dieser Seite garantiert nicht, dass der Import erfolgreich ist. Der Import ist nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzername nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
 **Kontrollkästchen in der Spaltenüberschrift**  
 Aktivieren Sie das Kontrollkästchen, um die Spalte in den Datenimport einzuschließen. Deaktivieren Sie das Kontrollkästchen, um die Spalte aus dem Datenimport zu entfernen.  
  
 **Schaltfläche mit Abwärtspfeil in der Spaltenüberschrift**  
 Filtern Sie Daten in der Spalte.  
  
 **Zeilenfilter löschen**  
 Entfernen Sie alle Filter, die auf die Daten in den Spalten angewendet wurden.  
  
  
