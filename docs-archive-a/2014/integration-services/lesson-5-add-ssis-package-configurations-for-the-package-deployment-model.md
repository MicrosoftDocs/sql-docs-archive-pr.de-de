---
title: 'Lektion 5: Hinzufügen von Paket Konfigurationen für das Paket Bereitstellungs Modell | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee03d624ac7144cf6aef0829bcb7835fe5af9c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696985"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a>Lektion 5: Hinzufügen von Paketkonfigurationen für das Paketbereitstellungsmodell
  Mithilfe von Paketkonfigurationen können Sie Laufzeiteigenschaften und -variablen von außerhalb der Entwicklungsumgebung festlegen. Mithilfe von Konfigurationen können Sie Pakete entwickeln, die flexibel und einfach bereitzustellen sowie zu verteilen sind. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt die folgenden Konfigurationstypen bereit:  
  
-   XML-Konfigurationsdatei  
  
-   Umgebungsvariable  
  
-   Registrierungseintrag  
  
-   Variable für das übergeordnete Paket  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tabelle  
  
 In dieser Lektion ändern Sie das einfache [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket, das Sie in [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) erstellt haben, um das Paketbereitstellungsmodell und die Paketkonfigurationen nutzen zu können. Sie können auch das abgeschlossene Paket aus Lektion 4 kopieren, das im Lieferumfang der Lernprogramme enthalten ist. Mithilfe des Paketkonfigurations-Assistenten erstellen Sie eine XML-Konfiguration, von der die `Directory`-Eigenschaft des Foreach-Schleifencontainers mithilfe einer Variablen auf Paketebene aktualisiert wird, die der Directory-Eigenschaft zugeordnet ist. Nach dem Erstellen der Konfigurationsdatei ändern Sie den Wert der Variablen von außerhalb der Entwicklungsumgebung und legen die geänderte Eigenschaft als Zeiger auf einen neuen Beispieldatenordner fest. Wenn Sie das Paket erneut ausführen, füllt die Konfigurationsdatei den Wert der Variablen auf, und die Variable aktualisiert wiederum die- `Directory` Eigenschaft. Im Ergebnis iteriert das Paket durch die Dateien im neuen Datenordner, und nicht durch die Dateien im Originalordner, der im Paket hartcodiert war.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Reporting Services Produktbeispiel-Projekt auf CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Schritt 3: Ändern des Konfigurationswerts der Directory-Eigenschaft](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Schritt 4: Testen des Tutorialpakets aus Lektion 5](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
