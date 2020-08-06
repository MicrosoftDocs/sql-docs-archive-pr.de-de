---
title: Anforderungen an den benutzerdefinierten Typ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4e692a4523829713cd95daf62374f84a74b6584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87609918"
---
# <a name="user-defined-type-requirements"></a>Anforderungen für den benutzerdefinierten Typ
  Beim Erstellen eines benutzerdefinierten Typs (User-Defined Type, UDT), der in installiert werden soll, müssen Sie einige wichtige Entwurfsentscheidungen treffen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Für die meisten UDTs wird das Erstellen als Struktur empfohlen, obwohl auch das Erstellen als Klasse möglich ist. Die UDT-Definition muss den Spezifikationen für das Erstellen von UDTs entsprechen, um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden zu können.  
  
## <a name="requirements-for-implementing-udts"></a>Anforderungen für das Implementieren von UDTs  
 Um in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt zu werden, muss der UDT die folgenden Anforderungen in der UDT-Definition implementieren:  
  
 Der UDT muss das `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` angeben. Die Verwendung des `System.SerializableAttribute`-Schlüsselworts ist optional, wird aber empfohlen.  
  
-   Der UDT muss die `System.Data.SqlTypes.INullable`-Schnittstelle in der Klasse oder Struktur implementieren, indem er eine öffentliche `static` (`Shared` in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) `Null`-Methode erstellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt standardmäßig NULL-Werte. Dies ist notwendig für Code, der im UDT ausgeführt wird, um in der Lage zu sein, einen NULL-Wert zu erkennen.  
  
-   Der UDT muss eine öffentliche `static` (oder `Shared`) `Parse`-Methode enthalten, die Analysen unterstützt, sowie eine öffentliche `ToString`-Methode für das Konvertieren in eine Zeichenfolgendarstellung des Objekts.  
  
-   Ein UDT mit benutzerdefiniertem Serialisierungsformat muss die `System.Data.IBinarySerialize`-Schnittstelle implementieren und eine `Read`- sowie eine `Write`-Methode bereitstellen.  
  
-   Der UDT muss `System.Xml.Serialization.IXmlSerializable` implementieren. Andernfalls müssen alle öffentlichen Felder und Eigenschaften Typen entsprechen, die durch XML serialisierbar sind oder das `XmlIgnore`-Attribut erhalten, wenn das Überschreiben einer Standardserialisierung erforderlich ist.  
  
-   Es darf nur eine Serialisierung eines UDT-Objekts geben. Die Überprüfung schlägt fehl, wenn die Serialisierungs- oder Deserialisierungsroutinen mehr als eine Darstellung eines bestimmten Objekts erkennen.  
  
-   `SqlUserDefinedTypeAttribute.IsByteOrdered` muss `true` sein, um Daten in Bytereihenfolge zu vergleichen. Wenn die IComparable-Schnittstelle nicht implementiert ist und `SqlUserDefinedTypeAttribute.IsByteOrdered` den Wert `false` hat, schlagen Vergleiche in Bytereihenfolge fehl.  
  
-   Ein in einer Klasse definierter UDT muss über einen öffentlichen Konstruktor verfügen, der keine Argumente verwendet. Sie können optional zusätzliche überladene Klassenkonstruktoren erstellen.  
  
-   Der UDT muss Datenelemente als öffentliche Felder oder Eigenschaftenprozeduren verfügbar machen.  
  
-   Öffentliche Namen dürfen nicht länger als 128 Zeichen sein, und Sie müssen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benennungs Regeln für Bezeichner entsprechen, wie in [Daten Bank bezeichnerdaten](../databases/database-identifiers.md)definiert.  
  
-   `sql_variant`-Spalten können keine Instanzen eines UDTs enthalten.  
  
-   Auf vererbte Member kann nicht von [!INCLUDE[tsql](../../includes/tsql-md.md)] aus zugegriffen werden, da das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typsystem die Vererbungshierarchie zwischen UDTs nicht kennt. Sie können Vererbung allerdings verwenden, wenn Sie Klassen strukturieren, und Sie können diese Methoden in der verwalteten Codeimplementierung des Typs aufrufen.  
  
