---
title: srv_paramtype (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4b4006f8214670e3bd2bddfbaabe917fb9d778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87615392"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a>srv_paramtype (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt den Datentyp des Aufrufparameters für eine remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Anzahl der Parameter an. Der erste Parameter ist 1.  
  
## <a name="returns"></a>Gibt zurück  
 Ein Tokenwert für den Datentyp des Parameters. Informationen zu Datentypen finden Sie unter [Datentypen (API für erweiterte gespeicherte Prozeduren)](data-types-extended-stored-procedure-api.md). Wenn es keinen *n*-ten Parameter oder keine remote gespeicherte Prozedur gibt, wird –1 zurückgegeben.  
  
 Diese Funktion gibt die folgenden Werte zurück, wenn der-Parameter einem der- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Datentypen entspricht.  
  
|Neue Datentypen|Rückgabewert|  
|--------------------|------------------|  
|`BITN`|SRVBIT|  
|`BIGVARCHAR`|VARCHAR|  
|`BIGCHAR`|CHAR|  
|`BIGBINARY`|BINARY|  
|`BIGVARBINARY`|VARBINARY|  
|`NCHAR`|CHAR|  
|`NVARCHAR`|VARCHAR|  
|`NTEXT`|-1|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC Handler wird immer noch aufgerufen, wird jedoch so angezeigt, als ob keine Parameter vorhanden wären und **srv_rpcparams** 0 zurückgibt.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_paraminfo &#40;API für erweiterte gespeicherte Prozeduren&#41;](srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams (API für erweiterte gespeicherte Prozeduren)](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
