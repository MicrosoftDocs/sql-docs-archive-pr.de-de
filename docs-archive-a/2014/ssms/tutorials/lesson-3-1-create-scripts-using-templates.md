---
title: Erstellen von Skripts mit Vorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b404ecc505e93c302e4c737f9c0b0161d9015519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717149"
---
# <a name="create-scripts-using-templates"></a>Erstellen von Skripts mit Vorlagen
  Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] stellt eine große Anzahl von Skriptvorlagen zur Verfügung, die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen für viele häufig ausgeführte Aufgaben umfassen. Diese Vorlagen enthalten Parameter für Werte, die vom Benutzer angegeben werden, wie z. B. der Tabellenname. Wenn Sie Parameter verwenden, brauchen Sie den Namen nur einmal einzugeben, er wird dann automatisch an alle erforderlichen Stellen im Skript kopiert. Sie können auch eigene, benutzerspezifische Vorlagen für die Skripts erstellen, die Sie am häufigsten benötigen. Sie können die Vorlagenstruktur neu anordnen, Vorlagen verschieben oder neue Ordner für Vorlagen anlegen. In der folgenden Übung verwenden Sie eine Vorlage zum Anlegen einer Datenbank.  
  
## <a name="using-templates"></a>Verwenden von Vorlagen  
  
#### <a name="to-create-a-script-using-a-template"></a>So erstellen Sie ein Skript mithilfe einer Vorlage  
  
1.  Klicken Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]im Menü **Ansicht** auf **Vorlagen-Explorer**.  
  
2.  Die Vorlagen im Vorlagen-Explorer sind in Gruppen angeordnet. Erweitern Sie **Datenbank**, und doppelklicken Sie anschließend auf **Datenbank erstellen**.  
  
3.  Vervollständigen Sie im Dialogfeld **Verbindung mit Datenbank-Engine herstellen** die Verbindungseinstellungen, und klicken Sie anschließend auf **Verbinden**. Ein neues Fenster des Abfrage-Editors wird geöffnet, in dem der Inhalt der Vorlage **Datenbank erstellen** angezeigt wird.  
  
4.  Klicken Sie im Menü **Abfrage** auf **Werte für Vorlagenparameter angeben**.  
  
5.  Im Dialogfeld **Werte für Vorlagenparameter angeben** enthält die **Wert** -Spalte einen empfohlenen Wert für den Parameter **Database_Name** . Geben Sie im Feld des Parameters **Database_Name** den Begriff **Marketing**ein, und klicken Sie auf **OK**. "Marketing" wird jetzt im Skript an mehreren Stellen eingefügt.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen von benutzerdefinierten Vorlagen](lesson-3-2-create-custom-templates.md)  
  
  
