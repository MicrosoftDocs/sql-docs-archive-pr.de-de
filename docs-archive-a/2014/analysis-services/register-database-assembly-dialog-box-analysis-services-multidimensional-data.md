---
title: Datenbankassembly registrieren (Dialog Feld) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidevstudio.assembly.registerassembly.f1
ms.assetid: 0c07cc87-fc94-456f-b878-7b23e39772b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: b2e930754237d8efb591fe698ded68b97f1b7cb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87620569"
---
# <a name="register-database-assembly-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Datenbankassembly registrieren' (Analysis Services – mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Serverassembly registrieren** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] können Sie die Eigenschaften eines Assemblyverweises in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank festlegen. Sie können das Dialogfeld **Serverassembly registrieren** anzeigen, indem Sie in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Objekt-Explorer **mit der rechten Maustaste auf den Ordner Assemblys einer** -Instanz oder -Datenbank klicken und **Neue Assembly**auswählen.  
  
## <a name="options"></a>Tastatur  
  
|Begriff|Definition|  
|----------|----------------|  
|**Type**|Wählen Sie den Typ des Assemblyverweises aus. Die folgenden Werte sind verfügbar:<br /><br /> **.NET-Assembly**: <br />                      Der Assemblyverweis verweist auf eine [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework-Assembly.<br /><br /> **COM DLL**: <br />                      Der Assemblyverweis verweist auf eine COM-Bibliothek.<br /><br /> <br /><br /> Sicherheitsnotiz com-Assemblys können ein Sicherheitsrisiko darstellen. ** \* \* \* \* ** Aufgrund dieses Risikos und anderer Überlegungen wurden COM-Assemblys in [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)]als veraltet markiert. COM-Assemblys werden in zukünftigen Versionen möglicherweise nicht mehr unterstützt.|  
|**Dateiname**|Geben Sie den vollständigen Pfad und den Dateinamen der .NET-Assembly oder COM-Bibliothek ein.|  
|**...**|Klicken Sie auf diese Option, um das Dialogfeld **Öffnen** anzuzeigen, und wählen Sie den vollständigen Pfad und den Dateinamen der .NET-Assembly oder COM-Bibliothek aus.|  
|**AssemblyName**|Hier können Sie per Eingabe den Namen des Assemblyverweises festlegen.<br /><br /> Hinweis: Durch Ändern dieses Werts wird der Name der Assembly, auf den der Assemblyverweis verweist, nicht geändert. Stattdessen wird der Name geändert, der von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz oder -Datenbank beim Verweisen auf den Assemblyverweis verwendet wird.|  
|**Debuginformationen einschließen**|Wählen Sie diese Option aus, um ggf. Debuginformationen für die .NET-Assembly oder COM-Bibliothek einzuschließen.|  
|**Timestamp erstellen**|Zeigt das Datum und die Uhrzeit der Erstellung des Assemblyverweises an.|  
|**Letztes Schemaupdate**|Zeigt das Datum und die Uhrzeit des letzten Updates der Metadaten für den Assemblyverweis an.|  
|**Quelle**|Zeigt die Quelle des Assemblyverweises an. Diese Eigenschaft enthält in der Regel den vollständigen Pfad und den Dateinamen der Assembly, auf die der Assemblyverweis verweist.|  
|**Sauberem**|Wählen Sie diese Option aus, um diesen Berechtigungssatz für den Assemblyverweis zu verwenden. Wenn diese Option ausgewählt ist, hat die Assembly nur Zugriff auf die lokalen Daten und kann nur interne Berechnungen durchführen. Code, der von einer Assembly ausgeführt wird, für die diese Option festgelegt ist, kann nicht auf externe Systemressourcen zugreifen, z. B. Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung.<br /><br /> ** \* \* Sicherheits \* Hinweis \* ** diese Option ist die empfohlene Berechtigungseinstellung für Assemblys, die Berechnungs-und Daten Verwaltungs Tasks ausführen, ohne auf Ressourcen außerhalb von zuzugreifen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Diese Option ist der restriktivste Berechtigungssatz.|  
|**Externer Zugriff**|Wählen Sie diese Option aus, um diesen Berechtigungssatz für den Assemblyverweis zu verwenden. Wenn diese Option ausgewählt ist, hat die Assembly nur Zugriff auf die lokalen Daten und kann nur interne Berechnungen durchführen. Code, der von einer Assembly mit diesem Berechtigungssatz ausgeführt wird, kann auf externe Systemressourcen zugreifen, z. B. Dateien, Netzwerke, Umgebungsvariablen oder die Registrierung.<br /><br /> ** \* \* Sicherheits \* Hinweis \* ** diese Option wird für Assemblys empfohlen, die auf Ressourcen außerhalb von zugreifen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Assemblys, für die diese Option festgelegt ist, verwenden bei der Ausführung standardmäßig die Anmeldeinformationen des Dienstkontos. Der Code in dieser Assembly kann explizit die Identität des Sicherheits Kontexts der Windows-Authentifizierung des Aufrufers annehmen [!INCLUDE[msCoName](../includes/msconame-md.md)] . Aufgrund der standardmäßigen Ausführung als Dienstkonto sollte die Berechtigung zur Ausführung von Assemblys mit dieser Option nur vertrauenswürdigen Rollen erteilt werden. Die Option stellt einen weniger restriktiven Berechtigungssatz als **Sicher**dar, ist jedoch restriktiver als **Uneingeschränkt**.|  
|**Unbegrenzt**|Wählen Sie diese Option aus, um diesen Berechtigungssatz für den Assemblyverweis zu verwenden. Wenn diese Option ausgewählt ist, hat die Assembly uneingeschränkten Zugriff auf interne wie externe Ressourcen. Code, der in einer Assembly mit dieser Option ausgeführt wird, kann nicht verwalteten Code aufrufen.<br /><br /> ** \* \* Sicherheits \* Hinweis \* ** diese Option wird nicht empfohlen, es sei denn, die Assembly erfordert uneingeschränkten Zugriff. Vom Standpunkt der Sicherheit aus betrachtet, ist diese Option mit **Externer Zugriff**identisch. Assemblys, die die Option **Externer Zugriff** verwenden, bieten gegenüber Assemblys mit dieser Optionen ein Mehr an Zuverlässigkeit und Stabilität. Das Festlegen dieser Option ermöglicht es Code in der Assembly, nicht zulässige Vorgänge im Prozessbereich auszuführen. Dies hat eine potenzielle Gefährdung der Stabilität und Skalierbarkeit von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zur Folge. Die Option stellt den am wenigsten restriktiven Berechtigungssatz dar und sollte mit Vorsicht verwendet werden.|  
|**Bestimmten Benutzernamen und bestimmtes Kennwort verwenden**|Wählen Sie diese Option aus, damit das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt die Sicherheitsanmeldeinformationen eines angegebenen Benutzerkontos verwendet.|  
|**Benutzername**|Geben Sie die Domäne und den Namen des Benutzerkontos ein, die von dem ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verwendet werden sollen. Die Domäne und der Name des Benutzerkontos folgen dem folgenden Format:<br /><br /> *\<Domain name>* **\\** *\<User account name>*<br /><br /> Hinweis: Die Option ist nur verfügbar, wenn die Option **Bestimmten Benutzernamen und bestimmtes Kennwort verwenden** ausgewählt ist.|  
|**Kennwort**|Geben Sie die Domäne und den Namen des Benutzerkontos ein, die von dem ausgewählten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt verwendet werden sollen.|  
|**Dienstkonto verwenden**|Wählen Sie diese Option aus, damit das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt die Anmeldeinformationen mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Dienst verwendet, der das Objekt verwaltet.|  
|**Anmeldeinformationen des aktuellen Benutzers verwenden**|Wählen Sie diese Option aus, damit das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekt die Anmeldeinformationen des aktuellen Benutzers verwendet.|  
|**Standard**|Wählen Sie diese Option aus, um das Standardbenutzerkonto für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]zu verwenden. Diese Option entspricht der Option **Anmeldeinformationen des aktuellen Benutzers verwenden** .|  
|**Beschreibung**|Hier können Sie per Eingabe die Beschreibung des Assemblyverweises festlegen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Verwaltung von mehrdimensionalen Modellassemblys](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
