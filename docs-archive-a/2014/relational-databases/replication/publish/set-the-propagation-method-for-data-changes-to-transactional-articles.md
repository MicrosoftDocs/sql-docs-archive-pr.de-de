---
title: Festlegen der Propagierungsmethode für Datenänderungen an Transaktionsartikeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
- propagating data changes [SQL Server replication]
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3f8be8b6df1034b06d0aaff6ee61c0c494833c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717848"
---
# <a name="set-the-propagation-method-for-data-changes-to-transactional-articles"></a>Festlegen der Propagierungsmethode für Datenänderungen an Transaktionsartikeln
  In diesem Thema wird beschrieben, wie die Propagierungsmethode für Datenänderungen an Transaktionsartikeln in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]festgelegt wird.  
  
 Standardmäßig werden bei der Transaktionsreplikation an Abonnenten vorgenommene Änderungen mithilfe eines Satzes gespeicherter Prozeduren für den jeweiligen Artikel weitergegeben. Sie können diese Prozeduren durch benutzerdefinierte Prozeduren ersetzen. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So legen Sie die Propagierungsmethode für Datenänderungen an Transaktionsartikeln fest**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Gehen Sie bei der Bearbeitung der bei der Replikation generierten Momentaufnahmedateien mit Bedacht vor. Sie müssen die benutzerdefinierte Logik in den benutzerdefinierten gespeicherten Prozeduren testen und unterstützen. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] bietet keine Unterstützung für benutzerdefinierte Logik.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie die Propagierungsmethode im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** an. Diese Registerkarte steht sowohl im Assistenten für neue Veröffentlichungen als auch im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** zur Verfügung. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-the-propagation-method"></a>So geben Sie die Propagierungsmethode an  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichungen auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.  
  
2.  Klicken Sie auf die Option **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen**.  
  
3.  Geben Sie im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** im Abschnitt **Anweisungsübermittlung** die Propagierungsmethode für die einzelnen Vorgänge an. Verwenden Sie hierzu die Menüs **INSERT-Übermittlungsformat**, **UPDATE-Übermittlungsformat** und **DELETE-Übermittlungsformat**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.  
  
#### <a name="to-generate-and-use-custom-stored-procedures"></a>So generieren und verwenden Sie benutzerdefinierte Prozeduren  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichungen auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.  
  
