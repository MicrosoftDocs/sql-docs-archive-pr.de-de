---
title: Konfigurieren von SQL Server für die Verwendung von Soft-NUMA (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- non-uniform memory access
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 731ddbf67450c917387df7e104d138c0b35df2d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622877"
---
# <a name="configure-sql-server-to-use-soft-numa-sql-server"></a>Konfigurieren von SQL Server zur Verwendung von Soft-NUMA (SQL Server)
Moderne Prozessoren verfügen über mehrere bis viele Kerne pro Socket. Jeder Socket wird in der Regel als ein einzelner NUMA-Knoten dargestellt. Die SQL Server-Datenbank-Engine partitioniert pro NUMA-Knoten verschiedene interne Strukturen und Dienstthreads für Partitionen. Bei Prozessoren, die 10 oder mehr Kerne pro Socket enthalten, erhöht die Verwendung von Software NUMA (Soft-NUMA) zum Aufteilen von Hardware-NUMA-Knoten in der Regel die Skalierbarkeit und Leistung.   

> [!NOTE]
> Hot-Add-Prozessoren werden von Soft-NUMA nicht unterstützt.
  
## <a name="automatic-soft-numa"></a>Automatischer Soft-NUMA
Ab SQL Server 2014 Service Pack 2 werden die Soft-NUMA-Knoten automatisch erstellt, wenn das Ablaufverfolgungsflag 8079 als Startparameter aktiviert ist, wenn der Datenbank-Engine-Server mehr als acht physische Prozessoren beim Start erkennt. Beim zählen physischer Prozessoren werden keine hyperthreadprozessor-Kerne berücksichtigt. Wenn die Anzahl der erkannten physischen Prozessoren mehr als 8 pro Socket beträgt, erstellt der Datenbank-Engine-Dienst Soft-NUMA-Knoten, die im Idealfall 8 Kerne enthalten, aber auf bis zu 9 logische Prozessoren pro Knoten zurückgreifen können. Die Größe des Hardwareknotens kann durch eine CPU-Affinitätsmaske eingeschränkt werden. Die Anzahl von NUMA-Knoten wird nie die maximale Anzahl von unterstützten NUMA-Knoten übersteigen.

Ohne das Ablaufverfolgungsflag ist Soft-NUMA standardmäßig deaktiviert. Sie können Soft-NUMA mithilfe des Ablaufverfolgungsflags 8079 aktivieren. Nach der Änderung des Werts dieser Einstellung ist ein Neustart der Datenbank-Engine erforderlich, damit diese wirksam wird.

Die folgende Abbildung zeigt den Typ von Informationen zu Soft-NUMA, die im SQL Server-Fehlerprotokoll angezeigt werden, wenn SQL Server Hardware-NUMA-Knoten mit mehr als acht logischen Prozessoren erkennt und das Ablaufverfolgungsflag 8079 aktiviert ist.

![Soft-NUMA](./media/soft-numa-sql-server/soft-numa.PNG)

> [!NOTE]
> Beginnend mit SQL Server 2016 wird dieses Verhalten durch die Engine gesteuert, und das Ablaufverfolgungsflag 8079 hat keine Auswirkungen.

## <a name="manual-soft-numa"></a>Manueller Soft-NUMA
  
Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie für die manuelle Verwendung von Soft-NUMA konfigurieren möchten, müssen Sie die Registrierung bearbeiten, um eine Affinitäts Maske für die Knoten Konfiguration hinzuzufügen. Die Soft-NUMA-Maske kann als binärer Eintrag, als DWORD-Registrierungseintrag (hexadezimal oder dezimal) oder als QWORD-Registrierungseintrag (hexadezimal oder dezimal) angegeben werden. Verwenden Sie QWORD- oder BINARY-Registrierungseinträge, um mehr als die ersten 32 CPUs zu konfigurieren. (QWord-Werte können vor nicht verwendet werden [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .) Sie müssen neu starten [!INCLUDE[ssDE](../../includes/ssde-md.md)] , um Soft-NUMA zu konfigurieren.  
  
> [!TIP]  
>  Die Nummerierung der CPUs beginnt mit 0.  
  
 [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Betrachten Sie das folgende Beispiel. Ein Computer mit acht CPUs verfügt über keine NUMA-Hardware. Drei Soft-NUMA-Knoten werden konfiguriert. [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz A wird für die Verwendung der CPUs 0 bis 3 konfiguriert. Eine zweite [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz wird installiert und für die Verwendung der CPUs 4 bis 7 konfiguriert. Das Beispiel kann wie folgt visuell dargestellt werden:  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 Instanz A, auf der ein hohes Maß an E/A-Aktivität stattfindet, verfügt nun über zwei E/A-Threads und einen Thread für LAZY WRITER-Prozesse (verzögertes Schreiben), während Instanz B, auf der prozessorintensive Vorgänge ausgeführt werden, nur über einen E/A-Thread und einen Thread für LAZY WRITER-Prozesse verfügt. Den Instanzen können zwar unterschiedliche Mengen an Arbeitsspeicher zugewiesen werden, aber im Unterschied zu Hardware-NUMA erhalten beide Instanzen den Arbeitsspeicher aus demselben Betriebssystem-Speicherblock und es ist keine Speicher-Prozessor-Affinität vorhanden.  
  
 Der LAZY WRITER-Thread ist an die SQL OS-Sicht der physischen NUMA-Arbeitsspeicherknoten gebunden. Daher entsprechen die physischen NUMA-Knoten der Hardware der Anzahl der erstellten LAZY WRITER-Threads. Weitere Informationen finden Sie unter [How It Works: Soft NUMA, I/O Completion Thread, Lazy Writer Workers and Memory Nodes](https://docs.microsoft.com/archive/blogs/psssql/how-it-works-soft-numa-io-completion-thread-lazy-writer-workers-and-memory-nodes)(Vorgehensweise: Soft-NUMA, E/A-Abschlussthreads, LAZY WRITER-Worker- und Arbeitsspeicherknoten).  
  
> [!NOTE]  
>  Die **Soft-NUMA** -Registrierungsschlüssel werden nicht kopiert, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Festlegen der CPU-Affinitätsmaske  
  
1.  Führen Sie auf Instanz A die folgende Anweisung aus, um die Instanz durch Festlegen der CPU-Affinitätsmaske für die Verwendung der CPUs 0, 1, 2 und 3 zu konfigurieren:  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=0 TO 3;  
    ```  
  
2.  Führen Sie auf Instanz B die folgende Anweisung aus, um die Instanz durch Festlegen der CPU-Affinitätsmaske für die Verwendung der CPUs 4, 5, 6 und 7 zu konfigurieren:  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=4 TO 7;  
    ```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Zuordnen von Soft-NUMA-Knoten zu den CPUs  
  
-   Fügen Sie mithilfe des Registrierungs-Editors (regedit.exe) die folgenden Registrierungsschlüssel hinzu, um den CPUs 0 und 1 den Soft-NUMA-Knoten 0, den CPUs 2 und 3 den Soft-NUMA-Knoten 1 und den CPUs 4, 5, 6 und 7 den Soft-NUMA-Knoten 2 zuzuordnen.  
  
     Legen Sie für das folgende Beispiel einen DL580 G9-Server mit 18 Kernen pro Fassung (in 4 Fassungen) zugrunde, wobei jede Fassung eine eigene K-Gruppe darstellt. Eine Soft-NUMA-Konfiguration, die Sie dafür erstellen, könnte etwa so aussehen. (6 Kerne pro Knoten, 3 Knoten pro Gruppe, 4 Gruppen).  
  
    |Beispiel für einen [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] -Server mit mehreren K-Gruppen|type|Wertname|Wertdaten|  
    |------------------------------------------------------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|Group|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|Group|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|Group|3|  
  
     Zusätzliche Beispiele:  
  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|type|Wertname|Wertdaten|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Group|0|  
  
    > [!TIP]  
    >  Verwenden Sie zum Angeben der CPUs 60 bis 63 den QWORD-Wert F000000000000000 oder den BINARY-Wert 1111000000000000000000000000000000000000000000000000000000000000.  
  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|type|Wertname|Wertdaten|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|Group|0|  
  
    |SQL Server 2008 R2|type|Wertname|Wertdaten|  
    |------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|Group|0|  
  
    |SQL Server 2008|type|Wertname|Wertdaten|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
    |SQL Server 2005|type|Wertname|Wertdaten|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnen von TCP/IP-Ports zu NUMA-Knoten &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Affinitätsmaske (Serverkonfigurationsoption)](affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
