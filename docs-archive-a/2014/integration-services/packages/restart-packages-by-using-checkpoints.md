---
title: Neustarten von Paketen mit Prüfpunkten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 48f2fbb7-8964-484a-8311-5126cf594bfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa0e0e9ad1da67bfc70dec61396ab026df62d3ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87619190"
---
# <a name="restart-packages-by-using-checkpoints"></a>Neustarten von Paketen mit Prüfpunkten
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] können fehlerhafte Pakete an dem Punkt neu gestartet werden, an dem der Fehler aufgetreten ist. Sie brauchen also nicht noch einmal vollständig ausgeführt werden. Wenn ein Paket zum Verwenden von Prüfpunkten konfiguriert ist, werden Informationen zur Ausführung des Pakets in eine Prüfpunktdatei geschrieben. Wenn das fehlerhafte Paket erneut ausgeführt wird, wird die Prüfpunktdatei verwendet, um das Paket von dem Punkt aus, an dem der Fehler aufgetreten ist, auszuführen. Wenn das Paket erfolgreich ausgeführt wird, wird die Prüfpunktdatei gelöscht und beim nächsten Ausführen des Pakets neu erstellt.  
  
 Das Verwenden von Prüfpunkten in einem Paket bietet die folgenden Vorteile:  
  
-   Vermeiden von wiederholten Download- und Uploadvorgängen für umfangreiche Dateien. Beispielsweise kann ein Paket, das mehrere umfangreiche Dateien mithilfe je eines FTP-Tasks herunterlädt, nach dem Herunterladen einer einzigen fehlerhaften Datei neu gestartet werden und anschließend nur diese eine Datei erneut herunterladen.  
  
-   Vermeiden, dass große Datenmengen wiederholt geladen werden müssen. Beispielsweise kann ein Paket, das mithilfe von einzelnen Masseneinfügungstasks Masseneinfügungen in Dimensionstabellen in einem Data Warehouse ausführt, neu gestartet werden, wenn eine Einfügung für eine einzige Dimensionstabelle einen Fehler auslöst. Anschließend braucht nur die fehlerhafte Dimension erneut geladen werden.  
  
-   Vermeiden wiederholter Wertaggregationen. Beispielsweise kann ein Paket, das mithilfe von einzelnen Datenflusstasks zahlreiche verschiedene Aggregate berechnet, wie z. B. Mittelwerte oder Summen, neu gestartet werden, nachdem die Berechnung einer einzigen Aggregation einen Fehler auslöst. Anschließend braucht nur die fehlerhafte Aggregation neu berechnet werden.  
  
 Wenn ein Paket für das Verwenden von Prüfpunkten konfiguriert ist, zeichnet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] den Punkt, an dem neu gestartet werden soll, in der Prüfpunktdatei auf. Der in der Prüfpunktdatei aufgezeichnete Punkt, an dem neu gestartet werden soll, ist vom Typ des fehlerhaften Containers und der Implementierung von Funktionen wie z. B. Transaktionen abhängig. Die aktuellen Werte von Variablen werden ebenfalls in der Prüfpunktdatei erfasst. Die Werte von Variablen mit dem `Object`-Datentyp werden jedoch nicht in Prüfpunktdateien gespeichert.  
  
## <a name="defining-restart-points"></a>Definieren von Prüfpunkten, an denen neu gestartet wird  
 Die kleinste atomare Arbeitseinheit, die neu gestartet werden kann, ist der Taskhostcontainer, der einen einzelnen Task kapselt. Der Foreach-Schleifencontainer und der Transaktionscontainer werden ebenfalls als atomare Arbeitseinheiten behandelt.  
  
 Wenn ein Paket während des Ausführens eines Transaktionscontainers beendet wird, wird auch die Transaktion beendet, und für alle eventuell durch den Container ausgeführten Vorgänge wird ein Rollback ausgeführt. Beim Neustarten des Pakets wird der fehlerhafte Container erneut ausgeführt. Das Abschließen eventuell vorhandener untergeordneter Container in Transaktionscontainern wird nicht in der Prüfpunktdatei aufgezeichnet. Daher werden beim Neustarten des Pakets sowohl der Transaktionscontainer als auch seine untergeordneten Container erneut ausgeführt.  
  
