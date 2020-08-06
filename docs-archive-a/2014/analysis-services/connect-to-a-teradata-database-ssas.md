---
title: Herstellen einer Verbindung mit einer Teradata-Datenbank (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connterradb.f1
ms.assetid: 875ad4a3-a2b3-4b68-8c1c-6507e9f25b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 047eed5f8625059750a67c51735c7c0d61d17853
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87610212"
---
# <a name="connect-to-a-teradata-database-ssas"></a>Mit einer Teradata-Datenbank verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie Einstellungen angeben, um eine Verbindung mit einer Teradata-Datenbank herzustellen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
> [!NOTE]  
>  Beim Auswählen einer Datenbank auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Servername**  
 Wählen Sie den Namen der Serverinstanz aus, zu der eine Verbindung hergestellt werden soll, oder geben Sie ihn an.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an.  
  
 Dieser Benutzername wird beim Erstellen der Verbindungszeichenfolge für die Datenquelle verwendet. Diese Anmeldeinformationen werden auch beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **Kennwort**  
 Geben Sie ein Kennwort für die Datenbankverbindung an.  
  
 **Kennwort speichern**  
 Geben Sie an, ob das Kennwort, das Sie im Feld **Kennwort** eingegeben haben, gespeichert werden soll.  
  
 **Erweitert**  
 Legen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest. Weitere Informationen finden Sie unter [Festlegen von erweiterten Eigenschaften &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
