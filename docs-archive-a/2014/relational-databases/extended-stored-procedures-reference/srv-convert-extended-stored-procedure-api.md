---
title: srv_convert (API für die erweiterte gespeicherte Prozedur) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622111"
---
# <a name="srv_convert-extended-stored-procedure-api"></a>srv_convert (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ändert Daten von einem Datentyp in einen anderen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Die Struktur enthält alle Kontrollinformationen, mit der die API für erweiterte gespeicherte Prozeduren Kommunikationen und Daten zwischen der Anwendung und dem Client verwaltet. Wenn das *srvproc*-Handle zur Verfügung gestellt wird, wird es an die Fehlerhandlerfunktion der API für erweiterte gespeicherte Prozeduren übergeben, sobald ein Fehler auftritt.  
  
 *srctype*  
 Gibt den Datentyp der zu konvertierenden Daten an. Dieser Parameter kann ein beliebiger Datentyp der API für erweiterte gespeicherte Prozeduren sein.  
  
 *src*  
 Ist ein Zeiger auf die zu konvertierenden Daten. Dieser Parameter kann ein beliebiger Datentyp der API für erweiterte gespeicherte Prozeduren sein.  
  
 *srclen*  
 Gibt die Länge der zu konvertierenden Daten in Byte an. Wenn *srclen* 0 ist, fügt **srv_convert** einen NULL-Wert in die Zielvariable ein. Wenn nicht 0, wird dieser Parameter für Datentypen fester Länge ignoriert. In diesem Fall wird für die Quelldaten der Wert NULL angenommen. Für Daten des SRVCHAR-Datentyps gibt eine Länge von -1 an, dass die Zeichenfolge NULL-terminiert ist.  
  
 *desttype*  
 Gibt den Datentyp an, in den die Quelle konvertiert werden soll. Dieser Parameter kann ein beliebiger Datentyp der API für erweiterte gespeicherte Prozeduren sein.  
  
 *dest*  
 Ist ein Zeiger auf die Zielvariable, die die konvertierten Daten empfängt. Wenn dieser Zeiger NULL ist, ruft **srv_convert** den ggf. vom Benutzer bereitgestellten Fehlerhandler auf und gibt –1 zurück.  
  
 Wenn *desttype* den Wert SRVDECIMAL oder SRVNUMERIC aufweist, muss der *dest*-Parameter ein Zeiger auf eine DBNUMERIC- oder DBDECIMAL-Struktur sein, und die Felder für Genauigkeit und Dezimalstellen müssen bereits auf die gewünschten Werte festgelegt worden sein. Mit DEFAULTPRECISION können Sie eine Standardgenauigkeit angeben und mit DEFAULTSCALE einen Standardwert für die Dezimalstellen.  
  
 *destlen*  
 Gibt die Länge der Zielvariable in Byte an. Dieser Parameter wird für Datentypen fester Länge ignoriert. Für eine Zielvariable des Typs SRVCHAR muss der Wert von *destlen* der Gesamtlänge des Zielpufferspeichers entsprechen. Eine Länge von -1 für eine Zielvariable des Typs SRVCHAR oder SRVBINARY gibt an, dass genügend Speicher verfügbar ist. Für eine Zielvariable des Typs *srvchar* führt eine Länge von –1 zur NULL-Terminierung der Zeichenfolge.  
  
## <a name="returns"></a>Gibt zurück  
 Die Länge der konvertierten Daten (in Byte) bei erfolgreicher Konvertierung des Datentyps. Wenn **srv_convert** eine Konvertierungsanforderung erhält, die nicht unterstützt wird, wird – sofern vorhanden – der vom Entwickler bereitgestellte Fehlerhandler aufgerufen, eine globale Fehlernummer festgelegt und der Wert –1 zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **srv_willconvert**-Funktion bestimmt, ob eine bestimmte Konvertierung zulässig ist.  
  
 Das Konvertieren von SRVFLT4 oder SRVFLT8 in die ungefähren numerischen Datentypen kann zu einem Genauigkeitsverlust führen. Ein Genauigkeitsverlust kann auch durch Konvertieren der ungefähren numerischen Datentypen SRVFLT4 oder SRVFLT8 in SRVCHAR oder SRVTEXT auftreten.  
  
 Das Konvertieren in SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL oder SRVNUMERIC kann zu einem Überlauf führen, wenn die Zahl größer ist als der Maximalwert des Ziels, oder zu einem Unterlauf, wenn die Zahl kleiner ist als der Mindestwert des Ziels. Wenn beim Konvertieren von SRVCHAR oder SRVTEXT ein Überlauf auftritt, enthält das erste Zeichen des resultierenden Werts einen Stern (*) als Hinweis auf den Fehler.  
  
 Wenn Sie SRVCHAR in SRVBINARY konvertieren, interpretiert **srv_convert** SRVCHAR als eine Hexadezimalzeichenfolge, unabhängig davon, ob die Zeichenfolge eine führende 0 enthält. Beim Konvertieren von SRVBINARY in SRVCHAR erstellt **srv_convert** eine Hexadezimalzeichenfolge ohne eine führende 0. In allen anderen Fällen ist eine Konvertierung in oder aus dem SRVBINARY-Datentyp eine exakte Bitkopie.  
  
 In bestimmten Fällen kann es nützlich sein, einen Datentyp in sich selbst zu konvertieren. Durch Konvertieren von SRVCHAR in SRVCHAR mit einem Wert für *destlen* von –1 wird einer Zeichenfolge beispielsweise ein NULL-Terminator hinzugefügt.  
  
 Eine Beschreibung von Datentypen und Datentypkonvertierungen der API für erweiterte gespeicherte Prozeduren finden Sie unter [Data Types (Extended Stored Procedure API) (Datentypen (API für erweiterte gespeicherte Prozeduren))](data-types-extended-stored-procedure-api.md).  
  
 Die **srv_convert**-Funktion kann aus verschiedenen Gründen fehlschlagen:  
  
-   Die angeforderte Konvertierung ist nicht verfügbar.  
  
-   Die Konvertierung hat zu Abschneidung, Überlauf oder Genauigkeitsverlust in der Zielvariablen geführt.  
  
-   Beim Konvertieren einer Zeichenfolge in einen numerischen Datentyp ist ein Syntaxfehler aufgetreten.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_setutype &#40;API für erweiterte gespeicherte Prozeduren&#41;](srv-setutype-extended-stored-procedure-api.md)   
 [srv_willconvert (API für erweiterte gespeicherte Prozeduren)](srv-willconvert-extended-stored-procedure-api.md)  
  
  
