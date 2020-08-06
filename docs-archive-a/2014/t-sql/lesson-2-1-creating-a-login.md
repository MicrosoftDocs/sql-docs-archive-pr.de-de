---
title: Erstellen einer Anmeldung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 400a57693fbea10270a51f5735a19b9639112ce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87722133"
---
# <a name="creating-a-login"></a>Erstellen einer Anmeldung
  Benutzer benötigen eine Anmeldung, damit sie auf [!INCLUDE[ssDE](../includes/ssde-md.md)]zugreifen können. Die Anmeldung kann die Identität des Benutzers als Windows-Konto oder als Mitglied einer Windows-Gruppe darstellen, oder es kann sich dabei um eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldung handeln, die nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]vorhanden ist. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
 Standardmäßig haben Administratoren auf Ihrem Computer vollständigen Zugriff auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In dieser Lektion benötigen wir einen Benutzer mit geringeren Privilegien. Aus diesem Grund erstellen Sie ein neues lokales Windows-Authentifizierungskonto auf Ihrem Computer. Dazu müssen Sie über Administratorrechte auf dem Computer verfügen. Anschließend erteilen Sie diesem neuen Benutzer Zugriff auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="to-create-a-new-windows-account"></a>So erstellen Sie ein neues Windows-Konto  
  
1.  Klicken Sie im **Startmenü**auf **Ausführen**, geben Sie im Feld **Öffnen** ein `%SystemRoot%\system32\compmgmt.msc /s` , und klicken Sie dann auf **OK** , um das Programm Computer Verwaltung zu öffnen.  
  
2.  Erweitern Sie unter **Systemprogramme**den Eintrag **Lokale Benutzer und Gruppen**, klicken Sie mit der rechten Maustaste auf **Benutzer**und anschließend auf **Neuer Benutzer**.  
  
3.  Geben Sie in das Feld **Benutzername****Mary**ein.  
  
4.  Geben Sie in das Feld **Kennwort** und **Kennwort bestätigen** ein sicheres Kennwort ein. Klicken Sie anschließend auf **Erstellen** , um einen neuen lokalen Windows-Benutzer zu erstellen.  
  
### <a name="to-create-a-login"></a>So erstellen Sie eine Anmeldung  
  
1.  Geben Sie in einem Abfrage-Editor-Fenster von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]folgenden Code ein, und führen Sie ihn aus. Ersetzen Sie dabei `computer_name` durch den Namen Ihres Computers. `FROM WINDOWS` gibt an, dass Windows den Benutzer authentifiziert. Mit dem optionalen `DEFAULT_DATABASE` -Argument wird `Mary` mit der `TestData` -Datenbank verbunden, sofern nicht ihre Verbindungszeichenfolge eine andere Datenbank angibt. Diese Anweisung führt das Semikolon als optionale Beendigung für eine [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisung ein.  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
     Dadurch wird ein Benutzer mit Namen `Mary`, der von Ihrem Computer authentifiziert wird, zum Zugriff auf diese Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]berechtigt. Ist auf dem Computer mehr als eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vorhanden, müssen Sie die Anmeldung auf jeder Instanz erstellen, auf die `Mary` Zugriff benötigt.  
  
    > [!NOTE]  
    >  Weil `Mary` kein Domänenkonto ist, kann dieser Benutzername nur auf diesem Computer authentifiziert werden.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Gewähren von Zugriff auf eine Datenbank](lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [Auswählen eines Authentifizierungsmodus](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
