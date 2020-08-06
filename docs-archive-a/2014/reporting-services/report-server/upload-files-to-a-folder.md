---
title: Hochladen von Dateien in einen Ordner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87617615"
---
# <a name="upload-files-to-a-folder"></a>Hochladen von Dateien in einen Ordner
  Sie können Dateien vom Dateisystem hochladen und in einer Berichtsserver-Datenbank als verwaltete Elemente speichern. Vom Dateityp hängt es ab, was beim Hochladen einer Datei passiert.

-   Das Hochladen einer RDL-Datei entspricht dem Veröffentlichen eines Berichts.

-   Beim Hochladen anderer Dateien werden diese als einzelne binäre Objekte der Berichtsserver-Datenbank hinzugefügt. Diese Dateien werden auf einem Berichtsserver als Ressource veröffentlicht. Ressourcen können einen beliebigen Dateityp aufweisen. Falls die Dateierweiterung einem bekannten MIME-Typ entspricht, wird ein Symbol für diesen MIME-Typ zur Identifizierung des Ressourcentyps verwendet. Andernfalls wird ein allgemeines Dateisymbol zum Anzeigen einer Ressource verwendet.

> [!NOTE]
>  Sie können eine RDS-Datei (report data source, Berichtsdatenquelle) nicht hochladen, um eine freigegebene Datenquelle zu erstellen. Eine RDS-Datei wird nur im Berichts-Designer verwendet. Die Datei kann den Inhalt für ein freigegebenes Datenquellenelement, das Sie mithilfe des Berichts-Managers definieren und verwalten, nicht bereitstellen. Als Alternative zum Hochladen können Sie ein Skript schreiben, das eine freigegebene, auf einer RDS-Datei basierende Datenquelle erstellt.

 Die maximale Dateigröße für hochgeladene Elemente wird von [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]bestimmt. Standardmäßig beträgt die maximale Dateigröße 4 Megabyte (MB).

 Dateien, die Sie in eine Berichtsserver-Datenbank hochladen, werden in der Ordnerhierarchie anhand der folgenden Symbole dargestellt.

 ![Berichts Symbol](../media/hlp-16doc.gif "Berichtssymbol") (Berichts Symbol)

 ![Modell Symbol](../media/model-icon.gif "Modell (Symbol)") Berichts Modell (Symbol)

 Allgemeines ![Ressourcen Symbol (Allgemeines Ressourcen](../media/hlp-16file.gif "allgemeines Ressourcensymbol") Symbol)

 Beim Hochladen einer Datei wird diese stets im aktuell ausgewählten Ordner gespeichert. Sie können zu dem Ordner navigieren, in dem das Element zuerst gespeichert werden soll. Oder Sie laden eine Datei hoch und verschieben diese dann später an den endgültigen Speicherort.

 Laden Sie Dateien mit dem Berichts-Manager hoch. Ob Sie Dateien auf einen Berichtsserver hochladen können, hängt von den Tasks ab, die zu der Rollenzuweisung gehören. Falls Sie die Standardsicherheit verwenden, können lokale Administratoren Elemente zu einem Berichtsserver hinzufügen. Wenn Meine Berichte aktiviert ist, hat jeder Benutzer, der über einen Ordner Meine Berichte verfügt, die Berechtigung, Elemente in diesen Ordner hochzuladen. Wenn Sie benutzerdefinierte Rollenzuweisungen verwenden, muss die Rollenzuweisung Aufgaben für die Ordnerverwaltung enthalten.

|Gehen Sie dazu folgendermaßen vor:|Einzubindende Aufgaben|
|----------------|-------------------------|
|Eine RDL-Datei in einen Ordner hochladen|Berichte verwalten|
|Eine beliebige Datei als binäres Objekt hochladen|Ressourcen verwalten|
|Die Inhalte eines Ordners anzeigen|Ressourcen anzeigen, Berichte anzeigen|

## <a name="see-also"></a>Weitere Informationen
 [Berichts-Manager &#40;SSRS-&#41; im einheitlichen Modus].. /Report-Manager-SSRS-Native-Mode.MD) [Erteilen von Berechtigungen für Berichts Server](../security/granting-permissions-on-a-native-mode-report-server.md) [Aufgaben und Berechtigungen](../security/tasks-and-permissions.md) im einheitlichen Modus [&#40;Berichts-Manager eine Datei oder einen Bericht&#41;](../reports/upload-a-file-or-report-report-manager.md)


