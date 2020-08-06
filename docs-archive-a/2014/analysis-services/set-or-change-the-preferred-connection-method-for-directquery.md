---
title: Festlegen oder Ändern der bevorzugten Verbindungsmethode für directquery | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721833"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery
  Wenn Sie ein Modell für die Verwendung im DirectQuery-Modus erstellen, müssen Sie zuerst die Entwurfsumgebung konfigurieren, um die Verwendung von DirectQuery zu unterstützen. Informationen hierzu finden Sie unter [enable directquery Design Mode &#40;SSAS tabellarischer&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).  
  
 Wenn Sie zur Bereitstellung des Modells bereit sind, müssen Sie einige zusätzliche Eigenschaften festlegen, um Benutzern den Zugriff auf das Modell mit einem der DirectQuery-Modi zu ermöglichen:  
  
-   Sie müssen angeben, ob in Abfragen für das Modell zwischengespeicherte Daten oder die relationale Datenquelle verwendet werden soll. Sie können nur einen Hybridmodus oder DirectQuery verwenden.  
  
-   Wenn Sie Partitionen verwenden, müssen Sie angeben, welche Partition als DirectQuery-Datenquelle verwendet werden soll.  
  
-   Sie müssen Identitätswechseloptionen für Benutzer festlegen, die auf die SQL Server-Datenquelle zugreifen.  
  
 In dieser Prozedur wird beschrieben, wie die bevorzugte Verbindungsmethode für ein DirectQuery-Modell im Designer festgelegt wird. Zudem wird geschildert, wie die Eigenschaft in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] nach der Bereitstellung des Modells geändert werden kann.  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>So legen Sie die bevorzugte Verbindungsmethode für ein DirectQuery-Modell fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]die Lösungsdatei für das DirectQuery-Modell.  
  
2.  Wählen Sie in Visual Studio im Menü **Projekt** die Option **Eigenschaften**aus.  
  
3.  Ändern Sie im Bereich **Eigenschaften** die Eigenschaft **DirectQueryMode**in einen der Werte, die DirectQuery-Verwendung unterstützen:  
  
    -   **InMemory mit DirectQuery**: Wenn Sie diese Option verwenden, wird das Modell bereitgestellt, doch Sie müssen den Cache verarbeiten, bevor Sie Abfragen des Modell ausführen können.  
  
    -   **DirectQuery mit InMemory**: Wenn Sie diese Option verwenden, ist der Cache zur Verwendung durch Clients verfügbar, wenn er bereits verarbeitet wurde. Wenn Sie das Modell mit dieser Einstellung bereitstellen und den Cache nicht verarbeiten, müssen einige Clients eine Fehlermeldung erhalten, wenn sie versuchen, eine Verbindung mit dem Modell herzustellen.  
  
    -   **Nur DirectQuery**: Wenn Sie diese Option verwenden, werden die Metadaten bereitgestellt, doch das Modell enthält keine Daten. Clients, die versuchen, mit dem Modus "Im Arbeitsspeicher" eine Verbindung herzustellen, erhalten eine Fehlermeldung wegen eines nicht vorhandenen Modells oder der fehlenden Verarbeitung.  
  
4.  Wenn Fehler vorhanden sind, öffnen Sie in Visual Studio die **Fehlerliste** , und beheben Sie alle Probleme, durch die verhindert werden würde, dass das Modell im DirectQuery-Modus bereitgestellt wird.  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>So überprüfen oder ändern Sie die bevorzugte Verbindungsmethode für ein DirectQuery-Modell  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]eine Verbindung mit der Instanz her, wo Sie das DirectQuery-Modell bereitgestellt haben.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Modelldatenbank, und wählen Sie **Eigenschaften**aus.  
  
3.  Ändern Sie im Bereich **Eigenschaften** die Eigenschaft **DirectQueryMode**in einen der folgenden Werte:  
  
    -   **Nur directquery**  
  
    -   **InMemory mit DirectQuery**  
  
    -   **Directquery mit inMemory**  
  
 Diese Eigenschaften sind mit den Eigenschaften identisch, die für das Projekt vor der Bereitstellung in Visual Studio festgelegt werden. Sie können den bevorzugten Verbindungsmodus für den DirectQuery-Modus jederzeit ändern, vorausgesetzt, dass Sie das Modell für die Unterstützung von DirectQuery-Verwendung konfiguriert haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Directquery-Modus &#40;tabellarischen SSAS-&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [Aktivieren des directquery-Entwurfs Modus &#40;tabellarischen SSAS-&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