> [!NOTE]  
>  Das Verwenden von Prüfpunkten und Transaktionen im gleichen Paket könnte unerwartete Ergebnisse verursachen. Wenn beispielsweise ein Paket einen Fehler verursacht und von einem Prüfpunkt neu startet, wiederholt das Paket möglicherweise eine Transaktion, die bereits erfolgreich ausgeführt wurde.  
  
 Für For- und Foreach-Schleifencontainer werden keine Prüfpunktdaten gespeichert. Beim Neustart eines Pakets werden sowohl For- und Foreach-Schleifencontainer als auch deren untergeordnete Container erneut ausgeführt. Wenn ein untergeordneter Container einer Schleife erfolgreich ausgeführt wurde, wird er nicht in der Prüfpunktdatei aufgezeichnet, sondern erneut ausgeführt. Weitere Informationen und eine Umgehungslösung finden Sie unter [SSIS-Prüfpunkte werden bei Elementen von For- und Foreach-Schleifencontainern nicht berücksichtigt](https://go.microsoft.com/fwlink/?LinkId=241633).  
  
 Beim Neustarten des Pakets werden die Paketkonfigurationen nicht erneut geladen; stattdessen verwendet das Paket die Konfigurationsinformationen der Prüfpunktdatei. Auf diese Weise wird sichergestellt, dass das Paket beim erneuten Ausführen wie beim ursprünglichen (fehlerhaften) Ausführen dieselben Konfigurationen verwendet.  
  
 Ein Paket kann nur auf der Ablaufsteuerungsebene neu gestartet werden. Sie können ein Paket also nicht mitten in einem Datenfluss neu starten. Um zu vermeiden, dass der gesamte Datenfluss erneut ausgeführt werden muss, können Sie beim Entwerfen des Pakets mehrere Datenflüsse planen, die jeweils einen bestimmten Datenflusstask verwenden. Auf diese Weise kann das Paket neu gestartet werden und dabei nur einen Datenflusstask erneut ausführen.  
  
## <a name="configuring-a-package-to-restart"></a>Konfigurieren des Neustarts eines Pakets  
 Die Prüfpunktdatei enthält das Ausführungsergebnis aller abgeschlossenen Container, die aktuellen Werte der benutzerdefinierten und der Systemvariablen, sowie Paketkonfigurationsinformationen. Die Datei enthält außerdem den eindeutigen Bezeichner des Pakets. Der Paketbezeichner in der Prüfpunktdatei muss mit dem des Pakets übereinstimmen, damit das Paket neu gestartet werden kann. Anderenfalls tritt beim Neustarten ein Fehler auf. Auf diese Weise wird vermieden, dass ein Paket eine Prüfpunktdatei verwendet, die von einer anderen Paketversion geschrieben wurde. Wenn das Paket nach dem Neustarten erfolgreich ausgeführt wird, wird die Prüfpunktdatei gelöscht.  
  
 In der folgenden Tabelle sind die Paketeigenschaften aufgeführt, die Sie zum Implementieren von Prüfpunkten festlegen können.  
  
|Eigenschaft|BESCHREIBUNG|  
|--------------|-----------------|  
|CheckpointFileName|Gibt den Namen der Prüfpunktdatei an.|  
|CheckpointUsage|Gibt an, ob Prüfpunkte verwendet werden.|  
|SaveCheckpoints|Gibt an, ob das Paket Prüfpunkte speichert. Diese Eigenschaft muss auf True festgelegt sein, damit ein Paket an dem Punkt neu gestartet wird, an dem ein Fehler aufgetreten ist.|  
  
 Außerdem müssen Sie die FailPackageOnFailure-Eigenschaft auf `true` für alle Container im Paket festlegen, die als Neustart Punkte identifiziert werden sollen.  
  
 Mit der ForceExecutionResult-Eigenschaft können Sie die Verwendung der Prüfpunkte eines Pakets testen. Sie können einen Echtzeitfehler imitieren, indem Sie die ForceExecutionResult-Eigenschaft eines Tasks oder eines Containers auf Failure festlegen. Wenn Sie das Paket erneut ausführen, werden der fehlerhafte Task bzw. die fehlerhaften Container erneut ausgeführt.  
  
### <a name="checkpoint-usage"></a>Syntax von Prüfpunkten  
 Die CheckpointUsage-Eigenschaft kann auf die folgenden Werte festgelegt werden:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|`Never`|Gibt an, dass die Prüfpunktdatei nicht verwendet wird und dass das Paket vom Beginn des Paketworkflows aus ausgeführt wird.|  
|`Always`|Gibt an, dass die Prüfpunktdatei immer verwendet wird und dass das Paket von dem Punkt aus neu gestartet wird, an dem bei der letzten Ausführung ein Fehler aufgetreten ist. Wenn die Prüfpunktdatei nicht gefunden wird, schlägt das Paket fehl.|  
|`IfExists`|Gibt an, dass die Prüfpunktdatei verwendet wird, falls sie vorhanden ist. Wenn die Prüfpunktdatei vorhanden ist, wird das Paket an dem Punkt neu gestartet, an dem bei der letzten Ausführung ein Fehler aufgetreten ist; anderenfalls wird das Paket vom Beginn des Paketworkflows aus ausgeführt.|  
  
> [!NOTE]  
>  Die **/CheckPointing on** -Option von dtexec entspricht dem Festlegen der `SaveCheckpoints` -Eigenschaft des Pakets auf `True` und der- `CheckpointUsage` Eigenschaft auf Always. Weitere Informationen finden Sie [hier](dtexec-utility.md).  
  
## <a name="securing-checkpoint-files"></a>Sichern von Prüfpunktdateien  
 Der Schutz auf Paketebene schließt nicht den Schutz von Prüfpunktdateien ein. Daher müssen diese Dateien separat gesichert werden. Prüfpunktdaten können nur im Dateisystem gespeichert werden. Sie sollten daher eine Zugriffssteuerungsliste (ACL, Access Control List) des Betriebssystems verwenden, um den Speicherort der Datei bzw. den Ordner, in dem die Datei gespeichert wird, zu sichern. Prüfpunktdateien sollten unbedingt gesichert werden, da sie Informationen zum Paketstatus enthalten, einschließlich der aktuellen Variablenwerte. Beispielsweise kann eine Variable ein Recordset mit mehreren Zeilen privater Daten, wie z. B. Telefonnummern, enthalten. Weitere Informationen finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../access-to-files-used-by-packages.md).  
  
### <a name="to-configure-the-checkpoint-properties"></a>So konfigurieren Sie die Prüfpunkteigenschaften  
  
-   [Konfigurieren von Prüfpunkten zum erneuten Starten eines fehlerhaften Pakets](../configure-checkpoints-for-restarting-a-failed-package.md)  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Technischer Artikel [Automatischer Neustart von SSIS-Paketen nach Failover oder Fehler](https://go.microsoft.com/fwlink/?LinkId=200407)auf social.technet.microsoft.com.  
  
-   Support-Artikel [SSIS-Prüfpunkte werden bei Elementen von For- und Foreach-Schleifencontainern nicht berücksichtigt](https://go.microsoft.com/fwlink/?LinkId=241633)auf support.microsoft.com.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
