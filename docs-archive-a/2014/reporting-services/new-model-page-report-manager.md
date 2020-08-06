---
title: Neues Modell (Seite) (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed591108585b494ebb4498c1a0ab3e782693a45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620237"
---
# <a name="new-model-page-report-manager"></a>Neues Modell (Seite) (Berichts-Manager)
  Verwenden Sie diese Seite, um ein Standardberichtsmodell aus einer freigegebenen Datenquelle zu generieren. Sie können Berichtsmodelle nur aus mehrdimensionalen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenquellen, relationalen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenquellen und relationalen Oracle-Datenquellen generieren.  
  
 Modelle, die Sie im Berichts-Manager generieren, basieren auf dem Schema der freigegebenen Datenquelle. Für alle Tabellen und Spalten in der Datenquelle werden Entitäten, Ordner und Felder erstellt. Sie können weder Elemente ausschließen, noch können Sie Optionen festlegen, die bestimmen, wie das Modell generiert wird. Wenn Sie ein Modell anpassen oder verfeinern möchten, müssen Sie stattdessen den Modell-Designer verwenden.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-new-model-page"></a>So öffnen Sie die Seite "Neues Modell"  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie die freigegebene Datenquelle, von der Sie ein Modell generieren möchten.  
  
2.  Zeigen Sie auf die Datenquelle, und klicken Sie auf den Dropdownpfeil.  
  
3.  Führen Sie im Dropdownmenü einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Berichtsmodell generieren** , um die Seite Neues Modell zu öffnen.  
  
    -   Klicken Sie auf **Verwalten** , um die Seite Allgemeine Eigenschaften für den Bericht zu öffnen. Klicken Sie dann auf **Modell generieren** , um die Seite Neues Modell zu öffnen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen des Modells an. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = +, $/* \< > | " /  
  
 **Beschreibung**  
 Zeigt eine Beschreibung des Modells an. Benutzer, die dieses Element über den Berichts-Manager anzeigen, können diese Beschreibung sehen, wenn sie die Ordnerhierarchie durchsuchen.  
  
 **Speicherort ändern**  
 Zeigt den Speicherort des Ordners des neuen Modells an. Sie können auf die Schaltfläche **Speicherort ändern** klicken, um einen anderen Speicherort auszuwählen.  
  
  
