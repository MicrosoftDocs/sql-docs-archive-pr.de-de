---
title: Protokolldateien für Standardablaufverfolgung deaktiviert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fed8fb006427b4dda9d99c57cbabca8538efcad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87616005"
---
# <a name="default-trace-log-files-disabled"></a>Protokolldateien für Standardablaufverfolgung deaktiviert
  Diese Regel überprüft den Wert der Option Standardablaufverfolgung aktiviert der gespeicherten Prozedur sp_configure, um festzustellen, ob die Standardablaufverfolgung auf ON (1) oder OFF (0) festgelegt ist. Wenn diese Option aktiviert ist, stellt die Standardablaufverfolgung Informationen über Konfigurations- und DDL-Änderungen an [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]bereit. In manchen Fällen sind diese Informationen für Kunden sowie den Kundendienst- und Support von [!INCLUDE[msCoName](../../includes/msconame-md.md)] bei der Behebung von Fehlern bei [!INCLUDE[ssDE](../../includes/ssde-md.md)]hilfreich.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Aktivieren Sie die Ablaufverfolgung mit der gespeicherten Prozedur sp_configure, indem Sie den Wert von "Standardablaufverfolgung aktiviert" auf 1 festlegen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
