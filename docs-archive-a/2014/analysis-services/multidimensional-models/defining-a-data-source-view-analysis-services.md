---
title: Definieren einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- names [Analysis Services], data source views
- name matching criteria [Analysis Services]
- Data Source View Wizard
- data source views [Analysis Services], creating
ms.assetid: 0bae4ee4-1742-40e9-bebe-17c788854484
author: minewiskan
ms.author: owend
ms.openlocfilehash: 477504929c6e550dbdf17b6c27cd91ba030876ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622252"
---
# <a name="defining-a-data-source-view-analysis-services"></a>Definieren einer Datenquellensicht (Analysis Services)
  Eine Datenquellen Sicht enthält das logische Modell des Schemas, das von mehr [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimensionalen Datenbankobjekten verwendet wird, nämlich Cubes, Dimensionen und Mining Strukturen. Eine Datenquellensicht ist die im XML-Format gespeicherte Metadatendefinition dieser Schemaelemente, die vom UDM (Unified Dimensional Model) und von den Miningstrukturen verwendet werden. Eine Datenquellensicht:  
  
-   Enthält die Metadaten, die ausgewählte Objekte aus mindestens einer zugrunde liegenden Datenquelle darstellen bzw. die Metadaten, die zum Generieren eines zugrunde liegenden relationalen Datenspeichers verwendet werden, wenn zur Schemagenerierung der Top-Down-Ansatz verwendet wird.  
  
-   Kann für eine oder mehrere Datenquellen erstellt werden und ermöglicht Ihnen das Definieren von mehrdimensionalen Objekten und Data Mining-Objekten, die Daten aus mehreren Quellen integrieren.  
  
-   Kann Beziehungen, Primärschlüssel, Objektnamen, berechnete Spalten und Abfragen enthalten, die nicht in einer zugrunde liegenden Datenquelle und getrennt von den zugrunde liegenden Datenquellen vorhanden sind.  
  
-   Ist für Clientanwendungen nicht sichtbar bzw. kann von Clientanwendungen nicht abgerufen werden.  
  
 Eine Datenquellensicht ist eine erforderliche Komponente in einem mehrdimensionalen Modell. Die meisten Analysis Services-Entwickler erstellen eine Datenquellensicht in den Anfangsphasen des Modellentwurfs. Dabei generieren sie mindestens eine Datenquellensicht auf Grundlage einer externen relationalen Datenbank, die zugrunde liegende Daten bereitstellt. Sie können eine Datenquellensicht jedoch auch in einer späteren Phase erstellen und das Schema und die zugrunde liegenden Datenbankstrukturen nach der Erstellung der Dimensionen und Cubes generieren. Dieser zweite Ansatz wird mitunter Top-Down-Entwurf genannt und wird häufig für die Erstellung von Prototypen und die Analysemodellierung verwendet. Wenn Sie diesen Ansatz verwenden, können Sie mit dem Schemagenerierungs-Assistenten die zugrunde liegende Datenquellensicht und die Datenquellenobjekte erstellen, die auf den in einem Analysis Services-Projekt oder einer Analysis Services-Datenbank definierten OLAP-Objekten basieren. Unabhängig davon, wie und wann Sie eine Datenquellensicht erstellen, muss jedes Modell eine Datenquellensicht besitzen, bevor eine Verarbeitung möglich ist.  
  
 Dieses Thema enthält die folgenden Abschnitte:  
  
 [Zusammenstellung der Datenquellensicht](#bkmk_dsvdef)  
  
 [Erstellen einer Datenquellensicht mithilfe des Datenquellensicht-Assistenten](#bkmk_startWiz)  
  
 [Angeben von Namensübereinstimmungskriterien für Beziehungen](#bkmk_NameMatch)  
  
 [Hinzufügen einer sekundären Datenquelle](#bkmk_secondaryDS)  
  
##  <a name="data-source-view-composition"></a><a name="bkmk_dsvdef"></a>Komposition der Datenquellen Sicht  
 Eine Datenquellensicht enthält die folgenden Elemente:  
  
-   Einen Namen und eine Beschreibung.  
  
-   Eine Definition einer beliebigen Teilmenge des Schemas, die aus einer oder mehreren Datenquellen abgerufen wird, einschließlich des gesamten Schemas, das Folgendes umfasst:  
  
    -   Tabellennamen  
  
    -   Spaltennamen  
  
    -   Datentypen  
  
    -   NULL-Zulässigkeit  
  
    -   Spaltenlängen  
  
    -   Primärschlüssel  
  
    -   Primärschlüssel-Fremdschlüssel-Beziehungen  
  
-   Anmerkungen zum Schema aus den zugrunde liegenden Datenquellen, einschließlich der folgenden Angaben:  
  
    -   Anzeigenamen für Tabellen, Sichten und Spalten.  
  
    -   Benannte Abfragen, die Spalten aus einer oder mehreren Datenquellen zurückgeben (werden als Tabellen im Schema angezeigt).  
  
    -   Benannte Berechnungen, die Spalten aus einer Datenquelle zurückgeben (werden als Spalten in Tabellen oder Sichten angezeigt).  
  
    -   Logische Primärschlüssel (erforderlich, wenn kein Primärschlüssel in der zugrunde liegenden Tabelle definiert oder nicht in der Sicht oder benannten Abfrage eingeschlossen ist).  
  
    -   Logische Primärschlüssel-Fremdschlüssel-Beziehungen zwischen Tabellen, Sichten und benannten Abfragen.  
  
##  <a name="create-a-dsv-using-the-data-source-view-wizard"></a><a name="bkmk_startWiz"></a>Erstellen einer Datenquellen Sicht mithilfe des Datenquellen Sicht-Assistenten  
 Um eine Datenquellensicht zu erstellen, führen Sie den Datenquellensicht-Assistenten im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]aus.  
  
> [!NOTE]  
>  Alternativ können Sie zunächst Dimensionen und Cubes erstellen und anschließend mit dem Schemagenerierungs-Assistenten eine Datenquellensicht für das Modell generieren. Weitere Informationen finden Sie unter [Schemagenerierungs-Assistent &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md).  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner Datenquellensichten, und klicken Sie anschließend auf **Neue Datenquellensicht**.  
  
2.  Geben Sie ein neues oder ein vorhandenes Datenquellenobjekt an, das Verbindungsinformationen für eine externe relationale Datenbank bereitstellt (Sie können im Assistenten nur eine Datenquelle auswählen).  
  
3.  Klicken Sie auf derselben Seite auf **Erweitert** , um bestimmte Schemas auszuwählen, einen Filter anzuwenden oder um Informationen zu Tabellenbeziehungen auszuschließen.  
  
     **Schemas auswählen**  
  
     Bei sehr großen Datenquellen mit mehreren Schemas können Sie die zu verwendenden Schemas in einer durch Trennzeichen getrennten Liste (ohne Leerzeichen) auswählen.  
  
     **Beziehungen abrufen**  
  
     Sie können Informationen zu Tabellenbeziehungen absichtlich weglassen, indem Sie im Dialogfeld Erweiterte Optionen für Datenquellensicht das Kontrollkästchen **Beziehungen abrufen** deaktivieren. Nun können Sie manuell Beziehungen zwischen den Tabellen im Datenquellensicht-Designer erstellen.  
  
4.  **Filtern verfügbarer Objekte**  
  
     Wenn in der Liste Verfügbare Objekte eine Vielzahl von Objekten enthalten ist, können Sie die Liste durch einen einfachen Filter reduzieren, der eine Zeichenfolge als Auswahlkriterium angibt. Wenn Sie z. B. **dbo** eingeben und anschließend auf die Schaltfläche **Filter** klicken, werden nur die Elemente in der Liste **Verfügbare Objekte** angezeigt, die mit "dbo" beginnen. Der Filter kann eine partielle Zeichenfolge sein (z. b. "SAL" gibt Verkäufe und Gehalt zurück), kann aber nicht mehrere Zeichen folgen oder Operatoren enthalten.  
  
5.  Bei relationalen Datenquellen, für die keine Tabellenbeziehungen definiert sind, wird die Seite **Namensübereinstimmung** angezeigt, auf der Sie die geeignete Methode zum Abgleich von Namen auswählen können. Weitere Informationen finden Sie im Abschnitt [Angeben von Namensübereinstimmungskriterien für Beziehungen](#bkmk_NameMatch) in diesem Thema.  
  
##  <a name="add-a-secondary-data-source"></a><a name="bkmk_secondaryDS"></a>Hinzufügen einer sekundären Datenquelle  
 Wenn Sie eine Datenquellensicht definieren, die Tabellen, Sichten oder Spalten aus mehreren Datenquellen enthält, wird die erste Datenquelle, aus der Sie Objekte zur Datenquellensicht hinzufügen, als primäre Datenquelle festgelegt (nach der Definition der primären Datenquelle kann diese Festlegung nicht mehr geändert werden). Nachdem Sie eine Datenquellensicht basierend auf Objekten aus einer einzelnen Datenquelle definiert haben, können Sie Objekte aus anderen Datenquellen hinzufügen.  
  
 Wenn für eine OLAP-Verarbeitungs- oder eine Data Mining-Abfrage Daten aus mehreren Datenquellen in einer einzelnen Abfrage erforderlich sind, muss die primäre Datenquelle Remoteabfragen mithilfe von `OpenRowset` unterstützen. In der Regel handelt es sich dabei um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle. Wenn Sie beispielsweise eine OLAP-Dimension entwerfen, die Attribute enthält, die an Spalten aus mehreren Datenquellen gebunden sind, wird in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine `OpenRowset`-Abfrage erstellt, um diese Dimension währen der Verarbeitung aufzufüllen. Wenn die Auffüllung eines OLAP-Objekts oder die Auflösung einer Data Mining-Abfrage jedoch mithilfe einer einzelnen Datenquelle möglich ist, wird keine `OpenRowset`-Abfrage erstellt. In bestimmten Situationen kann es möglich sein, Attributbeziehungen zwischen Attributen zu definieren, sodass keine `OpenRowset`-Abfrage mehr erforderlich ist. Weitere Informationen zu Attributbeziehungen finden Sie unter [Attributbeziehungen](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md), [Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md) und [Definieren von Attributbeziehungen](attribute-relationships-define.md)aus.  
  
 Um Tabellen und Spalten aus einer zweiten Datenquelle hinzuzufügen, doppelklicken Sie im Projektmappen-Explorer auf die Datenquellensicht, um sie im Datenquellensicht-Designer zu öffnen und verwenden dann das Dialogfeld Tabellen hinzufügen/entfernen, um Objekte aus anderen im Projekt definierten Datenquellen einzuschließen. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellensicht &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)aus.  
  
##  <a name="specify-name-matching-criteria-for-relationships"></a><a name="bkmk_NameMatch"></a>Angeben von namens Übereinstimmungs Kriterien für Beziehungen  
 Wenn Sie eine Datenquellensicht erstellen, werden Beziehungen zwischen Tabellen erstellt, die auf FOREIGN KEY-Einschränkungen in der Datenquelle basieren. Diese Beziehungen sind erforderlich, damit die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Engine die geeigneten OLAP-Verarbeitungs- und Data Mining-Abfragen erstellen kann. Manchmal hat eine Datenquelle mit mehreren Tabellen keine FOREIGN KEY-Einschränkungen. Wenn eine Datenquelle nicht über FOREIGN KEY-Einschränkungen verfügt, werden Sie vom Datenquellensicht-Assistenten aufgefordert zu definieren, wie der Assistent Spaltennamen verschiedener Tabellen vergleichen soll.  
  
> [!NOTE]  
>  Sie werden nur dann aufgefordert, Namensübereinstimmungskriterien anzugeben, wenn in der zugrunde liegenden Datenquelle keine Fremdschlüsselbeziehungen erkannt werden. Wenn Fremdschlüsselbeziehungen erkannt werden, werden die gefundenen Beziehungen verwendet. Zusätzliche Beziehungen, die Sie in die Datenquellensicht einschließen möchten, einschließlich logischer Primärschlüssel, müssen manuell definiert werden. Weitere Informationen finden Sie unter [Definieren von logischen Beziehungen in einer Datenquellensicht &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md) und [Definieren logischer Primärschlüssel in einer Datenquellensicht &#40;Analysis Services&#41;](define-logical-primary-keys-in-a-data-source-view-analysis-services.md).  
  
 Der Datenquellensicht-Assistent verwendet Ihre Antwort, um Spaltennamen zu vergleichen und Beziehungen zwischen verschiedenen Tabellen in der Datenquellensicht zu erstellen. Sie können jedes beliebige Kriterium angeben, das in der folgenden Tabelle aufgeführt ist.  
  
|Namensübereinstimmungskriterien|BESCHREIBUNG|  
|----------------------------|-----------------|  
|**Gleicher Name wie Primärschlüssel**|Der Name der Fremdschlüsselspalte in der Quelltabelle stimmt mit dem Namen der Primärschlüsselspalte in der Zieltabelle überein. Beispielsweise ist die Fremdschlüsselspalte `Order.CustomerID` identisch mit der Primärschlüsselspalte `Customer.CustomerID`.|  
|**Gleicher Name wie Zieltabelle**|Der Name der Fremdschlüsselspalte in der Quelltabelle ist mit dem Namen der Zieltabelle identisch. Beispielsweise ist die Fremdschlüsselspalte `Order.Customer` identisch mit der Primärschlüsselspalte `Customer.CustomerID`.|  
|**Zieltabellenname und Primärschlüsselname**|Der Name der Fremdschlüsselspalte in der Quelltabelle ist identisch mit dem Zieltabellennamen, der mit dem Namen der Primärschlüsselspalte verkettet ist. Ein Leerzeichen oder Unterstrich als Trennzeichen ist zulässig. Beispielsweise stimmen die folgenden FOREIGN KEY-Primärschlüssel alle überein:<br /><br /> `Order.CustomerID` und `Customer.ID`<br /><br /> `Order.Customer ID` und `Customer.ID`<br /><br /> `Order.Customer_ID` und `Customer.ID`|  
  
 Durch die ausgewählten Kriterien wird die Einstellung der **NameMatchingCriteria** -Eigenschaft der Datenquellensicht geändert. Mit dieser Einstellung wird bestimmt, wie der Assistent verknüpfte Tabellen hinzufügt. Wenn Sie die Datenquellensicht mit dem Datenquellensicht-Designer ändern, legen Sie fest, wie die Spalten vom Designer abgeglichen werden, um Beziehungen zwischen Tabellen in der Datenquellensicht herzustellen. Sie können die Einstellung der **NameMatchingCriteria** -Eigenschaft im Datenquellensicht-Designer ändern. Weitere Informationen finden Sie unter [Ändern von Eigenschaften in einer Datenquellensicht &#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md).  
  
> [!NOTE]  
>  Nachdem Sie den Datenquellensicht-Assistenten fertig gestellt haben, können Sie Beziehungen im Schemabereich von Datenquellensicht-Designer hinzufügen oder entfernen. Weitere Informationen finden Sie unter [Definieren von logischen Beziehungen in einer Datenquellensicht &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Das Hinzufügen oder Entfernen von Tabellen oder Sichten in einer Datenquellen Sicht &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)   
 [Definieren logischer Primärschlüssel in einer Datenquellen Sicht &#40;Analysis Services&#41;](define-logical-primary-keys-in-a-data-source-view-analysis-services.md)   
 [Definieren Sie benannte Berechnungen in einer Datenquellen Sicht &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md)   
 [Definieren Sie benannte Abfragen in einer Datenquellen Sicht &#40;Analysis Services&#41;](define-named-queries-in-a-data-source-view-analysis-services.md)   
 [Ersetzen einer Tabelle oder einer benannten Abfrage in einer Datenquellen Sicht &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)   
 [Arbeiten mit Diagrammen im Datenquellen Sicht-Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)   
 [Durchsuchen von Daten in einer Datenquellen Sicht &#40;Analysis Services&#41;](explore-data-in-a-data-source-view-analysis-services.md)   
 [Löschen Sie eine Datenquellen Sicht &#40;Analysis Services&#41;](delete-a-data-source-view-analysis-services.md)   
 [Aktualisieren des Schemas in einer Datenquellensicht &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md)  
  
  