-   Mit Ausnahme des Klassenkonstruktors können Member nicht überladen werden. Wenn Sie eine überladene Methode erstellen, wird kein Fehler ausgelöst, wenn Sie die Assembly registrieren oder den Typ in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen Erkennung der überladenen Methode tritt zur Laufzeit auf, nicht beim Erstellen des Typs. Überladene Methoden können in der Klasse vorhanden sein, solange sie nie aufgerufen werden. Sobald Sie eine überladene Methode aufrufen, wird ein Fehler ausgelöst.  
  
-   Alle `static`- oder `Shared`-Member müssen als Konstanten oder als schreibgeschützt deklariert werden. Statische Member können nicht änderbar sein.  
  
-   Wenn das `SqlUserDefinedTypeAttribute.MaxByteSize`-Feld auf -1 festgelegt wurde, kann die serialisierte UDT so groß wir die Größenbeschränkung für große Objekte (LOB, Large Object) sein (zurzeit 2 GB). Die Größe des UDTs kann den im `MaxByteSized`-Feld angegebenen Wert nicht überschreiten.  
  
> [!NOTE]  
>  Obwohl sie vom Server zum Durchführen von Vergleichen nicht verwendet wird, können Sie optional die `System.IComparable`-Schnittstelle implementieren, die eine einzelne Methode, nämlich `CompareTo`, bereitstellt Diese Methode wird auf Clientseite in Situationen verwendet, in denen UDT-Werte präzise verglichen oder geordnet werden sollen.  
  
## <a name="native-serialization"></a>Systemeigene Serialisierung  
 Die Auswahl der richtigen Serialisierungsattribute für den UDT hängt vom Typ des UDTs ab, den Sie erstellen möchten. Für das `Native`-Serialisierungsformat wird eine sehr einfache Struktur verwendet, die es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht, eine effiziente systemeigene Darstellung des UDTs auf dem Datenträger zu speichern. Das `Native`-Format wird empfohlen, wenn der UDT einfach ist und nur Felder der folgenden Typen enthält:  
  
 **bool**, **Byte**, **SByte**, **Short**, **UShort**, **int**, **uint**, **Long**, **ulong**, **float**, **Double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Werttypen, die aus Feldern der oben genannten Typen bestehen, sind gute Kandidaten für `Native` das Format, z `structs` . b. in Visual c# (oder `Structures` in Visual Basic). Ein UDT, der mit dem `Native`-Serialisierungsformat angegeben wurde, kann z. B. ein Feld eines anderen UDTs enthalten, das auch mit dem `Native`-Format angegeben wurde. Wenn die UDT-Definition komplexer ist und Datentypen enthält, die nicht aus der Liste oben stammen, müssen Sie stattdessen das `UserDefined`-Serialisierungsformat angeben.  
  
 Für das `Native`-Format müssen die folgenden Anforderungen erfüllt sein:  
  
-   Der Typ darf für `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize` keinen Wert angeben.  
  
-   Alle Felder müssen serialisierbar sein.  
  
