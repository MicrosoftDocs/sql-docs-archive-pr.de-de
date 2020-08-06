---
title: Paket Konfigurationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d22dbfedcf4cf7084e1667586f9774926f3b2a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622776"
---
# <a name="package-configurations"></a>Paketkonfigurationen
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stellt Paketkonfigurationen bereit, die Sie zum Aktualisieren der Werte von Eigenschaften zur Laufzeit verwenden können.  
  
> [!NOTE]  
>  Konfigurationen sind für das Paketbereitstellungsmodell verfügbar. Parameter werden für das Projektbereitstellungsmodell anstelle von Konfigurationen verwendet. Mithilfe des Projektbereitstellungsmodells können Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekte auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen. Weitere Informationen zu Bereitstellungsmodellen finden Sie unter [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Eine Konfiguration ist ein Eigenschaft/Wert-Paar, das zu einem fertigen Paket hinzugefügt werden kann. Normalerweise erstellen Sie ein Paket, legen bei der Paketentwicklung die Eigenschaften der Paketobjekte fest und fügen die Konfiguration dem Paket hinzu. Bei der Ausführung ruft das Paket die neuen Werte für die Eigenschaften aus der Konfiguration ab. Sie können mithilfe einer Konfiguration beispielsweise die Verbindungszeichenfolge eines Verbindungs-Managers ändern oder den Wert einer Variablen aktualisieren.  
  
 Paketkonfigurationen bieten die folgenden Vorteile:  
  
-   Konfigurationen erleichtern das Verschieben von Paketen aus einer Entwicklungsumgebung in eine Produktionsumgebung. Mit einer Konfiguration können Sie z. B. den Pfad einer Quelldatei aktualisieren oder den Namen einer Datenbank oder eines Servers ändern.  
  
-   Konfigurationen sind nützlich, wenn Sie Pakete für viele unterschiedliche Server bereitstellen. Eine Variable in der Konfiguration für jedes bereitgestellte Paket kann beispielsweise verschiedene Speicherplatzwerte enthalten, und wenn der verfügbare Speicherplatz nicht dem Wert entspricht, kann das Paket nicht ausgeführt werden.  
  
-   Konfigurationen machen Pakete flexibler. So kann z. B. eine Konfiguration den Wert einer Variablen aktualisieren, die in einem Eigenschaftsausdruck verwendet wird.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] unterstützt verschiedene unterschiedliche Methoden zum Speichern von Paketkonfigurationen, z.B. als XML-Dateien, als Tabellen in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank und als Umgebungs- und Paketvariablen.  
  
 Jede Konfiguration besteht aus einem Paar aus Eigenschaft und Wert. Die XML-Konfigurationsdatei und die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurationstypen können mehrere Konfigurationen enthalten.  
  
 Die Konfigurationen werden einbezogen, wenn Sie ein Paketbereitstellungshilfsprogramm zum Installieren von Paketen erstellen. Wenn Sie die Pakete installieren, können die Konfigurationen im Rahmen eines Schritts bei der Paketinstallation aktualisiert werden.  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a>Grundlegendes zur Anwendung von Paketkonfigurationen zur Laufzeit  
 Wenn Sie das Befehlszeilen-Hilfsprogramm **dtexec.exe** verwenden, um ein bereitgestelltes Paket auszuführen, wendet das Hilfsprogramm Paketkonfigurationen zweimal an. Das Hilfsprogramm wendet Konfigurationen sowohl vor als auch nach dem Anwenden der Optionen an, die Sie in der Befehlszeile angegeben haben.  
  
 Während das Hilfsprogramm das Paket lädt und ausführt, treten Ereignisse in der folgenden Reihenfolge auf:  
  
1.  Das Hilfsprogramm **dtexec** lädt das Paket.  
  
2.  Das Hilfsprogramm wendet die Konfigurationen, die zur Entwurfszeit im Paket angegeben wurden, in der Reihenfolge an, die im Paket festgelegt ist. (Die einzige Ausnahme ist hierbei die Variablenkonfiguration für übergeordnete Pakete. Das Hilfsprogramm wendet diese Konfigurationen nur einmal später im Prozess an.)  
  
