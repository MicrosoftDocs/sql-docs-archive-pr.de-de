---
title: Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1dbd9e44518b6e849a06a76e21fc605172fd2ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87696049"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Max. Bereich für Volltextdurchforstung (Serverkonfigurationsoption)
  Verwenden Sie die Option **max full-text crawl range** , um die CPU-Auslastung zu optimieren. Hierdurch wird die Durchforstungsleistung während eines vollständigen Durchforstungsvorgangs verbessert. Mithilfe dieser Option können Sie die Anzahl von Partitionen angeben, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während eines vollständigen Indexdurchforstungsvorgangs verwenden sollte. Wenn z. B. viele CPUs vorhanden sind und ihre Auslastung nicht optimal ist, können Sie den maximalen Wert dieser Option erhöhen. Zusätzlich zu dieser Option verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Reihe anderer Faktoren, wie z. B. die Anzahl von Zeilen in der Tabelle und die Anzahl von CPUs, um die tatsächliche Anzahl von verwendeten Partitionen zu ermitteln.  
  
 Der Standardwert dieser Option ist 4, der Mindestwert 1 und der maximale Wert 256. Änderungen an dieser Option beeinflussen nur nachfolgende Crawls. Auf in Verarbeitung befindliche Durchforstungsvorgänge hat eine Änderung dieser Optionseinstellung keine Auswirkungen.  
  
 Bei der Option **max full-text crawl range** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **max full-text crawl range** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
