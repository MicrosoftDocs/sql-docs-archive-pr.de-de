---
title: Weiterleiten des CDC-Datenstroms gemäß Änderungstyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a9b4e0c6a196669e4cedafcecf0477b228f3001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615491"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>Weiterleiten des CDC-Datenstroms gemäß Änderungstyp
  Um eine CDC-Splittertransformation hinzuzufügen und zu konfigurieren, muss das Paket mindestens einen Datenflusstask und eine CDC-Quelle enthalten.  
  
 Für die dem Paket hinzugefügte CDC-Quelle muss ein NetCDC-Verarbeitungsmodus ausgewählt werden. Weitere Informationen zum Auswählen von Verarbeitungsmodi finden Sie unter [Quellen-Editor für CDC &#40;Seite Verbindungs-Manager&#41;](../cdc-source-editor-connection-manager-page.md).  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>So leiten Sie den CDC-Datenstrom gemäß Änderungstyp weiter  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] das [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie den CDC-Splitter dann aus der **Toolbox**auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die CDC-Quelle, die im Paket enthalten ist, mit dem CDC-Splitter.  
  
5.  Verbinden Sie den CDC-Splitter mit einem oder mehreren Zielen. Sie können Verbindungen für bis zu drei verschiedene Ausgaben herstellen.  
  
6.  Wählen Sie eine der folgenden Ausgaben aus:  
  
    -   Ausgabe löschen: Die Ausgabe, an die DELETE-Änderungszeilen geleitet werden.  
  
    -   Ausgabe einfügen: Die Ausgabe, an die INSERT-Änderungszeilen geleitet werden.  
  
    -   Ausgabe aktualisieren: Die Ausgabe, an die UPDATE-Änderungszeilen (vor/nach Update) und Merge-Änderungszeilen geleitet werden.  
  
7.  Optional können Sie die erweiterten Eigenschaften mithilfe des Dialogfelds **Erweiterter Editor** konfigurieren.  
  
     Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können.  
  
     So öffnen Sie das Dialogfeld **Erweiterter Editor** :  
  
    -   Klicken Sie auf dem Bildschirm **Datenfluss** des [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Projekts mit der rechten Maustaste auf den CDC-Splitter, und wählen Sie **Erweiterten Editor anzeigen**.  
  
     Weitere Informationen zur Verwendung des CDC-Splitters finden Sie unter CDC-Komponenten für Microsoft SQL Server Integration Services.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CDC-Splitter](cdc-splitter.md)  
  
  
