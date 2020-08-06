---
title: Implementieren einer DataReader-Klasse für Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c9e55741c72d624b7149435ced90550135d8b4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87725273"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Implementieren einer DataReader-Klasse für Datenverarbeitungserweiterungen
  Mithilfe des **DataReader**-Objekts kann ein Client einen schreibgeschützten Vorwärtsdatenstrom von einer Datenquelle empfangen. Ergebnisse werden bei der Ausführung der Abfrage zurückgegeben und im Netzwerkpuffer auf dem Client gespeichert, bis Sie sie unter Verwendung der **Read**-Methode der **DataReader**-Klasse anfordern. Implementieren Sie <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> und optional <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>, um eine **DataReader**-Klasse zu erstellen. Die Verwendung eines **DataReader**-Objekts erhöht die Anwendungsleistung, da die Daten sofort bei Verfügbarkeit abgerufen werden, statt auf die gesamten Ergebnisse der Abfrage zu warten, und da (standardmäßig) immer nur eine Zeile im Speicher gespeichert wird. So wird der Systemverwaltungsaufwand reduziert.  
  
 Nachdem Sie eine Instanz der **Command**-Klasse erstellt haben, legen Sie ein **DataReader**-Objekt an, indem Sie **Command.ExecuteReader** aufrufen, um Zeilen von der Datenquelle abzurufen. Die **DataReader**-Implementierung muss über zwei grundlegende Funktionen verfügen: Vorwärtszugriff auf die Resultsets, die durch die Ausführung eines Befehls abgerufen wurden, und Zugriff auf die Spaltentypen, Namen und Werte innerhalb jeder Zeile. Clients verwenden die **Read**-Methode des **DataReader**-Objekts, um eine Zeile aus den Ergebnissen der Abfrage abzurufen.  
  
 Im Berichts-Designer werden mithilfe des **DataReader**-Objekts eine Liste der Felder sowie Schemainformationen zur Ergebnisreihe abgerufen. Hierzu müssen die Methoden **GetName**, **GetValue**, **GetFieldType,** und **GetOrdinal** der <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>-Schnittstelle implementiert werden.  
  
 Mit der <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>-Schnittstelle können Sie bestimmte Aggregationsinformationen über das Resultset angeben. Eine Beispiel-**DataReader**-Klassenimplementierung finden Sie unter [SQL Server Reporting Services Product Samples (SQL Server Reporting Services-Produktbeispiele)](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