3.  Das Hilfsprogramm wendet dann alle Optionen an, die Sie in der Befehlszeile angegeben haben.  
  
4.  Anschließend lädt das Hilfsprogramm die Konfigurationen neu, die zur Entwurfszeit im Paket angegeben wurden. Dabei wird die Reihenfolge verwendet, die im Paket festgelegt ist. (Die Ausnahme von dieser Regel ist wiederum die Variablenkonfiguration für übergeordnete Pakete.) Das Hilfsprogramm verwendet alle angegebenen Befehlszeilenoptionen, um die Konfigurationen neu zu laden. Es kann also sein, dass andere Werte von einem anderen Speicherort erneut geladen werden.  
  
5.  Das Hilfsprogramm wendet die Variablenkonfiguration für übergeordnete Pakete an.  
  
6.  Das Hilfsprogramm führt das Paket aus.  
  
 Die Art und Weise, wie das Hilfsprogramm **dtexec** Konfigurationen anwendet, wirkt sich auf die folgenden Befehlszeilenoptionen aus:  
  
-   Sie können zur Laufzeit die Option **/Connection** oder **/Set** verwenden, um Paketkonfigurationen von einem anderen Speicherort als dem zur Entwurfszeit angegebenen Speicherort zu laden.  
  
-   Sie können die Option **/ConfigFile** verwenden, um zur Laufzeit zusätzliche Konfigurationen zu laden, die Sie zur Entwurfszeit nicht angegeben haben.  
  
 Für diese Befehlszeilenoptionen gelten jedoch einige Einschränkungen:  
  
-   Sie können die Option **/Set** oder **/Connection** nicht verwenden, um einzelne Werte zu überschreiben, die auch von einer Konfiguration festgelegt werden.  
  
-   Sie können die Option **/ConfigFile** nicht verwenden, um Konfigurationen zu laden, die die zur Entwurfszeit angegebenen Konfigurationen ersetzen.  
  
 Weitere Informationen zu diesen Optionen und dazu, wie sich das Verhalten dieser Optionen zwischen [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] und früheren Versionen unterscheidet, finden [Sie unter Verhaltensänderungen in Integration Services Features in SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).  
  
## <a name="package-configuration-types"></a>Paketkonfigurationstypen  
 Die folgende Tabelle beschreibt die verschiedenen Paketkonfigurationstypen.  
  
|type|BESCHREIBUNG|  
|----------|-----------------|  
|XML-Konfigurationsdatei|Eine XML-Datei enthält die Konfigurationen. Die XML-Datei kann mehrere Konfigurationen enthalten.|  
|Umgebungsvariable|Eine Umgebungsvariable enthält die Konfiguration.|  
|Registrierungseintrag|Ein Registrierungseintrag enthält die Konfiguration.|  
|Variable für das übergeordnete Paket|Eine Variable im Paket enthält die Konfiguration. Dieser Konfigurationstyp wird normalerweise zum Aktualisieren von Eigenschaften in untergeordneten Paketen verwendet.|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tabelle|Eine Tabelle in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank enthält die Konfiguration. Die Tabelle kann mehrere Konfigurationen enthalten.|  
  
### <a name="xml-configuration-files"></a>XML-Konfigurationsdateien  
 Wenn Sie den Konfigurationstyp **XML-Konfigurationsdatei** auswählen, können Sie eine neue Konfigurationsdatei erstellen, eine vorhandene Datei erneut verwenden und neue Konfigurationen hinzufügen oder eine vorhandene Datei erneut verwenden und dabei den bisherigen Dateiinhalt überschreiben.  
  
 Eine XML-Konfigurationsdatei besteht aus zwei Abschnitten:  
  
-   Einer Überschrift, die Informationen zur Konfigurationsdatei enthält. Dieses Element enthält Attribute wie z. B. der Erstellungszeitpunkt der Datei und den Namen der Person, von der die Datei erstellt wurde.  
  
