---
title: Datenquellen Namen und 64-Bit-Betriebssysteme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615358"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Datenquellennamen und 64-Bit-Betriebssysteme
  Wenn Sie eine Anwendung als 32-Bit-Anwendung entwickeln und unter einem 64-Bit-Betriebssystem ausführen möchten, müssen Sie die ODBC-Datenquelle mit dem ODBC-Administrator in %windir%\SysWOW64\odbcad32.exe erstellen.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein 64-Bit-Windows-Betriebssystem verfügt über zwei odbcad32.exe-Dateien:  
  
-   %SystemRoot%\system32\odbcad32.exe wird verwendet, um Datenquellennamen für 64-Bit-Anwendungen zu erstellen und zu warten.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe wird verwendet, um Datenquellennamen für 32-Bit-Anwendungen, einschließlich 32-Bit-Anwendungen, die auf 64-Bit-Betriebssystemen ausgeführt werden, zu erstellen und zu warten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
