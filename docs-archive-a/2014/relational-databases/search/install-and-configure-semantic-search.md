---
title: Installieren und Konfigurieren der semantischen Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717725"
---
# <a name="install-and-configure-semantic-search"></a>Installieren und Konfigurieren der semantischen Suche
  Beschreibt die erforderlichen Komponenten für die statistische semantische Suche und wie diese Komponenten installiert oder überprüft werden.  
  
## <a name="installing-semantic-search"></a>Installieren der semantischen Suche  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a>Gewusst wie: überprüfen, ob die semantische Suche installiert ist  
 Fragen Sie die Eigenschaft **IsFullTextInstalled** der Metadatenfunktion [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) ab.  
  
 Der Rückgabewert 1 gibt an, dass die Volltextsuche und die semantische Suche installiert sind. Der Rückgabewert 0 gibt an, dass sie nicht installiert sind.  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a>Gewusst wie: Installieren der semantischen Suche  
 Wählen Sie zum Installieren der semantischen Suche während des Setups auf der Seite **Zu installierende Funktionen** die Option **Volltext- und semantische Extraktion für Suche** aus.  
  
 Die statistische semantische Suche ist von der Volltextsuche abhängig. Diese zwei optionalen Funktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden zusammen installiert.  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a>Installieren oder Entfernen der Datenbank für semantische Sprachstatistik  
 Die semantische Suche hat eine zusätzliche externe Abhängigkeit, die als semantische Sprachstatistikdatenbank bezeichnet wird. Diese Datenbank enthält die für die semantische Suche erforderlichen statistischen Sprachmodelle. Eine einzelne semantische Sprachstatistikdatenbank enthält die Sprachenmodelle für alle Sprachen, die für die semantische Indizierung unterstützt werden.  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a>Vorgehensweise: überprüfen, ob die Semantic Language Statistics-Datenbank installiert ist  
 Fragen Sie die Katalogsicht [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql) ab.  
  
 Wenn die semantische Sprachstatistikdatenbank installiert und für die Instanz registriert ist, dann enthalten die Abfrageergebnisse eine einzelne Zeile mit Informationen zur Datenbank.  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a>Vorgehensweise: installieren, Anfügen und Registrieren der Semantic Language Statistics Datenbank  
 Die Datenbank für semantische Sprachstatistik wird nicht vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setupprogramm installiert. Führen Sie zum Einrichten der semantischen Sprachstatistikdatenbank als erforderliche Komponente für die semantische Indizierung folgende Aufgaben aus:  
  
 **1. Installieren Sie die Datenbank für semantische Sprachstatistik.**  
 1.  Suchen Sie die semantische Sprachstatistikdatenbank auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationsmedium, oder laden Sie sie aus dem Internet herunter.  
  
    -   Suchen Sie das Windows Installer-Paket **SemanticLanguageDatabase.msi** auf den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationsmedien. Suchen Sie je nach Zielsystem die 32-Bit- oder 64-Bit-Version des Installationspakets. Der Name des entsprechenden Ordners identifiziert die 32-Bit- oder 64-Bit-Version der Datei; der Dateiname selbst ist für beide Versionen gleich.  
  
    -   Laden Sie das Installer-Paket von [Microsoft herunter? SQL Server?? 2014 Semantic Language Statistics](https://go.microsoft.com/fwlink/?LinkID=296743) Seite im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Download Center.  
  
2.  Führen Sie das **SemanticLanguageDatabase.msi** Windows Installer-Paket aus, um die Datenbank und die Protokolldatei zu extrahieren.  
  
     Sie können optional das Zielverzeichnis ändern. Standardmäßig extrahiert das Installationsprogramm die Dateien in den Ordner **Microsoft Semantic Language Database** im Ordner mit den 32-Bit- oder 64-Bit-Programmdateien. Die MSI-Datei enthält eine komprimierte Datenbankdatei und eine Protokolldatei.  
  
3.  Verschieben Sie die extrahierte Datenbank- und Protokolldatei an einen passenden Speicherort im Dateisystem.  
  
     Wenn Sie die Dateien an ihrem Standardspeicherort belassen, ist es nicht möglich, für eine weitere Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]eine weitere Kopie der Datenbank zu extrahieren.  
  
