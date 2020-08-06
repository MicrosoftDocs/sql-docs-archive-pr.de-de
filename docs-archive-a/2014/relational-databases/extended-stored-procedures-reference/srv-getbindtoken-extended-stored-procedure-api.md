---
title: srv_getbindtoken (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_getbindtoken
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_getbindtoken
ms.assetid: c947d011-08ac-4fb8-b925-3da6e0999277
author: rothja
ms.author: jroth
ms.openlocfilehash: d42f95c8a7df87f20ebaa30501b96b5f2a00815a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622109"
---
# <a name="srv_getbindtoken-extended-stored-procedure-api"></a>srv_getbindtoken (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Enthält ein Bindungstoken der Transaktion in der aktuellen Clientsitzung, mit dem die erweiterte gespeicherte Prozedur aufgerufen wird.  
  
 Die erweiterte gespeicherte Prozedur kann dann mithilfe von **sp_bindsession** eine neue Sitzung binden, die sie mit demselben Server für die vorhandene Transaktion erstellt. So kann die neue Sitzung denselben Transaktionssperrbereich zusammen mit der Clientsitzung nutzen, die die erweiterte gespeicherte Prozedur aufgerufen hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_getbindtoken (  
SRV_PROC*  
srvproc  
,  
char*  
bindtoken  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält alle Kontrollinformationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren Kommunikationen und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *bindtoken*  
 Ein Zeiger auf einen Puffer, in dem das Bindungstoken kopiert wird. Das Bindungstoken wird als eine Zeichenfolge dargestellt, die auf NULL endet. Der Puffer, den Sie angeben, muss mindestens 255 Bytes lang sein.  
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
  
### <a name="to-bind-an-extended-stored-procedure-session-to-the-client-session-that-called-it-so-they-share-the-same-transaction-lock-space"></a>So binden Sie eine Sitzung der erweiterten gespeicherten Prozedur an die Clientsitzung, die die Prozedur aufgerufen hat, sodass beide Sitzungen denselben Transaktionssperrbereich nutzen  
  
1.  Die erweiterte gespeicherte Prozedur ruft **svr_getbindtoken** auf, um das Bindungstoken für die aktuelle Transaktion in der Sitzung abzurufen. Das Token wird im gegebenen *bindtoken*-Parameter zurückgegeben.  
  
2.  Die erweiterte gespeicherte Prozedur öffnet auf demselben Server neue Sitzungen. Innerhalb dieser Sitzung verwendet die erweiterte gespeicherte Prozedur das Bindungstoken mit **sp_bindsession**, um die neue Sitzung an dieselbe Transaktion zu binden. Die erweiterte gespeicherte Prozedur kann mehrere Sitzungen erstellen und alle Sitzungen an dieselbe Transaktion binden.  
  
3.  Die Bindung einer gebundenen Sitzung wird aufgehoben, wenn die externe gespeicherte Prozedur eine leere Zeichenfolge zurückgibt oder wenn **sp_bindsession** mit einer leeren Zeichenfolge aufgerufen wird.  
  
    > [!NOTE]  
    >  Es kann immer jeweils nur eine gebundene Sitzung Zugriff auf eine gemeinsam genutzte Verbindung haben. Wenn eine Sitzung derzeit eine Anweisung auf dem Server ausführt oder auf Ergebnisse vom Server wartet, können andere Sitzungen, die dieselbe gebundene Verbindung nutzen, erst dann auf den Server zugreifen, wenn die aktuelle Sitzung die aktuelle Anweisung ausgeführt hat. Wenn durch eine andere Sitzung auf die Verbindung zugegriffen wird, solange der Server ausgelastet ist, wird an die den Konflikt verursachende Sitzung die Fehlermeldung zurückgegeben, dass die Verbindung verwendet wird und der Zugriffsversuch der Sitzung später wiederholt werden kann.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_bindsession (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql)   
 [sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)  
  
  