-   `System.Runtime.InteropServices.StructLayoutAttribute` muss als `StructLayout.LayoutKindSequential` angegeben werden, wenn der UDT in einer Klasse und nicht in einer Struktur definiert wird. Dieses Attribut steuert das physische Layout der Datenfelder und wird verwendet, um zu erzwingen, dass die Elemente in der Reihenfolge angeordnet werden, in der sie erscheinen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmt anhand dieses Attributs die Feldreihenfolge für UDTs mit mehreren Werten.  
  
 Ein Beispiel für einen UDT, der mit `Native` der Serialisierung definiert wird, finden Sie unter Point UDT beim [Codieren von benutzerdefinierten Typen](creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>UserDefined-Serialisierung  
 Die `UserDefined`-Formateinstellung für das `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`-Attribut gibt dem Entwickler volle Kontrolle über das Binärformat. Wenn Sie die `Format`-Attributeigenschaft als `UserDefined` angeben, müssen Sie im Code wie folgt vorgehen:  
  
-   Geben Sie die optionale `IsByteOrdered`-Attributeigenschaft an. Standardwert: `false`.  
  
-   Geben Sie die `MaxByteSize`-Eigenschaft von `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` an.  
  
-   Schreiben Sie Code, um die `Read`- und die `Write`-Methode für den UDT zu implementieren, indem Sie die `System.Data.Sql.IBinarySerialize`-Schnittstelle implementieren.  
  
 Ein Beispiel für einen UDT, der mit `UserDefined` der Serialisierung definiert wird, finden Sie im Currency UDT unter [Programmieren benutzerdefinierter Typen](creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Für UDT-Felder muss die systemeigene Serialisierung verwendet werden, oder die Felder müssen erhalten bleiben, um indiziert zu werden.  
  
## <a name="serialization-attributes"></a>Serialisierungsattribute  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen. Beim Erstellen des UDTs ist es erforderlich, das `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` anzugeben. Das `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`-Attribut gibt an, dass die Klasse ein UDT ist, und gibt den Speicher für den UDT an. Sie können das `Serializable`-Attribut optional angeben, obwohl [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dieses nicht erfordert.  
  
 Das `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` verfügt über folgende Eigenschaften.  
  
 `Format`  
 Gibt das Serialisierungsformat an, das je nach den Datentypen des UDTs `Native` oder `UserDefined` sein kann.  
  
 `IsByteOrdered`  
 Ein `Boolean`-Wert, der bestimmt, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binäre Vergleiche für den UDT durchführt.  
  
 `IsFixedLength`  
 Gibt an, ob alle Instanzen dieses UDTs dieselbe Länge haben.  
  
 `MaxByteSize`  
 Die maximale Größe der Instanz in Byte. Sie müssen die `MaxByteSize` mit dem `UserDefined`-Serialisierungsformat angeben. Bei einem UDT, für den benutzerdefinierte Serialisierung festgelegt ist, bezieht sich `MaxByteSize` auf die Gesamtgröße des UDTs in der vom Benutzer festgelegten serialisierten Form. Der Wert von `MaxByteSize` muss zwischen 1 und 8000 liegen oder auf -1 festgelegt werden, um anzugeben, dass der UDT größer als 8000 Byte ist (die Gesamtgröße kann die maximale LOB-Größe nicht übersteigen). Angenommen, für einen UDT ist eine Zeichenfolge von 10 Zeichen (`System.Char`) festgelegt. Wenn der UDT anhand eines BinaryWriter serialisiert wird, beträgt die Gesamtgröße der serialisierten Zeichenfolge 22 Byte: 2 Byte pro Unicode-UTF-16-Zeichen, multipliziert mit der maximalen Anzahl von Zeichen, plus 2 Kontrollzeichen, die beim Serialisieren eines binären Datenstroms zusätzlich anfallen. Bei der Ermittlung des `MaxByteSize`-Werts muss daher die Gesamtgröße des serialisierten UDTs berücksichtigt werden: die Größe der ins Binärformat serialisierten Daten plus die bei der Serialisierung anfallenden Daten.  
  
 `ValidationMethodName`  
 Der Name der Methode, mit der Instanzen des UDTs überprüft werden.  
  
### <a name="setting-isbyteordered"></a>Einstellung 'IsByteOrdered'  
 Wenn die `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered`-Eigenschaft auf `true` festgelegt wird, gewährleisten Sie damit, dass die serialisierten Binärdaten für eine semantische Sortierung der Informationen verwendet werden können. So kann jede Instanz eines UDT-Objekts mit Bytereihenfolge nur eine einzige serialisierte Darstellung haben. Die Ausführung eines Vergleichsvorgangs für die serialisierten Bytes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte zu denselben Resultaten führen wie der entsprechende Vergleichsvorgang für verwalteten Code. Die folgenden Funktionen werden ebenfalls unterstützt, wenn `IsByteOrdered` auf `true` festgelegt ist:  
  
-   Die Fähigkeit zum Erstellen von Indizes für Spalten dieses Typs  
  
-   Die Fähigkeit, für Spalten dieses Typs Primär- und Fremdschlüssel sowie die Einschränkungen CHECK und UNIQUE zu erstellen  
  
-   Die Fähigkeit, [!INCLUDE[tsql](../../includes/tsql-md.md)]-ORDER BY-, GROUP BY- und PARTITION BY-Klauseln zu verwenden. In diesen Fällen wird die binäre Darstellung des Typs verwendet, um die Reihenfolge zu bestimmen  
  
-   Die Fähigkeit, Vergleichsoperatoren in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen zu verwenden  
  
-   Die Fähigkeit, berechnete Spalten dieses Typs persistent zu speichern  
  
 Beachten Sie, dass sowohl das `Native`-Serialisierungsformat als auch das `UserDefined`-Serialisierungsformat die folgenden Vergleichsoperatoren unterstützen, wenn `IsByteOrdered` auf `true` festgelegt ist:  
  
-   Gleich (=)  
  
-   Ungleich (!=)  
  
-   Größer als (>)  
  
-   Kleiner als (\<)  
  
-   Größer als oder gleich (>=)  
  
-   Kleiner oder gleich (<=)  
  
### <a name="implementing-nullability"></a>Implementieren von NULL-Zulässigkeit  
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss die Klasse auch NULL-Zulässigkeit unterstützen. UDTs, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen werden, erkennen Nullwerte, aber damit der UDT einen Nullwert erkennt, muss die Klasse die `INullable`-Schnittstelle implementieren. Weitere Informationen und ein Beispiel für die Implementierung der NULL-Zulässigkeit in einem UDT finden Sie unter Programmieren von [benutzerdefinierten Typen](creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Zeichenfolgenkonvertierungen  
 Zum Unterstützen der Zeichenfolgenkonvertierung in und aus UDTs müssen Sie in der Klasse eine `Parse`-Methode und eine `ToString`-Methode angeben. Die `Parse`-Methode lässt das Konvertieren einer Zeichenfolge in einen UDT zu. Die Zeichenfolge muss als `static` (oder `Shared` in Visual Basic) deklariert werden und einen Parameter vom Typ `System.Data.SqlTypes.SqlString` verwenden. Weitere Informationen und ein Beispiel für die Implementierung der `Parse` -Methode und der- `ToString` Methode finden Sie unter [Programmieren benutzerdefinierter Typen](creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>XML-Serialisierung  
 UDTs müssen die Konvertierung in und aus `xml`-Daten unterstützen, indem sie dem Vertrag für die XML-Serialisierung entsprechen. Der `System.Xml.Serialization`-Namespace enthält Klassen, die zum Serialisieren von Objekten in Dokumente oder Streams im XML-Format verwendet werden. Sie können die `xml`-Serialisierung mithilfe der `IXmlSerializable`-Schnittstelle implementieren, die das benutzerdefinierte Formatieren für die XML-Serialisierung und -Deserialisierung bereitstellt.  
  
 Zusätzlich zum Durchführen expliziter Konvertierungen von UDT in `xml` ermöglicht die XML-Serialisierung Folgendes:  
  
-   Verwenden von `Xquery` für Werte von UDT-Instanzen nach der Konvertierung in den `xml`-Datentyp.  
  
-   Verwenden von UDTs in parametrisierten Abfragen und Webmethoden mit systemeigenen XML-Webdiensten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Verwenden von UDTs, um ein Massenladen von XML-Daten durchzuführen.  
  
-   Serialisieren von DataSets, die Tabellen mit UDT-Spalten enthalten.  
  
 UDTs werden nicht in FOR XML-Abfragen serialisiert. Um eine FOR XML-Abfrage auszuführen, die die XML-Serialisierung von UDTs anzeigt, konvertieren Sie die einzelnen UDT-Spalten explizit in den `xml`-Datentyp in der SELECT-Anweisung. Sie können die Spalten auch explizit in `varbinary`, `varchar` oder `nvarchar` konvertieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Typs](creating-user-defined-types.md)  
  
  