> [!IMPORTANT]  
>  Beim Extrahieren der semantischen Sprachstatistikdatenbank werden der Datenbankdatei und der Protokolldatei am Standardspeicherort im Dateisystem eingeschränkte Berechtigungen zugewiesen. Folglich verfügen Sie möglicherweise nicht über die Berechtigung, die Datenbank anzufügen, wenn Sie diese am Standardspeicherort belassen. Tritt ein Fehler beim Versuch auf, die Datenbank anzufügen, verschieben Sie die Dateien, oder überprüfen Sie die Dateisystemberechtigungen, und korrigieren Sie diese entsprechend.  
  
 **2. Fügen Sie die Datenbank für die semantische Sprachstatistik an.**  
 Fügen Sie die Datenbank zur Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder durch Aufrufen von [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) mit der **FOR ATTACH**-Syntax an. Weitere Informationen finden Sie unter [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md).  
  
 Standardmäßig lautet der Name der Datenbank **semanticsdb**. Sie können der Datenbank beim Anfügen einen anderen Namen geben. Sie müssen diesen Namen angeben, wenn Sie die Datenbank im nachfolgenden Schritt registrieren.  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 Bei diesem Codebeispiel wird davon ausgegangen, dass Sie die Datenbank von ihrem Standardspeicherort zu einem neuen Speicherort verschoben haben.  
  
 **3. Registrieren Sie die Datenbank für die semantische Sprachstatistik.**  
 Rufen Sie die gespeicherte Prozedur [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) auf, und geben Sie den Namen an, den die Datenbank beim Anfügen erhalten hat:  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a>Vorgehensweise: Aufheben der Registrierung, trennen und Entfernen der Semantic Language Statistics Datenbank  
 **Heben Sie die Registrierung der semantischen sprach Statistik Datenbank auf.**  
 Rufen Sie die gespeicherte Prozedur [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql) auf. Sie müssen den Namen der Datenbank nicht angeben, da eine Instanz nur eine semantische Sprachstatistikdatenbank aufweisen kann.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 **Trennen Sie die Datenbank für die semantische sprach Statistik.**  
 Rufen Sie die gespeicherte Prozedur [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) auf, und geben Sie den Namen der Datenbank an.  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 **Entfernen Sie die semantische sprach Statistik Datenbank.**  
 Nach dem Aufheben und Trennen der Datenbank können Sie die Datenbankdatei einfach löschen. Es gibt kein Deinstallationsprogramm und keinen Eintrag unter **Programme und Funktionen** in der Systemsteuerung.  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a>Anforderungen und Einschränkungen für das Installieren und Entfernen der Semantic Language Statistics Datenbank  
  
-   Sie können nur eine Datenbank für semantische Sprachstatistik in einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]anfügen und registrieren.  
  
     Für jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf einem einzelnen Computer ist eine separate physische Kopie der semantischen Sprachstatistikdatenbank erforderlich. Fügen Sie eine Kopie an jede Instanz an.  
  
-   Es ist nicht möglich, eine gültige und registrierte semantische Sprachstatistikdatenbank zu trennen und sie durch eine beliebige Datenbank mit demselben Namen zu ersetzen. Dadurch würden bei aktiven oder zukünftigen Indexauffüllungen ein Fehler auftreten.  
  
-   Die semantische Sprachstatistikdatenbank ist schreibgeschützt. Sie können diese Datenbank nicht anpassen. Wenn Sie den Inhalt der Datenbank ändern, sind die Ergebnisse für die zukünftige semantische Indizierung indeterministisch. Um den ursprünglichen Status dieser Daten wiederherzustellen, können Sie die geänderte Datenbank löschen und eine neue, unveränderte Kopie der Datenbank herunterladen.  
  
-   Es ist möglich, die semantische Sprachstatistikdatenbank zu trennen oder zu löschen. Wenn aktive Indizierungs Vorgänge mit Lese Sperren in der Datenbank vorhanden sind, tritt beim Trennen oder löschen ein Fehler auf, oder es tritt ein Timeout auf. Dies ist mit vorhandenem Verhalten konsistent. Nach dem Entfernen der Datenbank schlagen alle semantischen Indizierungsvorgänge fehl.  
  
## <a name="installing-optional-support-for-newer-document-types"></a>Installieren von optionaler Unterstützung für neuere Dokumenttypen  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a>Gewusst wie: Installieren der neuesten Filter für Microsoft Office und andere Microsoft-Dokumenttypen  
 Diese Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert die neuesten [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Wörtertrennungen und -Wortstammerkennungen, aber nicht die neuesten Filter für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office-Dokumente und andere [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Dokumenttypen. Diese Filter sind zum Indizieren von Dokumenten erforderlich, die mit den neuen Versionen von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office und anderen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] -Anwendungen erstellt wurden. Die neuesten Filter können unter [Microsoft Office 2010-Filterpakete](https://www.microsoft.com/download/details.aspx?id=17062)heruntergeladen werden.  
  
  
