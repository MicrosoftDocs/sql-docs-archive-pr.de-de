---
title: Dialogfeld „Richtlinien importieren“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609183"
---
# <a name="import-policies-dialog-box"></a>Dialogfeld 'Richtlinien importieren'
  Mithilfe dieses Dialogfelds können Sie ein oder mehrere Richtlinien (und deren referenzierte Bedingung), die als XML-Dateien gespeichert sind, in die aktuelle [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz importieren.  
  
## <a name="options"></a>Tastatur  
 **Zu importierende Dateien**  
 Um eine Richtlinie aus einer XML-Datei zu importieren, geben Sie den Pfad und den Namen der Datei ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen ( **...** ).  
  
 **Duplikate mit importierten Elementen ersetzen**  
 Wählen Sie diese Option aus, um eine vorhandene Richtlinie oder Bedingung mit demselben Namen zu überschreiben, wenn diese bereits in dieser [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz vorhanden ist. Eine Bedingung mit einer abhängigen Richtlinie kann nur überschrieben werden, wenn die abhängige Richtlinie ebenfalls überschrieben wird. Wenn diese Option nicht aktiviert ist, verursacht eine vorhandene Bedingung, die denselben Bedingungsausdruck verwendet, keinen Fehler.  
  
 **Richtlinienstatus**  
 Wählen Sie für die importierte Richtlinie den gewünschten Status aus:  
  
-   **Richtlinienstatus beim Import beibehalten**  
  
-   **Alle Richtlinien beim Import aktivieren**  
  
-   **Alle Richtlinien beim Import deaktivieren**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md)   
 [Importieren einer Richtlinie der richtlinienbasierten Verwaltung](import-a-policy-based-management-policy.md)   
 [Exportieren einer Richtlinie der richtlinienbasierten Verwaltung](export-a-policy-based-management-policy.md)  
  
  