-   Konfigurationselemente können Informationen zu jeder Konfiguration enthalten. Dieses Element enthält Attribute wie z. B. den Eigenschaftspfad und den konfigurierten Wert einer Eigenschaft.  
  
 Das folgende XML-Codebeispiel veranschaulicht die Syntax von XML-Konfigurationsdateien. Das Beispiel zeigt eine Konfiguration für die Value-Eigenschaft der ganzzahligen Variable `MyVar`.  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a>Registrierungseintrag  
 Wenn Sie zum Speichern einer Konfiguration einen Registrierungseintrag verwenden möchten, können Sie entweder einen vorhandenen Schlüssel verwenden oder einen neuen Schlüssel in HKEY_CURRENT_USER erstellen. Der verwendete Registrierungsschlüssel muss einen Wert mit dem Namen `Value` aufweisen. Bei diesem Wert kann es sich um einen Wert vom Typ DWORD oder um eine Zeichenfolge handeln.  
  
 Wenn Sie den Konfigurationstyp **Registrierungseintrag** auswählen, geben Sie den Namen des Registrierungsschlüssels im Eingabefeld Registrierung ein. Das Format ist \<registry key>. Wenn Sie einen Registrierungsschlüssel verwenden möchten, der nicht im Stamm von HKEY_CURRENT_USER enthalten ist, verwenden Sie das Format \<Registry key\registry key\\...>, um den Schlüssel zu identifizieren. Wenn Sie beispielsweise den Schlüssel MyPackage verwenden, der sich in SSISPackages befindet, geben Sie `SSISPackages\MyPackage` ein.  
  
### <a name="sql-server"></a>SQL Server  
 Wenn Sie den Konfigurationstyp **SQL Server** auswählen, geben Sie die Verbindung mit der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank an, in der die Konfigurationen gespeichert werden sollen. Sie können die Konfigurationen in einer vorhandenen Tabelle speichern oder eine neue Tabelle in der angegebenen Datenbank erstellen.  
  
 Die folgende SQL-Anweisung zeigt die standardmäßige CREATE TABLE-Anweisung, die der Paketkonfigurations-Assistent bereitstellt.  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 Der Name, den Sie für die Konfiguration bereitstellen, ist der Wert, der in der **ConfigurationFilter** -Spalte gespeichert wird.  
  
## <a name="direct-and-indirect-configurations"></a>Direkte und indirekte Konfigurationen  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ermöglicht direkte und indirekte Konfigurationen. Wenn Sie Konfigurationen direkt angeben, erstellt [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] eine direkte Verknüpfung zwischen dem Konfigurationselement und der Paketobjekteigenschaft. Direkte Konfigurationen sind die bessere Wahl, wenn sich der Speicherort der Quelle nicht ändert. Wenn Sie z. B. sicher sind, dass alle Bereitstellungen im Paket denselben Dateipfad verwenden, können Sie eine XML-Konfigurationsdatei angeben.  
  
 Indirekte Konfigurationen verwenden Umgebungsvariablen. Statt die Konfigurationseinstellung direkt anzugeben, zeigt die Konfiguration auf eine Umgebungsvariable, die ihrerseits den Konfigurationswert enthält. Das Verwenden indirekter Konfigurationen ist die bessere Wahl, wenn sich der Speicherort der Konfiguration für jede Bereitstellung eines Pakets ändern kann.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Technischer Artikel [Grundlegendes zu Integration Services-Paketkonfigurationen](https://go.microsoft.com/fwlink/?LinkId=165643)auf msdn.microsoft.com.  
  
-   Blog Eintrag [Erstellen von Paketen in Code Paket Konfigurationen](https://go.microsoft.com/fwlink/?LinkId=217663)auf www.sqlis.com.  
  
-   Blog Eintrag [API-Beispiel: Programm gesteuertes Hinzufügen einer Konfigurationsdatei zu einem Paket](https://go.microsoft.com/fwlink/?LinkId=217664)auf Blogs.msdn.com.  
  
  