2.  Klicken Sie auf die Option **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen**.  
  
     Wählen Sie im Dialogfeld **Artikeleigenschaften - \<Article>** auf der Registerkarte **Eigenschaften** im Abschnitt **Anweisungsübermittlung** die CALL-Syntax im Menü des entsprechenden Übermittlungsformats (**INSERT-Übermittlungsformat**, **UPDATE-Übermittlungsformat** oder **DELETE-Übermittlungsformat**) aus, und geben Sie dann den Namen der Prozedur ein, die in **gespeicherter Prozedur INSERT**, in **gespeicherter Prozedur DELETE** oder **in gespeicherter Prozedur UPDATE** verwendet werden soll. Weitere Informationen zur CALL-Syntax finden Sie im Abschnitt „Aufrufsyntax für gespeicherte Prozeduren“ in [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften - \<Publication>** befinden, klicken Sie auf **OK**, um die Einstellungen zu speichern und das Dialogfeld zu schließen.  
  
5.  Wenn die Momentaufnahme für die Veröffentlichung generiert wird, enthält er die Prozedur, die Sie im vorherigen Schritt angegeben haben. Von den Prozeduren wird die von Ihnen angegebene CALL-Syntax verwendet, die bei der Replikation verwendete Standardlogik ist jedoch enthalten.  
  
     Navigieren Sie nach der Momentaufnahmegenerierung zu dem Momentaufnahmeordner der Veröffentlichung, zu der dieser Artikel gehört, und suchen Sie die **.sch** -Datei, die denselben Namen wie der Artikel trägt. Öffnen Sie diese Datei im Editor oder einem anderen Text-Editor, suchen Sie den CREATE PROCEDURE-Befehl für die gespeicherte Prozedur INSERT, UPDATE oder DELETE, und bearbeiten Sie die Prozedurdefinition, um jegliche benutzerdefinierte Logik für das Propagieren von Datenänderungen bereitzustellen. Wenn die Momentaufnahme erneut generiert wird, muss die benutzerdefinierte Prozedur ebenfalls erneut erstellt werden.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die Transaktionsreplikation ermöglicht es Ihnen zu steuern, wie Änderungen vom Verleger an die Abonnenten weitergegeben (propagiert) werden. Diese Propagierungsmethode kann bei der Erstellung eines Artikels programmgesteuert festgelegt und später anhand gespeicherter Replikationsprozeduren geändert werden.  
  
> [!NOTE]  
>  Sie können für jeden DML-Vorgangstyp (Data Manipulation Language, Datenbearbeitungssprache), der auf einer Zeile veröffentlichter Daten vorkommt (Einfügen, Aktualisieren oder Löschen), eine andere Propagierungsmethode angeben.  
  
 Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-that-uses-transact-sql-commands-to-propagate-data-changes"></a>So erstellen Sie einen Artikel, der Transact-SQL-Befehle verwendet, um Datenänderungen weiterzugeben  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das Datenbankobjekt, das veröffentlicht wird, für **\@source_object** und den Wert **SQL** für mindestens einen der folgenden Parameter an:  
  
    -   **\@ins_cmd**: Steuert die Replikation von [INSERT](/sql/t-sql/statements/insert-transact-sql)-Befehlen.  
  
    -   **\@upd_cmd**: Steuert die Replikation von [UPDATE](/sql/t-sql/queries/update-transact-sql)-Befehlen.  
  
    -   **\@del_cmd**: Steuert die Replikation von [DELETE](/sql/t-sql/statements/delete-transact-sql)-Befehlen.  
  
    > [!NOTE]  
    >  Wenn Sie den Wert **SQL** für einen der obigen Parameter angeben, werden die Befehle des betreffenden Typs auf den Abonnenten als entsprechende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Befehle repliziert.  
  
     Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
#### <a name="to-create-an-article-that-does-not-propagate-data-changes"></a>So erstellen Sie einen Artikel, der keine Datenänderungen weitergibt  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das Datenbankobjekt, das veröffentlicht wird, für **\@source_object** und den Wert **NONE** für mindestens einen der folgenden Parameter an:  
  
    -   **\@ins_cmd**: Steuert die Replikation von [INSERT](/sql/t-sql/statements/insert-transact-sql)-Befehlen.  
  
    -   **\@upd_cmd**: Steuert die Replikation von [UPDATE](/sql/t-sql/queries/update-transact-sql)-Befehlen.  
  
    -   **\@del_cmd**: Steuert die Replikation von [DELETE](/sql/t-sql/statements/delete-transact-sql)-Befehlen.  
  
    > [!NOTE]  
    >  Wenn Sie den Wert **NONE** für einen der obigen Parameter angeben, werden die Befehle des betreffenden Typs auf den Abonnenten nicht repliziert.  
  
     Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
#### <a name="to-create-an-article-with-user-modified-custom-stored-procedures"></a>So erstellen Sie einen Artikel mit benutzerdefinierten gespeicherten Prozeduren  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das zu veröffentlichende Datenbankobjekt für **\@source_object**, einen Wert für die **\@schema_option**-Bitmaske, der den Wert **0x02** enthält (aktiviert die automatische Erstellung benutzerdefinierter gespeicherter Prozeduren), und mindestens einen der folgenden Parameter an:  
  
    -   ** \@ ins_cmd** geben Sie den Wert " <strong>callsp_MSins_*article_name*</strong>" an, wobei **_article_name_** der für den ** \@ Artikel**angegebene Wert ist.  
  
    -   ** \@ del_cmd** : Geben Sie den Wert " <strong>callsp_MSdel_*article_name* </strong> " oder " <strong>xcallsp_MSdel_*article_name*</strong>" an, wobei **_article_name_** der Wert ist, der für _ * \@ article * * angegeben ist.  
  
    -   ** \@ upd_cmd** : Geben Sie den Wert <strong>SCALL sp_Msupd_*article_name*</strong>, den Befehl <strong>sp_Msupd_*article_name*</strong>, <strong>xcallsp_MSupd__article_name *</strong> oder <strong>mcallsp_MSupd_* article_name *</strong>an, wobei _**article_name**_ der Wert ist, der für den ** \@ Artikel**angegeben ist.  
  
    > [!NOTE]  
    >  Für jeden der obigen Befehlsparameter gilt: Sie können einen selbst gewählten Namen für die gespeicherten Prozeduren angeben, die von der Replikation generiert werden.  
  
    > [!NOTE]  
    >  Weitere Informationen über die CALL, SCALL, XCALL und MCALL-Syntax finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Navigieren Sie nach der Momentaufnahmegenerierung zu dem Momentaufnahmeordner der Veröffentlichung, zu der dieser Artikel gehört, und suchen Sie die **.sch** -Datei, die denselben Namen wie der Artikel trägt. Öffnen Sie diese Datei mit Notepad.exe, suchen Sie den CREATE PROCEDURE-Befehl für die gespeicherte Prozedur INSERT, UPDATE oder DELETE, und bearbeiten Sie die Prozedurdefinition, um eine benutzerdefinierte Logik für die Propagierung von Datenänderungen bereitzustellen. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-with-custom-scripting-in-the-custom-stored-procedures-to-propagate-data-changes"></a>So erstellen Sie einen Artikel mit benutzerdefinierter Skriptprozedur in den benutzerdefinierten gespeicherten Prozeduren, um Datenänderungen weiterzugeben  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für **\@publication**, den Namen des Artikels für **\@article**, das zu veröffentlichende Datenbankobjekt für **\@source_object**, einen Wert für die **\@schema_option**-Bitmaske, der den Wert **0x02** enthält (aktiviert die automatische Erstellung benutzerdefinierter gespeicherter Prozeduren), und mindestens einen der folgenden Parameter an:  
  
    -   ** \@ ins_cmd** geben Sie den Wert " <strong>callsp_MSins_*article_name*</strong>" an, wobei _**article_name**_ der für den ** \@ Artikel**angegebene Wert ist.  
  
    -   ** \@ del_cmd** : Geben Sie den Wert " <strong>callsp_MSdel_*article_name* </strong> " oder " <strong>xcallsp_MSdel_*article_name*</strong>" an, wobei _**article_name**_ der für den ** \@ Artikel**angegebene Wert ist.  
  
    -   ** \@ upd_cmd** : Geben Sie den Wert <strong>SCALL sp_Msupd_*article_name*</strong>an, und <strong>sp_Msupd_*article_name*</strong>, <strong>xcallsp_MSupd_*article_name*</strong>article_name, <strong>mcallsp_MSupd_*article_name article_name*</strong>, wobei _**article_name**_ der Wert ist, der für den ** \@ Artikel**angegeben ist.  
  
    > [!NOTE]  
    >  Für jeden der obigen Befehlsparameter gilt: Sie können einen selbst gewählten Namen für die gespeicherten Prozeduren angeben, die von der Replikation generiert werden.  
  
    > [!NOTE]  
    >  Weitere Informationen über die CALL, SCALL, XCALL und MCALL-Syntax finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Verwenden Sie auf dem Verleger für die Veröffentlichungsdatenbank die [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) -Anweisung, um [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) so zu bearbeiten, dass ein [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) -Skript für die benutzerdefinierten, gespeicherten Prozeduren INSERT, UPDATE und DELETE zurückgegeben wird. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-change-the-method-of-propagating-changes-for-an-existing-article"></a>So ändern Sie die Methode zur Weitergabe von Änderungen an einen vorhandenen Artikel  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)aus. Geben Sie **\@publication**, **\@article**, den Wert **ins_cmd**, **upd_cmd** oder **del_cmd** für **\@property** und die entsprechende Propagierungsmethode für **\@value** an.  
  
2.  Wiederholen Sie Schritt 1 für jede Propagierungsmethode, die geändert werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Erstellen einer Veröffentlichung](create-a-publication.md)  
  
  
