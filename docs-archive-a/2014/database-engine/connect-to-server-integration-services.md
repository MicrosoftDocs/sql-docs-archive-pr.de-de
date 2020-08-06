---
title: Verbindung mit Server herstellen (Integration Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8821018c45fdd77c4b3b896afc47b8f5b425af88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87724142"
---
# <a name="connect-to-server-integration-services"></a>Verbindung mit Server herstellen (Integration Services)
  Verwenden Sie dieses Dialogfeld, um Optionen bei der Verbindungsherstellung mit [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
 **Servertyp**  
 Wenn Sie einen Server über den Objekt-Explorer registrieren, wählen Sie den Typ des Servers aus, mit dem eine Verbindung hergestellt wird: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services oder Integration Services. Im verbleibenden Bereich des Dialogfelds werden nur die Optionen angezeigt, die auf den ausgewählten Servertyp zutreffen. Wenn Sie einen Server über Registrierte Server registrieren, ist das Feld Servertyp schreibgeschützt, wobei der Feldeintrag mit dem in der Komponente Registrierte Server angezeigten Servertyp übereinstimmt. Zum Registrieren eines anderen Servertyps wählen Sie auf der Symbolleiste "Registrierte Server" die Option [!INCLUDE[ssDE](../includes/ssde-md.md)], "Analysis Services", "Reporting Services" oder "Integration Services" aus. Anschließend können Sie mit der Registrierung eines neuen Servers beginnen.  
  
 **Servername**  
 Wählen Sie den Server für die Verbindungsherstellung aus. Standardmäßig wird die Serverinstanz angezeigt, mit der zuletzt eine Verbindung bestanden hat.  
  
> [!NOTE]  
>  Verwenden Sie nicht *\<servername>* \\ *\<instancename>* , da [!INCLUDE[ssIS](../includes/ssis-md.md)] nicht mehrere Instanzen auf einem Computer unterstützt.  
  
 **Authentifizierung**  
 Für [!INCLUDE[msCoName](../includes/msconame-md.md)] steht nur die [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows-Authentifizierung zur Verfügung. Der Windows Authentifizierungsmodus ermöglicht Benutzern die Verbindung über ein Windows-Benutzerkonto.  
  
 **Benutzername**  
 Diese Option ist nicht verfügbar, da für [!INCLUDE[ssIS](../includes/ssis-md.md)]nur die Windows-Authentifizierung zur Verfügung steht.  
  
 **Kennwort**  
 Diese Option ist nicht verfügbar, da für [!INCLUDE[ssIS](../includes/ssis-md.md)]nur die Windows-Authentifizierung zur Verfügung steht.  
  
 **Herstellen einer Verbindung**  
 Klicken Sie hier, um eine Verbindung mit dem oben ausgewählten Server herzustellen.  
  
 **Optionen**  
 Klicken Sie auf diese Schaltfläche, um zusätzliche Optionen für die Serververbindung anzuzeigen, z. B. zum Registrieren eines Servers oder zum Speichern des Kennworts.  
  
  
