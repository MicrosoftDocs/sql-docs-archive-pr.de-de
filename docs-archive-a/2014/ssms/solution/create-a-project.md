---
title: Erstellen eines Projekts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
author: stevestein
ms.author: sstein
ms.openlocfilehash: 269feee7225ceb09b1c2ed86419b19ec4001c1f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619521"
---
# <a name="create-a-project"></a>Erstellen eines Projekts
  Sie können innerhalb einer vorhandenen Projektmappe ein oder mehrere Projekte erstellen.  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a>So erstellen Sie ein neues Projekt erstellen und fügen es zu einer Projektmappe hinzu  
  
1.  Wählen Sie die Projektmappe im Projektmappen-Explorer aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie auf **Neues Projekt**.  
  
3.  Klicken Sie im Dialogfeld  **Neues Projekt** auf einen Projekttyp.  
  
     **Vorlagen**  
     Wählen Sie im Feld **Vorlagen** eine Vorlage aus. Neben dem Feld **Vorlagen** wird eine kurze Beschreibung der ausgewählten Projektvorlage angezeigt.  
  
     **Name**  
     Geben Sie den Namen des zu erstellenden Skriptprojekts ein. Ein Ordner mit demselben Namen wie das Projekt wird ebenfalls an dem Ort erstellt, der im Feld **Speicherort** angezeigt wird. Für einige Projekte erstellt [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Quell- und andere unterstützende Dateien, die dem neuen Projektordner hinzugefügt werden.  
  
    > [!NOTE]  
    >  Bei einigen Projekttypen ist das Textfeld **Name** nicht verfügbar, weil der Name durch die Angabe des Speicherorts festgelegt wird. Webanwendungen und Webdienste befinden sich beispielsweise auf einem Webserver und leiten ihren Namen aus dem virtuellen Verzeichnis ab, das auf diesem Server angegeben wurde.  
  
     Folgende Zeichen dürfen nicht in den Namen verwendet werden:  
  
    -   Nummernzeichen (#)  
  
    -   Prozent (%)  
  
    -   Kaufmännisches Und-Zeichen (&)  
  
    -   Sternchen (*)  
  
    -   Senkrechter Strich (|)  
  
    -   Umgekehrter Schrägstrich (\\)  
  
    -   Doppelpunkt (:)  
  
    -   Anführungszeichen (")  
  
    -   Kleiner als (\<)  
  
    -   Größer als (>)  
  
    -   Fragezeichen (?)  
  
    -   Schrägstrich (/)  
  
    -   Führende oder nachfolgende Leerzeichen (' ')  
  
    -   Namen, die für Microsoft Windows oder MS-DOS reserviert sind (z. B. „nul“, „aux“, „con“, „com1“, „lpt1“ usw.)  
  
     **Location**  
     Geben Sie hier den Speicherort ein, an dem das Projekt erstellt werden soll, oder wählen Sie einen aus der Liste.  
  
     **Durchsuchen**  
     Zeigt das Dialogfeld **Projektspeicherort** an, mit dem Sie zu einem neuen Verzeichnis navigieren können, in dem das Projekt gespeichert werden soll.  
  
     **Lösung**  
     Wählen Sie **Neue Projektmappe erstellen** aus, um eine Projektmappe im Projektmappen-Explorer zu erstellen. Wählen Sie **Zu Projektmappe hinzufügen** , um das neue Projekt zur aktuell geöffneten Projektmappe im Projektmappen-Explorer hinzuzufügen.  
  
     **Projektmappenverzeichnis erstellen**  
     Wählen Sie diese Option aus, um das Textfeld **Projektmappenname** zu aktivieren. Diese Option erstellt ein neues Verzeichnis mit dem gewählten Namen für das Projekt und die Projektmappe.  
  
     **Projektmappenname**  
     Geben Sie den Namen der neuen Projektmappe ein, in der das Projekt erstellt werden soll. Der Standardwert für dieses Feld ist derselbe Name, der im Feld **Name** eingegeben wurde.  
  
     **Hinweis** Um auf diese Option zugreifen zu können, müssen Sie die Kontrollkästchen **Neue Projektmappe erstellen** in der **Projektmappe** und **Projektmappenverzeichnis erstellen** aktivieren. Einige Projektvorlagen unterstützen diese Option nicht (z. B. Webanwendungen).  
  
     **Zur Quellcodeverwaltung hinzufügen**  
     Wenn dieses Kontrollkästchen aktiviert ist, wird die Quellcodeverwaltungs-Anwendung gestartet, sobald Sie auf **OK**klicken. Geben Sie alle Daten ein, die von der Quellcodeverwaltungs-Anwendung angefordert werden, um den Vorgang fortzusetzen. Um diese Option verwenden zu können, muss eine Quellcodeverwaltungs-Clientanwendung installiert sein.  
  
4.  Klicken Sie auf **OK**.  
  
 Für das Skriptprojekt können Sie einen Namen festlegen. Die Ordnernamen hingegen werden von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] festgelegt und können nicht geändert werden. Sie können die Laufwerk- und Pfadspezifikation für den gemeinsamen Ordnersatz mit dem Dialogfeld **Neues Projekt hinzufügen** konfigurieren. Klicken Sie mit der rechten Maustaste auf das Projektmappensymbol im **Projektmappen-Explorer**, und klicken Sie dann auf **Hinzufügen**. Der Standardspeicherort für Skriptprojektordner lautet: „C:\Dokumente und Einstellungen\\*Benutzername*\Eigene Dokumente\SQL Server Management Studio\Projects\\.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Projektmappen-Explorer](solution-explorer.md)   
 [Vorhandenes Projekt zu einer Projekt Mappe hinzufügen](add-an-existing-project-to-a-solution.md)   
 [Hinzufügen neuer Elemente zu einem Projekt](add-new-items-to-a-project.md)   
 [Hinzufügen vorhandener Elemente zu einem Projekt](add-existing-items-to-a-project.md)   
 [Ändern des Standard Speicher Orts für Projekte](change-the-default-location-for-projects.md)   
 [Entfernen oder Löschen eines Elements oder Projekts](remove-or-delete-an-item-or-project.md)   
 [Löschen einer Projektmappe](delete-a-solution.md)  
  
  
