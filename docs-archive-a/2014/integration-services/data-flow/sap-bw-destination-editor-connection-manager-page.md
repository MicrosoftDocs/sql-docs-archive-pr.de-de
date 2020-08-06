---
title: Ziel-Editor für SAP BW (Seite „Verbindungs-Manager“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87695910"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a>Ziel-Editor für SAP BW (Seite Verbindungs-Manager)
  Verwenden Sie die Seite **Verbindungs-Manager** im **Ziel-Editor für SAP BW** , um den SAP BW-Verbindungs-Manager auszuwählen, der vom SAP BW-Ziel verwendet wird. Auf dieser Seite wählen Sie außerdem die Parameter aus, die zum Laden der Daten in das SAP NetWeaver BW-System verwendet werden.  
  
 Weitere Informationen zum SAP BW-Ziel von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Ziel](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie die Seite "Verbindungs-Manager"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
## <a name="options"></a>Tastatur  
  
> [!NOTE]  
>  Wenn Sie nicht alle Werte kennen, die zur Konfiguration des Ziels erforderlich sind, müssen Sie ggf. Ihren SAP-Administrator um Unterstützung bitten.  
  
 **SAP BW-Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder erstellen Sie eine neue Verbindung, indem Sie auf **Neu**klicken.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **SAP BW-Verbindungs-Manager** einen neuen Verbindungs-Manager.  
  
 **Testladevorgang**  
 Führen Sie einen Testladevorgang aus, in dem die ausgewählten Einstellungen verwendet und 0 Zeilen geladen werden.  
  
### <a name="infopackageinfosource-options"></a>Optionen für "InfoPackage/InfoSource"  
 Diese Werte müssen nicht im Voraus bekannt sein und eingegeben werden. Verwenden Sie die Schaltfläche **Suchen** , um das entsprechende InfoPackage zu suchen und auszuwählen. Nachdem Sie ein InfoPackage ausgewählt haben, werden die entsprechenden Werte für diese Optionen von der Komponente eingegeben.  
  
 **InfoPackage**  
 Geben Sie den Namen für das InfoPackage ein.  
  
 **InfoSource**  
 Geben Sie den Namen für die InfoSource ein.  
  
 **Typ**  
 Geben Sie das Einzelzeichen ein, durch das der InfoSource-Typ identifiziert wird. In der folgenden Tabelle sind die zulässigen Einzelzeichenwerte aufgeführt.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**D**|Transaktionsdaten|  
|**M**|Masterdaten|  
|**T**|Texte|  
|**H**|Hierarchiedaten|  
  
 **Logisches System**  
 Geben Sie den Namen des logischen Systems ein, das dem InfoPackage zugeordnet ist.  
  
 **Suchen**  
 Suchen Sie das InfoPackage mithilfe des Dialogfelds **InfoPackage suchen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up InfoPackage](look-up-infopackage.md).  
  
### <a name="rfc-destination-options"></a>Optionen für "RFC-Ziel"  
 Diese Werte müssen nicht im Voraus bekannt sein und eingegeben werden. Verwenden Sie die Schaltfläche **Suchen** , um das entsprechende RFC-Ziel zu suchen und auszuwählen. Nachdem Sie ein RFC-Ziel ausgewählt haben, werden die entsprechenden Werte für diese Optionen von der Komponente eingegeben.  
  
 **Gatewayhost**  
 Geben Sie den Servernamen oder die IP-Adresse des Gatewayhosts ein. Normalerweise ist der Name oder die IP-Adresse identisch mit dem SAP-Anwendungsserver.  
  
 **Gatewaydienst**  
 Geben Sie den Namen des Gatewaydiensts im Format `sapgwNN` ein, wobei `NN` der Systemnummer entspricht.  
  
 **Programm-ID**  
 Geben Sie die Programm-ID ein, die dem RFC-Ziel zugeordnet ist.  
  
 **Suchen**  
 Suchen Sie das RFC-Ziel mithilfe des Dialogfelds **RFC-Ziel suchen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up RFC Destination](look-up-rfc-destination.md).  
  
### <a name="create-sap-bw-objects-options"></a>Optionen für "SAP BW-Objekte erstellen"  
 **Objekttyp auswählen**  
 Wählen Sie den Typ des SAP NetWeaver BW-Objekts aus, das Sie erstellen möchten. Wählen Sie einen der folgenden Typen aus:  
  
-   InfoObject  
  
-   InfoCube  
  
-   InfoSource  
  
-   InfoPackage  
  
 **Erstellen**  
 Erstellen Sie den ausgewählten SAP NetWeaver BW-Objekttyp.  
  
|Objekttyp|Ergebnis|  
|-----------------|------------|  
|**InfoObject**|Erstellen Sie ein neues InfoObject mithilfe des Dialogfelds **Neues InfoObject erstellen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Create New InfoObject](create-new-infoobject.md).|  
|**InfoCube**|Erstellen Sie einen neuen InfoCube mithilfe des Dialogfelds **InfoCube für Transaktionsdaten erstellen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).|  
|**InfoSource**|Erstellen Sie eine neue InfoSource, indem Sie erst das Dialogfeld **InfoSource erstellen** und dann das Dialogfeld **InfoSource für Transaktionsdaten erstellen** oder **InfoSource für Masterdaten erstellen** verwenden. Weitere Informationen zu diesen Dialogfeldern finden Sie unter [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) und [Create InfoSource for Master Data](create-infosource-for-master-data.md).|  
|**InfoPackage**|Erstellen Sie ein neues InfoPackage mithilfe des Dialogfelds **InfoPackage erstellen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Create InfoPackage](create-infopackage.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziel-Editor für SAP BW &#40;Seite „Zuordnungen“&#41;](sap-bw-destination-editor-mappings-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Fehlerausgabe“&#41;](sap-bw-destination-editor-error-output-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite „Erweitert“&#41;](sap-bw-destination-editor-advanced-page.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
