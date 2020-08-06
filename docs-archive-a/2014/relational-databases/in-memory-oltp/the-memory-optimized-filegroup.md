---
title: Die speicheroptimierte Dateigruppe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87622106"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="99857-102">Die speicheroptimierte Dateigruppe</span><span class="sxs-lookup"><span data-stu-id="99857-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="99857-103">Um speicheroptimierte Tabellen zu erstellen, müssen Sie zuerst eine speicheroptimierte Dateigruppe erstellen.</span><span class="sxs-lookup"><span data-stu-id="99857-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="99857-104">Die speicheroptimierte Dateigruppe enthält mindestens einen Container.</span><span class="sxs-lookup"><span data-stu-id="99857-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="99857-105">Jeder Container enthält Datendateien oder Änderungsdateien oder sowohl als auch.</span><span class="sxs-lookup"><span data-stu-id="99857-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="99857-106">Obwohl Datenzeilen aus `SCHEMA_ONLY`-Tabellen nicht beibehalten werden und die Metadaten für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren in herkömmlichen Katalogen gespeichert werden, ist für die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine weiterhin eine speicheroptimierte Dateigruppe erforderlich, damit die Behandlung speicheroptimierter `SCHEMA_ONLY`-Tabellen für Datenbanken mit speicheroptimierten Tabellen konsistent ist.</span><span class="sxs-lookup"><span data-stu-id="99857-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="99857-107">Die speicheroptimierte Dateigruppe basiert auf Filestream-Dateigruppen, von denen sie sich in folgenden Punkten unterscheidet:</span><span class="sxs-lookup"><span data-stu-id="99857-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="99857-108">Sie können nur eine speicheroptimierte Dateigruppe pro Datenbank erstellen.</span><span class="sxs-lookup"><span data-stu-id="99857-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="99857-109">Sie müssen die Dateigruppe explizit als Container für aus memory_optimized_data markieren.</span><span class="sxs-lookup"><span data-stu-id="99857-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="99857-110">Sie können die Dateigruppe erstellen, wenn Sie die Datenbank erstellen, oder Sie können sie später hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="99857-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="99857-111">Sie müssen der MEMORY_OPTIMIZED_DATA-Dateigruppe mindestens einen Container hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="99857-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="99857-112">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="99857-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="99857-113">Es ist nicht erforderlich, Filestream zu aktivieren ([Aktivieren und Konfigurieren von FILESTREAM](../blob/enable-and-configure-filestream.md)), um eine speicheroptimierte Dateigruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="99857-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="99857-114">Die Zuordnung zu Filestream wird über die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="99857-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="99857-115">Sie können einer speicheroptimierten Dateigruppe neue Container hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="99857-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="99857-116">Möglicherweise benötigen Sie einen neuen Container, um den Speicher zu erweitern, der für die dauerhafte Speicher optimierte Tabelle benötigt wird, sowie für die Verteilung von e/a über mehrere Container.</span><span class="sxs-lookup"><span data-stu-id="99857-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="99857-117">Die Datenverschiebung mit einer speicheroptimierten Dateigruppe ist in einer AlwaysOn-Verfügbarkeitsgruppenkonfiguration optimiert.</span><span class="sxs-lookup"><span data-stu-id="99857-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="99857-118">Im Gegensatz zu Filestream-Dateien, die an sekundäre Replikate gesendet werden, werden die Prüfpunktdateien (Daten und Änderungen) in der speicheroptimierten Dateigruppe nicht an die sekundären Replikate gesendet.</span><span class="sxs-lookup"><span data-stu-id="99857-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="99857-119">Die Daten- und Änderungsdateien werden mithilfe des Transaktionsprotokolls für das sekundäre Replikat erstellt.</span><span class="sxs-lookup"><span data-stu-id="99857-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="99857-120">Beachten Sie die folgenden Einschränkungen der speicheroptimierten Dateigruppe:</span><span class="sxs-lookup"><span data-stu-id="99857-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="99857-121">Sobald Sie eine speicheroptimierte Dateigruppe erstellt haben, können Sie sie nur entfernen, indem Sie die Datenbank löschen.</span><span class="sxs-lookup"><span data-stu-id="99857-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="99857-122">In einer Produktionsumgebung müssen Sie die speicheroptimierte Dateigruppe wahrscheinlich nicht entfernen.</span><span class="sxs-lookup"><span data-stu-id="99857-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="99857-123">Sie können einen nicht leeren Container nicht löschen und Daten- und Änderungsdateipaare nicht in einen anderen Container in der speicheroptimierten Dateigruppe verschieben.</span><span class="sxs-lookup"><span data-stu-id="99857-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="99857-124">Konfigurieren einer speicheroptimierten Dateigruppe</span><span class="sxs-lookup"><span data-stu-id="99857-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="99857-125">Erwägen Sie, mehrere Container in der speicheroptimierten Dateigruppe zu erstellen und auf unterschiedliche Laufwerke zu verteilen, um beim Streamen der Daten in den Arbeitsspeicher eine höhere Bandbreite zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="99857-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="99857-126">Wenn Sie den Speicher konfigurieren, müssen Sie freien Speicherplatz bereitstellen, der viermal so groß wie die dauerhaften speicheroptimierten Tabellen ist.</span><span class="sxs-lookup"><span data-stu-id="99857-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="99857-127">Stellen Sie sicher, dass das e/a-Subsystem die erforderlichen IOPS für die Arbeitsauslastung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="99857-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="99857-128">Wenn Daten- und Änderungsdateipaare bei bestimmten IOPS aufgefüllt werden, benötigen Sie dreimal so viel IOPS, um Speicher- und Zusammenführungsvorgänge zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="99857-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="99857-129">Sie können Speicherkapazität und IOPS hinzufügen, indem Sie einen oder mehrere Container zur speicheroptimierten Dateigruppe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="99857-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="99857-130">In einem Szenario mit mehreren Containern und mehreren Laufwerken werden Daten- und Änderungsdateien im Round-Robin-Verfahren den Containern zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="99857-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="99857-131">Die erste Datendatei wird aus dem ersten Container zugewiesen, und die Änderungsdatei wird aus dem nächsten Container zugewiesen. Dieses Zuordnungsmuster wird wiederholt.</span><span class="sxs-lookup"><span data-stu-id="99857-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="99857-132">Bei diesem Zuordnungsschema werden Daten- und Änderungsdateien gleichmäßig auf Container verteilt, wenn Sie über eine ungerade Zahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="99857-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="99857-133">Wenn Sie jedoch über eine gerade Anzahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind, kann dies zu einer unausgeglichenen Speicherung führen, bei der Datendateien ungeraden Laufwerken und Änderungsdateien geraden Laufwerken zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="99857-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="99857-134">Um bei der Wiederherstellung einen ausgeglichenen e/a-Datenstrom zu erhalten, sollten Sie in Erwägung ziehen, Paare von Daten-und Änderungs Dateien in denselben Spindeln/Speicher zu platzieren, wie im folgenden Beispiel beschrieben.</span><span class="sxs-lookup"><span data-stu-id="99857-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="99857-135">Wenn ein `MAXSIZE`-Wert für die speicheroptimierte Dateigruppe festgelegt wird und Prüfpunktdateien die maximale Größe des Containers überschreiten, ändert sich der Zustand der Datenbank in SUSPECT.</span><span class="sxs-lookup"><span data-stu-id="99857-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="99857-136">Versuchen Sie in diesem Fall nicht, die Datenbank OFFLINE und ONLINE zu schalten, damit die Datenbank im Zustand RECOVERY_PENDING bleibt.</span><span class="sxs-lookup"><span data-stu-id="99857-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="99857-137">Beispiel</span><span class="sxs-lookup"><span data-stu-id="99857-137">Example</span></span> 
<span data-ttu-id="99857-138">Angenommen, Sie verfügen über eine speicheroptimierte Dateigruppe mit den beiden Containern Container 1 auf Laufwerk X und Container 2 auf Laufwerk Y.</span><span class="sxs-lookup"><span data-stu-id="99857-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="99857-139">Da die Zuordnung von Daten- und Änderungsdateien im Round-Robin-Verfahren erfolgt, enthält Container 1 nur Datendateien und Container 2 nur Änderungsdateien. Dies führt zu einer unausgeglichenen Persistenz sowie zu unausgeglichenen Eingabe/Ausgabe-Vorgängen pro Sekunde, da Datendateien deutlich größer als Änderungsdateien sind.</span><span class="sxs-lookup"><span data-stu-id="99857-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="99857-140">Wenn Sie Daten-und Änderungs Dateien gleichmäßig auf die Laufwerke X und Y verteilen möchten, erstellen Sie vier Container anstelle von zwei, und ordnen Sie die ersten beiden Container dem Laufwerk x und den nächsten zwei Containern zu, um Y zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="99857-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="99857-141">Bei der Roundrobin-Zuordnung werden die ersten Daten und die erste Delta Datei aus Container-1 bzw. Container-2 zugeordnet, die Laufwerk X zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="99857-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="99857-142">Ebenso werden die nächste Daten-und Änderungsdatei aus Container-3 und Container-4 zugeordnet, die Laufwerk Y zugeordnet sind. Dadurch können Daten und Delta Dateien gleichmäßig auf zwei Laufwerke verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="99857-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="99857-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99857-143">See Also</span></span>  
<span data-ttu-id="99857-144">[Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="99857-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="99857-145">Datenbankdateien und Dateigruppen</span><span class="sxs-lookup"><span data-stu-id="99857-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  