---
title: Konfigurieren der Eigenschaften eines Datensammlers | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05172c2c831ec649269512a625be069cdc67047a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718250"
---
# <a name="configure-properties-of-a-data-collector"></a>Konfigurieren der Eigenschaften eines Datensammlers
  In diesem Thema wird erläutert, wie Sie die Eigenschaften eines Datensammlers konfigurieren.  
  
## <a name="data-collection-properties-general-tab"></a>Datensammlungseigenschaften (Registerkarte 'Allgemein')  
 Verwenden Sie diese Seite, um Einstellungen für das Verwaltungs-Data Warehouse zu konfigurieren und den Speicherort für aufgelistete Daten anzugeben, bevor diese in das Data Warehouse hochgeladen werden.  
  
 **Datensammlung aktivieren**  
 Aktivieren Sie dieses Kontrollkästchen, um die Datensammlung zu aktivieren. Dies hat die gleichen Auswirkungen wie das Ausführen der gespeicherten Prozedur sp_syscollector_enable_collector stored procedure. Wenn Sie dieses Kontrollkästchen deaktivieren, ist die Datensammlung deaktiviert. Dies hat die gleichen Auswirkungen wie das Ausführen der gespeicherten Prozedur sp_syscollector_disable_collector.  
  
 **Server**  
 Zeigt den Namen des Servers an, der als Host für das Verwaltungs-Data Warehouse fungiert.  
  
 **Datenbankname**  
 Zeigt den Namen der relationalen Datenbank an, die für das Verwaltungs-Data Warehouse verwendet wird.  
  
 **Verbindung testen**  
 Testen Sie die Verbindung mit dem angegebenen **Server** mithilfe der Informationen, die beim Konfigurieren der Datensammlung angegeben werden.  
  
 **Cacheverzeichnis**  
 Gibt das Verzeichnis an, in dem die aufgelisteten Daten auf dem die Daten auflistenden System gespeichert werden, bevor sie in das Verwaltungs-Data Warehouse hochgeladen werden. Wenn kein **Cacheverzeichnis** angegeben ist, sucht der Datensammler nach den Umgebungsvariablen %TEMP% und %TMP% und verwendet einen dieser Speicherorte als Standardspeicherort für die temporäre Speicherung. Wenn diese Umgebungsvariablen nicht konfiguriert sind, tritt ein Fehler auf, und Sie werden aufgefordert, ein Cacheverzeichnis zu erstellen.  
  
## <a name="data-collection-properties-advanced-tab"></a>Datensammlungseigenschaften (Registerkarte 'Erweitert')  
 Verwenden Sie diese Seite, um die Einstellungen für Wiederholungsversuche für die Verbindung mit dem Verwaltungs-Data Warehouse zu konfigurieren.  
  
 **Anzahl der Wiederholungsversuche im Falle eines Fehlers beim Hochladen**  
 Gibt an, wie häufig im Fall eines Fehlers erneut versucht wird, Daten in das Verwaltungs-Data Warehouse hochzuladen. Der Standardwert ist 1.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Datensammlungen](data-collection.md)   
 [Konfigurieren des Verwaltungs-Data Warehouses &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
