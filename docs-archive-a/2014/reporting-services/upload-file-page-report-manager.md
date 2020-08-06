---
title: Datei hochladen (Seite) (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7bb3166f-9374-4449-b66a-ffb77298507d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de03c6c6bd03cbe083d5e1edfd320264d2cc3bde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719405"
---
# <a name="upload-file-page-report-manager"></a>Datei hochladen (Seite) (Berichts-Manager)
  Mithilfe der Seite Datei hochladen können Sie eine Datei aus dem Dateisystem in der Berichtsserver-Datenbank veröffentlichen. Hochgeladene Dateien werden als Elemente in der Ordnerhierarchie des Berichtsservers dargestellt.  
  
-   Hochgeladene RDL-Dateien werden als Berichte auf einem Berichtsserver veröffentlicht.  
  
-   Hochgeladene SMDL-Dateien werden als Berichtsmodelle veröffentlicht, wenn sie Informationen zur Datenquellensicht enthalten. Wenn ein Verweis auf eine Datenquellensicht fehlt, tritt beim Hochladen ein Fehler auf. Datenquellen Sicht-Informationen fehlen möglicherweise, wenn Sie eine SMDL-Datei aus einem [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Berichts Modellprojekt hochladen. In Berichtsmodellprojekten werden die Informationen zu Datenquellensichten in einer separaten Datei gespeichert und nicht in der SMDL-Datei selbst.  
  
     Modelldateien, die Informationen zu Datenquellensichten enthalten (und daher erfolgreich hochgeladen werden können), sind jene, die zuvor auf einen Berichtsserver veröffentlicht und dann vom Server in eine Datei im Dateisystem gespeichert wurden. Wenn Sie die Seite mit den allgemeinen Eigenschaften eines Modells öffnen und auf **Bearbeiten** klicken, um das Modell zu öffnen, können Sie es in einer Datei speichern und dann als neues Modell auf den Berichtsserver hochladen. Die SMDL-Datei, die Sie hochladen, enthält alle Informationen, die zum Veröffentlichen des Modell notwendig sind.  
  
-   Alle anderen Dateitypen, die Sie hochladen, werden als Ressourcen gespeichert. Dies schließt RDS-Dateien ein, die Verbindungsinformationen für Berichtsdatenquellen enthalten. Durch das Hochladen einer RDS-Datei wird kein freigegebenes Datenquellenelement auf dem Berichtsserver erzeugt.  
  
 Wenn Sie ein Element hochladen, wird es in den aktuellen Ordner eingefügt. Nach Abschluss des Uploadvorgangs können Sie das Element an einen anderen Speicherort verschieben.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-upload-file-page"></a>So öffnen Sie die Seite "Datei hochladen"  
  
1.  Öffnen Sie den Berichts-Manager, und navigieren Sie zu dem Ordner, in den Sie eine Datei hochladen möchten.  
  
2.  Klicken Sie auf der Symbolleiste auf **Datei hochladen**.  
  
## <a name="options"></a>Tastatur  
 **Hochzuladende Datei**  
 Zeigt den vollqualifizierten Pfad der Datei an, die Sie aus dem Dateisystem kopieren.  
  
 **Durchsuchen**  
 Klicken Sie auf diese Schaltfläche, um eine Datei aus dem Dateisystem auszuwählen.  
  
 **Name**  
 Geben Sie den Namen der Datei ein, der im Namespace des Berichtsservers angezeigt wird. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und bestimmte Sonderzeichen enthalten. Folgende Zeichen können nicht beim Angeben eines Namens verwendet werden: ; ? : \@ & = +, $ * \< > | "oder/, wenn ein Elementname angegeben wird.  
  
 **Vorhandenes Element überschreiben**  
 Aktivieren Sie dieses Kontrollkästchen, wenn Sie ein vorhandenes Element durch eine neuere Version ersetzen möchten. Um eine vorhandene Version zu überschreiben, muss der Name des neuen Elements genau mit dem Namen des vorhandenen Elements übereinstimmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Die Inhaltsseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Berichts-Manager F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Hochladen von Dateien in einen Ordner](report-server/upload-files-to-a-folder.md)  
  
  
