---
title: Testen der Berechtigungen eines Benutzers (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8c109eebb4bf06bf7605ca3b7b5930ce18951e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87618747"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Testen der Berechtigungen eines Benutzers (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können Sie einen Testbenutzer erstellen und sich bei der Webanwendung anmelden, um Berechtigungen zu testen. Wenn ein Benutzer versucht, auf die [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -URL zuzugreifen, werden die Anmeldeinformationen des Benutzers authentifiziert. In Internet Explorer wird über Sicherheitseinstellungen gesteuert, ob dies automatisch stattfindet oder ob der Benutzer einen Benutzernamen und ein Kennwort eingeben muss. Um diese Einstellungen zu ändern, führen Sie die folgenden Schritte aus:  
  
### <a name="to-test-a-users-security"></a>So testen Sie die Sicherheitseinstellungen für einen Benutzer  
  
1.  Klicken Sie in Internet Explorer 7 und höher auf **Extras**, **Internetoptionen**und dann auf die Registerkarte **Sicherheit** .  
  
2.  Klicken Sie auf **Lokales Intranet** und dann auf die Schaltfläche **Stufe anpassen** .  
  
3.  Wählen Sie im Abschnitt **Benutzerauthentifizierung** die Option **Nach Benutzername und Kennwort fragen**aus.  
  
4.  Das nächste Mal, wenn Sie das Browserfenster öffnen, werden Sie zur Eingabe eines Benutzernamens und Kennworts aufgefordert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheit &#40;Master Data Services&#41;](security-master-data-services.md)  
  
  
