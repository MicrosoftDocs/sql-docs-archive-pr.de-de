---
title: CLR-fähig (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87608852"
---
# <a name="clr-enabled-server-configuration-option"></a>CLR-fähig (Serverkonfigurationsoption)
  Mithilfe der Option CLR-fähig können Sie angeben, ob Benutzerassemblys von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden dürfen. Von der Option "CLR-fähig" werden folgende Werte bereitgestellt.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0|Das Ausführen von Assemblys für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist unzulässig.|  
|1|Das Ausführen von Assemblys für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist zulässig.|  
  
 WOW64-Server müssen neu gestartet werden, bevor die Änderungen an dieser Einstellung wirksam werden. Ein Neustart ist für andere Servertypen nicht erforderlich.  
  
> [!NOTE]  
>  Wenn RECONFIGURE ausgeführt und der Ausführungswert der Option "CLR-fähig" von 1 in 0 geändert wird, werden alle Anwendungsdomänen mit Benutzerassemblys sofort entladen.  
  
> [!NOTE]  
>  CLR (Common Language Runtime) wird beim Lightweightpooling nicht unterstützt. Deaktivieren Sie eine der beiden Optionen "CLR-fähig" oder "Lightweightpooling". Zu den Funktionen, die auf CLR basieren und nicht ordnungsgemäß im Fibermodus arbeiten, gehören der `hierarchy`-Datentyp, die Replikation und die richtlinienbasierte Verwaltung.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird zunächst die aktuelle Einstellung der Option CLR-fähig angezeigt und die Option dann aktiviert, indem der Optionswert auf 1 festgelegt wird. Wenn Sie die Option deaktivieren möchten, legen Sie den Wert auf 0 fest.  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lightweightpooling (Serverkonfigurationsoption)](lightweight-pooling-server-configuration-option.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Lightweightpooling (Serverkonfigurationsoption)](lightweight-pooling-server-configuration-option.md)  
  
  
