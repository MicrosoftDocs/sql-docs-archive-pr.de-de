---
title: Datenbankeigenschaften (Seite Änderungsnachverfolgung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4107f81ef4cdf19df60d4a70d8e79007f2c9270c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718241"
---
# <a name="database-properties-changetracking-page"></a>Datenbankeigenschaften (Seite Änderungsnachverfolgung)
  Mithilfe dieser Seite können Sie die Einstellungen der Änderungsnachverfolgung für die ausgewählte Datenbank anzeigen und ändern. Informationen zu den auf dieser Seite verfügbaren Optionen finden Sie unter [Aktivieren und Deaktivieren der Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 **Änderungsnachverfolgung**  
 Mithilfe dieser Option können Sie die Änderungsnachverfolgung für die Datenbank aktivieren und deaktivieren.  
  
 Um die Änderungsnachverfolgung aktivieren zu können, müssen Sie über die Berechtigung zur Änderung der Datenbank verfügen.  
  
 Durch Festlegen des Werts auf **True** wird eine Datenbankoption festgelegt, die eine Aktivierung der Änderungsnachverfolgung für einzelne Tabellen ermöglicht.  
  
 Sie können die Änderungsnachverfolgung mithilfe von [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)konfigurieren.  
  
 **Aufbewahrungszeitraum**  
 Gibt die Mindestdauer für die Beibehaltung von Änderungsnachverfolgungsinformationen in der Datenbank an. Die Daten werden nur dann entfernt, wenn der Wert für **Automatisches Cleanup**auf **True**festgelegt ist.  
  
 Der Standardwert ist 2.  
  
 **Einheiten für die Beibehaltungsdauer**  
 Gibt die Einheiten für den Beibehaltungsdauerwert an. Sie können **Tage**, **Stunden**oder **Minuten**auswählen. Der Standardwert ist **Tage**.  
  
 Die Mindestbeibehaltungsdauer ist 1 Minute. Es gibt keine maximale Beibehaltungsdauer.  
  
 **Automatisches Cleanup**  
 Gibt an, ob Änderungsnachverfolgungsinformationen nach der angegebenen Beibehaltungsdauer automatisch entfernt werden.  
  
 Durch Aktivieren von **Automatisches Cleanup** wird eine vorhandene benutzerdefinierte Beibehaltungsdauer auf die Standardbeibehaltungsdauer von 2 Tagen zurückgesetzt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
